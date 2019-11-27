---
title: UI Otomasyon GridItem Denetim Düzeni Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
ms.openlocfilehash: 832a53e072afc5533f2eeb7feb0cc326771cf23d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435260"
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a>UI Otomasyon GridItem Denetim Düzeni Uygulama
> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, özellikler hakkında bilgiler de dahil olmak üzere <xref:System.Windows.Automation.Provider.IGridItemProvider>uygulamak için kılavuz ve kuralları tanıtır. Ek başvuruların bağlantıları genel bakış sonunda listelenir.  
  
 <xref:System.Windows.Automation.GridItemPattern> denetim stili, <xref:System.Windows.Automation.Provider.IGridProvider>uygulayan kapsayıcıların tek tek alt denetimlerini desteklemek için kullanılır. Bu denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama kılavuzları ve kuralları  
 <xref:System.Windows.Automation.Provider.IGridProvider>uygularken, aşağıdaki kılavuz ve kurallara göz önünde yer verilmiştir:  
  
- Izgara koordinatları, koordinatlara (0, 0) sahip üstteki sol hücreyle sıfır tabanlıdır.  
  
- Birleştirilmiş hücreler, <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> ve <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> özelliklerini, Kullanıcı Arabirimi Otomasyonu sağlayıcısı tarafından tanımlanan temel alınan bağlayıcı hücrelerine göre rapor eder. Genellikle, en üstteki ve en soldaki satır veya sütun olacaktır.  
  
- <xref:System.Windows.Automation.Provider.IGridItemProvider>, kılavuz için hücre birleştirme veya bölme gibi etkin düzenleme için sağlamaz.  
  
- <xref:System.Windows.Automation.Provider.IGridItemProvider> uygulayan denetimler genellikle, klavyeyi kullanarak (bir UI Otomasyon istemcisi bitişik denetimlere taşınabilir) geçebilir.  
  
<a name="Required_Members_for_IGridItemProvider"></a>   
## <a name="required-members-for-igriditemprovider"></a>IGridItemProvider için gerekli Üyeler  
 <xref:System.Windows.Automation.Provider.IGridItemProvider>uygulamak için aşağıdaki özellikler ve Yöntemler gereklidir.  
  
|Gerekli Üyeler|Üye türü|Notlar|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|Özellik|Yok.|  
  
 Bu denetim deseninin ilişkili yöntemleri veya olayları yok.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Özel Durumlar  
 Bu denetim deseninin ilişkili özel durumları yok.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Denetim Desenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyonu Grid Denetim Desenini Uygulama](implementing-the-ui-automation-grid-control-pattern.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
