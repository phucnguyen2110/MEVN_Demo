<template>
    <v-container>
        <v-row no-gutters>
            <v-col sm="10" class="pa-4 mx-auto">
                <v-card class="pa-2">
                    <v-img :src="`/${post.image}`"></v-img>
                    <v-card-actions class="pb-0">
                        <v-row class="mt-1 mx-1">
                            <v-col sm="2">
                                <v-btn small outlined color="primary" class="category">{{post.category}}</v-btn>
                            </v-col>
                            <v-col sm="10" class="d-flex justify-end">
                                <v-btn color="success" text :to="{name: 'edit-post', params: {id: post._id}}">
                                    <v-icon left>mdi-pencil</v-icon> Sửa</v-btn>
                                <v-btn color="red" text @click="removePost()">
                                    <v-icon left>mdi-delete</v-icon> Xóa</v-btn>
                            </v-col>
                        </v-row>
                    </v-card-actions>
                    <v-card-subtitle class="headline">
                        <h3>{{post.title}}</h3>
                    </v-card-subtitle>
                    <v-card-text class="grey--text">
                        <p>{{post.content}}</p>
                        <p>{{post.created}}</p>
                    </v-card-text>
                </v-card>
            </v-col>
        </v-row>
    </v-container>
</template>
<style>
@import '../css/main.css';
</style>
<script>
import API from '../api'
export default {
    data(){
        return {
            post: {},
        }
    },
    async created(){
        const response = await API.getPostByID(this.$route.params.id)
        this.post = response;
    },
    methods: {
        async removePost(){
            Swal.fire({
                title: 'Thông báo!',
                text: 'Chức năng nhóm đang hoàn thiện',
                icon: 'info',
                confirmButtonText: 'OK'
            })
        }
    }
}
</script>
