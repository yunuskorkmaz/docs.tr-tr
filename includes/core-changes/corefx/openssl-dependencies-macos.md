---
ms.openlocfilehash: 8790637c31d503455eb8ba722cca827c2a24b7c9
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021466"
---
### <a name="openssl-versions-on-macos"></a>macOS'ta OpenSSL sürümleri

.NET Core 3.0 ve daha sonra macOS'taki çalışma süreleri artık OpenSSL 1.1.x sürümlerini <xref:System.Security.Cryptography.AesCcm> <xref:System.Security.Cryptography.AesGcm>OpenSSL <xref:System.Security.Cryptography.RSAOpenSsl>1.0.x sürümleriiçin <xref:System.Security.Cryptography.SafeEvpPKeyHandle> <xref:System.Security.Cryptography.DSAOpenSsl> <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> <xref:System.Security.Cryptography.ECDsaOpenSsl>tercih ediyor.

.NET Core 2.1 çalışma süresi artık OpenSSL 1.1.x sürümlerini destekler, ancak yine de OpenSSL 1.0.x sürümlerini tercih eder.

#### <a name="change-description"></a>Açıklamayı değiştir

Daha önce,.NET Core çalışma zamanı OpenSSL ile etkileşime geçen türler için macOS'ta OpenSSL 1.0.x sürümlerini kullansA. En son OpenSSL 1.0.x sürümü OpenSSL 1.0.2, şimdi destek dışında. OpenSSL'nin desteklenen sürümlerinde OpenSSL kullanan türleri tutmak için .NET Core 3.0 ve daha sonraki çalışma süreleri artık macOS'ta OpenSSL'nin yeni sürümlerini kullansın.

Bu değişiklikle, macOS'taki .NET Core çalışma sürelerini içeren davranış aşağıdaki gibidir:

- .NET Core 3.0 ve sonraki sürüm çalışma süreleri OpenSSL 1.1.x'i kullanır, eğer varsa ve yalnızca 1.1.x sürümü yoksa OpenSSL 1.0.x'e geri döner.

  OpenSSL interop türlerini özel P/Invokes ile kullanan arayanlar <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> için, açıklamalartaki kılavuzu izleyin. <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion> Değeri kontrol etmezseniz uygulamanız çökebilir.

- .NET Core 2.1 çalışma süresi varsa OpenSSL 1.0.x kullanır ve varsa OpenSSL 1.1.x sürümü yoksa geri düşer.

  <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> Özellik .NET Core 2.1'de bulunmadığından, 2.1 çalışma süresi OpenSSL'in önceki sürümünü tercih eder, bu nedenle OpenSSL sürümü çalışma zamanında güvenilir bir şekilde belirlenemez.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

- .NET Çekirdek 2.1.16
- .NET Çekirdek 3.0.3
- .NET Çekirdek 3.1.2

#### <a name="recommended-action"></a>Önerilen eylem

- Artık gerekli değilse OpenSSL sürüm 1.0.2'yi kaldırın.

- OpenSSL 1.1.x'i <xref:System.Security.Cryptography.AesCcm>yüklerseniz , <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> <xref:System.Security.Cryptography.ECDsaOpenSsl>, <xref:System.Security.Cryptography.RSAOpenSsl> <xref:System.Security.Cryptography.AesGcm> <xref:System.Security.Cryptography.DSAOpenSsl>, <xref:System.Security.Cryptography.SafeEvpPKeyHandle> , , veya türleri kullanın.

- OpenSSL interop türlerini özel P/Invokes ile kullanıyorsanız, <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> açıklamalartaki kılavuzu izleyin.

#### <a name="category"></a>Kategori

Çekirdek .NET kitaplıkları

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Security.Cryptography.AesCcm?displayProperty=fullName>
- <xref:System.Security.Cryptography.AesGcm?displayProperty=fullName>
- <xref:System.Security.Cryptography.DSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDsaOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.RSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.SafeEvpPKeyHandle?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Security.Cryptography.AesCcm``
- `T:System.Security.Cryptography.AesGcm`
- `T:System.Security.Cryptography.DSAOpenSsl`
- `T:System.Security.Cryptography.ECDiffieHellmanOpenSsl`
- `T:System.Security.Cryptography.ECDsaOpenSsl`
- `T:System.Security.Cryptography.RSAOpenSsl`
- `T:System.Security.Cryptography.SafeEvpPKeyHandle`

-->
