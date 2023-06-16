# kopi-kuy
<!DOCTYPE html>
<html lang="id">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="shortcut icon" href="images/favicon/favicon.ico" type="image/x-icon">
    <title>Produk</title>
    <link rel="shortcut icon" href="images/favicon.ico" type="image/x-icon">
    <link rel="stylesheet" href="vendor/bootstrap/bootstrap.min.css">
    <link rel="stylesheet" href="vendor/bootstrap/bootstrap-icons.css">
    <script src="vendor/bootstrap/bootstrap.bundle.min.js"></script>
    <link rel="stylesheet" href="https://rikikurnia.com/block/vendor/rikiblock/css/riki_block.css">
    <style>
        section {
            min-height: 90vh;
        }

        .bg-cokelat {
            background-color: rgb(167, 105, 6);
        }
    </style>
    <script src="js/jquery-3.6.3.min.js"></script>
</head>

<body>
    <!-- Tulis Kode Bootstrap Di Bawah Sini -->

    <nav class="navbar navbar-expand-lg bg-success navbar-dark w-100 fixed-top">
        <div class="container-fluid">
            <a class="navbar-brand" href="#">
                <img class="logo" src="images/logo/logo_kuy.png" height="40">
            </a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse"
                data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false"
                aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarSupportedContent">
                <ul class="navbar-nav ms-auto me-3 mb-2 mb-lg-0">
                    <li class="nav-item">
                        <a class="nav-link active" aria-current="page" href="index.html">Home</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="index.html#best-seller">Best Seller</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="index.html#our-team">Our Team</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="index.html#review">Review</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="index.html#contact-us">Contact Us</a>
                    </li>
                </ul>
                <a class="btn btn-outline-light" href="https://wa.me/6281290465034" target="_blank">Chat <i
                        class="bi bi-whatsapp"></i></a>

            </div>
        </div>
    </nav>


    <section class="produk mt-5 pt-5 text-center">
        <div class="container">
            <h1 id="judul">Silahkan Pilih Kopi Anda !</h1>
            <p>KUALITAS NO 1 NO BOHONG BOHONG</p>
            <hr class="border border-success border-3 opacity-75">

            <div class="form-floating col-md-4 m-auto">
                <select class="form-select" id="select_kopi">
                    <option selected disabled>-</option>
                    <option value="arabica">Arabica</option>
                    <option value="robusta">Robusta</option>
                </select>
                <label for="select_kopi">Pilih Jenis Kopi</label>
            </div>

            <div id="baris_produk" class="row row-cols-1 row-cols-sm-2 row-cols-md-3 row-cols-lg-4 my-4">

                <div class="col mb-4">
                    <div class="card">
                        <img src="images/produk/anime.jpg" class="card-img-top" alt="...">
                        <div class="card-body">
                            <h5 class="card-title">Cappuccino</h5>
                            <div class="row keterangan my-4">
                                <div class="col">
                                    100 Gram
                                </div>
                                <div class="col">
                                    24.000
                                </div>
                            </div>
                            <a href="#" class="btn btn-success w-100">Beli</a>
                        </div>
                    </div>
                </div>

            </div>



        </div>
    </section>

    <footer class="bg-success py-4">
        <div class="container">
            <div class="row align-items-center">
                <div class="col-md-8">
                    <ul class="nav">
                        <li class="nav-item">
                            <a class="nav-link link-light active" aria-current="page" href="index.html">Home</a>
                        </li>
                        <li class="nav-item">
                            <a class="nav-link link-light" href="index.html#best-seller">Best Seller</a>
                        </li>
                        <li class="nav-item">
                            <a class="nav-link link-light" href="index.html#our-team">Our Team</a>
                        </li>
                        <li class="nav-item">
                            <a class="nav-link link-light" href="index.html#review">Review</a>
                        </li>
                        <li class="nav-item">
                            <a class="nav-link link-light" href="index.html#contact-us">Contact Us</a>
                        </li>
                    </ul>
                </div>
                <div class="col-md-4 text-light text-end">
                    Copyright Kopi Kuy 2023
                </div>
            </div>
        </div>
    </footer>

    <script>
        /* Tulis Javascript Di bawah Sini*/
        var sumber = "https://rikikurnia.com/prakerja/api/kopi"
        var sumber2 = "data.json"

        select_kopi.onchange = function () {
            var dipilih = select_kopi.value
            console.log(dipilih)

            var template = ""

            $.getJSON(sumber).then(function (data) {
                var data_kopi = data[dipilih]
                console.log(data_kopi)

                data_kopi.forEach(item => {
                    template += `<div class="col mb-4">
                        <div class="card">
                            <img src="${item.foto}" class="card-img-top" alt="...">
                            <div class="card-body">
                                <h5 class="card-title">${item.nama}</h5>
                                <div class="row keterangan my-4">
                                    <div class="col">
                                        ${item.size}
                                    </div>
                                    <div class="col">
                                        ${item.harga}
                                    </div>
                                </div>
                                <a href="${item.link}" class="btn btn-success w-100">Beli</a>
                            </div>
                        </div>
                    </div>`
                })

                baris_produk.innerHTML = template

            })
        }
    </script>
</body>

</html>
