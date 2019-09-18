---
title: UI Otomasyon ExpandCollapse Denetim Düzeni Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, ExpandCollapse control pattern
- ExpandCollapse control pattern
- control patterns, ExpandCollapse
ms.assetid: 1dbabb8c-0d68-47c1-a35e-1c01cb01af26
ms.openlocfilehash: 232bceba8286c2566a7df03b9001a5c43b348b20
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043454"
---
# <a name="implementing-the-ui-automation-expandcollapse-control-pattern"></a>UI Otomasyon ExpandCollapse Denetim Düzeni Uygulama

> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).

Bu konuda özellikler, Yöntemler ve olaylar hakkında <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>bilgiler de dahil olmak üzere uygulama yönergeleri ve kuralları tanıtılmaktadır. Ek başvuruların bağlantıları genel bakış sonunda listelenir.

<xref:System.Windows.Automation.ExpandCollapsePattern> Denetim deseninin daha fazla içerik görüntülemesi için görsel genişlettikten ve içeriği gizlemek için daraltılacak denetimleri desteklemek için kullanılır. Bu denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](control-pattern-mapping-for-ui-automation-clients.md).

<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a>Uygulama kılavuzları ve kuralları

ExpandCollapse denetim modelini uygularken, aşağıdaki kılavuz ve kurallara göz önünde yer verilmiştir:

- Genişletme/daraltma işleviyle Kullanıcı arabirimini sağlayan alt nesneler ile oluşturulan toplama denetimleri, <xref:System.Windows.Automation.ExpandCollapsePattern> alt öğeleri olmadığı halde denetim deseninin desteklenmesi gerekir. Örneğin, bir Birleşik giriş kutusu denetimi liste kutusu, düğme ve düzenleme denetimleri ile oluşturulmuştur, ancak yalnızca öğesini desteklemesi <xref:System.Windows.Automation.ExpandCollapsePattern>gereken üst Birleşik giriş kutusudur.

  > [!NOTE]
  > Özel durum, tek tek MenuItem nesnelerinin toplamı olan menü denetimidir. MenuItem nesneleri <xref:System.Windows.Automation.ExpandCollapsePattern> denetim modelini destekleyebilir, ancak üst menü denetimi olamaz. Ağaç ve ağaç öğesi denetimleri için benzer bir özel durum geçerlidir.

- Bir denetimin ' e <xref:System.Windows.Automation.ExpandCollapseState.LeafNode>ayarlandığı zaman, herhangi <xref:System.Windows.Automation.ExpandCollapsePattern> bir işlev denetim için şu anda etkin değildir ve bu denetim düzeniyle <xref:System.Windows.Automation.ExpandCollapseState>elde edilebilir tek bilgiler. <xref:System.Windows.Automation.ExpandCollapseState> Herhangi bir alt nesne daha sonra eklenirse, <xref:System.Windows.Automation.ExpandCollapseState> değişiklikler ve <xref:System.Windows.Automation.ExpandCollapsePattern> işlevler etkinleştirilir.

- <xref:System.Windows.Automation.ExpandCollapseState>yalnızca anlık alt nesnelerin görünürlüğünü ifade eder; tüm alt nesnelerin görünürlüğüne başvurmaz.

- Genişletme ve daraltma işlevselliği denetimine özgüdür. Aşağıda bu davranışın örnekleri verilmiştir.

  - Office kişisel menüsü, bir<xref:System.Windows.Automation.ExpandCollapseState.Expanded> <xref:System.Windows.Automation.ExpandCollapseState.PartiallyExpanded> veya<xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> <xref:System.Windows.Automation.ExpandCollapseState.Collapsed> çağrıldığında<xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> denetimin benimseme durumunu belirttiği bir üçlü durum MenuItem (ve) olabilir.

  - Bir <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> ağaç öğesinde çağırmak, tüm alt öğeleri veya yalnızca anlık alt öğeleri görüntüleyebilir.

  - Bir denetimde <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> veya <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> bir denetim üzerinde çağrılması durumunda, alt öğelerinin durumu korunsa da, üst denetim daraltılmış durumdayken alt öğelerinin durumunu korumasa, bir görünürlük değişiklik olayı gönderilmesi gerekir, bu durum değişiklik olayı değil, denetim artık görünür olmayan tüm alt öğeleri yok edin ve yok edilmiş bir olayı yükseltin; ya da <xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A> her alt öğe için öğesini değiştirebilir ve görünürlük değişikliği olayı oluşturabilir.

- Gezinmeyi garantilemek için, üst öğelerinden [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation.ExpandCollapseState>bağımsız olarak bir nesnenin ağaçta olması (uygun görünürlük durumuyla) istenir. İsteğe bağlı olarak alt öğeler oluşturulursa, yalnızca ilk kez veya görünür olmaları [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] durumunda yalnızca ağaçta görünebilirler.

<a name="Required_Members_for_the_IValueProvider_Interface"></a>

## <a name="required-members-for-iexpandcollapseprovider"></a>IExpandCollapseProvider için gerekli Üyeler

Uygulamak <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>için aşağıdaki özellikler ve Yöntemler gereklidir.

|Gerekli Üyeler|Üye türü|Notlar|
|----------------------|-----------------|-----------|
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A>|Özellik|Yok.|
|<xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A>|Yöntem|Yok.|
|<xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A>|Yöntem|Yok.|
|<xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>|Olay|Bu denetimde ilişkili olay yok; Bu genel temsilciyi kullanın.|

<a name="Exceptions"></a>

## <a name="exceptions"></a>Özel Durumlar

Sağlayıcılar aşağıdaki özel durumları oluşturması gerekir.

|Özel durum türü|Koşul|
|--------------------|---------------|
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> Ya daolarak = çağrılır. <xref:System.Windows.Automation.ExpandCollapseState> <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> <xref:System.Windows.Automation.ExpandCollapseState.LeafNode>|

## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Denetim Desenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [TreeWalker ile UI Otomasyonu Öğeleri Arasında Gezinme](navigate-among-ui-automation-elements-with-treewalker.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
