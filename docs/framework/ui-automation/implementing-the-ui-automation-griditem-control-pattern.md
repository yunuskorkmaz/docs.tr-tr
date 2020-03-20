---
title: UI Otomasyon GridItem Denetim Düzeni Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
ms.openlocfilehash: d561587e6bb98ba857b27ba89b4c1a45ba964ffd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180197"
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a>UI Otomasyon GridItem Denetim Düzeni Uygulama
> [!NOTE]
> Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır. Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu <xref:System.Windows.Automation.Provider.IGridItemProvider>konu, özellikler hakkında bilgi de dahil olmak üzere uygulama yönergeleri ve kuralları sunar. Ek başvurulara bağlantılar genel bakışın sonunda listelenir.  
  
 Denetim <xref:System.Windows.Automation.GridItemPattern> deseni, uygulayan <xref:System.Windows.Automation.Provider.IGridProvider>kapsayıcıların tek tek alt denetimlerini desteklemek için kullanılır. Bu denetim deseni uygulayan denetim örnekleri için, [UI Otomasyon Istemcileri için Denetim Deseni Eşleciliği'ne](control-pattern-mapping-for-ui-automation-clients.md)bakın.  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Uygulama Yönergeleri ve Sözleşmeleri  
 Uygularken <xref:System.Windows.Automation.Provider.IGridProvider>aşağıdaki yönergeleri ve kuralları unutmayın:  
  
- Izgara koordinatları, sol üst hücrenin koordinatları (0, 0) olan sıfır tabanlıdır.  
  
- Birleştirilmiş hücreler, <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> UI Automation sağlayıcısı tarafından tanımlandığı şekilde temel bağlantı hücrelerine göre kendi özelliklerini ve <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> özelliklerini bildirir. Genellikle, en üstteki ve en soldaki satır veya sütun olur.  
  
- <xref:System.Windows.Automation.Provider.IGridItemProvider>hücrelerin birleştirilmesi veya bölünmesi gibi ızgaranın etkin bir şekilde manipüle sini sağlamaz.  
  
- Uygulayan <xref:System.Windows.Automation.Provider.IGridItemProvider> denetimler genellikle klavyeyi kullanarak geçiş yapılabilir (diğer bir şekilde, bir UI Automation istemcisi bitişik denetimlere geçebilir).  
  
<a name="Required_Members_for_IGridItemProvider"></a>
## <a name="required-members-for-igriditemprovider"></a>IGridItemProvider için Gerekli Üyeler  
 Uygulamak için aşağıdaki özellikler ve <xref:System.Windows.Automation.Provider.IGridItemProvider>yöntemler gereklidir.  
  
|Gerekli üyeler|Üye tipi|Notlar|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|Özellik|None|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|Özellik|None|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|Özellik|None|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|Özellik|None|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|Özellik|None|  
  
 Bu denetim deseni ilişkili yöntem veya olay vardır.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Özel durumlar  
 Bu denetim deseni ilişkili özel durumlar vardır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Denetim Desenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyonu Grid Denetim Desenini Uygulama](implementing-the-ui-automation-grid-control-pattern.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
