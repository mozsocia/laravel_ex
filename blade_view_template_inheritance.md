#### layouts/app.blade.php
```
<html>
    <head>
        <title>App Name - @yield('title')</title>
    </head>
    <body>
        @section('sidebar')
            This is the master sidebar.
        @show

        @include('layouts.navigation')

        <div class="container">
            @yield('content')
        </div>

        <footer>
            
            @include('layouts.footer')
        </footer>
    </body>
</html>
```

#### layouts/navigation.blade.php
```
<ul>
  <li>
    <a
      href="/"
      class="{{ request()->is('/' ? 'active' : '') }}">
      home
    </a>
  </li>
  <li>
    <a
      href="/"
      class="{{ request()->is('about' ? 'active' : '') }}">
      about
    </a>
  </li>
  <li>
    <a
      href="/"
      class="{{ request()->is('contact/*' ? 'active' : '') }}">
      contact
    </a>
  </li>
</ul>

```

#### child.blade.php
```
@extends('layouts.app')

@section('title', 'Page Title')

@section('sidebar')
    @parent

    <p>This is appended to the master sidebar.</p>
@endsection

@section('content')
    <p>This is my body content.</p>
@endsection
```
