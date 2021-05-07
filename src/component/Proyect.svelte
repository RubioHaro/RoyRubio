<svelte:options accessors={true} />

<script>
  import {
    Button,
    Modal,
    ModalBody,
    ModalFooter,
    ModalHeader,
    Col,
    Container,
    Row,
  } from "sveltestrap";

  export let open;
  export let proyect;
  export let toggle = () => (open = !open);
</script>

<svelte:head>
  <title>Proyect</title>
  <!-- <link rel="stylesheet" href="css/animate.min.css" />
  <link
    rel="stylesheet"
    href="https://cdnjs.cloudflare.com/ajax/libs/normalize/8.0.1/normalize.min.css"
  /> -->
  <!-- <script src="//ajax.googleapis.com/ajax/libs/jquery/1.11.1/jquery.min.js"></script> -->
</svelte:head>

<div>

  <Modal size="lg" isOpen={open} {toggle}>
    <ModalHeader {toggle}>
      <h3>
        {proyect.title}
      </h3>
    </ModalHeader>
    <ModalBody>
      <Row>
        <Col md="8" xs="12">
          <img class="img-fluid" src={proyect.img} alt={proyect.imgTitle} />
        </Col>
        <Col md="4" xs="12">
          <p>
            {proyect.content}
          </p>
        </Col>
      </Row>
    </ModalBody>
  </Modal>
</div>
