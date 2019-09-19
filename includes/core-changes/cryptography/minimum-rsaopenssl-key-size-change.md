---
ms.openlocfilehash: 07ab65de16b72bd0844a39e4b35235c5f043f3ec
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117166"
---
### <a name="minimum-size-for-rsaopenssl-key-generation-has-increased"></a><span data-ttu-id="36fb6-101">RSAOpenSsl anahtar üretimi için en düşük boyut arttı</span><span class="sxs-lookup"><span data-stu-id="36fb6-101">Minimum size for RSAOpenSsl key generation has increased</span></span>

<span data-ttu-id="36fb6-102">Linux üzerinde yeni RSA anahtarları oluşturmak için en düşük boyut, 384 bitten 512 bit 'e artmıştır.</span><span class="sxs-lookup"><span data-stu-id="36fb6-102">The minimum size for generating new RSA keys on Linux has increased from 384-bit to 512-bit.</span></span>

#### <a name="change-description"></a><span data-ttu-id="36fb6-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="36fb6-103">Change description</span></span>

<span data-ttu-id="36fb6-104">.NET Core 3,0 ' den itibaren, < System. Security. Cryptography. `LegalKeySizes` RSA ' dan RSA örneklerinde özelliği tarafından raporlanan minimum geçerli anahtar boyutu. Create% 2A? DisplayProperty = namewithtype >, < System. Security. Cryptography. rsaopenssl.% 23ctor% 2A? displayProperty = nameWithType > ve < System. Security. Cryptography. RSACryptoServicePlatform.% 23ctor% 2A? displayProperty = nameWithType >, Linux üzerinde 384 ' den 512 ' e artmıştır.</span><span class="sxs-lookup"><span data-stu-id="36fb6-104">Starting with .NET Core 3.0, the minimum legal key size reported by the `LegalKeySizes` property on RSA instances from <System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>, <System.Security.Cryptography.RSAOpenSsl.%23ctor%2A?displayProperty=nameWithType>, and <System.Security.Cryptography.RSACryptoServicePlatform.%23ctor%2A?displayProperty=nameWithType> on Linux has increased from 384 to 512.</span></span>

<span data-ttu-id="36fb6-105">Sonuç olarak, .NET Core 2,2 ve önceki sürümlerde, gibi bir yöntem çağrısı `RSA.Create(384)` başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="36fb6-105">As a result, in .NET Core 2.2 and earlier versions, a method call such as `RSA.Create(384)` succeeds.</span></span> <span data-ttu-id="36fb6-106">.NET Core 3,0 ve sonraki sürümlerinde Yöntem çağrısı `RSA.Create(384)` , boyutun çok küçük olduğunu belirten bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="36fb6-106">In .NET Core 3.0 and later versions, the method call `RSA.Create(384)` throws an exception indicating the size is too small.</span></span>

<span data-ttu-id="36fb6-107">Bu değişiklikler, Linux üzerinde şifreleme işlemlerini gerçekleştiren OpenSSL, 1.0.2 ve 1.1.0 sürümleri arasında en düşük bir değer oluşturduğundan yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="36fb6-107">This changes was made because OpenSSL, which performs the cryptographic operations on Linux, raised its minimum between versions 1.0.2 and 1.1.0.</span></span>  <span data-ttu-id="36fb6-108">.NET Core 3,0, OpenSSL 1.1. x-1.0. x ' i tercih eder ve bildirilen en düşük sürüm, bu yeni daha yüksek bağımlılık sınırlamasını yansıtacak şekilde tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="36fb6-108">.NET Core 3.0 prefers OpenSSL 1.1.x to 1.0.x, and the minimum reported version was raised to reflect this new higher dependency limitation.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="36fb6-109">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="36fb6-109">Version introduced</span></span>

<span data-ttu-id="36fb6-110">3.0</span><span class="sxs-lookup"><span data-stu-id="36fb6-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="36fb6-111">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="36fb6-111">Recommended action</span></span>

<span data-ttu-id="36fb6-112">Etkilenen API 'lerden herhangi birini çağırırsanız, oluşturulan anahtarların boyutunun en düşük sağlayıcıdan daha az olmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="36fb6-112">If you call any of the affected APIs, ensure that the size of any generated keys is not less than the provider minimum.</span></span>

> [!NOTE]
> <span data-ttu-id="36fb6-113">384-bit RSA zaten güvenli değil (512 bit RSA olarak).</span><span class="sxs-lookup"><span data-stu-id="36fb6-113">384-bit RSA is already considered insecure (as is 512-bit RSA).</span></span> <span data-ttu-id="36fb6-114">[NIST özel yayını 800-57 1. Bölüm düzeltme 4](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf)gibi modern öneriler, yeni oluşturulan anahtarlar için en düşük boyut olarak 2048 bit önerilir.</span><span class="sxs-lookup"><span data-stu-id="36fb6-114">Modern recommendations, such as [NIST Special Publication 800-57 Part 1 Revision 4](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf), suggest 2048-bit as the minimum size for newly generated keys.</span></span>

#### <a name="category"></a><span data-ttu-id="36fb6-115">Kategori</span><span class="sxs-lookup"><span data-stu-id="36fb6-115">Category</span></span>

<span data-ttu-id="36fb6-116">To</span><span class="sxs-lookup"><span data-stu-id="36fb6-116">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="36fb6-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="36fb6-117">Affected APIs</span></span>

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
