---
title: UI Otomasyonu Tablo Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Table control pattern
- control patterns, Table
- TableControl pattern
ms.assetid: 880cd85c-aa8c-4fb5-9369-45491d34bb78
ms.openlocfilehash: 0b3d000112060550734890ad3c4063a26c320b04
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180111"
---
# <a name="implementing-the-ui-automation-table-control-pattern"></a>UI Otomasyonu Tablo Denetim Düzenini Uygulama
> [!NOTE]
> Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır. Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, özellikler, yöntemler ve <xref:System.Windows.Automation.Provider.ITableProvider>olaylar hakkında bilgiler de dahil olmak üzere uygulama yönergeleri ve kuralları sunar. Ek başvurulara bağlantılar genel bakışın sonunda listelenir.  
  
 Denetim <xref:System.Windows.Automation.TablePattern> deseni, alt öğelerin toplanması için kapsayıcı görevi yapan denetimleri desteklemek için kullanılır. Bu öğenin alt <xref:System.Windows.Automation.Provider.ITableItemProvider> uygulamak ve satır ve sütun tarafından geçilebilir iki boyutlu bir mantıksal koordinat sistemi içinde organize edilmelidir. Bu denetim <xref:System.Windows.Automation.Provider.IGridProvider>deseni, herhangi bir denetim uygulamasının <xref:System.Windows.Automation.Provider.ITableProvider> her alt öğe için bir sütun ve/veya satır üstbilgi ilişkisini de ortaya koyması gerektiği ayrımıyla benzerdir. Bu denetim deseni uygulayan denetim örnekleri için, [UI Otomasyon Istemcileri için Denetim Deseni Eşleciliği'ne](control-pattern-mapping-for-ui-automation-clients.md)bakın.  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Uygulama Yönergeleri ve Sözleşmeleri  
 Tablo denetim deseni uygulanırken aşağıdaki yönergeleri ve kuralları not edin:  
  
- Tek tek hücrelerin içeriğine erişim, gerekli eşzamanlı uygulama tarafından sağlanan iki boyutlu bir <xref:System.Windows.Automation.Provider.IGridProvider>mantıksal koordinat sistemi veya dizi üzerinden dir.  
  
- Sütun veya satır üstbilgi bir tablo nesnesi içinde bulunabilir veya bir tablo nesnesi ile ilişkili ayrı bir üstbilgi nesnesi olabilir.  
  
- Sütun ve satır üstbilgi, hem birincil üstbilgi hem de destekleyici üstbilgi içerebilir.  
  
> [!NOTE]
> Bu kavram, bir kullanıcının "Ad" sütunu tanımladığı Microsoft Excel elektronik tablosunda belirgin hale gelir. Bu sütunda artık iki üstbilgi vardır: kullanıcı tarafından tanımlanan "Ad" başlığı ve uygulama tarafından atanan bu sütuniçin alfasayısal atama.  
  
- İlgili ızgara işlevselliği için [UI Automation Grid Control Modelini uygulama](implementing-the-ui-automation-grid-control-pattern.md) hakkındabkz.  
  
 ![Karmaşık üstbilgi öğeleri içeren tablo.](./media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")  
Karmaşık Sütun Üstbilgili Tablo Örneği  
  
 ![Belirsiz RowOrColumnMajor özelliğine sahip tablo.](./media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")  
Belirsiz Satır Veya SütunAna Özelliği Olan Tablo Örneği  
  
<a name="Required_Members_for_ITableProvider"></a>
## <a name="required-members-for-itableprovider"></a>ITableProvider için Gerekli Üyeler  
 ITableProvider arabirimi için aşağıdaki özellikler ve yöntemler gereklidir.  
  
|Gerekli üyeler|Üye tipi|Notlar|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableProvider.RowOrColumnMajor%2A>|Özellik|None|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetColumnHeaders%2A>|Yöntem|None|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetRowHeaders%2A>|Yöntem|None|  
  
 Bu denetim deseni ilişkili olaylar vardır.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Özel durumlar  
 Bu denetim deseni ilişkili özel durumlar vardır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Denetim Desenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyonu TableItem Denetim Desenini Uygulama](implementing-the-ui-automation-tableitem-control-pattern.md)
- [UI Otomasyonu Grid Denetim Desenini Uygulama](implementing-the-ui-automation-grid-control-pattern.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
