---
title: UI Otomasyon TableItem Denetim Düzeni Uygulama
description: UI Otomasyonu 'nda TableItem denetim modelini uygulamak için yönergeleri ve kuralları gözden geçirin. ITableItemProvider arabirimi için gerekli üyeleri öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Table Item
- UI Automation, Table Item control pattern
- TableItem control pattern
ms.assetid: ac178408-1485-436f-8d3e-eee3bf80cb24
ms.openlocfilehash: 3d6d31fe0e041fbba147df14d290a775188755f2
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163518"
---
# <a name="implementing-the-ui-automation-tableitem-control-pattern"></a>UI Otomasyon TableItem Denetim Düzeni Uygulama
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu <xref:System.Windows.Automation.Provider.ITableItemProvider> , olaylar ve özellikler hakkında bilgiler de dahil olmak üzere uygulama yönergelerini ve kurallarını tanıtır. Ek başvuruların bağlantıları genel bakış sonunda listelenir.  
  
 <xref:System.Windows.Automation.TableItemPattern>Denetim stili, uygulayan kapsayıcıların alt denetimlerini desteklemek için kullanılır <xref:System.Windows.Automation.Provider.ITableProvider> . Bağımsız hücre işlevselliğine erişim, için gerekli olan eşzamanlı uygulamayla sağlanır <xref:System.Windows.Automation.Provider.IGridItemProvider> . Bu denetim deseninin, <xref:System.Windows.Automation.Provider.IGridItemProvider> uygulayan herhangi bir denetimin, tek bir hücre ve <xref:System.Windows.Automation.Provider.ITableItemProvider> onun satırı ve sütun bilgileri arasındaki ilişkiyi programlı bir şekilde kullanıma sunmasının gereken ayrım ile benzerdir. Bu denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Uygulama kılavuzları ve kuralları  
  
- İlgili ızgara öğesi işlevselliği için bkz. [UI Otomasyonu GridItem denetim modelini uygulama](implementing-the-ui-automation-griditem-control-pattern.md).  
  
<a name="Required_Members_for_ITableItemProvider"></a>
## <a name="required-members-for-itableitemprovider"></a>ITableItemProvider için gerekli Üyeler  
  
|Gerekli üye|Üye türü|Notlar|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetColumnHeaderItems%2A>|Yöntem|Hiçbiri|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetRowHeaderItems%2A>|Yöntem|Hiçbiri|  
  
 Bu denetim deseninin ilişkili özellikleri veya olayları yok.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Özel durumlar  
 Bu denetim deseninin ilişkili özel durumları yok.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyon Denetim Düzenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyon Sağlayıcısında Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyon Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyonu Tablo Denetim Düzenini Uygulama](implementing-the-ui-automation-table-control-pattern.md)
- [UI Otomasyon GridItem Denetim Düzeni Uygulama](implementing-the-ui-automation-griditem-control-pattern.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
