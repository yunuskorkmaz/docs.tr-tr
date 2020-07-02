---
ms.openlocfilehash: 1d2e4a058008676c6ea85becebd4bb9220569ef3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621448"
---
### <a name="wpf-spell-checking-in-text-enabled-controls-will-not-work-in-windows-10-for-languages-not-in-the-oss-input-language-list"></a>Metin özellikli denetimlerde WPF yazım denetimi, işletim sisteminin giriş dili listesinde olmayan diller için Windows 10 ' da çalışmaz

#### <a name="details"></a>Ayrıntılar

Windows 10 ' da çalışırken, platform yazım denetimi özellikleri yalnızca giriş dilleri listesinde bulunan diller için kullanılabilir olduğundan, yazım denetleyicisi WPF metin özellikli denetimler için çalışmayabilir. Windows 10 ' da, kullanılabilir klavyeler listesine bir dil eklendiğinde, Windows otomatik olarak yazım denetimi özellikleri sağlayan ilgili bir Isteğe bağlı Özellik (FOD) paketini indirir ve yükler. Dili giriş dilleri listesine ekleyerek, yazım denetleyicisi desteklenecektir.

#### <a name="suggestion"></a>Öneri

Yazım denetimi yapılacak dilin veya metnin, Windows 10 ' da çalışmak üzere yazım denetimi yapmak için bir giriş dili olarak eklenmesi gerektiğini unutmayın.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4.6|
|Tür|Çalışma Zamanı|
