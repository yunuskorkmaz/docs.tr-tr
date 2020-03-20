---
title: UI Otomasyon Yerleştirme Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, dock
- dock control pattern
- UI Automation, dock control pattern
ms.assetid: ea3d2212-7c8e-4dd7-bf08-73141ca2d4fb
ms.openlocfilehash: b1213791609245209fa37e3cdcb0876c963bfeb0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180200"
---
# <a name="implementing-the-ui-automation-dock-control-pattern"></a>UI Otomasyon Yerleştirme Denetim Düzenini Uygulama
> [!NOTE]
> Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır. Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu <xref:System.Windows.Automation.Provider.IDockProvider>konu, özellikler hakkında bilgi de dahil olmak üzere uygulama yönergeleri ve kuralları sunar. Ek başvurulara bağlantılar konunun sonunda listelenir.  
  
 Denetim <xref:System.Windows.Automation.DockPattern> deseni, bir yerleştirme kapsayıcısı içindeki bir denetimin dock özelliklerini ortaya çıkarmak için kullanılır. Yerleştirme kapsayıcısı, alt öğeleri birbirine göre yatay ve dikey olarak düzenlemenizi sağlayan bir denetimdir. Bu denetim deseni uygulayan denetim örnekleri için, [UI Otomasyon Istemcileri için Denetim Deseni Eşleciliği'ne](control-pattern-mapping-for-ui-automation-clients.md)bakın.  
  
 ![İki kenetlenmiş çocukla kenetlenmiş konteynır.](./media/uia-dockpattern-dockingexample.PNG "UIA_DockPattern_DockingExample")  
"Sınıf Görünümü" Penceresinin DockPosition.Right ve "Hata Listesi" Penceresinin DockPosition olduğu Visual Studio'dan Yerleştirme Örneği.Alt  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Uygulama Yönergeleri ve Sözleşmeleri  
 Dock denetim modelini uygularken aşağıdaki yönergeleri ve kuralları dikkate alabelirtin:  
  
- <xref:System.Windows.Automation.Provider.IDockProvider>yerleştirme kabının herhangi bir özelliğini veya yerleştirme kabı içindeki geçerli denetime bitişik olarak sabitlenmiş denetimlerin özelliklerini ortaya çıkarmaz.  
  
- Denetimler, geçerli z sıralarına göre birbirine göre sabitlenir; z-sıra yerleşimleri ne kadar yüksekse, yerleştirme kabının belirtilen kenarından o kadar uzağa yerleştirilirler.  
  
- Yerleştirme kapsayıcısı yeniden boyutlandırılırsa, konteyneriçindeki sabitlenmiş denetimler, ilk olarak sabitlendikleri kenarına yeniden konumlandırılır. Kenetlenmiş denetimler de kendi <xref:System.Windows.Automation.DockPosition>yerleştirme davranışına göre kapsayıcı içinde herhangi bir alanı doldurmak için yeniden boyutlandırAcak . Örneğin, <xref:System.Windows.Automation.DockPosition.Top> belirtilirse, denetimin sol ve sağ tarafları kullanılabilir alanı doldurmak için genişler. <xref:System.Windows.Automation.DockPosition.Fill> Belirtilirse, denetimin dört tarafı kullanılabilir alanı doldurmak için genişler.  
  
- Çoklu monitör sisteminde, denetimler geçerli monitörün sol veya sağ tarafına dock gerekir. Bu mümkün değilse, en soldaki monitörün sol tarafına veya en sağdaki monitörün sağ tarafına dock gerekir.  
  
<a name="Required_Members_for_IDockProvider"></a>
## <a name="required-members-for-idockprovider"></a>IDockProvider için Gerekli Üyeler  
 IDockProvider arabiriminin uygulanması için aşağıdaki özellikler ve yöntemler gereklidir.  
  
|Gerekli üyeler|Üye tipi|Notlar|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IDockProvider.DockPosition%2A>|Özellik|None|  
|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A>|Yöntem|None|  
  
 Bu denetim deseni ilişkili olaylar vardır.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Özel durumlar  
 Sağlayıcılar aşağıdaki özel durumları atmalıdır.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A><br /><br /> - Bir denetim istenen dock stilini yürütemediğinde.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Denetim Desenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
