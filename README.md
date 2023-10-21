# Bashar Laravel Search
A laravel package to search via your models .

installation : 

`composer require basharbkaya/laravel-search`

## Usage :

### in model
- use `Searchable` trait in your model
- Define `$searchable` property in your model to select which columns to search in

Example :

```  
use BasharBkaya\LaravelSearch\Searchable;

class User extends Model {

  use Searchable ;
  protected $searchable = ['name', 'comments.title'];
  
  public function comments(){
    return $this->hasMany(Post::class);
  }
}
```

### in controller
Example :

```  
<?php

namespace App\Http\Controllers;

use App\Models\User;
use Illuminate\Http\Request;
use Illuminate\Routing\Controller as BaseController;

class Controller extends BaseController
{
    use AuthorizesRequests, ValidatesRequests;

    function index(Request $request)
    {
        $term = $request->query('term', '');
        return User::search($term)->get();
    }
}
```