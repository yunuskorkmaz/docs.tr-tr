---
title: UI Otomasyon İstemcileri İçin Denetim Düzeni Eşleştirmesi
description: UI Otomasyon istemcileri için bir denetim modelini eşleme tablosu görüntüleyin. Belirli denetim türlerine yönelik eylemler desteklenir, koşullu olarak desteklenir veya desteklenmez.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, for UI Automation clients
- UI Automation, clients, control patterns for
ms.assetid: 8b81645b-8be3-4e26-9c98-4fb0fceca06b
ms.openlocfilehash: 7673ce4ac88cc36a7c35e2e946a31d23b2ce6eca
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164189"
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
|Düğme|Hiçbiri|Çağır, aç, Genişlet Daralt|Hiçbiri|  
|Takvim|Kılavuz, tablo|Seçim, kaydırma|Değer|  
|Onay kutusu|İki Durumlu Düğme|Hiçbiri|Hiçbiri|  
|Birleşik Giriş Kutusu|Daralt Genişlet|Seçim, değer|Kaydırma|  
|Veri Kılavuzu|Kılavuz|Kaydırma, seçim, tablo|Hiçbiri|  
|Veri Öğesi|Seçim Öğesi|Daralt Genişlet, kılavuz öğesi, kaydırma öğesi, tablo, değiştirme, değer|Hiçbiri|  
|Belge|Metin|Kaydırma, değer|Hiçbiri|  
|Düzenle|Hiçbiri|Metin, Aralık değeri, değer|Hiçbiri|  
|Grup|Hiçbiri|Daralt Genişlet|Hiçbiri|  
|Üst bilgi|Hiçbiri|Dönüşüm|Hiçbiri|  
|Üstbilgi Öğesi|Hiçbiri|Dönüştürme, çağırma|Hiçbiri|  
|Köprü|Çağır|Değer|Hiçbiri|  
|Görüntü|Hiçbiri|Grid öğesi, tablo öğesi|Invoke, seçim öğesi|  
|Liste|Hiçbiri|Kılavuz, birden çok görünüm, kaydırma, seçim|Tablo|  
|Liste öğesi|Seçim Öğesi|Genişlet, kılavuz öğesi, çağır, kaydırma öğesi, Iki durumlu, değer|Hiçbiri|  
|Menü|Hiçbiri|Hiçbiri|Hiçbiri|  
|Menü Çubuğu|Hiçbiri|Daralt Genişlet, yerleştir, Dönüştür|Hiçbiri|  
|Menü Öğesi|Hiçbiri|Daralt Genişlet, çağır, seçim öğesi, geçiş yap|Hiçbiri|  
|Bölme|Hiçbiri|Dock. Kaydır, Dönüştür|Pencere|  
|İlerleme Çubuğu|Hiçbiri|Aralık değeri, değer|Hiçbiri|  
|Radyo Düğmesi|Seçim Öğesi|Hiçbiri|İki Durumlu Düğme|  
|Kaydırma Çubuğu|Hiçbiri|Aralık Değeri|Kaydırma|  
|Ayırıcı|Hiçbiri|Hiçbiri|Hiçbiri|  
|Slider|Hiçbiri|Aralık değeri, seçim, değer|Hiçbiri|  
|Değer Değiştirici|Hiçbiri|Aralık değeri, seçim, değer|Hiçbiri|  
|Bölünmüş Düğme|Çağır, Genişlet Daralt|Hiçbiri|Hiçbiri|  
|Durum Çubuğu|Hiçbiri|Kılavuz|Hiçbiri|  
|Tab|Seçim|Kaydırma|Hiçbiri|  
|Sekme Öğesi|Seçim Öğesi|Hiçbiri|Çağır|  
|Tablo|Kılavuz, kılavuz öğesi, tablo, tablo öğesi|Hiçbiri|Hiçbiri|  
|Metin|Hiçbiri|Grid öğesi, tablo öğesi, metin|Değer|  
|Parmak|Dönüşüm|Hiçbiri|Hiçbiri|  
|Başlık Çubuğu|Hiçbiri|Hiçbiri|Hiçbiri|  
|Araç çubuğu|Hiçbiri|Yerleştir, Genişlet Daralt, Dönüştür|Hiçbiri|  
|Araç Ipucu|Hiçbiri|Metin, pencere|Hiçbiri|  
|Ağaç|Hiçbiri|Kaydırma, seçim|Hiçbiri|  
|Ağaç Öğesi|Daralt Genişlet|Çağırma, kaydırma öğesi, seçim öğesi, değiştirme|Hiçbiri|  
|Pencere|Dönüştür, pencere|Dock|Hiçbiri|  
  
> [!NOTE]
> Denetim türünde desteklenen denetim desenleri yoksa ancak bir veya daha fazla koşullu desteklenen denetim deseni varsa, bu koşullu denetim desenlerinden biri her zaman desteklenecektir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
