---
ms.openlocfilehash: 8db115a46df3fcea103e8fa6896542d0116aa256
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804667"
---
### <a name="vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a><span data-ttu-id="9a035-101">VB.NET artık System.Windows API'leri için kısmi ad alanı niteliğini desteklemiyor</span><span class="sxs-lookup"><span data-stu-id="9a035-101">VB.NET no longer supports partial namespace qualification for System.Windows APIs</span></span>

|   |   |
|---|---|
|<span data-ttu-id="9a035-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="9a035-102">Details</span></span>|<span data-ttu-id="9a035-103">.NET Framework 4.5.2'den başlayarak, VB.NET projeler system.windows API'lerini kısmen nitelikli ad boşluklarıyla belirtemez.</span><span class="sxs-lookup"><span data-stu-id="9a035-103">Beginning in .NET Framework 4.5.2, VB.NET projects cannot specify System.Windows APIs with partially-qualified namespaces.</span></span> <span data-ttu-id="9a035-104">Örneğin, atıfta başarısız <code>Windows.Forms.DialogResult</code> olur.</span><span class="sxs-lookup"><span data-stu-id="9a035-104">For example, referring to <code>Windows.Forms.DialogResult</code> will fail.</span></span> <span data-ttu-id="9a035-105">Bunun yerine, kod tam nitelikli<xref:System.Windows.Forms.DialogResult>adı () veya belirli ad <xref:System.Windows.Forms.DialogResult?displayProperty=name>alanını alma ve yalnızca .</span><span class="sxs-lookup"><span data-stu-id="9a035-105">Instead, code must refer to the fully qualified name (<xref:System.Windows.Forms.DialogResult>) or import the specific namespace and refer simply to <xref:System.Windows.Forms.DialogResult?displayProperty=name>.</span></span>|
|<span data-ttu-id="9a035-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="9a035-106">Suggestion</span></span>|<span data-ttu-id="9a035-107">Kod, <code>System.Windows</code> BASIT adlarla (ve ilgili ad alanını alma) veya tam nitelikli adlarla API'lere başvurmak üzere güncelleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="9a035-107">Code should be updated to refer to <code>System.Windows</code> APIs either with simple names (and importing the relevant namespace) or with fully qualified names.</span></span>|
|<span data-ttu-id="9a035-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="9a035-108">Scope</span></span>|<span data-ttu-id="9a035-109">İkincil</span><span class="sxs-lookup"><span data-stu-id="9a035-109">Minor</span></span>|
|<span data-ttu-id="9a035-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="9a035-110">Version</span></span>|<span data-ttu-id="9a035-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="9a035-111">4.5.2</span></span>|
|<span data-ttu-id="9a035-112">Tür</span><span class="sxs-lookup"><span data-stu-id="9a035-112">Type</span></span>|<span data-ttu-id="9a035-113">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="9a035-113">Retargeting</span></span>|
