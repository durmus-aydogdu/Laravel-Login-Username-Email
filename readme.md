## Laravel Login Username or Email

Laravel Login Username or Email code example.

## Login Code

    app/Http/Controllers/Auth/LoginController.php
    
    `public function username()
     {
 
         $login = request()['login'];
 
         if (filter_var($login, FILTER_VALIDATE_EMAIL)) {
             request()->merge(['email' => $login]);
             return 'email';
         }
 
         request()->merge(['name' => $login]);
         return 'name';
 
     }`
     
     
     resources/views/auth/login.blade.php
     
    <div class="col-md-6">                          
        <input id="login" type="text" class="form-control{{ $errors->has('name') ? ' is-invalid' : ''}} {{$errors->has('email') ? ' is-invalid' : ''}}" name="login" value="{{ old('login') }}" required autocomplete="email" autofocus>
    
            @if ($errors->has('name') || $errors->has('email'))
                 <span class="invalid-feedback" role="alert">
                        <strong>These credentials do not match our records.</strong>
                 </span>
            @endif
    </div>
    
    
