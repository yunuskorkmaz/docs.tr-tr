---
title: UI Otomasyonu Tablo Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Table control pattern
- control patterns, Table
- TableControl pattern
ms.assetid: 880cd85c-aa8c-4fb5-9369-45491d34bb78
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 955d9f005a45ab805012dd43cbef27877a9dfdb4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="implementing-the-ui-automation-table-control-pattern"></a>UI Otomasyonu Tablo Denetim Düzenini Uygulama
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu kılavuzları ve uygulamak için kuralları tanıtır <xref:System.Windows.Automation.Provider.ITableProvider>, özellikleri, yöntemleri ve etkinlikleri hakkında bilgiler dahil olmak üzere. Ek başvurular bağlantılar genel bakış sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.TablePattern> Denetim düzeni alt öğe koleksiyonunu için kapsayıcı olarak hareket denetimleri desteklemek için kullanılır. Bu öğenin alt öğeleri uygulamalıdır <xref:System.Windows.Automation.Provider.ITableItemProvider> ve satır ve sütun tarafından geçiş bir iki boyutlu mantıksal koordinat sistemi düzenlenir. Bu denetim düzeni paraleldir <xref:System.Windows.Automation.Provider.IGridProvider>, herhangi bir uygulama denetim ayrım ile <xref:System.Windows.Automation.Provider.ITableProvider> her alt öğesi için bir sütun ve/veya satır üstbilgisi ilişki de kullanıma gerekir. Bu denetim düzeni uygulama denetimleri örnekleri için bkz: [denetim düzeni eşleştirmesi UI Otomasyon istemcileri için](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama rehberi ve kuralları  
 Tablo denetim düzenini uygulama, aşağıdaki yönergeleri ve kuralları dikkat edin:  
  
-   Tek tek hücreler içeriğe erişimi olan bir iki boyutlu mantıksal koordinat sistemi ya da gerekli eşzamanlı uygulaması tarafından sağlanan dizi yoluyla <xref:System.Windows.Automation.Provider.IGridProvider>.  
  
-   Bir sütun veya satır üstbilgisi bir tablo nesnesi içinde bulunabilir veya bir tablo nesneyle ilişkilendirilen bir ayrı bir üstbilgi nesnesi olmalıdır.  
  
-   Sütun ve satır başlıklarının hem birincil üst bilgi, hem de tüm destekleyici üstbilgileri içerebilir.  
  
> [!NOTE]
>  Bu kavram, korumalı hale bir [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] burada bir kullanıcının belirlediği bir "Ad" sütununu elektronik tablo. Bu artık iki Üstbilgi sütununda — kullanıcı ve uygulama tarafından atanan bu sütun için alfasayısal ataması tarafından tanımlanan "Ad" başlığı.  
  
-   Bkz: [UI Otomasyon kılavuz denetim düzenini uygulama](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md) ilgili kılavuz işlevselliği için.  
  
 ![Karmaşık üstbilgi öğeleri içeren tablo. ] (../../../docs/framework/ui-automation/media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")  
Karmaşık sütun üst bilgileri içeren bir tablo örneği  
  
 ![Tablo Belirsiz RowOrColumnMajor özelliğine sahip. ] (../../../docs/framework/ui-automation/media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")  
Belirsiz RowOrColumnMajor özelliğine sahip bir tablo örneği  
  
<a name="Required_Members_for_ITableProvider"></a>   
## <a name="required-members-for-itableprovider"></a>Gerekli üyeleri ITableProvider için  
 Aşağıdaki özellikleri ve yöntemleri için ITableProvider arabirimi gerekli değildir.  
  
|Gerekli üyeleri|Üye türü|Notlar|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableProvider.RowOrColumnMajor%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetColumnHeaders%2A>|Yöntem|Yok.|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetRowHeaders%2A>|Yöntem|Yok.|  
  
 Bu denetim düzeni ilişkili olay vardır.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Özel Durumlar  
 Bu denetim düzeni ilişkili hiçbir özel durum vardır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UI Otomasyonu Denetim Desenlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [İstemciler İçin UI Otomasyonu Denetim Düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [UI Otomasyonu TableItem Denetim Desenini Uygulama](../../../docs/framework/ui-automation/implementing-the-ui-automation-tableitem-control-pattern.md)  
 [UI Otomasyonu Grid Denetim Desenini Uygulama](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md)  
 [UI Otomasyon Ağacına Genel Bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [UI Otomasyonunda Önbelleğe Almayı Kullanma](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
