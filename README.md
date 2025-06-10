# Polar Codes in MATLAB: A Comprehensive Implementation

This repository provides a comprehensive MATLAB implementation of polar codes, featuring various components from channel reliability estimation to advanced decoding algorithms. This project is intended for educational and research purposes to demonstrate the principles of polar coding and evaluate their performance under different channel conditions.

## Description

Polar codes, introduced by Erdal Arıkan, are a class of error-correcting codes that provably achieve the symmetric capacity of any binary-input discrete memoryless channel. This implementation covers the entire pipeline of a polar coding system:

* **Reliability Sequence Generation:** Computes the reliability of each sub-channel using Bhattacharyya parameters. This is crucial for determining which channels should carry information bits and which should be frozen.
* **Encoder:** Implements a polar encoder that transforms a message block, including information and frozen bits, into a coded block.
* **Channel Models:**
    * **BPSK Modulation and AWGN Channel:** Simulates the transmission of the encoded signal over an Additive White Gaussian Noise (AWGN) channel using Binary Phase-Shift Keying (BPSK) modulation.
    * **Mixed Noise Channel:** A custom channel model that introduces a combination of Gaussian, Laplace, and Uniform noise, allowing for performance evaluation in more complex noise environments.
* **Decoders:**
    * **Successive Cancellation (SC) Decoder:** Implements the baseline SC decoding algorithm.
    * **Successive Cancellation List (SCL) Decoder with Cyclic Redundancy Check (CRC):** Implements the more powerful SCL decoder, which maintains a list of potential candidate codewords. This is augmented with a CRC to significantly improve error detection and correction performance.
* **Performance Evaluation:** Includes scripts to simulate and plot the Bit Error Rate (BER), Block Error Rate (BLER), and Probability of Success for various code rates and signal-to-noise ratios (Eb/No). It also includes a comparison with the Shannon limit to benchmark the performance.

---

## Improvements and Key Features

This implementation builds upon the fundamental concepts of polar codes and introduces several key features and improvements over standard or existing public codes:

* **Comprehensive and Modular Codebase:** The code is well-structured into distinct functions for each logical block (encoding, decoding, channel modeling, etc.). This modularity makes it easy to understand, modify, and extend for further research.

* **Advanced CRC-Aided SCL Decoder:** While many basic implementations focus only on the SC decoder, this project includes a fully functional CRC-aided SCL decoder. This is a significant enhancement as it dramatically improves the error-correction performance, bringing it closer to that of state-of-the-art codes like LDPC and Turbo codes, especially for finite block lengths. The use of a CRC to select the correct codeword from the list of candidates is a critical feature for practical polar code implementations.

* **Novel Mixed Noise Channel:** A unique feature of this project is the `bpsk_mixed_channel` function. Most academic implementations of polar codes are evaluated over the standard AWGN channel. By providing a channel that combines Gaussian, Laplace, and Uniform noise distributions, this codebase allows for the analysis of polar code robustness in non-Gaussian and more realistic noise scenarios. This is a valuable tool for researchers looking to explore the performance of polar codes beyond idealized channel models.

* **Detailed Performance Analysis and Visualization:** The project includes extensive scripts for performance evaluation. It not only calculates BER and BLER but also provides:
    * **Comparisons between SC and SCL decoders:** This directly illustrates the performance gains achieved by the more complex SCL algorithm.
    * **Performance analysis across different code rates and block lengths:** This allows for a thorough understanding of how these parameters affect the performance of polar codes.
    * **Benchmarking against the Shannon Limit:** By plotting the performance against the theoretical Shannon limit, the implementation provides a clear measure of how close the polar codes are to optimal performance.
    * **Comparison between AWGN and the mixed noise channel:** This highlights the impact of different noise statistics on the decoder's performance.

* **Clear and Reusable Functions:** The functions are written with clear input and output arguments, making them easy to reuse in other projects or for different simulation setups. For instance, the `polar_encode` and `bpsk_awgn_channel` functions can be readily integrated into other communication system simulations.

In summary, this MATLAB project offers a more complete and advanced simulation environment for polar codes than many publicly available examples. The inclusion of a CRC-aided SCL decoder, a custom mixed noise channel, and comprehensive performance comparison scripts make it a powerful tool for both learning and research in the field of channel coding.
