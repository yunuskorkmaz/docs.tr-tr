---
ms.openlocfilehash: 5bbbf9075683b0f124e126b661b4ab85011e6c2e
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002999"
---
### <a name="change-of-access-for-accessibleobjectruntimeidfirstitem"></a><span data-ttu-id="b3447-101">Erişilebilir nesne. Runtimeıdfirtıtem için erişim değişikliği</span><span class="sxs-lookup"><span data-stu-id="b3447-101">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>

<span data-ttu-id="b3447-102">.NET Core 3,0 RC1 'den başlayarak, `AccessibleObject.RuntimeIDFirstItem` ' ı ' nin erişilebilirliği `protected` ' den `internal` ' ye değişti.</span><span class="sxs-lookup"><span data-stu-id="b3447-102">Starting in .NET Core 3.0 RC1, the accessibility of `AccessibleObject.RuntimeIDFirstItem` has changed from `protected` to `internal`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="b3447-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="b3447-103">Change description</span></span>

<span data-ttu-id="b3447-104">.NET Core 3,0 Preview 4 ' te başlayarak `AccessibleObject.RuntimeIDFirstItem` alanı `protected` idi.</span><span class="sxs-lookup"><span data-stu-id="b3447-104">Starting with .NET Core 3.0 Preview 4, the `AccessibleObject.RuntimeIDFirstItem` field was `protected`.</span></span> <span data-ttu-id="b3447-105">.NET Core 3,0 RC1 ile başlayarak, .NET Framework alanın erişilebilirliği ile hizalamak için `protected` ' dan `internal` ' e değişmiştir.</span><span class="sxs-lookup"><span data-stu-id="b3447-105">Starting with .NET Core 3.0 RC1, it has changed from `protected` to `internal` to align with the accessibility of the field in the .NET Framework.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b3447-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="b3447-106">Version introduced</span></span>

<span data-ttu-id="b3447-107">3,0 RC1</span><span class="sxs-lookup"><span data-stu-id="b3447-107">3.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b3447-108">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="b3447-108">Recommended action</span></span>

<span data-ttu-id="b3447-109">@No__t-0 ' dan türetilen ve `RuntimeIDFirstItem` alanına erişen bir türde .NET Core uygulaması geliştirdiyseniz değişiklik sizi etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="b3447-109">The change can affect you if you've developed a .NET Core app with a type that derives from <xref:System.Windows.Forms.AccessibleObject> and accesses the `RuntimeIDFirstItem` field.</span></span> <span data-ttu-id="b3447-110">Bu durumda, yerel bir sabiti şu şekilde tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b3447-110">If this is the case, you can define a local constant as follows:</span></span>

```csharp
const int RuntimeIDFirstItem = 0x2a;
```

#### <a name="category"></a><span data-ttu-id="b3447-111">Kategori</span><span class="sxs-lookup"><span data-stu-id="b3447-111">Category</span></span>

<span data-ttu-id="b3447-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b3447-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b3447-113">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="b3447-113">Affected APIs</span></span>

- <span data-ttu-id="b3447-114">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="b3447-114">Not detectable via API analysis.</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis.

-->
