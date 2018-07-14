# Reference

## Functions
* [`cache_data`](#cache_data): Retrieves data from a cache file, or creates it with supplied data if the file doesn't exist  Useful for having data that's randomly generate
* [`default_content`](#default_content): Takes an optional content and an optional template name and returns the contents of a file.  Examples:      $config_file_content = default_co
* [`dump_args`](#dump_args): dump_args - prints the args to STDOUT in Pretty JSON format.  Useful for debugging purposes only. Ideally you would use this in conjunction w
* [`echo`](#echo): This function output the variable content and its type to the debug log. It's similiar to the "notice" function but provides a better output 
* [`extlib::has_module`](#extlibhas_module): A function that lets you know whether a specific module is on your modulepath
* [`ip_to_cron`](#ip_to_cron): 
* [`random_password`](#random_password): Returns a string of arbitrary length that contains randomly selected characters.  Prototype:      random_password(n)  Where n is a non-negati
* [`resources_deep_merge`](#resources_deep_merge): Deeply merge a "defaults" hash into a "resources" hash like the ones expected by create_resources(). Internally calls the puppetlabs-stdlib f
## Functions

### cache_data
Type: Ruby 3.x API

Retrieves data from a cache file, or creates it with supplied data if the file doesn't exist

Useful for having data that's randomly generated once on the master side (e.g. a password), but
then stays the same on subsequent runs.

Usage: cache_data(namespace, name, initial_data)
Example: $password = cache_data('mysql', 'mysql_password', 'this_is_my_password')

#### `cache_data()`

Retrieves data from a cache file, or creates it with supplied data if the file doesn't exist

Useful for having data that's randomly generated once on the master side (e.g. a password), but
then stays the same on subsequent runs.

Usage: cache_data(namespace, name, initial_data)
Example: $password = cache_data('mysql', 'mysql_password', 'this_is_my_password')

Returns: `Any`

### default_content
Type: Ruby 3.x API

Takes an optional content and an optional template name and returns the
contents of a file.

Examples:

    $config_file_content = default_content($file_content, $template_location)
    file { '/tmp/x':
      ensure  => 'file',
      content => $config_file_content,
    }

#### `default_content()`

Takes an optional content and an optional template name and returns the
contents of a file.

Examples:

    $config_file_content = default_content($file_content, $template_location)
    file { '/tmp/x':
      ensure  => 'file',
      content => $config_file_content,
    }

Returns: `Any`

### dump_args
Type: Ruby 3.x API

dump_args - prints the args to STDOUT in Pretty JSON format.

Useful for debugging purposes only. Ideally you would use this in
conjunction with a rspec-puppet unit test.  Otherwise the output will
be shown during a puppet run when verbose/debug options are enabled.

#### `dump_args()`

dump_args - prints the args to STDOUT in Pretty JSON format.

Useful for debugging purposes only. Ideally you would use this in
conjunction with a rspec-puppet unit test.  Otherwise the output will
be shown during a puppet run when verbose/debug options are enabled.

Returns: `Any`

### echo
Type: Ruby 3.x API

This function output the variable content and its type to the
debug log. It's similiar to the "notice" function but provides
a better output format useful to trace variable types and values
in the manifests.

Example:
$v1 = 'test'
$v2 = ["1", "2", "3"]
$v3 = {"a"=>"1", "b"=>"2"}
$v4 = true
# $v5 is not defined
$v6 = { "b" => { "b" => [1,2,3], "c" => true, "d" => { 'x' => 'y' }}, 'x' => 'y', 'z' => [1,2,3,4,5,6]}
$v7 = 12345

echo($v1, 'My string')
echo($v2, 'My array')
echo($v3, 'My hash')
echo($v4, 'My boolean')
echo($v5, 'My undef')
echo($v6, 'My structure')
echo($v7) # no comment here

# debug log output
# My string (String) "test"
# My array (Array) ["1", "2", "3"]
# My hash (Hash) {"a"=>"1", "b"=>"2"}
# My boolean (TrueClass) true
# My undef (String) ""
# My structure (Hash) {"b"=>{"b"=>["1", "2", "3"], "c"=>true, "d"=>{"x"=>"y"}}, "x"=>"y", "z"=>["1", "2", "3", "4", "5", "6"]}
# (String) "12345"

#### `echo()`

This function output the variable content and its type to the
debug log. It's similiar to the "notice" function but provides
a better output format useful to trace variable types and values
in the manifests.

Example:
$v1 = 'test'
$v2 = ["1", "2", "3"]
$v3 = {"a"=>"1", "b"=>"2"}
$v4 = true
# $v5 is not defined
$v6 = { "b" => { "b" => [1,2,3], "c" => true, "d" => { 'x' => 'y' }}, 'x' => 'y', 'z' => [1,2,3,4,5,6]}
$v7 = 12345

echo($v1, 'My string')
echo($v2, 'My array')
echo($v3, 'My hash')
echo($v4, 'My boolean')
echo($v5, 'My undef')
echo($v6, 'My structure')
echo($v7) # no comment here

# debug log output
# My string (String) "test"
# My array (Array) ["1", "2", "3"]
# My hash (Hash) {"a"=>"1", "b"=>"2"}
# My boolean (TrueClass) true
# My undef (String) ""
# My structure (Hash) {"b"=>{"b"=>["1", "2", "3"], "c"=>true, "d"=>{"x"=>"y"}}, "x"=>"y", "z"=>["1", "2", "3", "4", "5", "6"]}
# (String) "12345"

Returns: `Any`

### extlib::has_module
Type: Ruby 4.x API

A function that lets you know whether a specific module is on your modulepath

#### `extlib::has_module(Pattern[/\A\w+[-\/]\w+\z/] $module_name)`

Returns: `Boolean` Returns true or false.

##### `module_name`

Data type: `Pattern[/\A\w+[-\/]\w+\z/]`

The full name of the module you want to know exists or not.
Namespace and modulename can be separated with either '-' or '/'.

### ip_to_cron
Type: Ruby 3.x API

The ip_to_cron class.

#### `ip_to_cron()`

Returns: `Any`

### random_password
Type: Ruby 3.x API

Returns a string of arbitrary length that contains randomly selected characters.

Prototype:

    random_password(n)

Where n is a non-negative numeric value that denotes length of the desired password.

For example:

  Given the following statements:

    $a = 4
    $b = 8
    $c = 16

    notice random_password($a)
    notice random_password($b)
    notice random_password($c)

  The result will be as follows:

    notice: Scope(Class[main]): fNDC
    notice: Scope(Class[main]): KcKDLrjR
    notice: Scope(Class[main]): FtvfvkS9j9wXLsd6

#### `random_password()`

Returns a string of arbitrary length that contains randomly selected characters.

Prototype:

    random_password(n)

Where n is a non-negative numeric value that denotes length of the desired password.

For example:

  Given the following statements:

    $a = 4
    $b = 8
    $c = 16

    notice random_password($a)
    notice random_password($b)
    notice random_password($c)

  The result will be as follows:

    notice: Scope(Class[main]): fNDC
    notice: Scope(Class[main]): KcKDLrjR
    notice: Scope(Class[main]): FtvfvkS9j9wXLsd6

Returns: `Any`

### resources_deep_merge
Type: Ruby 3.x API

Deeply merge a "defaults" hash into a "resources" hash like the ones expected
by create_resources(). Internally calls the puppetlabs-stdlib function
deep_merge(). In case of duplicate keys the "resources" hash keys win over the
"defaults" hash keys.

Example:

$defaults_hash = {
  'one'   => '1',
  'two'   => '2',
  'three' => '3',
  'four'  => {
    'five'  => '5',
    'six'   => '6',
    'seven' => '7',
  }
}

$numbers_hash = {
  'german' => {
    'one'   => 'eins'
    'three' => 'drei',
    'four'  => {
      'six' => 'sechs',
    }
  },
  'french' => {
    'one' => 'un',
    'two' => 'deux',
    'four' => {
      'five'  => 'cinq',
      'seven' => 'sept',
    }
  }
}

$result_hash = resources_deep_merge($numbers_hash, $defaults_hash)

The $result_hash then looks like this:

# $result_hash = {
#   'german' => {
#     'one'   => 'eins',
#     'two'   => '2',
#     'three' => 'drei',
#     'four'  => {
#       'five'  => '5',
#       'six'   => 'sechs',
#       'seven' => '7',
#     }
#   },
#   'french' => {
#     'one'   => 'un',
#     'two'   => 'deux',
#     'three' => '3',
#     'four'  => {
#       'five'  => 'cinq',
#       'six'   => '6',
#       'seven' => 'sept',
#     }
#   }
# }

#### `resources_deep_merge()`

Deeply merge a "defaults" hash into a "resources" hash like the ones expected
by create_resources(). Internally calls the puppetlabs-stdlib function
deep_merge(). In case of duplicate keys the "resources" hash keys win over the
"defaults" hash keys.

Example:

$defaults_hash = {
  'one'   => '1',
  'two'   => '2',
  'three' => '3',
  'four'  => {
    'five'  => '5',
    'six'   => '6',
    'seven' => '7',
  }
}

$numbers_hash = {
  'german' => {
    'one'   => 'eins'
    'three' => 'drei',
    'four'  => {
      'six' => 'sechs',
    }
  },
  'french' => {
    'one' => 'un',
    'two' => 'deux',
    'four' => {
      'five'  => 'cinq',
      'seven' => 'sept',
    }
  }
}

$result_hash = resources_deep_merge($numbers_hash, $defaults_hash)

The $result_hash then looks like this:

# $result_hash = {
#   'german' => {
#     'one'   => 'eins',
#     'two'   => '2',
#     'three' => 'drei',
#     'four'  => {
#       'five'  => '5',
#       'six'   => 'sechs',
#       'seven' => '7',
#     }
#   },
#   'french' => {
#     'one'   => 'un',
#     'two'   => 'deux',
#     'three' => '3',
#     'four'  => {
#       'five'  => 'cinq',
#       'six'   => '6',
#       'seven' => 'sept',
#     }
#   }
# }

Returns: `Any`
