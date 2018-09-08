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
ms.openlocfilehash: 042f3f82a88e987131145f38c1d8f5ecfa8dc487
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44179042"
---
# <a name="ui-automation-tree-overview"></a>UI Otomasyon Ağacına Genel Bakış
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Yardımcı teknoloji ürünlerinin ve test betikleri gidin [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hakkında bilgi toplamak için ağaç [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] ve alt öğeleri.  
  
 İçinde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç var olan bir kök öğe (<xref:System.Windows.Automation.AutomationElement.RootElement%2A>) temsil eden geçerli masaüstü ve windows uygulaması alt öğeleri temsil eder. Bu alt öğelerin her biri parçalarını temsil eden öğeler de içerebilen [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] menüler, düğmeler, araç çubukları ve liste kutuları gibi. Bu öğeler sırayla liste öğeleri gibi öğeler içerebilir.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağaç sabit bir yapı değildir ve öğeleri binlerce içerebileceğinden kendi katkılarının nadiren görülür. Bunlar gereklidir ve öğeleri eklendiğinde, taşınır veya kaldırılan değişiklikleri geçirilebilen bölümlerini oluşturulur.  
  
 UI Otomasyonu sağlayıcıları Destek [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] (genellikle bir pencere içinde barındırılan) bir kök ve alt ağacı oluşan bir parça içindeki öğeler arasında gezinmeyi uygulayarak ağaç. Ancak, sağlayıcı bir denetimden Gezinti ile ilgili değildir. Tarafından yönetilen bu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] varsayılan pencere sağlayıcıları bilgileri kullanarak, çekirdek.  
  
<a name="uiautomation_tree_view"></a>   
## <a name="views-of-the-automation-tree"></a>Otomasyon ağacı görünümleri  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağacı, yalnızca içeren görünümler oluşturmak amacıyla filtrelenebilir <xref:System.Windows.Automation.AutomationElement> nesneleri belirli bir istemci için ilgili. Bu yaklaşım aracılığıyla sunulan yapısı özelleştirmek istemcilerin [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kendi belirli gereksinimlerine.  
  
 İstemci görünümünü özelleştirme iki yolu vardır: kapsam ve filtreleme. Kapsam görünümü temel öğesinden başlayarak kapsamını tanımlama olan: Örneğin, uygulama yalnızca doğrudan alt öğeleri Masaüstü veya bir uygulama penceresinin tüm alt öğeleri bulmak isteyebilirsiniz. Filtre Görünümü'nde dahil edilecek öğeleri türlerini tanımlamaktır.  
  
 UI Otomasyonu sağlayıcıları desteği dahil olmak üzere öğelerde özellikleri tanımlayarak filtreleme <xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty> ve <xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty> özellikleri.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] üç varsayılan görünüm sağlar. Bu görünümler, gerçekleştirilen filtre türünü tarafından tanımlanır; herhangi bir görünümün kapsamını, uygulama tarafından tanımlanır. Ayrıca, uygulama özellikleri diğer filtreler uygulayabilirsiniz; Örneğin, yalnızca dahil etmek için bir denetim görünümünde denetimleri etkin.  
  
<a name="uiautomation_raw_view"></a>   
### <a name="raw-view"></a>Ham görüntüle  
 İşlenmemiş bir görünümünü [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacıdır tam ağacının <xref:System.Windows.Automation.AutomationElement> desktop, kök nesneleri. Ham görünümünün bir uygulamanın yerel programlı yapısını yakından takip eder ve bu nedenle en ayrıntılı görünümde kullanılabilir. Ayrıca bir ağaç görünümlerini yerleşik olan temel bir hizmettir. Bu görünüm, altta yatan bağlı olduğundan [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] framework, işlenmemiş bir görünümünü bir [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] düğmesi değerinden farklı bir ham görünüme sahip olacak bir [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] düğmesi.  
  
 Ham görünümünün özellikleri belirtmeden öğeler için arama veya kullanılarak elde edilen <xref:System.Windows.Automation.TreeWalker.RawViewWalker> ağaç gidin.  
  
<a name="uiautomation_control_view"></a>   
### <a name="control-view"></a>Denetim Görünüm  
 Denetimin görünümünü [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç açıklayan yardımcı teknolojik ürün görevini basitleştirir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] yardımcı ve son kullanıcı, son kullanıcı yakından eşlenir olduğundan, uygulamayla etkileşim [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] yapısı bir son kullanıcı tarafından algılanır.  
  
 Denetim görünüm ham görünümünün bir alt kümesidir. Tüm içeren [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] son kullanıcı olarak etkileşimli veya katkıda bulunan denetiminde mantıksal yapısı için öğrenmesi ham görünümünün öğelerinden [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Örnekleri [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] mantıksal yapısını katkıda bulunan öğeleri [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], ancak kendisi etkileşimli değildir, liste görünümü üst bilgiler, araç çubukları, menüler ve durum çubuğu gibi öğesi kapsayıcılardır. Etkileşimli olmayan öğeleri sadece düzeni veya dekoratif amaçlı kullanılan denetim görünümünde görünmez. Yalnızca bir iletişim kutusu denetimleri düzenlemek için kullanılan bir panel örneğidir ancak kendisi herhangi bir bilgi içermiyor. Denetim görünümünde görülür etkileşimsiz öğeler, bilgi ve iletişim kutusunda statik metin grafiklerdir. Denetim görünümünde bulunan etkileşimsiz öğeler klavye odağı alamıyor.  
  
 Denetim görünümü olan öğeler için arama yaparak elde edilen <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> özelliğini `true`, veya kullanarak <xref:System.Windows.Automation.TreeWalker.ControlViewWalker> ağaç gidin.  
  
<a name="uiautomation_content_view"></a>   
### <a name="content-view"></a>İçerik görünümü  
 İçerik görünümü [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç görünümü denetimi özelliklerinin bir alt kümesidir. İçerdiği [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] kullanıcı arabiriminde true bilgi ileten öğeleri dahil olmak üzere [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] alabilir öğeleri klavye odağı ve bir etiket değil metin bir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğesi. Örneğin, bir son kullanıcı tarafından kullanılan bilgileri temsil ettikleri çünkü değerlerin açılan kutusunda içerik Görünümü'nde görünür. İçerik görünümünde bir birleşik giriş kutusu ve liste kutusu hem de koleksiyonu olarak temsil edilir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğeleri burada aşağıdakilerden birini veya belki de birden fazla öğe seçilebilir. Her zaman açık biridir ve bir genişletebileceğiniz ve daraltabileceğiniz olgu verileri göstermek için tasarlanmıştır ve içerik, kullanıcıya sunulmaktadır içerik Görünümü'nde ilgisiz olmasıdır.  
  
 Olan öğeler için arama yaparak içerik görünümü elde <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> özelliğini `true`, kullanarak veya <xref:System.Windows.Automation.TreeWalker.ContentViewWalker> ağaç gidin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Automation.AutomationElement>  
 [UI Otomasyonuna Genel Bakış](../../../docs/framework/ui-automation/ui-automation-overview.md)
