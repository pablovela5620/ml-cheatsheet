.. _activation_functions:

====================
Activation Functions
====================

.. contents:: :local:



ELU
===

Be the first to `contribute! <https://github.com/bfortuner/ml-cheatsheet>`__


.. _activation_relu:

ReLU
====

A recent invention which stands for Rectified Linear Units. The formula is deceptively simple: :math:`max(0,z)`. Despite its name and appearance, it’s not linear and provides the same benefits as Sigmoid but with better performance.

+-------------------------------------------------------+------------------------------------------------------+
| Function                                              | Derivative                                           |
+-------------------------------------------------------+------------------------------------------------------+
| .. math::                                             | .. math::                                            |
|      R(z) = \begin{Bmatrix} z & z > 0 \\              |       R'(z) = \begin{Bmatrix} 1 & z>0 \\             |
|       0 & z <= 0 \end{Bmatrix}                        |       0 & z<0 \end{Bmatrix}                          |
+-------------------------------------------------------+------------------------------------------------------+
| .. image:: images/relu.png                            | .. image:: images/relu_prime.png                     |
|       :align: center                                  |      :align: center                                  |
|       :width: 256 px                                  |      :width: 256 px                                  |
|       :height: 256 px                                 |      :height: 256 px                                 |
+-------------------------------------------------------+------------------------------------------------------+
| .. literalinclude:: ../code/activation_functions.py   | .. literalinclude:: ../code/activation_functions.py  |
|       :pyobject: relu                                 |      :pyobject: relu_prime                           |
+-------------------------------------------------------+------------------------------------------------------+

.. quick create tables with tablesgenerator.com/text_tables and import our premade template in figures/

.. rubric:: Pros

- Faster convergence of stochastic gradient descent v.s. sigmoid/tanh
- Simpler operation compared to sigmoid/tanh activations
- Typically used as hidden layer activation function in neural networks

.. rubric:: Cons

- Can result in dead neurons (neurons that never activate across entire training set) if improper learning rate is used

.. rubric:: Further reading

- `Deep Sparse Rectifier Neural Networks <http://proceedings.mlr.press/v15/glorot11a/glorot11a.pdf>`_ Glorot et al., (2011)
- `Yes You Should Understand Backprop <https://medium.com/@karpathy/yes-you-should-understand-backprop-e2f06eab496b>`_, Karpathy (2016)


.. _activation_leakyrelu:

LeakyReLU
=========

LeakyRelu is a variant of ReLU. Instead of being 0 when :math:`z < 0`, a leaky ReLU allows a small, non-zero, constant gradient :math:`\alpha` (Normally, :math:`\alpha = 0.01`). However, the consistency of the benefit across tasks is presently unclear. [1]_

+-------------------------------------------------------+------------------------------------------------------+
| Function                                              | Derivative                                           |
+-------------------------------------------------------+------------------------------------------------------+
| .. math::                                             | .. math::                                            |
|      R(z) = \begin{Bmatrix} z & z > 0 \\              |       R'(z) = \begin{Bmatrix} 1 & z>0 \\             |
|       \alpha z & z <= 0 \end{Bmatrix}                 |       \alpha & z<0 \end{Bmatrix}                     |
+-------------------------------------------------------+------------------------------------------------------+
| .. image:: images/leakyrelu.png                       | .. image:: images/leakyrelu_prime.png                |
|       :align: center                                  |      :align: center                                  |
|       :width: 256 px                                  |      :width: 256 px                                  |
|       :height: 256 px                                 |      :height: 256 px                                 |
+-------------------------------------------------------+------------------------------------------------------+
| .. literalinclude:: ../code/activation_functions.py   | .. literalinclude:: ../code/activation_functions.py  |
|       :pyobject: leakyrelu                            |      :pyobject: leakyrelu_prime                      |
+-------------------------------------------------------+------------------------------------------------------+

.. quick create tables with tablesgenerator.com/text_tables and import our premade template in figures/



.. rubric:: Pros

- Similar benefits to RELU function
- Attempts to fix dying RELU problem by having a small negative slope when x < 0

.. rubric:: Cons

- Results not always consistent in helping non-firing neurons

.. rubric:: Further reading

- `Delving Deep into Rectifiers: Surpassing Human-Level Performance on ImageNet Classification <https://arxiv.org/pdf/1502.01852.pdf>`_, Kaiming He et al. (2015)


.. _activation_sigmoid:

Sigmoid
=======

Sigmoid takes a real value as input and outputs another value between 0 and 1. It’s easy to work with and has all the nice properties of activation functions: it’s non-linear, continuously differentiable, monotonic, and has a fixed output range.

+-----------------------------------------------------+-----------------------------------------------------+
| Function                                            | Derivative                                          |
+-----------------------------------------------------+-----------------------------------------------------+
| .. math::                                           | .. math::                                           |
|      S(z) = \frac{1} {1 + e^{-z}}                   |      S'(z) = S(z) \cdot (1 - S(z))                  |
+-----------------------------------------------------+-----------------------------------------------------+
| .. image:: images/sigmoid.png                       | .. image:: images/sigmoid_prime.png                 |
|       :align: center                                |       :align: center                                |
|       :width: 256 px                                |       :width: 256 px                                |
+-----------------------------------------------------+-----------------------------------------------------+
| .. literalinclude:: ../code/activation_functions.py | .. literalinclude:: ../code/activation_functions.py |
|       :pyobject: sigmoid                            |       :pyobject: sigmoid_prime                      |
+-----------------------------------------------------+-----------------------------------------------------+

.. quick create tables with tablesgenerator.com/text_tables and import our premade template in figures/

.. rubric:: Pros

- Typically used as final activation function of network for binary classification

.. rubric:: Cons

- Saturates and kills gradients
- Outputs from function are not zero-centered

.. rubric:: Further reading

- `Yes You Should Understand Backprop <https://medium.com/@karpathy/yes-you-should-understand-backprop-e2f06eab496b>`_, Karpathy (2016)


.. _activation_tanh:

Tanh
====

Tanh squashes a real-valued number to the range [-1, 1]. It's non-linear. But unlike Sigmoid, its output is zero-centered.
Therefore, in practice the tanh non-linearity is always preferred to the sigmoid nonlinearity. [1]_ 

+-----------------------------------------------------+-----------------------------------------------------+
| Function                                            | Derivative                                          |
+-----------------------------------------------------+-----------------------------------------------------+
| .. math::                                           | .. math::                                           |
|      tanh(z) = \frac{e^{z} - e^{-z}}{e^{z} + e^{-z}}|      tanh'(z) = 1 - tanh(z)^{2}                     |
+-----------------------------------------------------+-----------------------------------------------------+
| .. image:: images/tanh.png                          | .. image:: images/tanh_prime.png                    |
|       :align: center                                |       :align: center                                |
|       :width: 256 px                                |       :width: 256 px                                |
+-----------------------------------------------------+-----------------------------------------------------+
| .. literalinclude:: ../code/activation_functions.py | .. literalinclude:: ../code/activation_functions.py |
|       :pyobject: tanh                               |       :pyobject: tanh_prime                         |
+-----------------------------------------------------+-----------------------------------------------------+

.. quick create tables with tablesgenerator.com/text_tables and import our premade template in figures/

.. rubric:: Pros

- Typically used in Recurrent Neural Networks
- Zero-centered output from activation

.. rubric:: Cons

- More computationally expensive operation compared to RELU


Softmax
=======

Be the first to `contribute! <https://github.com/bfortuner/ml-cheatsheet>`__


.. rubric:: References

.. [1] http://cs231n.github.io/neural-networks-1/
