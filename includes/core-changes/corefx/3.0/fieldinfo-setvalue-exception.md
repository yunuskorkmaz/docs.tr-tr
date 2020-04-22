---
ms.openlocfilehash: 9f8a790718fbb9d685bb8959808338dc1766bf2c
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021552"
---
### <a name="fieldinfosetvalue-throws-exception-for-static-init-only-fields"></a><span data-ttu-id="a9387-101">FieldInfo.SetValue statik, yalnızca init-only alanları için özel durum atar</span><span class="sxs-lookup"><span data-stu-id="a9387-101">FieldInfo.SetValue throws exception for static, init-only fields</span></span>

<span data-ttu-id="a9387-102">.NET Core 3.0'dan başlayarak, statik bir <xref:System.Reflection.FieldAttributes.InitOnly> alana bir değer ayarlamaya <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>çalıştığınızda bir özel durum atılır.</span><span class="sxs-lookup"><span data-stu-id="a9387-102">Starting in .NET Core 3.0, an exception is thrown when you attempt to set a value on a static, <xref:System.Reflection.FieldAttributes.InitOnly> field by calling <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="a9387-103">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="a9387-103">Change description</span></span>

<span data-ttu-id="a9387-104">.NET Framework ve .NET Core sürümlerinde 3.0'dan önce,[(yalnızca C# olarak okunur)](~/docs/csharp/language-reference/keywords/readonly.md)olarak adlandırıldıktan <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>sonra sabit olan statik alanın değerini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a9387-104">In .NET Framework and versions of .NET Core prior to 3.0, you could set the value of a static field that's constant after it is initialized ([readonly in C#](~/docs/csharp/language-reference/keywords/readonly.md)) by calling <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>.</span></span> <span data-ttu-id="a9387-105">Ancak, böyle bir alanın bu şekilde ayarlanması, hedef çerçeve ve optimizasyon ayarlarına dayalı öngörülemeyen davranışlara yol açtı.</span><span class="sxs-lookup"><span data-stu-id="a9387-105">However, setting such a field in this way resulted in unpredictable behavior based on the target framework and optimization settings.</span></span>

<span data-ttu-id="a9387-106">.NET Core 3.0 ve sonraki sürümlerinde, statik, <xref:System.Reflection.FieldInfo.SetValue%2A> <xref:System.Reflection.FieldAttributes.InitOnly> alan <xref:System.FieldAccessException?displayProperty=nameWithType> üzerinde arama yaptığınızda, bir özel durum atılır.</span><span class="sxs-lookup"><span data-stu-id="a9387-106">In .NET Core 3.0 and later versions, when you call <xref:System.Reflection.FieldInfo.SetValue%2A> on a static, <xref:System.Reflection.FieldAttributes.InitOnly> field, a <xref:System.FieldAccessException?displayProperty=nameWithType> exception is thrown.</span></span>

> [!TIP]
> <span data-ttu-id="a9387-107">Alan, <xref:System.Reflection.FieldAttributes.InitOnly> yalnızca beyan edildiği anda veya içeren sınıfın oluşturucusunda ayarlanabilen alandır.</span><span class="sxs-lookup"><span data-stu-id="a9387-107">An <xref:System.Reflection.FieldAttributes.InitOnly> field is one that can only be set at the time it's declared or in the constructor for the containing class.</span></span> <span data-ttu-id="a9387-108">Başka bir deyişle, baş harfe basıldıktan sonra sabittir.</span><span class="sxs-lookup"><span data-stu-id="a9387-108">In other words, it's constant after it is initialized.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a9387-109">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="a9387-109">Version introduced</span></span>

<span data-ttu-id="a9387-110">3,0</span><span class="sxs-lookup"><span data-stu-id="a9387-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a9387-111">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="a9387-111">Recommended action</span></span>

<span data-ttu-id="a9387-112">Statik, <xref:System.Reflection.FieldAttributes.InitOnly> statik bir oluşturucu alanları başlatma.</span><span class="sxs-lookup"><span data-stu-id="a9387-112">Initialize static, <xref:System.Reflection.FieldAttributes.InitOnly> fields in a static constructor.</span></span> <span data-ttu-id="a9387-113">Bu, hem dinamik hem de dinamik olmayan türler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a9387-113">This applies to both dynamic and non-dynamic types.</span></span>

<span data-ttu-id="a9387-114">Alternatif olarak, özniteliği <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> alandan kaldırabilir ve <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType>sonra çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a9387-114">Alternatively, you can remove the <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> attribute from the field, and then call <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="a9387-115">Kategori</span><span class="sxs-lookup"><span data-stu-id="a9387-115">Category</span></span>

<span data-ttu-id="a9387-116">Çekirdek .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="a9387-116">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a9387-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="a9387-117">Affected APIs</span></span>

- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)?displayProperty=nameWithType>
- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)`
- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)`

-->
