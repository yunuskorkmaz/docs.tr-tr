---
title: UI Otomasyon İstemcileri İçin Denetim Düzeni Eşleştirmesi
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, for UI Automation clients
- UI Automation, clients, control patterns for
ms.assetid: 8b81645b-8be3-4e26-9c98-4fb0fceca06b
ms.openlocfilehash: 64c3dccac61ceb2934904c5d03fc96d961976d6b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932620"
---
# <a name="control-pattern-mapping-for-ui-automation-clients"></a>UI Otomasyon İstemcileri İçin Denetim Düzeni Eşleştirmesi
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konuda denetim türleri ve bunlarla ilişkili denetim desenleri listelenmektedir.  
  
 Aşağıdaki tablo Denetim desenlerini aşağıdaki kategorilere göre düzenler:  
  
- Desteklenen. Denetimde bu denetim deseninin desteklenmesi gerekir.  
  
- Koşullu destek. Denetim, denetimin durumuna bağlı olarak bu denetim modelini destekleyebilir.  
  
- Desteklenmez. Denetim bu denetim modelini desteklemiyor; özel denetimler bu denetim modelini destekleyebilir.  
  
> [!NOTE]
> Bazı denetimlerin, denetimin işlevselliğine bağlı olarak birkaç denetim deseni için koşullu desteği vardır. Örneğin, menü öğesi denetimi, menü denetimindeki işlevine <xref:System.Windows.Automation.InvokePattern>bağlı olarak <xref:System.Windows.Automation.TogglePattern>, <xref:System.Windows.Automation.ExpandCollapsePattern>,, veya <xref:System.Windows.Automation.SelectionItemPattern> denetim deseninin koşullu desteğine sahiptir.  
  
<a name="control_mapping_clients"></a>   
## <a name="ui-automation-control-patterns-for-clients"></a>İstemciler İçin UI Otomasyon Denetim Düzenleri  
  
|Denetim türü|Desteklenir|Koşullu destek|Desteklenmez|  
|------------------|---------------|-------------------------|-------------------|  
|Düğme|Yok.|Çağır, aç, Genişlet Daralt|Yok.|  
|Takvim|Kılavuz, tablo|Seçim, kaydırma|Değer|  
|Onay kutusu|İki Durumlu Düğme|Yok.|Yok.|  
|Birleşik Giriş Kutusu|Daralt Genişlet|Seçim, değer|Kaydırma|  
|Veri Kılavuzu|Kılavuz|Kaydırma, seçim, tablo|Yok.|  
|Veri Öğesi|Seçim Öğesi|Daralt Genişlet, kılavuz öğesi, kaydırma öğesi, tablo, değiştirme, değer|Yok.|  
|Belge|Metin|Kaydırma, değer|Yok.|  
|Düzenle|Yok.|Metin, Aralık değeri, değer|Yok.|  
|Grup|Yok.|Daralt Genişlet|Yok.|  
|Üstbilgi|Yok.|Dönüştürme|Yok.|  
|Üstbilgi Öğesi|Yok.|Dönüştürme, çağırma|Yok.|  
|Köprü|Çağır|Değer|Yok.|  
|Görüntü|Yok.|Grid öğesi, tablo öğesi|Invoke, seçim öğesi|  
|List|Yok.|Kılavuz, birden çok görünüm, kaydırma, seçim|Tablo|  
|Liste öğesi|Seçim Öğesi|Genişlet, kılavuz öğesi, çağır, kaydırma öğesi, Iki durumlu, değer|Yok.|  
|Menü|Yok.|Yok.|Yok.|  
|Menü Çubuğu|Yok.|Daralt Genişlet, yerleştir, Dönüştür|Yok.|  
|Menü Öğesi|Yok.|Daralt Genişlet, çağır, seçim öğesi, geçiş yap|Yok.|  
|Bölme|Yok.|Dock. Kaydır, Dönüştür|Pencere|  
|İlerleme Çubuğu|Yok.|Aralık değeri, değer|Yok.|  
|Radyo Düğmesi|Seçim Öğesi|Yok.|İki Durumlu Düğme|  
|Kaydırma Çubuğu|Yok.|Aralık Değeri|Kaydırma|  
|Ayırıcı|Yok.|Yok.|Yok.|  
|Kaydırıcı|Yok.|Aralık değeri, seçim, değer|Yok.|  
|Değer Değiştirici|Yok.|Aralık değeri, seçim, değer|Yok.|  
|Bölünmüş Düğme|Çağır, Genişlet Daralt|Yok.|Yok.|  
|Durum Çubuğu|Yok.|Kılavuz|Yok.|  
|Tab|Seçim|Kaydırma|Yok.|  
|Sekme Öğesi|Seçim Öğesi|Yok.|Çağır|  
|Tablo|Kılavuz, kılavuz öğesi, tablo, tablo öğesi|Yok.|Yok.|  
|Metin|Yok.|Grid öğesi, tablo öğesi, metin|Değer|  
|Parmak|Dönüştürme|Yok.|Yok.|  
|Başlık Çubuğu|Yok.|Yok.|Yok.|  
|Araç çubuğu|Yok.|Yerleştir, Genişlet Daralt, Dönüştür|Yok.|  
|Araç Ipucu|Yok.|Metin, pencere|Yok.|  
|Ağaç|Yok.|Kaydırma, seçim|Yok.|  
|Ağaç Öğesi|Daralt Genişlet|Çağırma, kaydırma öğesi, seçim öğesi, değiştirme|Yok.|  
|Pencere|Dönüştür, pencere|Dock|Yok.|  
  
> [!NOTE]
> Denetim türünde desteklenen denetim desenleri yoksa ancak bir veya daha fazla koşullu desteklenen denetim deseni varsa, bu koşullu denetim desenlerinden biri her zaman desteklenecektir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonuna Genel Bakış](../../../docs/framework/ui-automation/ui-automation-overview.md)
