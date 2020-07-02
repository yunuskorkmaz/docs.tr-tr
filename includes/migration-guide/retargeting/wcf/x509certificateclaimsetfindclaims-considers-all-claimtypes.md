---
ms.openlocfilehash: abef47c64a7cfd99c5b50bf2100401a2d5fcc5c3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614738"
---
### <a name="x509certificateclaimsetfindclaims-considers-all-claimtypes"></a><span data-ttu-id="90c88-101">X509CertificateClaimSet. Findclaim tüm claimTypes 'ı kabul eder</span><span class="sxs-lookup"><span data-stu-id="90c88-101">X509CertificateClaimSet.FindClaims Considers All claimTypes</span></span>

#### <a name="details"></a><span data-ttu-id="90c88-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="90c88-102">Details</span></span>

<span data-ttu-id="90c88-103">.NET Framework 4.6.1 hedefleyen uygulamalarda, bir x509 talep kümesi, SAN alanında birden çok DNS girişi olan bir sertifikadan başlatılmışsa, <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=fullName> yöntemi tüm DNS girişleriyle birlikte ClaimType bağımsız değişkenini eşleştirmeye çalışır. .NET Framework önceki sürümlerini hedefleyen uygulamalar için, <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=fullName> yöntemi yalnızca son DNS girdisiyle birlikte ClaimType bağımsız değişkenini eşleştirmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="90c88-103">In apps that target the .NET Framework 4.6.1, if an X509 claim set is initialized from a certificate that has multiple DNS entries in its SAN field, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=fullName> method attempts to match the claimType argument with all the DNS entries.For apps that target previous versions of the .NET Framework, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=fullName> method attempts to match the claimType argument only with the last DNS entry.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="90c88-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="90c88-104">Suggestion</span></span>

<span data-ttu-id="90c88-105">Bu değişiklik yalnızca .NET Framework 4.6.1 hedefleyen uygulamaları etkiler.</span><span class="sxs-lookup"><span data-stu-id="90c88-105">This change only affects applications targeting the .NET Framework 4.6.1.</span></span> <span data-ttu-id="90c88-106">Bu değişiklik, [Disablemultiplednsendenemeler](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md#mitigation) uyumluluk anahtarıyla devre dışı bırakılabilir (veya ön 4.6.1 hedefleniyorsa etkinleştirilebilir).</span><span class="sxs-lookup"><span data-stu-id="90c88-106">This change may be disabled (or enabled if targeting pre-4.6.1) with the [DisableMultipleDNSEntries](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md#mitigation) compatibility switch.</span></span>

| <span data-ttu-id="90c88-107">Name</span><span class="sxs-lookup"><span data-stu-id="90c88-107">Name</span></span>    | <span data-ttu-id="90c88-108">Değer</span><span class="sxs-lookup"><span data-stu-id="90c88-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="90c88-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="90c88-109">Scope</span></span>   | <span data-ttu-id="90c88-110">İkincil</span><span class="sxs-lookup"><span data-stu-id="90c88-110">Minor</span></span>       |
| <span data-ttu-id="90c88-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="90c88-111">Version</span></span> | <span data-ttu-id="90c88-112">4.6.1</span><span class="sxs-lookup"><span data-stu-id="90c88-112">4.6.1</span></span>       |
| <span data-ttu-id="90c88-113">Tür</span><span class="sxs-lookup"><span data-stu-id="90c88-113">Type</span></span>    | <span data-ttu-id="90c88-114">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="90c88-114">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="90c88-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="90c88-115">Affected APIs</span></span>

- <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=nameWithType>
