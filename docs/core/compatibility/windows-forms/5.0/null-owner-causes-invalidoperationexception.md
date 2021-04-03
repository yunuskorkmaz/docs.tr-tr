---
title: ".NET 5 Son değişiklik: DataGridView ile ilgili API 'Ler InvalidOperationException"
description: DataGridView ile ilgili bazı API 'Lerin bir özel durum oluşturması için nesnenin DataGridViewCellAccessibleObject. Owner değeri null ise, .NET 5 ' teki son değişiklik hakkında bilgi edinin.
ms.date: 09/18/2020
ms.openlocfilehash: 57ff50d7bdc83286d4d452746e8f64bace187edb
ms.sourcegitcommit: 109507b6c16704ed041efe9598c70cd3438a9fbc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106079602"
---
# <a name="datagridview-related-apis-throw-invalidoperationexception"></a><span data-ttu-id="63a43-103">DataGridView ile ilgili API 'Ler InvalidOperationException throw</span><span class="sxs-lookup"><span data-stu-id="63a43-103">DataGridView-related APIs throw InvalidOperationException</span></span>

<span data-ttu-id="63a43-104">Bundan sonra ilgili bazı API 'Ler, <xref:System.Windows.Forms.DataGridView> nesnenin değeri ise öğesini oluşturur <xref:System.InvalidOperationException> <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner?displayProperty=nameWithType> `null` .</span><span class="sxs-lookup"><span data-stu-id="63a43-104">Some APIs related to <xref:System.Windows.Forms.DataGridView> now throw an <xref:System.InvalidOperationException> if the object's <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner?displayProperty=nameWithType> value is `null`.</span></span>

## <a name="change-description"></a><span data-ttu-id="63a43-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="63a43-105">Change description</span></span>

<span data-ttu-id="63a43-106">Önceki .NET sürümlerinde, etkilenen API 'Ler çağrıldığında bir oluşturur <xref:System.NullReferenceException> ve <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> özellik değeri şeklindedir `null` .</span><span class="sxs-lookup"><span data-stu-id="63a43-106">In previous .NET versions, the affected APIs throw a <xref:System.NullReferenceException> when they are invoked and the <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> property value is `null`.</span></span> <span data-ttu-id="63a43-107">.NET 5 ' den itibaren, <xref:System.InvalidOperationException> <xref:System.NullReferenceException> <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> özellik değeri çağrıldığında, bu API 'ler yerine bir oluşturur `null` .</span><span class="sxs-lookup"><span data-stu-id="63a43-107">Starting in .NET 5, these APIs throw an <xref:System.InvalidOperationException> instead of a <xref:System.NullReferenceException> if the <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> property value is `null` when they're invoked.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="63a43-108">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="63a43-108">Reason for change</span></span>

<span data-ttu-id="63a43-109"><xref:System.InvalidOperationException>.NET çalışma zamanının davranışına uygun bir şekilde oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="63a43-109">Throwing an <xref:System.InvalidOperationException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="63a43-110">Ayrıca geçersiz özelliği açıkça iletişim kurarak hata ayıklama deneyimini geliştirir.</span><span class="sxs-lookup"><span data-stu-id="63a43-110">It also improves the debugging experience by clearly communicating the invalid property.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="63a43-111">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="63a43-111">Version introduced</span></span>

<span data-ttu-id="63a43-112">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="63a43-112">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="63a43-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="63a43-113">Recommended action</span></span>

<span data-ttu-id="63a43-114">Kodunuzu inceleyin ve gerekirse, özelliği ile etkilenen türlerin oluşturulmasını engellemek için güncelleştirin <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> `null` .</span><span class="sxs-lookup"><span data-stu-id="63a43-114">Review your code and, if necessary, update it to prevent constructing the affected types with the <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> property as `null`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="63a43-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="63a43-115">Affected APIs</span></span>

<span data-ttu-id="63a43-116">Aşağıdaki tabloda etkilenen API 'Ler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="63a43-116">The following table lists the affected APIs:</span></span>

> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="63a43-117">Etkilenen Yöntem veya özellik</span><span class="sxs-lookup"><span data-stu-id="63a43-117">Affected method or property</span></span> | <span data-ttu-id="63a43-118">Doğrulanan özellik</span><span class="sxs-lookup"><span data-stu-id="63a43-118">Validated property</span></span> | <span data-ttu-id="63a43-119">Sürüm eklendi</span><span class="sxs-lookup"><span data-stu-id="63a43-119">Version added</span></span> |
> |-|-|-|
> | <xref:System.Windows.Forms.DataGridViewButtonCell.DataGridViewButtonCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="63a43-120">5.0</span><span class="sxs-lookup"><span data-stu-id="63a43-120">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.DefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="63a43-121">5.0</span><span class="sxs-lookup"><span data-stu-id="63a43-121">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.State?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="63a43-122">5.0</span><span class="sxs-lookup"><span data-stu-id="63a43-122">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="63a43-123">5.0</span><span class="sxs-lookup"><span data-stu-id="63a43-123">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Bounds?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="63a43-124">5.0</span><span class="sxs-lookup"><span data-stu-id="63a43-124">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.DefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="63a43-125">5.0</span><span class="sxs-lookup"><span data-stu-id="63a43-125">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Name?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="63a43-126">5.0</span><span class="sxs-lookup"><span data-stu-id="63a43-126">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Parent?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="63a43-127">5.0</span><span class="sxs-lookup"><span data-stu-id="63a43-127">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="63a43-128">5.0</span><span class="sxs-lookup"><span data-stu-id="63a43-128">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Navigate(System.Windows.Forms.AccessibleNavigation)?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="63a43-129">5.0</span><span class="sxs-lookup"><span data-stu-id="63a43-129">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewImageCell.DataGridViewImageCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="63a43-130">5.0</span><span class="sxs-lookup"><span data-stu-id="63a43-130">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="63a43-131">5.0</span><span class="sxs-lookup"><span data-stu-id="63a43-131">5.0</span></span> |

## <a name="see-also"></a><span data-ttu-id="63a43-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="63a43-132">See also</span></span>

- [<span data-ttu-id="63a43-133">DataGridView ile ilgili API 'Ler InvalidOperationException throw (.NET 6)</span><span class="sxs-lookup"><span data-stu-id="63a43-133">DataGridView-related APIs throw InvalidOperationException (.NET 6)</span></span>](../6.0/null-owner-causes-invalidoperationexception.md)

<!--

### Affected APIs

- `M:System.Windows.Forms.DataGridViewButtonCell.DataGridViewButtonCellAccessibleObject.DoDefaultAction`
- `P:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.DefaultAction`
- `P:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.State`
- `M:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.DoDefaultAction`
- `P:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Bounds`
- `P:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.DefaultAction`
- `P:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Name`
- `P:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Parent`
- `M:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.DoDefaultAction`
- `M:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Navigate(System.Windows.Forms.AccessibleNavigation)`
- `M:System.Windows.Forms.DataGridViewImageCell.DataGridViewImageCellAccessibleObject.DoDefaultAction`
- `M:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject.DoDefaultAction`

### Category

Windows Forms

-->
