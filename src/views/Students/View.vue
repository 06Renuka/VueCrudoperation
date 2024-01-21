

<script>
import axios from 'axios';
import { RouterLink } from 'vue-router';

export default {
    name: 'students',
    data() {
        return {
            student: []
        }

    },
    mounted() {

        this.getStudents();
    },
    methods: {
        getStudents() {

            axios.get('http://localhost:8000/api/students').then(res => {
                this.students = resizeBy.data.students
                //   console.log(this.students);

            });
        },
        deleteStudent(studentId) {

            if (confirm('Are you sure, you want to delete this data?')) {
                //console.log(studentId)
                axios.delete(`http://localhost:8000/api/students/${studentId}/delete`)
                    .then(res => {
                        alert(res.data.message);
                        this.getStudent();

                    })
                    .catch(function (error) {
                        if (error.response) {
                            if (error.Response.status == 404) {
                                alert(error.response.data.message);

                            }


                        }

                    });


            }
        }
    }
};
</script>




<template>
    <div class="container">
        <div class="card">
            <div class="card-header">
                <h4>students
                    <RouterLink to="/students/create" class="btn btn-primary float-end">Addd Student</RouterLink>
                </h4>
            </div>
            <div class='card-body'>
                <table class="table table-bordered">
                    <thead>
                        <tr>
                            <th>ID</th>
                            <h4>This is page</h4>
                            <th>NAME</th>
                            <th>Course</th>
                            <th>Email</th>
                            <th>Phone</th>
                            <th>Created At</th>
                            <th>Action</th>

                        </tr>
                    </thead>
                    <tbody v-if="this.students.length > 0">
                        <tr v-for="(student, index) in this.students" :key="index">
                            <td>{{ student.id }}</td>
                            <td>{{ student.name }}</td>
                            <td>{{ student.courses }}</td>
                            <td>{{ student.email }}</td>
                            <td>{{ student.phone }}</td>
                            <td>{{ student.Created_At }}</td>

                            <td>{{ student.Action }}</td>
                            <td>
                                <RouterLink to="{path:'/students/'+student.id+'/edit'}" class="btn btn-success float-end">
                                    Edit</RouterLink>
                                <button type="button" @click="deleteStudent(student.id)"
                                    class="btn btn-danger float-end">Delete</button>
                            </td>
                        </tr>


                    </tbody>

                    <tbody v-else>
                        <tr>
                            <td colspan="7">Loading...</td>
                        </tr>
                    </tbody>

                </table>
            </div>

        </div>
    </div>
</template>
  
