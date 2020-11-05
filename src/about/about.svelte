<script>
    import { Container,Row,Col,Card,CardBody,CardFooter } from "sveltestrap";
    let src = "/img/profile.jpg";
</script>

<Container>
    <Card class="mt-5 mb-5 custom-card">
        <CardBody>
            <Row class="mt-5 mb-5">
                <Col sm="5 text-center">
                    <img {src} alt="Profile" class="rounded-circle img-thumbnail mt-3">
                    <p class="text-muted mt-3">~ Ronaldo Kereh ~<br>Advance Beginner Programmer</p>
                </Col>
                <Col sm="7 text-center">
                    <h4 class="text-center">About Me</h4>
                    <p>
                        My name is Ronaldo Kereh, I live in Manado - North Sulawesi. I am interested in making a website application in grade 2 junior high school and my preferred languages ​​are Javascript and Python
                    </p>
                    <h4 class="text-center mt-5">About This Application</h4>
                    <p>
                        This application is made using svelte as the frontend and express as the backend and all data obtained is obtained from <a href="https://www.animecharactersdatabase.com/">https://www.animecharactersdatabase.com/</a>
                    </p>
                </Col>
            </Row>
        </CardBody>
    </Card>
</Container>