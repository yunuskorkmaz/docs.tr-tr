---
title: UI Otomasyon İstemcileri İçin Denetim Düzeni Eşleştirmesi
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, for UI Automation clients
- UI Automation, clients, control patterns for
ms.assetid: 8b81645b-8be3-4e26-9c98-4fb0fceca06b
ms.openlocfilehash: 689e649343c93d0670c6870098a09f61097f4fb4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180235"
---
# <a name="control-pattern-mapping-for-ui-automation-clients"></a>UI Otomasyon İstemcileri İçin Denetim Düzeni Eşleştirmesi
> [!NOTE]
> Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır. Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, denetim türlerini ve bunların ilişkili denetim modellerini listeler.  
  
 Aşağıdaki tablo denetim modellerini aşağıdaki kategorilerde düzenler:  
  
- Destekleniyor. Denetim bu denetim deseni desteklemelidir.  
  
- Şartlı destek. Denetim, denetimin durumuna bağlı olarak bu denetim deseni destekleyebilir.  
  
- Desteklenmiyor. Denetim bu denetim deseni desteklemez; özel denetimler bu denetim deseni destekleyebilir.  
  
> [!NOTE]
> Bazı denetimler, denetimin işlevselliliği bağlı olarak çeşitli denetim desenleri için koşullu desteğe sahiptir. Örneğin, menü öğesi denetimi, menü denetimindeki <xref:System.Windows.Automation.ExpandCollapsePattern> <xref:System.Windows.Automation.TogglePattern>işlevine <xref:System.Windows.Automation.SelectionItemPattern> bağlı olarak <xref:System.Windows.Automation.InvokePattern>, , veya denetim deseni için koşullu desteğe sahiptir.  
  
<a name="control_mapping_clients"></a>
## <a name="ui-automation-control-patterns-for-clients"></a>İstemciler İçin UI Otomasyon Denetim Düzenleri  
  
|Kontrol Türü|Destekleniyor|Koşullu Destek|Desteklenmiyor|  
|------------------|---------------|-------------------------|-------------------|  
|Düğme|None|Çağırma, Geçiş, Genişletme|None|  
|Takvim|Izgara, Tablo|Seçim, Kaydırma|Değer|  
|Onay Kutusu|İki Durumlu Düğme|None|None|  
|Birleşik Giriş Kutusu|Daraltma'yı Genişlet|Seçim, Değer|Kaydırma|  
|Veri Kılavuzu|Kılavuz|Kaydırma, Seçim, Tablo|None|  
|Veri Öğesi|Seçim Öğesi|Daraltma, Izgara Öğesi, Kaydırma Öğesi, Tablo, Geçiş, Değer genişletme|None|  
|Belge|Metin|Kaydırma, Değer|None|  
|Düzenle|None|Metin, Aralık Değeri, Değer|None|  
|Grup|None|Daraltma'yı Genişlet|None|  
|Üst bilgi|None|Dönüşüm|None|  
|Üstbilgi Öğesi|None|Dönüştür, Çağır|None|  
|Köprü|Çağır|Değer|None|  
|Görüntü|None|Izgara Öğesi, Tablo Öğesi|Çağırma, Seçim Öğesi|  
|Liste|None|Izgara, Çoklu Görünüm, Kaydırma, Seçim|Tablo|  
|Liste Öğesi|Seçim Öğesi|Genişletme, Izgara Öğesi, Çağır, Kaydırma Öğesi, Geçiş, Değer|None|  
|Menü|None|None|None|  
|Menü Çubuğu|None|Daraltma, Yerleştirme, Dönüştürmeyi Genişlet|None|  
|Menü Öğesi|None|Daraltma, Çağırma, Seçim Öğesini Genişletme, Geçiş|None|  
|Bölme|None|Dock. Kaydırma, Dönüştürme|Pencere|  
|İlerleme Çubuğu|None|Aralık Değeri, Değer|None|  
|Radyo Düğmesi|Seçim Öğesi|None|İki Durumlu Düğme|  
|Kaydırma Çubuğu|None|Aralık Değeri|Kaydırma|  
|Ayırıcı|None|None|None|  
|Kaydırıcı|None|Aralık Değeri, Seçimi, Değeri|None|  
|Değer Değiştirici|None|Aralık Değeri, Seçimi, Değeri|None|  
|Bölünmüş Düğme|Çağırma, Genişletme|None|None|  
|Durum Çubuğu|None|Kılavuz|None|  
|Tab|Seçim|Kaydırma|None|  
|Sekme Öğesi|Seçim Öğesi|None|Çağır|  
|Tablo|Izgara, Izgara Öğesi, Tablo, Tablo Öğesi|None|None|  
|Metin|None|Izgara Öğesi, Tablo Öğesi, Metin|Değer|  
|Parmak|Dönüşüm|None|None|  
|Başlık Çubuğu|None|None|None|  
|Araç Çubuğu|None|Dock, Genişletme Daraltma, Dönüştürme|None|  
|Araç İpucu|None|Metin, Pencere|None|  
|Ağaç|None|Kaydırma, Seçim|None|  
|Ağaç Öğesi|Daraltma'yı Genişlet|Çağırma, Öğeyi Kaydırma, Seçim Öğesi, Geçiş|None|  
|Pencere|Dönüşüm, Pencere|Dock|None|  
  
> [!NOTE]
> Denetim türünde desteklenen denetim desenleri yoksa ancak bir veya daha fazla koşullu destekli denetim desenleri varsa, bu koşullu denetim desenlerinden biri her zaman desteklenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
