---
ms.openlocfilehash: 2fb980c8b75e25ba347c56ccc1c90f2959e83e21
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74567954"
---
### <a name="minimum-size-for-rsaopenssl-key-generation-has-increased"></a>RSAOpenSsl anahtar üretimi için minimum boyut arttı

Linux'ta yeni RSA anahtarları üretmek için minimum boyut 384 bit'ten 512 bit'e yükselmiştir.

#### <a name="change-description"></a>Açıklamayı değiştir

.NET Core 3.0 ile başlayarak, RSA `LegalKeySizes` örneklerinde mülk tarafından <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A?displayProperty=nameWithType>bildirilen <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A?displayProperty=nameWithType> minimum yasal anahtar boyutu , ve Linux'ta 384'ten 512'ye yükselmiştir.

Sonuç olarak, .NET Core 2.2 ve önceki sürümlerde, başarılı gibi `RSA.Create(384)` bir yöntem çağrısı. .NET Core 3.0 ve sonraki sürümlerinde, yöntem çağrısı `RSA.Create(384)` boyutu çok küçük olduğunu belirten bir özel durum atar.

Bu değişiklik, Linux'taki şifreleme işlemlerini gerçekleştiren OpenSSL'nin 1.0.2 ve 1.1.0 sürümleri arasındaki minimum limitini yükseltmesi nedeniyle yapıldı. .NET Core 3.0 OpenSSL 1.1.x ile 1.0.x arasında tercih eder ve bildirilen minimum sürüm bu yeni yüksek bağımlılık sınırlamasını yansıtacak şekilde yükseltilir.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="recommended-action"></a>Önerilen eylem

Etkilenen API'lerden herhangi birini ararsanız, oluşturulan anahtarların boyutunun sağlayıcı minimumundan az olmadığından emin olun.

> [!NOTE]
> 384-bit RSA zaten güvensiz olarak kabul edilir (512-bit RSA olduğu gibi). [NIST Özel Yayın 800-57 Bölüm 1 Revizyon 4](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf)gibi modern öneriler, yeni oluşturulan anahtarlar için minimum boyut olarak 2048-bit öneririz.

#### <a name="category"></a>Kategori

Şifreleme

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Security.Cryptography.AsymmetricAlgorithm.LegalKeySizes?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A?displayProperty=nameWithType>

<!--
### Affected APIs

- `P:System.Security.Cryptography.AsymmetricAlgorithm.LegalKeySizes`
- `Overload:System.Security.Cryptography.RSA.Create`
- `Overload:System.Security.Cryptography.RSAOpenSsl.#ctor`
- `Overload:System.Security.Cryptography.RSACryptoServiceProvider.#ctor`

-->
