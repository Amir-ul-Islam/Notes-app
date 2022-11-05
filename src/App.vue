<template>
   <div class="container mt-4">
      <div class="row mb-3">
         <div class="col d-flex align-items-center justify-content-around">
            <h1 class="fs-1 fw-bold">Notes.</h1>
            <!-- modal button start -->
            <button
               type="button"
               @click="checkInput"
               class="btn btn-lg btn-success add-btn"
               data-bs-toggle="modal"
               data-bs-target="#exampleModal"
               data-bs-whatever="@mdo"
            >
               <i class="bi bi-plus-circle"></i>
            </button>
            <!-- modal button end -->

            <!-- modal div start -->
            <div
               class="modal fade"
               id="exampleModal"
               tabindex="-1"
               aria-labelledby="exampleModalLabel"
               aria-hidden="true"
            >
               <div class="modal-dialog">
                  <div class="modal-content">
                     <div class="modal-header">
                        <h1
                           class="modal-title fs-5 modal-text"
                           id="exampleModalLabel"
                        >
                           Add new note.
                        </h1>
                        <button
                           type="button"
                           class="btn-close"
                           data-bs-dismiss="modal"
                           aria-label="Close"
                        ></button>
                     </div>
                     <div class="modal-body">
                        <form>
                           <div class="mb-1">
                              <label
                                 for="recipient-name"
                                 class="col-form-label modal-text"
                                 >Title:</label
                              >
                              <input
                                 v-model.trim="noteValue.topic"
                                 @input="checkInput"
                                 type="text"
                                 class="form-control"
                                 placeholder="Please input topic and it should be less than 20 characters"
                                 id="recipient-name"
                              />
                           </div>
                           <div class="mb-1">
                              <label
                                 for="message-text"
                                 class="col-form-label modal-text"
                                 >Note:</label
                              >
                              <textarea
                                 v-model.trim="noteValue.massage"
                                 @input="checkInput"
                                 class="form-control"
                                 id="message-text"
                                 placeholder="Please input valid massage and it should be less than 100 characters"
                              ></textarea>
                           </div>
                        </form>
                     </div>
                     <div class="modal-footer">
                        <button
                           type="button"
                           class="btn btn-danger"
                           data-bs-dismiss="modal"
                        >
                           Close
                        </button>
                        <button
                           @click="closeModalFunc"
                           type="button"
                           class="btn btn-primary"
                           :disabled="isDisable"
                           data-bs-dismiss="modal"
                        >
                           Save new note
                        </button>
                     </div>
                  </div>
               </div>
            </div>
            <!-- modal div start -->
         </div>
      </div>
      <div class="row">
         <div class="col">
            <!-- cards div start -->
            <div class="cards d-flex flex-wrap justify-content-center">
               <div
                  v-for="(note, i) in allNotesValue"
                  :key="i"
                  class="card m-2 align-self-start"
                  style="
                     max-width: 15rem;
                     min-width: 15rem;
                     max-height: 15rem;
                     overflow: hidden;
                  "
                  :style="{ backgroundColor: note.bgColor }"
               >
                  <div class="card-header">{{ note.topic }}</div>
                  <div class="card-body">
                     <p class="card-text">
                        {{ note.massage }}
                     </p>
                     <span class="badge text-bg-danger">{{ note.date }}</span>
                  </div>
               </div>
            </div>
            <!-- cards div end -->
         </div>
      </div>
   </div>
</template>

<script setup>
import { ref, reactive } from "vue";

// declare & assign all variable
const isDisable = ref(true);
const allNotesValue = ref([]);
const nodesId = ref(0);
const noteValue = reactive({
   topic: "",
   massage: "",
});

//function declare for check input valid or invalid
function checkInput() {
   if (
      !noteValue.topic ||
      !noteValue.massage ||
      noteValue.topic.length > 20 ||
      noteValue.massage.length > 100
   ) {
      isDisable.value = true;
   } else {
      isDisable.value = false;
   }
}

//function declare for push all value in allNotesValue
const closeModalFunc = () => {
   //check for check input valid or invalid
   if (
      !noteValue.topic ||
      !noteValue.massage ||
      noteValue.topic.length > 20 ||
      noteValue.massage.length > 100
   )
      return;
   //push method
   allNotesValue.value.push({
      id: nodesId.value++,
      topic: noteValue.topic,
      massage: noteValue.massage,
      date: new Date().toLocaleDateString("bd"),
      bgColor: getRandomColor(),
   });
   //after push empty input v-modal
   noteValue.topic = "";
   noteValue.massage = "";
};

//function declare for light color generator
function getRandomColor() {
   return "hsl(" + Math.random() * 360 + ", 100%, 75%)";
}
</script>

<style>
.btn {
   cursor: pointer;
}
.modal-text {
   color: black;
}
</style>
