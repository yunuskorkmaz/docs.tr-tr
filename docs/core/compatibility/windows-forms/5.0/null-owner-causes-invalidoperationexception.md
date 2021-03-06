---
title: "Son değişiklik: DataGridView ile ilgili API 'Ler InvalidOperationException throw"
description: DataGridView ile ilgili bazı API 'Lerin bir özel durum oluşturması için nesnenin DataGridViewCellAccessibleObject. Owner değeri null ise, .NET 5 ' teki son değişiklik hakkında bilgi edinin.
ms.date: 09/18/2020
ms.openlocfilehash: e49ce0ebecb5a9ab4ed7f0e0d70d994ab751bc58
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256120"
---
# <a name="datagridview-related-apis-now-throw-invalidoperationexception"></a><span data-ttu-id="5f23a-103">DataGridView ile ilgili API 'Ler artık InvalidOperationException 'yi oluşturur</span><span class="sxs-lookup"><span data-stu-id="5f23a-103">DataGridView-related APIs now throw InvalidOperationException</span></span>

<span data-ttu-id="5f23a-104">Bundan sonra ilgili bazı API 'Ler, <xref:System.Windows.Forms.DataGridView> nesnenin değeri ise öğesini oluşturur <xref:System.InvalidOperationException> <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner?displayProperty=nameWithType> `null` .</span><span class="sxs-lookup"><span data-stu-id="5f23a-104">Some APIs related to <xref:System.Windows.Forms.DataGridView> now throw an <xref:System.InvalidOperationException> if the object's <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner?displayProperty=nameWithType> value is `null`.</span></span>

## <a name="change-description"></a><span data-ttu-id="5f23a-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="5f23a-105">Change description</span></span>

<span data-ttu-id="5f23a-106">Önceki .NET sürümlerinde, etkilenen API 'Ler çağrıldığında bir oluşturur <xref:System.NullReferenceException> ve <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> değeri şeklindedir `null` .</span><span class="sxs-lookup"><span data-stu-id="5f23a-106">In previous .NET versions, the affected APIs throw a <xref:System.NullReferenceException> when they are invoked and the <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> value is `null`.</span></span> <span data-ttu-id="5f23a-107">.NET 5 ' den başlayarak, bu API 'Ler <xref:System.InvalidOperationException> bir yerine bir, <xref:System.NullReferenceException> <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> değeri çağrıldığında bir oluşturur `null` .</span><span class="sxs-lookup"><span data-stu-id="5f23a-107">Starting in .NET 5, these APIs throw an <xref:System.InvalidOperationException> instead of a <xref:System.NullReferenceException> if the <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> value is `null` when they are invoked.</span></span>

<span data-ttu-id="5f23a-108"><xref:System.InvalidOperationException>.NET çalışma zamanının davranışına uygun bir şekilde oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="5f23a-108">Throwing an <xref:System.InvalidOperationException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="5f23a-109">Ayrıca geçersiz özelliği açıkça iletişim kurarak hata ayıklama deneyimini geliştirir.</span><span class="sxs-lookup"><span data-stu-id="5f23a-109">It also improves the debugging experience by clearly communicating the invalid property.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="5f23a-110">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="5f23a-110">Version introduced</span></span>

<span data-ttu-id="5f23a-111">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="5f23a-111">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="5f23a-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="5f23a-112">Recommended action</span></span>

<span data-ttu-id="5f23a-113">Kodunuzu inceleyin ve gerekirse, özelliği ile etkilenen türlerin oluşturulmasını engellemek için güncelleştirin <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> `null` .</span><span class="sxs-lookup"><span data-stu-id="5f23a-113">Review your code and, if necessary, update it to prevent constructing the affected types with the <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> property as `null`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="5f23a-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="5f23a-114">Affected APIs</span></span>

<span data-ttu-id="5f23a-115">Aşağıdaki tabloda etkilenen özellikler ve parametreler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="5f23a-115">The following table lists the affected properties and parameters:</span></span>

> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="5f23a-116">Etkilenen Yöntem veya özellik</span><span class="sxs-lookup"><span data-stu-id="5f23a-116">Affected method or property</span></span> | <span data-ttu-id="5f23a-117">Doğrulanan özellik</span><span class="sxs-lookup"><span data-stu-id="5f23a-117">Validated property</span></span> | <span data-ttu-id="5f23a-118">Sürüm eklendi</span><span class="sxs-lookup"><span data-stu-id="5f23a-118">Version added</span></span> |
> |-|-|-|
> | <xref:System.Windows.Forms.DataGridViewButtonCell.DataGridViewButtonCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="5f23a-119">5.0</span><span class="sxs-lookup"><span data-stu-id="5f23a-119">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.DefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="5f23a-120">5.0</span><span class="sxs-lookup"><span data-stu-id="5f23a-120">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.State?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="5f23a-121">5.0</span><span class="sxs-lookup"><span data-stu-id="5f23a-121">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="5f23a-122">5.0</span><span class="sxs-lookup"><span data-stu-id="5f23a-122">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Bounds?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="5f23a-123">5.0</span><span class="sxs-lookup"><span data-stu-id="5f23a-123">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.DefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="5f23a-124">5.0</span><span class="sxs-lookup"><span data-stu-id="5f23a-124">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Name?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="5f23a-125">5.0</span><span class="sxs-lookup"><span data-stu-id="5f23a-125">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Parent?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="5f23a-126">5.0</span><span class="sxs-lookup"><span data-stu-id="5f23a-126">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="5f23a-127">5.0</span><span class="sxs-lookup"><span data-stu-id="5f23a-127">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Navigate(System.Windows.Forms.AccessibleNavigation)?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="5f23a-128">5.0</span><span class="sxs-lookup"><span data-stu-id="5f23a-128">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewImageCell.DataGridViewImageCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="5f23a-129">5.0</span><span class="sxs-lookup"><span data-stu-id="5f23a-129">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="5f23a-130">5.0</span><span class="sxs-lookup"><span data-stu-id="5f23a-130">5.0</span></span> |

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
