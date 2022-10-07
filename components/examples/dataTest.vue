<template>
    <div>

        <ul v-for="item in users">
            <li>id : {{item.id}}</li>
            <li>이름 : {{item.name}}</li>
            <li>전화번호 : {{item.phone_number}}</li>
            <li>등록 시간 : {{item.created_date}}</li>
        </ul>
    </div>
</template>

<script>
    import userList from "/components/testData.json";
    
    export default {
      name: "UserList",
      computed: {
        users() { // #1
          return userList.users.map((items) => { // #2
            // #3 
              let c = new Date(items["created_date"]); 
              let created_date = c.getHours()+"시 "+c.getMinutes()+"분"; 
    
              items["created_date"] = created_date;
              
            return items;
          })
        },
      }
    };
    </script>
    