---
ms.openlocfilehash: 43e9c1c2f03daedf4d56152da5672b89399a3c69
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804667"
---
### <a name="vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a><span data-ttu-id="c2c5a-101">VB.NET kısmi ad niteliği System.Windows API'leri için artık desteklemektedir.</span><span class="sxs-lookup"><span data-stu-id="c2c5a-101">VB.NET no longer supports partial namespace qualification for System.Windows APIs</span></span>

|   |   |
|---|---|
|<span data-ttu-id="c2c5a-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="c2c5a-102">Details</span></span>|<span data-ttu-id="c2c5a-103">.NET Framework 4.5.2 başlayarak VB.NET projeleri System.Windows API'leri kısmen nitelenmiş ad alanları ile belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2c5a-103">Beginning in .NET Framework 4.5.2, VB.NET projects cannot specify System.Windows APIs with partially-qualified namespaces.</span></span> <span data-ttu-id="c2c5a-104">Örneğin, söz konusu <code>Windows.Forms.DialogResult</code> başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="c2c5a-104">For example, referring to <code>Windows.Forms.DialogResult</code> will fail.</span></span> <span data-ttu-id="c2c5a-105">Bunun yerine, kod tam adına başvurmak gerekir (<xref:System.Windows.Forms.DialogResult>) veya belirli ad alanını içeri aktarır ve başvurmak için yalnızca <xref:System.Windows.Forms.DialogResult?displayProperty=name>.</span><span class="sxs-lookup"><span data-stu-id="c2c5a-105">Instead, code must refer to the fully qualified name (<xref:System.Windows.Forms.DialogResult>) or import the specific namespace and refer simply to <xref:System.Windows.Forms.DialogResult?displayProperty=name>.</span></span>|
|<span data-ttu-id="c2c5a-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="c2c5a-106">Suggestion</span></span>|<span data-ttu-id="c2c5a-107">Kod başvurmak için güncelleştirilmesi gerektiğini <code>System.Windows</code> API'leri basit adları (ve ilgili ad alanı alma) veya tam olarak nitelenmiş adlar.</span><span class="sxs-lookup"><span data-stu-id="c2c5a-107">Code should be updated to refer to <code>System.Windows</code> APIs either with simple names (and importing the relevant namespace) or with fully qualified names.</span></span>|
|<span data-ttu-id="c2c5a-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="c2c5a-108">Scope</span></span>|<span data-ttu-id="c2c5a-109">İkincil</span><span class="sxs-lookup"><span data-stu-id="c2c5a-109">Minor</span></span>|
|<span data-ttu-id="c2c5a-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="c2c5a-110">Version</span></span>|<span data-ttu-id="c2c5a-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="c2c5a-111">4.5.2</span></span>|
|<span data-ttu-id="c2c5a-112">Tür</span><span class="sxs-lookup"><span data-stu-id="c2c5a-112">Type</span></span>|<span data-ttu-id="c2c5a-113">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="c2c5a-113">Retargeting</span></span>|

