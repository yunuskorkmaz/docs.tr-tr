---
title: UI Otomasyon Kılavuz Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, grid
- grid control pattern
- UI Automation, grid control pattern
ms.assetid: 234d11a0-7ce7-4309-8989-2f4720e02f78
ms.openlocfilehash: 5eceafee4d02478c9e011a473ee1d036df91075d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932173"
---
# <a name="implementing-the-ui-automation-grid-control-pattern"></a>UI Otomasyon Kılavuz Denetim Düzenini Uygulama
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konuda özellikler, Yöntemler ve olaylar hakkında <xref:System.Windows.Automation.Provider.IGridProvider>bilgiler de dahil olmak üzere uygulama yönergeleri ve kuralları tanıtılmaktadır. Ek başvuruların bağlantıları genel bakış sonunda listelenir.  
  
 <xref:System.Windows.Automation.GridPattern> Denetim stili, alt öğelerin bir koleksiyonu için kapsayıcılar olarak davranan denetimleri desteklemek için kullanılır. Bu öğenin alt öğeleri, satır ve <xref:System.Windows.Automation.Provider.IGridItemProvider> sütun tarafından geçilen iki boyutlu bir mantıksal koordinat sisteminde uygulamanız ve düzenlenmelidir. Bu denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama kılavuzları ve kuralları  
 Kılavuz denetim modelini uygularken aşağıdaki kılavuz ve kurallara göz önünde yer verilmiştir:  
  
- Izgara koordinatları, koordinatlara sahip (0, 0) sol üst (veya yerel ayara bağlı olarak sağ üst hücre) ile sıfır tabanlıdır.  
  
- Bir hücre boşsa, bu hücrenin <xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A> özelliğini desteklemek için bir UI Otomasyon öğesi döndürülmeye devam etmelidir. Kılavuzdaki alt öğelerin düzeni düzensiz bir diziye benzediğinde bu mümkündür (aşağıdaki örneğe bakın).  
  
 ![Düzensiz düzeni gösteren Windows Gezgini görünümü.](../../../docs/framework/ui-automation/media/uia-gridpattern-ragged-array.PNG "UIA_GridPattern_Ragged_Array")  
Boş koordinatları olan Grid denetimine örnek  
  
- Tek bir öğe içeren bir ızgara, mantıksal olarak bir kılavuz <xref:System.Windows.Automation.Provider.IGridProvider> olarak kabul edildiğinde uygulanması gerekir. Kılavuzdaki alt öğe öğelerinin sayısı immalzemedir.  
  
- Sağlayıcı uygulamasına bağlı olarak gizli satırlar ve sütunlar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaca yüklenebilir ve bu nedenle, <xref:System.Windows.Automation.GridPattern.GridPatternInformation.RowCount%2A> ve <xref:System.Windows.Automation.GridPattern.GridPatternInformation.ColumnCount%2A> özelliklerine yansıtılacaktır. Gizli satırlar ve sütunlar henüz yüklenmediyse, bunlar sayılmaz.  
  
- <xref:System.Windows.Automation.Provider.IGridProvider>bir kılavuzun etkin işlemesini etkinleştirmez; <xref:System.Windows.Automation.Provider.ITransformProvider> bu işlevi etkinleştirmek için uygulanması gerekir.  
  
- Eklenmiş, <xref:System.Windows.Automation.StructureChangedEventHandler> kaldırılmış veya birleştirilmiş hücreler gibi kılavuzda yapısal veya Düzen değişikliklerini dinlemek için bir kullanın.  
  
- Bir <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> kılavuzun öğeleri veya hücreleri aracılığıyla çapraz geçişi izlemek için kullanın.  
  
<a name="Required_Members_for_IGridProvider"></a>   
## <a name="required-members-for-igridprovider"></a>Igrprovider için gerekli Üyeler  
 Aşağıdaki özellikler ve Yöntemler ıgrprovider arabirimini uygulamak için gereklidir.  
  
|Gerekli Üyeler|Tür|Notlar|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A>|Yöntem|Yok.|  
  
 Bu denetim deseninin ilişkili olayları yok.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Özel Durumlar  
 Sağlayıcılar aşağıdaki özel durumları oluşturması gerekir.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> -İstenen satır koordinatı öğesinden <xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A> daha büyükse veya sütun koordinatı <xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>öğesinden daha büyükse.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> -İstenen satır veya sütun koordinatlarından herhangi biri sıfırdan küçükse.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Denetim Desenlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [UI Otomasyonu GridItem Denetim Desenini Uygulama](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md)
- [UI Otomasyon Ağacına Genel Bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
