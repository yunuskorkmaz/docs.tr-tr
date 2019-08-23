---
title: UI Otomasyon Yerleştirme Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, dock
- dock control pattern
- UI Automation, dock control pattern
ms.assetid: ea3d2212-7c8e-4dd7-bf08-73141ca2d4fb
ms.openlocfilehash: 9bc4f80569dc2bab68e3f65c9e99df72df372171
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968912"
---
# <a name="implementing-the-ui-automation-dock-control-pattern"></a>UI Otomasyon Yerleştirme Denetim Düzenini Uygulama
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu, özellikler hakkında bilgiler de dahil <xref:System.Windows.Automation.Provider.IDockProvider>olmak üzere uygulama yönergelerini ve kurallarını tanıtır. Ek başvuruların bağlantıları konunun sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.DockPattern> Denetim deseninin, bir yerleştirme kapsayıcısı içindeki denetimin dock özelliklerini göstermek için kullanılır. Bir yerleştirme kapsayıcısı, alt öğeleri yatay ve dikey olarak birbirlerine göre düzenlemenizi sağlayan bir denetimdir. Bu denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
 ![İki sabitlenmiş alt öğe ile kapsayıcıyı sabitleme.](../../../docs/framework/ui-automation/media/uia-dockpattern-dockingexample.PNG "UIA_DockPattern_DockingExample")  
Visual Studio 'dan "Sınıf Görünümü" penceresinin DockPosition olduğu yere yerleştirme örneği. Right ve "Hata Listesi" Window, DockPosition. Bottom  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama kılavuzları ve kuralları  
 Dock denetim modelini uygularken, aşağıdaki kılavuz ve kurallara göz önünde yer verilmiştir:  
  
- <xref:System.Windows.Automation.Provider.IDockProvider>, yerleştirme kapsayıcısının veya yerleştirme kapsayıcısı içindeki geçerli denetime bitişik yerleştirilmiş denetimlerin özelliklerinin herhangi bir özelliğini açığa çıkarmaz.  
  
- Denetimler, geçerli z sıralarına göre birbirlerine göre sabitlenebilir; z sırası yerleşimi arttıkça, yerleştirme kapsayıcısının belirtilen kenarından de yerleştirilirler.  
  
- Yerleştirme kapsayıcısı yeniden boyutlandırılırsa, kapsayıcıdaki tüm yerleşik denetimler, özgün olarak yerleştirildikleri kenara yeniden konumlandırılacaktır. Sabitlenmiş denetimler Ayrıca, kapsayıcının içindeki herhangi bir alanı kendi <xref:System.Windows.Automation.DockPosition>yerleştirme davranışına göre dolduracak şekilde yeniden boyutlandırılır. Örneğin, <xref:System.Windows.Automation.DockPosition.Top> belirtilirse, denetimin sol ve sağ kenarları, kullanılabilir alanı dolduracak şekilde genişletilir. <xref:System.Windows.Automation.DockPosition.Fill> Belirtilmişse, denetimin dört kenarı kullanılabilir alanı dolduracak şekilde genişletilir.  
  
- Birden çok Monitor sisteminde, denetimler geçerli izleyicinin sol veya sağ tarafına yerleştirilmelidir. Bu mümkün değilse, en soldaki izleyicinin sol tarafına veya en sağdaki monitörün sağ tarafına yerleştirilmelidir.  
  
<a name="Required_Members_for_IDockProvider"></a>   
## <a name="required-members-for-idockprovider"></a>IDockProvider için gerekli Üyeler  
 IDockProvider arabirimini uygulamak için aşağıdaki özellikler ve Yöntemler gereklidir.  
  
|Gerekli Üyeler|Üye türü|Notlar|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IDockProvider.DockPosition%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A>|Yöntem|Yok.|  
  
 Bu denetim deseninin ilişkili olayları yok.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Özel Durumlar  
 Sağlayıcılar aşağıdaki özel durumları oluşturması gerekir.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A><br /><br /> -Bir denetim istenen yuva stilini yürütemediğinde.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Denetim Desenlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [UI Otomasyon Ağacına Genel Bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
