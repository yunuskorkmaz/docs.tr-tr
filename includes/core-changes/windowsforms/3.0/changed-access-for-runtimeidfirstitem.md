---
ms.openlocfilehash: 1ea2d70a7cfe04cc4c4b9b58ea6bb6fa0226b245
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721172"
---
### <a name="change-of-access-for-accessibleobjectruntimeidfirstitem"></a><span data-ttu-id="44ec6-101">Erişilebilir nesne. Runtimeıdfirtıtem için erişim değişikliği</span><span class="sxs-lookup"><span data-stu-id="44ec6-101">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>

<span data-ttu-id="44ec6-102">.NET Core 3,0 RC1 'den başlayarak, uygulamasının erişilebilirliği `AccessibleObject.RuntimeIDFirstItem` `protected` olarak değiştirilmiştir `internal` .</span><span class="sxs-lookup"><span data-stu-id="44ec6-102">Starting in .NET Core 3.0 RC1, the accessibility of `AccessibleObject.RuntimeIDFirstItem` has changed from `protected` to `internal`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="44ec6-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="44ec6-103">Change description</span></span>

<span data-ttu-id="44ec6-104">.NET Core 3,0 Preview 4 ' ü kullanmaya başlama `AccessibleObject.RuntimeIDFirstItem` alanı `protected` .</span><span class="sxs-lookup"><span data-stu-id="44ec6-104">Starting with .NET Core 3.0 Preview 4, the `AccessibleObject.RuntimeIDFirstItem` field was `protected`.</span></span> <span data-ttu-id="44ec6-105">.NET Core 3,0 RC1 'den başlayarak, `protected` `internal` .NET Framework alanın erişilebilirliği ile hizalanacak şekilde değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="44ec6-105">Starting with .NET Core 3.0 RC1, it has changed from `protected` to `internal` to align with the accessibility of the field in the .NET Framework.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="44ec6-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="44ec6-106">Version introduced</span></span>

<span data-ttu-id="44ec6-107">3,0 RC1</span><span class="sxs-lookup"><span data-stu-id="44ec6-107">3.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="44ec6-108">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="44ec6-108">Recommended action</span></span>

<span data-ttu-id="44ec6-109">' Dan türetilmiş <xref:System.Windows.Forms.AccessibleObject> ve alanla erişilen bir tür ile .NET Core uygulaması geliştirdiyseniz değişiklik sizi etkileyebilir `RuntimeIDFirstItem` .</span><span class="sxs-lookup"><span data-stu-id="44ec6-109">The change can affect you if you've developed a .NET Core app with a type that derives from <xref:System.Windows.Forms.AccessibleObject> and accesses the `RuntimeIDFirstItem` field.</span></span> <span data-ttu-id="44ec6-110">Bu durumda, yerel bir sabiti şu şekilde tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="44ec6-110">If this is the case, you can define a local constant as follows:</span></span>

```csharp
const int RuntimeIDFirstItem = 0x2a;
```

#### <a name="category"></a><span data-ttu-id="44ec6-111">Kategori</span><span class="sxs-lookup"><span data-stu-id="44ec6-111">Category</span></span>

<span data-ttu-id="44ec6-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="44ec6-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="44ec6-113">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="44ec6-113">Affected APIs</span></span>

- <span data-ttu-id="44ec6-114">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="44ec6-114">Not detectable via API analysis.</span></span>

<!-- 

#### Affected APIs

- Not detectable via API analysis.

-->
