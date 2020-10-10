---
title: PrepareHeaderDrag yöntemi (System. Windows. Controls. GridViewHeaderRowPresenter)
description: PrepareHeaderDrag adlı özel WPF yöntemi hakkında bilgi edinin.
ms.date: 09/25/2020
ms.technology: dotnet-wpf
topic_type:
- apiref
api_name:
- System.Windows.Controls.GridViewHeaderRowPresenter.PrepareHeaderDrag
api_location:
- PresentationFramework.dll
api_type:
- Assembly
ms.openlocfilehash: 6d806b8a50de3234cd04198f4ab86621dcd6ede1
ms.sourcegitcommit: eb7e87496f42361b1da98562dd75b516c9d58bbc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91877767"
---
# <a name="prepareheaderdrag-method"></a><span data-ttu-id="cd93d-103">PrepareHeaderDrag yöntemi</span><span class="sxs-lookup"><span data-stu-id="cd93d-103">PrepareHeaderDrag method</span></span>

<span data-ttu-id="cd93d-104">Belirtilen sütun başlığını yeniden sıralama için hazırlar.</span><span class="sxs-lookup"><span data-stu-id="cd93d-104">Prepares the specified column header for reordering.</span></span>

```csharp
private void PrepareHeaderDrag(GridViewColumnHeader header, Point pos, Point relativePos, bool cancelInvoke)
```

> [!WARNING]
> <span data-ttu-id="cd93d-105">Bu yöntem özeldir ve doğrudan kodunuzda kullanılmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="cd93d-105">This method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="cd93d-106">Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="cd93d-106">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="parameters"></a><span data-ttu-id="cd93d-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cd93d-107">Parameters</span></span>

<span data-ttu-id="cd93d-108">`header` <xref:System.Windows.Controls.GridViewColumnHeader></span><span class="sxs-lookup"><span data-stu-id="cd93d-108">`header` <xref:System.Windows.Controls.GridViewColumnHeader></span></span>\
<span data-ttu-id="cd93d-109">Yeniden sıralama için hazırlanmaya yönelik sütun üst bilgisi.</span><span class="sxs-lookup"><span data-stu-id="cd93d-109">The column header to prepare for reordering.</span></span>

<span data-ttu-id="cd93d-110">`pos` <xref:System.Windows.Point></span><span class="sxs-lookup"><span data-stu-id="cd93d-110">`pos` <xref:System.Windows.Point></span></span>\
<span data-ttu-id="cd93d-111">Sürükleme başladığı konuma göre konumu <xref:System.Windows.Controls.GridViewHeaderRowPresenter> .</span><span class="sxs-lookup"><span data-stu-id="cd93d-111">The position, relative to <xref:System.Windows.Controls.GridViewHeaderRowPresenter>, where the dragging starts.</span></span>

<span data-ttu-id="cd93d-112">`relativePos` <xref:System.Windows.Point></span><span class="sxs-lookup"><span data-stu-id="cd93d-112">`relativePos` <xref:System.Windows.Point></span></span>\
<span data-ttu-id="cd93d-113">Sürükleme başladığı konuma göre konumu `header` .</span><span class="sxs-lookup"><span data-stu-id="cd93d-113">The position, relative to `header`, where the dragging starts.</span></span>

<span data-ttu-id="cd93d-114">`cancelInvoke` <xref:System.Boolean></span><span class="sxs-lookup"><span data-stu-id="cd93d-114">`cancelInvoke` <xref:System.Boolean></span></span>\
<span data-ttu-id="cd93d-115">`true` yeniden sıralamayı iptal etmek için Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="cd93d-115">`true` to cancel the reordering; otherwise, `false`.</span></span>

## <a name="requirements"></a><span data-ttu-id="cd93d-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cd93d-116">Requirements</span></span>

<span data-ttu-id="cd93d-117">**Ad alanı:**<xref:System.Windows.Controls></span><span class="sxs-lookup"><span data-stu-id="cd93d-117">**Namespace:** <xref:System.Windows.Controls></span></span>

<span data-ttu-id="cd93d-118">**Bütünleştirilmiş kod:** PresentationFramework.dll</span><span class="sxs-lookup"><span data-stu-id="cd93d-118">**Assembly:** PresentationFramework.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="cd93d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd93d-119">See also</span></span>

- <xref:System.Windows.Controls.GridViewHeaderRowPresenter>
