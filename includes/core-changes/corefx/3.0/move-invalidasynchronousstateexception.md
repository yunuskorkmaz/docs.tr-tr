---
ms.openlocfilehash: ace0a4a60ad4d3f3a13cf4bdb2431e61d04ad8e7
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021610"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a><span data-ttu-id="94de1-101">GeçersizAsynchronousStateException başka bir derlemetaşındı</span><span class="sxs-lookup"><span data-stu-id="94de1-101">InvalidAsynchronousStateException moved to another assembly</span></span>

<span data-ttu-id="94de1-102">Sınıf <xref:System.ComponentModel.InvalidAsynchronousStateException> taşındı.</span><span class="sxs-lookup"><span data-stu-id="94de1-102">The <xref:System.ComponentModel.InvalidAsynchronousStateException> class has been moved.</span></span>

#### <a name="change-description"></a><span data-ttu-id="94de1-103">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="94de1-103">Change description</span></span>

<span data-ttu-id="94de1-104">.NET Core 2.2 ve önceki <xref:System.ComponentModel.InvalidAsynchronousStateException> sürümlerinde, sınıf *System.ComponentModel.TypeConverter* derlemesinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="94de1-104">In .NET Core 2.2 and earlier versions, the <xref:System.ComponentModel.InvalidAsynchronousStateException> class is found in the *System.ComponentModel.TypeConverter* assembly.</span></span>

<span data-ttu-id="94de1-105">.NET Core 3.0 ile başlayarak *System.ComponentModel.Primitives* derlemesinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="94de1-105">Starting with .NET Core 3.0, it is found in the *System.ComponentModel.Primitives* assembly.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="94de1-106">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="94de1-106">Version introduced</span></span>

<span data-ttu-id="94de1-107">3,0</span><span class="sxs-lookup"><span data-stu-id="94de1-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="94de1-108">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="94de1-108">Recommended action</span></span>

<span data-ttu-id="94de1-109">Bu değişiklik yalnızca, tür belirli bir <xref:System.ComponentModel.InvalidAsynchronousStateException> derlemede olduğunu <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> varsayar gibi <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> bir yöntem veya aşırı yük çağırarak yüklemek için yansıma kullanan uygulamaları etkiler.</span><span class="sxs-lookup"><span data-stu-id="94de1-109">This change only affects applications that use reflection to load the <xref:System.ComponentModel.InvalidAsynchronousStateException> by calling a method such as <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or an overload of <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> that assumes the type is in a particular assembly.</span></span> <span data-ttu-id="94de1-110">Bu durumda, yöntem çağrısında başvurulan derleme derleme sürünün yeni derleme konumunu yansıtacak şekilde güncelleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="94de1-110">If that is the case, the assembly the assembly referenced in the method call should be updated to reflect the type's new assembly location.</span></span>

#### <a name="category"></a><span data-ttu-id="94de1-111">Kategori</span><span class="sxs-lookup"><span data-stu-id="94de1-111">Category</span></span>

<span data-ttu-id="94de1-112">Çekirdek .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="94de1-112">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="94de1-113">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="94de1-113">Affected APIs</span></span>

<span data-ttu-id="94de1-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="94de1-114">None.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->
