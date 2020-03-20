---
title: UI Otomasyon Kılavuz Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, grid
- grid control pattern
- UI Automation, grid control pattern
ms.assetid: 234d11a0-7ce7-4309-8989-2f4720e02f78
ms.openlocfilehash: 04f3ee1e01054df6a13ab2391e14a6a7f7274bb9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180222"
---
# <a name="implementing-the-ui-automation-grid-control-pattern"></a>UI Otomasyon Kılavuz Denetim Düzenini Uygulama
> [!NOTE]
> Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır. Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, özellikler, yöntemler ve <xref:System.Windows.Automation.Provider.IGridProvider>olaylar hakkında bilgiler de dahil olmak üzere uygulama yönergeleri ve kuralları sunar. Ek başvurulara bağlantılar genel bakışın sonunda listelenir.  
  
 Denetim <xref:System.Windows.Automation.GridPattern> deseni, alt öğelerin toplanması için kapsayıcı görevi yapan denetimleri desteklemek için kullanılır. Bu öğenin alt <xref:System.Windows.Automation.Provider.IGridItemProvider> uygulamak ve satır ve sütun tarafından geçilebilir iki boyutlu bir mantıksal koordinat sistemi içinde organize edilmelidir. Bu denetim deseni uygulayan denetim örnekleri için, [UI Otomasyon Istemcileri için Denetim Deseni Eşleciliği'ne](control-pattern-mapping-for-ui-automation-clients.md)bakın.  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Uygulama Yönergeleri ve Sözleşmeleri  
 Izgara denetim deseni uygulanırken, aşağıdaki yönergeleri ve kuralları not edin:  
  
- Izgara koordinatları, koordinatları (0, 0) olan sol üst (veya yerel bağlı olarak sağ üst hücre) ile sıfır tabanlıdır.  
  
- Bir hücre boşsa, o hücrenin özelliğini <xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A> desteklemek için yine de bir UI Otomasyon öğesi döndürülmelidir. Bu, ızgaradaki alt öğelerin düzeni düzensiz bir diziye benzerolduğunda mümkündür (aşağıdaki örneğe bakın).  
  
 ![Düzensiz düzeni gösteren Windows Gezgini görünümü.](./media/uia-gridpattern-ragged-array.PNG "UIA_GridPattern_Ragged_Array")  
Boş Koordinatları Olan Izgara Denetimi Örneği  
  
- Mantıksal olarak ızgara olarak kabul edilirse, tek bir öğeye sahip bir ızgaranın uygulanması <xref:System.Windows.Automation.Provider.IGridProvider> yine de gereklidir. Kılavuzdaki alt öğelerin sayısı önemsizdir.  
  
- Sağlayıcı nın uygulanmasına bağlı olarak gizli satır lar ve [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sütunlar ağaca yüklenebilir <xref:System.Windows.Automation.GridPattern.GridPatternInformation.RowCount%2A> ve <xref:System.Windows.Automation.GridPattern.GridPatternInformation.ColumnCount%2A> bu nedenle ve özellikleri yansıtılır. Gizli satırlar ve sütunlar henüz yüklenmediyse, bunlar sayılmamalıdır.  
  
- <xref:System.Windows.Automation.Provider.IGridProvider>bir ızgaranın etkin manipülasyonuna olanak sağlamaz; <xref:System.Windows.Automation.Provider.ITransformProvider> bu işlevselliği etkinleştirmek için uygulanmalıdır.  
  
- Ağarırda eklenen, kaldırılan veya birleştirilmiş hücreler gibi yapısal veya düzen değişikliklerini dinlemek için a <xref:System.Windows.Automation.StructureChangedEventHandler> kullanın.  
  
- Bir <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> ızgaranın öğeleri veya hücreleri arasında geçişi izlemek için a'yı kullanın.  
  
<a name="Required_Members_for_IGridProvider"></a>
## <a name="required-members-for-igridprovider"></a>IGridProvider için Gerekli Üyeler  
 IGridProvider arabiriminin uygulanması için aşağıdaki özellikler ve yöntemler gereklidir.  
  
|Gerekli üyeler|Tür|Notlar|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A>|Özellik|None|  
|<xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>|Özellik|None|  
|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A>|Yöntem|None|  
  
 Bu denetim deseni ilişkili olaylar vardır.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Özel durumlar  
 Sağlayıcılar aşağıdaki özel durumları atmalıdır.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> - İstenen satır koordinatı daha <xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A> büyükse veya sütun <xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>koordinatı .|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> - İstenen satır veya sütun koordinatlarından biri sıfırdan az ise.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Denetim Desenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyonu GridItem Denetim Desenini Uygulama](implementing-the-ui-automation-griditem-control-pattern.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
