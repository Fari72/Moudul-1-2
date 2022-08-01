###### Nama: Fari' Affrizal S.
###### Kelas: RPL 1
###### No.Absen: 25
## Modul 1
### Mengenal dan Instalasi Laravel

Tugas soal nomor 1 lakukan proses instalasi framework laravel dalam folder dengan nama masing-masing

```
create_project_laravel/laravel penjualan
```

## Modul 2
### Fitur Pada Laravel

Tugas soal nomor 1 buatlah migration tabel kategori dengan menggunakan teknik yang telah dipelajari dalam modul ini

Langkah 1

ke bagian explorer cari **.env untuk merubah DB_DATABASE=laravel**

buatlah migration memakai terminal VSCode caranya dengan **(klik ctrl+shift+`)** klik seperti dibawah ini

```
php artisan make:migration create_produk_table
```

Isikan kode dibawah ini kedalam file yang telah dibuat
```
<?php

use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

return new class extends Migration
{
    /**
     * Run the migrations.
     *
     * @return void
     */
    public function up()
    {
        Schema::create('produk', function (Blueprint $table) {
            $table->id();
            $table->string('nama');
            $table->integer('id_kategori');
            $table->integer('qty');
            $table->integer('harga_beli');
            $table->integer('harga_jual');
            $table->timestamps();
        });
    }

    /**
     * Reverse the migrations.
     *
     * @return void
     */
    public function down()
    {
        Schema::dropIfExists('produk');
    }
};
```

membuat seeder barang table seeder
```
php artisan make:seeder barangTableSeeder
```

Isikan kode dibawah ini kedalam file yang telah dibuat untuk memberi struktur
```
<?php

namespace Database\Seeders;

use Illuminate\Database\Console\Seeds\WithoutModelEvents;
use Illuminate\Database\Seeder;
use DB;

class barangTabelSeeder extends Seeder
{
    /**
     * Run the database seeds.
     *
     * @return void
     */
    public function run()
    {
        DB::table('barang')->insert(array(
            [
                'nama' => 'Meja',
                'id_kategori' => '1',
                'qty' => '12',
                'harga_beli' => '50000',
                'harga_jual' => '540000',
            ],
            [
                'nama' => 'Kursi',
                'id_kategori' => '1',
                'qty' => '12',
                'harga_beli' => '40000',
                'harga_jual' => '450000',
            ]
            ));
    }
}

```


```
explorer cari database -> seeders -> DatabaseSeeder
```

untuk memanggil bagian barangTableSeeder ke database
```
<?php

namespace Database\Seeders;

// use Illuminate\Database\Console\Seeds\WithoutModelEvents;
use Illuminate\Database\Seeder;

class DatabaseSeeder extends Seeder
{
    /**
     * Seed the application's database.
     *
     * @return void
     */
    public function run()
    {
        $this->call(barangTabelSeeder::class);
    }
}
```

lalu kita bisa mengisi ke terminal seperti dibawah ini
```
php artisan db:seed
```

tugas soal 2 membuat 
###### tabel kategori berstruktur 
- id
- nama
###### value tabel kategori
- Perlengkapan Sekolah
- Komputer
- Sabun
- Accessoris
- ATK

langkah pertama membuat table

```
php artisan make:migration create_kategori
```
Isikan kode dibawah ini kedalam file yang telah dibuat untuk memberi struktur kategori
```
<?php

use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

return new class extends Migration
{
    /**
     * Run the migrations.
     *
     * @return void
     */
    public function up()
    {
        Schema::create('kategori', function (Blueprint $table) {
            $table->id();
            $table->string('nama');
            $table->timestamps();
        });
    }

    /**
     * Reverse the migrations.
     *
     * @return void
     */
    public function down()
    {
        Schema::dropIfExists('kategori');
    }
};
```

untuk membuat seeder kategoriTableSeeder
```
php artisan make:seeder kategoriTableSeeder
```

untuk mengisi bagian nama kategori

```
<?php

namespace Database\Seeders;

use Illuminate\Database\Console\Seeds\WithoutModelEvents;
use Illuminate\Database\Seeder;
use DB;

class kategoriTableSeeder extends Seeder
{
    /**
     * Run the database seeds.
     *
     * @return void
     */
    public function run()
    {
        DB::table('kategori')->insert(array(
            [
            'nama'=> 'PerlengkapanSekolah',
            ],
            [
            'nama'=> 'Komputer',
            ],
            [
            'nama'=> 'Sabun',
            ],
            [
            'nama'=> 'Accesoris',
            ],
            [
            'nama'=> 'ATK',
            ]
        ));
    }
}
```

untuk memanggil bagian kategoriTableSeeder ke database

explorer cari database -> seeders -> DatabaseSeeder

```
<?php

namespace Database\Seeders;

use Illuminate\Database\Console\Seeds\WithoutModelEvents;
use Illuminate\Database\Seeder;
use DB;

class kategoriTableSeeder extends Seeder
{
    /**
     * Run the database seeds.
     *
     * @return void
     */
    public function run()
    {
        DB::table('kategori')->insert(array(
            [
            'nama'=> 'PerlengkapanSekolah',
            ],
            [
            'nama'=> 'Komputer',
            ],
            [
            'nama'=> 'Sabun',
            ],
            [
            'nama'=> 'Accesoris',
            ],
            [
            'nama'=> 'ATK',
            ]
        ));
    }
}
```

mengisi ke terminal untuk menambahkan nama pada kategori
```
php artisan bd:seeder
```
