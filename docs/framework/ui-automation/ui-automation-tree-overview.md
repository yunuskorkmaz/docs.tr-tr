---
title: UI Otomasyon Ağacına Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- automation tree
- UI Automation, tree
ms.assetid: 03b98058-bdb3-47a0-8ff7-45e6cdf67166
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 0823a569b19d46f32c1cb780470a935f20429c11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33409129"
---
# <a name="ui-automation-tree-overview"></a>UI Otomasyon Ağacına Genel Bakış
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Yardımcı teknoloji ürünlerinin ve test betikleri gidin [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hakkında bilgi toplamak için ağacı [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] ve öğeleri.  
  
 İçinde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç var olan bir kök öğe (<xref:System.Windows.Automation.AutomationElement.RootElement%2A>) geçerli masaüstü temsil eden ve alt öğeleri uygulama windows temsil eder. Bu alt öğelerin her birini parçalarını temsil eden öğeleri içerebilir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] menüleri, düğmeleri, araç çubukları ve liste kutuları gibi. Bu öğeleri sırayla liste öğeleri gibi öğeleri içerebilir.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağaç sabit bir yapı değil ve kendi totality öğeleri binlerce içerebileceğinden ender görülür. Bazı bölümleri gerekli değildir ve öğeleri eklendiğinde, taşınmış veya kaldırılmış değişiklikleri uygulayabilir olarak oluşturulur.  
  
 UI Otomasyon sağlayıcılar Destek [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] (genellikle bir pencerede barındırılan) bir kök ve bir alt ağacı oluşan bir parça içindeki öğeler arasında gezinmeyi uygulayarak ağacı. Ancak, sağlayıcı bir denetimden gezinme ile ilgili değildir. Tarafından yönetilen bu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] çekirdek, varsayılan pencere sağlayıcılardan gelen bilgileri kullanarak.  
  
<a name="uiautomation_tree_view"></a>   
## <a name="views-of-the-automation-tree"></a>Otomasyon ağacı görünümü  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağaç filtre yalnızca içeren görünümleri oluşturmak için <xref:System.Windows.Automation.AutomationElement> nesneleri belirli bir istemci için ilgili. Bu yaklaşım aracılığıyla sunulan yapısı özelleştirmek istemcilerin [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] belirli gereksinimlerine için.  
  
 İstemci görünümü özelleştirme iki yolu vardır: kapsamı ve filtreleme. Kapsamı bir temel öğesinden başlayarak görünüm kapsamını tanımlama olduğu: Örneğin, uygulama sadece doğrudan alt masaüstü veya bir uygulama penceresi tüm bağımlı öğelerini bulma isteyebilirsiniz. Filtreleme görünümünde dahil edilecek öğeleri türlerini tanımlama.  
  
 UI Otomasyon sağlayıcıları desteği dahil olmak üzere öğelerde özelliklerini tanımlayarak filtreleme <xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty> ve <xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty> özellikleri.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] üç varsayılan görünüm sağlar. Bu görünümler gerçekleştirilen Filtreleme türü tarafından tanımlanan; herhangi bir görünüm kapsamını uygulama tarafından tanımlanır. Ayrıca, uygulama özellikleri diğer filtreler uygulayabilirsiniz; Örneğin, yalnızca dahil etmek için bir denetim görünümünde denetimleri etkin.  
  
<a name="uiautomation_raw_view"></a>   
### <a name="raw-view"></a>Ham görünümü  
 Ham görünümünü [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacıdır tam ağacının <xref:System.Windows.Automation.AutomationElement> Masaüstü, kök nesneleri. Ham görünüm yakından bir uygulamanın yerel programlı yapısını izler ve bu nedenle en ayrıntılı görünümü kullanılabilir. Bunu ayrıca bir ağaç görünümlerini yerleşik olan tabanıdır. Bu görünüm, altta yatan bağımlı olduğundan [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] framework, ham görünümünü bir [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] düğmesi daha farklı bir ham görünüm sahip olacak bir [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] düğmesi.  
  
 Ham Görünüm Özellikleri belirtmeden öğeleri arıyor veya kullanılarak elde edilen <xref:System.Windows.Automation.TreeWalker.RawViewWalker> ağaç gidin.  
  
<a name="uiautomation_control_view"></a>   
### <a name="control-view"></a>Denetim Görünüm  
 Denetim görünümünü [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç açıklayan yardımcı teknoloji ürünün görevini basitleştirir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] yardımcı olma ve son kullanıcı, son kullanıcı yakından eşlendiği olduğundan, uygulama ile etkileşim [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] yapısı bir son kullanıcı tarafından algılanır.  
  
 Denetim görünüm ham görünüm alt kümesidir. Tüm içeren [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] bir son kullanıcı olarak etkileşimli veya katkıda bulunan denetiminde mantıksal yapısına öğrenmesi ham görünümünden öğeleri [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Örnekleri [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] mantıksal yapısını katkıda öğeleri [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], ancak kendilerini etkileşimli olmayan, liste görünümü üstbilgileri, araç çubukları, menüler ve durum çubuğu gibi öğesi kapsayıcılardır. Basit düzeni veya dekoratif amaçları için kullanılan etkileşimli olmayan öğeler Denetim görünümünde görünmez. Yalnızca bir iletişim kutusu denetimleri düzenlemek için kullanılan bir panel örneğidir ancak kendisi herhangi bir bilgi içermiyor. Denetim görünümünde görülen etkileşimli olmayan öğeler grafik bilgileri ve statik metne bir iletişim kutusu görüntülenir. Denetim görünümünde bulunan etkileşimli olmayan öğeler klavye odağı alamıyor.  
  
 Denetim görünüm olan öğeler için arama yaparak elde edilir <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> özelliğini `true`, veya kullanarak <xref:System.Windows.Automation.TreeWalker.ControlViewWalker> ağaç gidin.  
  
<a name="uiautomation_content_view"></a>   
### <a name="content-view"></a>İçerik görünümü  
 İçerik görünümünü [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç denetimi görünümünün bir alt kümesidir. İçerdiği [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] kullanıcı arabiriminde true bilgi ileten öğeler de dahil olmak üzere [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] alabilir öğeleri klavye odağı ve etiket üzerinde değil bazı metinleri bir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğesi. Örneğin, bir son kullanıcı tarafından kullanılan bilgileri gösterdiğinden açılan kutusunda değerleri içerik görünümünde görünür. İçerik görünümünde, bir birleşik giriş kutusu ve liste kutusu hem de koleksiyonu olarak temsil edilir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğeleri burada birini veya belki de birden çok öğe seçilebilir. Her zaman açık biridir ve bir genişletme ve daraltma olgu verileri göstermek için tasarlanan veya içeriği, kullanıcıya sunulan içerik görünümünde ilgisiz nedeni.  
  
 İçerik görünümü olan öğeler için arama yaparak elde <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> özelliğini `true`, veya kullanarak <xref:System.Windows.Automation.TreeWalker.ContentViewWalker> ağaç gidin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Automation.AutomationElement>  
 [UI Otomasyonuna Genel Bakış](../../../docs/framework/ui-automation/ui-automation-overview.md)
