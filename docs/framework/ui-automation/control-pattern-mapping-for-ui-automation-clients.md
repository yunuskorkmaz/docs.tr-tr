---
title: UI Otomasyon İstemcileri İçin Denetim Düzeni Eşleştirmesi
description: UI Otomasyon istemcileri için bir denetim modelini eşleme tablosu görüntüleyin. Belirli denetim türlerine yönelik eylemler desteklenir, koşullu olarak desteklenir veya desteklenmez.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, for UI Automation clients
- UI Automation, clients, control patterns for
ms.assetid: 8b81645b-8be3-4e26-9c98-4fb0fceca06b
ms.openlocfilehash: aaab4639a7573dd090af2e6d9bb06f896c4728f6
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276561"
---
# <a name="control-pattern-mapping-for-ui-automation-clients"></a>UI Otomasyon İstemcileri İçin Denetim Düzeni Eşleştirmesi

> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konuda denetim türleri ve bunlarla ilişkili denetim desenleri listelenmektedir.  
  
 Aşağıdaki tablo Denetim desenlerini aşağıdaki kategorilere göre düzenler:  
  
- Destekleniyor. Denetimde bu denetim deseninin desteklenmesi gerekir.  
  
- Koşullu destek. Denetim, denetimin durumuna bağlı olarak bu denetim modelini destekleyebilir.  
  
- Desteklenmez. Denetim bu denetim modelini desteklemiyor; özel denetimler bu denetim modelini destekleyebilir.  
  
> [!NOTE]
> Bazı denetimlerin, denetimin işlevselliğine bağlı olarak birkaç denetim deseni için koşullu desteği vardır. Örneğin, menü öğesi denetimi, <xref:System.Windows.Automation.InvokePattern> <xref:System.Windows.Automation.ExpandCollapsePattern> <xref:System.Windows.Automation.TogglePattern> <xref:System.Windows.Automation.SelectionItemPattern> menü denetimindeki işlevine bağlı olarak,,, veya denetim deseninin koşullu desteğine sahiptir.  
  
<a name="control_mapping_clients"></a>

## <a name="ui-automation-control-patterns-for-clients"></a>İstemciler İçin UI Otomasyon Denetim Düzenleri  
  
|Denetim türü|Desteklenir|Koşullu destek|Desteklenmiyor|  
|------------------|---------------|-------------------------|-------------------|  
|Düğme|Yok|Çağır, aç, Genişlet Daralt|Yok|  
|Takvim|Kılavuz, tablo|Seçim, kaydırma|Değer|  
|Onay kutusu|İki Durumlu Düğme|Yok|Yok|  
|Birleşik Giriş Kutusu|Daralt Genişlet|Seçim, değer|Kaydırma|  
|Veri Kılavuzu|Kılavuz|Kaydırma, seçim, tablo|Yok|  
|Veri Öğesi|Seçim Öğesi|Daralt Genişlet, kılavuz öğesi, kaydırma öğesi, tablo, değiştirme, değer|Yok|  
|Belge|Metin|Kaydırma, değer|Yok|  
|Düzenle|Yok|Metin, Aralık değeri, değer|Yok|  
|Grup|Yok|Daralt Genişlet|Yok|  
|Üst bilgi|Yok|Dönüşüm|Yok|  
|Üstbilgi Öğesi|Yok|Dönüştürme, çağırma|Yok|  
|Köprü|Çağır|Değer|Yok|  
|Görüntü|Yok|Grid öğesi, tablo öğesi|Invoke, seçim öğesi|  
|Liste|Yok|Kılavuz, birden çok görünüm, kaydırma, seçim|Tablo|  
|Liste öğesi|Seçim Öğesi|Genişlet, kılavuz öğesi, çağır, kaydırma öğesi, Iki durumlu, değer|Yok|  
|Menü|Yok|Yok|Yok|  
|Menü Çubuğu|Yok|Daralt Genişlet, yerleştir, Dönüştür|Yok|  
|Menü Öğesi|Yok|Daralt Genişlet, çağır, seçim öğesi, geçiş yap|Yok|  
|Bölme|Yok|Dock. Kaydır, Dönüştür|Pencere|  
|İlerleme Çubuğu|Yok|Aralık değeri, değer|Yok|  
|Radyo Düğmesi|Seçim Öğesi|Yok|İki Durumlu Düğme|  
|Kaydırma Çubuğu|Yok|Aralık Değeri|Kaydırma|  
|Ayırıcı|Yok|Yok|Yok|  
|Kaydırıcı|Yok|Aralık değeri, seçim, değer|Yok|  
|Değer Değiştirici|Yok|Aralık değeri, seçim, değer|Yok|  
|Bölünmüş Düğme|Çağır, Genişlet Daralt|Yok|Yok|  
|Durum Çubuğu|Yok|Kılavuz|Yok|  
|Tab|Seçim|Kaydırma|Yok|  
|Sekme Öğesi|Seçim Öğesi|Yok|Çağır|  
|Tablo|Kılavuz, kılavuz öğesi, tablo, tablo öğesi|Yok|Yok|  
|Metin|Yok|Grid öğesi, tablo öğesi, metin|Değer|  
|Parmak|Dönüşüm|Yok|Yok|  
|Başlık Çubuğu|Yok|Yok|Yok|  
|Araç çubuğu|Yok|Yerleştir, Genişlet Daralt, Dönüştür|Yok|  
|Araç Ipucu|Yok|Metin, pencere|Yok|  
|Ağaç|Yok|Kaydırma, seçim|Yok|  
|Ağaç Öğesi|Daralt Genişlet|Çağırma, kaydırma öğesi, seçim öğesi, değiştirme|Yok|  
|Pencere|Dönüştür, pencere|Dock|Yok|  
  
> [!NOTE]
> Denetim türünde desteklenen denetim desenleri yoksa ancak bir veya daha fazla koşullu desteklenen denetim deseni varsa, bu koşullu denetim desenlerinden biri her zaman desteklenecektir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
