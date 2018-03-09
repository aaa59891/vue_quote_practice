<template>
    <div class="row">
        <div class="col-sm-12">
            <h1>Quotes Added</h1>
            <div class="progress">
                <div class="progress-bar" role="progressbar" :style="{width: (current / max) * 100 + '%'}" :aria-valuenow="current" aria-valuemin="0"
                    :aria-valuemax="max">
                    {{ current }} / {{ max }}
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        props: {
            max: {
                type: Number,
                required: true
            },
            current: {
                type: Number,
                required: true
            }
        }
    }
</script>

<style scoped>
</style>