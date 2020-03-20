---
title: UI Otomasyon Ağacına Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- automation tree
- UI Automation, tree
ms.assetid: 03b98058-bdb3-47a0-8ff7-45e6cdf67166
ms.openlocfilehash: a0b888e8ecc80e3739c583931a86da3cdb7242d1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179448"
---
# <a name="ui-automation-tree-overview"></a>UI Otomasyon Ağacına Genel Bakış
> [!NOTE]
> Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır. Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Yardımcı teknoloji ürünleri ve test komut [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dosyaları, ağaç [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] ve öğeleri hakkında bilgi toplamak için ağaçta gezinir.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağacın içinde geçerli masaüstünü<xref:System.Windows.Automation.AutomationElement.RootElement%2A>temsil eden ve alt öğeleri uygulama pencerelerini temsil eden bir kök öğesi ( ) vardır. Bu alt öğelerin her biri menüler, düğmeler, araç çubukları ve liste kutuları [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] gibi parçaları temsil eden öğeler içerebilir. Bu öğeler sırayla liste öğeleri gibi öğeleri içerebilir.  
  
 Ağaç [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sabit bir yapı değildir ve binlerce öğe içerebileceğinden, nadiren bütünlük içinde görülür. Parçaları gerektiği gibi inşa edilir ve öğeler eklendikçe, taşındıkça veya kaldırıldıkça değişikliklere uğrayabilir.  
  
 UI Otomasyon sağlayıcıları, bir kök (genellikle bir pencerede barındırılan) ve bir alt ağaçtan oluşan bir parça içindeki öğeler arasında gezinme uygulayarak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı destekler. Ancak, sağlayıcılar bir denetimden diğerine gezinme ile ilgili değildir. Bu, varsayılan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pencere sağlayıcılarından gelen bilgiler kullanılarak çekirdek tarafından yönetilir.  
  
<a name="uiautomation_tree_view"></a>
## <a name="views-of-the-automation-tree"></a>Otomasyon Ağacının Görünümleri  
 Ağaç, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] yalnızca belirli bir istemci yle <xref:System.Windows.Automation.AutomationElement> ilgili nesneleri içeren görünümler oluşturmak için filtrelenebilir. Bu yaklaşım, istemcilerin kendi özel [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ihtiyaçlarına aracılığıyla sunulan yapıözelleştirmek için izin verir.  
  
 İstemcinin görünümü özelleştirmenin iki yolu vardır: kapsam alet ederek ve filtreleyerek. Kapsam, temel öğeden başlayarak görünümün kapsamını tanımlıyor: örneğin, uygulama yalnızca masaüstünün doğrudan çocuklarını veya bir uygulama penceresinin tüm torunlarını bulmak isteyebilir. Filtreleme, görünüme eklenecek öğe türlerini tanımlar.  
  
 UI Automation sağlayıcıları, özellikler ve <xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty> <xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty> özellikler de dahil olmak üzere öğeler üzerindeki özellikleri tanımlayarak filtrelemeyi destekler.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]üç varsayılan görünüm sağlar. Bu görünümler, gerçekleştirilen filtreleme türüne göre tanımlanır; herhangi bir görünümün kapsamı uygulama tarafından tanımlanır. Buna ek olarak, uygulama özellikleri diğer filtreler uygulayabilirsiniz; örneğin, yalnızca etkin denetimleri bir denetim görünümüne eklemek için.  
  
<a name="uiautomation_raw_view"></a>
### <a name="raw-view"></a>Ham Görünüm  
 Ağacın ham görünümü, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] masaüstünün kök <xref:System.Windows.Automation.AutomationElement> olduğu nesnelerin tam ağacıdır. Ham görünüm, bir uygulamanın yerel programlı yapısını yakından izler ve bu nedenle mevcut en ayrıntılı görünümdür. Aynı zamanda ağacın diğer görünümlerinin inşa edildiği tabandır. Bu görünüm temel [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] çerçeveye bağlı olduğundan, bir [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] düğmenin ham görünümü Win32 düğmesinden farklı bir ham görünüme sahip olacaktır.  
  
 Ham görünüm özellikleri belirtmeden öğeleri arayarak veya ağaç <xref:System.Windows.Automation.TreeWalker.RawViewWalker> gezinmek için kullanarak elde edilir.  
  
<a name="uiautomation_control_view"></a>
### <a name="control-view"></a>Kontrol Görünümü  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağacın denetim görünümü, yardımcı teknoloji ürünü görevini, son kullanıcıyı [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] son kullanıcıya açıklama ve son kullanıcı tarafından algılanan [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] yapıyla yakından eşleştiğinden, son kullanıcının uygulamayla etkileşime geçmesine yardımcı etme görevini basitleştirir.  
  
 Denetim görünümü ham görünümün bir alt kümesidir. Bir son [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] kullanıcının etkileşimli olarak anlayacağı veya denetimin mantıksal yapısına katkıda bulunacağı ham görünümdeki tüm öğeleri [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]içerir. ,'ın mantıksal yapısına katkıda bulunan ancak etkileşimli olmayan [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğelere örnekler, liste görünümü üstbilgi, araç çubukları, menüler ve durum çubuğu gibi öğe kapsayıcılarıdır. [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] Yalnızca düzen veya dekoratif amaçlar için kullanılan etkileşimli olmayan öğeler denetim görünümünde görülmez. Bir örnek, yalnızca denetimleri bir iletişim kutusunda düzenlemek için kullanılan ancak kendisi herhangi bir bilgi içermeyen bir paneldir. Denetim görünümünde görülecek etkileşimli olmayan öğeler, iletişim kutusunda bilgi ve statik metin içeren grafiklerdir. Denetim görünümünde bulunan etkileşimli olmayan öğeler klavye odağı alamaz.  
  
 Denetim görünümü, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> özelliği ayarlanan `true`öğeler in aranması veya ağaçta <xref:System.Windows.Automation.TreeWalker.ControlViewWalker> gezinmek için kullanılmasıyla elde edilir.  
  
<a name="uiautomation_content_view"></a>
### <a name="content-view"></a>İçerik Görünümü  
 Ağacın içerik görünümü, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetim görünümünün bir alt kümesidir. Klavye [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] odağı alabilen [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğeler ve [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğe üzerinde etiket olmayan bazı metinler de dahil olmak üzere, kullanıcı arabirimindeki doğru bilgileri ileten öğeler içerir. Örneğin, açılır açılan kutudaki değerler, son kullanıcı tarafından kullanılan bilgileri temsil ettiği için içerik görünümünde görünür. İçerik görünümünde, açılan kutu ve liste kutusu, bir veya [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] belki de birden fazla öğenin seçilebileceği öğelertopluluğu olarak temsil edilir. Kullanıcıya sunulan verileri veya içeriği göstermek üzere tasarlandıklarından, kişinin her zaman açık olması ve genişletilip daraltılması içerik görünümünde önemsizdir.  
  
 İçerik görünümü, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> özelliği ayarlanmış `true`öğeler in aranarak veya ağaçta <xref:System.Windows.Automation.TreeWalker.ContentViewWalker> gezinmek için kullanılarak elde edilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.AutomationElement>
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
