---
ms.openlocfilehash: abb89099c4c8a5d9c0e55ef8f357faf44e75b045
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774238"
---
### <a name="wpf-spell-checking-in-text-enabled-controls-will-not-work-in-windows-10-for-languages-not-in-the-oss-input-language-list"></a>WPF yazım metin özellikli denetimlerinde işletim sisteminin giriş dili listede olmayan dilleri için Windows 10'da çalışmaz

|   |   |
|---|---|
|Ayrıntılar|Windows 10'da çalıştırırken, Platform yazım denetimi özelliklerini yalnızca diller listesinde mevcut diller için kullanılabilir olmadığından yazım denetleyicisi metin özellikli WPF denetimleri için çalışmayabilir. Windows 10'daki bir dil kullanılabilir klavyeler listesine eklendiğinde Windows otomatik olarak indirir ve karşılık gelen bir özellik, yazım denetimi özellikleri sağlayan isteğe bağlı (FOD) paketi yükler. Dil diller listesine ekleyerek, yazım denetleyicisi desteklenecektir.|
|Öneri|Windows 10'da çalışmak için yazım denetimi için bir giriş dili olarak dili veya yazım iade edilecek metin eklenmelidir dikkat edin.|
|Kapsam|Kenar|
|Sürüm|4.6|
|Tür|Çalışma zamanı|
