---
ms.openlocfilehash: d1562cb76f37b6cc2aeb6fe2f7c17c393e169e84
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158494"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a><span data-ttu-id="48c31-101">InvalidAsynchronousStateException başka bir derlemeye taşındı</span><span class="sxs-lookup"><span data-stu-id="48c31-101">InvalidAsynchronousStateException moved to another assembly</span></span>

<span data-ttu-id="48c31-102"><xref:System.ComponentModel.InvalidAsynchronousStateException> Sınıf taşınmış.</span><span class="sxs-lookup"><span data-stu-id="48c31-102">The <xref:System.ComponentModel.InvalidAsynchronousStateException> class has been moved.</span></span>

#### <a name="change-description"></a><span data-ttu-id="48c31-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="48c31-103">Change description</span></span>

<span data-ttu-id="48c31-104">.NET Core 2,2 ve önceki sürümlerinde, <xref:System.ComponentModel.InvalidAsynchronousStateException> sınıfı *System. ComponentModel. TypeConverter* derlemesinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="48c31-104">In .NET Core 2.2 and earlier versions, the <xref:System.ComponentModel.InvalidAsynchronousStateException> class is found in the *System.ComponentModel.TypeConverter* assembly.</span></span>

<span data-ttu-id="48c31-105">.NET Core 3,0 ile başlayarak, *System. ComponentModel. ilkel* derleme derlemesinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="48c31-105">Starting with .NET Core 3.0, it is found in the *System.ComponentModel.Primitives* assembly.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="48c31-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="48c31-106">Version introduced</span></span>

<span data-ttu-id="48c31-107">3,0</span><span class="sxs-lookup"><span data-stu-id="48c31-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="48c31-108">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="48c31-108">Recommended action</span></span>

<span data-ttu-id="48c31-109">Bu değişiklik yalnızca, <xref:System.ComponentModel.InvalidAsynchronousStateException> gibi <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> bir yöntemi çağırarak ya da türün belirli bir derlemede olduğunu varsayan bir aşırı yüklemesi <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> çağırarak yüklemesi için yansıma kullanan uygulamaları etkiler.</span><span class="sxs-lookup"><span data-stu-id="48c31-109">This change only affects applications that use reflection to load the <xref:System.ComponentModel.InvalidAsynchronousStateException> by calling a method such as <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or an overload of <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> that assumes the type is in a particular assembly.</span></span> <span data-ttu-id="48c31-110">Bu durumda, yöntem çağrısında başvurulan derlemeyi, türün yeni derleme konumunu yansıtacak şekilde güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="48c31-110">If that is the case, update the assembly referenced in the method call to reflect the type's new assembly location.</span></span>

#### <a name="category"></a><span data-ttu-id="48c31-111">Kategori</span><span class="sxs-lookup"><span data-stu-id="48c31-111">Category</span></span>

<span data-ttu-id="48c31-112">Core .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="48c31-112">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="48c31-113">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="48c31-113">Affected APIs</span></span>

<span data-ttu-id="48c31-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="48c31-114">None.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->
