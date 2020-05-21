---
ms.openlocfilehash: a4476fbff572c004632153e5a98812c241efca57
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721069"
---
### <a name="openssl-versions-on-macos"></a>MacOS üzerinde OpenSSL sürümleri

MacOS 'ta .NET Core 3,0 ve üzeri çalışma zamanları artık OpenSSL 1.1. x sürümlerini,,,,, <xref:System.Security.Cryptography.AesCcm> <xref:System.Security.Cryptography.AesGcm> <xref:System.Security.Cryptography.DSAOpenSsl> <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> <xref:System.Security.Cryptography.ECDsaOpenSsl> <xref:System.Security.Cryptography.RSAOpenSsl> ve <xref:System.Security.Cryptography.SafeEvpPKeyHandle> türleri için OpenSSL 1.0. x sürümlerine tercih ediyor.

.NET Core 2,1 çalışma zamanı artık OpenSSL 1.1. x sürümlerini destekliyor, ancak yine de OpenSSL 1.0. x sürümlerini tercih ediyor.

#### <a name="change-description"></a>Açıklamayı Değiştir

Daha önce .NET Core çalışma zamanı, OpenSSL ile etkileşime geçen türler için macOS üzerinde OpenSSL 1.0. x sürümlerini kullandı. En son OpenSSL 1.0. x sürümü olan OpenSSL 1.0.2 artık destek dışındadır. OpenSSL 'nin desteklenen sürümlerinde OpenSSL kullanan türleri tutmak için, .NET Core 3,0 ve üzeri çalışma zamanları artık macOS 'ta OpenSSL 'nin daha yeni sürümlerini kullanıyor.

Bu değişiklik ile, macOS 'ta .NET Core çalışma zamanları için davranış aşağıdaki gibidir:

- .NET Core 3,0 ve sonraki sürüm çalışma zamanları, varsa OpenSSL 1.1. x kullanır ve yalnızca 1.1. x sürümü yoksa OpenSSL 1.0. x ' e geri döner.

  Özel P/Invoke ile OpenSSL birlikte çalışma türlerini kullanan çağıranlar için, açıklamalar bölümündeki yönergeleri izleyin <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> . Değeri denetmezseniz uygulamanız kilitlenebilir <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion> .

- .NET Core 2,1 çalışma zamanı, varsa OpenSSL 1.0. x kullanır ve kullanılabilir 1.0. x sürümü yoksa OpenSSL 1.1. x ' e geri döner.

  2,1 çalışma zamanı, OpenSSL 'nin önceki sürümünü tercih eder çünkü <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> özellik .NET Core 2,1 ' de mevcut olmadığından, OpenSSL sürümü çalışma zamanında güvenilir bir şekilde belirlenemez.

#### <a name="version-introduced"></a>Sunulan sürüm

- .NET Core 2.1.16
- .NET Core 3.0.3
- .NET Core 3.1.2

#### <a name="recommended-action"></a>Önerilen eylem

- Artık gerekmiyorsa OpenSSL sürüm 1.0.2 'yi kaldırın.

- ,,,,, <xref:System.Security.Cryptography.AesCcm> <xref:System.Security.Cryptography.AesGcm> <xref:System.Security.Cryptography.DSAOpenSsl> <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> <xref:System.Security.Cryptography.ECDsaOpenSsl> <xref:System.Security.Cryptography.RSAOpenSsl> Veya <xref:System.Security.Cryptography.SafeEvpPKeyHandle> türlerini kullanıyorsanız OpenSSL 1.1. x ' i yükler.

- OpenSSL birlikte çalışma türlerini özel P/Invoke ile birlikte kullanıyorsanız, açıklamalar bölümündeki yönergeleri izleyin <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> .

#### <a name="category"></a>Kategori

Core .NET kitaplıkları

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Security.Cryptography.AesCcm?displayProperty=fullName>
- <xref:System.Security.Cryptography.AesGcm?displayProperty=fullName>
- <xref:System.Security.Cryptography.DSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDsaOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.RSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.SafeEvpPKeyHandle?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Security.Cryptography.AesCcm``
- `T:System.Security.Cryptography.AesGcm`
- `T:System.Security.Cryptography.DSAOpenSsl`
- `T:System.Security.Cryptography.ECDiffieHellmanOpenSsl`
- `T:System.Security.Cryptography.ECDsaOpenSsl`
- `T:System.Security.Cryptography.RSAOpenSsl`
- `T:System.Security.Cryptography.SafeEvpPKeyHandle`

-->
