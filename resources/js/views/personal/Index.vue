<script>
import api from "../../api.js";
export default {
   data(){
         return{
            orders: [],
        }
    },
    methods:{
        getOrders(){
            api.get('/api/auth/personal')
                .then(res =>{
                    console.log(res)
                    this.orders = res.data.data
                    console.log(this.orders)
                })
        }
    },
    mounted() {
        this.getOrders()
    },
}
</script>

<template>
    <main class="overflow-hidden ">
        <!--Start Breadcrumb Style2-->
        <section class="breadcrumb-area" style="background-image: url(/assets/images/inner-pages/breadcum-bg.png);">
            <div class="container">
                <div class="row">
                    <div class="col-xl-12">
                        <div class="breadcrumb-content text-center wow fadeInUp animated">
                            <h2>My Account </h2>
                            <div class="breadcrumb-menu">
                                <ul>
                                    <li><a href="#"><i class="flaticon-home pe-2"></i>Home</a></li>
                                    <li> <i class="flaticon-next"></i> </li>
                                    <li class="active">My Account</li>
                                </ul>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>
        <!--End Breadcrumb Style2-->
        <!--Start My Account Page-->
        <section class="my-account-page pt-120 pb-120">
            <div class="container">
                <div class="row wow fadeInUp animated">
                    <!--Start My Account Page Menu-->
                    <div class="col-xl-3 col-lg-4">
                        <div class="d-flex align-items-start">
                            <div class="nav my-account-page__menu flex-column nav-pills me-3" id="v-pills-tab" role="tablist" aria-orientation="vertical">
                                <button class="nav-link active" id="v-pills-dashboard-tab" data-bs-toggle="pill" data-bs-target="#v-pills-dashboard" type="button" role="tab" aria-controls="v-pills-dashboard" aria-selected="true">
                                    <span> Orders</span>
                                </button>
                                <button class="nav-link" id="v-pills-downloads-tab" data-bs-toggle="pill" data-bs-target="#v-pills-downloads" type="button" role="tab" aria-controls="v-pills-downloads" aria-selected="false">
                                    <span> Downloads</span>
                                </button>
                                <button class="nav-link" id="v-pills-address-tab" data-bs-toggle="pill" data-bs-target="#v-pills-address" type="button" role="tab" aria-controls="v-pills-address" aria-selected="false">
                                    <span> Address</span>
                                </button>
                                <button class="nav-link" id="v-pills-account-tab" data-bs-toggle="pill" data-bs-target="#v-pills-account" type="button" role="tab" aria-controls="v-pills-account" aria-selected="false">
                                    <span> Account Details</span>
                                </button> <button class="nav-link">
                                <span> Logout </span>
                            </button>
                            </div>
                        </div>
                    </div>
                    <div class="col-lg-7">
                        <div class="tab-content " id="v-pills-tabContent">
                            <div class="tab-pane fade show active" id="v-pills-dashboard" role="tabpanel"
                                 aria-labelledby="v-pills-dashboard-tab">
                                <div class="tabs-content__single">
                                    <table v-for="order in orders" class="table">
                                        <thead>
                                        <tr>
                                            <th scope="col"></th>
                                            <th scope="col">Order #{{ order.id }}</th>
                                            <th scope="col">Total</th>
                                            <th scope="col">Status</th>
                                        </tr>
                                        </thead>
                                        <tbody>
                                        <tr>
                                            <th scope="row"></th>
                                            <td>
                                                <template v-for="product in order.products">
                                                    <b>${{product.price}}</b> {{product.title}} <b>x {{ product.qty }} </b><br>
                                                </template>
                                            </td>
                                            <td>${{order.total_price}}</td>
                                            <td v-if="order.payment_status === 1">processed</td>
                                        </tr>
                                        </tbody>
                                    </table>
                                </div>
                            </div>
                            <div class="tab-pane fade" id="v-pills-orders" role="tabpanel"
                                 aria-labelledby="v-pills-orders-tab">
                                <div class="tabs-content__single">

                                </div>
                            </div>
                            <div class="tab-pane fade" id="v-pills-downloads" role="tabpanel"
                                 aria-labelledby="v-pills-downloads-tab">
                                <div class="tabs-content__single">
                                    <h5>My orders</h5>
                                </div>
                            </div>
                            <div class="tab-pane fade" id="v-pills-address" role="tabpanel"
                                 aria-labelledby="v-pills-address-tab">
                                <div class="tabs-content__single">
                                    <h4><span>Hello Admin</span> (Not Admin? Logout)</h4>
                                    <h5>From your account dashboard you can view your <span>Recent Orders, manage your
                                            shipping</span> and <span>billing addresses,</span> and edit your
                                        <span>Password and account details</span></h5>
                                </div>
                            </div>
                            <div class="tab-pane fade" id="v-pills-account" role="tabpanel"
                                 aria-labelledby="v-pills-account-tab">
                                <div class="tabs-content__single">
                                    <h4><span>Hello Admin</span> (Not Admin? Logout)</h4>
                                    <h5>From your account dashboard you can view your <span>Recent Orders, manage your
                                            shipping</span> and <span>billing addresses,</span> and edit your
                                        <span>Password and account details</span></h5>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>
        <!--End My Account Page-->
    </main>
</template>

<style>

</style>
