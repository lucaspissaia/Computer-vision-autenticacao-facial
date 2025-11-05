# 🚀 Autenticação Facial com Detecção de Vivacidade (Computer Vision)

Este repositório contém um projeto de Computer Vision desenvolvido para o **MBA em Data Science & AI da FIAP (10DTSR)**.

O objetivo foi prototipar um sistema de autenticação facial seguro (Anti-Spoofing) para uma fintech fictícia (Quantum Finance). A solução combina duas técnicas principais:

1.  **Identificação Facial:** Verifica *se* o rosto no vídeo é o do cliente cadastrado.
2.  **Detecção de Vivacidade (Liveness Detection):** Verifica *se* o rosto é de uma pessoa real e presente, e não uma foto ou vídeo (ataque de *spoofing*).

**Link da Apresentação em Vídeo:** [https://youtu.be/ASXEqmySHoM](https://youtu.be/ASXEqmySHoM)

---

## 🛠️ Metodologia e Ferramentas

O projeto foi desenvolvido em um *notebook* (Google Colab) e estruturado nas seguintes etapas:

### 1. Detecção de Rosto (Face Detection)
* **O que faz:** Localiza um rosto humano nos *frames* do vídeo.
* **Ferramenta:** `MediaPipe Face Detection`.

### 2. Identificação Facial (Facial Identification)
* **O que faz:** Compara o rosto detectado com uma imagem de referência do cliente.
* **Como:**
    1.  Uma "assinatura facial" (um *embedding* numérico) é gerada a partir dos *landmarks* faciais da foto de referência usando `MediaPipe Face Mesh`.
    2.  O mesmo processo é feito para o rosto detectado no vídeo.
    3.  Calculamos a distância Euclidiana entre as duas assinaturas. Se a distância for baixa, consideramos um *match*.
* **Ferramentas:** `MediaPipe Face Mesh`, `NumPy`.

### 3. Detecção de Vivacidade (Liveness Detection)
* **O que faz:** Confirma que o rosto identificado é de uma pessoa real, analisando movimentos naturais.
* **Como:** O sistema monitora os *landmarks* dos olhos (índices 145 e 159) ao longo dos *frames* para detectar piscadas (uma rápida diminuição e aumento da distância entre as pálpebras).
* **Ferramentas:** `MediaPipe Face Mesh` (com `refine_landmarks=True`), `OpenCV`, `NumPy`.

---

## 💻 Stack Tecnológica

* **Linguagem:** Python
* **Bibliotecas de CV/Processamento:** OpenCV (`cv2`), MediaPipe (`mp.solutions.face_detection`, `mp.solutions.face_mesh`)
* **Análise Numérica:** NumPy
* **Ambiente:** Google Colab / Jupyter Notebook

## 👥 Autores

* Erika Koyanagui
* Fabio Asnis Campos da Silva
* Lucas Huber Pissaia
* Matheus Raeski
