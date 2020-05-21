---
ms.openlocfilehash: 3d94023fc508a56304587121c6cf1444c87b0d52
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83720920"
---
### <a name="minimum-size-for-rsaopenssl-key-generation-has-increased"></a>RSAOpenSsl anahtar üretimi için en düşük boyut arttı

Linux üzerinde yeni RSA anahtarları oluşturmak için en düşük boyut, 384 bitten 512 bit 'e artmıştır.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 3,0 ' den itibaren, `LegalKeySizes` Linux üzerinde, ve Linux ÜZERINDE RSA örneklerinde özelliği tarafından raporlanan en düşük yasal anahtar boyutu <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A> 384 ' <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A> den 512 ' ye yükselmiştir.

Sonuç olarak, .NET Core 2,2 ve önceki sürümlerde, gibi bir yöntem çağrısı `RSA.Create(384)` başarılı olur. .NET Core 3,0 ve sonraki sürümlerinde Yöntem çağrısı, `RSA.Create(384)` boyutun çok küçük olduğunu belirten bir özel durum oluşturur.

Bu değişiklik, Linux üzerinde şifreleme işlemlerini gerçekleştiren OpenSSL, 1.0.2 ve 1.1.0 sürümleri arasında en düşük bir değer oluşturduğundan yapılmıştır. .NET Core 3,0, OpenSSL 1.1. x-1.0. x ' i tercih eder ve bildirilen en düşük sürüm, bu yeni daha yüksek bağımlılık sınırlamasını yansıtacak şekilde tetiklenir.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="recommended-action"></a>Önerilen eylem

Etkilenen API 'lerden herhangi birini çağırırsanız, oluşturulan anahtarların boyutunun en düşük sağlayıcıdan daha az olmadığından emin olun.

> [!NOTE]
> 384-bit RSA zaten güvenli değil (512 bit RSA olarak). [NIST özel yayını 800-57 1. Bölüm düzeltme 4](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf)gibi modern öneriler, yeni oluşturulan anahtarlar için en düşük boyut olarak 2048 bit önerilir.

#### <a name="category"></a>Kategori

Şifreleme

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Security.Cryptography.AsymmetricAlgorithm.LegalKeySizes?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A>
- <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A>

<!--
#### Affected APIs

- `P:System.Security.Cryptography.AsymmetricAlgorithm.LegalKeySizes`
- `Overload:System.Security.Cryptography.RSA.Create`
- `Overload:System.Security.Cryptography.RSAOpenSsl.#ctor`
- `Overload:System.Security.Cryptography.RSACryptoServiceProvider.#ctor`

-->
