---
ms.openlocfilehash: 3d94023fc508a56304587121c6cf1444c87b0d52
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83720920"
---
### <a name="minimum-size-for-rsaopenssl-key-generation-has-increased"></a><span data-ttu-id="75184-101">RSAOpenSsl anahtar üretimi için en düşük boyut arttı</span><span class="sxs-lookup"><span data-stu-id="75184-101">Minimum size for RSAOpenSsl key generation has increased</span></span>

<span data-ttu-id="75184-102">Linux üzerinde yeni RSA anahtarları oluşturmak için en düşük boyut, 384 bitten 512 bit 'e artmıştır.</span><span class="sxs-lookup"><span data-stu-id="75184-102">The minimum size for generating new RSA keys on Linux has increased from 384-bit to 512-bit.</span></span>

#### <a name="change-description"></a><span data-ttu-id="75184-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="75184-103">Change description</span></span>

<span data-ttu-id="75184-104">.NET Core 3,0 ' den itibaren, `LegalKeySizes` Linux üzerinde, ve Linux ÜZERINDE RSA örneklerinde özelliği tarafından raporlanan en düşük yasal anahtar boyutu <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A> 384 ' <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A> den 512 ' ye yükselmiştir.</span><span class="sxs-lookup"><span data-stu-id="75184-104">Starting with .NET Core 3.0, the minimum legal key size reported by the `LegalKeySizes` property on RSA instances from <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>, <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A>, and <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A> on Linux has increased from 384 to 512.</span></span>

<span data-ttu-id="75184-105">Sonuç olarak, .NET Core 2,2 ve önceki sürümlerde, gibi bir yöntem çağrısı `RSA.Create(384)` başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="75184-105">As a result, in .NET Core 2.2 and earlier versions, a method call such as `RSA.Create(384)` succeeds.</span></span> <span data-ttu-id="75184-106">.NET Core 3,0 ve sonraki sürümlerinde Yöntem çağrısı, `RSA.Create(384)` boyutun çok küçük olduğunu belirten bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="75184-106">In .NET Core 3.0 and later versions, the method call `RSA.Create(384)` throws an exception indicating the size is too small.</span></span>

<span data-ttu-id="75184-107">Bu değişiklik, Linux üzerinde şifreleme işlemlerini gerçekleştiren OpenSSL, 1.0.2 ve 1.1.0 sürümleri arasında en düşük bir değer oluşturduğundan yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="75184-107">This change was made because OpenSSL, which performs the cryptographic operations on Linux, raised its minimum between versions 1.0.2 and 1.1.0.</span></span> <span data-ttu-id="75184-108">.NET Core 3,0, OpenSSL 1.1. x-1.0. x ' i tercih eder ve bildirilen en düşük sürüm, bu yeni daha yüksek bağımlılık sınırlamasını yansıtacak şekilde tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="75184-108">.NET Core 3.0 prefers OpenSSL 1.1.x to 1.0.x, and the minimum reported version was raised to reflect this new higher dependency limitation.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="75184-109">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="75184-109">Version introduced</span></span>

<span data-ttu-id="75184-110">3.0</span><span class="sxs-lookup"><span data-stu-id="75184-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="75184-111">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="75184-111">Recommended action</span></span>

<span data-ttu-id="75184-112">Etkilenen API 'lerden herhangi birini çağırırsanız, oluşturulan anahtarların boyutunun en düşük sağlayıcıdan daha az olmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="75184-112">If you call any of the affected APIs, ensure that the size of any generated keys is not less than the provider minimum.</span></span>

> [!NOTE]
> <span data-ttu-id="75184-113">384-bit RSA zaten güvenli değil (512 bit RSA olarak).</span><span class="sxs-lookup"><span data-stu-id="75184-113">384-bit RSA is already considered insecure (as is 512-bit RSA).</span></span> <span data-ttu-id="75184-114">[NIST özel yayını 800-57 1. Bölüm düzeltme 4](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf)gibi modern öneriler, yeni oluşturulan anahtarlar için en düşük boyut olarak 2048 bit önerilir.</span><span class="sxs-lookup"><span data-stu-id="75184-114">Modern recommendations, such as [NIST Special Publication 800-57 Part 1 Revision 4](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf), suggest 2048-bit as the minimum size for newly generated keys.</span></span>

#### <a name="category"></a><span data-ttu-id="75184-115">Kategori</span><span class="sxs-lookup"><span data-stu-id="75184-115">Category</span></span>

<span data-ttu-id="75184-116">Şifreleme</span><span class="sxs-lookup"><span data-stu-id="75184-116">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="75184-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="75184-117">Affected APIs</span></span>

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
