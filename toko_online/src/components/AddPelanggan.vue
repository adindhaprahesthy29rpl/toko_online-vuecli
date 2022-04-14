<template>
<br>
<br>
    <div class="container">
        <div class="card">
            <div class="card-body"><br>
            <h3 class="card-title"><center>Tambah Data Pelanggan</center></h3>
            
            Nama :
            <input type="text" name="nama" v-model="nama" class="form-control">
            <br>
            
            Alamat :
            <textarea class="form-control" id="alamat" v-model="alamat" rows="3"></textarea>
            <br>
            
            Telephone :
            <input type="number" name="telp" v-model="telp" class="form-control">
            <br>
            
            Username :
            <input type="text" name="username" v-model="username" class="form-control">
            <br>
            
            Password :
            <input type="password" name="password" v-model="password" class="form-control">
            <br>
            <button type="button" class="btn btn-primary" @click="addpelanggan()" data-bs-dismiss="modal">Submit</button>
            </div>
        </div>
    </div>

</template>

<script>
    export default {
        name : "AddPelanggan",
        data(){
            return {
                nama : "",
                alamat : "",
                telp : "",
                username : "",
                password : ""
            }
        },

        methods:{
            addpelanggan:function(){
                let form =
                {
                    'nama':this.nama,
                    'alamat':this.alamat,
                    'telp':this.telp,
                    'username':this.username,
                    'password':this.password
                }

                this.axios.post('http://127.0.0.1:8000/public/api/pelanggan', form)
                .then((response)=>{
                    this.list_pelanggan = response.data;
                    this.$router.push('/pelanggan')
                    console.log(response)
                })
            }
        }
    }
</script>
