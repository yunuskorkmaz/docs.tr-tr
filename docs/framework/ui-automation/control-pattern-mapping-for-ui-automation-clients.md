---
title: UI Otomasyon İstemcileri İçin Denetim Düzeni Eşleştirmesi
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, for UI Automation clients
- UI Automation, clients, control patterns for
ms.assetid: 8b81645b-8be3-4e26-9c98-4fb0fceca06b
ms.openlocfilehash: b98735b111d634584ec019a75d942f39e38cc8c5
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57679586"
---
# <a name="control-pattern-mapping-for-ui-automation-clients"></a>UI Otomasyon İstemcileri İçin Denetim Düzeni Eşleştirmesi
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu, denetim türlerini ve bunların ilişkili denetim düzenleri listeler.  
  
 Aşağıdaki tabloda, Denetim düzenleri aşağıdaki kategorilere göre düzenler:  
  
-   Desteklenen. Denetim, bu denetim düzenini desteklemelidir.  
  
-   Koşullu desteği. Denetim, denetimin durumunun bağlı olarak bu denetim düzeni destekleyebilir.  
  
-   Desteklenmez. Denetim, bu denetim düzeni desteklemiyor; özel denetimler, bu denetim düzeni destekleyebilir.  
  
> [!NOTE]
>  Bazı denetimler, denetimi işlevlerini bağlı olarak birkaç denetim desenleri için koşullu destek vardır. Örneğin, menü öğesi denetimi için koşullu destek sahip <xref:System.Windows.Automation.InvokePattern>, <xref:System.Windows.Automation.ExpandCollapsePattern>, <xref:System.Windows.Automation.TogglePattern>, veya <xref:System.Windows.Automation.SelectionItemPattern> menü denetimi, işlev bağlı olarak, Denetim düzeni.  
  
<a name="control_mapping_clients"></a>   
## <a name="ui-automation-control-patterns-for-clients"></a>İstemciler İçin UI Otomasyon Denetim Düzenleri  
  
|Denetim türü|Desteklenir|Koşullu destek|Desteklenmez|  
|------------------|---------------|-------------------------|-------------------|  
|Düğme|Hiçbiri|Çağırma, Değiştir, Genişlet ve Daralt|Hiçbiri|  
|Takvim|Kılavuz, tablo|Seçim, kaydırma|Değer|  
|Onay kutusu|İki Durumlu Düğme|Hiçbiri|Hiçbiri|  
|Birleşik Giriş Kutusu|Genişlet ve Daralt|Seçim, değer|Kaydırma|  
|Veri Kılavuzu|Kılavuz|Kaydır, seçimi, tablo|Hiçbiri|  
|Veri Öğesi|Seçim Öğesi|Daraltma, kılavuz öğesi, kaydırma öğesi, tablo, geçiş, değer'ı genişletin.|Hiçbiri|  
|Belge|Metin|Kaydırma, değer|Hiçbiri|  
|Düzenle|Hiçbiri|Aralık değeri, bir metin değeri|Hiçbiri|  
|Grup|Hiçbiri|Genişlet ve Daralt|Hiçbiri|  
|Üstbilgi|Hiçbiri|Dönüştürme|Hiçbiri|  
|Üstbilgi Öğesi|Hiçbiri|Dönüştürme, çağırma|Hiçbiri|  
|Köprü|Çağır|Değer|Hiçbiri|  
|Görüntü|Hiçbiri|Kılavuz öğesi, Tablo öğesi|Seçim öğesi çağırma|  
|List|Hiçbiri|Kılavuz, birden çok görünüm Kaydır, seçimi|Tablo|  
|Liste öğesi|Seçim Öğesi|Genişlet ve Daralt, kılavuz öğesi çağırmak, kaydırma öğesi, Değiştir, değer|Hiçbiri|  
|Menü|Hiçbiri|Yok.|Hiçbiri|  
|Menü Çubuğu|Hiçbiri|Dönüştürme Daralt, Dock'ı genişletin|Hiçbiri|  
|Menü Öğesi|Hiçbiri|Genişlet ve Daralt, seçim öğesi geçiş çağırma|Hiçbiri|  
|Bölme|Hiçbiri|Dock. Kaydırma, dönüştürme|Pencere|  
|İlerleme Çubuğu|Hiçbiri|Aralık değeri|Hiçbiri|  
|Radyo Düğmesi|Seçim Öğesi|Hiçbiri|İki Durumlu Düğme|  
|Kaydırma Çubuğu|Hiçbiri|Aralık Değeri|Kaydırma|  
|Ayırıcı|Hiçbiri|Yok.|Hiçbiri|  
|Kaydırıcı|Hiçbiri|Aralık değeri, seçim, değeri|Hiçbiri|  
|Değer Değiştirici|Hiçbiri|Aralık değeri, seçim, değeri|Hiçbiri|  
|Bölünmüş Düğme|Çağırma, Genişlet ve Daralt|Hiçbiri|Hiçbiri|  
|Durum Çubuğu|Hiçbiri|Kılavuz|Hiçbiri|  
|Tab|Seçim|Kaydırma|Hiçbiri|  
|Sekme Öğesi|Seçim Öğesi|Hiçbiri|Çağır|  
|Tablo|Kılavuz, kılavuz öğesi, tablo, Tablo öğesi|Hiçbiri|Hiçbiri|  
|Metin|Hiçbiri|Kılavuz öğesi, Tablo öğesi metni|Değer|  
|Parmak|Dönüştürme|Hiçbiri|Hiçbiri|  
|Başlık Çubuğu|Hiçbiri|Yok.|Hiçbiri|  
|Araç çubuğu|Hiçbiri|Yerleştirme, genişletme daraltma, dönüştürme|Hiçbiri|  
|Araç İpucu|Hiçbiri|Pencere metni|Hiçbiri|  
|Ağaç|Hiçbiri|Kaydır, seçimi|Hiçbiri|  
|Ağaç Öğesi|Genişlet ve Daralt|Kaydırma öğesi seçim öğesi, geçiş çağırma|Hiçbiri|  
|Pencere|Dönüştürme, penceresi|Dock|Hiçbiri|  
  
> [!NOTE]
>  Bir denetim türü listelenen herhangi bir desteklenen denetimi desen varken bu koşullu denetim desenlerden birini hiç desteklenecek koşullu olarak desteklenen denetim düzenleri, bir veya daha fazla varsa zaman.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [UI Otomasyonuna Genel Bakış](../../../docs/framework/ui-automation/ui-automation-overview.md)
