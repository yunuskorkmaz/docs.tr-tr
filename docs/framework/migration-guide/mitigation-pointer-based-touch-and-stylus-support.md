---
title: 'Risk azaltma: Işaretçi tabanlı dokunmatik ve Stilus desteği'
ms.date: 04/07/2017
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- WPF pointer-based touch and stylus stack
ms.assetid: f99126b5-c396-48f9-8233-8f36b4c9e717
ms.openlocfilehash: 023c38f66611bd0022699d3f62d90c3923585012
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094481"
---
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a>Risk azaltma: Işaretçi tabanlı dokunmatik ve Stilus desteği

.NET Framework 4,7 ' i hedefleyen ve Windows 10 Creators Update ile başlayan WPF uygulamaları, isteğe bağlı `WM_POINTER`tabanlı bir WPF dokunmatik/Stilus yığınını etkinleştirebilir.

## <a name="impact"></a>Etkisi

İşaretçi tabanlı dokunmatik/ekran kalemi desteğinin açıkça etkinleştirilmedikleri geliştiriciler WPF dokunma/ekran kalemi davranışında değişiklik görmez.

Aşağıda, isteğe bağlı `WM_POINTER`tabanlı dokunmatik/ekran kalemi yığınında bilinen güncel sorunlar verilmiştir:

- Gerçek zamanlı mürekkep oluşturma desteği yoktur.

   Mürekkep oluşturma ve ekran kalemi eklentileri çalışmaya devam ederken, Kullanıcı arabirimi iş parçacığında işlenir ve bu da kötü performansa yol açabilir.

- Dokunmatik/ekran kalemi olaylarından fare olaylarına yükseltme yapılan değişiklikler nedeniyle davranış değişiklikleri.

  - Düzenleme farklı davranabilirler.

  - Sürükle/bırak, dokunma girişi için uygun geri bildirimi göstermez. (Bu, Stilus girişini etkilemez.)

  - Sürükle/bırak, artık dokunmatik/ekran kalemi olaylarında başlatılamaz.

      Bu, fare girişi algılanana kadar uygulamanın yanıt vermemesine neden olabilir. Bunun yerine, geliştiriciler fare olaylarından sürükle ve bırak işlemini başlatmalıdır.

## <a name="opting-in-to-wm_pointer-based-touchstylus-support"></a>WM_POINTER tabanlı dokunmatik/ekran kalemi desteğiyle opzip

Bu yığını etkinleştirmek isteyen geliştiriciler aşağıdakini uygulamanın *app. config* dosyasına ekleyebilir.

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

Bu girdiyi kaldırmak veya değerini `false` olarak ayarlamak, bu isteğe bağlı yığını kapatır.

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama uyumluluğu](application-compatibility.md)
