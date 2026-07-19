{
  "nbformat": 4,
  "nbformat_minor": 0,
  "metadata": {
    "colab": {
      "provenance": [],
      "authorship_tag": "ABX9TyMkx0qhDxsELtMzty1itNN3",
      "include_colab_link": true
    },
    "kernelspec": {
      "name": "python3",
      "display_name": "Python 3"
    },
    "language_info": {
      "name": "python"
    }
  },
  "cells": [
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "view-in-github",
        "colab_type": "text"
      },
      "source": [
        "<a href=\"https://colab.research.google.com/github/anamikamohan82-ops/Quantum-Computing/blob/main/README.md\" target=\"_parent\"><img src=\"https://colab.research.google.com/assets/colab-badge.svg\" alt=\"Open In Colab\"/></a>"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": 5,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 173
        },
        "id": "moEp6AM1eUdv",
        "outputId": "1c8c2c61-9f77-49f6-9c3c-ed04de79f13b"
      },
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Requirement already satisfied: qiskit in /usr/local/lib/python3.12/dist-packages (2.5.0)\n",
            "Requirement already satisfied: numpy<3,>=2.0 in /usr/local/lib/python3.12/dist-packages (from qiskit) (2.0.2)\n",
            "Requirement already satisfied: scipy>=1.14 in /usr/local/lib/python3.12/dist-packages (from qiskit) (1.16.3)\n",
            "Requirement already satisfied: rustworkx>=0.15.0 in /usr/local/lib/python3.12/dist-packages (from qiskit) (0.18.0)\n",
            "Requirement already satisfied: dill>=0.3 in /usr/local/lib/python3.12/dist-packages (from qiskit) (0.3.8)\n",
            "Requirement already satisfied: stevedore>=3.0.0 in /usr/local/lib/python3.12/dist-packages (from qiskit) (5.9.0)\n",
            "Requirement already satisfied: typing-extensions in /usr/local/lib/python3.12/dist-packages (from qiskit) (4.16.0)\n"
          ]
        },
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "[0.70710678+0.j,0.57735027+0.j]"
            ]
          },
          "metadata": {}
        },
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "False"
            ]
          },
          "metadata": {}
        }
      ],
      "source": [
        "!pip install qiskit\n",
        "from qiskit.quantum_info import Statevector\n",
        "from numpy import sqrt\n",
        "u = Statevector([1/sqrt(2),1/sqrt(3)])\n",
        "display(u.draw(\"text\"))\n",
        "display(u.is_valid())\n",
        "\n"
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "from qiskit.quantum_info import Operator\n",
        "Y=Operator([[0,-1.0j],[1.0j,0]])\n",
        "H=Operator([[1/sqrt(2),1/sqrt(2)],[1/sqrt(2),-1/sqrt(2)]])\n",
        "S=Operator([[1,0],[0,1.0j]])\n",
        "T=Operator([[1,0],[0,(1+1.0j)/sqrt(2)]])\n",
        "\n",
        "display(T.draw(\"latex\"))\n",
        "display(S.draw(\"latex\"))\n",
        "display(Y.draw(\"latex\"))\n",
        "display(H.draw(\"latex\"))"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 193
        },
        "id": "OJAjdcUSedi1",
        "outputId": "56c1004e-b644-41be-82ce-b10617ec4272"
      },
      "execution_count": 4,
      "outputs": [
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "<IPython.core.display.Latex object>"
            ],
            "text/latex": "$$\n\n\\begin{bmatrix}\n1 & 0  \\\\\n 0 & \\frac{\\sqrt{2}}{2} + \\frac{\\sqrt{2} i}{2}  \\\\\n \\end{bmatrix}\n$$"
          },
          "metadata": {}
        },
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "<IPython.core.display.Latex object>"
            ],
            "text/latex": "$$\n\n\\begin{bmatrix}\n1 & 0  \\\\\n 0 & i  \\\\\n \\end{bmatrix}\n$$"
          },
          "metadata": {}
        },
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "<IPython.core.display.Latex object>"
            ],
            "text/latex": "$$\n\n\\begin{bmatrix}\n0 & - i  \\\\\n i & 0  \\\\\n \\end{bmatrix}\n$$"
          },
          "metadata": {}
        },
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "<IPython.core.display.Latex object>"
            ],
            "text/latex": "$$\n\n\\begin{bmatrix}\n\\frac{\\sqrt{2}}{2} & \\frac{\\sqrt{2}}{2}  \\\\\n \\frac{\\sqrt{2}}{2} & - \\frac{\\sqrt{2}}{2}  \\\\\n \\end{bmatrix}\n$$"
          },
          "metadata": {}
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "v=Statevector([1,0])\n",
        "v=v.evolve(H)\n",
        "v=v.evolve(T)\n",
        "v=v.evolve(H)\n",
        "v=v.evolve(S)\n",
        "v=v.evolve(Y)\n",
        "display(v.draw(\"latex\"))\n",
        "outcome,state=v.measure()\n",
        "print(f\"Measured: {outcome}\\nPost_measurement state:\")\n",
        "display(state.draw(\"latex\"))"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 96
        },
        "id": "b50aqoHcezgD",
        "outputId": "50e9629c-0a8d-44dc-93be-7b40aaa33d21"
      },
      "execution_count": 6,
      "outputs": [
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "<IPython.core.display.Latex object>"
            ],
            "text/latex": "$$(0.1464466094 - 0.3535533906 i) |0\\rangle+(-0.3535533906 + 0.8535533906 i) |1\\rangle$$"
          },
          "metadata": {}
        },
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Measured: 1\n",
            "Post_measurement state:\n"
          ]
        },
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "<IPython.core.display.Latex object>"
            ],
            "text/latex": "$$(-0.3826834324 + 0.9238795325 i) |1\\rangle$$"
          },
          "metadata": {}
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "from qiskit import QuantumCircuit\n",
        "\n",
        "circuit = QuantumCircuit(1)\n",
        "\n",
        "circuit.h(0)\n",
        "circuit.t(0)\n",
        "circuit.h(0)\n",
        "circuit.s(0)\n",
        "circuit.y(0)\n",
        "\n",
        "display(circuit.draw(output=\"text\"))"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 63
        },
        "id": "7C5T7hOce2yr",
        "outputId": "57e5d188-61d1-4e40-d3e0-c1ee275c09ff"
      },
      "execution_count": 7,
      "outputs": [
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "   ┌───┐┌───┐┌───┐┌───┐┌───┐\n",
              "q: ┤ H ├┤ T ├┤ H ├┤ S ├┤ Y ├\n",
              "   └───┘└───┘└───┘└───┘└───┘"
            ],
            "text/html": [
              "<pre style=\"word-wrap: normal;white-space: pre;background: #fff0;line-height: 1.1;font-family: &quot;Courier New&quot;,Courier,monospace\">   ┌───┐┌───┐┌───┐┌───┐┌───┐\n",
              "q: ┤ H ├┤ T ├┤ H ├┤ S ├┤ Y ├\n",
              "   └───┘└───┘└───┘└───┘└───┘</pre>"
            ]
          },
          "metadata": {}
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "from qiskit import QuantumCircuit\n",
        "\n",
        "circuit = QuantumCircuit(1)\n",
        "\n",
        "circuit.h(0)\n",
        "circuit.t(0)\n",
        "circuit.h(0)\n",
        "circuit.s(0)\n",
        "circuit.y(0)\n",
        "\n",
        "display(circuit.draw(output=\"text\"))\n",
        "display(Operator.from_circuit(circuit).draw(\"latex\"))"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 104
        },
        "id": "3vZvieg9e7qQ",
        "outputId": "225b55c1-752b-4cfc-f553-4d534549ba8d"
      },
      "execution_count": 8,
      "outputs": [
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "   ┌───┐┌───┐┌───┐┌───┐┌───┐\n",
              "q: ┤ H ├┤ T ├┤ H ├┤ S ├┤ Y ├\n",
              "   └───┘└───┘└───┘└───┘└───┘"
            ],
            "text/html": [
              "<pre style=\"word-wrap: normal;white-space: pre;background: #fff0;line-height: 1.1;font-family: &quot;Courier New&quot;,Courier,monospace\">   ┌───┐┌───┐┌───┐┌───┐┌───┐\n",
              "q: ┤ H ├┤ T ├┤ H ├┤ S ├┤ Y ├\n",
              "   └───┘└───┘└───┘└───┘└───┘</pre>"
            ]
          },
          "metadata": {}
        },
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "<IPython.core.display.Latex object>"
            ],
            "text/latex": "$$\n\n\\begin{bmatrix}\n0.1464466094 - 0.3535533906 i & 0.8535533906 + 0.3535533906 i  \\\\\n -0.3535533906 + 0.8535533906 i & 0.3535533906 + 0.1464466094 i  \\\\\n \\end{bmatrix}\n$$"
          },
          "metadata": {}
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "from qiskit.visualization import plot_histogram\n",
        "ket0=Statevector([1,0])\n",
        "v=ket0.evolve(circuit)\n",
        "display(v.draw(\"latex\"))\n",
        "graph=v.sample_counts(1000)\n",
        "display(plot_histogram(graph))\n",
        "outcome,state=v.measure()\n",
        "print(f\"Measured: {outcome}\\nPost_Measured state:\")\n",
        "display(state.draw(\"latex\"))"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 566
        },
        "id": "guFsVDZUfO6b",
        "outputId": "a0f98b69-d648-4379-d566-4e62f1b8e3a2"
      },
      "execution_count": 13,
      "outputs": [
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "<IPython.core.display.Latex object>"
            ],
            "text/latex": "$$(0.1464466094 - 0.3535533906 i) |0\\rangle+(-0.3535533906 + 0.8535533906 i) |1\\rangle$$"
          },
          "metadata": {}
        },
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "<Figure size 640x480 with 1 Axes>"
            ],
            "image/png": "iVBORw0KGgoAAAANSUhEUgAAAnYAAAHWCAYAAAD6oMSKAAAAOnRFWHRTb2Z0d2FyZQBNYXRwbG90bGliIHZlcnNpb24zLjEwLjAsIGh0dHBzOi8vbWF0cGxvdGxpYi5vcmcvlHJYcgAAAAlwSFlzAAAPYQAAD2EBqD+naQAALGtJREFUeJzt3X9YlHW+//HXzDAgKqCigGyg6HZEzIKyDPVUJEdUqrWwPZ7jqpGbuy5aqJm4LXQ0f6Tn0tz2bLmdSttrdVu79pSumeHiD0pRyaQfbpoZhmUoiDJqijAz3z/8OlcjooDCjJ99Pq6r65L3/Zn7fr/hGnrNzT33WNxut1sAAAC47ll93QAAAACuDYIdAACAIQh2AAAAhiDYAQAAGIJgBwAAYAiCHQAAgCEIdgAAAIYg2AEAABgiwNcN+CuXy6XDhw8rJCREFovF1+0AAIB/Um63WydPnlR0dLSs1sufkyPYNeDw4cOKiYnxdRsAAACSpEOHDumGG2647BqCXQNCQkIknf8mhoaG+rgbAADwz8rhcCgmJsaTTS6HYNeAC39+DQ0NJdgBAACfa8ylYbx5AgAAwBAEOwAAAEMQ7AAAAAxBsAMAwABOp1O5ubmKi4tTcHCwevbsqWeffVZut9uz5pFHHpHFYvH6b+jQoZ7tmzdvrrf9wn/FxcW+GAtNxJsnAAAwwIIFC/TSSy/p9ddfV58+ffThhx8qMzNTYWFhevzxxz3rhg4dqmXLlnm+DgoK8vx7wIAB+u6777z2m5ubq4KCAvXr16/lh8BVI9gBAGCAbdu26Sc/+YnS09MlSd27d9ef//xn7dy502tdUFCQoqKiLrmPwMBAr221tbVavXq1Jk+ezM36rxP8KRYAAAMMGDBABQUF+uKLLyRJH3/8sT744AMNGzbMa93mzZsVERGhXr16aeLEiTp27FiD+1yzZo2OHTumzMzMFu0d1w5n7AAAMEBOTo4cDofi4+Nls9nkdDo1d+5cjR492rNm6NCheuihhxQXF6cDBw7o17/+tYYNG6aioiLZbLZ6+3z11VeVlpZ2xU87gP8g2AEAYIBVq1ZpxYoVWrlypfr06aOSkhJlZ2crOjpa48aNkySNGjXKs75v3766+eab1bNnT23evFmDBw/22t8333yj9957T6tWrWrVOXB1CHYAABhg+vTpysnJ8YS3vn376uuvv9b8+fM9we5iPXr0UOfOnfXll1/WC3bLli1TeHi4HnjggRbvHdcO19gBAGCA77//Xlar9//WbTabXC5Xg4/55ptvdOzYMXXt2tWr7na7tWzZMo0dO1Z2u71F+kXL4IwdAAAGuP/++zV37lzFxsaqT58+2r17txYvXqxHH31UknTq1CnNmjVLGRkZioqK0oEDB/TUU0/pxz/+sdLS0rz2tXHjRpWWlurnP/+5L0bBVbC4f3jnQng4HA6FhYWpurpaoaGhvm4HAIDLOnnypHJzc/XWW2/p6NGjio6O1n/8x38oLy9PgYGBOnPmjEaMGKHdu3frxIkTio6O1pAhQ/Tss88qMjLSa1//+Z//qa+//lpbt2710TT4oaZkEoJdAwh2AADAHzQlk3CNHQAAgCEIdgAAAIYg2AEAABiCYAcAAGAIgh0AAIAhCHYAAACGINgBAAAYgmAHAABgCIIdAACAIQh2AAAAhiDYAQAAGIJgBwAAYAiCHQAAgCEIdgAAAIYg2AEAABiCYAcAAGAIgh0AAIAhCHYAAACGINgBAAAYgmAHAABgCIIdAACAIQh2AAAAhgjwdQMAADRW95x3fN0CUM/B59J93YIHZ+wAAAAMQbADAAAwBMEOAADAEAQ7AAAAQxDsAAAADEGwAwAAMATBDgAAwBAEOwAAAEMQ7AAAAAxBsAMAADAEwQ4AAMAQBDsAAABDEOwAAAAMQbADAAAwBMEOAADAEAQ7AAAAQxDsAAAADEGwAwAAMATBDgAAwBAEOwAAAEP4XbBzOp3Kzc1VXFycgoOD1bNnTz377LNyu92eNW63W3l5eeratauCg4OVmpqq/fv3e+2nqqpKo0ePVmhoqDp06KDx48fr1KlTrT0OAABAq/G7YLdgwQK99NJL+p//+R99/vnnWrBggRYuXKjf/e53njULFy7UCy+8oKVLl2rHjh1q166d0tLSdPbsWc+a0aNHa8+ePdqwYYPWrl2rwsJCTZgwwRcjAQAAtAqL+4enwvzAfffdp8jISL366queWkZGhoKDg/WnP/1Jbrdb0dHRmjZtmp588klJUnV1tSIjI7V8+XKNGjVKn3/+uRISElRcXKx+/fpJktavX6/hw4frm2++UXR09BX7cDgcCgsLU3V1tUJDQ1tmWABAk3TPecfXLQD1HHwuvUX335RM4ndn7AYMGKCCggJ98cUXkqSPP/5YH3zwgYYNGyZJKi0tVXl5uVJTUz2PCQsLU//+/VVUVCRJKioqUocOHTyhTpJSU1NltVq1Y8eOVpwGAACg9QT4uoGL5eTkyOFwKD4+XjabTU6nU3PnztXo0aMlSeXl5ZKkyMhIr8dFRkZ6tpWXlysiIsJre0BAgDp16uRZc7GamhrV1NR4vnY4HJKk2tpa1dbWSpKsVqunJ5fL5Vl7oV5XV+d1LaDNZpPVam2wfmG/P+xRkurq6hpVt9vtcrlccjqdnprFYlFAQECD9YZ6ZyZmYiZmuh5mAvxRazyfGsvvgt2qVau0YsUKrVy5Un369FFJSYmys7MVHR2tcePGtdhx58+fr1mzZtWr5+fnq23btpKk2NhYJSUl6ZNPPlFZWZlnTa9evRQfH6+dO3eqoqLCU09MTFS3bt1UWFiokydPeurJycmKiIhQfn6+1w8rJSVFwcHBWrdunVcPw4cP15kzZ7Rp0yZPLSAgQOnp6aqsrPScqZSkkJAQ3XvvvTp06JBKSko89S5dumjAgAHav3+/9u3b56kzEzMxEzNdTzMB/qiln09bt25tdC9+d41dTEyMcnJylJWV5anNmTNHf/rTn7R371599dVX6tmzp3bv3q3ExETPmrvvvluJiYn67W9/q9dee03Tpk3T8ePHPdvr6urUpk0bvfnmm3rwwQfrHfdSZ+xiYmJUWVnp+Xu2v71yNfHVODMxEzMx0+XqN+bmC/A3X80b1qLPp6qqKoWHhzfqGju/e/nz/fffy2r1vvTPZrN5vgFxcXGKiopSQUGBJ9g5HA7t2LFDEydOlHT+leGJEye0a9cu3XbbbZKkjRs3yuVyqX///pc8blBQkIKCgurV7Xa77HZ7vX5sNlu9tQ29mmyofvF+m1O3Wq31vl+XqzfUOzMxU1PrzMRMkm9mAvyNr55Pl1zb6JWt5P7779fcuXMVGxurPn36aPfu3Vq8eLEeffRRSedTcHZ2tubMmaMbb7xRcXFxys3NVXR0tEaMGCFJ6t27t4YOHarHHntMS5cuVW1trSZNmqRRo0Y16h2xAAAA1yO/C3a/+93vlJubq1/96lc6evSooqOj9Ytf/EJ5eXmeNU899ZROnz6tCRMm6MSJExo0aJDWr1+vNm3aeNasWLFCkyZN0uDBg2W1WpWRkaEXXnjBFyMBAAC0Cr+7xs5fcB87APA/3McO/oj72AEAAOCaI9gBAAAYgmAHAABgCIIdAACAIQh2AAAAhiDYAQAAGIJgBwAAYAiCHQAAgCEIdgAAAIYg2AEAABiCYAcAAGAIgh0AAIAhCHYAAACGINgBAAAYgmAHAABgCIIdAACAIQh2AAAAhiDYAQAAGIJgBwAAYAiCHQAAgCEIdgAAAIYg2AEAABiCYAcAAGAIgh0AAIAhCHYAAACGINgBAAAYgmAHAABgCIIdAACAIQh2AAAAhiDYAQAAGIJgBwAAYAiCHQAAgCEIdgAAAIYg2AEAABiCYAcAAGAIgh0AAIAhCHYAAACGINgBAAAYgmAHAABgCIIdAACAIQh2AAAAhiDYAQAAGIJgBwAAYAiCHQAAgCEIdgAAAIYg2AEAABiCYAcAAGAIgh0AAIAhCHYAAACGINgBAAAYgmAHAABgCIIdAACAIQh2AAAAhiDYAQAAGIJgBwAAYAiCHQAAgCEIdgAAAIYg2AEAABiCYAcAAGAIgh0AAIAhCHYAAACGINgBAAAYgmAHAABgCIIdAACAIQh2AAAAhiDYAQAAGIJgBwAAYAiCHQAAgCEIdgAAAIYg2AEAABiCYAcAAGAIgh0AAIAhCHYAAACGINgBAAAYgmAHAABgCIIdAACAIQh2AAAAhiDYAQAAGIJgBwAAYAiCHQAAgCH8Mth9++23+tnPfqbw8HAFBwerb9+++vDDDz3b3W638vLy1LVrVwUHBys1NVX79+/32kdVVZVGjx6t0NBQdejQQePHj9epU6daexQAAIBW43fB7vjx4xo4cKDsdrveffdd/eMf/9CiRYvUsWNHz5qFCxfqhRde0NKlS7Vjxw61a9dOaWlpOnv2rGfN6NGjtWfPHm3YsEFr165VYWGhJkyY4IuRAAAAWoXF7Xa7fd3ED+Xk5Gjr1q16//33L7nd7XYrOjpa06ZN05NPPilJqq6uVmRkpJYvX65Ro0bp888/V0JCgoqLi9WvXz9J0vr16zV8+HB98803io6OvmIfDodDYWFhqq6uVmho6LUbEADQbN1z3vF1C0A9B59Lb9H9NyWTBLRoJ82wZs0apaWl6eGHH9aWLVv0ox/9SL/61a/02GOPSZJKS0tVXl6u1NRUz2PCwsLUv39/FRUVadSoUSoqKlKHDh08oU6SUlNTZbVatWPHDj344IP1jltTU6OamhrP1w6HQ5JUW1ur2tpaSZLVapXNZpPT6ZTL5fKsvVCvq6vTD3OyzWaT1WptsH5hvxcEBJz/cdTV1TWqbrfb5XK55HQ6PTWLxaKAgIAG6w31zkzMxEzMdD3MBPij1ng+NZbfBbuvvvpKL730kqZOnapf//rXKi4u1uOPP67AwECNGzdO5eXlkqTIyEivx0VGRnq2lZeXKyIiwmt7QECAOnXq5Flzsfnz52vWrFn16vn5+Wrbtq0kKTY2VklJSfrkk09UVlbmWdOrVy/Fx8dr586dqqio8NQTExPVrVs3FRYW6uTJk556cnKyIiIilJ+f7/XDSklJUXBwsNatW+fVw/Dhw3XmzBlt2rTJa5709HRVVlaqqKjIUw8JCdG9996rQ4cOqaSkxFPv0qWLBgwYoP3792vfvn2eOjMxEzMx0/U0E+CPWvr5tHXr1kb34nd/ig0MDFS/fv20bds2T+3xxx9XcXGxioqKtG3bNg0cOFCHDx9W165dPWt++tOfymKx6C9/+YvmzZun119/3eubKUkRERGaNWuWJk6cWO+4lzpjFxMTo8rKSs9pT3975Wriq3FmYiZmYqbL1W/MzRfgb76aN6xFn09VVVUKDw+/Pv8U27VrVyUkJHjVevfurb/+9a+SpKioKEnSkSNHvILdkSNHlJiY6Flz9OhRr33U1dWpqqrK8/iLBQUFKSgoqF7dbrfLbrd71Ww2m2w2W721Db2abKh+8X6bU7darbJa678HpqF6Q70zEzM1tc5MzCT5ZibA3/jq+XTJXhq9spUMHDiw3pm2L774Qt26dZMkxcXFKSoqSgUFBZ7tDodDO3bsUHJysqTzp/xPnDihXbt2edZs3LhRLpdL/fv3b4UpAAAAWp/fnbGbMmWKBgwYoHnz5umnP/2pdu7cqZdfflkvv/yypPOnN7OzszVnzhzdeOONiouLU25urqKjozVixAhJ58/wDR06VI899piWLl2q2tpaTZo0SaNGjWrUO2IBAACuR34X7G6//Xa99dZbmjlzpmbPnq24uDgtWbJEo0eP9qx56qmndPr0aU2YMEEnTpzQoEGDtH79erVp08azZsWKFZo0aZIGDx4sq9WqjIwMvfDCC74YCQAAoFX43Zsn/AX3sQMA/8N97OCP/Ok+dn53jR0AAACah2AHAABgCIIdAACAIQh2AAAAhiDYAQAAGIJgBwAAYAiCHQAAgCEIdgAAAIYg2AEAABiCYAcAAGAIgh0AAIAhCHYAAACGINgBAAAYgmAHAABgCIIdAACAIQh2AAAAhiDYAQAAGIJgBwAAYAiCHQAAgCEIdgAAAIYg2AEAABiCYAcAAGAIgh0AAIAhCHYAAACGINgBAAAYotnBrrCwUGVlZZddc+jQIRUWFjb3EAAAAGiCZge7lJQULV++/LJr/vjHPyolJaW5hwAAAEATNDvYud3uK65xuVyyWCzNPQQAAACaoEWvsdu/f7/CwsJa8hAAAAD4/wKasvjRRx/1+vrtt9/WwYMH661zOp2e6+uGDRt2VQ0CAACgcZoU7H54TZ3FYlFJSYlKSkouudZisej222/X888/fzX9AQAAoJGaFOxKS0slnb++rkePHsrOztYTTzxRb53NZlPHjh3Vrl27a9MlAAAArqhJwa5bt26efy9btkxJSUleNQAAAPhOk4LdD40bN+5a9gEAAICr1Oxgd8HOnTtVXFysEydOyOl01ttusViUm5t7tYcBAADAFTQ72FVVVWnEiBHaunXrZe9pR7ADAABoHc0OdlOnTtUHH3yge+65R+PGjdMNN9yggICrPgEIAACAZmp2Elu7dq3uuOMOFRQU8OkSAAAAfqDZnzxx5swZ3XXXXYQ6AAAAP9HsYJeYmHjJT50AAACAbzQ72D3zzDNas2aNtm/ffi37AQAAQDM1+xq78vJypaen6+6779bo0aN16623KjQ09JJrx44d2+wGAQAA0DgW9+XuVXIZVqtVFovF61YnF19v53a7ZbFYLnl/O3/ncDgUFham6urqBgMrAKB1dc95x9ctAPUcfC69RffflEzS7DN2y5Yta+5DAQAA0AL4SDEAAABDNPvNEwAAAPAvzT5jV1ZW1ui1sbGxzT0MAAAAGqnZwa579+6NujmxxWJRXV1dcw8DAACARmp2sBs7duwlg111dbU+/vhjlZaW6u6771b37t2vpj8AAAA0UrOD3fLlyxvc5na7tWjRIi1cuFCvvvpqcw8BAACAJmiRN09YLBY9+eST6tOnj6ZPn94ShwAAAMBFWvRdsf369dPGjRtb8hAAAAD4/1o02B04cIA3TgAAALSSZl9j1xCXy6Vvv/1Wy5cv1+rVqzV48OBrfQgAAABcQrOD3YXPim2I2+1Wx44dtWjRouYeAgAAAE3Q7GB31113XTLYWa1WdezYUbfffrsyMzMVERFxVQ0CAACgcZod7DZv3nwN2wAAAMDV4rNiAQAADHFN3jyxdetWlZSUyOFwKDQ0VImJiRo4cOC12DUAAAAa6aqC3bZt25SZmakvv/xS0vk3TFy47u7GG2/UsmXLlJycfPVdAgAA4IqaHez27NmjIUOG6Pvvv9e//du/KSUlRV27dlV5ebk2bdqk/Px8paWlafv27UpISLiWPQMAAOASmh3sZs+erXPnzmndunUaOnSo17YZM2Zo/fr1euCBBzR79my98cYbV90oAAAALq/Zb57YvHmzRo4cWS/UXTB06FCNHDlSmzZtanZzAAAAaLxmB7vq6mrFxcVddk1cXJyqq6ubewgAAAA0QbODXXR0tLZv337ZNTt27FB0dHRzDwEAAIAmaHawe+CBB7R582bl5ubq7NmzXtvOnj2rZ555Rps2bdJPfvKTq24SAAAAV2Zxu93u5jzw2LFj6t+/v0pLSxUeHq477rhDkZGROnLkiIqLi1VRUaEePXpo586d6tSp07Xuu8U5HA6FhYWpurpaoaGhvm4HACCpe847vm4BqOfgc+ktuv+mZJJmvys2PDxc27dv11NPPaU33nhD69at82xr06aNMjMztWDBgusy1AEAAFyPruoGxZ07d9Zrr72mP/zhD9q7d6/nkyfi4+Nlt9uvVY8AAABohCYHu7lz5+r06dOaNWuWJ7zZ7Xb17dvXs+bcuXN6+umnFRISopycnGvXLQAAABrUpDdP/P3vf1deXp7Cw8Mve0YuMDBQ4eHhevrpp7mPHQAAQCtpUrD74x//qI4dO2rSpElXXJuVlaVOnTpp2bJlzW4OAAAAjdekYLdt2zalpqYqKCjoimuDgoKUmpqqrVu3Nrs5AAAANF6Tgt3hw4fVo0ePRq+Pi4vTd9991+SmAAAA0HRNCnZWq1W1tbWNXl9bWyurtdn3QAYAAEATNCl1RUdH67PPPmv0+s8++0w/+tGPmtwUAAAAmq5Jwe5f//VftXHjRh08ePCKaw8ePKiNGzfqrrvuam5vAAAAaIImBbusrCzV1tZq5MiRqqysbHDdsWPH9PDDD6uurk4TJ0686iYBAABwZU26QfGtt96q7OxsLVmyRAkJCfrlL3+plJQU3XDDDZKkb7/9VgUFBXr55ZdVUVGhqVOn6tZbb22RxgEAAOCtye9sWLRokXJycnT8+HHNnTtXqampio+PV3x8vAYPHqy5c+eqqqpKM2fO1H//939fVXPPPfecLBaLsrOzPbWzZ88qKytL4eHhat++vTIyMnTkyBGvx5WVlSk9PV1t27ZVRESEpk+frrq6uqvqBQAAwN81+SPFLBaL5s2bp/Hjx2vZsmXatm2bysvLJUlRUVEaOHCgHnnkEfXs2fOqGisuLtYf/vAH3XzzzV71KVOm6J133tGbb76psLAwTZo0SQ899JDnfnlOp1Pp6emKiorStm3b9N1332ns2LGy2+2aN2/eVfUEAADgzyxut9vt6yYudurUKd1666168cUXNWfOHCUmJmrJkiWqrq5Wly5dtHLlSo0cOVKStHfvXvXu3VtFRUW688479e677+q+++7T4cOHFRkZKUlaunSpZsyYoYqKCgUGBjaqB4fDobCwMFVXVys0NLTFZgUANF73nHd83QJQz8Hn0lt0/03JJH55k7msrCylp6crNTXVq75r1y7V1tZ61ePj4xUbG6uioiJJUlFRkfr27esJdZKUlpYmh8OhPXv2tM4AAAAAPtDkP8W2tDfeeEMfffSRiouL620rLy9XYGCgOnTo4FWPjIz0/Dm4vLzcK9Rd2H5hW0NqampUU1Pj+drhcEg6f5PlCzdltlqtstlscjqdcrlcnrUX6nV1dfrhCVCbzSar1dpg/eKbPQcEnP9xXHw9YEN1u90ul8slp9PpqVksFgUEBDRYb6h3ZmImZmKm62EmwB+1xvOpsfwq2B06dEhPPPGENmzYoDZt2rTqsefPn69Zs2bVq+fn56tt27aSpNjYWCUlJemTTz5RWVmZZ02vXr0UHx+vnTt3qqKiwlNPTExUt27dVFhYqJMnT3rqycnJioiIUH5+vtcPKyUlRcHBwVq3bp1XD8OHD9eZM2e0adMmTy0gIEDp6emqrKz0nK2UpJCQEN177706dOiQSkpKPPUuXbpowIAB2r9/v/bt2+epMxMzMRMzXU8zAf6opZ9PF95H0Bh+dY3d22+/rQcffFA2m81Tczqdslgsslqteu+995Samqrjx497nbXr1q2bsrOzNWXKFOXl5WnNmjVe3+DS0lL16NFDH330kZKSki557EudsYuJiVFlZaXn79n+9srVxFfjzMRMzMRMl6vfmJsvwN98NW9Yiz6fqqqqFB4e3qhr7Pzq5c/gwYP16aefetUyMzMVHx+vGTNmKCYmRna7XQUFBcrIyJAk7du3T2VlZUpOTpZ0/lXh3LlzdfToUUVEREiSNmzYoNDQUCUkJDR47KCgIAUFBdWr2+122e12r5rNZvMKnxc09GqyofrF+21O3Wq1XvLzeBuqN9Q7MzFTU+vMxEySb2YC/I2vnk+XXNvola0gJCREN910k1etXbt2Cg8P99THjx+vqVOnqlOnTgoNDdXkyZOVnJysO++8U5I0ZMgQJSQkaMyYMVq4cKHKy8v1m9/8RllZWZcMbgAAAKbwq2DXGM8//7ysVqsyMjJUU1OjtLQ0vfjii57tNptNa9eu1cSJE5WcnKx27dpp3Lhxmj17tg+7BgAAaHl+dY2dP+E+dgDgf7iPHfwR97EDAADANUewAwAAMATBDgAAwBAEOwAAAEMQ7AAAAAxBsAMAADAEwQ4AAMAQBDsAAABDEOwAAAAMQbADAAAwBMEOAADAEAQ7AAAAQxDsAAAADEGwAwAAMATBDgAAwBAEOwAAAEMQ7AAAAAxBsAMAADAEwQ4AAMAQBDsAAABDEOwAAAAMQbADAAAwBMEOAADAEAQ7AAAAQxDsAAAADEGwAwAAMATBDgAAwBAEOwAAAEMQ7AAAAAxBsAMAADAEwQ4AAMAQBDsAAABDEOwAAAAMQbADAAAwBMEOAADAEAQ7AAAAQxDsAAAADEGwAwAAMATBDgAAwBAEOwAAAEMQ7AAAAAxBsAMAADAEwQ4AAMAQBDsAAABDEOwAAAAMQbADAAAwBMEOAADAEAQ7AAAAQxDsAAAADEGwAwAAMATBDgAAwBAEOwAAAEMQ7AAAAAxBsAMAADAEwQ4AAMAQBDsAAABDEOwAAAAMQbADAAAwBMEOAADAEAQ7AAAAQxDsAAAADEGwAwAAMATBDgAAwBAEOwAAAEMQ7AAAAAxBsAMAADAEwQ4AAMAQBDsAAABDEOwAAAAMQbADAAAwBMEOAADAEAQ7AAAAQxDsAAAADEGwAwAAMATBDgAAwBAEOwAAAEMQ7AAAAAxBsAMAADAEwQ4AAMAQBDsAAABD+F2wmz9/vm6//XaFhIQoIiJCI0aM0L59+7zWnD17VllZWQoPD1f79u2VkZGhI0eOeK0pKytTenq62rZtq4iICE2fPl11dXWtOQoAAECr8rtgt2XLFmVlZWn79u3asGGDamtrNWTIEJ0+fdqzZsqUKfrb3/6mN998U1u2bNHhw4f10EMPebY7nU6lp6fr3Llz2rZtm15//XUtX75ceXl5vhgJAACgVVjcbrfb101cTkVFhSIiIrRlyxbdddddqq6uVpcuXbRy5UqNHDlSkrR371717t1bRUVFuvPOO/Xuu+/qvvvu0+HDhxUZGSlJWrp0qWbMmKGKigoFBgZe8bgOh0NhYWGqrq5WaGhoi84IAGic7jnv+LoFoJ6Dz6W36P6bkkn87ozdxaqrqyVJnTp1kiTt2rVLtbW1Sk1N9ayJj49XbGysioqKJElFRUXq27evJ9RJUlpamhwOh/bs2dOK3QMAALSeAF83cDkul0vZ2dkaOHCgbrrpJklSeXm5AgMD1aFDB6+1kZGRKi8v96z5Yai7sP3CtkupqalRTU2N52uHwyFJqq2tVW1trSTJarXKZrPJ6XTK5XJ51l6o19XV6YcnQG02m6xWa4P1C/u9ICDg/I/j4msBG6rb7Xa5XC45nU5PzWKxKCAgoMF6Q70zEzMxEzNdDzMB/qg1nk+N5dfBLisrS5999pk++OCDFj/W/PnzNWvWrHr1/Px8tW3bVpIUGxurpKQkffLJJyorK/Os6dWrl+Lj47Vz505VVFR46omJierWrZsKCwt18uRJTz05OVkRERHKz8/3+mGlpKQoODhY69at8+ph+PDhOnPmjDZt2uSpBQQEKD09XZWVlZ4zlZIUEhKie++9V4cOHVJJSYmn3qVLFw0YMED79+/3ejMKMzETMzHT9TQT4I9a+vm0devWRvfit9fYTZo0SatXr1ZhYaHi4uI89Y0bN2rw4ME6fvy411m7bt26KTs7W1OmTFFeXp7WrFnj9U0uLS1Vjx499NFHHykpKane8S51xi4mJkaVlZWev2f72ytXE1+NMxMzMRMzXa5+Y26+AH/z1bxhLfp8qqqqUnh4eKOusfO7lz9ut1uTJ0/WW2+9pc2bN3uFOkm67bbbZLfbVVBQoIyMDEnSvn37VFZWpuTkZEnnXxnOnTtXR48eVUREhCRpw4YNCg0NVUJCwiWPGxQUpKCgoHp1u90uu93uVbPZbLLZbPXWNvRqsqH6xfttTt1qtcpqrX+pZEP1hnpnJmZqap2ZmEnyzUyAv/HV8+mSaxu9spVkZWVp5cqVWr16tUJCQjzXxIWFhSk4OFhhYWEaP368pk6dqk6dOik0NFSTJ09WcnKy7rzzTknSkCFDlJCQoDFjxmjhwoUqLy/Xb37zG2VlZV0yvAEAAJjA74LdSy+9JEm65557vOrLli3TI488Ikl6/vnnZbValZGRoZqaGqWlpenFF1/0rLXZbFq7dq0mTpyo5ORktWvXTuPGjdPs2bNbawwAAIBW57fX2Pka97EDAP/Dfezgj7iPHQAAAK45gh0AAIAhCHYAAACGINjBbxUWFur+++9XdHS0LBaL3n777QbX/vKXv5TFYtGSJUu86g888IBiY2PVpk0bde3aVWPGjNHhw4dbtnEAAHyEYAe/dfr0ad1yyy36/e9/f9l1b731lrZv367o6Oh621JSUrRq1Srt27dPf/3rX3XgwAGNHDmypVoGAMCn/O52J8AFw4YN07Bhwy675ttvv9XkyZP13nvvKT29/ruSpkyZ4vl3t27dlJOToxEjRqi2tpYbnwIAjMMZO1y3XC6XxowZo+nTp6tPnz5XXF9VVaUVK1ZowIABhDoAgJEIdrhuLViwQAEBAXr88ccvu27GjBlq166dwsPDVVZWptWrV7dShwAAtC6CHa5Lu3bt0m9/+1stX75cFovlsmunT5+u3bt3Kz8/XzabTWPHjhX35QYAmIhr7HBdev/993X06FHFxsZ6ak6nU9OmTdOSJUt08OBBT71z587q3Lmz/uVf/kW9e/dWTEyMtm/fruTkZB90DgBAyyHY4bo0ZswYpaametXS0tI0ZswYZWZmNvg4l8slSaqpqWnR/gAA8AWCHfzWqVOn9OWXX3q+Li0tVUlJiTp16qTY2FiFh4d7rbfb7YqKilKvXr0kSTt27FBxcbEGDRqkjh076sCBA8rNzVXPnj05WwcAMBLX2MFvffjhh0pKSlJSUpIkaerUqUpKSlJeXl6jHt+2bVv93//9nwYPHqxevXpp/Pjxuvnmm7VlyxYFBQW1ZOsAAPgEZ+zgt+65554mvcnhh9fVSVLfvn21cePGa9wVAAD+izN2AAAAhiDYAQAAGIJgBwAAYAiCHQAAgCEIdgAAAIbgXbE+1j3nHV+3ANRz8Ll0X7cAAGgGztgBAAAYgmAHAABgCIIdAACAIQh2AAAAhiDYAQAAGIJgBwAAYAiCHQAAgCEIdgAAAIYg2AEAABiCYAcAAGAIgh0AAIAhCHYAAACGINgBAAAYgmAHAABgCIIdAACAIQh2AAAAhiDYAQAAGIJgBwAAYAiCHQAAgCEIdgAAAIYg2AEAABiCYAcAAGAIgh0AAIAhCHYAAACGINgBAAAYgmAHAABgCIIdAACAIQh2AAAAhiDYAQAAGIJgBwAAYAiCHQAAgCEIdgAAAIYg2AEAABiCYAcAAGAIgh0AAIAhCHYAAACGINgBAAAYgmAHAABgCIIdAACAIQh2AAAAhiDYAQAAGIJgBwAAYAiCHQAAgCEIdgAAAIYg2AEAABiCYAcAAGAIgh0AAIAhCHYAAACGINgBAAAYgmAHAABgCIIdAACAIQh2AAAAhiDYAQAAGIJgBwAAYAiCHQAAgCEIdgAAAIYg2AEAABiCYAcAAGAIgh0AAIAhCHYAAACGMDrY/f73v1f37t3Vpk0b9e/fXzt37vR1SwAAAC3G2GD3l7/8RVOnTtUzzzyjjz76SLfccovS0tJ09OhRX7cGAADQIowNdosXL9Zjjz2mzMxMJSQkaOnSpWrbtq1ee+01X7cGAADQIgJ83UBLOHfunHbt2qWZM2d6alarVampqSoqKrrkY2pqalRTU+P5urq6WpJUVVWl2tpazz5sNpucTqdcLpfXvm02m+rq6uR2uz11m80mq9XaYL22tlaumu+vzdDANXTs2DFJUkDA+V8RdXV1XtvtdrtcLpecTqenZrFYFBAQ0GC9oefNtXw+/VBDvTPT9T0TvzPhj06cONGiz6eqqipJ8trWECODXWVlpZxOpyIjI73qkZGR2rt37yUfM3/+fM2aNatePS4urkV6BPxZ5yW+7gAArh8dl7TOcU6ePKmwsLDLrjEy2DXHzJkzNXXqVM/XLpdLVVVVCg8Pl8Vi8WFnaAyHw6GYmBgdOnRIoaGhvm4HAPwavzOvL263WydPnlR0dPQV1xoZ7Dp37iybzaYjR4541Y8cOaKoqKhLPiYoKEhBQUFetQ4dOrRUi2ghoaGh/JICgEbid+b140pn6i4w8s0TgYGBuu2221RQUOCpuVwuFRQUKDk52YedAQAAtBwjz9hJ0tSpUzVu3Dj169dPd9xxh5YsWaLTp08rMzPT160BAAC0CGOD3b//+7+roqJCeXl5Ki8vV2JiotavX1/vDRUwQ1BQkJ555pl6f04HANTH70xzWdyNee8sAAAA/J6R19gBAAD8MyLYAQAAGIJgBwAAYAiCHQAAgCEIdgAAAIYg2ME4DofD68OYAQD4Z2Hsfezwz6WyslJvvPGGFi1apM6dOyssLEyDBg3Sz372M/Xs2ZPP+wUA/FPgPnYwwqOPPqqPP/5Yw4YNU2hoqCorK/X555/r0KFDio+P13/9138pPj7e120CgN84c+aMgoODfd0GrjGCHa57brdb7du31zvvvKN77rnHUztw4IDef/99vfLKK6qurtaqVauUkJDg22YBwE9MmzZNAwcO1G233aaoqKhLfgrFsWPHFB4e7oPu0FxcY4fr3j/+8Q/16NFD7du399QsFot+/OMfKzMzU3//+99ls9m0atUqH3YJAP5j5cqVev755zVq1CilpKRo5syZ2rRpk44ePaq6ujpJ0unTpzV+/Hh9+umnPu4WTcEZO1z3zpw5o/vuu091dXVavny5unfvXu+ausWLF2vlypX68MMPfdQlAPiPn//85woMDNSTTz6pP//5z3rllVf09ddfKykpSQ8//LDS0tJUUlKiCRMmqLa21tftogk4Y4frXnBwsObMmSOHw6ExY8Zo5cqV+u6773TmzBlJUk1NjbZv365evXr5uFMA8L26ujr16NFDHTp0UI8ePfT000+rtLRUJSUl6tevn5577jnddddd+sUvfqExY8b4ul00EWfsYIxPP/1Uzz77rP72t7+pffv2GjRokKKiovTee++pc+fOeuWVV3TzzTf7uk0A8LkTJ07oyJEj6tWrl86dOye73e71l44VK1ZozJgx2r17t2655RYfdoqmItjBOEePHtXatWv19ttvKzg4WDfddJNGjhyp3r17+7o1APBbLpdLbrdbNptN//u//6snnnhC33//va/bQhMR7GA0l8slq5UrDgCgKRYvXiyn06np06f7uhU0EcEOAAB4qa2tlc1m44XxdYhgBwAAYAiiOAAAgCEIdgAAAIYg2AEAABiCYAcAAGAIgh0AAIAhCHYAAACGINgBAAAYgmAHAABgCIIdAACAIf4fsqjPTY5sybsAAAAASUVORK5CYII=\n"
          },
          "metadata": {}
        },
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Measured: 0\n",
            "Post_Measured state:\n"
          ]
        },
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "<IPython.core.display.Latex object>"
            ],
            "text/latex": "$$(0.3826834324 - 0.9238795325 i) |0\\rangle$$"
          },
          "metadata": {}
        }
      ]
    }
  ]
}