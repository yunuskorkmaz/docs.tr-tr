---
title: Otomatik Test İçin UI Otomasyonunu Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- automated testing
- testing, UI Automation
- UI Automation, automated testing
ms.assetid: 3a0435c0-a791-4ad7-ba92-a4c1d1231fde
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 2fe3d511b92ff055e80999fa498c24a44f771ebf
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43457011"
---
# <a name="using-ui-automation-for-automated-testing"></a>Otomatik Test İçin UI Otomasyonunu Kullanma
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu genel bakış açıklar nasıl [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] programlı erişim için bir çerçeve olarak yararlı de testi senaryoları otomatik hale getirilebilir.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Tüm sağlayan bir birleşik nesne modeli sağlar [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] çerçeveleri karmaşık ve zengin işlevleri erişilebilir ve kolayca otomatik bir şekilde kullanıma sunma.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] için bir ardıl olarak geliştirilmiştir [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)]. [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] Mevcut bir çerçeve denetimleri ve uygulamaları erişilebilir yapmak için bir çözüm sağlamak için tasarlanmıştır. [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] Erişilebilirlik ve Otomasyon çok benzer gereksinimleri nedeniyle bu rolü içinde gelişerek olsa bile aklınızda test Otomasyonu ile tasarlanmamıştır. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], daha iyi çözümler için erişilebilirlik sağlamanın yanı sıra da özellikle otomatik test için sağlam işlevselliği sağlamak için tasarlanmıştır. Örneğin, [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] hem kullanıcı Arabirimi hakkında bilgilerin açığa çıkmasına neden hem de; ürünler için gerekli bilgileri toplamak için tek bir arabirim kullanır [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] iki model ayırır.  
  
 Hem sağlayıcı hem de istemci uygulamak için gereken [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bir otomatik test aracı olarak kullanışlı olması için. UI Otomasyonu sağlayıcıları, Microsoft Word, Excel, gibi uygulama ve diğer üçüncü taraf uygulamaların ve denetimlerin temel alarak [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)] işletim sistemi. UI Otomasyon istemcileri, otomatik test betikleri ve yardımcı teknoloji uygulamalar içerir.  
  
> [!NOTE]
>  Yeni ve geliştirilmiş otomatik test özelliklerini göstermek için bu genel bakışta amacı olan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Bu genel bakışta, özellikler ve erişilebilirlik dışında gerektiğinde gidermeyeceğini erişilebilirlik hakkında bilgiler sağlamak için tasarlanmamıştır.  
  
<a name="Using_UI_Automation_During_Development"></a>   
## <a name="ui-automation-in-a-provider"></a>UI Otomasyon sağlayıcı  
 İçin bir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] otomatikleştirilmesi için bir geliştirici bir uygulama veya denetimin ne bir son kullanıcının eylemleri gerçekleştirdiklerinden adresindeki benzemelidir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] standart klavye ve fare etkileşimi kullanarak nesne.  
  
 Karşılık gelen eylemleri belirlenmiştir, sonra bu anahtar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetim desenleri (diğer bir deyişle, davranışlarını ve işlevlerinin yansıtma denetim düzenleri [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğesi) denetimi uygulanmalıdır. Örneğin, kullanıcı etkileşimi bir birleşik giriş kutusu denetimi (örneğin, çalışma iletişim) ile genellikle genişletme ve daraltma öğelerinin listesini görüntülemek veya gizlemek için birleşik giriş kutusu, bu listeden bir öğeyi seçtikten veya klavye girdisi aracılığıyla yeni bir değer eklemeyi içerir.  
  
> [!NOTE]
>  Diğer erişilebilirlik modelleriyle, geliştiricilerin bilgi doğrudan bireysel düğmeler, menüler veya diğer denetimleri toplamanız gerekir. Ne yazık ki, her denetim türü küçük farklılıklar onlarca içinde sunulur. Bir basma düğmesi on çeşitleri tümü aynı şekilde çalışır ve aynı işlevi gerçekleştirir olsa bile, diğer bir deyişle, bunlar tüm benzersiz denetim değerlendirilmesi gerekir. Bu denetimlerin işlevsel olarak eşdeğer olduğunu bilmek hiçbir yolu yoktur. Denetim düzenleri, bu ortak denetim davranışlarını temsil etmek üzere geliştirilmiştir. Daha fazla bilgi için [UI Otomasyon denetim düzenlerine genel bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
<a name="Implementing_UI_Automation"></a>   
### <a name="implementing-ui-automation"></a>UI Otomasyonu uygulama  
 Tarafından sağlanan bir birleşik modele olmadan daha önce belirtildiği gibi [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], çerçeveye özgü bilgileri özellikler ve davranışlar, Framework denetimlerin kullanıma sunmak için yerinizi bilmesi için test araçları ve geliştiricilerin gereklidir. Birkaç farklı UI çerçeveleri tek herhangi bir zamanda Windows işletim sistemleri içinde mevcut olabileceği gibi [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)], [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)], ve Windows Presentation Foundation (WPF), birden çok uygulama ile test etmek için göreve göz korkutucu olabilir Bu denetimler benzerdir. Örneğin, aşağıdaki tabloda bir düğme denetimi ile ilişkili adı (veya metin) almak için gereken çerçeveye özgü özellik adlarını özetler ve tek eşdeğer gösterir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özelliği.  
  
|UI Otomasyon denetim türü|UI çerçevesi|Framework belirli özellik|UI Otomasyon özelliği|  
|--------------------------------|------------------|---------------------------------|----------------------------|  
|Düğme|Windows Presentation Foundation|İçerik|NameProperty|  
|Düğme|Win32|Başlık|NameProperty|  
|Görüntü|HTML|Alt|NameProperty|  
  
 UI Otomasyonu sağlayıcıları denetimlerini çerçeveye özgü özelliklerini eşdeğer eşlemek için sorumlu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri.  
  
 Uygulama konusunda bilgi [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sağlayıcı şu yolda bulunabilir: [yönetilen kod için UI Otomasyon sağlayıcılar](../../../docs/framework/ui-automation/ui-automation-providers-for-managed-code.md). Denetim desenlerini uygulama konusunda bilgi şu adreste [UI Otomasyon denetim düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns.md) ve [UI Otomasyonu metin deseni](../../../docs/framework/ui-automation/ui-automation-text-pattern.md).  
  
<a name="Testing_with_UI_Automation"></a>   
## <a name="ui-automation-in-a-client"></a>UI Otomasyonu istemcisinde  
 Birçok otomatikleştirilmiş test araçları ve senaryoları kullanıcı arabiriminin tutarlı ve tekrarlanabilir düzenlenmesini hedeftir. Bu, birim testi kaydetme ve kayıttan yürütme Denetim grubunun genel Eylemler bir dizi aracılığıyla yineleme test betikleri aracılığıyla belirli denetimler içerebilir.  
  
 Otomatik uygulamalardan ortaya bir karmaşıklık dinamik hedef test eşitleme zorluk ' dir. Örneğin, bir Windows Görev Yöneticisi'nde yer alan gibi bir liste kutusu denetimini, çalışmakta olan uygulamaların bir listesini görüntüler. Öğeleri liste kutusunda test uygulama denetimi dışında dinamik olarak güncelleştirilen bu yana, belirli bir öğeyi liste kutusunda tüm tutarlılık seçimini yineleyin çalışılıyor mümkün değildir. Benzer sorunlar da çıkabilir basit odak değişiklikleri yinelemek çalışırken bir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] test uygulama denetimi dışında olmasıdır.  
  
<a name="Programmatic_Access"></a>   
### <a name="programmatic-access"></a>Programlı erişim  
 Programlı erişim, kod, etkileşim ve geleneksel fare ve klavye tarafından kullanıma sunulan deneyimi aracılığıyla taklit olanağı sağlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] beş bileşene aracılığıyla programlı erişim sağlar:  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağaç yapısını gezinmeyi kolaylaştıran [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Ağaç hWnd'ın koleksiyonundan yerleşik olarak bulunur. Daha fazla bilgi için [UI Otomasyon ağacına genel bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
  
-   Otomasyon öğeleridir bileşenleri tek tek [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Bunlar genellikle bir hWnd daha ayrıntılı olabilir. Daha fazla bilgi için [UI Otomasyon denetim türlerine genel bakış](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md).  
  
-   Otomasyon özellikleri hakkında ayrıntılı bilgi sağlamak [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğeleri. Daha fazla bilgi için [UI Otomasyon özelliklerine genel bakış](../../../docs/framework/ui-automation/ui-automation-properties-overview.md).  
  
-   Denetimin işlevsellik belirli bir yönüyle denetim düzenleri tanımlayın. Bunlar, özellik, yöntem, olay ve yapı bilgileri oluşabilir. Daha fazla bilgi için [UI Otomasyon denetim düzenlerine genel bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
-   Otomasyon olayları, olay bildirimleri ve bilgileri sağlayın. Daha fazla bilgi için [UI Otomasyonu olaylarına genel bakış](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
<a name="Key_properties_critical_to_test_automation"></a>   
### <a name="key-properties-for-test-automation"></a>Test otomasyonu için anahtar özellikler  
 Benzersiz şekilde tanımlamak ve daha sonra içinde herhangi bir denetimi bulmak olanağı [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] üzerinde çalışılacak otomatik test uygulamaları için temelini [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Vardır [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] istemcileri ve bu konuda yardımcı sağlayıcıları tarafından kullanılan özellikleri.  
  
#### <a name="automationid"></a>Automationıd  
 Bir Otomasyon eşdüzey öğeyi benzersiz olarak tanımlar. <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> , bir özellik gibi yerelleştirilmez <xref:System.Windows.Automation.AutomationElement.NameProperty> , genellikle yerelleştirilmiş bir ürün birden çok dilde sevk. Bkz: [Automationıd özelliğini kullanma](../../../docs/framework/ui-automation/use-the-automationid-property.md).  
  
> [!NOTE]
>  <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> Otomasyon ağacı genelinde benzersiz bir kimlik garanti etmez. Örneğin, bir uygulama, buna karşılık, birden çok alt menü öğeleri sahip birden çok üst düzey menü öğeleri ile bir menü denetimi içerebilir. Bu ikincil menü öğeleri "Item1, öğe 2, Item3, vb." gibi genel bir şema belirtilebileceği yinelenen tanımlayıcıları alt öğeleri için üst düzey menü öğeleri arasında izin verme.  
  
#### <a name="controltype"></a>ControlType  
 Bir Otomasyon öğesi tarafından temsil edilen denetim türünü tanımlar. Önemli bilgileri, Denetim türü bilgilerden çıkarılan. Bkz: [UI Otomasyonu denetim türlerine genel bakış](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md).  
  
#### <a name="nameproperty"></a>NameProperty  
 Bu tanımlar veya bir denetim anlatan bir metin dizesidir. <xref:System.Windows.Automation.AutomationElement.NameProperty> yerelleştirilmiş bu yana dikkatli kullanılmalıdır. Bkz: [UI Otomasyon özelliklerine genel bakış](../../../docs/framework/ui-automation/ui-automation-properties-overview.md).  
  
<a name="Steps_Required_To_Automate_the_UI_in_a_Test_Application"></a>   
### <a name="implementing-ui-automation-in-a-test-application"></a>UI Otomasyonu uygulama içinde bir Test uygulaması  
  
|||  
|-|-|  
|UI Otomasyon başvurular ekleyin.|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Burada listelenen UI Otomasyon istemcileri için dll gerekli.<br /><br /> -UIAutomationClient.dll erişim sağlar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] istemci tarafı API.<br />-UIAutomationClientSideProvider.dll otomatikleştirme olanağı sağlar [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] kontrol eder. Bkz: [standart denetimler için UI Otomasyon desteği](../../../docs/framework/ui-automation/ui-automation-support-for-standard-controls.md).<br />-UIAutomationTypes.dll içinde tanımlanmış özel türlere erişim sağlar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|  
|Ekleme <xref:System.Windows.Automation> ad alanı.|Bu ad alanı özelliklerini kullanmak için UI Otomasyon istemcileri ihtiyacınız olan her şeyi içeren [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] metin işleme dışında.|  
|Ekleme <xref:System.Windows.Automation.Text> ad alanı.|Bu ad alanı özelliklerini kullanmak için UI Otomasyonu istemcileri gerek her şeyi içerir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] metin işleme.|  
|İlgilendiğiniz denetimleri Bul|Otomatik test betikleri denetimlerini ilgilendiren Otomasyon ağacı içinde UI Otomasyonu öğeleri bulun.<br /><br /> UI Otomasyonu öğeleri kodla almak için birden çok yolu vardır.<br /><br /> -Sorgu [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] kullanarak bir <xref:System.Windows.Automation.Condition> deyimi. Bu genellikle, burada dilden <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> kullanılır. **Not:** bir <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> belirtmek bulabildiği Inspect.exe gibi bir araç kullanarak elde edilebilir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetimin özelliklerini. <br /><br /> -Kullanma <xref:System.Windows.Automation.TreeWalker> tüm geçirmek için sınıf [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç veya onun bir alt.<br />-Odak izleyin.<br />-HWnd denetimi kullanın.<br />-Ekran konumu gibi fare imlecini konumunu kullanın.<br /><br /> Bkz: [UI Otomasyon öğelerini alma](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)|  
|Denetim düzenleri elde|Denetim desenlerini işlevsel olarak benzer denetimleri için ortak davranışları ortaya çıkarır.<br /><br /> Otomatik test betikleri test edilmesini gerektirir denetimleri bulunduktan sonra bu UI Otomasyonu öğeleri ilgi denetim düzenleri edinin. Örneğin, <xref:System.Windows.Automation.InvokePattern> tipik düğme işlevleri için Denetim düzeni veya <xref:System.Windows.Automation.WindowPattern> pencere işlevleri için Denetim düzeni.<br /><br /> Bkz: [UI Otomasyonu denetim desenleri genel bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).|  
|Kullanıcı arabirimini otomatik hale getirin|Otomatik test betikleri artık denetim herhangi [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] ilgilendiğiniz bir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] çerçevesi tarafından kullanıma sunulan işlevsellikten ve bilgi kullanılarak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetim desenleri.|  
  
<a name="Supporting_tools"></a>   
## <a name="related-tools-and-technologies"></a>İlgili araçları ve teknolojileri  
 İlgili araçları ve desteği ile otomatikleştirilmiş test teknoloji birçok [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
-   Inspect.exe olduğu bir [!INCLUDE[TLA#tla_gui](../../../includes/tlasharptla-gui-md.md)] toplamak için kullanılan uygulama [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sağlayıcısı ve istemci geliştirme ve hata ayıklama bilgileri. Inspect.exe dahil [!INCLUDE[TLA#tla_winfxsdk](../../../includes/tlasharptla-winfxsdk-md.md)].  
  
-   MSAABridge sunan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bilgileri [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] istemciler. Köprü oluşturma birincil amacı [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] için [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] varolan izin vermektir [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] istemcileri gerçekleştirdiğini herhangi bir çerçeveyi etkileşme yeteneği [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
<a name="Security"></a>   
## <a name="security"></a>Güvenlik  
 Güvenlik bilgileri için bkz: [UI Otomasyon güvenliğine genel bakış](../../../docs/framework/ui-automation/ui-automation-security-overview.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UI Otomasyonu Temelleri](../../../docs/framework/ui-automation/index.md)
