---
title: 'Risk azaltma: Işaretçi tabanlı dokunmatik ve Stilus desteği'
description: .NET Framework 4,7 ' i hedefleyen WPF uygulamaları için isteğe bağlı WPF Touch/Stilus yığınını etkinleştirmenin etkileri hakkında bilgi edinin.
ms.date: 04/07/2017
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- WPF pointer-based touch and stylus stack
ms.assetid: f99126b5-c396-48f9-8233-8f36b4c9e717
ms.openlocfilehash: d0c0effeaa727c615dddc3b92cdd34aafde65705
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475430"
---
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a>Risk azaltma: Işaretçi tabanlı dokunmatik ve Stilus desteği

.NET Framework 4,7 ' i hedefleyen ve Windows 10 Creators Update ile başlayarak Windows üzerinde çalışan WPF uygulamaları, isteğe bağlı tabanlı bir `WM_POINTER` WPF dokunmatik/Stilus yığınını etkinleştirebilir.

## <a name="impact"></a>Etki

İşaretçi tabanlı dokunmatik/ekran kalemi desteğinin açıkça etkinleştirilmedikleri geliştiriciler WPF dokunma/ekran kalemi davranışında değişiklik görmez.

İsteğe bağlı `WM_POINTER` tabanlı dokunmatik/Stilus Stack ile ilgili olarak bilinen geçerli sorunlar şunlardır:

- Gerçek zamanlı mürekkep oluşturma desteği yoktur.

   Mürekkep oluşturma ve ekran kalemi eklentileri çalışmaya devam ederken, Kullanıcı arabirimi iş parçacığında işlenir ve bu da kötü performansa yol açabilir.

- Dokunmatik/ekran kalemi olaylarından fare olaylarına yükseltme yapılan değişiklikler nedeniyle davranış değişiklikleri.

  - Düzenleme farklı davranabilirler.

  - Sürükle/bırak, dokunma girişi için uygun geri bildirimi göstermez. (Bu, Stilus girişini etkilemez.)

  - Sürükle/bırak, artık dokunmatik/ekran kalemi olaylarında başlatılamaz.

      Bu, fare girişi algılanana kadar uygulamanın yanıt vermemesine neden olabilir. Bunun yerine, geliştiriciler fare olaylarından sürükle ve bırak işlemini başlatmalıdır.

## <a name="opting-in-to-wm_pointer-based-touchstylus-support"></a>WM_POINTER tabanlı dokunmatik/ekran kalemi desteğiyle opzip

Bu yığını etkinleştirmek isteyen geliştiriciler aşağıdakini uygulamanın *app.config* dosyasına ekleyebilir.

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

Bu giriş kaldırılıyor veya değeri, `false` Bu isteğe bağlı yığını devre dışı olarak ayarlanıyor.

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama uyumluluğu](application-compatibility.md)
