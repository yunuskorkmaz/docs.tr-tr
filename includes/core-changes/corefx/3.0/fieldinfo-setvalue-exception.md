---
ms.openlocfilehash: 02c9305a36f47dfaf0b1fa8d19b07cd2d34badae
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721678"
---
### <a name="fieldinfosetvalue-throws-exception-for-static-init-only-fields"></a><span data-ttu-id="80891-101">FieldInfo. SetValue statik, yalnızca init alanları için özel durum oluşturur</span><span class="sxs-lookup"><span data-stu-id="80891-101">FieldInfo.SetValue throws exception for static, init-only fields</span></span>

<span data-ttu-id="80891-102">.NET Core 3,0 ' den başlayarak, çağırarak statik, alan üzerinde bir değer ayarlamaya çalıştığınızda bir özel durum oluşturulur <xref:System.Reflection.FieldAttributes.InitOnly> <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="80891-102">Starting in .NET Core 3.0, an exception is thrown when you attempt to set a value on a static, <xref:System.Reflection.FieldAttributes.InitOnly> field by calling <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="80891-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="80891-103">Change description</span></span>

<span data-ttu-id="80891-104">3,0 ' dan önceki .NET Core .NET Framework ve sürümlerinde, öğesini çağırarak, sabit bir statik alanın değerini, başlatıldıktan sonra ([C# dilinde ReadOnly](~/docs/csharp/language-reference/keywords/readonly.md)) ayarlayabilirsiniz <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="80891-104">In .NET Framework and versions of .NET Core prior to 3.0, you could set the value of a static field that's constant after it is initialized ([readonly in C#](~/docs/csharp/language-reference/keywords/readonly.md)) by calling <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>.</span></span> <span data-ttu-id="80891-105">Ancak böyle bir alanın bu şekilde ayarlanması, hedef çerçeveye ve iyileştirme ayarlarına bağlı olarak öngörülemeyen davranışlara neden oldu.</span><span class="sxs-lookup"><span data-stu-id="80891-105">However, setting such a field in this way resulted in unpredictable behavior based on the target framework and optimization settings.</span></span>

<span data-ttu-id="80891-106">.NET Core 3,0 ve sonraki sürümlerinde, <xref:System.Reflection.FieldInfo.SetValue%2A> bir statik, alanı çağırdığınızda bir <xref:System.Reflection.FieldAttributes.InitOnly> <xref:System.FieldAccessException?displayProperty=nameWithType> özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="80891-106">In .NET Core 3.0 and later versions, when you call <xref:System.Reflection.FieldInfo.SetValue%2A> on a static, <xref:System.Reflection.FieldAttributes.InitOnly> field, a <xref:System.FieldAccessException?displayProperty=nameWithType> exception is thrown.</span></span>

> [!TIP]
> <span data-ttu-id="80891-107">Bir <xref:System.Reflection.FieldAttributes.InitOnly> alan, yalnızca bildirildiği sırada veya kapsayan sınıf için oluşturucuda ayarlanabilir bir alandır.</span><span class="sxs-lookup"><span data-stu-id="80891-107">An <xref:System.Reflection.FieldAttributes.InitOnly> field is one that can only be set at the time it's declared or in the constructor for the containing class.</span></span> <span data-ttu-id="80891-108">Diğer bir deyişle, başlatıldıktan sonra sabittir.</span><span class="sxs-lookup"><span data-stu-id="80891-108">In other words, it's constant after it is initialized.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="80891-109">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="80891-109">Version introduced</span></span>

<span data-ttu-id="80891-110">3.0</span><span class="sxs-lookup"><span data-stu-id="80891-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="80891-111">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="80891-111">Recommended action</span></span>

<span data-ttu-id="80891-112"><xref:System.Reflection.FieldAttributes.InitOnly>Statik bir oluşturucuda statik, alanları başlatın.</span><span class="sxs-lookup"><span data-stu-id="80891-112">Initialize static, <xref:System.Reflection.FieldAttributes.InitOnly> fields in a static constructor.</span></span> <span data-ttu-id="80891-113">Bu hem dinamik hem de dinamik olmayan türler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="80891-113">This applies to both dynamic and non-dynamic types.</span></span>

<span data-ttu-id="80891-114">Alternatif olarak, <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> alanından özniteliğini kaldırabilir ve ardından öğesini çağırabilirsiniz <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="80891-114">Alternatively, you can remove the <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> attribute from the field, and then call <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="80891-115">Kategori</span><span class="sxs-lookup"><span data-stu-id="80891-115">Category</span></span>

<span data-ttu-id="80891-116">Core .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="80891-116">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="80891-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="80891-117">Affected APIs</span></span>

- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)?displayProperty=nameWithType>
- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)`
- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)`

-->
