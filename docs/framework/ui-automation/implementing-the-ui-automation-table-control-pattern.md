---
title: UI Otomasyonu Tablo Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Table control pattern
- control patterns, Table
- TableControl pattern
ms.assetid: 880cd85c-aa8c-4fb5-9369-45491d34bb78
ms.openlocfilehash: 1fec3671f017ae6c6864537805e6c793b5f9046b
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458150"
---
# <a name="implementing-the-ui-automation-table-control-pattern"></a>UI Otomasyonu Tablo Denetim Düzenini Uygulama
> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konuda özellikler, Yöntemler ve olaylar hakkında bilgiler de dahil olmak üzere <xref:System.Windows.Automation.Provider.ITableProvider>uygulamak için yönergeler ve kurallar tanıtılmaktadır. Ek başvuruların bağlantıları genel bakış sonunda listelenir.  
  
 <xref:System.Windows.Automation.TablePattern> denetim deseninin bir alt öğe koleksiyonu için kapsayıcılar olarak davranan denetimleri desteklemek için kullanılır. Bu öğenin alt öğeleri <xref:System.Windows.Automation.Provider.ITableItemProvider> uygulamalıdır ve satır ve sütun tarafından çapraz bir şekilde iki boyutlu bir mantıksal koordinat sisteminde düzenlenmelidir. Bu denetim deseninin <xref:System.Windows.Automation.Provider.IGridProvider>benzer şekilde, <xref:System.Windows.Automation.Provider.ITableProvider> uygulayan herhangi bir denetimin her alt öğe için bir sütun ve/veya satır üst bilgisi ilişkisi olması gerekir. Bu denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama kılavuzları ve kuralları  
 Tablo denetim modelini uygularken aşağıdaki kılavuz ve kurallara göz önünde yer verilmiştir:  
  
- Tek tek hücrelerin içeriğine erişim iki boyutlu bir mantıksal koordinat sistemi veya <xref:System.Windows.Automation.Provider.IGridProvider>için gereken eşzamanlı uygulama tarafından sağlanmış dizi.  
  
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
|<xref:System.Windows.Automation.Provider.ITableProvider.RowOrColumnMajor%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetColumnHeaders%2A>|Yöntem|Yok.|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetRowHeaders%2A>|Yöntem|Yok.|  
  
 Bu denetim deseninin ilişkili olayları yok.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Özel Durumlar  
 Bu denetim deseninin ilişkili özel durumları yok.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Denetim Desenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyonu TableItem Denetim Desenini Uygulama](implementing-the-ui-automation-tableitem-control-pattern.md)
- [UI Otomasyonu Grid Denetim Desenini Uygulama](implementing-the-ui-automation-grid-control-pattern.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
