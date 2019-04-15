1、在 app Providers目录中的AppServiceProvider.php  中的boot 方法中添加
    DB::listen(function ($query) {
		    // $query->sql
		    // $query->bindings
		    // $query->time

		    $tmp = str_replace('?', '"'.'%s'.'"', $query->sql);
		    $tmp = vsprintf($tmp, $query->bindings);
		    $tmp = str_replace("\\","",$tmp);
		    Log::info($tmp."\t");
	    });