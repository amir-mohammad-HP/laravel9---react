#basic commands:

## creata laravel application :
  ```bash
  composer create-project --prefer-dist laravel/laravel project-name
  ```

## migrations :
```bash
php artisan migrate
```

## create authentication api:
creata a controller under http/controllers/api folder in apps:
```bash
php artisan make:controller Api/AuthController
```
open AuthController:
add this in to your code:

```php 

public function signup(SignupRequest $request) 
    {
        $data = $request->validated();
        /** @var \App\Models\User $user */
        $user = User::create([
            'name' => $data['name'],
            'email' => $data['email'],
            'password' => bcrypt($data['password']),
        ]);

        $token = $user->createToken('main')->plainTextToken;
        
        // return response([
        //     'user' => $user,
        //     'token' => $token
        // ]); 
        return response(compact('user', 'token'));
    }

    public function login(LoginRequest $request)
    {
        $credentials = $request->validated();
        if(!Auth::attempt($credentials)) {
            return response([
                'message' => 'Provided email address or password is incorrect'
            ], 422);
        };

        /** @var User $user */
        $user = Auth::user();
        $token = $user->createToken('main')->plainTextToken;

        return response(compact('user', 'token'));
    }

    public function logout(Request $request) 
    {   
        /** @var User $user */
        $user = $request ->user();
        $user->currentAccessToken()->delete();
        return response('', 204); // means response was success but nothing to return 
    }


```

don't worry about errors will catch up soon 

now needs to create two requests:
```bash
php artisan make:request LoginRequest

php artisan make:request SignupRequest
```

