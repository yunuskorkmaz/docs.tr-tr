---
title: ".NET 6 Son değişiklik: DataGridView ile ilgili API 'Ler InvalidOperationException"
description: DataGridView ile ilgili bazı API 'Lerin bir özel durum oluşturması için nesnenin DataGridViewCellAccessibleObject. Owner değeri null ise, .NET 6 ' daki önemli değişiklik hakkında bilgi edinin.
ms.date: 03/29/2021
ms.openlocfilehash: 3726296bb93c88d438e45ea832bf9070ace69dd0
ms.sourcegitcommit: 109507b6c16704ed041efe9598c70cd3438a9fbc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106080682"
---
# <a name="datagridview-related-apis-now-throw-invalidoperationexception"></a><span data-ttu-id="55892-103">DataGridView ile ilgili API 'Ler artık InvalidOperationException 'yi oluşturur</span><span class="sxs-lookup"><span data-stu-id="55892-103">DataGridView-related APIs now throw InvalidOperationException</span></span>

<span data-ttu-id="55892-104">Bundan sonra ilgili bazı API 'Ler, <xref:System.Windows.Forms.DataGridView> nesnenin değeri ise öğesini oluşturur <xref:System.InvalidOperationException> <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner?displayProperty=nameWithType> `null` .</span><span class="sxs-lookup"><span data-stu-id="55892-104">Some APIs related to <xref:System.Windows.Forms.DataGridView> now throw an <xref:System.InvalidOperationException> if the object's <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner?displayProperty=nameWithType> value is `null`.</span></span>

## <a name="change-description"></a><span data-ttu-id="55892-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="55892-105">Change description</span></span>

<span data-ttu-id="55892-106">Önceki .NET sürümlerinde, etkilenen API 'Ler çağrıldığında bir oluşturur <xref:System.NullReferenceException> ve <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> özellik değeri şeklindedir `null` .</span><span class="sxs-lookup"><span data-stu-id="55892-106">In previous .NET versions, the affected APIs throw a <xref:System.NullReferenceException> when they are invoked and the <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> property value is `null`.</span></span> <span data-ttu-id="55892-107">.NET 6 ' dan itibaren, <xref:System.InvalidOperationException> <xref:System.NullReferenceException> <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> özellik değeri çağrıldığında, bu API 'ler yerine bir oluşturur `null` .</span><span class="sxs-lookup"><span data-stu-id="55892-107">Starting in .NET 6, these APIs throw an <xref:System.InvalidOperationException> instead of a <xref:System.NullReferenceException> if the <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> property value is `null` when they're invoked.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="55892-108">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="55892-108">Reason for change</span></span>

<span data-ttu-id="55892-109"><xref:System.InvalidOperationException>.NET çalışma zamanının davranışına uygun bir şekilde oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="55892-109">Throwing an <xref:System.InvalidOperationException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="55892-110">Ayrıca geçersiz özelliği açıkça iletişim kurarak hata ayıklama deneyimini geliştirir.</span><span class="sxs-lookup"><span data-stu-id="55892-110">It also improves the debugging experience by clearly communicating the invalid property.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="55892-111">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="55892-111">Version introduced</span></span>

<span data-ttu-id="55892-112">.NET 6.0</span><span class="sxs-lookup"><span data-stu-id="55892-112">.NET 6.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="55892-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="55892-113">Recommended action</span></span>

<span data-ttu-id="55892-114">Kodunuzu inceleyin ve gerekirse, özelliği ile etkilenen türlerin oluşturulmasını engellemek için güncelleştirin <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> `null` .</span><span class="sxs-lookup"><span data-stu-id="55892-114">Review your code and, if necessary, update it to prevent constructing the affected types with the <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> property as `null`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="55892-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="55892-115">Affected APIs</span></span>

<span data-ttu-id="55892-116">Aşağıdaki tabloda etkilenen özellikler ve Yöntemler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="55892-116">The following table lists the affected properties and methods:</span></span>

> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="55892-117">Etkilenen Yöntem veya özellik</span><span class="sxs-lookup"><span data-stu-id="55892-117">Affected method or property</span></span> | <span data-ttu-id="55892-118">Sürüm eklendi</span><span class="sxs-lookup"><span data-stu-id="55892-118">Version added</span></span> |
> |-|-|
> | <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.Bounds?displayProperty=fullName> | <span data-ttu-id="55892-119">Preview 4</span><span class="sxs-lookup"><span data-stu-id="55892-119">Preview 4</span></span> |
> | <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.DefaultAction?displayProperty=fullName> | <span data-ttu-id="55892-120">Preview 4</span><span class="sxs-lookup"><span data-stu-id="55892-120">Preview 4</span></span> |
> | <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.Name?displayProperty=fullName> | <span data-ttu-id="55892-121">Preview 4</span><span class="sxs-lookup"><span data-stu-id="55892-121">Preview 4</span></span> |
>| <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.Navigate(System.Windows.Forms.AccessibleNavigation)?displayProperty=fullName> | <span data-ttu-id="55892-122">Preview 4</span><span class="sxs-lookup"><span data-stu-id="55892-122">Preview 4</span></span> |
> | <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.State?displayProperty=fullName> | <span data-ttu-id="55892-123">Preview 4</span><span class="sxs-lookup"><span data-stu-id="55892-123">Preview 4</span></span> |

## <a name="see-also"></a><span data-ttu-id="55892-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55892-124">See also</span></span>

- [<span data-ttu-id="55892-125">DataGridView ile ilgili API 'Ler throw (.NET 5)</span><span class="sxs-lookup"><span data-stu-id="55892-125">DataGridView-related APIs throw InvalidOperationException (.NET 5)</span></span>](../5.0/null-owner-causes-invalidoperationexception.md)

<!--

### Affected APIs

- `P:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.Bounds`
- `P:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.DefaultAction`
- `P:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.Name`
- `M:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.Navigate(System.Windows.Forms.AccessibleNavigation)`
- `P:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.State`

### Category

Windows Forms

-->
