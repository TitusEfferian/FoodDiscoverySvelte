<style>
    .restorant-container {
        height: 96px;
        display: flex;
        margin-top: 20px;
    }
    .restorant-image {
        width: 96px;
        height: 96px;
        border-radius: 6px;
        margin-right: 16px;
        object-fit: cover;
    }
    .restorant-wrapper {
        display: flex;
        flex-direction: column;
    }
    .restorant-title {
        overflow: hidden;
        display: -webkit-box;
        -webkit-line-clamp: 2;
        -webkit-box-orient: vertical;
        font-size: 14px;
        line-height: 1.42857143;
        font-weight: 500;
    }
    .restorant-type {
        margin-top: 6px;
        font-size: .85714286rem;
        line-height: 1.5;
        font-weight: 400;
        color: #676767;
    }
    .rating-distance-wrapper {
        display: flex;
        margin-top: 4px;
        font-size: .85714286rem;
        line-height: 1.5;
        font-weight: 400;
        color: #676767;
        align-items: center;
    }
    .star {
        display: inline-block;
        background-position: center center;
        background-repeat: no-repeat;
        background-size: contain;
        background-image: url('https://food.grab.com/static/images/icons/icon-star.svg');
        width: 16px;
        height: 16px;
    }
    p{
        margin: 0;
        padding: 0;
    }
</style>

<script>
    export let restorantName;
    export let restorantRating;
    export let restorantDistance;
    export let restorantImage;
    export let restorantType;
</script>

<div class="restorant-container">
    <img alt="restorant" class="restorant-image" src={restorantImage}/>
    <div class="restorant-wrapper">
        <p class="restorant-title">{restorantName}</p>
        <p class="restorant-type">{restorantType}</p>
        <div class="rating-distance-wrapper">
            <div class="star"/>
            <p style="margin-left: 6px;">{restorantRating}</p>
            <p style="margin-left: 6%;">{restorantDistance} km</p>
        </div>
    </div>
</div>