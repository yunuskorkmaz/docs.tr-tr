---
title: UI Otomasyon Yerleştirme Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, dock
- dock control pattern
- UI Automation, dock control pattern
ms.assetid: ea3d2212-7c8e-4dd7-bf08-73141ca2d4fb
ms.openlocfilehash: 1e2084483a34709392b9d3ceab02472c36944132
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435440"
---
# <a name="implementing-the-ui-automation-dock-control-pattern"></a>UI Otomasyon Yerleştirme Denetim Düzenini Uygulama
> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, özellikler hakkında bilgiler de dahil olmak üzere <xref:System.Windows.Automation.Provider.IDockProvider>uygulamak için kılavuz ve kuralları tanıtır. Ek başvuruların bağlantıları konunun sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.DockPattern> denetim stili, bir denetimin dock özelliklerini yerleştirme kapsayıcısı içinde göstermek için kullanılır. Bir yerleştirme kapsayıcısı, alt öğeleri yatay ve dikey olarak birbirlerine göre düzenlemenizi sağlayan bir denetimdir. Bu denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](control-pattern-mapping-for-ui-automation-clients.md).  
  
 ![İki sabitlenmiş alt öğe ile kapsayıcıyı sabitleme.](./media/uia-dockpattern-dockingexample.PNG "UIA_DockPattern_DockingExample")  
Visual Studio 'dan "Sınıf Görünümü" penceresinin DockPosition olduğu yere yerleştirme örneği. Right ve "Hata Listesi" Window, DockPosition. Bottom  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama kılavuzları ve kuralları  
 Dock denetim modelini uygularken, aşağıdaki kılavuz ve kurallara göz önünde yer verilmiştir:  
  
- <xref:System.Windows.Automation.Provider.IDockProvider>, yerleştirme kapsayıcısının veya yerleştirme kapsayıcısı içindeki geçerli denetime bitişik yerleştirilmiş denetimlerin özelliklerinin herhangi bir özelliğini sunmaz.  
  
- Denetimler, geçerli z sıralarına göre birbirlerine göre sabitlenebilir; z sırası yerleşimi arttıkça, yerleştirme kapsayıcısının belirtilen kenarından de yerleştirilirler.  
  
- Yerleştirme kapsayıcısı yeniden boyutlandırılırsa, kapsayıcıdaki tüm yerleşik denetimler, özgün olarak yerleştirildikleri kenara yeniden konumlandırılacaktır. Sabitlenmiş denetimler Ayrıca, <xref:System.Windows.Automation.DockPosition>yerleştirme davranışına göre kapsayıcının içindeki herhangi bir alanı dolduracak şekilde yeniden boyutlandırılır. Örneğin, <xref:System.Windows.Automation.DockPosition.Top> belirtilirse, denetimin sol ve sağ tarafları kullanılabilir alanı dolduracak şekilde genişletilir. <xref:System.Windows.Automation.DockPosition.Fill> belirtilirse, denetimin dört kenarı kullanılabilir alanı dolduracak şekilde genişletilir.  
  
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
## <a name="exceptions"></a>Özel durumlar  
 Sağlayıcılar aşağıdaki özel durumları oluşturması gerekir.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A><br /><br /> -Bir denetim istenen yuva stilini yürütemediğinde.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Denetim Desenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
