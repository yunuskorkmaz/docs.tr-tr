---
title: UI Otomasyon Yerleştirme Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, dock
- dock control pattern
- UI Automation, dock control pattern
ms.assetid: ea3d2212-7c8e-4dd7-bf08-73141ca2d4fb
ms.openlocfilehash: bc426634f981356c4e183da421c9ced99469b87c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647170"
---
# <a name="implementing-the-ui-automation-dock-control-pattern"></a>UI Otomasyon Yerleştirme Denetim Düzenini Uygulama
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu, yönergeleri ve uygulama kuralları tanıtır <xref:System.Windows.Automation.Provider.IDockProvider>, özellikler hakkında bilgiler dahil olmak üzere. Ek başvurular bağlantılar konunun sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.DockPattern> Denetim düzeni yerleştirme bir kapsayıcıdaki bir denetim noktası özelliklerini göstermek için kullanılır. Alt öğeleri Yatayda ve Dikeyde, birbirine göre düzenlemek izin veren bir denetimi bir yerleştirme kapsayıcıdır. Bu denetim düzeni uygulama denetimleri örnekleri için bkz: [denetim düzeni eşlemesi için UI Otomasyonu istemcileri](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
 ![İki yerleşik alt ile kapsayıcı yerleştirme. ](../../../docs/framework/ui-automation/media/uia-dockpattern-dockingexample.PNG "UIA_DockPattern_DockingExample")  
Visual Studio'dan örnek "Class View" penceresinde DockPosition.Right ve "Hata listesi" penceresinde olduğu yerleştirme DockPosition.Bottom olduğu  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama yönergeleri ve kuralları  
 Dock denetim düzeni uygularken aşağıdaki yönergeler ve kuralları dikkat edin:  
  
- <xref:System.Windows.Automation.Provider.IDockProvider> yerleştirme kapsayıcının herhangi bir özelliği ya da yerleştirme kapsayıcıdaki geçerli denetim bitişik yerleştirilen denetimlerin herhangi bir özelliği kullanıma sunmuyor.  
  
- Denetimleri birbirine geçerli kendi z-düzeni tabanlı yerleştirilmiştir; en yüksek yerleştirme kapsayıcının belirtilen edge'den yerleştirilen, z düzenini yatırımlarından, daha da esnetmenize.  
  
- Yerleştirme kapsayıcı boyutlandırılırsa, kapsayıcı içindeki herhangi bir yerleşik denetim, bunlar ilk olarak yerleştirildi kenarına temizleme konumlandırılmasına. Yerleşik denetimler de yerleştirme davranışını göre kapsayıcıdaki herhangi bir alanı doldurmak için boyutlandırılır kendi <xref:System.Windows.Automation.DockPosition>. Örneğin, varsa <xref:System.Windows.Automation.DockPosition.Top> belirtilir ve denetimin sol tarafında tüm kullanılabilir alanı dolduracak şekilde genişletin. Varsa <xref:System.Windows.Automation.DockPosition.Fill> belirtilirse, denetimin dört tarafına tüm kullanılabilir alanı dolduracak şekilde genişletir.  
  
- Bir çoklu monitör sisteminde sol veya sağ tarafında geçerli izleyici denetimleri yerleştirme. Bu mümkün değilse, en soldaki monitöre sol tarafındaki veya sağdaki ekranın sağ tarafındaki dock.  
  
<a name="Required_Members_for_IDockProvider"></a>   
## <a name="required-members-for-idockprovider"></a>Gerekli üyeleri IDockProvider için  
 Aşağıdaki özellikleri ve yöntemleri IDockProvider arabirim uygulamak için gereklidir.  
  
|Gerekli üyeleri|Üye türü|Notlar|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IDockProvider.DockPosition%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A>|Yöntem|Yok.|  
  
 Bu denetim düzeni, ilişkili olay vardır.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Özel Durumlar  
 Sağlayıcıları, aşağıdaki özel durumlar gerekir.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A><br /><br /> -Bir denetimi istenen dock stili yürütebilmek için değil.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Denetim Desenlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [UI Otomasyon Ağacına Genel Bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
