---
title: 'Son değişiklik: TextFormatFlags. ModifyString artık kullanılmıyor'
description: .NET 5,0 'deki önemli değişiklik hakkında bilgi edinmek için TextFormatFlags. ModifyString alanının bir uyarı olarak artık kullanılmıyor olduğunu öğrenin.
ms.date: 11/05/2020
ms.openlocfilehash: 83dca65a770ccdcd5ce48bb669f5122dc2d5ad77
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761429"
---
# <a name="textformatflagsmodifystring-is-obsolete"></a><span data-ttu-id="97434-103">TextFormatFlags. ModifyString artık kullanılmıyor</span><span class="sxs-lookup"><span data-stu-id="97434-103">TextFormatFlags.ModifyString is obsolete</span></span>

<span data-ttu-id="97434-104">Bu <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> alan, bir uyarı olarak kullanımdan kalkmıştır ve gelecek bir .NET sürümünde kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="97434-104">The <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> field is obsolete, as a warning, and may be removed in a future .NET version.</span></span>

## <a name="change-description"></a><span data-ttu-id="97434-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="97434-105">Change description</span></span>

<span data-ttu-id="97434-106">Önceki .NET sürümlerinde, <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> Enumeration alanı kullanılmıyor olarak işaretlenmemiştir.</span><span class="sxs-lookup"><span data-stu-id="97434-106">In previous .NET versions, the <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> enumeration field is not marked obsolete.</span></span> <span data-ttu-id="97434-107">.NET 5,0 ve sonraki sürümlerinde, uyarı olarak artık kullanılmıyor olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="97434-107">In .NET 5.0 and later versions, it is marked obsolete as a warning.</span></span> <span data-ttu-id="97434-108">Bu alan, gelecekteki bir .NET sürümünde kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="97434-108">This field may be removed in a future .NET version.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="97434-109">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="97434-109">Reason for change</span></span>

<span data-ttu-id="97434-110">İle bir dize geçirilmesi <xref:System.Windows.Forms.TextRenderer.MeasureText%2A?displayProperty=nameWithType> <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> , bazı durumlarda dizeyi değiştirir.</span><span class="sxs-lookup"><span data-stu-id="97434-110">Passing a string to <xref:System.Windows.Forms.TextRenderer.MeasureText%2A?displayProperty=nameWithType> with <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> alters the string in some situations.</span></span> <span data-ttu-id="97434-111">Bu davranış, dize imlik kullanılabilirliği taahhüdünü keser ve önemli bir .NET çalışma zamanı durumu bozulması oluşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="97434-111">This behavior breaks the string immutability promise and may lead to a fatal .NET runtime state corruption.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="97434-112">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="97434-112">Version introduced</span></span>

<span data-ttu-id="97434-113">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="97434-113">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="97434-114">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="97434-114">Recommended action</span></span>

<span data-ttu-id="97434-115">' İ temel alan tüm kodları güncelleştirin <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="97434-115">Update any code that relies on <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType>.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="97434-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="97434-116">Affected APIs</span></span>

- <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=fullName>

<!--

### Affected APIs

- `F:System.Windows.Forms.TextFormatFlags.ModifyString`

### Category

Windows Forms

-->
