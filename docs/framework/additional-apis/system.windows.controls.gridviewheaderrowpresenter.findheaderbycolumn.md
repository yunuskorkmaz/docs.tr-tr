---
title: FindHeaderByColumn yöntemi (System. Windows. Controls. GridViewHeaderRowPresenter)
description: FindHeaderByColumn adlı özel WPF yöntemi hakkında bilgi edinin.
ms.date: 09/25/2020
ms.technology: dotnet-wpf
topic_type:
- apiref
api_name:
- System.Windows.Controls.GridViewHeaderRowPresenter.FindHeaderByColumn
api_location:
- PresentationFramework.dll
api_type:
- Assembly
ms.openlocfilehash: 88ed2928f86602d1078488354de6d5267c0311f5
ms.sourcegitcommit: eb7e87496f42361b1da98562dd75b516c9d58bbc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91877772"
---
# <a name="findheaderbycolumn-method"></a><span data-ttu-id="7f46c-103">FindHeaderByColumn yöntemi</span><span class="sxs-lookup"><span data-stu-id="7f46c-103">FindHeaderByColumn method</span></span>

<span data-ttu-id="7f46c-104">Görsel ağaçta belirtilen sütun için sütun üst bilgisini bulur.</span><span class="sxs-lookup"><span data-stu-id="7f46c-104">Finds the column header for the specified column in the visual tree.</span></span>

```csharp
private GridViewColumnHeader FindHeaderByColumn(GridViewColumn column)
```

> [!WARNING]
> <span data-ttu-id="7f46c-105">Bu yöntem özeldir ve doğrudan kodunuzda kullanılmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="7f46c-105">This method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="7f46c-106">Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="7f46c-106">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="parameters"></a><span data-ttu-id="7f46c-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7f46c-107">Parameters</span></span>

<span data-ttu-id="7f46c-108">`column` <xref:System.Windows.Controls.GridViewColumn></span><span class="sxs-lookup"><span data-stu-id="7f46c-108">`column` <xref:System.Windows.Controls.GridViewColumn></span></span>\
<span data-ttu-id="7f46c-109">Üst bilgisi bulunan ve döndürülecek olan sütun.</span><span class="sxs-lookup"><span data-stu-id="7f46c-109">The column whose header should be found and returned.</span></span>

## <a name="return-value"></a><span data-ttu-id="7f46c-110">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="7f46c-110">Return value</span></span>

<xref:System.Windows.Controls.GridViewColumnHeader>\
<span data-ttu-id="7f46c-111">Belirtilen sütunun üst bilgisi veya `null` belirtilen sütun mevcut değilse.</span><span class="sxs-lookup"><span data-stu-id="7f46c-111">The header of the specified column, or `null` if the specified column doesn't exist.</span></span>

## <a name="requirements"></a><span data-ttu-id="7f46c-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7f46c-112">Requirements</span></span>

<span data-ttu-id="7f46c-113">**Ad alanı:**<xref:System.Windows.Controls></span><span class="sxs-lookup"><span data-stu-id="7f46c-113">**Namespace:** <xref:System.Windows.Controls></span></span>

<span data-ttu-id="7f46c-114">**Bütünleştirilmiş kod:** PresentationFramework.dll</span><span class="sxs-lookup"><span data-stu-id="7f46c-114">**Assembly:** PresentationFramework.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="7f46c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f46c-115">See also</span></span>

- <xref:System.Windows.Controls.GridViewHeaderRowPresenter>
