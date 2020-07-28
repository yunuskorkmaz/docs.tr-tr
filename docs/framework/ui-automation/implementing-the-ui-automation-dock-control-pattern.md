---
title: UI Otomasyon Yerleştirme Denetim Düzenini Uygulama
description: UI Otomasyon Dock denetim modelini uygulamayı öğrenin. Bir denetimin dock özelliklerini göstermek için Dockmodel denetim modelini kullanın. IDockProvider 'ı uygulayın.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, dock
- dock control pattern
- UI Automation, dock control pattern
ms.assetid: ea3d2212-7c8e-4dd7-bf08-73141ca2d4fb
ms.openlocfilehash: 8080d78c7bded3cb884f92948eb1259cda5544dc
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165898"
---
# <a name="implementing-the-ui-automation-dock-control-pattern"></a>UI Otomasyon Yerleştirme Denetim Düzenini Uygulama
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu <xref:System.Windows.Automation.Provider.IDockProvider> , özellikler hakkında bilgiler de dahil olmak üzere uygulama yönergelerini ve kurallarını tanıtır. Ek başvuruların bağlantıları konunun sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.DockPattern>Denetim deseninin, bir yerleştirme kapsayıcısı içindeki denetimin dock özelliklerini göstermek için kullanılır. Bir yerleştirme kapsayıcısı, alt öğeleri yatay ve dikey olarak birbirlerine göre düzenlemenizi sağlayan bir denetimdir. Bu denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](control-pattern-mapping-for-ui-automation-clients.md).  
  
 ![İki sabitlenmiş alt öğe ile kapsayıcıyı sabitleme.](./media/uia-dockpattern-dockingexample.PNG "UIA_DockPattern_DockingExample")  
Visual Studio 'dan "Sınıf Görünümü" penceresinin DockPosition olduğu yere yerleştirme örneği. Right ve "Hata Listesi" Window, DockPosition. Bottom  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Uygulama kılavuzları ve kuralları  
 Dock denetim modelini uygularken, aşağıdaki kılavuz ve kurallara göz önünde yer verilmiştir:  
  
- <xref:System.Windows.Automation.Provider.IDockProvider>, yerleştirme kapsayıcısının veya yerleştirme kapsayıcısı içindeki geçerli denetime bitişik yerleştirilmiş denetimlerin özelliklerinin herhangi bir özelliğini açığa çıkarmaz.  
  
- Denetimler, geçerli z sıralarına göre birbirlerine göre sabitlenebilir; z sırası yerleşimi arttıkça, yerleştirme kapsayıcısının belirtilen kenarından de yerleştirilirler.  
  
- Yerleştirme kapsayıcısı yeniden boyutlandırılırsa, kapsayıcıdaki tüm yerleşik denetimler, özgün olarak yerleştirildikleri kenara yeniden konumlandırılacaktır. Sabitlenmiş denetimler Ayrıca, kapsayıcının içindeki herhangi bir alanı kendi yerleştirme davranışına göre dolduracak şekilde yeniden boyutlandırılır <xref:System.Windows.Automation.DockPosition> . Örneğin, belirtilirse, <xref:System.Windows.Automation.DockPosition.Top> denetimin sol ve sağ kenarları, kullanılabilir alanı dolduracak şekilde genişletilir. <xref:System.Windows.Automation.DockPosition.Fill>Belirtilmişse, denetimin dört kenarı kullanılabilir alanı dolduracak şekilde genişletilir.  
  
- Birden çok Monitor sisteminde, denetimler geçerli izleyicinin sol veya sağ tarafına yerleştirilmelidir. Bu mümkün değilse, en soldaki izleyicinin sol tarafına veya en sağdaki monitörün sağ tarafına yerleştirilmelidir.  
  
<a name="Required_Members_for_IDockProvider"></a>
## <a name="required-members-for-idockprovider"></a>IDockProvider için gerekli Üyeler  
 IDockProvider arabirimini uygulamak için aşağıdaki özellikler ve Yöntemler gereklidir.  
  
|Gerekli Üyeler|Üye türü|Notlar|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IDockProvider.DockPosition%2A>|Özellik|Hiçbiri|  
|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A>|Yöntem|Hiçbiri|  
  
 Bu denetim deseninin ilişkili olayları yok.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Özel durumlar  
 Sağlayıcılar aşağıdaki özel durumları oluşturması gerekir.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A><br /><br /> -Bir denetim istenen yuva stilini yürütemediğinde.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyon Denetim Düzenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyon Sağlayıcısında Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyon Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
