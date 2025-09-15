# Project File Structure

```
ai-educational-video-generator/
│
├── README.md                    # Main project documentation
├── requirements.txt             # Python dependencies
├── .env.example                # Environment variables template
├── .gitignore                  # Git ignore file
├── docker-compose.yml          # Local development setup
│
├── app/                        # Main application code
│   ├── main.py                 # FastAPI main application
│   ├── config.py               # Configuration settings
│   ├── knowledge_graph.py      # Concept storage and retrieval
│   ├── ai_generator.py         # AI content generation
│   ├── manim_scenes.py         # Video rendering with Manim
│   └── utils.py                # Helper functions
│
├── data/                       # Data and knowledge base
│   ├── concepts/               # Educational concepts
│   │   ├── dsa_concepts.json   # Data Structures & Algorithms
│   │   ├── gis_concepts.json   # Geographic Information Systems
│   │   └── space_concepts.json # Space Technology
│   └── templates/              # Content templates
│       ├── slide_templates.py
│       └── script_templates.py
│
├── manim_animations/           # Animation scenes
│   ├── dsa_scenes.py          # DSA-specific animations
│   ├── gis_scenes.py          # GIS-specific animations
│   └── space_scenes.py        # Space Tech animations
│
├── static/                     # Static files
│   ├── css/
│   │   └── style.css
│   ├── js/
│   │   └── app.js
│   └── images/
│
├── templates/                  # HTML templates
│   ├── index.html             # Main interface
│   ├── generate.html          # Video generation page
│   └── results.html           # Results display
│
├── tests/                      # Test files
│   ├── test_knowledge_graph.py
│   ├── test_ai_generator.py
│   ├── test_manim_scenes.py
│   └── test_integration.py
│
├── outputs/                    # Generated content
│   ├── videos/                # Generated videos
│   ├── slides/                # Generated slides
│   └── scripts/               # Generated scripts
│
├── docs/                      # Documentation
│   ├── ARCHITECTURE.md        # System architecture
│   ├── API_DOCS.md           # API documentation
│   └── USER_GUIDE.md         # How to use the system
│
└── scripts/                   # Utility scripts
    ├── setup_db.py           # Database initialization
    ├── sample_data.py        # Load sample concepts
    └── test_generation.py    # Test video generation
```

## Key Files Explanation

### Core Application Files

**`app/main.py`** - Main FastAPI application
```python
from fastapi import FastAPI
from knowledge_graph import KnowledgeGraph
from ai_generator import AIGenerator
from manim_scenes import VideoRenderer

app = FastAPI(title="AI Educational Video Generator")
kg = KnowledgeGraph()
ai_gen = AIGenerator()
renderer = VideoRenderer()

@app.post("/generate")
async def generate_video(concept: str, domain: str):
    # Main video generation endpoint
    pass
```

**`app/knowledge_graph.py`** - Concept storage
```python
class KnowledgeGraph:
    def __init__(self):
        self.concepts = self.load_concepts()
    
    def get_concept(self, concept_id, domain):
        # Retrieve concept data
        pass
    
    def get_prerequisites(self, concept_id):
        # Get prerequisite concepts
        pass
```

**`app/ai_generator.py`** - AI content creation
```python
class AIGenerator:
    def __init__(self):
        self.openai_client = OpenAI(api_key=os.getenv("OPENAI_KEY"))
    
    def generate_slides(self, concept_data):
        # Create educational slides
        pass
    
    def generate_script(self, concept_data):
        # Create narration script
        pass
```

### Data Files

**`data/concepts/dsa_concepts.json`** - Sample concept data
```json
{
    "binary_search": {
        "title": "Binary Search Algorithm",
        "description": "Efficient search algorithm for sorted arrays",
        "difficulty": "intermediate",
        "prerequisites": ["arrays", "sorting"],
        "key_points": [
            "Divide and conquer approach",
            "O(log n) time complexity",
            "Requires sorted input"
        ],
        "examples": ["Finding element in array", "First/last occurrence"]
    }
}
```

### Animation Files

**`manim_animations/dsa_scenes.py`** - Algorithm animations
```python
from manim import *

class BinarySearchScene(Scene):
    def construct(self):
        # Create binary search visualization
        array = [1, 3, 5, 7, 9, 11, 13]
        target = 7
        
        # Animate search process
        pass
```

### Configuration Files

**`requirements.txt`** - Dependencies
```
fastapi==0.104.1
uvicorn==0.24.0
openai==1.3.0
manim==0.18.0
neo4j==5.15.0
redis==5.0.0
python-multipart==0.0.6
jinja2==3.1.2
```

**`docker-compose.yml`** - Local setup
```yaml
version: '3.8'
services:
  app:
    build: .
    ports:
      - "8000:8000"
    environment:
      - OPENAI_API_KEY=${OPENAI_API_KEY}
    volumes:
      - ./outputs:/app/outputs
  
  redis:
    image: redis:7-alpine
    ports:
      - "6379:6379"
```

This structure is realistic for a final year engineering project - comprehensive but not overwhelming, showing good software engineering practices without being overly complex.
