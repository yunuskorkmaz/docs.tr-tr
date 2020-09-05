---
ms.openlocfilehash: d4e60f2a59980263916718ebcc71cc359952c031
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496821"
---
### <a name="wpf-spell-checking-fails-in-unexpected-ways"></a>WPF yazım denetimi beklenmeyen yollarla başarısız oluyor

#### <a name="details"></a>Ayrıntılar

Buna bir dizi WPF yazım denetleyicisi sorunu dahildir:<ul><li>WPF yazım denetleyicisi bazen <xref:System.Runtime.InteropServices.COMException?displayProperty=fullName></li><li>WPF yazım denetleyicisi <xref:System.UnauthorizedAccessException> , ' farklı kullanıcı olarak Çalıştır ' kullanılarak uygulama başlatıldığında başarısız oluyor</li><li>WPF yazım denetleyicisi, Almanya 'daki ' Hausnummer ' gibi bileşik sözcüklerdeki yazım hatalarını yanlış bir şekilde tanımlıyor.</li></ul>

#### <a name="suggestion"></a>Öneri

Sorun #1-Bu, .NET Framework 4.6.2 sorunu #2 düzeltildi-WPF yazım denetleyicisi, ' farklı kullanıcı olarak Çalıştır ' kullanılarak başlatıldığında artık desteklenmez. .NET Framework 4.6.2 başlatılıyor, bu şekilde başlatılan uygulamalar artık beklenmedik şekilde kilitlenmeyecektir. bunun yerine yazım denetleyicisi sessizce devre dışı bırakılır. Sorun #3-Bu, .NET Framework 4.6.2 içinde düzeltildi.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4.6.1|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
