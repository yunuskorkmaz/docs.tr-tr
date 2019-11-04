---
title: 'Risk azaltma: Işaretçi tabanlı dokunmatik ve Stilus desteği'
ms.date: 04/07/2017
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- WPF pointer-based touch and stylus stack
ms.assetid: f99126b5-c396-48f9-8233-8f36b4c9e717
ms.openlocfilehash: 6b3e8068be2f5ed82c483b760fe100ea0a751588
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457861"
---
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a>Risk azaltma: Işaretçi tabanlı dokunmatik ve Stilus desteği

Windows 10 Creators Update ile başlayan .NET Framework 4,7 ve Windows sistemlerinde çalışan WPF uygulamaları, isteğe bağlı `WM_POINTER`tabanlı bir WPF dokunmatik/Stilus yığınını etkinleştirebilir.

## <a name="impact"></a>Etki

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

Bu yığını etkinleştirmek isteyen geliştiriciler aşağıdakini uygulamanın App. config dosyasına ekleyebilir:

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
