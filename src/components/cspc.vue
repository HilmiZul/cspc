<template>
  <div id="nomor-1">
    <div class="container">
      <div class="row justify-content-center">
        <div class="col-md-6">
          <div class="form-group">
            <textarea v-model="teks" class="form-control shadow-lg" cols="30" rows="5" placeholder="Type something..."></textarea>
          </div>
          <div class="form-group">
            <textarea readonly class="form-control shadow-lg" cols="30" rows="5" placeholder="The results will appear here...">{{ this.result }}</textarea>
          </div>
        </div>
        <div class="col-md-6">
          <div class="alert alert-info text-left shadow-lg">
            <strong>e.g. input:</strong>
            <pre>z+U-L- h+I-lmi</pre>
            <strong>output:</strong>
            <pre>Zul Hilmi</pre>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'nomor-1',
  data() {
    return {
      teks: '',
    }
  },

  computed: {
    result() {
      let t = this.teks.split("")
      for (let i = 0; i < t.length; i++) {
        if (t[i] === '+') {
          t[i] = t.splice(i, '')
          t[i-1] = t[i-1].toUpperCase()
        } else if (t[i] === '-') {
          t[i] = t.splice(i, '')
          t[i-1] = t[i-1].toLowerCase()
        }
      }
      t = t.join("")
      return t
    }
  }
}
</script>