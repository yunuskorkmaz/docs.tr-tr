---
title: 'Azaltma: Pointer tabanlı Dokunmatik ve Stylus Desteği'
ms.date: 04/07/2017
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- WPF pointer-based touch and stylus stack
ms.assetid: f99126b5-c396-48f9-8233-8f36b4c9e717
ms.openlocfilehash: 023c38f66611bd0022699d3f62d90c3923585012
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77094481"
---
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a>Azaltma: Pointer tabanlı Dokunmatik ve Stylus Desteği

.NET Framework 4.7'yi hedefleyen ve Windows 10 Creators Update'ten başlayarak `WM_POINTER`Windows'da çalışan WPF uygulamaları isteğe bağlı wpf dokunmatik/stylus yığınına olanak sağlayabilir.

## <a name="impact"></a>Etki

İşaretçi tabanlı dokunma/kalem desteğini açıkça etkinleştirmeyen geliştiriciler, WPF touch/stylus davranışında herhangi bir değişiklik görmemelidir.

İsteğe bağlı `WM_POINTER`tabanlı dokunmatik/kalem yığınıyla ilgili bilinen güncel sorunlar şunlardır:

- Gerçek zamanlı mürekkep için destek yok.

   Mürekkep ve kalem eklentileri hala çalışırken, düşük performansa yol açabilecek ui iş parçacığı üzerinde işlenir.

- Dokunma/kalem etkinliklerinden fare olaylarına terfi değişiklikleri nedeniyle davranış değişiklikleri.

  - Manipülasyon farklı davranabilir.

  - Sürükle/Bırak, dokunma girişi için uygun geri bildirim göstermez. (Bu, kalem girişini etkilemez.)

  - Dokunma/kalem olaylarında Sürükle/Bırak başlatılamaz.

      Bu, fare girişi algılanıncaya kadar uygulamanın yanıt vermemesine neden olabilir. Bunun yerine, geliştiriciler fare olaylarından sürükle ve bırak başlatmalıdır.

## <a name="opting-in-to-wm_pointer-based-touchstylus-support"></a>WM_POINTER tabanlı dokunmatik/stylus desteğini seçme

Bu yığını etkinleştirmek isteyen geliştiriciler, uygulamalarının *app.config* dosyasına aşağıdakileri ekleyebilir.

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

Bu girişi kaldırmak veya bu `false` isteğe bağlı yığını kapatmak için değerini ayarlama.

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama uyumluluğu](application-compatibility.md)
