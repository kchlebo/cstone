<template>
    <div class="row justify-content-center">
        <div class="col-8">
            <form name="editForm" role="form" novalidate v-on:submit.prevent="save()" >
                <h2 id="cstoneApp.group.home.createOrEditLabel" v-text="$t('cstoneApp.group.home.createOrEditLabel')">Create or edit a Group</h2>
                <div>
                    <div class="form-group" v-if="group.id">
                        <label for="id" v-text="$t('global.field.id')">ID</label>
                        <input type="text" class="form-control" id="id" name="id"
                               v-model="group.id" readonly />
                    </div>
                    <div class="form-group">
                        <label class="form-control-label" v-text="$t('cstoneApp.group.name')" for="group-name">Name</label>
                        <input type="text" class="form-control" name="name" id="group-name"
                            :class="{'valid': !$v.group.name.$invalid, 'invalid': $v.group.name.$invalid }" v-model="$v.group.name.$model"  required/>
                        <div v-if="$v.group.name.$anyDirty && $v.group.name.$invalid">
                            <small class="form-text text-danger" v-if="!$v.group.name.required" v-text="$t('entity.validation.required')">
                                This field is required.
                            </small>
                        </div>
                    </div>
                    <div class="form-group">
                        <label class="form-control-label" v-text="$t('cstoneApp.group.email')" for="group-email">Email</label>
                        <input type="text" class="form-control" name="email" id="group-email"
                            :class="{'valid': !$v.group.email.$invalid, 'invalid': $v.group.email.$invalid }" v-model="$v.group.email.$model"  required/>
                        <div v-if="$v.group.email.$anyDirty && $v.group.email.$invalid">
                            <small class="form-text text-danger" v-if="!$v.group.email.required" v-text="$t('entity.validation.required')">
                                This field is required.
                            </small>
                        </div>
                    </div>
                </div>
                <div>
                    <button type="button" id="cancel-save" class="btn btn-secondary" v-on:click="previousState()">
                        <font-awesome-icon icon="ban"></font-awesome-icon>&nbsp;<span v-text="$t('entity.action.cancel')">Cancel</span>
                    </button>
                    <button type="submit" id="save-entity" :disabled="$v.group.$invalid || isSaving" class="btn btn-primary">
                        <font-awesome-icon icon="save"></font-awesome-icon>&nbsp;<span v-text="$t('entity.action.save')">Save</span>
                    </button>
                </div>
            </form>
        </div>
    </div>
</template>
<script lang="ts" src="./group-update.component.ts">
</script>
