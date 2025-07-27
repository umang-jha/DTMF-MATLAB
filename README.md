# DTMF Tone Decoder Using MATLAB

A real-time MATLAB-based system that captures and decodes Dual Tone Multi Frequency (DTMF) signals from telephone keypad tones via frequency analysis.

## 📋 Table of Contents
- [Overview](#overview)
- [Features](#features)
- [How DTMF Works](#how-dtmf-works)
- [System Requirements](#system-requirements)
- [Installation](#installation)
- [Usage](#usage)
- [Algorithm Details](#algorithm-details)
- [Results](#results)
- [Future Improvements](#future-improvements)
- [Applications](#applications)
- [Contributors](#contributors)

## 🔍 Overview

This project implements a DTMF (Dual Tone Multi Frequency) decoder that can detect and decode telephone keypad tones in real-time. DTMF is the signaling method used by telephones to indicate which key has been pressed using a combination of two tones—one low frequency and one high frequency.

### Problem Statement
To build a MATLAB-based system that decodes DTMF tones captured through a microphone and reconstructs a complete phone number.

### Key Challenges Addressed
- Real-time signal capture and processing
- Accurate tone detection amid noise
- Reliable digit recognition with time constraints
- Detecting end of input using silence detection

## ✨ Features

- **Real-time Audio Capture**: Captures audio signals from microphone input
- **DTMF Tone Detection**: Accurately identifies valid DTMF tone pairs
- **Digit Decoding**: Converts detected tones into corresponding keypad digits
- **Phone Number Reconstruction**: Displays complete phone number after silence detection
- **Noise Filtering**: Robust performance in various audio environments
- **Dynamic Thresholding**: Adaptive signal processing for improved accuracy

## 📞 How DTMF Works

DTMF uses a 4×4 matrix system where each key generates two simultaneous tones:

### Frequency Matrix
| Key | Low Freq (Hz) | High Freq (Hz) |
|-----|---------------|----------------|
| 1   | 697           | 1209           |
| 2   | 697           | 1336           |
| 3   | 697           | 1477           |
| A   | 697           | 1633           |
| 4   | 770           | 1209           |
| 5   | 770           | 1336           |
| 6   | 770           | 1477           |
| B   | 770           | 1633           |
| 7   | 852           | 1209           |
| 8   | 852           | 1336           |
| 9   | 852           | 1477           |
| C   | 852           | 1633           |
| *   | 941           | 1209           |
| 0   | 941           | 1336           |
| #   | 941           | 1477           |
| D   | 941           | 1633           |

## 🔧 System Requirements

- **MATLAB**: R2018b or later recommended
- **Audio System Toolbox**: For real-time audio processing
- **Signal Processing Toolbox**: For FFT and filtering operations
- **Microphone**: For audio input capture
- **Minimum RAM**: 4GB recommended
- **Operating System**: Windows/Mac/Linux

## 🚀 Installation

1. **Clone the Repository**
   ```bash
   git clone https://github.com/yourusername/dtmf-tone-decoder.git
   cd dtmf-tone-decoder
   ```

2. **MATLAB Setup**
   - Ensure MATLAB is installed with required toolboxes
   - Add the project folder to MATLAB path

3. **Audio Device Configuration**
   - Connect microphone to your system
   - Test audio input in MATLAB using `audiodevinfo`

## 💻 Usage

1. **Run the Main Script**
   ```matlab
   % In MATLAB Command Window
   run('dtmf_decoder_main.m')
   ```

2. **Audio Input**
   - The system will start listening for DTMF tones
   - Press telephone keypad keys or play DTMF tones near the microphone

3. **Output**
   - Each detected digit will be displayed in real-time
   - Complete phone number shown after 2 seconds of silence

### Example Output
```
Detected digit: 9
Detected digit: 8
Detected digit: 7
Detected digit: 6
Detected digit: 5
Detected digit: 4
Detected digit: 3
Detected digit: 2
Detected digit: 1
Detected digit: 0

Complete Phone Number: 9876543210
```

## 🔬 Algorithm Details

### Signal Acquisition
- **Sample Rate**: 16 kHz
- **Frame Size**: 2048 samples with 1024 overlap
- **Audio Recorder**: MATLAB's `audioDeviceReader`

### Tone Detection Process

1. **Windowing**: Hamming window applied to reduce spectral leakage
2. **FFT Analysis**: Fast Fourier Transform applied to each frame
3. **Dynamic Thresholding**: Threshold = mean(signal) × factor
4. **Peak Detection**: Using `findpeaks` function
5. **Frequency Matching**: Match two peaks to nearest DTMF pair (±20 Hz tolerance)
6. **Digit Validation**: Minimum tone duration required for valid digit
7. **Silence Detection**: Used to detect end of number input

### Key Parameters
- **Frequency Tolerance**: ±20 Hz
- **Minimum Tone Duration**: Configurable
- **Silence Threshold**: 2 seconds for end-of-input detection

## 📊 Results

### System Performance
- ✅ Successfully detects digits from keypad tones in quiet environments
- ✅ Capable of outputting entire phone number when input ends
- ✅ Reliable distinction between digits using frequency matching
- ✅ Real-time processing with minimal latency

### Key Findings
- FFT-based frequency detection is efficient for tone decoding
- Noise handling and multi-frame logic significantly improve robustness
- Real-time signal processing requires fine-tuning of timing and thresholds

## 🚀 Future Improvements

- [ ] **Graphical User Interface (GUI)** for better user interaction
- [ ] **Machine Learning Integration** for improved tone classification
- [ ] **Enhanced Noise Filtering** for field deployment
- [ ] **Multi-threading Support** for better real-time performance
- [ ] **Database Integration** for number logging
- [ ] **Mobile App Version** using MATLAB Mobile

## 🎯 Applications

- **IVR Systems**: Interactive Voice Response systems
- **Access Control**: Keypad-based security systems
- **Phone-based Authentication**: Banking and security applications
- **Telecommunication Testing**: Network equipment testing
- **Educational Tools**: Signal processing demonstrations

## 👥 Contributors

**Presented by:**
- **Pearl Vyas** - 23BEC043
- **Umang Jha** - 23BEC049

**Under Mentorship of:**
- **Dr. Manish Mandloi**

**Department of Electronics and Communication**  
**PDEU, Gandhinagar**

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📞 Support

For questions or support, please contact:
- Pearl Vyas: [email]
- Umang Jha: [email]

## 🙏 Acknowledgments

- Dr. Manish Mandloi for project guidance
- PDEU ECE Department for project support
- MATLAB community for technical resources

---

**⭐ If you found this project helpful, please give it a star!**
