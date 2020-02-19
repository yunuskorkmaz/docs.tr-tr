---
ms.openlocfilehash: dc733ee32184db5af59bb06e294cd73765977581
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449575"
---
### <a name="fieldinfosetvalue-throws-exception-for-static-init-only-fields"></a><span data-ttu-id="310db-101">FieldInfo. SetValue statik, yalnızca init alanları için özel durum oluşturur</span><span class="sxs-lookup"><span data-stu-id="310db-101">FieldInfo.SetValue throws exception for static, init-only fields</span></span>

<span data-ttu-id="310db-102">.NET Core 3,0 ' den başlayarak, <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>çağırarak statik, <xref:System.Reflection.FieldAttributes.InitOnly> alanında bir değer ayarlamaya çalıştığınızda bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="310db-102">Starting in .NET Core 3.0, an exception is thrown when you attempt to set a value on a static, <xref:System.Reflection.FieldAttributes.InitOnly> field by calling <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="310db-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="310db-103">Change description</span></span>

<span data-ttu-id="310db-104">3,0 ' dan önceki .NET Core .NET Framework ve sürümlerinde, <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>çağırarak, başlatıldıktan sonra sabit bir statik alanın değerini ([salt okunur C# ](~/docs/csharp/language-reference/keywords/readonly.md)) ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="310db-104">In .NET Framework and versions of .NET Core prior to 3.0, you could set the value of a static field that's constant after it is initialized ([readonly in C#](~/docs/csharp/language-reference/keywords/readonly.md)) by calling <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>.</span></span> <span data-ttu-id="310db-105">Ancak böyle bir alanın bu şekilde ayarlanması, hedef çerçeveye ve iyileştirme ayarlarına bağlı olarak öngörülemeyen davranışlara neden oldu.</span><span class="sxs-lookup"><span data-stu-id="310db-105">However, setting such a field in this way resulted in unpredictable behavior based on the target framework and optimization settings.</span></span>

<span data-ttu-id="310db-106">.NET Core 3,0 ve sonraki sürümlerinde, statik, <xref:System.Reflection.FieldAttributes.InitOnly> alanında <xref:System.Reflection.FieldInfo.SetValue%2A> çağırdığınızda <xref:System.FieldAccessException?displayProperty=nameWithType> özel durumu oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="310db-106">In .NET Core 3.0 and later versions, when you call <xref:System.Reflection.FieldInfo.SetValue%2A> on a static, <xref:System.Reflection.FieldAttributes.InitOnly> field, a <xref:System.FieldAccessException?displayProperty=nameWithType> exception is thrown.</span></span>

> [!TIP]
> <span data-ttu-id="310db-107"><xref:System.Reflection.FieldAttributes.InitOnly> alan, yalnızca bildirildiği sırada veya kapsayan sınıf için oluşturucuda ayarlanabilir bir alandır.</span><span class="sxs-lookup"><span data-stu-id="310db-107">An <xref:System.Reflection.FieldAttributes.InitOnly> field is one that can only be set at the time it's declared or in the constructor for the containing class.</span></span> <span data-ttu-id="310db-108">Diğer bir deyişle, başlatıldıktan sonra sabittir.</span><span class="sxs-lookup"><span data-stu-id="310db-108">In other words, it's constant after it is initialized.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="310db-109">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="310db-109">Version introduced</span></span>

<span data-ttu-id="310db-110">3.0</span><span class="sxs-lookup"><span data-stu-id="310db-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="310db-111">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="310db-111">Recommended action</span></span>

<span data-ttu-id="310db-112">Statik bir oluşturucuda statik, <xref:System.Reflection.FieldAttributes.InitOnly> alanları başlatın.</span><span class="sxs-lookup"><span data-stu-id="310db-112">Initialize static, <xref:System.Reflection.FieldAttributes.InitOnly> fields in a static constructor.</span></span> <span data-ttu-id="310db-113">Bu hem dinamik hem de dinamik olmayan türler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="310db-113">This applies to both dynamic and non-dynamic types.</span></span>

<span data-ttu-id="310db-114">Alternatif olarak, <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> özniteliğini alandan kaldırabilir ve sonra <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType>çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="310db-114">Alternatively, you can remove the <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> attribute from the field, and then call <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="310db-115">Kategori</span><span class="sxs-lookup"><span data-stu-id="310db-115">Category</span></span>

<span data-ttu-id="310db-116">CoreFx</span><span class="sxs-lookup"><span data-stu-id="310db-116">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="310db-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="310db-117">Affected APIs</span></span>

- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)?displayProperty=nameWithType>
- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)`
- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)`

-->
