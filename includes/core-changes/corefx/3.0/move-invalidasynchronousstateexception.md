---
ms.openlocfilehash: 78678b4b352bb063d1521e9aee3492c0cee059b8
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721523"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a><span data-ttu-id="4e7ed-101">InvalidAsynchronousStateException başka bir derlemeye taşındı</span><span class="sxs-lookup"><span data-stu-id="4e7ed-101">InvalidAsynchronousStateException moved to another assembly</span></span>

<span data-ttu-id="4e7ed-102"><xref:System.ComponentModel.InvalidAsynchronousStateException>Sınıf taşınmış.</span><span class="sxs-lookup"><span data-stu-id="4e7ed-102">The <xref:System.ComponentModel.InvalidAsynchronousStateException> class has been moved.</span></span>

#### <a name="change-description"></a><span data-ttu-id="4e7ed-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="4e7ed-103">Change description</span></span>

<span data-ttu-id="4e7ed-104">.NET Core 2,2 ve önceki sürümlerinde, <xref:System.ComponentModel.InvalidAsynchronousStateException> sınıfı *System. ComponentModel. TypeConverter* derlemesinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="4e7ed-104">In .NET Core 2.2 and earlier versions, the <xref:System.ComponentModel.InvalidAsynchronousStateException> class is found in the *System.ComponentModel.TypeConverter* assembly.</span></span>

<span data-ttu-id="4e7ed-105">.NET Core 3,0 ile başlayarak, *System. ComponentModel. ilkel* derleme derlemesinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="4e7ed-105">Starting with .NET Core 3.0, it is found in the *System.ComponentModel.Primitives* assembly.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4e7ed-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="4e7ed-106">Version introduced</span></span>

<span data-ttu-id="4e7ed-107">3.0</span><span class="sxs-lookup"><span data-stu-id="4e7ed-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4e7ed-108">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="4e7ed-108">Recommended action</span></span>

<span data-ttu-id="4e7ed-109">Bu değişiklik yalnızca, <xref:System.ComponentModel.InvalidAsynchronousStateException> gibi bir yöntemi çağırarak <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> ya da türün belirli bir derlemede olduğunu varsayan bir aşırı yüklemesi çağırarak yüklemesi için yansıma kullanan uygulamaları etkiler <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="4e7ed-109">This change only affects applications that use reflection to load the <xref:System.ComponentModel.InvalidAsynchronousStateException> by calling a method such as <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or an overload of <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> that assumes the type is in a particular assembly.</span></span> <span data-ttu-id="4e7ed-110">Bu durumda, yöntem çağrısında başvurulan derlemeyi, türün yeni derleme konumunu yansıtacak şekilde güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="4e7ed-110">If that is the case, update the assembly referenced in the method call to reflect the type's new assembly location.</span></span>

#### <a name="category"></a><span data-ttu-id="4e7ed-111">Kategori</span><span class="sxs-lookup"><span data-stu-id="4e7ed-111">Category</span></span>

<span data-ttu-id="4e7ed-112">Core .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="4e7ed-112">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4e7ed-113">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="4e7ed-113">Affected APIs</span></span>

<span data-ttu-id="4e7ed-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="4e7ed-114">None.</span></span>

<!--

#### Affected APIs

- Not detectable via API analysis

-->
