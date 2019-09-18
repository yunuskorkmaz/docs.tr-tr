---
title: UI Otomasyon TableItem Denetim Düzeni Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Table Item
- UI Automation, Table Item control pattern
- TableItem control pattern
ms.assetid: ac178408-1485-436f-8d3e-eee3bf80cb24
ms.openlocfilehash: cdbfc8d24dce3b63801682528a49c13d89660935
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043170"
---
# <a name="implementing-the-ui-automation-tableitem-control-pattern"></a>UI Otomasyon TableItem Denetim Düzeni Uygulama
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu, olaylar ve özellikler hakkında bilgiler <xref:System.Windows.Automation.Provider.ITableItemProvider>de dahil olmak üzere uygulama yönergelerini ve kurallarını tanıtır. Ek başvuruların bağlantıları genel bakış sonunda listelenir.  
  
 Denetim stili, uygulayan <xref:System.Windows.Automation.Provider.ITableProvider>kapsayıcıların alt denetimlerini desteklemek için kullanılır. <xref:System.Windows.Automation.TableItemPattern> Bağımsız hücre işlevselliğine erişim, için gerekli olan <xref:System.Windows.Automation.Provider.IGridItemProvider>eşzamanlı uygulamayla sağlanır. Bu denetim deseninin, uygulayan <xref:System.Windows.Automation.Provider.IGridItemProvider> <xref:System.Windows.Automation.Provider.ITableItemProvider> herhangi bir denetimin, tek bir hücre ve onun satırı ve sütun bilgileri arasındaki ilişkiyi programlı bir şekilde kullanıma sunmasının gereken ayrım ile benzerdir. Bu denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama kılavuzları ve kuralları  
  
- İlgili ızgara öğesi işlevselliği için bkz. [UI Otomasyonu GridItem denetim modelini uygulama](implementing-the-ui-automation-griditem-control-pattern.md).  
  
<a name="Required_Members_for_ITableItemProvider"></a>   
## <a name="required-members-for-itableitemprovider"></a>ITableItemProvider için gerekli Üyeler  
  
|Gerekli üye|Üye türü|Notlar|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetColumnHeaderItems%2A>|Yöntem|Yok.|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetRowHeaderItems%2A>|Yöntem|Yok.|  
  
 Bu denetim deseninin ilişkili özellikleri veya olayları yok.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Özel Durumlar  
 Bu denetim deseninin ilişkili özel durumları yok.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Denetim Desenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyonu Table Denetim Desenini Uygulama](implementing-the-ui-automation-table-control-pattern.md)
- [UI Otomasyonu GridItem Denetim Desenini Uygulama](implementing-the-ui-automation-griditem-control-pattern.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
