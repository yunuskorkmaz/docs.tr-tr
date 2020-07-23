---
title: UI Otomasyon Ağacına Genel Bakış
description: UI Otomasyon ağaçları hakkında genel bakışı okuyun. Ham görünüm, denetim görünümü ve içerik görünümü gibi bir UI Otomasyon ağacının farklı görünümleri hakkında bilgi edinin.
ms.date: 03/30/2017
helpviewer_keywords:
- automation tree
- UI Automation, tree
ms.assetid: 03b98058-bdb3-47a0-8ff7-45e6cdf67166
ms.openlocfilehash: 0ffe4b4e6157f5bff3284d6978e0ec28641cf72d
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86924558"
---
# <a name="ui-automation-tree-overview"></a>UI Otomasyon Ağacına Genel Bakış
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Yardımcı teknoloji ürünleri ve test betikleri, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ve öğeleri hakkında bilgi toplamak için ağaca gider [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] .  
  
 Ağacın içinde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , <xref:System.Windows.Automation.AutomationElement.RootElement%2A> geçerli masaüstünü temsil eden ve alt öğeleri uygulama pencerelerini temsil eden bir kök öğe () vardır. Bu alt öğelerin her biri, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] Menüler, düğmeler, araç çubukları ve liste kutuları gibi parçaları temsil eden öğeleri içerebilir. Sırasıyla bu öğeler, liste öğeleri gibi öğeler içerebilir.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Ağaç sabit bir yapı değildir ve binlerce öğe içerebileceğinden totality içinde nadiren görülmüştür. Bunların bölümleri, gerektiği gibi oluşturulur ve öğeler eklendikçe, taşındığında veya kaldırıldığında değişikliklere devam edebilir.  
  
 UI Otomasyon sağlayıcıları, bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] parçadan (genellikle bir pencerede barındırılan) ve bir alt ağaçta oluşan öğeler arasında gezinti gerçekleştirerek ağacı destekler. Ancak, sağlayıcılar bir denetimden diğerine gidilmesiyle ilgilenmez. Bu, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] varsayılan pencere sağlayıcılarındaki bilgiler kullanılarak çekirdek tarafından yönetilir.  
  
<a name="uiautomation_tree_view"></a>
## <a name="views-of-the-automation-tree"></a>Otomasyon ağacının görünümleri  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Ağaç yalnızca <xref:System.Windows.Automation.AutomationElement> belirli bir istemci için ilgili nesneleri içeren görünümler oluşturmak üzere filtrelenebilir. Bu yaklaşım, istemcilerin belirli gereksinimlerine göre sunulan yapıyı özelleştirmesini sağlar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .  
  
 İstemci, görünümü özelleştirmeye ve filtrelemeye göre, görünümü özelleştirmenin iki yolu vardır. Kapsam, görünümün kapsamını bir temel öğeden başlayarak tanımlıyor: Örneğin, uygulama yalnızca masaüstünün doğrudan alt öğelerini veya bir uygulama penceresinin tüm alt öğelerini bulmak isteyebilir. Filtreleme, görünüme dahil edilecek öğe türlerini tanımlar.  
  
 UI Otomasyon sağlayıcıları, ve özellikleri dahil olmak üzere öğeler üzerinde Özellikler tanımlayarak filtrelemeyi destekler <xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty> <xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty> .  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Üç varsayılan görünüm sağlar. Bu görünümler, gerçekleştirilen filtreleme türü tarafından tanımlanır; herhangi bir görünümün kapsamı uygulama tarafından tanımlanır. Ayrıca, uygulama özellikleri üzerinde başka filtreler de uygulayabilir; Örneğin, bir denetim görünümünde yalnızca etkin denetimleri dahil etmek için.  
  
<a name="uiautomation_raw_view"></a>
### <a name="raw-view"></a>Ham görünüm  
 Ağacın ham görünümü, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation.AutomationElement> masaüstünün kök olduğu nesnelerin tam ağacıdır. Ham görünüm, bir uygulamanın yerel programlama yapısına yakından uyar ve bu nedenle, en ayrıntılı görünüm kullanılabilir. Ayrıca, ağacın diğer görünümlerinin oluşturulduğu temeldir. Bu görünüm temel alınan çerçeveye bağlı olduğundan [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] , bir düğmenin ham görünümü bir [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] Win32 düğmesine göre farklı bir ham görünüme sahip olur.  
  
 Ham görünüm, özellikleri belirtmeden veya ağaçta gezinmek için kullanarak öğeleri arayarak elde edilir <xref:System.Windows.Automation.TreeWalker.RawViewWalker> .  
  
<a name="uiautomation_control_view"></a>
### <a name="control-view"></a>Denetim görünümü  
 Ağacın denetim görünümü [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , bir son kullanıcı [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] tarafından algılanan yapıyla yakından eşlendiğinden, yardımcı teknoloji ürününün son kullanıcıya açıklanmasına ve son kullanıcının uygulamayla etkileşime girmesine yardımcı olan görevi basitleştirir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] .  
  
 Denetim görünümü ham görünümün bir alt kümesidir. [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]Ham görünümden, son kullanıcının etkileşimli olarak anlayacağından ve içindeki denetimin mantıksal yapısına katkıda bulunduğu tüm öğeleri içerir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] . Öğesinin [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] mantıksal yapısına katkıda bulunan [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] ancak etkileşimli olmayan öğe örnekleri, liste görünümü üstbilgileri, araç çubukları, menüler ve durum çubuğu gibi öğe kapsayıcılarıdır. Yalnızca Düzen veya dekoratif amaçlar için kullanılan etkileşimli olmayan öğeler denetim görünümünde görünmez. Örneğin, yalnızca bir iletişim kutusundaki denetimleri düzenlemek için kullanılan, ancak kendisi herhangi bir bilgi içermeyen bir paneldir. Denetim görünümünde görünecek etkileşimli olmayan öğeler, iletişim kutusunda bilgi ve statik metin içeren grafiklerdir. Denetim görünümünde bulunan etkileşimli olmayan öğeler klavye odağı alamaz.  
  
 Denetim görünümü, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> özelliği olarak ayarlanmış öğeleri arayarak `true` veya <xref:System.Windows.Automation.TreeWalker.ControlViewWalker> ağaçta gezinmek için kullanılarak elde edilir.  
  
<a name="uiautomation_content_view"></a>
### <a name="content-view"></a>İçerik görünümü  
 Ağacın içerik görünümü [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Denetim görünümünün bir alt kümesidir. [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] Klavye odağı alabilen öğeler ve bir öğe üzerinde etiket olmayan bazı metinler de dahil olmak üzere, Kullanıcı arabirimindeki gerçek bilgileri ileten öğeleri içerir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] . Örneğin, bir açılan Birleşik giriş kutusundaki değerler, bir son kullanıcı tarafından kullanılan bilgileri temsil ettiğinden içerik görünümünde görüntülenir. İçerik görünümünde, Birleşik giriş kutusu ve liste kutusu her ikisi de [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] bir veya birden fazla öğenin seçilebileceği öğelerin bir koleksiyonu olarak gösterilir. Birisi her zaman açıktır ve bir Kullanıcı, verileri veya içeriği göstermek üzere tasarlandığından, içerik görünümünde bir tane genişleyebilir ve daraltılır.  
  
 İçerik görünümü, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> özelliği olarak ayarlanmış öğeleri arayarak `true` veya <xref:System.Windows.Automation.TreeWalker.ContentViewWalker> ağaçta gezinmek için kullanılarak elde edilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.AutomationElement>
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
