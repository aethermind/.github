# Aethermind

<div align="center">
  
![Aethermind Logo](https://placeholder.com/logo.png)

**Distributed Browser-Based LLM Framework with Collaborative Decision Making**

[![GitHub Stars](https://img.shields.io/github/stars/aethermind/aethermind.svg)](https://github.com/aethermind/aethermind/stargazers)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](https://github.com/aethermind/aethermind/blob/main/LICENSE)
[![Experimental](https://img.shields.io/badge/Status-Experimental-orange.svg)](https://github.com/aethermind/aethermind)

[Website](https://aethermind.ai) • 
[Documentation](https://docs.aethermind.ai) • 
[Discord](https://discord.gg/aethermind) • 
[Twitter](https://twitter.com/aethermind) • 
[Blog](https://blog.aethermind.ai)

</div>

> **⚠️ WARNING: This project is not production-ready. It is an unstable experimental proof-of-concept and may contain bugs and/or incomplete features. Use it at your own risk.**

## Overview

Aethermind reimagines how we use AI by connecting browsers into a collaborative network. This framework creates a distributed computing environment where multiple language models work together to generate better responses through structured consensus mechanisms.

This proof-of-concept demonstrates how modern browsers can pool their resources to run AI models locally while also tapping into cloud-based LLMs when needed. By combining distributed computing with collaborative decision-making principles, Aethermind aims to make powerful AI more accessible and responsive.

## Key Features

Aethermind brings several innovative capabilities to browser-based AI:

- **Resource Sharing Network**: Connect multiple browsers to share GPU and CPU resources through WebLLM and WebGPU
- **Multi-Provider Integration**: Query different LLM services (OpenAI, Anthropic, Gemini, Hugging Face) through a single interface
- **Consensus Mechanisms**: Implement Epistemological Decision-Making (EDM) for improved response quality through model collaboration
- **Smart Resource Allocation**: Automatically distribute tasks based on available hardware and network conditions
- **Response Transparency**: View individual model outputs or their consensus-refined versions
- **Interactive Visualization**: Explore the network through real-time Three.js visualization

## Technical Architecture

Aethermind combines several cutting-edge technologies:

### Network Layer
```javascript
// WebRTC-based peer discovery and connection establishment
const initNetwork = async () => {
  // Libp2p provides the foundational P2P protocol stack
  const node = await Libp2p.create({
    modules: {
      transport: [WebRTCDirect],
      peerDiscovery: [Bootstrap, WebRTCStar]
    }
  });
  
  // Establish network connections
  await node.start();
  console.log("Network established and ready");
};
```

### Consensus Engine
```javascript
// EDM-based consensus mechanism
class ConsensusEngine {
  constructor(models) {
    // Each model represents a participant in our decision-making process
    this.participants = models.map(model => ({
      endpoint: model.endpoint,
      weight: model.expertise,
      domain: model.specialization
    }));
  }
  
  async process(query) {
    // Gather responses from each model
    const responses = await Promise.all(
      this.participants.map(participant => 
        this.invokeModel(participant.endpoint, query)
      )
    );
    
    // Check for unanimous agreement (highest confidence)
    if (this.isUnanimous(responses)) {
      return responses[0];
    }
    
    // Fall back to weighted decision mechanism
    return this.weightedConsensus(responses);
  }
}
```

## Getting Started

### Prerequisites

- Modern browser with WebGPU support (Chrome 113+, Edge 113+, or Firefox 119+)
- Node.js 18.0+
- npm or yarn package manager

### Installation

```bash
# Clone the repository
git clone https://github.com/aethermind/aethermind.git

# Navigate to the project directory
cd aethermind

# Install dependencies
npm install

# Start the development server
npm run dev
```

## Usage Examples

### Configuring LLM Endpoints

```javascript
// Configure multiple LLM providers for diverse perspectives
const engine = new ConsensusEngine([
  {
    name: "OpenAI GPT-4",
    endpoint: "https://api.openai.com/v1/completions",
    apiKey: process.env.OPENAI_API_KEY,
    expertise: 0.85,
    specialization: ["general", "coding", "reasoning"]
  },
  {
    name: "Anthropic Claude",
    endpoint: "https://api.anthropic.com/v1/complete",
    apiKey: process.env.ANTHROPIC_API_KEY,
    expertise: 0.90,
    specialization: ["creative", "nuanced", "ethical"]
  },
  // Additional models/endpoints can be configured here
]);
```

### Making Collaborative Decisions

```javascript
// Get either individual responses or consensus-refined output
const response = await engine.process({
  query: "What are the ethical implications of AGI?",
  mode: "consensus", // or "raw" to see individual responses
  consensusThreshold: 0.7,
  requireUnanimity: false
});

console.log(response.consensus);
// Access individual responses if needed
response.responses.forEach(item => {
  console.log(`${item.model}: ${item.response}`);
});
```

## Roadmap

- [ ] Core WebLLM integration with P2P networking
- [ ] Multi-provider API abstraction layer
- [ ] Consensus engine implementation
- [ ] Browser resource monitoring and allocation
- [ ] Three.js network visualization
- [ ] Task scheduling for distributed inference
- [ ] Model partitioning across browsers
- [ ] Security and privacy enhancements
- [ ] Community contribution framework
- [ ] Mobile browser support

## Contributing

Contributions to Aethermind are welcome, though please keep in mind its experimental status. If you'd like to contribute:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

See [`CONTRIBUTING.md`](https://github.com/aethermind/aethermind/blob/main/CONTRIBUTING.md) for more details.

## Research Foundations

Aethermind builds upon recent research in distributed systems, browser-based ML, and collaborative decision-making:

- **Task Scheduling**: Adapts algorithms from "Task Scheduling for Decentralized LLM Serving in Heterogeneous Networks" (UC Berkeley, 2024)
- **In-Browser Inference**: Leverages the WebLLM framework for high-performance transformer execution
- **Consensus Mechanisms**: Implements Epistemological Decision-Making for improved model collaboration
- **Distributed Computing**: Utilizes WebRTC and libp2p for peer-to-peer browser networking

## License

This project is licensed under the MIT License - see the [`LICENSE`](https://github.com/aethermind/aethermind/blob/main/LICENSE) file for details.

## Acknowledgments

Aethermind builds on the work of many innovative projects:

- The WebLLM project for enabling in-browser LLM inference
- UC Berkeley research on decentralized LLM serving
- The WebRTC and WebGPU standards committees
- Collaborative decision-making research and frameworks

---

<div align="center">
  
**Aethermind: Connecting Browsers for Better AI**

</div>
