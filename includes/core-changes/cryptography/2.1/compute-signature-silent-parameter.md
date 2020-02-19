---
ms.openlocfilehash: 9583d868ee01117d7bd6e465e7d89a734489d1a8
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449238"
---
### <a name="boolean-parameter-of-signedcmscomputesignature-is-respected"></a><span data-ttu-id="28af4-101">SignedCms. ComputeSignature Boolean parametresi dikkate alındı</span><span class="sxs-lookup"><span data-stu-id="28af4-101">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>

<span data-ttu-id="28af4-102">.NET Core 'da <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> yönteminin Boole `silent` parametresi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="28af4-102">In .NET Core, the Boolean `silent` parameter of the <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> method is respected.</span></span> <span data-ttu-id="28af4-103">Bu parametre `true`olarak ayarlandıysa bir PIN istemi gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="28af4-103">A PIN prompt is not shown if this parameter is set to `true`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="28af4-104">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="28af4-104">Change description</span></span>

<span data-ttu-id="28af4-105">.NET Framework, <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> yönteminin `silent` parametresi yok sayılır ve sağlayıcı tarafından gerekliyse bir PIN istemi her zaman gösterilir.</span><span class="sxs-lookup"><span data-stu-id="28af4-105">In .NET Framework, the `silent` parameter of the <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> method is ignored, and a PIN prompt is always shown if required by the provider.</span></span> <span data-ttu-id="28af4-106">.NET Core 'da `silent` parametresi dikkate alınsa da, `true`olarak ayarlanırsa, sağlayıcı için gerekli olsa bile bir PIN istemi gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="28af4-106">In .NET Core, the `silent` parameter is respected, and if set to `true`, a PIN prompt is never shown, even if it's required by the provider.</span></span>

<span data-ttu-id="28af4-107">CMS/PKCS #7 iletileri için destek, sürüm 2,1 ' de .NET Core ' a eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="28af4-107">Support for CMS/PKCS #7 messages was introduced into .NET Core in version 2.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="28af4-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="28af4-108">Version introduced</span></span>

<span data-ttu-id="28af4-109">2.1</span><span class="sxs-lookup"><span data-stu-id="28af4-109">2.1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="28af4-110">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="28af4-110">Recommended action</span></span>

<span data-ttu-id="28af4-111">Gerektiğinde bir PIN isteminin göründüğünden emin olmak için, masaüstü uygulamaları <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> çağırmalıdır ve Boole parametresini `false`olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="28af4-111">To ensure a PIN prompt appears if required, desktop applications should call <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> and set the Boolean parameter to `false`.</span></span> <span data-ttu-id="28af4-112">Elde edilen davranış, sessiz bağlamın orada devre dışı bırakılıp bırakılmadığına bakılmaksızın .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="28af4-112">The resulting behavior is the same as on .NET Framework regardless of whether the silent context is disabled there.</span></span>

### <a name="category"></a><span data-ttu-id="28af4-113">Kategori</span><span class="sxs-lookup"><span data-stu-id="28af4-113">Category</span></span>

<span data-ttu-id="28af4-114">Şifreleme</span><span class="sxs-lookup"><span data-stu-id="28af4-114">Cryptography</span></span>

### <a name="affected-apis"></a><span data-ttu-id="28af4-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="28af4-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)`

-->
