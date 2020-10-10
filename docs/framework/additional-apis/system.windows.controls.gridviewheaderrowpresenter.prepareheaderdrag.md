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
# <a name="prepareheaderdrag-method"></a>PrepareHeaderDrag yöntemi

Belirtilen sütun başlığını yeniden sıralama için hazırlar.

```csharp
private void PrepareHeaderDrag(GridViewColumnHeader header, Point pos, Point relativePos, bool cancelInvoke)
```

> [!WARNING]
> Bu yöntem özeldir ve doğrudan kodunuzda kullanılmak üzere tasarlanmamıştır.
>
> Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.

## <a name="parameters"></a>Parametreler

`header` <xref:System.Windows.Controls.GridViewColumnHeader>\
Yeniden sıralama için hazırlanmaya yönelik sütun üst bilgisi.

`pos` <xref:System.Windows.Point>\
Sürükleme başladığı konuma göre konumu <xref:System.Windows.Controls.GridViewHeaderRowPresenter> .

`relativePos` <xref:System.Windows.Point>\
Sürükleme başladığı konuma göre konumu `header` .

`cancelInvoke` <xref:System.Boolean>\
`true` yeniden sıralamayı iptal etmek için Aksi takdirde, `false` .

## <a name="requirements"></a>Gereksinimler

**Ad alanı:**<xref:System.Windows.Controls>

**Bütünleştirilmiş kod:** PresentationFramework.dll

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.GridViewHeaderRowPresenter>
