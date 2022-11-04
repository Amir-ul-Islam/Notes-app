<template>
   <div class="container mt-4">
      <div class="row mb-3">
         <div class="col d-flex align-items-center justify-content-around">
            <h1 class="fs-1 fw-bold">Notes.</h1>
            <button
               type="button"
               class="btn btn-lg btn-success add-btn"
               data-bs-toggle="modal"
               data-bs-target="#exampleModal"
               data-bs-whatever="@mdo"
            >
               <i class="bi bi-plus-circle"></i>
            </button>
            <!-- modal content start -->
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
                                 type="text"
                                 class="form-control"
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
                                 class="form-control"
                                 id="message-text"
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
                        <button type="button" class="btn btn-primary ">
                           Save new note
                        </button>
                     </div>
                  </div>
               </div>
            </div>
            <!-- modal content start -->
         </div>
      </div>
      <div class="row">
         <div class="col">
            <div class="cards">
               <div class="card text-bg-primary mb-2" style="max-width: 15rem">
                  <div class="card-header">Header</div>
                  <div class="card-body">
                     <h5 class="card-title">Primary card title</h5>
                     <p class="card-text">
                        Some quick example text to build on the card title and
                     </p>
                     <span class="badge text-bg-danger">Date</span>
                  </div>
               </div>
            </div>
         </div>
      </div>
   </div>
</template>

<script setup></script>

<style>
.btn {
   cursor: pointer;
}
.modal-text {
   color: black;
}
</style>
