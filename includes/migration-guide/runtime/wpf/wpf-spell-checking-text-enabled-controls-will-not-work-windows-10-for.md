---
ms.openlocfilehash: abb89099c4c8a5d9c0e55ef8f357faf44e75b045
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858653"
---
### <a name="wpf-spell-checking-in-text-enabled-controls-will-not-work-in-windows-10-for-languages-not-in-the-oss-input-language-list"></a>Metin etkin denetimlerde WPF yazım denetimi, işletim sistemi giriş dil listesinde olmayan diller için Windows 10'da çalışmaz

|   |   |
|---|---|
|Ayrıntılar|Windows 10'da çalışırken, platform yazım denetimi yetenekleri yalnızca giriş dilleri listesinde bulunan diller için kullanılabilir olduğundan yazım denetleyicisi WPF metin etkin denetimleri için çalışmayabilir. Windows 10'da, kullanılabilir klavyeler listesine bir dil eklendiğinde, Windows yazım denetimi özellikleri sağlayan ilgili Bir İsteğe Bağlı Özellik (FOD) paketini otomatik olarak karşıdan yükler ve yükler. Giriş dilleri listesine dil eklenerek yazım denetleyicisi desteklenir.|
|Öneri|Yazım denetimi yapılacak dil veya metnin Windows 10'da çalışmak için yazım denetimi için giriş dili olarak eklenmesi gerektiğini unutmayın.|
|Kapsam|Edge|
|Sürüm|4.6|
|Tür|Çalışma Zamanı|
