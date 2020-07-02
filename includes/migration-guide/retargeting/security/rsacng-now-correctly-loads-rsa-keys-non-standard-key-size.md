---
ms.openlocfilehash: c1e85941c8c6c31c7d937d0671ad955fa6490783
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614654"
---
### <a name="rsacng-now-correctly-loads-rsa-keys-of-non-standard-key-size"></a><span data-ttu-id="da689-101">RSACng artık standart olmayan anahtar boyutunun RSA anahtarlarını doğru şekilde yükler</span><span class="sxs-lookup"><span data-stu-id="da689-101">RSACng now correctly loads RSA keys of non-standard key size</span></span>

#### <a name="details"></a><span data-ttu-id="da689-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="da689-102">Details</span></span>

<span data-ttu-id="da689-103">4.6.2 ' den önceki .NET Framework sürümlerde, RSA sertifikaları için standart olmayan anahtar boyutlarına sahip müşteriler bu anahtarlara <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=fullName> ve <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=fullName> genişletme yöntemleriyle erişemez.</span><span class="sxs-lookup"><span data-stu-id="da689-103">In .NET Framework versions prior to 4.6.2, customers with non-standard key sizes for RSA certificates are unable to access those keys via the <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=fullName> and <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=fullName> extension methods.</span></span>  <span data-ttu-id="da689-104"><xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName>İleti ile &quot; İstenen anahtar boyutu desteklenmiyor &quot; .</span><span class="sxs-lookup"><span data-stu-id="da689-104">A <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> with the message &quot;The requested key size is not supported&quot; is thrown.</span></span> <span data-ttu-id="da689-105">.NET Framework 4.6.2 Bu sorun düzeltildi.</span><span class="sxs-lookup"><span data-stu-id="da689-105">In .NET Framework 4.6.2 this issue has been fixed.</span></span> <span data-ttu-id="da689-106">Benzer şekilde, <xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)> ve <xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)> Şimdi bir oluşturmadan standart olmayan anahtar boyutlarıyla çalışır <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="da689-106">Similarly, <xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)> and <xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)> now work with non-standard key sizes without throwing a <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="da689-107">Öneri</span><span class="sxs-lookup"><span data-stu-id="da689-107">Suggestion</span></span>

<span data-ttu-id="da689-108">Standart olmayan anahtar boyutları kullanıldığında, bir önceki davranışa dayanan özel durum işleme mantığı varsa <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> , mantığı kaldırmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="da689-108">If there is any exception handling logic that relies on the previous behavior where a <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> is thrown when non-standard key sizes are used, consider removing the logic.</span></span>

| <span data-ttu-id="da689-109">Name</span><span class="sxs-lookup"><span data-stu-id="da689-109">Name</span></span>    | <span data-ttu-id="da689-110">Değer</span><span class="sxs-lookup"><span data-stu-id="da689-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="da689-111">Kapsam</span><span class="sxs-lookup"><span data-stu-id="da689-111">Scope</span></span>   | <span data-ttu-id="da689-112">Edge</span><span class="sxs-lookup"><span data-stu-id="da689-112">Edge</span></span>        |
| <span data-ttu-id="da689-113">Sürüm</span><span class="sxs-lookup"><span data-stu-id="da689-113">Version</span></span> | <span data-ttu-id="da689-114">4.6.2</span><span class="sxs-lookup"><span data-stu-id="da689-114">4.6.2</span></span>       |
| <span data-ttu-id="da689-115">Tür</span><span class="sxs-lookup"><span data-stu-id="da689-115">Type</span></span>    | <span data-ttu-id="da689-116">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="da689-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="da689-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="da689-117">Affected APIs</span></span>

- <xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType>
