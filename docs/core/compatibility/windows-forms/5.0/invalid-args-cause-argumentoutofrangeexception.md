---
title: 'Son değişiklik: WinForms özellikleri artık ArgumentOutOfRangeException oluşturur'
description: Bazı Windows Forms özelliklerinin artık geçersiz bağımsız değişkenler için bir ArgumentOutOfRangeException oluşturması durumunda .NET 5,0 ' deki önemli değişiklik hakkında bilgi edinin.
ms.date: 06/18/2020
ms.openlocfilehash: 94593047d16304ce401b23993ad4ca173c10812b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761586"
---
# <a name="winforms-properties-now-throw-argumentoutofrangeexception"></a><span data-ttu-id="f0e03-103">WinForms özellikleri artık ArgumentOutOfRangeException oluşturur</span><span class="sxs-lookup"><span data-stu-id="f0e03-103">WinForms properties now throw ArgumentOutOfRangeException</span></span>

<span data-ttu-id="f0e03-104">Bazı Windows Forms özellikleri artık <xref:System.ArgumentOutOfRangeException> , daha önce olmadıkları durumlarda geçersiz bağımsız değişkenler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f0e03-104">Some Windows Forms properties now throw an <xref:System.ArgumentOutOfRangeException> for invalid arguments, where previously they did not.</span></span>

## <a name="change-description"></a><span data-ttu-id="f0e03-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="f0e03-105">Change description</span></span>

<span data-ttu-id="f0e03-106">Daha önce, bu özellikler <xref:System.NullReferenceException> <xref:System.IndexOutOfRangeException> <xref:System.ArgumentException> Aralık dışı bağımsız değişkenler geçirildiğinde, veya gibi çeşitli özel durumlar oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="f0e03-106">Previously, these properties threw various exceptions, such as <xref:System.NullReferenceException>, <xref:System.IndexOutOfRangeException>, or <xref:System.ArgumentException>, when passed out-of-range arguments.</span></span> <span data-ttu-id="f0e03-107">.NET 5,0 ' den itibaren, bu özellikler artık <xref:System.ArgumentOutOfRangeException> Aralık dışı olan bağımsız değişkenleri geçtiğinde bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f0e03-107">Starting in .NET 5.0, these properties now throw an <xref:System.ArgumentOutOfRangeException> when passed arguments that are out of range.</span></span>

<span data-ttu-id="f0e03-108"><xref:System.ArgumentOutOfRangeException>.NET çalışma zamanının davranışına uygun bir şekilde oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="f0e03-108">Throwing an <xref:System.ArgumentOutOfRangeException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="f0e03-109">Ayrıca, hangi bağımsız değişkenin geçersiz olduğu açıkça iletişim kurarak hata ayıklama deneyimini geliştirir.</span><span class="sxs-lookup"><span data-stu-id="f0e03-109">It also improves the debugging experience by clearly communicating which argument is invalid.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="f0e03-110">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="f0e03-110">Version introduced</span></span>

<span data-ttu-id="f0e03-111">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="f0e03-111">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="f0e03-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="f0e03-112">Recommended action</span></span>

- <span data-ttu-id="f0e03-113">Geçersiz bağımsız değişkenlerin geçirilmesini engellemek için kodu güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="f0e03-113">Update the code to prevent passing invalid arguments.</span></span>
- <span data-ttu-id="f0e03-114">Gerekirse, <xref:System.ArgumentOutOfRangeException> özelliği ayarlarken bir işleyin.</span><span class="sxs-lookup"><span data-stu-id="f0e03-114">If necessary, handle an <xref:System.ArgumentOutOfRangeException> when setting the property.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="f0e03-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="f0e03-115">Affected APIs</span></span>

<span data-ttu-id="f0e03-116">Aşağıdaki tabloda etkilenen özellikler ve parametreler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="f0e03-116">The following table lists the affected properties and parameters:</span></span>

> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="f0e03-117">Özellik</span><span class="sxs-lookup"><span data-stu-id="f0e03-117">Property</span></span> | <span data-ttu-id="f0e03-118">Parametre adı</span><span class="sxs-lookup"><span data-stu-id="f0e03-118">Parameter name</span></span> | <span data-ttu-id="f0e03-119">Sürüm eklendi</span><span class="sxs-lookup"><span data-stu-id="f0e03-119">Version added</span></span> |
> |-|-|-|
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.Item(System.Int32)?displayProperty=nameWithType> | `index` | <span data-ttu-id="f0e03-120">5,0 Preview 5</span><span class="sxs-lookup"><span data-stu-id="f0e03-120">5.0 Preview 5</span></span> |
> | <xref:System.Windows.Forms.TreeNode.ImageIndex?displayProperty=nameWithType> | `value` | <span data-ttu-id="f0e03-121">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="f0e03-121">5.0 Preview 6</span></span> |
> | <xref:System.Windows.Forms.TreeNode.SelectedImageIndex?displayProperty=nameWithType> | `value` | <span data-ttu-id="f0e03-122">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="f0e03-122">5.0 Preview 6</span></span> |

<!--

### Affected APIs

- `P:System.Windows.Forms.ListBox.IntegerCollection.Item(System.Int32)`
- `P:System.Windows.Forms.TreeNode.ImageIndex`
- `P:System.Windows.Forms.TreeNode.SelectedImageIndex`

### Category

Windows Forms

-->
