# AI_MohdGufranulHaque
AI Educational Video Generator 📚🎬
Final Year Project - BE Computer Engineering
A system that automatically creates educational videos using AI and animation
🎯 Problem Statement
Students often struggle to find quality visual explanations for complex topics. This system solves that by:

Taking a concept request from students
Automatically generating educational slides and scripts using AI
Creating animated videos with Manim
Supporting different domains like DSA, GIS, and Space Technology

🏗️ System Architecture

🔧 Core Components
1. Knowledge Graph
What it does: Stores educational concepts and their relationships
Technology: Neo4j (for complex relationships) or JSON (for prototype)
Why this choice: Need to track prerequisites like "arrays" → "sorting" → "quicksort"
2. AI Content Generator
What it does: Creates slides and narration scripts
Technology: OpenAI API or local models
Why this choice: OpenAI gives better quality, local models save cost
3. Video Renderer
What it does: Converts content to animated videos
Technology: Manim (Mathematical Animation Engine)
Why this choice: Professional quality animations, especially good for math/CS concepts

🔄 How It Works
python# Main Algorithm
def generate_educational_video(concept, domain):
    Step 1: Get concept data
    concept_data = knowledge_graph.retrieve(concept, domain)
    
     Step 2: Generate content with AI
    slides = ai_generator.create_slides(concept_data)
    script = ai_generator.create_narration(concept_data)
    
     Step 3: Create video with Manim
    video = manim_renderer.create_video(slides, script, domain)
    
     Step 4: Save and return
    return save_video(video)
Detailed Process Flow

Student Query → System checks if concept exists
Content Retrieval → Get concept info from knowledge graph
AI Generation → Create educational slides and script
Video Creation → Use Manim to animate the content
Delivery → Serve video to student

🎨 Domain-Specific Features
Data Structures & Algorithms (DSA)

Algorithm step-by-step visualization
Code execution animation
Complexity analysis charts
Interactive pseudocode

Geographic Information Systems (GIS)

Map-based explanations
Spatial data visualization
Coordinate system demos
Real-world location examples

Space Technology

Orbital mechanics simulation
3D space visualizations
Mathematical formula animations
Mission planning examples

💻 Technology Stack
Backend: Python with FastAPI
Database: Neo4j for relationships, Redis for caching
AI: OpenAI GPT-4 API
Animation: Manim Community Edition
Frontend: Simple React.js interface
Deployment: Docker containers

🏃‍♂️ Quick Start
bash# Clone the project
git clone https://github.com/gufranulhaque/AI_MohdGufranulHaque
cd ai-video-generator

Install dependencies
pip install -r requirements.txt

Set up environment
cp .env.example .env
# Add your OpenAI API key to .env

Run the system
python app/main.py


📊 Trade-offs Made
DecisionOption AOption BChosenWhy?FrameworkFlaskFastAPIFastAPIBetter for async AI callsDatabaseJSON filesNeo4jNeo4jBetter for concept relationshipsAI ServiceLocal modelOpenAI APIOpenAI APIHigher quality outputAnimationWeb-basedManimManimProfessional educational videos
🎯 Key Challenges Solved

Content Quality: Using AI to ensure educational accuracy
Domain Adaptation: Different visualization styles for different subjects
Performance: Async processing for video generation
Scalability: Microservice architecture for handling multiple requests

📈 Expected Results

Video Generation Time: Under 5 minutes per concept
Content Quality: 90%+ educational accuracy (based on expert review)
User Engagement: Students watch 80%+ of generated videos
System Performance: Handle 50+ concurrent users

🚀 Future Improvements

Voice Synthesis: Add AI-generated voice narration
Interactive Elements: Clickable video components
Mobile App: Native iOS/Android apps
Multi-language: Support for regional languages
Personalization: Adapt content based on student's learning level

🔍 Implementation Details
Sample Code Structure
ai-video-generator/
├── app/
│   ├── main.py              # FastAPI app
│   ├── knowledge_graph.py   # Concept storage
│   ├── ai_generator.py      # Content creation
│   └── manim_scenes.py      # Video rendering
├── data/
│   ├── concepts.json        # Sample concepts
│   └── templates/           # Content templates
├── tests/
│   └── test_basic.py        # Basic tests
├── docker-compose.yml       # Local setup
└── requirements.txt         # Dependencies

Key Algorithms
Concept Retrieval:
pythondef get_learning_path(start_concept, target_concept):
     Find shortest path in concept graph
     Returns: [prerequisite_concepts] + [target_concept]
    pass
Content Generation:
pythondef generate_slides(concept_data, domain):
     Create domain-specific slide templates
     Add concept-specific content
     Return structured slide data
    pass
Video Rendering:
pythondef create_manim_scene(slides, domain):
     Choose domain-specific animations
     Apply slide content to animations
     Render final video
    pass
📝 Testing Strategy

Unit Tests: Test individual components
Integration Tests: Test full pipeline
User Testing: Get feedback from fellow students
Performance Tests: Ensure system can handle load

🎓 Learning Outcomes
This project helped me learn:

System Design: How to architect a complex application
AI Integration: Working with modern AI APIs
Video Processing: Understanding multimedia pipelines
Database Design: Graph databases and relationships
Web Development: Building scalable web applications
