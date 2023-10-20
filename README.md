# Bashar Laravel Search
A laravel package to search via your models .

installation : 

`composer require basharbkaya/laravel-search`

Usage :

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