---
title: UI Otomasyon Ağacına Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- automation tree
- UI Automation, tree
ms.assetid: 03b98058-bdb3-47a0-8ff7-45e6cdf67166
ms.openlocfilehash: d1edbb82e0d5d6a6275c09646fbf8e54b4ff90df
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74800286"
---
# <a name="ui-automation-tree-overview"></a>UI Otomasyon Ağacına Genel Bakış
> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Yardımcı teknoloji ürünleri ve test betikleri, [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] ve öğeleri hakkında bilgi toplamak için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacına gider.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı içinde, geçerli masaüstünü temsil eden ve alt öğeleri uygulama pencerelerini temsil eden bir kök öğe (<xref:System.Windows.Automation.AutomationElement.RootElement%2A>) vardır. Bu alt öğelerin her biri, menüler, düğmeler, araç çubukları ve liste kutuları gibi [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] parçalarını temsil eden öğeleri içerebilir. Sırasıyla bu öğeler, liste öğeleri gibi öğeler içerebilir.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı sabit bir yapı değildir ve binlerce öğe içerebileceğinden, totality içinde nadiren görülmüştür. Bunların bölümleri, gerektiği gibi oluşturulur ve öğeler eklendikçe, taşındığında veya kaldırıldığında değişikliklere devam edebilir.  
  
 UI Otomasyon sağlayıcıları, bir ana bilgisayardan (genellikle bir pencerede barındırılan) ve bir alt ağaçta oluşan bir parçadaki öğeler arasında gezinti uygulayarak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacını destekler. Ancak, sağlayıcılar bir denetimden diğerine gidilmesiyle ilgilenmez. Bu, varsayılan pencere sağlayıcılarının bilgileri kullanılarak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] çekirdeği tarafından yönetilir.  
  
<a name="uiautomation_tree_view"></a>   
## <a name="views-of-the-automation-tree"></a>Otomasyon ağacının görünümleri  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı, yalnızca belirli bir istemciyle ilgili <xref:System.Windows.Automation.AutomationElement> nesneleri içeren görünümler oluşturmak üzere filtrelenebilir. Bu yaklaşım, istemcilerin [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ile sunulan yapıyı belirli gereksinimlerine özelleştirmesini sağlar.  
  
 İstemci, görünümü özelleştirmeye ve filtrelemeye göre, görünümü özelleştirmenin iki yolu vardır. Kapsam, görünümün kapsamını bir temel öğeden başlayarak tanımlıyor: Örneğin, uygulama yalnızca masaüstünün doğrudan alt öğelerini veya bir uygulama penceresinin tüm alt öğelerini bulmak isteyebilir. Filtreleme, görünüme dahil edilecek öğe türlerini tanımlar.  
  
 UI Otomasyon sağlayıcıları, <xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty> ve <xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty> özellikleri dahil olmak üzere öğelerde Özellikler tanımlayarak filtrelemeyi destekler.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] üç varsayılan görünüm sağlar. Bu görünümler, gerçekleştirilen filtreleme türü tarafından tanımlanır; herhangi bir görünümün kapsamı uygulama tarafından tanımlanır. Ayrıca, uygulama özellikleri üzerinde başka filtreler de uygulayabilir; Örneğin, bir denetim görünümünde yalnızca etkin denetimleri dahil etmek için.  
  
<a name="uiautomation_raw_view"></a>   
### <a name="raw-view"></a>Ham görünüm  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının ham görünümü, masaüstünün kök olduğu <xref:System.Windows.Automation.AutomationElement> nesnelerinin tam ağacıdır. Ham görünüm, bir uygulamanın yerel programlama yapısına yakından uyar ve bu nedenle, en ayrıntılı görünüm kullanılabilir. Ayrıca, ağacın diğer görünümlerinin oluşturulduğu temeldir. Bu görünüm temeldeki [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] çerçevesine bağlı olduğundan, bir [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] düğmesinin ham görünümü [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] düğmeden farklı bir ham görünüme sahip olur.  
  
 Ham görünüm, Özellikler belirtilmeden veya ağaçta gezinmek için <xref:System.Windows.Automation.TreeWalker.RawViewWalker> kullanarak öğeleri arayarak elde edilir.  
  
<a name="uiautomation_control_view"></a>   
### <a name="control-view"></a>Denetim görünümü  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının denetim görünümü, yardımcı teknoloji ürününün son kullanıcıya [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] açıklama oluşturma görevini basitleştirir ve son kullanıcının, son kullanıcı tarafından algılanan [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] yapısına yakından eşlendiğinden uygulamayla etkileşime geçmesini sağlar.  
  
 Denetim görünümü ham görünümün bir alt kümesidir. Bir son kullanıcının etkileşimli olarak anlayabilmesi veya [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]denetimin mantıksal yapısına katkıda bulunmak için ham görünümden tüm [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğelerini içerir. [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]mantıksal yapısına katkıda bulunan ancak etkileşimli olmayan [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğe örnekleri, liste görünümü üstbilgileri, araç çubukları, menüler ve durum çubuğu gibi öğe kapsayıcılarıdır. Yalnızca Düzen veya dekoratif amaçlar için kullanılan etkileşimli olmayan öğeler denetim görünümünde görünmez. Örneğin, yalnızca bir iletişim kutusundaki denetimleri düzenlemek için kullanılan, ancak kendisi herhangi bir bilgi içermeyen bir paneldir. Denetim görünümünde görünecek etkileşimli olmayan öğeler, iletişim kutusunda bilgi ve statik metin içeren grafiklerdir. Denetim görünümünde bulunan etkileşimli olmayan öğeler klavye odağı alamaz.  
  
 Denetim görünümü, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> özelliği `true`olarak ayarlanmış öğeleri arayarak veya ağaçta gezinmek için <xref:System.Windows.Automation.TreeWalker.ControlViewWalker> kullanarak elde edilir.  
  
<a name="uiautomation_content_view"></a>   
### <a name="content-view"></a>İçerik görünümü  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının içerik görünümü Denetim görünümünün bir alt kümesidir. Klavye odağını alabilen [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğeler ve bir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğesinde etiket olmayan bazı metinler dahil olmak üzere, Kullanıcı arabirimindeki gerçek bilgileri ileten [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğeleri içerir. Örneğin, bir açılan Birleşik giriş kutusundaki değerler, bir son kullanıcı tarafından kullanılan bilgileri temsil ettiğinden içerik görünümünde görüntülenir. İçerik görünümünde, Birleşik giriş kutusu ve liste kutusu her ikisi de bir veya birden fazla öğenin seçilebileceği [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğelerinin bir koleksiyonu olarak gösterilir. Birisi her zaman açıktır ve bir Kullanıcı, verileri veya içeriği göstermek üzere tasarlandığından, içerik görünümünde bir tane genişleyebilir ve daraltılır.  
  
 İçerik görünümü, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> özelliği `true`olarak ayarlanmış öğeleri arayarak veya ağaçta gezinmek için <xref:System.Windows.Automation.TreeWalker.ContentViewWalker> kullanarak elde edilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.AutomationElement>
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
