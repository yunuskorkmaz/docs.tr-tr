---
title: .NET Core ve .NET 5 ' te platformlar arası şifreleme
description: .NET tarafından desteklenen platformlarda şifreleme özellikleri hakkında bilgi edinin.
ms.date: 06/19/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- cryptography, cross-platform
- encryption, cross-platform
ms.openlocfilehash: 7269b32e509039fdd767446bd6e10202b089c094
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550025"
---
# <a name="cross-platform-cryptography-in-net-core-and-net-5"></a>.NET Core ve .NET 5 ' te platformlar arası şifreleme

.NET Core ve .NET 5 ' teki şifreleme işlemleri, işletim sistemi (OS) kitaplıkları tarafından yapılır. Bu bağımlılık avantajlara sahiptir:

* .NET uygulamaları, işletim sistemi güvenünden faydalanır. Şifreleme kitaplıklarının güvenlik açıklarından güvenli tutulması, işletim sistemi satıcıları için yüksek bir önceliktir. Bunu yapmak için, sistem yöneticilerinin uygulanması gereken güncelleştirmeleri sağlarlar.
* .NET uygulamaları, işletim sistemi kitaplıkları FIPS doğrulandıktan sonra FIPS tarafından doğrulanan algoritmalara erişebilir.

İşletim sistemi kitaplıklarının bağımlılığı ayrıca .NET uygulamalarının yalnızca işletim sisteminin desteklediği şifreleme özelliklerini kullanabileceği anlamına gelir. Tüm platformlar bazı temel özellikleri desteklese de, .NET tarafından desteklenen bazı özellikler bazı platformlarda kullanılamaz. Bu makalede, her platformda desteklenen özellikler tanımlanmaktadır.

Bu makalede, .NET 'teki şifrelemeye sahip olduğunuz varsayılmaktadır. Daha fazla bilgi için bkz. [.net şifreleme modeli](cryptography-model.md) ve [.NET Şifreleme Hizmetleri](cryptographic-services.md).

## <a name="hash-algorithms"></a>Karma algoritmaları

Sınıflar dahil olmak üzere tüm karma algoritmaların ve karma tabanlı ileti kimlik doğrulama (HMAC) sınıfları `*Managed` işletim sistemi kitaplıklarına erteler. Farklı işletim sistemi kitaplıklarının performansı farklı olsa da, uyumlu olmaları gerekir.

## <a name="symmetric-encryption"></a>Simetrik şifreleme

Temel şifrelemeler ve zincirleme sistem kitaplıkları tarafından yapılır ve tümü tüm platformlar tarafından desteklenir.

| Şifre + mod | Windows | Linux | macOS |
|---------------|---------|-------|-------|
| AES-CBC       | ✔️     | ✔️    | ✔️   |
| AES-ECB       | ✔️     | ✔️    | ✔️   |
| 3DES-CBC      | ✔️     | ✔️    | ✔️   |
| 3DES-ECB      | ✔️     | ✔️    | ✔️   |
| DES-CBC       | ✔️     | ✔️    | ✔️   |
| DES-ECB       | ✔️     | ✔️    | ✔️   |

## <a name="authenticated-encryption"></a>Kimliği doğrulanmış şifreleme

Kimliği doğrulanmış şifreleme (AE) desteği, ve sınıfları aracılığıyla AES-CCM ve AES-GCM için sağlanır <xref:System.Security.Cryptography.AesCcm?displayProperty=fullName> <xref:System.Security.Cryptography.AesGcm?displayProperty=fullName> .

Windows ve Linux 'ta, AES-CCM ve AES-GCM uygulamaları işletim sistemi kitaplıkları tarafından sağlanır.

### <a name="aes-ccm-and-aes-gcm-on-macos"></a>MacOS üzerinde AES-CCM ve AES-GCM

MacOS 'ta sistem kitaplıkları, üçüncü taraf kod için AES-CCM veya AES-GCM 'yi desteklemez, bu nedenle <xref:System.Security.Cryptography.AesCcm> ve <xref:System.Security.Cryptography.AesGcm> sınıfları destek Için OpenSSL kullanır. MacOS üzerindeki kullanıcıların, bu türler için bir OpenSSL (libşifre) kopyası olması gerekir ve bu, sistemin varsayılan olarak bir kitaplığı yükleyecek bir yolda olması gerekir. OpenSSL 'yi homebrew gibi bir paket yöneticisinden yüklemenizi öneririz.

`libcrypto.0.9.7.dylib` `libcrypto.0.9.8.dylib` MacOS 'a dahil edilen ve kitaplıkları OpenSSL 'nin önceki sürümlerinden ve kullanılmayacak. `libcrypto.35.dylib`, `libcrypto.41.dylib` Ve `libcrypto.42.dylib` kitaplıkları LibreSSL 'dan ve kullanılmayacak.

### <a name="aes-ccm-keys-nonces-and-tags"></a>AES-CCM anahtarları, nonce ve Etiketler

* Anahtar boyutları

  AES-CCM 128, 192 ve 256 bit anahtarlarla birlikte çalışmaktadır.

* Nonce boyutları

  <xref:System.Security.Cryptography.AesCcm>Sınıfı 56, 64, 72, 80, 88, 96 ve 104-bit (7, 8, 9, 10, 11, 12 ve 13-bayt) nonce 'yi destekler.

* Etiket boyutları

  <xref:System.Security.Cryptography.AesCcm>Sınıfı 32, 48, 64, 80, 96, 112 ve 128-bit (4, 8, 10, 12, 14 ve 16 bayt) etiketlerini oluşturmayı veya işlemeyi destekler.

### <a name="aes-gcm-keys-nonces-and-tags"></a>AES-GCM anahtarları, nonce ve Etiketler

* Anahtar boyutları

  AES-GCM 128, 192 ve 256 bit anahtarlarla çalışmaktadır.

* Nonce boyutları

  <xref:System.Security.Cryptography.AesGcm>Sınıfı yalnızca 96-bit (12 baytlık) nonce 'yi destekler.

* Etiket boyutları

  <xref:System.Security.Cryptography.AesGcm>Sınıfı 96, 104, 112, 120 ve 128-bit (12, 13, 14, 15 ve 16 bayt) etiketlerini oluşturmayı veya işlemeyi destekler.

## <a name="asymmetric-cryptography"></a>Asimetrik şifreleme

Bu bölüm aşağıdaki alt bölümleri içerir:

* [RSA](#rsa)
* [ECDSA](#ecdsa)
* [ECDH](#ecdh)
* ['DA](#dsa)

### <a name="rsa"></a>RSA

RSA (Rivest – Shamir – Adtaman) anahtar oluşturma, işletim sistemi kitaplıkları tarafından gerçekleştirilir ve boyut sınırlamalarına ve performans özelliklerine tabidir.

RSA anahtar işlemleri işletim sistemi kitaplıkları tarafından gerçekleştirilir ve yüklenebilen anahtar türleri işletim sistemi gereksinimlerine tabidir.

.NET, "RAW" (undoldurulmuş) RSA işlemlerini açığa çıkarır.

İşletim sistemi kitaplıkları şifreleme ve şifre çözme dolgusu için kullanılır. Tüm platformlar aynı doldurma seçeneklerini desteklemez:

| Doldurma modu                          | Windows (CNG) | Linux (OpenSSL) | macOS | Windows (CAPı) |
|---------------------------------------|---------------|-----------------|-------|----------------|
| PKCS1 şifreleme                      | ✔️           | ✔️              | ✔️   | ✔️             |
| OAEP-SHA-1                          | ✔️           | ✔️              | ✔️   | ✔️             |
| OAEP-SHA-2 (SHA256, SHA384, SHA512 OLUR) | ✔️           | ✔️              | ✔️   | ❌             |
| PKCS1 Imzası (MD5, SHA-1)          | ✔️           | ✔️              | ✔️   | ✔️             |
| PKCS1 Imzası (SHA-2)               | ✔️           | ✔️              | ✔️   | ⚠️\*           |
| 'Nın                                   | ✔️           | ✔️              | ✔️   | ❌             |

\* Windows Cryptoapı (CAPı), SHA-2 algoritması ile PKCS1 imzasına sahip değil. Ancak ayrı bir RSA nesnesi onu desteklemeyen bir şifreleme hizmeti sağlayıcısına (CSP) yüklenebilir.

#### <a name="rsa-on-windows"></a>Windows üzerinde RSA

* Her kullanıldığında Windows Cryptoapı (CAPı) kullanılır [`new RSACryptoServiceProvider()`](xref:System.Security.Cryptography.RSACryptoServiceProvider) .
* Windows şifreleme API 'SI yeni nesil (CNG) her [`new RSACng()`](xref:System.Security.Cryptography.RSACng) kullanıldığında kullanılır.
* Tarafından döndürülen nesne, <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> WINDOWS CNG tarafından dahili olarak desteklenmektedir. Windows CNG 'nin bu kullanımı bir uygulama ayrıntısının ve değişikliğe tabidir.
* <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey%2A>İçin uzantı yöntemi <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> bir örnek döndürür <xref:System.Security.Cryptography.RSACng> . Bu kullanımı <xref:System.Security.Cryptography.RSACng> bir uygulama ayrıntısıyla değiştirilebilir ve değişebilir.
* <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey%2A> <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> Şu anda bir örneği tercih eden genişletme yöntemi, <xref:System.Security.Cryptography.RSACng> ancak <xref:System.Security.Cryptography.RSACng> anahtarı açmadığında <xref:System.Security.Cryptography.RSACryptoServiceProvider> denenir. Tercih edilen sağlayıcı bir uygulama ayrıntısıyla değiştirilebilir ve değişebilir.

#### <a name="rsa-native-interop"></a>RSA yerel birlikte çalışma

.NET, programların .NET şifreleme kodunun kullandığı işletim sistemi kitaplıklarıyla birlikte çalışmasına izin vermek için türleri kullanıma sunar. Dahil edilen türler platformlar arasında çevrilmez ve yalnızca gerektiğinde doğrudan kullanılmalıdır.

| Tür                                                         | Windows | Linux         | macOS         |
|--------------------------------------------------------------|---------|---------------|---------------|
| <xref:System.Security.Cryptography.RSACryptoServiceProvider> | ✔️     | ⚠️<sup>1</sup>| ⚠️<sup>1</sup> |
| <xref:System.Security.Cryptography.RSACng>                   | ✔️     | ❌            | ❌            |
| <xref:System.Security.Cryptography.RSAOpenSsl>               | ❌     | ✔️            | ⚠️<sup>iki</sup> |

<sup>1</sup> , MacOS ve Linux üzerinde <xref:System.Security.Cryptography.RSACryptoServiceProvider> mevcut programlarla uyumluluk için kullanılabilir. Bu durumda, adlandırılmış anahtar açma gibi işletim sistemi birlikte çalışabilirliği gerektiren herhangi bir yöntem bir oluşturur <xref:System.PlatformNotSupportedException> .

<sup>2</sup> MacOS üzerinde <xref:System.Security.Cryptography.RSAOpenSsl> OpenSSL yüklüyse ve dinamik kitaplık yüklemesi aracılığıyla uygun bir libşifre dylib bulunabilir. Uygun bir kitaplık bulunamazsa özel durumlar atılır.

### <a name="ecdsa"></a>ECDSA

ECDSA (Eliptik Eğri dijital Imza algoritması) anahtar üretimi, işletim sistemi kitaplıkları tarafından yapılır ve boyut sınırlamalarına ve performans özelliklerine tabidir.

ECDSA anahtar eğrileri, işletim sistemi kitaplıkları tarafından tanımlanır ve sınırlamalarına tabidir.

| Eliptik Eğri                     | Windows 10    | Windows 7-8,1 | Linux         | macOS         |
|------------------------------------|---------------|-----------------|---------------|---------------|
| NıST P-256 (secp256r1)             | ✔️           | ✔️              | ✔️           | ✔️            |
| NıST P-384 (secp384r1)             | ✔️           | ✔️              | ✔️           | ✔️            |
| NıST P-521 (secp521r1)             | ✔️           | ✔️              | ✔️           | ✔️            |
| Brainpool eğrileri (adlandırılmış eğriler olarak) | ✔️           | ❌              | ⚠️<sup>1</sup>| ❌           |
| Diğer adlandırılmış eğriler                 | ⚠️<sup>iki</sup>| ❌             | ⚠️<sup>1</sup>| ❌           |
| Açık eğriler                    | ✔️           | ❌              | ✔️           | ❌            |
| Açık olarak içeri veya dışarı aktarma       | ✔️           | ❌<sup>03</sup>  | ✔️           | ❌<sup>03</sup>|

<sup>1</sup> Linux dağıtımları, aynı adlandırılmış eğrileri desteklemez.

Windows 10 ' da Windows CNG 'ye adlandırılmış eğriler için <sup>2</sup> destek eklenmiştir. Daha fazla bilgi için bkz: [CNG adlandırılmış eliptik eğrileri](/windows/win32/seccng/cng-named-elliptic-curves). Windows 7 ' de üç eğri dışında, adlandırılmış eğriler Windows 'un önceki sürümlerinde kullanılamaz.

<sup>3</sup> açık eğri parametreleriyle dışarı aktarma, MacOS veya Windows 'un önceki sürümlerinde kullanılamayan işletim sistemi kitaplığı desteği gerektirir.

#### <a name="ecdsa-native-interop"></a>ECDSA yerel birlikte çalışma

.NET, programların .NET şifreleme kodunun kullandığı işletim sistemi kitaplıklarıyla birlikte çalışmasına izin vermek için türleri kullanıma sunar. İlgili türler platformlar arasında çevrilmez ve yalnızca gerektiğinde doğrudan kullanılmalıdır.

| Tür                                             | Windows | Linux | macOS |
|--------------------------------------------------|---------|-------|-------|
| <xref:System.Security.Cryptography.ECDsaCng>     | ✔️     | ❌    | ❌    |
| <xref:System.Security.Cryptography.ECDsaOpenSsl> | ❌     | ✔️    | ⚠️\*  |

\* MacOS 'ta, <xref:System.Security.Cryptography.ECDsaOpenSsl> sistemde OpenSSL yüklüyse ve uygun bir libşifre dylib dinamik kitaplık yüklemesi aracılığıyla bulunamıyorsa, bu işe yarar. Uygun bir kitaplık bulunamazsa özel durumlar atılır.

### <a name="ecdh"></a>ECDH

ECDH (Eliptik Eğri Diffie-Hellman) anahtar üretimi, işletim sistemi kitaplıkları tarafından yapılır ve boyut sınırlamalarına ve performans özelliklerine tabidir.

<xref:System.Security.Cryptography.ECDiffieHellman>Sınıfı, ECDH hesaplamasının "RAW" değerini döndürmez. Döndürülen tüm veriler, anahtar türetme işlevleri açısından yapılır:

* KARMA (Z)
* Karma (Prepend | | Z | | ýna
* HMAC (anahtar, Z)
* HMAC (anahtar, önüne | | Z | | ýna
* HMAC (Z, Z)
* HMAC (Z, önüne | | Z | | ýna
* Tls11Prf (etiket, çekirdek)

ECDH anahtar eğrileri, işletim sistemi kitaplıkları tarafından tanımlanır ve sınırlamalarına tabidir.

| Eliptik Eğri                     | Windows 10    | Windows 7-8,1 | Linux         | macOS         |
|------------------------------------|---------------|-----------------|---------------|---------------|
| NıST P-256 (secp256r1)             | ✔️           | ✔️              | ✔️           | ✔️            |
| NıST P-384 (secp384r1)             | ✔️           | ✔️              | ✔️           | ✔️            |
| NıST P-521 (secp521r1)             | ✔️           | ✔️              | ✔️           | ✔️            |
| brainpool eğrileri (adlandırılmış eğriler olarak) | ✔️           | ❌              | ⚠️<sup>1</sup>| ❌           |
| diğer adlandırılmış eğriler                 | ⚠️<sup>iki</sup>| ❌             | ⚠️<sup>1</sup>| ❌           |
| Açık eğriler                    | ✔️           | ❌              | ✔️           | ❌            |
| Açık olarak içeri veya dışarı aktarma       | ✔️           | ❌<sup>03</sup>  | ✔️           | ❌<sup>03</sup>|

<sup>1</sup> Linux dağıtımları, aynı adlandırılmış eğrileri desteklemez.

Windows 10 ' da Windows CNG 'ye adlandırılmış eğriler için <sup>2</sup> destek eklenmiştir. Daha fazla bilgi için bkz: [CNG adlandırılmış eliptik eğrileri](/windows/win32/seccng/cng-named-elliptic-curves). Windows 7 ' de üç eğri dışında, adlandırılmış eğriler Windows 'un önceki sürümlerinde kullanılamaz.

<sup>3</sup> açık eğri parametreleriyle dışarı aktarma, MacOS veya Windows 'un önceki sürümlerinde kullanılamayan işletim sistemi kitaplığı desteği gerektirir.

#### <a name="ecdh-native-interop"></a>ECDH yerel birlikte çalışma

.NET, programların .NET tarafından kullanılan işletim sistemi kitaplıklarıyla birlikte çalışabilme türlerini kullanıma sunar. İlgili türler platformlar arasında çevrilmez ve yalnızca gerektiğinde doğrudan kullanılmalıdır.

| Tür                                                       | Windows | Linux | macOS |
|------------------------------------------------------------|---------|-------|-------|
| <xref:System.Security.Cryptography.ECDiffieHellmanCng>     | ✔️     | ❌    | ❌   |
| <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> | ❌     | ✔️    | ⚠️\* |

\* MacOS 'ta, <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> OpenSSL yüklüyse ve dinamik kitaplık yüklemesi aracılığıyla uygun bir libşifre dylib bulunamazsa, bu işe yarar. Uygun bir kitaplık bulunamazsa özel durumlar atılır.

### <a name="dsa"></a>'DA

DSA (dijital Imza algoritması) anahtar üretimi sistem kitaplıkları tarafından gerçekleştirilir ve boyut sınırlamalarına ve performans özelliklerine tabidir.

| İşlev                      | Windows CNG | Linux | macOS         | Windows CAPı |
|-------------------------------|-------------|-------|---------------|--------------|
| Anahtar oluşturma (<= 1024 bit)   | ✔️         | ✔️    | ❌            | ✔️           |
| Anahtar oluşturma (> 1024 bit)    | ✔️         | ✔️    | ❌            | ❌            |
| Anahtarları yükleme (<= 1024 bit)   | ✔️         | ✔️    | ✔️            | ✔️           |
| Anahtarları yükleme (> 1024 bit)    | ✔️         | ✔️    | ⚠️\*          | ❌            |
| FıPS 186-2                    | ✔️         | ✔️    | ✔️            | ✔️           |
| FIPS 186-3 (SHA-2 imzaları) | ✔️         | ✔️    | ❌            | ❌            |

\* macOS, 1024 bitten büyük olan DSA anahtarlarını yükler, ancak bu anahtarların davranışı tanımsız olur. FIPS 186-3 'e göre davranmazlar.

#### <a name="dsa-on-windows"></a>Windows üzerinde DSA

* Her kullanıldığında Windows Cryptoapı (CAPı) kullanılır [`new DSACryptoServiceProvider()`](xref:System.Security.Cryptography.DSACryptoServiceProvider) .
* Windows şifreleme API 'SI yeni nesil (CNG) her [`new DSACng()`](xref:System.Security.Cryptography.DSACng) kullanıldığında kullanılır.
* Tarafından döndürülen nesne, <xref:System.Security.Cryptography.DSA.Create%2A?displayProperty=nameWithType> WINDOWS CNG tarafından dahili olarak desteklenmektedir. Windows CNG 'nin bu kullanımı bir uygulama ayrıntısının ve değişikliğe tabidir.
* <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPublicKey%2A>İçin uzantı yöntemi <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> bir örnek döndürür <xref:System.Security.Cryptography.DSACng> . Bu kullanımı <xref:System.Security.Cryptography.DSACng> bir uygulama ayrıntısıyla değiştirilebilir ve değişebilir.
* <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPrivateKey%2A>İçin uzantı yöntemi <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> bir örneği tercih <xref:System.Security.Cryptography.DSACng> eder, ancak <xref:System.Security.Cryptography.DSACng> anahtarı açmadığında <xref:System.Security.Cryptography.DSACryptoServiceProvider> denenir.  Tercih edilen sağlayıcı bir uygulama ayrıntısıyla değiştirilebilir ve değişebilir.

#### <a name="dsa-native-interop"></a>DSA yerel birlikte çalışma

.NET, programların .NET şifreleme kodunun kullandığı işletim sistemi kitaplıklarıyla birlikte çalışmasına izin vermek için türleri kullanıma sunar. İlgili türler platformlar arasında çevrilmez ve yalnızca gerektiğinde doğrudan kullanılmalıdır.

| Tür                                                         | Windows | Linux         | macOS         |
|--------------------------------------------------------------|---------|---------------|---------------|
| <xref:System.Security.Cryptography.DSACryptoServiceProvider> | ✔️     | ⚠️<sup>1</sup> | ⚠️<sup>1</sup> |
| <xref:System.Security.Cryptography.DSACng>                   | ✔️     | ❌             | ❌            |
| <xref:System.Security.Cryptography.DSAOpenSsl>               | ❌      | ✔️            | ⚠️<sup>iki</sup> |

<sup>1</sup> , MacOS ve Linux üzerinde <xref:System.Security.Cryptography.DSACryptoServiceProvider> mevcut programlarla uyumluluk için kullanılabilir. Bu durumda, adlandırılmış bir anahtar açmak gibi sistem birlikte çalışabilirliğine ihtiyaç duyan herhangi bir yöntem bir oluşturur <xref:System.PlatformNotSupportedException> .

<sup>2</sup> MacOS üzerinde <xref:System.Security.Cryptography.DSAOpenSsl> OpenSSL yüklüyse ve dinamik kitaplık yüklemesi aracılığıyla uygun bir libşifre dylib bulunabilir. Uygun bir kitaplık bulunamazsa özel durumlar atılır.

## <a name="x509-certificates"></a>X. 509.440 sertifikaları

.NET 'teki X. 509.440 sertifikalarına yönelik desteğin çoğu işletim sistemi kitaplıklarından gelir. Bir sertifikayı <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> .net 'teki bir veya örneğe yüklemek için <xref:System.Security.Cryptography.X509Certificates.X509Certificate> , sertifikanın temel alınan işletim sistemi kitaplığı tarafından yüklenmesi gerekir.

### <a name="read-a-pkcs12pfx"></a>Bir PKCS12/PFX oku

| Senaryo                                     | Windows | Linux | macOS |
|----------------------------------------------|---------|-------|-------|
| Olmamalıdır                                        | ✔️     | ✔️    | ✔️   |
| Bir sertifika, özel anahtar yok              | ✔️     | ✔️    | ✔️   |
| Tek bir sertifika, özel anahtar            | ✔️     | ✔️    | ✔️   |
| Birden çok sertifika, özel anahtar yok       | ✔️     | ✔️    | ✔️   |
| Birden çok sertifika, bir özel anahtar       | ✔️     | ✔️    | ✔️   |
| Birden çok sertifika, birden çok özel anahtar | ✔️     | ⚠️\*  | ✔️   |

\* .NET 5 önizleme sürümleriyle kullanılabilir.

### <a name="write-a-pkcs12pfx"></a>Bir PKCS12/PFX yazın

| Senaryo                                     | Windows | Linux | macOS |
|----------------------------------------------|---------|-------|-------|
| Olmamalıdır                                        | ✔️     | ✔️    | ⚠️\* |
| Bir sertifika, özel anahtar yok              | ✔️     | ✔️    | ⚠️\* |
| Tek bir sertifika, özel anahtar            | ✔️     | ✔️    | ✔️   |
| Birden çok sertifika, özel anahtar yok       | ✔️     | ✔️    | ⚠️\* |
| Birden çok sertifika, bir özel anahtar       | ✔️     | ✔️    | ✔️   |
| Birden çok sertifika, birden çok özel anahtar | ✔️     | ⚠️\*  | ✔️   |
| Kısa ömürlü yükleme                            | ✔️     | ✔️    | ⚠️\* |

\* .NET 5 önizleme sürümleriyle kullanılabilir.

macOS, diske yazmayı gerektiren Anahtarlık nesne olmadan sertifika özel anahtarlarını yükleyemez. Anahtar zincirleri PFX yüklemesi için otomatik olarak oluşturulur ve artık kullanımda olmadığında silinir. Seçeneği, <xref:System.Security.Cryptography.X509Certificates.X509KeyStorageFlags.EphemeralKeySet?displayProperty=nameWithType> özel anahtarın diske yazılmayacağı anlamına gelir. Bu, macOS üzerinde bu bayrağın bir ile sonuçlenmesini sağlar <xref:System.PlatformNotSupportedException> .

### <a name="write-a-pkcs7-certificate-collection"></a>Bir PKCS7 sertifika koleksiyonu yazma

Windows ve Linux, her ikisi de DER kodlu PKCS7 bloblarını yay. macOS, belirsiz uzunlukta CER kodlamalı PKCS7 blob 'ları yayar.

### <a name="x509store"></a>X509Store

Windows 'da, <xref:System.Security.Cryptography.X509Certificates.X509Store> sınıfı Windows sertifika deposu API 'lerinin bir gösterimidir. Bu API 'Ler, .NET Framework .NET Core ve .NET 5 ' te aynı şekilde çalışır.

Linux 'ta, <xref:System.Security.Cryptography.X509Certificates.X509Store> sınıf, sistem güven kararlarının (salt okunurdur), Kullanıcı güven kararlarının (okuma-yazma) ve Kullanıcı anahtarı depolamanın (okuma-yazma) projeksiybirdir.

MacOS 'ta, <xref:System.Security.Cryptography.X509Certificates.X509Store> sınıf, sistem güven kararlarının (salt okunurdur), Kullanıcı güveni kararlarının (salt okunurdur) ve Kullanıcı anahtarı depolamanın (okuma-yazma) bir projeksiyonu olur.

Aşağıdaki tablolarda, her platformda desteklenen senaryolar gösterilmektedir. Desteklenmeyen senaryolar ( ❌ tablolarda) için, bir oluşturulur <xref:System.Security.Cryptography.CryptographicException> .

#### <a name="the-my-store"></a>My Store

| Senaryo                                         | Windows | Linux | macOS |
|--------------------------------------------------|---------|-------|-------|
| Currentuser\(ReadOnly) öğesini aç                   | ✔️     | ✔️    | ✔️   |
| Currentuser\(ReadWrite) öğesini aç                  | ✔️     | ✔️    | ✔️   |
| Currentuser\(yalnızca Existing) öğesini aç               | ✔️     | ⚠️    | ✔️   |
| Localmachine\open                             | ✔️     | ❌    | ✔️   |

Linux 'ta, depolar ilk yazma sırasında oluşturulur ve varsayılan olarak hiçbir Kullanıcı tarafından depolanmadıysa, açma `CurrentUser\My` `ExistingOnly` işlemi başarısız olabilir.

MacOS 'ta mağaza, `CurrentUser\My` Varsayılan olarak kullanıcının varsayılan anahtarlığdır `login.keychain` . `LocalMachine\My`Mağaza `System.keychain` .

#### <a name="the-root-store"></a>Kök depo

| Senaryo                              | Windows | Linux | macOS           |
|---------------------------------------|---------|-------|-----------------|
| CurrentUser\Root (ReadOnly) öğesini aç      | ✔️     | ✔️    | ✔️             |
| CurrentUser\Root (ReadWrite) aç     | ✔️     | ✔️    | ❌              |
| CurrentUser\Root (yalnızca Existing) aç  | ✔️     | ⚠️    | ✔️ (salt okunur ise) |
| Localmachıneroot 'ı (ReadOnly) aç     | ✔️     | ✔️    | ✔️             |
| Localmachınekökü 'ni (ReadWrite) aç    | ✔️     | ❌    | ❌              |
| Localmachınekökü (yalnızca Existing) aç | ✔️     | ⚠️    | ✔️ (salt okunur ise) |

Linux 'ta mağaza, `LocalMachine\Root` OpenSSL için varsayılan YOLDAKI CA paketinin bir yorumlamasıdır.

MacOS 'ta mağaza, `CurrentUser\Root` `SecTrustSettings` Kullanıcı güveni etki alanının sonuçlarını yorumlamasıdır. `LocalMachine\Root`Mağaza, `SecTrustSettings` yönetici ve sistem güven etki alanlarının sonuçlarını yorumlamasıdır.

#### <a name="the-intermediate-store"></a>Ara mağaza

| Senaryo                                      | Windows | Linux | macOS           |
|-----------------------------------------------|---------|-------|-----------------|
| Currentuser\ara (ReadOnly) öğesini aç      | ✔️     | ✔️    | ✔️             |
| Currentuser\ara (ReadWrite) öğesini aç     | ✔️     | ✔️    | ❌              |
| Currentuser\ara (yalnızca Existing) aç  | ✔️     | ⚠️    | ✔️ (salt okunur ise) |
| Localmachıne\ara (ReadOnly) öğesini aç     | ✔️     | ✔️    | ✔️             |
| Localmachıne\ara (ReadWrite) öğesini aç    | ✔️     | ❌    | ❌              |
| Localmachıne\ara (yalnızca Existing) aç | ✔️     | ⚠️    | ✔️ (salt okunur ise) |

Linux 'ta mağaza, `CurrentUser\Intermediate` ara CA 'ları, başarılı X509Chain derlemelerinde yetki bilgilerine erişim kayıtlarına indirme sırasında bir önbellek olarak kullanılır. `LocalMachine\Intermediate`Mağaza, OpenSSL için varsayılan YOLDAKI CA paketinin bir yorumlamasıdır.

#### <a name="the-disallowed-store"></a>Izin verilmeyen depo

| Senaryo                                    | Windows | Linux | macOS           |
|---------------------------------------------|---------|-------|-----------------|
| Currentuser\izin verilmeyen (ReadOnly) öğesini aç      | ✔️     | ⚠️    | ✔️             |
| Currentuser\izin verilmeyen (ReadWrite) öğesini aç     | ✔️     | ⚠️    | ❌              |
| Currentuser\izin verilmeyen (yalnızca Existing) aç  | ✔️     | ⚠️    | ✔️ (salt okunur ise) |
| Localmachıne\izin verilmeyen (salt okunur)     | ✔️     | ❌    | ✔️             |
| Localmachıne\izin verilmiyor (ReadWrite)    | ✔️     | ❌    | ❌              |
| Localmachıne\izin verilmiyor (yalnızca Existing) | ✔️     | ❌    | ✔️ (salt okunur ise) |

Linux 'ta mağaza, `Disallowed` zincir oluşturma sırasında kullanılmaz ve ona içerik eklenmeye çalışılıyor <xref:System.Security.Cryptography.CryptographicException> . <xref:System.Security.Cryptography.CryptographicException> `Disallowed` Zaten içerik aldıysanız mağaza açıldığında oluşturulur.

MacOS 'ta, Currentuser\izin verilmeyen ve localmachıneizin verilmeyen depolar, güvenine ayarlanmış olan sertifikalara uygun SecTrustSettings sonuçlarının yorumlarından oluşur `Always Deny` .

#### <a name="nonexistent-store"></a>Varolmayan depo

| Senaryo                                         | Windows | Linux | macOS |
|--------------------------------------------------|---------|-------|-------|
| Mevcut olmayan depoyu aç (yalnızca Existing)           | ❌     | ❌     | ❌    |
| CurrentUser var olmayan depo (ReadWrite) aç  | ✔️     | ✔️     | ⚠️   |
| LocalMachine mevcut olmayan depo (ReadWrite) aç | ✔️     | ❌     | ❌    |

MacOS 'ta, X509Store API 'SI ile özel depo oluşturma yalnızca konum için desteklenir `CurrentUser` . Kullanıcının Anahtarlık dizininde parolası olmayan yeni bir anahtarlık oluşturur (*~/Library/keyzincirleri*). Parola ile bir anahtarlık oluşturmak için bir P/Invoke `SecKeychainCreate` kullanılabilir. Benzer şekilde, `SecKeychainOpen` farklı konumlarda anahtar zincirlerini açmak için de kullanılabilir. Sonuç, `IntPtr` [`new X509Store(IntPtr)`](xref:System.Security.Cryptography.X509Certificates.X509Store.%23ctor(System.IntPtr)) geçerli kullanıcının izinlerine tabi olan bir okuma/yazma yeteneğine sahip bir mağaza almak için öğesine geçirilebilir.

### <a name="x509chain"></a>X509Chain

macOS çevrimdışı CRL kullanımını desteklemediğinden, `X509RevocationMode.Offline` olarak kabul edilir `X509RevocationMode.Online` .

macOS, CRL (sertifika Iptal listesi)/OCSP (çevrimiçi sertifika durumu Protokolü)/AIA (yetkili bilgi erişimi) indirme üzerinde kullanıcı tarafından başlatılan bir zaman aşımını desteklemez, bu nedenle `X509ChainPolicy.UrlRetrievalTimeout` yok sayılır.

## <a name="additional-resources"></a>Ek kaynaklar

* [.NET şifreleme modeli](cryptography-model.md)
* [.NET Şifreleme Hizmetleri](cryptographic-services.md)
* [Doldurmayı kullanarak CBC modunda simetrik şifre çözmedeki zamanlama açıkları](vulnerabilities-cbc-mode.md)
* [ASP.NET Core veri koruma](/aspnet/core/security/data-protection/introduction)
