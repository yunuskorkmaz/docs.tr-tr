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
ms.openlocfilehash: 94c4642221f88f4d41ee436ee6a46c830ea1811c
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47075443"
---
# <a name="implementing-the-ui-automation-grid-control-pattern"></a>UI Otomasyon Kılavuz Denetim Düzenini Uygulama
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu, yönergeleri ve uygulama kuralları tanıtır <xref:System.Windows.Automation.Provider.IGridProvider>, özellikler, yöntemler ve olaylar hakkında bilgiler dahil olmak üzere. Ek başvurular bağlantılar genel bakış sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.GridPattern> Denetim düzeni, alt öğelerinin koleksiyonu için kapsayıcı işlevi gören denetimleri desteklemek için kullanılır. Bu öğenin alt öğeleri uygulamalıdır <xref:System.Windows.Automation.Provider.IGridItemProvider> ve satır ve sütun tarafından çevrilebilen bir iki boyutlu mantıksal koordinat sisteminde düzenlenir. Bu denetim düzeni uygulama denetimleri örnekleri için bkz: [denetim düzeni eşlemesi için UI Otomasyonu istemcileri](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama yönergeleri ve kuralları  
 Kılavuz denetim düzeni uygularken aşağıdaki yönergeler ve kuralları dikkat edin:  
  
-   Sol üst (veya üst sağ hücresi yerel ayara bağlı olarak) (0, 0) koordinatlarına sahip kılavuz koordinatları sıfır tabanlıdır.  
  
-   Bir hücreyi boşsa, UI Otomasyon öğesi hala desteklemek için döndürülmelidir <xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A> hücre için özellik. Alt öğeleri kılavuzunda düzenini düzensiz bir diziye benzer olduğunda bu mümkündür (aşağıdaki örneğe bakın).  
  
 ![Windows Explorer görünümü gösteren düzensiz düzeni. ](../../../docs/framework/ui-automation/media/uia-gridpattern-ragged-array.PNG "UIA_GridPattern_Ragged_Array")  
Boş koordinatları ile bir kılavuz denetimi örneği  
  
-   Tek bir öğe içeren bir kılavuz uygulamak için hala gereklidir <xref:System.Windows.Automation.Provider.IGridProvider> , mantıksal olarak bir kılavuz olarak kabul edilir. Kurucularýn kılavuzunda alt öğe sayısı.  
  
-   Gizli satırları ve sütunları, sağlayıcı uygulaması bağlı olarak yüklenemeyen içinde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı ve bu nedenle yansıtılır <xref:System.Windows.Automation.GridPattern.GridPatternInformation.RowCount%2A> ve <xref:System.Windows.Automation.GridPattern.GridPatternInformation.ColumnCount%2A> özellikleri. Gizli satırları ve sütunları henüz yüklenmedi, bunlar sayılıp değil.  
  
-   <xref:System.Windows.Automation.Provider.IGridProvider> bir kılavuzun etkin işleme etkinleştirmez; <xref:System.Windows.Automation.Provider.ITransformProvider> bu işlevselliği etkinleştirmek için uygulanması gerekir.  
  
-   Kullanım bir <xref:System.Windows.Automation.StructureChangedEventHandler> kılavuzuna eklenmiş, kaldırılmış, birleştirilmiş veya hücre gibi yapısal veya düzen değişiklikleri dinlemek için.  
  
-   Kullanım bir <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> geçişi öğeleri veya hücre bir kılavuzun aracılığıyla izlemek için.  
  
<a name="Required_Members_for_IGridProvider"></a>   
## <a name="required-members-for-igridprovider"></a>Gerekli üyeleri IGridProvider için  
 Aşağıdaki özellikleri ve yöntemleri IGridProvider arabirim uygulamak için gereklidir.  
  
|Gerekli üyeleri|Tür|Notlar|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A>|Yöntem|Yok.|  
  
 Bu denetim düzeni, ilişkili olay vardır.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Özel Durumlar  
 Sağlayıcıları, aşağıdaki özel durumlar gerekir.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> -İstenen satır koordinat büyükse <xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A> veya sütun koordinat değerinden daha büyük <xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> -İstenen satır veya sütun koordinatları küçükse sıfır.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UI Otomasyonu Denetim Desenlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [İstemciler İçin UI Otomasyonu Denetim Düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [UI Otomasyonu GridItem Denetim Desenini Uygulama](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md)  
 [UI Otomasyon Ağacına Genel Bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [UI Otomasyonunda Önbelleğe Almayı Kullanma](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
