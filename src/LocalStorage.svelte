<script context="module">
  export function updateStorage(key, item) {
    localStorage.setItem(key, item)
  }
  export function readStorage(key) {
    const itemStr = localStorage.getItem(key)
    const items = itemStr === null ? [] : itemStr.split(',')
    return items
  }
</script>
