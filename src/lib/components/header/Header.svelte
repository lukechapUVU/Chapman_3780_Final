<script>
    let profileImg = 'https://t4.ftcdn.net/jpg/03/31/69/91/360_F_331699188_lRpvqxO5QRtwOM05gR50ImaaJgBx68vi.jpg'

    const changeProfileImg = (event) => {
        const file = event.target.files[0];
        const reader = new FileReader();
        reader.onload = () => {
            const src = reader.result;
            profileImg = src
        }
        reader.readAsDataURL(file)
    }

</script>
<header class="navbar flex">
    <a href="/dogs" class="btn btn-ghost normal-case text-xl">Dogs</a>
    <a href="/bookings" class="btn btn-ghost normal-case text-xl">Upcoming Bookings</a>
    <a href="/faq" class="btn btn-ghost normal-case text-xl">FAQ</a>
    <div class="ml-auto mr-4">
        <label for="profileModal" class="btn btn-lg btn-circle btn-ghost">
            <img class="btn btn-circle border-none" src={profileImg} alt="Profile Image"/>
        </label>
        
        <input type="checkbox" id="profileModal" class="modal-toggle" />
        <div class="modal">
            <div class="modal-box  w-1/3 max-w-5xl">
                <h1 class="text-3xl text-center">Edit Profile</h1>
                <label for="profileModal" class="btn btn-sm btn-circle absolute right-2 top-2">✕</label>
                <div class="flex">
                    <div class="my-auto pr-8">
                        <img class="mask mask-squircle w-1/2 block mx-auto mb-4" src={profileImg} alt="Profile Image" />
                        <input type="file" class="file-input file-input-xs file-input-bordered w-full max-w-xs" on:change={changeProfileImg} />
                    </div>
                    <form>
                        <div class="form-row">
                          <div class="form-group col-md-6">
                            <label for="inputFirstName">First Name:</label>
                            <input id="inputFirstName" type="text" class="form-control" style="width: 80%">
                          </div>
                          <div class="form-group col-md-6">
                            <label for="inputLastName">Last Name:</label>
                            <input id="inputLastName" type="text" class="form-control" style="width: 100%">
                          </div>
                        </div>
                        <div class="form-row">
                            <div class="form-group">
                            <label for="inputEmail">Email:</label>
                            <input id="inputEmail" type="email" class="form-control" style="width: 100%">
                            </div>
                        </div>
                        <div class="form-row">
                            <div class="form-group">
                                <label for="inputPhone">Phone:</label>
                                <input id="inputPhone" type="tel" class="form-control" style="width: 100%">
                            </div>
                        </div>
                        <div class="form-row">
                            <div class="form-group">
                                <label for="inputStreet">Street Address:</label>
                                <input id="inputStreet" type="text" class="form-control" style="width: 100%">
                            </div>
                        </div>
                        <div class="form-row">
                            <div class="form-group">
                                <label for="inputCity">City:</label>
                                <input id="inputCity" type="text" class="form-control" style="width: 90%">
                            </div>
                        </div>
                        <div class="form-row">
                            <div class="form-group col-md-6 mr-6">
                                <label for="inputState">State:</label>
                                <select id="inputState" class="bg-white text-black rounded h-1/2" name="cars">
                                    <option value="">--Select a state--</option>
                                    <option value="AL">Alabama</option>
                                    <option value="AK">Alaska</option>
                                    <option value="AZ">Arizona</option>
                                    <option value="AR">Arkansas</option>
                                    <option value="CA">California</option>
                                    <option value="CO">Colorado</option>
                                    <option value="CT">Connecticut</option>
                                    <option value="DE">Delaware</option>
                                    <option value="DC">District Of Columbia</option>
                                    <option value="FL">Florida</option>
                                    <option value="GA">Georgia</option>
                                    <option value="HI">Hawaii</option>
                                    <option value="ID">Idaho</option>
                                    <option value="IL">Illinois</option>
                                    <option value="IN">Indiana</option>
                                    <option value="IA">Iowa</option>
                                    <option value="KS">Kansas</option>
                                    <option value="KY">Kentucky</option>
                                    <option value="LA">Louisiana</option>
                                    <option value="ME">Maine</option>
                                    <option value="MD">Maryland</option>
                                    <option value="MA">Massachusetts</option>
                                    <option value="MI">Michigan</option>
                                    <option value="MN">Minnesota</option>
                                    <option value="MS">Mississippi</option>
                                    <option value="MO">Missouri</option>
                                    <option value="MT">Montana</option>
                                    <option value="NE">Nebraska</option>
                                    <option value="NV">Nevada</option>
                                    <option value="NH">New Hampshire</option>
                                    <option value="NJ">New Jersey</option>
                                    <option value="NM">New Mexico</option>
                                    <option value="NY">New York</option>
                                    <option value="NC">North Carolina</option>
                                    <option value="ND">North Dakota</option>
                                    <option value="OH">Ohio</option>
                                    <option value="OK">Oklahoma</option>
                                    <option value="OR">Oregon</option>
                                    <option value="PA">Pennsylvania</option>
                                    <option value="RI">Rhode Island</option>
                                    <option value="SC">South Carolina</option>
                                    <option value="SD">South Dakota</option>
                                    <option value="TN">Tennessee</option>
                                    <option value="TX">Texas</option>
                                    <option value="UT">Utah</option>
                                    <option value="VT">Vermont</option>
                                    <option value="VA">Virginia</option>
                                    <option value="WA">Washington</option>
                                    <option value="WV">West Virginia</option>
                                    <option value="WI">Wisconsin</option>
                                    <option value="WY">Wyoming</option>
                                </select>
                            </div>
                            <div class="form-group col-md-4">
                                <label for="inputZip">Zip:</label>
                                <input id="inputZip" type="text" class="form-control" style="width: 70%">
                            </div>
                        </div>
                    </form>
                </div>
            </div>
        </div>
        
    </div>
    
</header>

<style>
    .form-row {
        display: flex;
        flex-wrap: wrap;
    }

    .form-group {
        margin-bottom: 8px;
        margin-top: 8px;
    }

    .form-group.col-md-6 {
        flex: 0 0 50%;
    }

    .form-group.col-md-4 {
        flex: 0 0 33%;
    }

    .form-control {
        display: block;
        
        height: calc(1.5em + 0.75rem + 2px);
        padding: 0.375rem 0.75rem;
        font-size: 1rem;
        font-weight: 400;
        line-height: 1.5;
        color: #495057;
        background-color: #fff;
        background-clip: padding-box;
        border: 1px solid #ced4da;
        border-radius: 0.25rem;
        transition: border-color 0.15s ease-in-out, box-shadow 0.15s ease-in-out;
    }
</style>