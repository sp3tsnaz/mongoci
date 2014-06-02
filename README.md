mongoci
=======

Fork of : https://github.com/alexbilbie/MongoQB integrated with Codeigniter.

Install Instructions
====================

1- Download the repository
2- Move libraries/Mongoci.php to <codeigniter_install_path>/libraries/Mongoci.php
3- Move config/Mongoci.php to <codeigniter_install_path>/config/Mongoci.php

Edit the <codeigniter_install_path>/config/Mongoci.php file to include username, password, port, auth/no-auth, database_name according to your needs.

Example: (In controller functions) 

    $this->load->library('builder');
		$this->load->view('welcome_message');
		var_dump($this->mongoci->get('system.users'));
		

Examples from the original project (https://github.com/alexbilbie/MongoQB):
===========================================================================

 Insert a document

$qb->insert('collectionName', [
    'name'  =>  'Alex',
    'age'   =>  22,
    'likes' =>  ['whisky', 'gin']
]);

Update a single document

$qb
    ->where(['name' => 'Alex'])
    ->set([
        'country' => 'UK',
        'job' => 'Developer'
    ])
    ->push('likes', ['PHP', 'coffee'])
    ->update('collectionName');

Delete a single document

$qb
    ->where(['name' => 'Alex'])
    ->delete('collectionName');

Search for matching documents

$results = $qb
    ->whereGt('age', 21)
    ->whereIn('likes', ['whisky'])
    ->where('country', 'UK')
    ->get('collectionName');
