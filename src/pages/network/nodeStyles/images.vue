<template>
  <div>
    <p>
      Display nodes as images.
    </p>
    <vis-network :graph-data="graphData"
                 :options="options"
                 style="height: 500px;">
    </vis-network>
  </div>
</template>

<script>

export default {
  name: 'images',
  data () {
    return {
      graphData: {},
      options: {}
    }
  },
  mounted () {
    // Create a data table with nodes.
    var nodes = []

    // Create a data table with links.
    var edges = []

    const DIR = './static/img/refresh-cl/'
    const EDGE_LENGTH_MAIN = 150
    const EDGE_LENGTH_SUB = 50

    nodes.push({id: 1, label: 'Main', image: DIR + 'Network-Pipe-icon.png', shape: 'image'})
    nodes.push({id: 2, label: 'Office', image: DIR + 'Network-Pipe-icon.png', shape: 'image'})
    nodes.push({id: 3, label: 'Wireless', image: DIR + 'Network-Pipe-icon.png', shape: 'image'})
    edges.push({from: 1, to: 2, length: EDGE_LENGTH_MAIN})
    edges.push({from: 1, to: 3, length: EDGE_LENGTH_MAIN})

    for (let i = 4; i <= 7; i++) {
      nodes.push({id: i, label: 'Computer', image: DIR + 'Hardware-My-Computer-3-icon.png', shape: 'image'})
      edges.push({from: 2, to: i, length: EDGE_LENGTH_SUB})
    }

    nodes.push({id: 101, label: 'Printer', image: DIR + 'Hardware-Printer-Blue-icon.png', shape: 'image'})
    edges.push({from: 2, to: 101, length: EDGE_LENGTH_SUB})

    nodes.push({id: 102, label: 'Laptop', image: DIR + 'Hardware-Laptop-1-icon.png', shape: 'image'})
    edges.push({from: 3, to: 102, length: EDGE_LENGTH_SUB})

    nodes.push({id: 103, label: 'network drive', image: DIR + 'Network-Drive-icon.png', shape: 'image'})
    edges.push({from: 1, to: 103, length: EDGE_LENGTH_SUB})

    nodes.push({id: 104, label: 'Internet', image: DIR + 'System-Firewall-2-icon.png', shape: 'image'})
    edges.push({from: 1, to: 104, length: EDGE_LENGTH_SUB})

    for (let i = 200; i <= 201; i++) {
      nodes.push({id: i, label: 'Smartphone', image: DIR + 'Hardware-My-PDA-02-icon.png', shape: 'image'})
      edges.push({from: 3, to: i, length: EDGE_LENGTH_SUB})
    }

    this.graphData = {
      nodes: nodes,
      edges: edges
    }
    this.options = {}
  }
}
</script>
<style scoped>
</style>
