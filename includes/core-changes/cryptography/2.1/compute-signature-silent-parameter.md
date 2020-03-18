---
ms.openlocfilehash: 9583d868ee01117d7bd6e465e7d89a734489d1a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449238"
---
### <a name="boolean-parameter-of-signedcmscomputesignature-is-respected"></a><span data-ttu-id="cad4e-101">İmzaCms.ComputeSignature boolean parametre saygı duyulur</span><span class="sxs-lookup"><span data-stu-id="cad4e-101">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>

<span data-ttu-id="cad4e-102">.NET Core'da yöntemin `silent` Boolean <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> parametresi saygı duyulur.</span><span class="sxs-lookup"><span data-stu-id="cad4e-102">In .NET Core, the Boolean `silent` parameter of the <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> method is respected.</span></span> <span data-ttu-id="cad4e-103">Bu parametre ' ye `true`ayarlanmışsa PIN istemi gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="cad4e-103">A PIN prompt is not shown if this parameter is set to `true`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="cad4e-104">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="cad4e-104">Change description</span></span>

<span data-ttu-id="cad4e-105">.NET Framework'de `silent` yöntemin <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> parametresi yoksayılır ve sağlayıcı tarafından gerekirse her zaman pin istemi gösterilir.</span><span class="sxs-lookup"><span data-stu-id="cad4e-105">In .NET Framework, the `silent` parameter of the <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> method is ignored, and a PIN prompt is always shown if required by the provider.</span></span> <span data-ttu-id="cad4e-106">.NET Core'da `silent` parametreye saygı gösterilir ve `true`ayarlanmışsa, sağlayıcı tarafından gerekli olsa bile pin istemi hiçbir zaman gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="cad4e-106">In .NET Core, the `silent` parameter is respected, and if set to `true`, a PIN prompt is never shown, even if it's required by the provider.</span></span>

<span data-ttu-id="cad4e-107">CMS/PKCS #7 mesajları için destek .NET Core sürüm 2.1'de tanıtıldı.</span><span class="sxs-lookup"><span data-stu-id="cad4e-107">Support for CMS/PKCS #7 messages was introduced into .NET Core in version 2.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="cad4e-108">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="cad4e-108">Version introduced</span></span>

<span data-ttu-id="cad4e-109">2.1</span><span class="sxs-lookup"><span data-stu-id="cad4e-109">2.1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="cad4e-110">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="cad4e-110">Recommended action</span></span>

<span data-ttu-id="cad4e-111">Gerekirse PIN isteminin görüntülediğinden emin olmak <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> için masaüstü uygulamaları Boolean `false`parametresini aramalı ve 'ye ayarlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="cad4e-111">To ensure a PIN prompt appears if required, desktop applications should call <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> and set the Boolean parameter to `false`.</span></span> <span data-ttu-id="cad4e-112">Ortaya çıkan davranış, sessiz bağlamın devre dışı kalıp olmadığına bakılmaksızın .NET Framework'dekiyle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="cad4e-112">The resulting behavior is the same as on .NET Framework regardless of whether the silent context is disabled there.</span></span>

### <a name="category"></a><span data-ttu-id="cad4e-113">Kategori</span><span class="sxs-lookup"><span data-stu-id="cad4e-113">Category</span></span>

<span data-ttu-id="cad4e-114">Şifreleme</span><span class="sxs-lookup"><span data-stu-id="cad4e-114">Cryptography</span></span>

### <a name="affected-apis"></a><span data-ttu-id="cad4e-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="cad4e-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)`

-->
