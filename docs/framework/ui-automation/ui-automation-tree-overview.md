---
title: UI Otomasyon Ağacına Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- automation tree
- UI Automation, tree
ms.assetid: 03b98058-bdb3-47a0-8ff7-45e6cdf67166
ms.openlocfilehash: 7dd799b32d51c7e24e6717561aab549e7e7f1fbe
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69954003"
---
# <a name="ui-automation-tree-overview"></a>UI Otomasyon Ağacına Genel Bakış
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Yardımcı teknoloji ürünleri ve test betikleri, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] ve öğeleri hakkında bilgi toplamak için ağaca gider.  
  
 Ağacın içinde, geçerli masaüstünü temsil eden ve alt<xref:System.Windows.Automation.AutomationElement.RootElement%2A>öğeleri uygulama pencerelerini temsil eden bir kök öğe () vardır. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Bu alt öğelerin her biri, menüler, düğmeler, araç [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] çubukları ve liste kutuları gibi parçaları temsil eden öğeleri içerebilir. Sırasıyla bu öğeler, liste öğeleri gibi öğeler içerebilir.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağaç sabit bir yapı değildir ve binlerce öğe içerebileceğinden totality içinde nadiren görülmüştür. Bunların bölümleri, gerektiği gibi oluşturulur ve öğeler eklendikçe, taşındığında veya kaldırıldığında değişikliklere devam edebilir.  
  
 UI Otomasyon sağlayıcıları, bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] parçadan (genellikle bir pencerede barındırılan) ve bir alt ağaçta oluşan öğeler arasında gezinti gerçekleştirerek ağacı destekler. Ancak, sağlayıcılar bir denetimden diğerine gidilmesiyle ilgilenmez. Bu, varsayılan pencere sağlayıcılarındaki bilgiler kullanılarak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] çekirdek tarafından yönetilir.  
  
<a name="uiautomation_tree_view"></a>   
## <a name="views-of-the-automation-tree"></a>Otomasyon ağacının görünümleri  
 Ağaç yalnızca belirli bir istemci için ilgili nesneleriiçerengörünümleroluşturmaküzerefiltrelenebilir.<xref:System.Windows.Automation.AutomationElement> [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Bu yaklaşım, istemcilerin belirli gereksinimlerine göre sunulan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] yapıyı özelleştirmesini sağlar.  
  
 İstemci, görünümü özelleştirmeye ve filtrelemeye göre, görünümü özelleştirmenin iki yolu vardır. Kapsam, görünümün kapsamını bir temel öğeden başlayarak tanımlıyor: Örneğin, uygulama yalnızca masaüstünün doğrudan alt öğelerini veya bir uygulama penceresinin tüm alt öğelerini bulmak isteyebilir. Filtreleme, görünüme dahil edilecek öğe türlerini tanımlar.  
  
 UI Otomasyon sağlayıcıları, <xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty> ve <xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty> özellikleri dahil olmak üzere öğeler üzerinde Özellikler tanımlayarak filtrelemeyi destekler.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Üç varsayılan görünüm sağlar. Bu görünümler, gerçekleştirilen filtreleme türü tarafından tanımlanır; herhangi bir görünümün kapsamı uygulama tarafından tanımlanır. Ayrıca, uygulama özellikleri üzerinde başka filtreler de uygulayabilir; Örneğin, bir denetim görünümünde yalnızca etkin denetimleri dahil etmek için.  
  
<a name="uiautomation_raw_view"></a>   
### <a name="raw-view"></a>Ham görünüm  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağacın ham görünümü, masaüstünün kök olduğu <xref:System.Windows.Automation.AutomationElement> nesnelerin tam ağacıdır. Ham görünüm, bir uygulamanın yerel programlama yapısına yakından uyar ve bu nedenle, en ayrıntılı görünüm kullanılabilir. Ayrıca, ağacın diğer görünümlerinin oluşturulduğu temeldir. Bu görünüm temel alınan [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] çerçeveye bağlı olduğundan, bir [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] düğmenin ham görünümü bir [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] düğmeden farklı bir ham görünüme sahip olur.  
  
 Ham görünüm, özellikleri belirtmeden veya ağaçta gezinmek <xref:System.Windows.Automation.TreeWalker.RawViewWalker> için kullanarak öğeleri arayarak elde edilir.  
  
<a name="uiautomation_control_view"></a>   
### <a name="control-view"></a>Denetim görünümü  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağacın denetim görünümü, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] yardımcı teknoloji ürününün son kullanıcıya açıklanmasıyla ilgili görevi kolaylaştırır ve [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] yapıyla yakından eşlendiğinden son kullanıcının uygulamayla etkileşime girmesine yardımcı olur Son Kullanıcı tarafından algılanır.  
  
 Denetim görünümü ham görünümün bir alt kümesidir. Ham görünümden, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]son kullanıcının etkileşimli olarak anlayacağından ve içindeki denetimin mantıksal yapısına katkıda bulunduğu tüm öğeleri içerir. Öğesinin mantıksal yapısına [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]katkıda bulunan ancak etkileşimli olmayan öğeörnekleri,listegörünümüüstbilgileri,araççubukları,menülervedurumçubuğugibiöğekapsayıcılarıdır.[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] Yalnızca Düzen veya dekoratif amaçlar için kullanılan etkileşimli olmayan öğeler denetim görünümünde görünmez. Örneğin, yalnızca bir iletişim kutusundaki denetimleri düzenlemek için kullanılan, ancak kendisi herhangi bir bilgi içermeyen bir paneldir. Denetim görünümünde görünecek etkileşimli olmayan öğeler, iletişim kutusunda bilgi ve statik metin içeren grafiklerdir. Denetim görünümünde bulunan etkileşimli olmayan öğeler klavye odağı alamaz.  
  
 Denetim görünümü, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> özelliği olarak `true`ayarlanmış öğeleri arayarak veya ağaçta gezinmek <xref:System.Windows.Automation.TreeWalker.ControlViewWalker> için kullanılarak elde edilir.  
  
<a name="uiautomation_content_view"></a>   
### <a name="content-view"></a>İçerik görünümü  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağacın içerik görünümü Denetim görünümünün bir alt kümesidir. Klavye odağı [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] alabilen öğeler ve bir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğe üzerinde etiket olmayan bazı metinler de dahil [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] olmak üzere, Kullanıcı arabirimindeki gerçek bilgileri ileten öğeleri içerir. Örneğin, bir açılan Birleşik giriş kutusundaki değerler, bir son kullanıcı tarafından kullanılan bilgileri temsil ettiğinden içerik görünümünde görüntülenir. İçerik görünümünde, Birleşik giriş kutusu ve liste kutusu her ikisi de bir veya birden fazla öğenin seçilebileceği [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğelerin bir koleksiyonu olarak gösterilir. Birisi her zaman açıktır ve bir Kullanıcı, verileri veya içeriği göstermek üzere tasarlandığından, içerik görünümünde bir tane genişleyebilir ve daraltılır.  
  
 İçerik görünümü, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> özelliği olarak `true`ayarlanmış öğeleri arayarak veya ağaçta gezinmek <xref:System.Windows.Automation.TreeWalker.ContentViewWalker> için kullanılarak elde edilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.AutomationElement>
- [UI Otomasyonuna Genel Bakış](../../../docs/framework/ui-automation/ui-automation-overview.md)
