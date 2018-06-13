---
title: UI Otomasyon Kılavuz Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, grid
- grid control pattern
- UI Automation, grid control pattern
ms.assetid: 234d11a0-7ce7-4309-8989-2f4720e02f78
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 0038202fb7c7f1a6e0b4f21592d7a1056c4dfa2b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33410000"
---
# <a name="implementing-the-ui-automation-grid-control-pattern"></a>UI Otomasyon Kılavuz Denetim Düzenini Uygulama
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu kılavuzları ve uygulamak için kuralları tanıtır <xref:System.Windows.Automation.Provider.IGridProvider>, özellikleri, yöntemleri ve etkinlikleri hakkında bilgiler dahil olmak üzere. Ek başvurular bağlantılar genel bakış sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.GridPattern> Denetim düzeni alt öğe koleksiyonunu için kapsayıcı olarak hareket denetimleri desteklemek için kullanılır. Bu öğenin alt öğeleri uygulamalıdır <xref:System.Windows.Automation.Provider.IGridItemProvider> ve satır ve sütun tarafından geçiş bir iki boyutlu mantıksal koordinat sistemi düzenlenir. Bu denetim düzeni uygulama denetimleri örnekleri için bkz: [denetim düzeni eşleştirmesi UI Otomasyon istemcileri için](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama rehberi ve kuralları  
 Kılavuz denetim düzenini uygulama, aşağıdaki yönergeleri ve kuralları dikkat edin:  
  
-   Kılavuz koordinatları, sol üst (veya üst sağ hücre yerel ayara bağlı olarak) koordinatları (0, 0) sahip sıfır tabanlı.  
  
-   Bir hücre boşsa, UI Otomasyon öğesi hala desteklemek için döndürülmelidir <xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A> hücre için özellik. Alt öğeler kılavuzunda düzenini düzensiz bir diziye benzer olduğunda bu mümkündür (aşağıdaki örneğe bakın).  
  
 ![Windows Gezgini Dağınık düzeni gösteren görüntüleyin. ] (../../../docs/framework/ui-automation/media/uia-gridpattern-ragged-array.PNG "UIA_GridPattern_Ragged_Array")  
Kılavuz Denetim boş koordinatları ile örneği  
  
-   Tek bir öğe içeren bir kılavuz uygulamak için hala gereklidir <xref:System.Windows.Automation.Provider.IGridProvider> , mantıksal bir kılavuz olarak değerlendirilir. Alt öğeler kılavuzunda kurucularýn sayısıdır.  
  
-   Gizli satırları ve sütunları sağlayıcıyı uygulama bağlı yüklenmesi de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı ve bu nedenle yansıtılır <xref:System.Windows.Automation.GridPattern.GridPatternInformation.RowCount%2A> ve <xref:System.Windows.Automation.GridPattern.GridPatternInformation.ColumnCount%2A> özellikleri. Gizli satırları ve sütunları henüz yüklenmedi, bunlar alınmalıdır değil.  
  
-   <xref:System.Windows.Automation.Provider.IGridProvider> etkin bir kılavuz işlenmesini etkinleştirmez; <xref:System.Windows.Automation.Provider.ITransformProvider> bu işlevselliği etkinleştirmek için uygulanması gerekir.  
  
-   Kullanım bir <xref:System.Windows.Automation.StructureChangedEventHandler> kılavuz eklenmiş, kaldırılmış, birleştirilmiş veya hücreleri gibi yapısal veya düzen değişiklikleri dinlemek için.  
  
-   Kullanım bir <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> öğeler veya kılavuz hücrelerini aracılığıyla geçişi izlemek için.  
  
<a name="Required_Members_for_IGridProvider"></a>   
## <a name="required-members-for-igridprovider"></a>Gerekli üyeleri IGridProvider için  
 Aşağıdaki özellikleri ve yöntemleri IGridProvider arabirimi uygulamak için gereklidir.  
  
|Gerekli üyeleri|Tür|Notlar|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A>|Yöntem|Yok.|  
  
 Bu denetim düzeni ilişkili olay vardır.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Özel Durumlar  
 Sağlayıcıları aşağıdaki özel durumlar oluşturma gerekir.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> -İstenen satır koordinat büyükse <xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A> veya sütun koordinat büyük <xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> -İstenen satır veya sütun koordinatları küçükse sıfır.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UI Otomasyonu Denetim Desenlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [İstemciler İçin UI Otomasyonu Denetim Düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [UI Otomasyonu GridItem Denetim Desenini Uygulama](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md)  
 [UI Otomasyon Ağacına Genel Bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [UI Otomasyonunda Önbelleğe Almayı Kullanma](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
