[[**Microsoft Intune**]] — это облачная платформа Microsoft для **управления и защиты компьютеров, телефонов, приложений и корпоративных данных**. Проще говоря: компания с помощью Intune контролирует, **какие устройства могут подключаться к рабочим ресурсам и насколько они безопасны**.

Для cybersecurity тебе особенно полезно понимать такие вещи:

- **Device enrollment** — подключение Windows, macOS, iOS/iPadOS и Android к корпоративному управлению.
- **Compliance policies** — проверка, соответствует ли устройство требованиям: включён ли BitLocker, есть ли PIN, обновлена ли ОС, не взломано ли устройство и т. п.
- **Configuration profiles** — централизованная настройка компьютеров: firewall, Defender, пароли, ограничения USB и множество других параметров.
- **Conditional Access + Microsoft Entra ID** — например: _дать доступ к Microsoft 365 только пользователю с MFA и с compliant device_.
- **Application management** — установка, обновление и удаление приложений.
- **Endpoint security** — политики Defender, firewall, disk encryption, attack surface reduction и другие меры защиты.
- **Device actions** — удалённая синхронизация, блокировка, wipe/reset и другие административные действия.

Для **SOC** Intune тоже важен, хотя SOC-аналитик обычно не администрирует его целый день. Например, ты видишь alert в Defender:

**Suspicious PowerShell → пользователь → устройство → Entra ID identity → Intune compliance/configuration**

и можешь понять, управляется ли endpoint организацией, соответствует ли политикам и какие security controls на нём применены. Intune тесно работает с **Microsoft Entra ID, Conditional Access и Microsoft Defender for Endpoint**.

Если представить Microsoft Security ecosystem очень упрощённо:

**Entra ID** → _кто пользователь?_  
**Intune** → _какое устройство и безопасно ли оно?_  
**Defender for Endpoint** → _что происходит на этом устройстве?_  
**Sentinel** → _что происходит во всей инфраструктуре?_

Для твоего направления **SOC / SC-200** тебе не нужно сначала становиться Intune administrator. Я бы выучила примерно **20% Intune, которые дают 80% пользы**: enrollment → compliance → configuration profiles → Conditional Access → Defender integration → device investigation.


## Main functions of Microsoft Intune

Microsoft Intune is used to **manage devices, applications, security settings, and access to company resources**.

|Intune function|What it does|SC-200 importance|
|---|---|---|
|**Device enrollment**|Registers Windows, macOS, iOS, Android devices for management|🟡 Know concept|
|**Device configuration**|Pushes settings such as password requirements, Wi-Fi, VPN, security settings|🟡 Basic|
|**Compliance policies**|Checks whether devices meet security requirements|🟢 Important|
|**Endpoint security policies**|Configures Defender Antivirus, Firewall, BitLocker, ASR rules, etc.|🟢 Important|
|**Application management**|Installs, removes and protects corporate applications|⚪ Low|
|**Conditional Access integration**|Uses device compliance as a condition for access|🟡 Understand|
|**Defender for Endpoint integration**|Shares device risk/security information between Intune and Defender|🟢 Very important|
|**Security baselines**|Applies recommended Microsoft security configurations|🟡 Know concept|
|**Remote device actions**|Wipe, retire, restart, sync devices, etc.|⚪ Low for SC-200|

Compliance policies evaluate whether managed devices satisfy defined requirements, while Defender integration can contribute **device-risk signals** to those compliance decisions.

---


### 1. Intune ↔ Defender for Endpoint integration

This is the most important part.

Understand this flow:

**Endpoint**

↓  
**Microsoft Defender for Endpoint**

detects threats and calculates **device risk**

↓

**Microsoft Intune**

uses the risk information to determine whether the device is **compliant**

↓

**Entra Conditional Access**

can allow or block access.

For example:

> Malware is detected on Mila-PC → Defender for Endpoint marks device **High Risk** → Intune marks it **Non-compliant** → Conditional Access blocks Microsoft 365 access.

Microsoft specifically supports using Defender for Endpoint threat-risk signals in Intune compliance policies.

---

### 2. Compliance vs configuration

This distinction is useful for the exam.

**Configuration policy**

> "Turn BitLocker ON."

It **changes/configures** something.

**Compliance policy**

> "BitLocker must be ON."

It **checks** whether the condition is satisfied.

So think:

**Configuration = DO this**

**Compliance = CHECK this**

---

### 3. Endpoint security policies

Know what Intune can manage:

- Microsoft Defender Antivirus
- Windows Firewall
- BitLocker / disk encryption
- Attack Surface Reduction rules
- Account protection
- Endpoint Detection and Response settings
- Security baselines

Microsoft describes Intune endpoint-security policies as a way for security administrators to configure and manage security settings on managed devices.

You don't need to memorize every possible policy.

---

### 4. Device risk vs compliance

This is a common conceptual distinction.

**Device risk**

comes mainly from **Defender for Endpoint**.

Examples:

- Low
- Medium
- High

It represents detected security risk.

**Device compliance**

comes from **Intune**.

Examples:

- Compliant
- Non-compliant

A compliance policy might say:

> Maximum allowed device threat level = Medium.

Then:

**Defender:** device risk = High  
→ **Intune:** non-compliant  
→ **Conditional Access:** block access.


## A useful SC-200 mental model

Memorize this relationship:

**Entra ID**  
→ identities and access

**Intune**  
→ manages devices and determines compliance

**Defender for Endpoint**  
→ detects and responds to endpoint threats

**Defender XDR**  
→ correlates security incidents across Microsoft security products

**Sentinel**  
→ SIEM/SOAR collecting and correlating security data across the environment

