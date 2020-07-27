---
title: UI Otomasyon GridItem Denetim Düzeni Uygulama
description: UI otomasyonunda kılavuz öğeleri için GridItemPattern denetim modelini uygulamaya yönelik kılavuzları ve kuralları öğrenin. IGridItemProvider için gereken üyelere bakın.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
ms.openlocfilehash: e0a0c616f3f0cf9bc091e4fbb496d71ab8550bd3
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165828"
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a>UI Otomasyon GridItem Denetim Düzeni Uygulama
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu <xref:System.Windows.Automation.Provider.IGridItemProvider> , özellikler hakkında bilgiler de dahil olmak üzere uygulama yönergelerini ve kurallarını tanıtır. Ek başvuruların bağlantıları genel bakış sonunda listelenir.  
  
 <xref:System.Windows.Automation.GridItemPattern>Denetim stili, uygulayan kapsayıcıların tek tek alt denetimlerini desteklemek için kullanılır <xref:System.Windows.Automation.Provider.IGridProvider> . Bu denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Uygulama kılavuzları ve kuralları  
 Uygulama sırasında <xref:System.Windows.Automation.Provider.IGridProvider> , aşağıdaki kılavuz ve kurallara göz önünde yer verilmiştir:  
  
- Izgara koordinatları, koordinatlara (0, 0) sahip üstteki sol hücreyle sıfır tabanlıdır.  
  
- Birleştirilmiş hücreler, <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> Kullanıcı Arabirimi Otomasyonu sağlayıcısı tarafından tanımlanan temel alınan bağlantı hücrelerine göre ve özelliklerini raporlar. Genellikle, en üstteki ve en soldaki satır veya sütun olacaktır.  
  
- <xref:System.Windows.Automation.Provider.IGridItemProvider>, hücreleri birleştirme veya bölme gibi, kılavuzun etkin olarak düzenlenmesini sağlamaz.  
  
- Uygulayan denetimler <xref:System.Windows.Automation.Provider.IGridItemProvider> genellikle, klavyeyi kullanarak (bır UI Otomasyon istemcisi bitişik denetimlere taşınabilir) geçebilir.  
  
<a name="Required_Members_for_IGridItemProvider"></a>
## <a name="required-members-for-igriditemprovider"></a>IGridItemProvider için gerekli Üyeler  
 Uygulamak için aşağıdaki özellikler ve Yöntemler gereklidir <xref:System.Windows.Automation.Provider.IGridItemProvider> .  
  
|Gerekli Üyeler|Üye türü|Notlar|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|Özellik|Hiçbiri|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|Özellik|Hiçbiri|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|Özellik|Hiçbiri|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|Özellik|Hiçbiri|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|Özellik|Hiçbiri|  
  
 Bu denetim deseninin ilişkili yöntemleri veya olayları yok.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Özel durumlar  
 Bu denetim deseninin ilişkili özel durumları yok.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyon Denetim Düzenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyon Sağlayıcısında Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyon Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyon Kılavuz Denetim Düzenini Uygulama](implementing-the-ui-automation-grid-control-pattern.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
