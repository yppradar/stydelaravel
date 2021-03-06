# Constructor de consulta en sql
Obtener información de la Base de Datos desde el código laravel.

## Constructor manual de consulta en sql
Devuelve Array  
    $professions = DB::select('SELECT id FROM professions WHERE title = ?', ['Desarrollador back-end']);
    $professions[0]->id

Devuelve Dato  
    $profession = DB::select('SELECT id FROM professions WHERE title = :title LIMIT 0,1', ['title'=>'Desarrollador back-end']);
    $profession

## Constructor laravel de consulta en sql
Devuelve solo el campo id de la primer fila de la tabla  
    $professions = DB::table('professions')->select('id')->table(1)->get();

Devuelve todos los campos de la primer fila de la tabla  
    $professions = DB::table('professions')->first();

Devuelve dos campos con un where omitiendo operador de comparación  
    $professions = DB::table('professions')->select('id','title')->where(['title' => 'Desarrollador back-end'])->first();

    $professions = DB::table('professions')->select('id','title')->where('title','Desarrollador back-end')->first();

Devuelve dos campos con un where y operador de comparación  
    $professions = DB::table('professions')->select('id','title')->where('title', '=', 'Desarrollador back-end')->first();

Devuelve solo el campo id de la primer fila de la tabla  
    $profession = DB::table('professions')->select('id')->first();
    $profession->id

Devuelve el valor de la consulta que se indica  
    $profession = DB::table('professions')
                ->where('title', 'Desarrollador back-end')
                ->value('id');

Devuelve el valor de la consulta que se indica con método mágico  
    $profession = DB::table('professions')->whereTitle('Desarrollador back-end')->value('id');

## Constructor de consulta sql desde modelos laravel
Devuelve Dato  
    $profession = Profession::whereTitle('Desarrollador back-end')->value('id');
