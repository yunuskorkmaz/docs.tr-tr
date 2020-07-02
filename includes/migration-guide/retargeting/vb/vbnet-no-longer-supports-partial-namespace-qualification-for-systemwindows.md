---
ms.openlocfilehash: cef8096c971da8ae245ff974697022f350cb9195
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616071"
---
### <a name="vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a><span data-ttu-id="f7f8c-101">VB.NET artık System. Windows API 'Leri için kısmi ad alanı nitelemesini desteklemiyor</span><span class="sxs-lookup"><span data-stu-id="f7f8c-101">VB.NET no longer supports partial namespace qualification for System.Windows APIs</span></span>

#### <a name="details"></a><span data-ttu-id="f7f8c-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="f7f8c-102">Details</span></span>

<span data-ttu-id="f7f8c-103">.NET Framework 4.5.2 ' den başlayarak, VB.NET projeleri kısmen nitelenmiş ad alanları olan System. Windows API 'Lerini belirtemez.</span><span class="sxs-lookup"><span data-stu-id="f7f8c-103">Beginning in .NET Framework 4.5.2, VB.NET projects cannot specify System.Windows APIs with partially-qualified namespaces.</span></span> <span data-ttu-id="f7f8c-104">Örneğin, öğesine başvurma `Windows.Forms.DialogResult` başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="f7f8c-104">For example, referring to `Windows.Forms.DialogResult` will fail.</span></span> <span data-ttu-id="f7f8c-105">Bunun yerine, kod tam olarak nitelenmiş ada () başvurmalıdır <xref:System.Windows.Forms.DialogResult> veya belirli ad alanını içeri aktarıp yalnızca öğesine başvurmalıdır <xref:System.Windows.Forms.DialogResult?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="f7f8c-105">Instead, code must refer to the fully qualified name (<xref:System.Windows.Forms.DialogResult>) or import the specific namespace and refer simply to <xref:System.Windows.Forms.DialogResult?displayProperty=fullName>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f7f8c-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="f7f8c-106">Suggestion</span></span>

<span data-ttu-id="f7f8c-107">Kod `System.Windows` , basit adlarla (ve ilgili ad alanını içeri aktararak) veya tam nitelikli adlara sahip API 'lere başvuracak şekilde güncelleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="f7f8c-107">Code should be updated to refer to `System.Windows` APIs either with simple names (and importing the relevant namespace) or with fully qualified names.</span></span>

| <span data-ttu-id="f7f8c-108">Name</span><span class="sxs-lookup"><span data-stu-id="f7f8c-108">Name</span></span>    | <span data-ttu-id="f7f8c-109">Değer</span><span class="sxs-lookup"><span data-stu-id="f7f8c-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f7f8c-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="f7f8c-110">Scope</span></span>   | <span data-ttu-id="f7f8c-111">İkincil</span><span class="sxs-lookup"><span data-stu-id="f7f8c-111">Minor</span></span>       |
| <span data-ttu-id="f7f8c-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="f7f8c-112">Version</span></span> | <span data-ttu-id="f7f8c-113">4.5.2</span><span class="sxs-lookup"><span data-stu-id="f7f8c-113">4.5.2</span></span>       |
| <span data-ttu-id="f7f8c-114">Tür</span><span class="sxs-lookup"><span data-stu-id="f7f8c-114">Type</span></span>    | <span data-ttu-id="f7f8c-115">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="f7f8c-115">Retargeting</span></span> |
