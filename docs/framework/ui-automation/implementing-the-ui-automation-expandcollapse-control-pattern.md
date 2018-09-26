---
title: UI Otomasyon ExpandCollapse Denetim Düzeni Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, ExpandCollapse control pattern
- ExpandCollapse control pattern
- control patterns, ExpandCollapse
ms.assetid: 1dbabb8c-0d68-47c1-a35e-1c01cb01af26
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 307cbfa9b41440ebfe2b0d9fd15715a32b8a7cca
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47198130"
---
# <a name="implementing-the-ui-automation-expandcollapse-control-pattern"></a>UI Otomasyon ExpandCollapse Denetim Düzeni Uygulama
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu, yönergeleri ve uygulama kuralları tanıtır <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>, özellikler, yöntemler ve olaylar hakkında bilgiler dahil olmak üzere. Ek başvurular bağlantılar genel bakış sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.ExpandCollapsePattern> Denetim düzeni, görsel olarak daha fazla içeriği görüntülemek için genişletme ve içeriği gizlemek için daraltma denetimleri desteklemek için kullanılır. Bu denetim düzeni uygulama denetimleri örnekleri için bkz: [denetim düzeni eşlemesi için UI Otomasyonu istemcileri](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama yönergeleri ve kuralları  
 ExpandCollapse denetim düzeni uygularken aşağıdaki yönergeler ve kuralları dikkat edin:  
  
-   Denetimleri bir araya — Genişlet/Daralt işlevselliği ile kullanıcı arabirimini sağlayan alt nesneleri ile oluşturulmuş — desteklemelidir <xref:System.Windows.Automation.ExpandCollapsePattern> denetim düzeni bunların alt öğeleri almamasıdır. Örneğin, bir birleşik giriş kutusu denetimi birleşimi liste kutusu ve düğme düzenleme denetimleri ile derlendi ancak desteklemesi gereken üst birleşik giriş kutusu olan <xref:System.Windows.Automation.ExpandCollapsePattern>.  
  
    > [!NOTE]
    >  Tek tek MenuItem nesnelerin bir toplama menü denetimi istisnadır. MenuItem nesnelerini destekleyebilir <xref:System.Windows.Automation.ExpandCollapsePattern> denetim düzeni, ancak üst menü denetleyemezsiniz. Benzer bir özel durum ağacı ve ağaç öğesi denetim için geçerlidir.  
  
-   Zaman <xref:System.Windows.Automation.ExpandCollapseState> denetimin kümesine <xref:System.Windows.Automation.ExpandCollapseState.LeafNode>, <xref:System.Windows.Automation.ExpandCollapsePattern> işlevselliği denetim için şu anda etkin değil ve bu denetim desenini kullanarak elde edilebilecek tek bilgi <xref:System.Windows.Automation.ExpandCollapseState>. Tüm alt nesneleri daha sonradan eklenen, <xref:System.Windows.Automation.ExpandCollapseState> değişiklikleri ve <xref:System.Windows.Automation.ExpandCollapsePattern> işlevselliği etkinleştirilir.  
  
-   <xref:System.Windows.Automation.ExpandCollapseState> yalnızca ilk alt nesneler görünürlüğünü gösterir. tüm alt nesneleri görünürlüğünü başvurmuyor.  
  
-   Genişlet ve Daralt işlevi denetimine özgü olur. Bu davranış örnekleri aşağıda verilmiştir.  
  
    -   Office kişisel menü üç durum MenuItem olabilir (<xref:System.Windows.Automation.ExpandCollapseState.Expanded>, <xref:System.Windows.Automation.ExpandCollapseState.Collapsed> ve <xref:System.Windows.Automation.ExpandCollapseState.PartiallyExpanded>) burada denetimi belirtir benimsemek ne zaman durumuna bir <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> veya <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> çağrılır.  
  
    -   Çağırma <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> üzerinde bir Treeıtem tüm alt öğeleri veya yalnızca yakınındaki alt öğeleri görüntülenebilir.  
  
    -   Çağırma varsa <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> veya <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> denetimde alt öğelerini durumunu korur görünürlük değişiklik olayı gönderilmesi, durum değişiklik olayı üst denetim daraltılmış olduğunda alt öğelerini durumunu değilse, Denetim olabilir artık görünür değildir ve yok etme olayı tüm alt öğeleri yok; veya üzerinde değişiklik <xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A> her bir alt öğesi ve artırma için görünürlük değişiklik olayı.  
  
-   Gezinti sağlamak için nesnenin olması tercih edilir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacıyla (uygun görünürlük durumu) öğelerinden bakılmaksızın <xref:System.Windows.Automation.ExpandCollapseState>. İsteğe bağlı alt öğeleri oluşturduysanız, bunlar yalnızca görünebilir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] görünür çalışırken sonra ilk zaman veya yalnızca için görüntülenen ağaç.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-iexpandcollapseprovider"></a>Gerekli üyeleri IExpandCollapseProvider için  
 Aşağıdaki özellikleri ve yöntemleri uygulamak için gerekli olan <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>.  
  
|Gerekli üyeleri|Üye türü|Notlar|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A>|Yöntem|Yok.|  
|<xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A>|Yöntem|Yok.|  
|<xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>|Olay|Bu denetim, ilişkili olay vardır; Bu genel temsilcinin kullanın.|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Özel Durumlar  
 Sağlayıcıları, aşağıdaki özel durumlar gerekir.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Ya da <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> veya <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> aldığında çağrılan <xref:System.Windows.Automation.ExpandCollapseState>  =  <xref:System.Windows.Automation.ExpandCollapseState.LeafNode>.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UI Otomasyonu Denetim Desenlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [İstemciler İçin UI Otomasyonu Denetim Düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [TreeWalker ile UI Otomasyonu Öğeleri Arasında Gezinme](../../../docs/framework/ui-automation/navigate-among-ui-automation-elements-with-treewalker.md)  
 [UI Otomasyon Ağacına Genel Bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [UI Otomasyonunda Önbelleğe Almayı Kullanma](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
