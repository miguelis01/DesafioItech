<template>
  <div class="row">
      <div class="col">
        <div class="card mb-3 mx-10" style="max-width: 25rem">
          <h4 class="card-header">Profile</h4>
          <div class="card-body">
            <!-- Data here-->
            <form class="mb-5">
              <div class="mb-3">
                <label for="first_name" class="form-label">First name</label>
                <input
                  v-model="profile.firstName"
                  type="text"
                  class="form-control mb-3"
                  id="first_name"   
                  disabled               
                />
                <label for="last_name" class="form-label">Last name</label>
                <input
                  v-model="profile.lastName"
                  type="text"
                  class="form-control mb-3"
                  id="last_name" 
                  disabled                 
                />
                <label for="email" class="form-label">Email address</label>
                <input
                  type="email"
                  class="form-control mb-3"
                  id="email"                  
                  :value="$attrs.profile.email"
                  disabled
                />
                <label for="role" class="form-label">Role</label>
                <input
                  type="text"
                  class="form-control mb-3"
                  id="role"                  
                  :value="$attrs.profile.role"
                  disabled
                />
                <label for="is_active" class="form-label">Is Active</label>
                <input
                  type="text"
                  class="form-control mb-3"
                  id="is_active"                  
                  :value="$attrs.profile.isActive"
                  disabled
                />           
              </div>
            </form>
          </div>
        </div>
      </div>
  </div>  
</template>

<script setup>
const emit = defineEmits(["profileUpdate"]);

const { updateProfile } = useIam();
const updateSuccessful = ref(false);
let profileError = ref(null);

// Some profile values
const profile = {
  uuid: "",
  firstName: "",
  lastName: "",
};

// Get profile passed through attributes
const attrs = useAttrs();
profile.uuid = attrs.profile.uuid;
profile.firstName = attrs.profile.firstName;
profile.lastName = attrs.profile.lastName;

// Csrf token should be part of profile
const csrfToken = attrs.profile.csrfToken;

</script>
