---
title: UI Otomasyon ExpandCollapse Denetim Düzeni Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, ExpandCollapse control pattern
- ExpandCollapse control pattern
- control patterns, ExpandCollapse
ms.assetid: 1dbabb8c-0d68-47c1-a35e-1c01cb01af26
ms.openlocfilehash: 073ff0727fc6aab1189f73a254aa95da60820cc3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447152"
---
# <a name="implementing-the-ui-automation-expandcollapse-control-pattern"></a>UI Otomasyon ExpandCollapse Denetim Düzeni Uygulama

> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).

Bu konuda özellikler, Yöntemler ve olaylar hakkında bilgiler de dahil olmak üzere <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>uygulamak için yönergeler ve kurallar tanıtılmaktadır. Ek başvuruların bağlantıları genel bakış sonunda listelenir.

<xref:System.Windows.Automation.ExpandCollapsePattern> denetim deseninin daha fazla içerik görüntülemesi için görsel genişlettikten ve içeriği gizlemek için daraltılacak denetimleri desteklemek için kullanılır. Bu denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](control-pattern-mapping-for-ui-automation-clients.md).

<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a>Uygulama kılavuzları ve kuralları

ExpandCollapse denetim modelini uygularken, aşağıdaki kılavuz ve kurallara göz önünde yer verilmiştir:

- Genişletme/daraltma işleviyle Kullanıcı arabirimini sağlayan alt nesnelerle oluşturulan toplama denetimleri, alt öğeleri olmadığından <xref:System.Windows.Automation.ExpandCollapsePattern> denetim deseninin desteklenmesi gerekir. Örneğin, bir Birleşik giriş kutusu denetimi liste kutusu, düğme ve düzenleme denetimlerinin birleşimiyle oluşturulur, ancak yalnızca <xref:System.Windows.Automation.ExpandCollapsePattern>desteklemesi gereken üst Birleşik giriş kutusudur.

  > [!NOTE]
  > Özel durum, tek tek MenuItem nesnelerinin toplamı olan menü denetimidir. MenuItem nesneleri <xref:System.Windows.Automation.ExpandCollapsePattern> denetim modelini destekleyebilir, ancak üst menü denetimi olamaz. Ağaç ve ağaç öğesi denetimleri için benzer bir özel durum geçerlidir.

- Bir denetimin <xref:System.Windows.Automation.ExpandCollapseState> <xref:System.Windows.Automation.ExpandCollapseState.LeafNode>olarak ayarlandığında, herhangi bir <xref:System.Windows.Automation.ExpandCollapsePattern> işlevi şu anda denetim için etkin değildir ve bu denetim modelini kullanarak elde edilebilir tek bilgi, <xref:System.Windows.Automation.ExpandCollapseState>. Herhangi bir alt nesne daha sonra eklenirse, <xref:System.Windows.Automation.ExpandCollapseState> değişiklik ve <xref:System.Windows.Automation.ExpandCollapsePattern> işlevi etkinleştirilir.

- <xref:System.Windows.Automation.ExpandCollapseState>, yalnızca anlık alt nesnelerin görünürlüğünü ifade eder; tüm alt nesnelerin görünürlüğüne başvurmaz.

- Genişletme ve daraltma işlevselliği denetimine özgüdür. Aşağıda bu davranışın örnekleri verilmiştir.

  - Office kişisel menüsü, bir <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> veya <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> çağrıldığında denetimin benimseme durumunu belirttiği Üçlü durum MenuItem (<xref:System.Windows.Automation.ExpandCollapseState.Expanded>, <xref:System.Windows.Automation.ExpandCollapseState.Collapsed> ve <xref:System.Windows.Automation.ExpandCollapseState.PartiallyExpanded>) olabilir.

  - Bir ağaç öğesinde <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> çağırmak, tüm alt öğeleri veya yalnızca anlık alt öğeleri görüntüleyebilir.

  - Bir denetimde <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> veya <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> çağırmak, alt öğelerinin durumunu tutuyorsa, üst denetim daraltılmış durumdayken alt öğelerinin durumunu korumuyorsa, denetim artık görünür olmayan tüm alt öğeleri yok edebilir ve yok edilmiş bir olay oluşturabilir; ya da her alt öğe için <xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A> değiştirebilir ve görünürlük değişikliği olayı oluşturabilir.

- Gezinmeyi güvence altına almak için, üst <xref:System.Windows.Automation.ExpandCollapseState>ne olursa olsun bir nesnenin [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaçta (uygun görünürlük durumuyla) olması tercih edilir. İsteğe bağlı olarak alt öğeler oluşturulursa, yalnızca ilk kez veya görünür olmaları durumunda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaçta görünebilirler.

<a name="Required_Members_for_the_IValueProvider_Interface"></a>

## <a name="required-members-for-iexpandcollapseprovider"></a>IExpandCollapseProvider için gerekli Üyeler

<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>uygulamak için aşağıdaki özellikler ve Yöntemler gereklidir.

|Gerekli Üyeler|Üye türü|Notlar|
|----------------------|-----------------|-----------|
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A>|Özellik|Yok.|
|<xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A>|Yöntem|Yok.|
|<xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A>|Yöntem|Yok.|
|<xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>|Olay|Bu denetimde ilişkili olay yok; Bu genel temsilciyi kullanın.|

<a name="Exceptions"></a>

## <a name="exceptions"></a>Özel durumlar

Sağlayıcılar aşağıdaki özel durumları oluşturması gerekir.

|Özel durum türü|Koşul|
|--------------------|---------------|
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.ExpandCollapseState> = <xref:System.Windows.Automation.ExpandCollapseState.LeafNode><xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> ya da <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> çağrılır.|

## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Denetim Desenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [TreeWalker ile UI Otomasyonu Öğeleri Arasında Gezinme](navigate-among-ui-automation-elements-with-treewalker.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
