---
ms.openlocfilehash: 97ca78e154eb25e863256e06caa119fe753bc344
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858653"
---
### <a name="wpf-spell-checking-in-text-enabled-controls-will-not-work-in-windows-10-for-languages-not-in-the-oss-input-language-list"></a>WPF yazım metin özellikli denetimlerinde işletim sisteminin giriş dili listede olmayan dilleri için Windows 10'da çalışmaz

|   |   |
|---|---|
|Ayrıntılar|Windows 10'da çalıştırırken, Platform yazım denetimi özelliklerini yalnızca diller listesinde mevcut diller için kullanılabilir olmadığından yazım denetleyicisi metin özellikli WPF denetimleri için çalışmayabilir. Windows 10'daki bir dil kullanılabilir klavyeler listesine eklendiğinde Windows otomatik olarak indirir ve karşılık gelen bir özellik, yazım denetimi özellikleri sağlayan isteğe bağlı (FOD) paketi yükler. Dil diller listesine ekleyerek, yazım denetleyicisi desteklenecektir.|
|Öneri|Windows 10'da çalışmak için yazım denetimi için bir giriş dili olarak dili veya yazım iade edilecek metin eklenmelidir dikkat edin.|
|`Scope`|Kenar|
|Version|4.6|
|Type|Çalışma zamanı|

