---
ms.openlocfilehash: 5bbbf9075683b0f124e126b661b4ab85011e6c2e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74644049"
---
### <a name="change-of-access-for-accessibleobjectruntimeidfirstitem"></a><span data-ttu-id="24684-101">ErişilebilirObject.RuntimeIDFirstItem için erişim değişikliği</span><span class="sxs-lookup"><span data-stu-id="24684-101">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>

<span data-ttu-id="24684-102">.NET Core 3.0 RC1'den `AccessibleObject.RuntimeIDFirstItem` `protected` başlayarak erişilebilirlik `internal`.</span><span class="sxs-lookup"><span data-stu-id="24684-102">Starting in .NET Core 3.0 RC1, the accessibility of `AccessibleObject.RuntimeIDFirstItem` has changed from `protected` to `internal`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="24684-103">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="24684-103">Change description</span></span>

<span data-ttu-id="24684-104">.NET Core 3.0 Preview 4 `AccessibleObject.RuntimeIDFirstItem` ile `protected`başlayarak, alan .</span><span class="sxs-lookup"><span data-stu-id="24684-104">Starting with .NET Core 3.0 Preview 4, the `AccessibleObject.RuntimeIDFirstItem` field was `protected`.</span></span> <span data-ttu-id="24684-105">.NET Core 3.0 RC1 ile başlayarak, .NET Framework'deki alanın erişilebilirliğiyle hizaya `protected` kadar `internal` değişti.</span><span class="sxs-lookup"><span data-stu-id="24684-105">Starting with .NET Core 3.0 RC1, it has changed from `protected` to `internal` to align with the accessibility of the field in the .NET Framework.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="24684-106">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="24684-106">Version introduced</span></span>

<span data-ttu-id="24684-107">3.0 RC1</span><span class="sxs-lookup"><span data-stu-id="24684-107">3.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="24684-108">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="24684-108">Recommended action</span></span>

<span data-ttu-id="24684-109">Bu değişiklik, <xref:System.Windows.Forms.AccessibleObject> `RuntimeIDFirstItem` alandan türemiş ve alana erişen bir türe sahip bir .NET Core uygulaması geliştirdiyseniz sizi etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="24684-109">The change can affect you if you've developed a .NET Core app with a type that derives from <xref:System.Windows.Forms.AccessibleObject> and accesses the `RuntimeIDFirstItem` field.</span></span> <span data-ttu-id="24684-110">Bu durumda, yerel bir sabiti aşağıdaki gibi tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="24684-110">If this is the case, you can define a local constant as follows:</span></span>

```csharp
const int RuntimeIDFirstItem = 0x2a;
```

#### <a name="category"></a><span data-ttu-id="24684-111">Kategori</span><span class="sxs-lookup"><span data-stu-id="24684-111">Category</span></span>

<span data-ttu-id="24684-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="24684-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="24684-113">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="24684-113">Affected APIs</span></span>

- <span data-ttu-id="24684-114">API analizi ile tespit edilemez.</span><span class="sxs-lookup"><span data-stu-id="24684-114">Not detectable via API analysis.</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis.

-->
