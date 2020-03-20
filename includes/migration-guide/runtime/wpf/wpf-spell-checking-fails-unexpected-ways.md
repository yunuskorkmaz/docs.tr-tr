---
ms.openlocfilehash: 09e3f0e168e0dcbe79d8ee7216f2671c67bfb87e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802957"
---
### <a name="wpf-spell-checking-fails-in-unexpected-ways"></a>WPF Yazım Denetimi beklenmeyen şekillerde başarısız olur

|   |   |
|---|---|
|Ayrıntılar|Buna bir dizi WPF Yazım Denetleyicisi sorunları dahildir:<ul><li>WPF Yazım Denetleyicisi bazen atar<xref:System.Runtime.InteropServices.COMException?displayProperty=name></li><li>WPF Yazım Denetleyicisi, uygulamaların 'farklı kullanıcı olarak çalıştır' kullanılarak başlatıldığında başarısız olur <xref:System.UnauthorizedAccessException></li><li>WPF Yazım Denetleyicisi, Almanca'da 'Hausnummer' gibi bileşik sözcüklerdeki yazım hatalarını yanlış tanımlar.</li></ul>|
|Öneri|Sorun #1 - Bu ,NET Framework 4.6.2 Issue #2'da düzeltildi - Uygulamalar 'farklı kullanıcı olarak çalıştır' kullanılarak başlatıldığında WPF Yazım Denetleyicisi artık desteklenmez. .NET Framework 4.6.2'den başlayarak, bu şekilde başlatılan uygulamalar artık beklenmedik bir şekilde çökmez - bunun yerine Yazım Denetleyicisi sessizce devre dışı bırakılır. Sorun #3 - Bu durum .NET Framework 4.6.2'de sabitlenmiştir.|
|Kapsam|Edge|
|Sürüm|4.6.1|
|Tür|Çalışma Zamanı|
