---
title: "UI Otomasyon Yerleştirme Denetim Düzenini Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, dock
- dock control pattern
- UI Automation, dock control pattern
ms.assetid: ea3d2212-7c8e-4dd7-bf08-73141ca2d4fb
caps.latest.revision: "23"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 68c3dcdb1d8f15f312dea40ae59a3b1a4736c484
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-ui-automation-dock-control-pattern"></a>UI Otomasyon Yerleştirme Denetim Düzenini Uygulama
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu kılavuzları ve uygulamak için kuralları tanıtır <xref:System.Windows.Automation.Provider.IDockProvider>, özellikler hakkında bilgiler dahil olmak üzere. Ek başvurular bağlantılar konunun sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.DockPattern> Denetim düzeni takma kapsayıcı içindeki bir denetim yerleştirme özelliklerini göstermek için kullanılır. Alt öğelerini yatay ve dikey olarak, diğer göre düzenlemek izin veren bir denetim bir takma kapsayıcıdır. Bu denetim düzeni uygulama denetimleri örnekleri için bkz: [denetim düzeni eşleştirmesi UI Otomasyon istemcileri için](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
 ![Kapsayıcı yerleştirilmiş iki alt öğeyle yerleştirme. ] (../../../docs/framework/ui-automation/media/uia-dockpattern-dockingexample.PNG "UIA_DockPattern_DockingExample")  
DockPosition.Bottom olan "Sınıf Görünümü" penceresi DockPosition.Right ve "Hata listesi" penceresini olduğu örnek Visual Studio'dan yerleştirme  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama rehberi ve kuralları  
 Yerleştirme denetim düzenini uygulama, aşağıdaki yönergeleri ve kuralları dikkat edin:  
  
-   <xref:System.Windows.Automation.Provider.IDockProvider>yerleştirme kapsayıcının herhangi bir özellik veya takma kapsayıcı içindeki geçerli denetim bitişik yerleştirilmiş denetimlerinin herhangi bir özellik kullanıma sunmuyor.  
  
-   Denetimleri birbirine geçerli kendi z-sırasına göre yerleştirilmiş; en yüksek takma kapsayıcı belirtilen kenarından yerleştirilen bunlar z düzeni yatırımlarından, uzağa.  
  
-   Yerleştirme kapsayıcı boyutlandırılır, kapsayıcı içindeki herhangi bir yerleşik Denetim temizleme için bunlar ilk olarak yerleşik kenarına konumlandırılmasına. Yerleşik denetimleri de yerleştirme davranışını göre kapsayıcı içindeki herhangi bir alanı dolduracak şekilde yeniden boyutlandırılır kendi <xref:System.Windows.Automation.DockPosition>. Örneğin, varsa <xref:System.Windows.Automation.DockPosition.Top> belirtilirse, sol ve sağ tarafa denetiminin tüm kullanılabilir alanı dolduracak şekilde genişletin. Varsa <xref:System.Windows.Automation.DockPosition.Fill> belirtilmemişse, denetimi dört tarafına tüm kullanılabilir alanı dolduracak şekilde genişletin.  
  
-   Birden çok monitör sistemde sol veya sağ tarafındaki geçerli izleme denetimleri yerleştirme. Bu mümkün değilse, soldaki monitörün sol tarafındaki veya en sağdaki monitöre sağ tarafındaki yerleştirme.  
  
<a name="Required_Members_for_IDockProvider"></a>   
## <a name="required-members-for-idockprovider"></a>Gerekli üyeleri IDockProvider için  
 Aşağıdaki özellikleri ve yöntemleri IDockProvider arabirimi uygulamak için gereklidir.  
  
|Gerekli üyeleri|Üye türü|Notlar|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IDockProvider.DockPosition%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A>|Yöntem|Yok.|  
  
 Bu denetim düzeni ilişkili olay vardır.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Özel Durumlar  
 Sağlayıcıları aşağıdaki özel durumlar oluşturma gerekir.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A><br /><br /> -Ne zaman bir denetim istenen yerleştirme stilini yürütme mümkün değil.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UI Otomasyon denetim düzenlerine genel bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [UI Otomasyon sağlayıcısında denetim düzenleri desteği](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [İstemciler için UI Otomasyon denetim düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [UI Otomasyon ağacına genel bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [UI otomasyonda önbelleğe almayı kullanma](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
