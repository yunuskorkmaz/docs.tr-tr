---
ms.openlocfilehash: 82835915efa0e113e81bb09bd5062ee3252f2a64
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568172"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a><span data-ttu-id="27e71-101">InvalidAsynchronousStateException başka bir derlemeye taşındı</span><span class="sxs-lookup"><span data-stu-id="27e71-101">InvalidAsynchronousStateException moved to another assembly</span></span>

<span data-ttu-id="27e71-102"><xref:System.ComponentModel.InvalidAsynchronousStateException> sınıfı taşındı.</span><span class="sxs-lookup"><span data-stu-id="27e71-102">The <xref:System.ComponentModel.InvalidAsynchronousStateException> class has been moved.</span></span>

#### <a name="change-description"></a><span data-ttu-id="27e71-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="27e71-103">Change description</span></span>

<span data-ttu-id="27e71-104">.NET Core 2,2 ve önceki sürümlerinde <xref:System.ComponentModel.InvalidAsynchronousStateException> sınıfı *System. ComponentModel. TypeConverter* derlemesinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="27e71-104">In .NET Core 2.2 and earlier versions, the <xref:System.ComponentModel.InvalidAsynchronousStateException> class is found in the *System.ComponentModel.TypeConverter* assembly.</span></span>

<span data-ttu-id="27e71-105">.NET Core 3,0 ile başlayarak, *System. ComponentModel. ilkel* derleme derlemesinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="27e71-105">Starting with .NET Core 3.0, it is found in the *System.ComponentModel.Primitives* assembly.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="27e71-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="27e71-106">Version introduced</span></span>

<span data-ttu-id="27e71-107">3.0</span><span class="sxs-lookup"><span data-stu-id="27e71-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="27e71-108">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="27e71-108">Recommended action</span></span>

<span data-ttu-id="27e71-109">Bu değişiklik yalnızca, <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> veya türün belirli bir derlemede olduğunu varsayan bir <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> aşırı yüklemesi çağırarak <xref:System.ComponentModel.InvalidAsynchronousStateException> yüklemek için yansıma kullanan uygulamaları etkiler.</span><span class="sxs-lookup"><span data-stu-id="27e71-109">This change only affects applications that use reflection to load the <xref:System.ComponentModel.InvalidAsynchronousStateException> by calling a method such as <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or an overload of <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> that assumes the type is in a particular assembly.</span></span> <span data-ttu-id="27e71-110">Böyle bir durumda, yöntem çağrısında başvurulan derlemenin, türün yeni derleme konumunu yansıtacak şekilde güncellenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="27e71-110">If that is the case, the assembly the assembly referenced in the method call should be updated to reflect the type's new assembly location.</span></span>

#### <a name="category"></a><span data-ttu-id="27e71-111">Kategori</span><span class="sxs-lookup"><span data-stu-id="27e71-111">Category</span></span>

<span data-ttu-id="27e71-112">CoreFx</span><span class="sxs-lookup"><span data-stu-id="27e71-112">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="27e71-113">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="27e71-113">Affected APIs</span></span>

- <span data-ttu-id="27e71-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="27e71-114">None</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->
