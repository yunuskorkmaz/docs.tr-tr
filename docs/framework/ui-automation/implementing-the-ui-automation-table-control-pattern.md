---
title: UI Otomasyonu Tablo Denetim Düzenini Uygulama
description: UI Otomasyonu 'nda tablo Denetim modelini uygulamak için yönergeleri ve kuralları gözden geçirin. ITableProvider arabirimi için gerekli üyeleri öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Table control pattern
- control patterns, Table
- TableControl pattern
ms.assetid: 880cd85c-aa8c-4fb5-9369-45491d34bb78
ms.openlocfilehash: e88ddee04ba887daf1929d855526cd0d062f78d5
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168245"
---
# <a name="implementing-the-ui-automation-table-control-pattern"></a>UI Otomasyonu Tablo Denetim Düzenini Uygulama
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konuda <xref:System.Windows.Automation.Provider.ITableProvider> Özellikler, Yöntemler ve olaylar hakkında bilgiler de dahil olmak üzere uygulama yönergeleri ve kuralları tanıtılmaktadır. Ek başvuruların bağlantıları genel bakış sonunda listelenir.  
  
 <xref:System.Windows.Automation.TablePattern>Denetim stili, alt öğelerin bir koleksiyonu için kapsayıcılar olarak davranan denetimleri desteklemek için kullanılır. Bu öğenin alt öğeleri, <xref:System.Windows.Automation.Provider.ITableItemProvider> satır ve sütun tarafından geçilen iki boyutlu bir mantıksal koordinat sisteminde uygulamanız ve düzenlenmelidir. Bu denetim deseninin <xref:System.Windows.Automation.Provider.IGridProvider> , <xref:System.Windows.Automation.Provider.ITableProvider> her bir alt öğe için aynı zamanda bir sütun ve/veya satır üst bilgisi ilişkisi olması gereken ayrım ile benzerdir. Bu denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Uygulama kılavuzları ve kuralları  
 Tablo denetim modelini uygularken aşağıdaki kılavuz ve kurallara göz önünde yer verilmiştir:  
  
- Tek tek hücrelerin içeriğine erişim, iki boyutlu bir mantıksal koordinat sistemi veya ' nin gerekli eşzamanlı uygulamasıyla belirtilen dizisidir <xref:System.Windows.Automation.Provider.IGridProvider> .  
  
- Bir sütun veya satır üst bilgisi, tablo nesnesi içinde veya tablo nesnesiyle ilişkili ayrı bir üst bilgi nesnesi olabilir.  
  
- Sütun ve satır başlıkları hem birincil üstbilgiyi hem de tüm destekleyici üst bilgileri içerebilir.  
  
> [!NOTE]
> Bu kavram, bir kullanıcının "Ilk ad" sütunu tanımladığı bir Microsoft Excel elektronik tablosunda görünür hale gelir. Bu sütunda artık iki üst bilgi vardır: Kullanıcı tarafından tanımlanan "Ilk ad" üstbilgisi ve uygulama tarafından atanan sütun için alfasayısal atama.  
  
- İlgili kılavuz işlevselliği için [UI Otomasyonu kılavuz denetim modelini uygulama](implementing-the-ui-automation-grid-control-pattern.md) bölümüne bakın.  
  
 ![Karmaşık üstbilgi öğeleri içeren tablo.](./media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")  
Karmaşık sütun başlıkları içeren bir tablo örneği  
  
 ![Belirsiz Roworcolumnana özelliği olan tablo.](./media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")  
Belirsiz Roworcolumnana özelliği olan bir tablo örneği  
  
<a name="Required_Members_for_ITableProvider"></a>
## <a name="required-members-for-itableprovider"></a>ITableProvider için gerekli Üyeler  
 ITableProvider arabirimi için aşağıdaki özellikler ve Yöntemler gereklidir.  
  
|Gerekli Üyeler|Üye türü|Notlar|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableProvider.RowOrColumnMajor%2A>|Özellik|Hiçbiri|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetColumnHeaders%2A>|Yöntem|Hiçbiri|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetRowHeaders%2A>|Yöntem|Hiçbiri|  
  
 Bu denetim deseninin ilişkili olayları yok.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Özel durumlar  
 Bu denetim deseninin ilişkili özel durumları yok.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyon Denetim Düzenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyon Sağlayıcısında Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyon Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyon TableItem Denetim Düzeni Uygulama](implementing-the-ui-automation-tableitem-control-pattern.md)
- [UI Otomasyon Kılavuz Denetim Düzenini Uygulama](implementing-the-ui-automation-grid-control-pattern.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
