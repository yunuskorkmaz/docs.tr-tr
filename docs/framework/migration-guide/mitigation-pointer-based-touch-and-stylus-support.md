---
title: 'Azaltma: İşaretçi tabanlı dokunmatik ve Kalem desteği'
ms.date: 04/07/2017
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- WPF pointer-based touch and stylus stack
ms.assetid: f99126b5-c396-48f9-8233-8f36b4c9e717
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9264d8eb7923663061f9bccfffe5b8f5254549f0
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66379895"
---
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a>Azaltma: İşaretçi tabanlı dokunmatik ve Kalem desteği

.NET Framework 4.7 hedefleyen ve Windows 10 Creators güncelleştirmesi ile başlayarak Windows sistemleri üzerinde çalışan WPF uygulamalarını isteğe bağlı olarak etkinleştirebilir `WM_POINTER`-WPF dokunma/ekran kalemi yığın tabanlı.

## <a name="impact"></a>Etki

Geliştiriciler, işaretçi temelli dokunma/kalemi destek açıkça etkinleştirmeyin WPF dokunma/ekran kalemi davranışında değişiklik görmeniz gerekir.

İsteğe bağlı bilinen geçerli sorunlar aşağıda verilmiştir `WM_POINTER`-dokunma/ekran kalemi yığın tabanlı:

- Gerçek zamanlı mürekkep desteği yoktur.

   Mürekkep ve ekran kalemi eklenti hala çalışırken, düşük performansa neden olabilecek UI iş parçacığı üzerinde işlenir.

- Davranış değişiklikleri nedeniyle değişiklikler, dokunma/ekran kalemi olaylardan yükseltmede fare olayları.

  - İşleme farklı şekilde davranabilir.

  - Sürükle ve bırak, dokunma girişini ilgili geri bildirim göstermez. (Bu iğne girişi etkilemez.)

  - Sürükle ve bırak, dokunma/ekran kalemi olayları artık başlatılabilir.

      Bu durum uygulama fare girişi algılandığında kadar yanıt veremez duruma gelmesine neden olabilir. Bunun yerine, geliştiriciler, sürükle başlatmak ve fare olayları bırakın.

## <a name="opting-in-to-wmpointer-based-touchstylus-support"></a>Dokunma/kalemi WM_POINTER tabanlı desteklemek için seçim

Bu yığın etkinleştirmek isteyen geliştiricilerin aşağıdakileri, uygulamanın app.config dosyasına ekleyebilirsiniz:

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

Bu girişi kaldırılıyor veya ve değerini `false` isteğe bağlı Bu yığın kapatır.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework 4.7 yeniden hedefleme değişiklikleri](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)
