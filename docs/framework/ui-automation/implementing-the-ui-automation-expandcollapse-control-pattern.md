---
title: UI Otomasyon ExpandCollapse Denetim Düzeni Uygulama
description: UI otomasyonunda ExpandCollapse denetim deseninin uygulama kılavuzlarını ve kurallarını öğrenin. IExpandCollapseProvider nasıl uygulanacağını öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, ExpandCollapse control pattern
- ExpandCollapse control pattern
- control patterns, ExpandCollapse
ms.assetid: 1dbabb8c-0d68-47c1-a35e-1c01cb01af26
ms.openlocfilehash: 525b57816071ba2d879036676201a0506d1a29db
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165862"
---
# <a name="implementing-the-ui-automation-expandcollapse-control-pattern"></a>UI Otomasyon ExpandCollapse Denetim Düzeni Uygulama

> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).

Bu konuda <xref:System.Windows.Automation.Provider.IExpandCollapseProvider> Özellikler, Yöntemler ve olaylar hakkında bilgiler de dahil olmak üzere uygulama yönergeleri ve kuralları tanıtılmaktadır. Ek başvuruların bağlantıları genel bakış sonunda listelenir.

<xref:System.Windows.Automation.ExpandCollapsePattern>Denetim deseninin daha fazla içerik görüntülemesi için görsel genişlettikten ve içeriği gizlemek için daraltılacak denetimleri desteklemek için kullanılır. Bu denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](control-pattern-mapping-for-ui-automation-clients.md).

<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a>Uygulama kılavuzları ve kuralları

ExpandCollapse denetim modelini uygularken, aşağıdaki kılavuz ve kurallara göz önünde yer verilmiştir:

- Genişletme/daraltma işleviyle Kullanıcı arabirimini sağlayan alt nesneler ile oluşturulan toplama denetimleri, <xref:System.Windows.Automation.ExpandCollapsePattern> alt öğeleri olmadığı halde denetim deseninin desteklenmesi gerekir. Örneğin, bir Birleşik giriş kutusu denetimi liste kutusu, düğme ve düzenleme denetimleri ile oluşturulmuştur, ancak yalnızca öğesini desteklemesi gereken üst Birleşik giriş kutusudur <xref:System.Windows.Automation.ExpandCollapsePattern> .

  > [!NOTE]
  > Özel durum, tek tek MenuItem nesnelerinin toplamı olan menü denetimidir. MenuItem nesneleri <xref:System.Windows.Automation.ExpandCollapsePattern> Denetim modelini destekleyebilir, ancak üst menü denetimi olamaz. Ağaç ve ağaç öğesi denetimleri için benzer bir özel durum geçerlidir.

- <xref:System.Windows.Automation.ExpandCollapseState>Bir denetimin ' e ayarlandığı zaman <xref:System.Windows.Automation.ExpandCollapseState.LeafNode> , herhangi bir <xref:System.Windows.Automation.ExpandCollapsePattern> işlev denetim için şu anda etkin değildir ve bu denetim düzeniyle elde edilebilir tek bilgiler <xref:System.Windows.Automation.ExpandCollapseState> . Herhangi bir alt nesne daha sonra eklenirse, <xref:System.Windows.Automation.ExpandCollapseState> değişiklikler ve <xref:System.Windows.Automation.ExpandCollapsePattern> işlevler etkinleştirilir.

- <xref:System.Windows.Automation.ExpandCollapseState>yalnızca anlık alt nesnelerin görünürlüğünü ifade eder; tüm alt nesnelerin görünürlüğüne başvurmaz.

- Genişletme ve daraltma işlevselliği denetimine özgüdür. Aşağıda bu davranışın örnekleri verilmiştir.

  - Office kişisel menüsü, <xref:System.Windows.Automation.ExpandCollapseState.Expanded> <xref:System.Windows.Automation.ExpandCollapseState.Collapsed> <xref:System.Windows.Automation.ExpandCollapseState.PartiallyExpanded> bir veya çağrıldığında denetimin benimseme durumunu belirttiği bir üçlü durum MenuItem (ve) olabilir <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> .

  - <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A>Bir ağaç öğesinde çağırmak, tüm alt öğeleri veya yalnızca anlık alt öğeleri görüntüleyebilir.

  - <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> Bir denetimin çağrılması veya bir denetim üzerinde, alt öğelerinin durumunu tutuyorsa, üst denetim daraltılmış durumdayken alt öğelerinin durumunu korumuyorsa, denetim artık görünmeyen tüm alt öğeleri yok edebilir ve yok etme olayı oluşturabilir veya <xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A> her alt öğe için öğesini değiştirebilir ve görünürlük değişikliği olayını oluşturabilir.

- Gezinmeyi garantilemek için, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] üst öğelerinden bağımsız olarak bir nesnenin ağaçta olması (uygun görünürlük durumuyla) istenir <xref:System.Windows.Automation.ExpandCollapseState> . İsteğe bağlı olarak alt öğeler oluşturulursa, yalnızca [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ilk kez veya görünür olmaları durumunda yalnızca ağaçta görünebilirler.

<a name="Required_Members_for_the_IValueProvider_Interface"></a>

## <a name="required-members-for-iexpandcollapseprovider"></a>IExpandCollapseProvider için gerekli Üyeler

Uygulamak için aşağıdaki özellikler ve Yöntemler gereklidir <xref:System.Windows.Automation.Provider.IExpandCollapseProvider> .

|Gerekli Üyeler|Üye türü|Notlar|
|----------------------|-----------------|-----------|
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A>|Özellik|Hiçbiri|
|<xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A>|Yöntem|Hiçbiri|
|<xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A>|Yöntem|Hiçbiri|
|<xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>|Olay|Bu denetimde ilişkili olay yok; Bu genel temsilciyi kullanın.|

<a name="Exceptions"></a>

## <a name="exceptions"></a>Özel durumlar

Sağlayıcılar aşağıdaki özel durumları oluşturması gerekir.

|Özel durum türü|Koşul|
|--------------------|---------------|
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A>Ya da <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> olarak çağrılır <xref:System.Windows.Automation.ExpandCollapseState>  =  <xref:System.Windows.Automation.ExpandCollapseState.LeafNode> .|

## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyon Denetim Düzenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyon Sağlayıcısında Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyon Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [TreeWalker ile UI Otomasyon Öğeleri Arasında Gezinme](navigate-among-ui-automation-elements-with-treewalker.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
