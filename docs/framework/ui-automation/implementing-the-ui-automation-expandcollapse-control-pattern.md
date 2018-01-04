---
title: "UI Otomasyon ExpandCollapse Denetim Düzeni Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, ExpandCollapse control pattern
- ExpandCollapse control pattern
- control patterns, ExpandCollapse
ms.assetid: 1dbabb8c-0d68-47c1-a35e-1c01cb01af26
caps.latest.revision: "25"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 8e956008c6b80e0b2184adcf0a45b70efa21d752
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-the-ui-automation-expandcollapse-control-pattern"></a>UI Otomasyon ExpandCollapse Denetim Düzeni Uygulama
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu kılavuzları ve uygulamak için kuralları tanıtır <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>, özellikleri, yöntemleri ve etkinlikleri hakkında bilgiler dahil olmak üzere. Ek başvurular bağlantılar genel bakış sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.ExpandCollapsePattern> Denetim düzeni görsel olarak daha fazla içerik görüntülemek için genişletme ve daraltma içeriği gizlemek için denetimleri desteklemek için kullanılır. Bu denetim düzeni uygulama denetimleri örnekleri için bkz: [denetim düzeni eşleştirmesi UI Otomasyon istemcileri için](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama rehberi ve kuralları  
 ExpandCollapse denetim düzeni uygulama, aşağıdaki yönergeleri ve kuralları dikkat edin:  
  
-   Denetimleri bir araya — Genişlet/Daralt işlevsellikle kullanıcı Arabirimi sağlayan alt nesneleri ile oluşturulan — desteklemelidir <xref:System.Windows.Automation.ExpandCollapsePattern> denetim düzeni kendi alt öğelerini yapılamaz. Örneğin, bir birleşik giriş kutusu denetimi liste kutusu, düğme ve düzenleme denetimleriyle birlikte yerleşiktir ancak desteklemesi gereken üst birleşik giriş kutusu olduğu <xref:System.Windows.Automation.ExpandCollapsePattern>.  
  
    > [!NOTE]
    >  Bir özel durum olan tek tek MenuItem nesnelerini, toplama menü denetimdir. MenuItem nesnelerini destekleyebilir <xref:System.Windows.Automation.ExpandCollapsePattern> denetim düzeni, ancak üst menü denetleyemezsiniz. Benzer bir özel durum ağacı ve ağaç öğesi denetimler için geçerlidir.  
  
-   Zaman <xref:System.Windows.Automation.ExpandCollapseState> bir denetimin kümesine <xref:System.Windows.Automation.ExpandCollapseState.LeafNode>, her türlü <xref:System.Windows.Automation.ExpandCollapsePattern> işlevselliği denetim için şu anda etkin değil ve bu denetim düzeni kullanılarak edinilebilir yalnızca bilgilerinin <xref:System.Windows.Automation.ExpandCollapseState>. Tüm alt nesneleri sonradan eklediyseniz, <xref:System.Windows.Automation.ExpandCollapseState> değişiklikleri ve <xref:System.Windows.Automation.ExpandCollapsePattern> işlevselliği etkinleştirilir.  
  
-   <xref:System.Windows.Automation.ExpandCollapseState>yalnızca anlık alt nesnelerin görünürlüğünü gösterir; tüm alt nesneler görünürlüğünü başvurmuyor.  
  
-   Genişletme ve daraltma işlevleri özel denetim. Bu davranış örnekleri verilmiştir.  
  
    -   Office kişisel menü üç durumlu MenuItem olabilir (<xref:System.Windows.Automation.ExpandCollapseState.Expanded>, <xref:System.Windows.Automation.ExpandCollapseState.Collapsed> ve <xref:System.Windows.Automation.ExpandCollapseState.PartiallyExpanded>) burada denetimi belirtir ne zaman benimsemeyi durumuna bir <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> veya <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> olarak adlandırılır.  
  
    -   Çağırma <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> Treeıtem tüm alt öğeleri veya yalnızca yakınındaki alt öğeleri görüntüleyebilir.  
  
    -   Çağırma varsa <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> veya <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> bir denetimde alt öğelerinden durumunu korur görünürlük değişiklik olayı gönderilmesi gerektiğini, durum değişikliği olayı üst denetim daraltılmış olduğunda alt öğeleri durumunu tutmaz varsa, Denetim olabilir artık görünür değildir ve yok etme olayı tüm bağımlı öğelerini yok; ya da değiştirin <xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A> bir görünürlük her alt öğesi ve raise olay değiştirin.  
  
-   Gezinti güvence altına almak için onu olduğu bir nesne için tercih edilir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacıyla (uygun görünürlük durumu) üst öğelerinden bağımsız olarak <xref:System.Windows.Automation.ExpandCollapseState>. İsteğe bağlı alt öğeleri oluşturursa, bunlar yalnızca olarak görünebilir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] görünür durumdayken sonra ilk kez veya yalnızca için görüntülenen ağacı.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-iexpandcollapseprovider"></a>Gerekli üyeleri IExpandCollapseProvider için  
 Aşağıdaki özellikleri ve yöntemleri uygulamak için gerekli olan <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>.  
  
|Gerekli üyeleri|Üye türü|Notlar|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A>|Yöntem|Yok.|  
|<xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A>|Yöntem|Yok.|  
|<xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>|Olay|Bu denetim ilişkili bir olay yok; yine de sahip istiyor musunuz? Bu genel temsilcisi kullanın.|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Özel Durumlar  
 Sağlayıcıları aşağıdaki özel durumlar oluşturma gerekir.  
  
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
