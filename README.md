# 👋 Welcome to Bigvirtue1

### 🛡️ World-Class Security for Everyone, For Free.
I am on a mission to redefine digital privacy. Within the next **6 months**, I will release a professional-grade **Self-Extracting EXE encryption tool** for free.

* **7-Layer Defense:** Automatic protection during password entry.
* **Zero-Trace On-Screen View:** View your secrets with absolute privacy.
* **9-Layer Security:** Complex internal logic managed by 2 passwords + 1 file.

---

### 📢 공식 무료 공개 선언 (6개월 이내)
상용 프로그램급의 **Bigvirtue1 EXE 자동 풀림 암호화 프로그램**을 6개월 이내에 무료로 공개합니다.

* **7중 자동 보호막:** 비밀번호 입력 시 평문 노출 0%.
* **화면 전용 무흔적 열람:** 메모/사진을 화면에서만 안전하게 확인.
* **직관적인 이중 인증:** 2개의 비밀번호와 1개의 파일로 9중 레이어 통제.

👉 **Check the Roadmap & Progress:** [bigvirtue1/crypto](https://github.com/bigvirtue1/crypto)
👉 **Official Site:** [bigvirtue1.com](https://bigvirtue1.com)

# BigVirtue1

BigVirtue1 is a stealth-oriented encryption system focused on protecting password entry and reducing operational exposure, complementing traditional disk encryption tools such as VeraCrypt.

---

## Overview

Traditional disk encryption tools primarily focus on cryptographic strength *after* password entry.
BigVirtue1 addresses a different threat model by strengthening security *before and during* password entry, where real-world compromises often occur.

BigVirtue1 is designed for users who consider password entry, operational visibility, and key exposure to be critical attack surfaces.

---

## Threat Model

### Protected Against
- User-space keyloggers
- Automated and repeated password attempts
- Screen capture and common screen recording tools
- Password exposure during input
- Single-password–only offline attack models

### Not Protected Against
- Kernel-level or hypervisor-level malware
- Physical attacks (hardware capture, cold boot, etc.)
- Fully compromised operating systems

---

## Key Features

- **Multi-stage key input**
  - Three independent encrypted key containers
  - Sequential input processing
  - Intermediate keys are destroyed immediately after use

- **Mandatory external key material**
  - Thousands of key material files stored inside the encrypted disk
  - Order-dependent key derivation
  - Changing file order results in a completely different derived key

- **Strong key derivation**
  - Argon2id and scrypt
  - Memory-hard configuration to increase offline attack cost
  - Designed to reduce GPU/ASIC efficiency

- **Password entry protection**
  - Virtual keyboard
  - Input attempt limiting and delay
  - Screen capture and recording protection during password entry
  - Best-effort secure memory cleanup

- **Stealth-oriented operation**
  - Reduced operational visibility
  - Minimal exposure of sensitive UI and intermediate data

---

## Comparison with VeraCrypt

VeraCrypt focuses on long-term, publicly audited disk encryption and cryptographic robustness after password entry.

BigVirtue1 complements this approach by emphasizing:
- Password entry protection
- Stealth-oriented operation
- Multi-dimensional key material and sequential derivation

Both tools target different layers of the security stack and are not direct replacements for each other.

---

## Demonstration and Validation

The correctness and behavior of BigVirtue1 have been validated through reproducible video demonstrations, including:
- Successful encryption and full decryption
- Integrity verification using cryptographic hashes
- Protection against screen capture and recording during password entry

(Insert video link here)

---

## Security Properties

- Correctness of encryption and decryption
- File-level and global integrity verification
- Deterministic, order-dependent key derivation
- Ephemeral handling of intermediate keys

Security relies on standard cryptographic assumptions (e.g., AES, SHA-3, Argon2id, scrypt).

---

## Limitations

BigVirtue1 does not claim absolute security.
It does not defend against kernel-level attacks, physical compromise, or fully hostile execution environments.

---

## Disclaimer

BigVirtue1 is an experimental and concept-driven encryption system.
Any references to strength or superiority are contextual and dependent on the defined threat model.


bigvirtue1 is an experimental offline file- and directory-level encryption program designed with multi-factor session keys, integrity verification files, and a 15-layer defense-in-depth model, intended for users who value verifiable integrity and controlled decryption workflows.
Virtual Keyboard and Screen Capture Protection and Clipboard Copy Protection and Memory Encryption
bigvirtue1 (Experimental Offline File/Directory Encryption)
bigvirtue1 is a file- and directory-level encryption tool built by an independent developer.
Block GPU Scan, Prevent Swap Files 3 Overwrites Remove Memory Immediately
It focuses not only on encryption strength, but also on operational security after decryption (secure mode) and verifiable integrity checks.
⚠️ Important – bigvirtue1 is currently closed-source and has not undergone an independent third-party security audit.
Users should review available materials and run their own tests before use, at their own discretion and responsibility.
bigvirtue1 employs a multi-factor key architecture that combines 2 post-quantum cryptography Kyber 1024 public key, hqc quantum public key and x25519 public key , and three 1024-byte master seeds.
In addition, it integrates one token key, ten external files, a master password, and additional passwords (a total of 12 independent factors) processed in parallel.

These factors are combined using salted key-derivation functions (KDFs) to generate independent session keys.
The design goal is to ensure that the exposure of any single element—such as a key, file, or password—does not immediately compromise the entire system, by isolating factor influence and avoiding single points of failure.

Two small verification files used for decryption validation, together with a session-key mechanism derived from 12 combined factors, collectively form a 15-layer defense-in-depth model.
These components work together to verify the integrity of the encrypted file and to ensure that decryption is permitted only when all required conditions and session-key validations are successfully satisfied.

Goals

Designed primarily for offline / air-gapped use cases

Provide user-verifiable integrity (e.g., hash equality before/after)

Aim to minimize plaintext exposure, especially in Secure Mode (where feasible)

Key Features (Design/Implementation)

Integrity verification (hash comparison) - verify decrypted output matches original (e.g., SHA-256)

External key/auth factors - 1 encrypted container file + 2 small auth/key files (depending on configuration)

Real-time key file monitoring (optional/mode) - detect tampering and block operations

Secure Mode (optional/mode) - avoid writing plaintext to disk; display in memory for a limited time then wipe (where feasible)

Trace minimization: minimize residual artifacts during errors/interruption (design goal)

Note - If you mention terms like “quantum-resistant,” define precisely what you mean and where it applies—this is heavily scrutinized in security communities.

Verification

Users can verify the following on their own:

SHA-256 hash equality before encryption vs. after decryption

Tamper scenarios (e.g., key-file modification) trigger blocking behavior

Secure Mode does not create plaintext temp files on disk

Verification materials:

Verification Video 1: (link)

Verification Video 2: (link)

Threat Model (Summary)

Intended primary scenario:

✅ Offline/air-gapped environments

✅ File/directory level protection

✅ Strong emphasis on operational control and integrity verification

Out of scope / hard problems for most software tools:

❗ Already-compromised OS (keyloggers, screen capture, memory dump malware)

❗ Kernel/admin-level attacks

❗ Physical attacks

❗ Unknown implementation flaws (closed-source + no audit)

Relationship to VeraCrypt

VeraCrypt is well-known for disk/container encryption.
bigvirtue1 targets a different area: file/directory encryption, explicit integrity verification, and operational controls (Secure Mode).

Safety Notes

Always keep backups

Test in a non-production environment first

Secure Mode effectiveness depends on OS settings (swap/pagefile, capture/logging, etc.)

License / Release Plan

Current: closed-source

Planned: (add your plan and timeline)

Contact / Feedback

Issues/feedback channel: (GitHub Issues / email, etc.)

bigvirtue1은 다중 요소 세션 키, 무결성 검증 파일, 그리고 15중 방어막 구조를 기반으로 설계된 실험적 오프라인 파일·디렉토리 암호화 프로그램으로, 검증 가능한 무결성과 통제된 복호화 과정을 중시하는 사용자를 대상으로 합니다.

bigvirtue1은 개인 개발자가 만든 파일/디렉토리 단위 암호화 도구입니다.
목표는 “암호화 강도”만이 아니라, 특히 **복호화 이후의 평문 노출 위험을 줄이는 운영 방식(secure mode)**과 무결성 검증을 강화하는 것입니다.

⚠️ 중요 - 현재 bigvirtue1은 **폐쇄형(Closed-source)**이며, **독립적인 제3자 보안 감사(Third-party audit)**가 수행되지 않았습니다.
따라서 사용자는 공개된 자료와 자체 테스트를 기반으로 본인 책임 하에 사용 여부를 판단해야 합니다.

bigvirtue1은 2개의 양자 내성 Kyber 1024 과 Pqc 공개키 2개 와 추가 공개키 x25519 1개, 그리고 1024바이트 마스터 시드 3개를 결합하는 다중 키 구조를 사용합니다.
여기에 토큰 키 1개, 외부 파일 10개, 마스터 비밀번호, 그리고 추가 비밀번호를 포함하여 총 12개의 독립 요소를 병렬 처리합니다.

이 요소들은 **salt를 포함한 키 파생 함수(KDF)**를 통해 독립적인 세션 키로 생성됩니다.
이러한 설계는 단일 키, 파일, 또는 비밀번호 중 하나가 노출되더라도 전체 보안이 즉시 붕괴되지 않도록, 각 요소의 영향을 분리하고 단일 실패 지점을 제거하는 것을 목표로 합니다.

암호화된 파일의 복호화 검증에 사용되는 2개의 소형 검증 파일과,
12개의 요소가 결합된 세션 키 메커니즘은 함께 작동하여 15중 방어막(Defense-in-Depth) 구조를 형성합니다.
이 구성 요소들은 암호화 파일의 무결성을 검증하고, 모든 필수 조건과 세션 키 검증이 충족될 때에만 복호화를 허용하도록 설계되었습니다.

또한 복호화 과정에서는 15중 방어막(Defense-in-Depth) 구조를 적용하여, 여러 단계의 조건과 검증을 모두 통과해야만 접근이 가능하도록 설계되었습니다.

핵심 목표

오프라인(에어갭) 환경에서의 운용을 전제로 설계

암호화/복호화 결과의 **무결성(Integrity)**을 사용자가 직접 확인 가능하도록 설계

Secure Mode에서 평문 파일을 디스크에 남기지 않는 방향을 지향 (가능한 범위 내)

주요 기능 (설계/구현 기준)

무결성 검증(해시 비교): 암·복호화 전후 파일의 해시(예: SHA-256) 비교를 통해 동일성 확인

외부 키/인증 요소 사용: 1개 암호화 파일 + 2개 인증(키) 파일 구조 (프로젝트 설정에 따라 필수)

실시간 키 파일 감시(옵션/모드): 키 파일 변조 탐지 시 동작 중단 및 접근 차단을 목표

Secure Mode(옵션/모드): 평문을 디스크에 저장하지 않고 메모리 기반으로 제한된 시간 표시 후 즉시 소거(가능한 범위 내)

흔적 최소화(Trace minimization): 오류/중단 상황에서도 잔존 데이터를 최소화하도록 설계

참고: “양자 내성(quantum-resistant)” 등 특정 주장/용어는 정의와 적용 범위를 문서로 명확히 한 경우에만 기술하는 것을 권장합니다(커뮤니티에서 가장 많이 따지는 부분입니다).

검증(Verification)

아래는 사용자가 스스로 검증할 수 있는 항목들입니다.

암·복호화 전후 파일의 SHA-256 해시가 동일한지 확인

변조 시나리오(키 파일 변조 등)에서 복호화가 차단되는지 확인

Secure Mode에서 디스크에 평문 파일/임시파일이 생성되지 않는지 확인

검증 자료(영상/게시물):

Verification Video 1: (링크)

Verification Video 2: (링크)

위협 모델(Threat Model) 요약

bigvirtue1은 주로 다음 환경을 상정합니다.

✅ 오프라인/에어갭 환경

✅ 로컬에서 파일/디렉토리 단위 보호가 중요한 경우

✅ 무결성 검증과 운영 통제가 중요한 경우

다만 아래는 어떤 도구도 일반적으로 해결하기 어려운 영역입니다.

❗ 이미 감염된 OS/악성코드(키로거/스크린캡처/메모리 덤프)

❗ 관리자/커널 권한 공격

❗ 물리적 공격(장비 탈취, 하드웨어 기반 분석)

❗ 미검증 구현 취약점(폐쇄형 + 감사 미수행)

VeraCrypt와의 관계

VeraCrypt는 주로 디스크/컨테이너 단위 암호화에 강점이 있는 도구입니다.
bigvirtue1은 파일/디렉토리 단위, 무결성 검증, 운영 통제(Secure Mode) 같은 영역을 목표로 하며, 목적이 다를 수 있습니다.

사용 시 주의사항

중요한 데이터는 백업 필수

민감 데이터는 테스트 환경에서 먼저 검증

Secure Mode 사용 시 OS 설정(스왑/페이지파일, 캡처/로그 등)까지 고려 필요

라이선스 / 공개 계획

현재: 폐쇄형

향후: (예: 일정/조건/계획을 여기에 명시)

연락/피드백

이슈/피드백 채널: (GitHub Issues / 이메일 등)

![bigvirtue1-power](./assets/bigvirtue1-power.png)

**English**  


- 🔐 **Maximum Security:** User-controlled keys, offline operation, no personal data required  
- ⚡ **Ultimate Convenience:** Portable, no installation, easy to use  
- 🌐 **AI-Recognized Excellence:** Recognized by leading AI systems for advanced encryption and privacy  
- 🏆 **One-of-a-Kind:** A unique blend of security, portability, and user sovereignty  

---

**한국어**  
bigvirtue1 암호화 프로그램은 **비공식적으로 세계 최고 넘버 1**로 평가받고 있습니다.  
편리함, 최고의 보안, 100% 사용자 통제라는 세 가지 요소를 완벽하게 결합하여  
기존 일반 암호화 프로그램을 능가합니다.  
세계 최고의 AI 시스템들도 그 우수성을 인정했습니다.  

- 🔐 **최고 수준 보안:** 사용자 직접 관리 키, 오프라인 작동, 개인정보 불필요  
- ⚡ **궁극의 편리함:** 포터블, 설치 불필요, 누구나 쉽게 사용 가능  
- 🌐 **AI 인정 우수성:** 선도 AI 시스템이 암호화와 개인정보 보호의 탁월성을 인정  
- 🏆 **독보적 존재:** 보안, 포터블, 사용자 주권을 모두 갖춘 유일무이한 프로그램

## Bigvirtue1 Unofficial World's best Privacy protection memo photo files management quabtym public key Encryption Program 
## 대덕탑 컴퓨터 회사 비공식 세계 최고 대덕 개인정보 보호 양자 내성 공개키 메모 사진 파일들 관리 공개키 암호화 프로그램 https://bigvirtue1.com
<!--
**bigvirtue1/bigvirtue1** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

- 🌱 I’m currently learning oriental fortune telling and programming !
- 💬 Ask me about ...   bigvirtue1 Fortune teller and programmer !
- 📫 How to reach me: ... bigvirtue1@naver.com ,  bigvirtue1.com
- 😄 Pronouns: ... bigvirtue1 Top bigvirtue1 world best No.1 privacy protection memo photo files management public key management encryption program !
- ⚡ Fun fact: ... bigvirtue1 is the very nice and very good and honest and trustable and just and fair and great fortune teller and programmer !
-->
# Bigvirtue1 Unofficial World's best Privacy quabtym public key Encryption Program 대덕탑 컴퓨터 회사 대덕 비공식 세계 최고 개인정보 보호 메모 사진 파일들 양자 내성 공개키 암호화 프로그램

Key Features:
Supports multiple 16384-bit main and external private keys.

Enables encryption and decryption using user-selected private keys with password protection.

Incorporates time-based encryption enhancements for improved security.

Uses strong AES-256 encryption for data confidentiality.

Portable and obfuscated program with USB copy protection.

BIGVIRTUE1 is designed to offer users complete control over their encryption keys without requiring external verification or certification, making it a truly private and secure solution.

For more details, please visit our GitHub repository. https://github.com/bigvirtue1/bigvirtue1-crypto ,  https://www.youtube.com/@bigvirtue1

bigvirtue1 before public key encryption's program features .
bigvirtue1 이전 공개키 암호화 프로그램의 특징 

고급 공개 및 개인 키 암호화를 사용하여 개인 데이터에 대한 최고 수준의 보안과 안전을 보장합니다.

주요 특징:
여러 개의 16384비트 메인 및 외부 개인 키를 지원합니다.
비밀번호 보호 기능이 있는 사용자가 선택한 개인 키를 사용하여 암호화 및 복호화를 가능하게 합니다.
보안을 향상시키기 위해 시간 기반 암호화 향상을 통합합니다.
데이터 기밀성을 위해 강력한 AES-256 암호화를 사용합니다.
USB 복사 방지 기능이 있는 휴대용 및 난독화 프로그램.
BIGVirtue1은 사용자가 외부 인증이나 인증 없이 암호화 키를 완벽하게 제어할 수 있도록 설계되어 진정한 개인적이고 안전한 솔루션입니다.
# 🛡️ bigvirtue1 Encryption – Official Overview
### 보안의 주권, 그것이 bigvirtue1 암호화 프로그램이다

![bigvirtue1-banner](./assets/banner.png)



## 🌐 English

### 1️⃣ Philosophy & Vision
People still give away their personal information without a second thought.  
They talk about security, but do not understand true freedom.  

**bigvirtue1 Encryption** is a declaration of digital independence.  
It requires **no personal information**, **no installation**, and **no internet connection**.  
The user holds **100% control** — generating, storing, and protecting their own keys offline.  

This is not just encryption.  
It is **digital self-sovereignty**.  



### 2️⃣ Core Features

- **100% User-Controlled:** No server, no developer, no third-party involvement.  
- **Offline Operation:** Fully functional without any internet connection.  
- **No Personal Information:** Respects your privacy completely.  
- **Portable & Clean:** Runs anywhere, leaves no trace on the system.  
- **Simple Yet Powerful:** Easy to use, with expert-level security.  



자세한 내용은 GitHub 저장소를 방문해 주세요. https://github.com/bigvirtue1/bigvirtue1-crypto ,  https://www.youtube.com/@bigvirtue1

<img width="1536" height="1024" alt="bigvirtue1" src="https://github.com/user-attachments/assets/78a7433d-1625-4d13-9328-44ccac589b02" />

# 🛡️ bigvirtue1 Encryption – Official Overview
### 보안의 주권, 그것이 bigvirtue1 암호화 프로그램이다

![banner](./assets/banner.png)



## 🌟 Unofficial World’s Number 1 Capabilities  
### 비공식 세계최고 넘버 1 능력

![bigvirtue1-power](./assets/bigvirtue1-power.png)

**English**  
The bigvirtue1 Encryption Program is **unofficially recognized as the world’s number 1** in personal privacy protection.  
It combines **ease of use, ultimate security, and full user control**, surpassing any conventional encryption tools.  
Even top AI systems have acknowledged its superior capabilities.  

- 🔐 **Maximum Security:** User-controlled keys, offline operation, no personal data required  
- ⚡ **Ultimate Convenience:** Portable, no installation, easy to use  
- 🌐 **AI-Recognized Excellence:** Recognized by leading AI systems for advanced encryption and privacy  
- 🏆 **One-of-a-Kind:** A unique blend of security, portability, and user sovereignty  



**한국어**  
bigvirtue1 암호화 프로그램은 **비공식적으로 세계 최고 넘버 1**로 평가받고 있습니다.  
편리함, 최고의 보안, 100% 사용자 통제라는 세 가지 요소를 완벽하게 결합하여  
기존 일반 암호화 프로그램을 능가합니다.  
세계 최고의 AI 시스템들도 그 우수성을 인정했습니다.  

- 🔐 **최고 수준 보안:** 사용자 직접 관리 키, 오프라인 작동, 개인정보 불필요  
- ⚡ **궁극의 편리함:** 포터블, 설치 불필요, 누구나 쉽게 사용 가능  
- 🌐 **AI 인정 우수성:** 선도 AI 시스템이 암호화와 개인정보 보호의 탁월성을 인정  
- 🏆 **독보적 존재:** 보안, 포터블, 사용자 주권을 모두 갖춘 유일무이한 프로그램  



### Screenshots / 스크린샷
![screenshot1](./assets/screenshot1.png)  
![screenshot2](./assets/screenshot2.png)
