---
title: UI Otomasyonu Tablo Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Table control pattern
- control patterns, Table
- TableControl pattern
ms.assetid: 880cd85c-aa8c-4fb5-9369-45491d34bb78
ms.openlocfilehash: 0852e904414ac4af6777b9476b4b6ad504a09ef3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935703"
---
# <a name="implementing-the-ui-automation-table-control-pattern"></a>UI Otomasyonu Tablo Denetim Düzenini Uygulama
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konuda özellikler, Yöntemler ve olaylar hakkında <xref:System.Windows.Automation.Provider.ITableProvider>bilgiler de dahil olmak üzere uygulama yönergeleri ve kuralları tanıtılmaktadır. Ek başvuruların bağlantıları genel bakış sonunda listelenir.  
  
 <xref:System.Windows.Automation.TablePattern> Denetim stili, alt öğelerin bir koleksiyonu için kapsayıcılar olarak davranan denetimleri desteklemek için kullanılır. Bu öğenin alt öğeleri, satır ve <xref:System.Windows.Automation.Provider.ITableItemProvider> sütun tarafından geçilen iki boyutlu bir mantıksal koordinat sisteminde uygulamanız ve düzenlenmelidir. Bu denetim deseninin <xref:System.Windows.Automation.Provider.IGridProvider>, her bir alt öğe için aynı zamanda bir sütun ve <xref:System.Windows.Automation.Provider.ITableProvider> /veya satır üst bilgisi ilişkisi olması gereken ayrım ile benzerdir. Bu denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama kılavuzları ve kuralları  
 Tablo denetim modelini uygularken aşağıdaki kılavuz ve kurallara göz önünde yer verilmiştir:  
  
- Tek tek hücrelerin içeriğine erişim, iki boyutlu bir mantıksal koordinat sistemi veya ' nin <xref:System.Windows.Automation.Provider.IGridProvider>gerekli eşzamanlı uygulamasıyla belirtilen dizisidir.  
  
- Bir sütun veya satır üst bilgisi, tablo nesnesi içinde veya tablo nesnesiyle ilişkili ayrı bir üst bilgi nesnesi olabilir.  
  
- Sütun ve satır başlıkları hem birincil üstbilgiyi hem de tüm destekleyici üst bilgileri içerebilir.  
  
> [!NOTE]
> Bu kavram, kullanıcının bir "ilk [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] ad" sütunu tanımladığı bir elektronik tabloda görünür hale gelir. Bu sütunda artık iki üst bilgi vardır: Kullanıcı tarafından tanımlanan "Ilk ad" üstbilgisi ve uygulama tarafından atanan sütun için alfasayısal atama.  
  
- İlgili kılavuz işlevselliği için [UI Otomasyonu kılavuz denetim modelini uygulama](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md) bölümüne bakın.  
  
 ![Karmaşık üstbilgi öğeleri Içeren tablo.](../../../docs/framework/ui-automation/media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")  
Karmaşık sütun başlıkları içeren bir tablo örneği  
  
 ![Belirsiz Roworcolumnana özelliği olan tablo.](../../../docs/framework/ui-automation/media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")  
Belirsiz Roworcolumnana özelliği olan bir tablo örneği  
  
<a name="Required_Members_for_ITableProvider"></a>   
## <a name="required-members-for-itableprovider"></a>ITableProvider için gerekli Üyeler  
 ITableProvider arabirimi için aşağıdaki özellikler ve Yöntemler gereklidir.  
  
|Gerekli Üyeler|Üye türü|Notlar|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableProvider.RowOrColumnMajor%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetColumnHeaders%2A>|Yöntem|Yok.|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetRowHeaders%2A>|Yöntem|Yok.|  
  
 Bu denetim deseninin ilişkili olayları yok.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Özel Durumlar  
 Bu denetim deseninin ilişkili özel durumları yok.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Denetim Desenlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [UI Otomasyonu TableItem Denetim Desenini Uygulama](../../../docs/framework/ui-automation/implementing-the-ui-automation-tableitem-control-pattern.md)
- [UI Otomasyonu Grid Denetim Desenini Uygulama](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md)
- [UI Otomasyon Ağacına Genel Bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
