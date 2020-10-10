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
# <a name="findheaderbycolumn-method"></a>FindHeaderByColumn yöntemi

Görsel ağaçta belirtilen sütun için sütun üst bilgisini bulur.

```csharp
private GridViewColumnHeader FindHeaderByColumn(GridViewColumn column)
```

> [!WARNING]
> Bu yöntem özeldir ve doğrudan kodunuzda kullanılmak üzere tasarlanmamıştır.
>
> Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.

## <a name="parameters"></a>Parametreler

`column` <xref:System.Windows.Controls.GridViewColumn>\
Üst bilgisi bulunan ve döndürülecek olan sütun.

## <a name="return-value"></a>Döndürülen değer

<xref:System.Windows.Controls.GridViewColumnHeader>\
Belirtilen sütunun üst bilgisi veya `null` belirtilen sütun mevcut değilse.

## <a name="requirements"></a>Gereksinimler

**Ad alanı:**<xref:System.Windows.Controls>

**Bütünleştirilmiş kod:** PresentationFramework.dll

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.GridViewHeaderRowPresenter>
