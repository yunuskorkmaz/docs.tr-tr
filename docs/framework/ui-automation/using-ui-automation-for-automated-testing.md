---
title: Otomatik Test İçin UI Otomasyonunu Kullanma
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- automated testing
- testing, UI Automation
- UI Automation, automated testing
ms.assetid: 3a0435c0-a791-4ad7-ba92-a4c1d1231fde
caps.latest.revision: 26
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: d38183d90e99c7b8b9b5ffabb871f13886d801f0
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="using-ui-automation-for-automated-testing"></a>Otomatik Test İçin UI Otomasyonunu Kullanma
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu genel bakış açıklanmaktadır nasıl [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] programlı erişim için bir çerçeve olarak yararlı de senaryolarınızı test otomatikleştirilebilir.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Tüm sağlayan bir birleşik nesne modeli sağlar [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] çerçeveleri karmaşık ve zengin işlevleri erişilebilir ve kolayca otomatik bir şekilde kullanıma sunma.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bir ardılı olarak geliştirilmiştir [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)]. [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] Varolan bir çerçeve denetimleri ve uygulamaları, erişilebilir yapmak için bir çözüm sağlamak için tasarlanmıştır. [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] Bu rol erişilebilirlik ve Otomasyon çok benzer gereksinimlerini nedeniyle içine gelişen olsa bile test Otomasyonu aklınızda ile tasarlanmamıştır. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], daha gelişmiş çözümleri için erişilebilirlik sağlamanın yanı sıra, özellikle de otomatikleştirilmiş test için sağlam işlevselliği sağlamak için tasarlanmıştır. Örneğin, [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] hem kullanıcı Arabirimi hakkında bilgi göstermek ve; ürünleri için gerekli bilgileri toplamak için tek bir arabirim kullanır [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] iki model ayırır.  
  
 Bir sağlayıcı ve istemci uygulamak için gereken [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] otomatikleştirilmiş test aracı olarak kullanışlı olması için. UI Otomasyon sağlayıcıları olan Microsoft Word, Excel gibi uygulamalar ve diğer üçüncü taraf uygulamalar veya denetimleri temel alarak [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)] işletim sistemi. UI Otomasyon istemcileri otomatikleştirilmiş test komut dosyaları ve yardımcı teknoloji uygulamalar içerir.  
  
> [!NOTE]
>  Yeni ve geliştirilmiş otomatik test özelliklerini göstermek için bu genel bakışta amacı olan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Bu genel bakışta, özellikleri ve erişilebilirlik dışında gerektiğinde ele almayacaktır erişilebilirlik hakkında bilgiler sağlamak üzere tasarlanmamıştır.  
  
<a name="Using_UI_Automation_During_Development"></a>   
## <a name="ui-automation-in-a-provider"></a>UI Otomasyon sağlayıcı  
 İçin bir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] otomatikleştirilmesi için bir geliştirici, uygulamanın veya denetim ne son kullanıcı bir eylemler gerçekleştirebileceğiniz en benzemelidir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] standart klavye ve fare etkileşimi kullanarak nesne.  
  
 Karşılık gelen eylemler belirlenmiştir, sonra bu anahtar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetim düzenleri (diğer bir deyişle, işlevsellik ve davranışını yansıtma denetim desenleri [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğesi) üzerinde denetim uygulanmalıdır. Örneğin, birleşik giriş kutusu denetimi (örneğin, çalışma iletişim) ile kullanıcı etkileşimi genellikle genişletme ve daraltma öğelerinin bir listesini görüntülemek veya gizlemek için birleşik giriş kutusu, bir öğe, listeden seçerek veya klavye girdisi aracılığıyla yeni bir değer ekleme içerir.  
  
> [!NOTE]
>  Diğer erişilebilirlik modellerde geliştiriciler bilgileri doğrudan düğmelerin, menüler veya diğer denetimleri toplamanız gerekir. Ne yazık ki, her denetim türü ikincil Çeşitlemeler düzinelerce içinde birlikte gelir. Bir basma düğmesi on varyasyonları tüm aynı şekilde çalışır ve aynı işlevi gerçekleştirir olsa bile, diğer bir deyişle, bunlar tüm benzersiz denetimleri olarak değerlendirilmesi gerekir. Bu denetimleri işlevsel olarak eşdeğerdir bilmenin bir yolu yoktur. Denetim desenleri, bu ortak denetim davranışları temsil etmek üzere geliştirilmiştir. Daha fazla bilgi için bkz: [UI Otomasyon denetim düzenlerine genel bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
<a name="Implementing_UI_Automation"></a>   
### <a name="implementing-ui-automation"></a>UI Otomasyonu uygulama  
 Tarafından sağlanan birleşik modeli olmadan daha önce belirtildiği gibi [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], test araçları ve geliştiricilerin özellikleri ve bu framework denetimlerinde davranışlarını kullanıma sunmak için framework özgü bilgileri bilmesi için gereklidir. Birçok farklı kullanıcı Arabirimi çerçevelerini tek herhangi bir zamanda Windows işletim sistemleri içinde mevcut olabilir beri dahil olmak üzere [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)], [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)], ve Windows Presentation Foundation (WPF) ile birden çok uygulama test etmek için zorlu bir görev olabilir benzerdir denetler. Örneğin, aşağıdaki tabloda bir düğme denetimi ile ilişkili adı (veya metin) almak için gereken çerçeveye özel özellik adları özetler ve tek eşdeğerini gösterir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özelliği.  
  
|UI Otomasyon denetim türü|UI çerçevesi|Framework belirli özelliği|UI Otomasyon özelliği|  
|--------------------------------|------------------|---------------------------------|----------------------------|  
|Düğme|Windows Presentation Foundation|İçerik|NameProperty|  
|Düğme|Win32|Başlık|NameProperty|  
|Görüntü|HTML|Alt|NameProperty|  
  
 UI Otomasyon sağlayıcıları kendi denetimleri çerçeveye özel özelliklerini eşdeğer eşlemek için sorumlu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri.  
  
 Uygulama konusunda bilgi [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sağlayıcı bulunabilir [yönetilen kod için UI Otomasyon sağlayıcılar](../../../docs/framework/ui-automation/ui-automation-providers-for-managed-code.md). Denetim desenleri uygulama hakkında daha fazla bilgi şu adreste [UI Otomasyon denetim düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns.md) ve [UI Otomasyon metin düzeni](../../../docs/framework/ui-automation/ui-automation-text-pattern.md).  
  
<a name="Testing_with_UI_Automation"></a>   
## <a name="ui-automation-in-a-client"></a>İstemci UI Otomasyonu  
 Birçok otomatikleştirilmiş test araçları ve senaryoları kullanıcı arabiriminin tutarlı ve tekrarlanabilir işleme hedefidir. Bu birim testi kaydetme ve kayıttan yürütme denetimleri birtakım genel Eylemler bir dizi yinelemek test komut dosyalarının belirli denetimlerde içerebilir.  
  
 Otomatik uygulamalardan ortaya olası bir test dinamik hedef eşitleme zorluk ' dir. Örneğin, bir Windows Görev Yöneticisi'nde yer alan gibi bir liste kutusu denetimi, şu anda çalışmakta olan uygulamalar listesini görüntüler. Liste kutusu öğeleri test uygulama denetimi dışında dinamik olarak güncelleştirilen olduğundan, belirli bir öğenin hiçbir tutarlılık liste kutusunda seçimi yineleyin çalışılıyor mümkün değildir. Benzer sorunları da ortaya çıkabilir basit odak değişiklikleri yineleyin çalışılırken bir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] test uygulama denetimi dışında olmasıdır.  
  
<a name="Programmatic_Access"></a>   
### <a name="programmatic-access"></a>Programlı erişim  
 Programlı erişim kodu, tüm etkileşim ve geleneksel fare ve klavye girdisi tarafından kullanıma sunulan deneyimi aracılığıyla taklit olanağı sağlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] beş bileşenleri aracılığıyla programlı erişim sağlar:  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağaç yapısını gezinmeyi kolaylaştırır [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Ağaç hWnd'ın koleksiyonundan yerleşik olarak bulunur. Daha fazla bilgi için bkz: [UI Otomasyon ağacına genel bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
  
-   Otomasyon öğeleridir bileşenleri tek tek [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Bunlar genellikle bir hWnd daha ayrıntılı olabilir. Daha fazla bilgi için bkz: [UI Otomasyon denetim türlerine genel bakış](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md).  
  
-   Otomasyon özellikleri hakkında ayrıntılı bilgi sağlamak [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğeleri. Daha fazla bilgi için bkz: [UI Otomasyon özelliklerine genel bakış](../../../docs/framework/ui-automation/ui-automation-properties-overview.md).  
  
-   Denetim desenleri belirli bir denetimin işlevselliği durumuyla tanımlayın; Bunlar, özellik, yöntem, olay ve yapı bilgileri oluşabilir. Daha fazla bilgi için bkz: [UI Otomasyon denetim düzenlerine genel bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
-   Otomasyon olayları olay bildirimleri ve bilgileri sağlayın. Daha fazla bilgi için bkz: [UI Otomasyonu olaylarına genel bakış](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
<a name="Key_properties_critical_to_test_automation"></a>   
### <a name="key-properties-for-test-automation"></a>Test otomasyonu için anahtar özellikler  
 Benzersiz şekilde tanımlamak ve daha sonra içinde herhangi bir denetimi bulun olanağı [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] üzerinde çalışması otomatikleştirilmiş test uygulamaları için temel sağlayan [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Birkaç yolu vardır [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] istemciler ve bu konuda yardımcı sağlayıcıları tarafından kullanılan özellik.  
  
#### <a name="automationid"></a>Automationıd  
 Eşdüzey bir Otomasyon öğeyi benzersiz olarak tanımlar. <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> , bir özellik gibi yerelleştirilmiş değil <xref:System.Windows.Automation.AutomationElement.NameProperty> , genellikle yerelleştirilmiş bir ürün birden fazla dilde sevk. Bkz: [Automationıd özelliğini kullanma](../../../docs/framework/ui-automation/use-the-automationid-property.md).  
  
> [!NOTE]
>  <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> Otomasyon ağacı genelinde benzersiz bir kimlik garanti etmez. Örneğin, bir uygulama olan, buna karşılık, birden çok alt menü öğesi birden çok üst düzey menü öğesi ile bir menü denetimi içerebilir. Bu ikincil menü öğeleri, "Item1, 2 öğesi, Item3, vb." gibi genel bir şema tarafından tanımlanan yinelenen tanımlayıcıları çocuklar için üst düzey menü öğeleri arasında izin verme.  
  
#### <a name="controltype"></a>ControlType  
 Bir Otomasyon öğesi tarafından temsil edilen denetim türünü tanımlar. Önemli bilgileri denetim türü bilgilerini çıkarsanabileceği. Bkz: [UI Otomasyon denetim türleri genel bakış](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md).  
  
#### <a name="nameproperty"></a>NameProperty  
 Bu tanımlayan veya bir denetim açıklayan bir metin dizesidir. <xref:System.Windows.Automation.AutomationElement.NameProperty> yerelleştirilmiş olabilir beri dikkatli kullanılmalıdır. Bkz: [UI Otomasyon özelliklerine genel bakış](../../../docs/framework/ui-automation/ui-automation-properties-overview.md).  
  
<a name="Steps_Required_To_Automate_the_UI_in_a_Test_Application"></a>   
### <a name="implementing-ui-automation-in-a-test-application"></a>UI Otomasyonu Test uygulamada uygulama  
  
|||  
|-|-|  
|UI Otomasyon başvurular ekleyin.|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] UI Otomasyon istemcileri burada listelenen için dll gerekli.<br /><br /> -UIAutomationClient.dll erişim sağlar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] istemci-tarafı API'leri.<br />-UIAutomationClientSideProvider.dll otomatik hale getirme olanağı sağlar [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] kontrol eder. Bkz: [standart denetimler için UI Otomasyon desteği](../../../docs/framework/ui-automation/ui-automation-support-for-standard-controls.md).<br />-UIAutomationTypes.dll tanımlanan belirli türleri için erişim sağlar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|  
|Ekleme <xref:System.Windows.Automation> ad alanı.|Bu ad özelliklerini kullanmak için UI Otomasyon istemcileri gereken her şeyi içeren [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] metin işleme dışında.|  
|Ekleme <xref:System.Windows.Automation.Text> ad alanı.|Bu ad özelliklerini kullanmak için UI Otomasyon istemcileri gerek her şeyi içeren [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] metin işleme.|  
|Denetimleri ilgi Bul|Otomatikleştirilmiş test komut Otomasyon ağaçtaki ilgi denetimleri temsil eden UI Otomasyon öğeleri bulun.<br /><br /> UI Otomasyon öğeleri arasında kod ile almak için birden çok yolu vardır.<br /><br /> -Sorgu [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] kullanarak bir <xref:System.Windows.Automation.Condition> deyimi. Bu genellikle burada dilden <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> kullanılır. **Not:** bir <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> belirtmek bulabildiği Inspect.exe gibi bir araç kullanılarak edinilebilir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bir denetimin özelliklerini. <br /><br /> -Kullanın <xref:System.Windows.Automation.TreeWalker> tüm çapraz geçiş için sınıf [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç veya bunların bir alt kümesi.<br />-Odağı izleme.<br />-Denetim hWnd kullanın.<br />-Ekran konumu, fare imlecini konum gibi kullanın.<br /><br /> Bkz: [UI Otomasyon öğelerini alma](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)|  
|Denetim desenleri alın|Denetim desenleri işlevsel olarak benzer denetimler için ortak davranışları ortaya çıkarır.<br /><br /> Sınama gerektiren denetimleri bulunduktan sonra otomatikleştirilmiş test komut dosyaları bu UI Otomasyon öğeleri ilgi denetim düzenleri edinin. Örneğin, <xref:System.Windows.Automation.InvokePattern> tipik düğme işlevleri için Denetim düzeni veya <xref:System.Windows.Automation.WindowPattern> pencere işlevleri için Denetim düzeni.<br /><br /> Bkz: [UI Otomasyon denetim düzenleri genel bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).|  
|Kullanıcı arabirimini otomatikleştirme|Otomatikleştirilmiş test komut dosyaları artık denetleyebilir herhangi [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] ilgi bir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] çerçevesi tarafından sunulan işlevselliği ve bilgi kullanılarak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetim düzenleri.|  
  
<a name="Supporting_tools"></a>   
## <a name="related-tools-and-technologies"></a>İlgili araçlar ve teknolojiler  
 Bir dizi ilgili araçlar ve ile otomatikleştirilmiş testleri destekleyen teknolojileri vardır [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
-   Inspect.exe olan bir [!INCLUDE[TLA#tla_gui](../../../includes/tlasharptla-gui-md.md)] toplamak için kullanılan uygulama [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sağlayıcısı ve istemci geliştirme ve hata ayıklama bilgileri. Inspect.exe dahil [!INCLUDE[TLA#tla_winfxsdk](../../../includes/tlasharptla-winfxsdk-md.md)].  
  
-   MSAABridge sunan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bilgileri [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] istemciler. Köprüleme birincil amacı [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] için [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] varolan izin [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] istemcileri uyguladı herhangi framework ile etkileşim becerisi [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
<a name="Security"></a>   
## <a name="security"></a>Güvenlik  
 Güvenlik bilgileri için bkz: [UI Otomasyon güvenliğine genel bakış](../../../docs/framework/ui-automation/ui-automation-security-overview.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UI Otomasyonu Temelleri](../../../docs/framework/ui-automation/index.md)
