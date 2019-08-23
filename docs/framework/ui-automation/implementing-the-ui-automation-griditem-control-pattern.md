---
title: UI Otomasyon GridItem Denetim Düzeni Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
ms.openlocfilehash: 1fa0de86ee59a48d0d64156b41ad2db794dff761
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968880"
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a>UI Otomasyon GridItem Denetim Düzeni Uygulama
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu, özellikler hakkında bilgiler de dahil <xref:System.Windows.Automation.Provider.IGridItemProvider>olmak üzere uygulama yönergelerini ve kurallarını tanıtır. Ek başvuruların bağlantıları genel bakış sonunda listelenir.  
  
 Denetim stili, uygulayan <xref:System.Windows.Automation.Provider.IGridProvider>kapsayıcıların tek tek alt denetimlerini desteklemek için kullanılır. <xref:System.Windows.Automation.GridItemPattern> Bu denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama kılavuzları ve kuralları  
 Uygulama <xref:System.Windows.Automation.Provider.IGridProvider>sırasında, aşağıdaki kılavuz ve kurallara göz önünde yer verilmiştir:  
  
- Izgara koordinatları, koordinatlara (0, 0) sahip üstteki sol hücreyle sıfır tabanlıdır.  
  
- Birleştirilmiş hücreler, Kullanıcı arabirimi <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> Otomasyonu <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> sağlayıcısı tarafından tanımlanan temel alınan bağlantı hücrelerine göre ve özelliklerini raporlar. Genellikle, en üstteki ve en soldaki satır veya sütun olacaktır.  
  
- <xref:System.Windows.Automation.Provider.IGridItemProvider>, hücreleri birleştirme veya bölme gibi, kılavuzun etkin olarak düzenlenmesini sağlamaz.  
  
- Uygulayan <xref:System.Windows.Automation.Provider.IGridItemProvider> denetimler genellikle, klavyeyi kullanarak (bir UI Otomasyon istemcisi bitişik denetimlere taşınabilir) geçebilir.  
  
<a name="Required_Members_for_IGridItemProvider"></a>   
## <a name="required-members-for-igriditemprovider"></a>IGridItemProvider için gerekli Üyeler  
 Uygulamak <xref:System.Windows.Automation.Provider.IGridItemProvider>için aşağıdaki özellikler ve Yöntemler gereklidir.  
  
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

- [UI Otomasyonu Denetim Desenlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [UI Otomasyonu Grid Denetim Desenini Uygulama](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md)
- [UI Otomasyon Ağacına Genel Bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
