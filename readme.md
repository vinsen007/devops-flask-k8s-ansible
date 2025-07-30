📄 README.md

# 🚀 Flask Web App Deployment on Kubernetes via Ansible

This project demonstrates how to automate the end-to-end deployment of a Dockerized Flask web application on a local Kubernetes cluster using Ansible. All components — Docker image building, container orchestration, and Ansible playbooks — are configured manually from scratch, ensuring transparency and learning.

---

## 📦 Tech Stack

- Python 3 + Flask
- Docker (Manually Built Image)
- Kubernetes via Minikube (running in Docker Desktop)
- Ansible (running in WSL Ubuntu)
- No DockerHub or pre-built images used

---

## 🧱 Project Structure

flask-k8s-ansible-project/
├── app/
│ ├── app.py # Flask app
│ └── requirements.txt # Python dependencies
├── Dockerfile # Docker image definition
├── k8s/
│ ├── deployment.yaml # Kubernetes Deployment
│ └── service.yaml # Kubernetes Service (NodePort)
├── ansible/
│ ├── inventory.ini # Ansible inventory (localhost)
│ └── deploy.yml # Playbook to build, tag, and apply
└── README.md

yaml
Copy
Edit

---

## ⚙️ Prerequisites

Ensure the following are installed and configured:

✅ On Windows Host:
- Docker Desktop with Kubernetes enabled
- ~/.kube/config configured correctly

✅ Inside WSL Ubuntu:
- Docker CLI installed and mapped to Docker Desktop daemon
- Ansible installed
- kubectl configured (copy kube config from Windows)

```bash
mkdir -p ~/.kube
cp /mnt/c/Users/<YOUR_USERNAME>/.kube/config ~/.kube/config
🛠️ Setup Steps
Start Minikube in Docker mode:

bash
Copy
Edit
minikube start --driver=docker
Clone this repo inside WSL:

bash
Copy
Edit
git clone <your-repo-url>
cd flask-k8s-ansible-project
Run the Ansible playbook:

bash
Copy
Edit
ansible-playbook -i ansible/inventory.ini ansible/deploy.yml
🌐 Access the App
Get the NodePort service and visit the Flask app in the browser:

bash
Copy
Edit
kubectl get svc
If the NodePort is 30007 and Minikube IP is 127.0.0.1:

arduino
Copy
Edit
http://localhost:30007
📎 Notes
All Docker builds are done locally — no image registry is used.

Kubernetes manifests are minimal for clarity and education.

This setup is perfect for local DevOps testing and experimentation.

🧑‍💻 Author
Vinayak sen | DevOps Practitioner
RHCSA Certified | Based in Jaipur

