<script>

    import { Container,Row,Col, Card, CardHeader, CardBody } from "sveltestrap";
    import axios from "axios";

    let chara;
    let data = [];

    async function inputHandler(e) {
        chara = e.target.value.replace(" ", "+");
    }

    async function submitHandler(e) {
        e.preventDefault();
        try {
            const respone = await axios.get("https://acd-api.herokuapp.com/" + chara);
            const json = respone.data.search_results;
            if (json == undefined) {
                throw new Error;
            } else {
                data = json;
            }
        } catch (err) {
            console.log(err);
        }
    }
    
</script>

<Container>
    <Row class="mt-5 mb-5">
        <Col class="12">
            <Card class="custom-card">
                <CardHeader class="text-center">
                    <form on:submit|preventDefault={submitHandler}>
                        <input type="text" class="trans" placeholder="Search Here" on:input={inputHandler}>
                        <!-- <button type="submit" class="btn btn-primary">Cari</button> -->
                    </form>
                </CardHeader>
                <CardBody>
                    {#each data as row}
                        <Row>
                            <Col sm="12" class="mb-3">
                                <Card class="custom-card">
                                    <CardHeader class="text-center">
                                        <img src={row?.character_image} alt="Anime" class="rounded-circle kecil">
                                    </CardHeader>
                                    <CardBody class="text-center">
                                        Character Name : {row?.name}<br>
                                        Gender : {row?.gender}<br>
                                        Anime : {row?.anime_name}<br>
                                    </CardBody>
                                </Card>
                            </Col>
                        </Row>
                    {:else}
                        <div class="text-center">
                            <h4>Awaiting Your Command</h4>
                        </div>
                    {/each}
                </CardBody>
            </Card>
        </Col>
    </Row>
</Container>