---
ms.openlocfilehash: 43ebb37124b8efe077b9f81fe5351bd7db2c72f7
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302730"
---
### <a name="vectort-always-throws-notsupportedexception-for-unsupported-types"></a><span data-ttu-id="81b1c-101">Vektör, \<T> Desteklenmeyen türler için her zaman NotSupportedException oluşturur</span><span class="sxs-lookup"><span data-stu-id="81b1c-101">Vector\<T> always throws NotSupportedException for unsupported types</span></span>

<span data-ttu-id="81b1c-102"><xref:System.Numerics.Vector%601?displayProperty=nameWithType>Artık, <xref:System.NotSupportedException> desteklenmeyen tür parametreleri için her zaman bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="81b1c-102"><xref:System.Numerics.Vector%601?displayProperty=nameWithType> now always throws a <xref:System.NotSupportedException> for unsupported type parameters.</span></span>

#### <a name="change-description"></a><span data-ttu-id="81b1c-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="81b1c-103">Change description</span></span>

<span data-ttu-id="81b1c-104">Daha önce, üyeleri <xref:System.Numerics.Vector%601> <xref:System.NotSupportedException> Desteklenmeyen bir tür olduğunda her zaman bir oluşturmaz `T` . [unsupported type](#unsupported-types)</span><span class="sxs-lookup"><span data-stu-id="81b1c-104">Previously, members of <xref:System.Numerics.Vector%601> would not always throw a <xref:System.NotSupportedException> when `T` was an [unsupported type](#unsupported-types).</span></span> <span data-ttu-id="81b1c-105">Donanım hızlandırmasının desteklediği kod yolları nedeniyle özel durum her zaman oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="81b1c-105">The exception wasn't always thrown because of code paths that supported hardware acceleration.</span></span> <span data-ttu-id="81b1c-106">Örneğin, `Vector<bool> + Vector<bool>` ARM32 gibi `default` donanım hızlandırmayan platformlarda bir özel durum oluşturmak yerine döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="81b1c-106">For example, `Vector<bool> + Vector<bool>` returned `default` instead of throwing an exception on platforms that have no hardware acceleration, such as ARM32.</span></span> <span data-ttu-id="81b1c-107">Desteklenmeyen türler için, <xref:System.Numerics.Vector%601> Üyeler farklı platformlarda ve donanım yapılandırmalarında tutarsız davranışlar sergilen.</span><span class="sxs-lookup"><span data-stu-id="81b1c-107">For unsupported types, <xref:System.Numerics.Vector%601> members exhibited inconsistent behavior across different platforms and hardware configurations.</span></span>

<span data-ttu-id="81b1c-108">.NET 5,0 ' den başlayarak, <xref:System.Numerics.Vector%601> Üyeler <xref:System.NotSupportedException> `T` desteklenen bir tür olmadığında her zaman tüm donanım yapılandırmalarında bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="81b1c-108">Starting in .NET 5.0, <xref:System.Numerics.Vector%601> members always throw a <xref:System.NotSupportedException> on all hardware configurations when `T` is not a supported type.</span></span>

##### <a name="unsupported-types"></a><span data-ttu-id="81b1c-109">Desteklenmeyen türler</span><span class="sxs-lookup"><span data-stu-id="81b1c-109">Unsupported types</span></span>

<span data-ttu-id="81b1c-110">Tür parametresi için desteklenen türler <xref:System.Numerics.Vector%601> şunlardır:</span><span class="sxs-lookup"><span data-stu-id="81b1c-110">The supported types for the type parameter of <xref:System.Numerics.Vector%601> are:</span></span>

- `byte`
- `sbyte`
- `short`
- `ushort`
- `int`
- `uint`
- `long`
- `ulong`
- `float`
- `double`

<span data-ttu-id="81b1c-111">Desteklenen türler değişmemiştir, ancak gelecekte değişebilir.</span><span class="sxs-lookup"><span data-stu-id="81b1c-111">The supported types have not changed, however, they may change in the future.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="81b1c-112">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="81b1c-112">Version introduced</span></span>

<span data-ttu-id="81b1c-113">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="81b1c-113">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="81b1c-114">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="81b1c-114">Recommended action</span></span>

<span data-ttu-id="81b1c-115">Tür parametresi için desteklenmeyen bir tür kullanmayın <xref:System.Numerics.Vector%601> .</span><span class="sxs-lookup"><span data-stu-id="81b1c-115">Don't use an unsupported type for the type parameter of <xref:System.Numerics.Vector%601>.</span></span>

#### <a name="category"></a><span data-ttu-id="81b1c-116">Kategori</span><span class="sxs-lookup"><span data-stu-id="81b1c-116">Category</span></span>

<span data-ttu-id="81b1c-117">Core .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="81b1c-117">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="81b1c-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="81b1c-118">Affected APIs</span></span>

- <span data-ttu-id="81b1c-119"><xref:System.Numerics.Vector%601?displayProperty=fullName>ve tüm üyelerini</span><span class="sxs-lookup"><span data-stu-id="81b1c-119"><xref:System.Numerics.Vector%601?displayProperty=fullName> and all its members</span></span>

<!--

#### Affected APIs

- ``T:System.Numerics.Vector`1``

-->
