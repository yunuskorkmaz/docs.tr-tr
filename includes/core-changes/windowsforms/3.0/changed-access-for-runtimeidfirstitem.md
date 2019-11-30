---
ms.openlocfilehash: 5bbbf9075683b0f124e126b661b4ab85011e6c2e
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644049"
---
### <a name="change-of-access-for-accessibleobjectruntimeidfirstitem"></a><span data-ttu-id="d8cd0-101">Erişilebilir nesne. Runtimeıdfirtıtem için erişim değişikliği</span><span class="sxs-lookup"><span data-stu-id="d8cd0-101">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>

<span data-ttu-id="d8cd0-102">.NET Core 3,0 RC1 'den başlayarak `AccessibleObject.RuntimeIDFirstItem` erişilebilirliği `protected` `internal`olarak değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d8cd0-102">Starting in .NET Core 3.0 RC1, the accessibility of `AccessibleObject.RuntimeIDFirstItem` has changed from `protected` to `internal`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d8cd0-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="d8cd0-103">Change description</span></span>

<span data-ttu-id="d8cd0-104">.NET Core 3,0 Preview 4 ' te başlayarak `AccessibleObject.RuntimeIDFirstItem` alanı `protected`.</span><span class="sxs-lookup"><span data-stu-id="d8cd0-104">Starting with .NET Core 3.0 Preview 4, the `AccessibleObject.RuntimeIDFirstItem` field was `protected`.</span></span> <span data-ttu-id="d8cd0-105">.NET Core 3,0 RC1 ile başlayarak, .NET Framework alanın erişilebilirliği ile hizalamak için `protected` `internal` olarak değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d8cd0-105">Starting with .NET Core 3.0 RC1, it has changed from `protected` to `internal` to align with the accessibility of the field in the .NET Framework.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d8cd0-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="d8cd0-106">Version introduced</span></span>

<span data-ttu-id="d8cd0-107">3,0 RC1</span><span class="sxs-lookup"><span data-stu-id="d8cd0-107">3.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d8cd0-108">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="d8cd0-108">Recommended action</span></span>

<span data-ttu-id="d8cd0-109"><xref:System.Windows.Forms.AccessibleObject> bir .NET Core uygulamasını geliştirdiyseniz ve `RuntimeIDFirstItem` alanına eriştiğinde bu değişiklik sizi etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="d8cd0-109">The change can affect you if you've developed a .NET Core app with a type that derives from <xref:System.Windows.Forms.AccessibleObject> and accesses the `RuntimeIDFirstItem` field.</span></span> <span data-ttu-id="d8cd0-110">Bu durumda, yerel bir sabiti şu şekilde tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d8cd0-110">If this is the case, you can define a local constant as follows:</span></span>

```csharp
const int RuntimeIDFirstItem = 0x2a;
```

#### <a name="category"></a><span data-ttu-id="d8cd0-111">Kategori</span><span class="sxs-lookup"><span data-stu-id="d8cd0-111">Category</span></span>

<span data-ttu-id="d8cd0-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d8cd0-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d8cd0-113">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="d8cd0-113">Affected APIs</span></span>

- <span data-ttu-id="d8cd0-114">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="d8cd0-114">Not detectable via API analysis.</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis.

-->
