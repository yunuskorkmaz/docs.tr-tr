---
ms.openlocfilehash: 4d479636f41095610eaf39f92ad0dad4863ab8b5
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568125"
---
### <a name="typedescriptionproviderattribute-moved-to-another-assembly"></a><span data-ttu-id="e5b6b-101">TypeDescriptionProviderAttribute başka bir derlemeye taşındı</span><span class="sxs-lookup"><span data-stu-id="e5b6b-101">TypeDescriptionProviderAttribute moved to another assembly</span></span>

<span data-ttu-id="e5b6b-102"><xref:System.ComponentModel.TypeDescriptionProviderAttribute> sınıfı taşındı.</span><span class="sxs-lookup"><span data-stu-id="e5b6b-102">The <xref:System.ComponentModel.TypeDescriptionProviderAttribute> class has been moved.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e5b6b-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="e5b6b-103">Change description</span></span>

<span data-ttu-id="e5b6b-104">.NET Core 2,2 ve önceki sürümlerinde <xref:System.ComponentModel.TypeDescriptionProviderAttribute> sınıfı *System. ComponentModel. TypeConverter* derlemesinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="e5b6b-104">In .NET Core 2.2 and earlier versions, The <xref:System.ComponentModel.TypeDescriptionProviderAttribute> class is found in the *System.ComponentModel.TypeConverter* assembly.</span></span>

<span data-ttu-id="e5b6b-105">.NET Core 3,0 ile başlayarak, *System. ObjectModel* derlemesinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="e5b6b-105">Starting with .NET Core 3.0, it is found in the *System.ObjectModel* assembly.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e5b6b-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="e5b6b-106">Version introduced</span></span>

<span data-ttu-id="e5b6b-107">3.0</span><span class="sxs-lookup"><span data-stu-id="e5b6b-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e5b6b-108">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="e5b6b-108">Recommended action</span></span>

<span data-ttu-id="e5b6b-109">Bu değişiklik yalnızca, <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> gibi bir metodu veya türün belirli bir derlemede olduğunu varsayan <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> aşırı yüklemesini çağırarak <xref:System.ComponentModel.TypeDescriptionProviderAttribute> türünü yüklemek için yansıma kullanan uygulamaları etkiler.</span><span class="sxs-lookup"><span data-stu-id="e5b6b-109">This change only affects applications that use reflection to load the <xref:System.ComponentModel.TypeDescriptionProviderAttribute> type by calling a method such as <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or an overload of <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> that assumes the type is in a particular assembly.</span></span> <span data-ttu-id="e5b6b-110">Bu durumda, yöntem çağrısında başvurulan derleme, türün yeni derleme konumunu yansıtacak şekilde güncellenmelidir.</span><span class="sxs-lookup"><span data-stu-id="e5b6b-110">If that is the case, the assembly referenced in the method call should be updated to reflect the type's new assembly location.</span></span>

#### <a name="category"></a><span data-ttu-id="e5b6b-111">Kategori</span><span class="sxs-lookup"><span data-stu-id="e5b6b-111">Category</span></span>

<span data-ttu-id="e5b6b-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e5b6b-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e5b6b-113">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="e5b6b-113">Affected APIs</span></span>

- <span data-ttu-id="e5b6b-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="e5b6b-114">None</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->
