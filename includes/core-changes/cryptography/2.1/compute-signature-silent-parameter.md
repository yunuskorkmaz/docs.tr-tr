---
ms.openlocfilehash: b861dbaa02c97a03c015fdf4e63d25c40c90ea0a
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721553"
---
### <a name="boolean-parameter-of-signedcmscomputesignature-is-respected"></a><span data-ttu-id="9bb4b-101">SignedCms. ComputeSignature Boolean parametresi dikkate alındı</span><span class="sxs-lookup"><span data-stu-id="9bb4b-101">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>

<span data-ttu-id="9bb4b-102">.NET Core 'da `silent` yöntemin Boolean parametresi <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> dikkate alındı.</span><span class="sxs-lookup"><span data-stu-id="9bb4b-102">In .NET Core, the Boolean `silent` parameter of the <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> method is respected.</span></span> <span data-ttu-id="9bb4b-103">Bu parametre olarak ayarlandıysa, bir PIN istemi gösterilmez `true` .</span><span class="sxs-lookup"><span data-stu-id="9bb4b-103">A PIN prompt is not shown if this parameter is set to `true`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="9bb4b-104">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="9bb4b-104">Change description</span></span>

<span data-ttu-id="9bb4b-105">.NET Framework, `silent` <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> yönteminin parametresi yok sayılır ve sağlayıcı tarafından GEREKLIYSE bir PIN istemi her zaman gösterilir.</span><span class="sxs-lookup"><span data-stu-id="9bb4b-105">In .NET Framework, the `silent` parameter of the <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> method is ignored, and a PIN prompt is always shown if required by the provider.</span></span> <span data-ttu-id="9bb4b-106">.NET Core 'da `silent` parametre dikkate alınsa da, olarak ayarlandıysa `true` , sağlayıcı için gerekli olsa bıle bir PIN istemi hiçbir şekilde gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="9bb4b-106">In .NET Core, the `silent` parameter is respected, and if set to `true`, a PIN prompt is never shown, even if it's required by the provider.</span></span>

<span data-ttu-id="9bb4b-107">CMS/PKCS #7 iletileri için destek, sürüm 2,1 ' de .NET Core ' a eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="9bb4b-107">Support for CMS/PKCS #7 messages was introduced into .NET Core in version 2.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9bb4b-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="9bb4b-108">Version introduced</span></span>

<span data-ttu-id="9bb4b-109">2.1</span><span class="sxs-lookup"><span data-stu-id="9bb4b-109">2.1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9bb4b-110">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="9bb4b-110">Recommended action</span></span>

<span data-ttu-id="9bb4b-111">Gerekirse, bir PIN isteminin göründüğünden emin olmak için, masaüstü uygulamaları, <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> Boole parametresini çağırmalıdır ve olarak ayarlanmalıdır `false` .</span><span class="sxs-lookup"><span data-stu-id="9bb4b-111">To ensure a PIN prompt appears if required, desktop applications should call <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> and set the Boolean parameter to `false`.</span></span> <span data-ttu-id="9bb4b-112">Elde edilen davranış, sessiz bağlamın orada devre dışı bırakılıp bırakılmadığına bakılmaksızın .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9bb4b-112">The resulting behavior is the same as on .NET Framework regardless of whether the silent context is disabled there.</span></span>

#### <a name="category"></a><span data-ttu-id="9bb4b-113">Kategori</span><span class="sxs-lookup"><span data-stu-id="9bb4b-113">Category</span></span>

<span data-ttu-id="9bb4b-114">Şifreleme</span><span class="sxs-lookup"><span data-stu-id="9bb4b-114">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9bb4b-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="9bb4b-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)`

-->
