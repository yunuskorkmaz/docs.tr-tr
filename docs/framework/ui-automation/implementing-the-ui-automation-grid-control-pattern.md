---
title: UI Otomasyon Kılavuz Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, grid
- grid control pattern
- UI Automation, grid control pattern
ms.assetid: 234d11a0-7ce7-4309-8989-2f4720e02f78
ms.openlocfilehash: f4b5f1763b655026b20f37605d4649606af7fea6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435366"
---
# <a name="implementing-the-ui-automation-grid-control-pattern"></a>UI Otomasyon Kılavuz Denetim Düzenini Uygulama
> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konuda özellikler, Yöntemler ve olaylar hakkında bilgiler de dahil olmak üzere <xref:System.Windows.Automation.Provider.IGridProvider>uygulamak için yönergeler ve kurallar tanıtılmaktadır. Ek başvuruların bağlantıları genel bakış sonunda listelenir.  
  
 <xref:System.Windows.Automation.GridPattern> denetim deseninin bir alt öğe koleksiyonu için kapsayıcılar olarak davranan denetimleri desteklemek için kullanılır. Bu öğenin alt öğeleri <xref:System.Windows.Automation.Provider.IGridItemProvider> uygulamalıdır ve satır ve sütun tarafından çapraz bir şekilde iki boyutlu bir mantıksal koordinat sisteminde düzenlenmelidir. Bu denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama kılavuzları ve kuralları  
 Kılavuz denetim modelini uygularken aşağıdaki kılavuz ve kurallara göz önünde yer verilmiştir:  
  
- Izgara koordinatları, koordinatlara sahip (0, 0) sol üst (veya yerel ayara bağlı olarak sağ üst hücre) ile sıfır tabanlıdır.  
  
- Bir hücre boşsa, bu hücrenin <xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A> özelliğini desteklemek için UI Otomasyon öğesi yine de döndürülmelidir. Kılavuzdaki alt öğelerin düzeni düzensiz bir diziye benzediğinde bu mümkündür (aşağıdaki örneğe bakın).  
  
 ![Düzensiz düzeni gösteren Windows Gezgini görünümü.](./media/uia-gridpattern-ragged-array.PNG "UIA_GridPattern_Ragged_Array")  
Boş koordinatları olan Grid denetimine örnek  
  
- Tek bir öğe içeren bir ızgara, mantıksal olarak bir kılavuz olarak kabul edildiğinde <xref:System.Windows.Automation.Provider.IGridProvider> uygulamak için de gereklidir. Kılavuzdaki alt öğe öğelerinin sayısı immalzemedir.  
  
- Sağlayıcı uygulamasına bağlı olarak gizli satırlar ve sütunlar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacına yüklenebilir ve bu nedenle <xref:System.Windows.Automation.GridPattern.GridPatternInformation.RowCount%2A> ve <xref:System.Windows.Automation.GridPattern.GridPatternInformation.ColumnCount%2A> özelliklerine yansıtılacaktır. Gizli satırlar ve sütunlar henüz yüklenmediyse, bunlar sayılmaz.  
  
- <xref:System.Windows.Automation.Provider.IGridProvider>, bir kılavuzun etkin işlemesini etkinleştirmez; Bu işlevi etkinleştirmek için <xref:System.Windows.Automation.Provider.ITransformProvider> uygulanması gerekir.  
  
- Eklenmiş, kaldırılmış veya birleştirilmiş hücreler gibi kılavuzda yapısal veya Düzen değişikliklerinin dinlemek için bir <xref:System.Windows.Automation.StructureChangedEventHandler> kullanın.  
  
- Bir kılavuzun öğeleri veya hücreleri aracılığıyla çapraz geçişi izlemek için <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> kullanın.  
  
<a name="Required_Members_for_IGridProvider"></a>   
## <a name="required-members-for-igridprovider"></a>Igrprovider için gerekli Üyeler  
 Aşağıdaki özellikler ve Yöntemler ıgrprovider arabirimini uygulamak için gereklidir.  
  
|Gerekli Üyeler|Type|Notlar|  
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
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> -İstenen satır koordinatı <xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A> büyükse veya sütun koordinatı <xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>daha büyük.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> -İstenen satır veya sütun koordinatlarından herhangi biri sıfırdan küçükse.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Denetim Desenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyonu GridItem Denetim Desenini Uygulama](implementing-the-ui-automation-griditem-control-pattern.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
