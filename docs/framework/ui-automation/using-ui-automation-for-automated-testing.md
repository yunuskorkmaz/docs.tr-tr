---
title: Otomatik Test İçin UI Otomasyonunu Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- automated testing
- testing, UI Automation
- UI Automation, automated testing
ms.assetid: 3a0435c0-a791-4ad7-ba92-a4c1d1231fde
ms.openlocfilehash: 3fb5d1107a2dacdc4dfd2210322c312becdfd90b
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566951"
---
# <a name="using-ui-automation-for-automated-testing"></a>Otomatik Test İçin UI Otomasyonunu Kullanma
> [!NOTE]
>  Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu genel bakışta, [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] otomatikleştirilmiş test senaryolarında programlı erişim için bir çerçeve olarak nasıl yararlı olduğu açıklanır.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Tüm [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] çerçevelerin, erişilebilir ve kolay bir şekilde otomatik olarak karmaşık ve zengin işlevsellik sergilemesini sağlayan birleştirilmiş bir nesne modeli sağlar.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], Microsoft Etkin Erişilebilirlik için bir ardıl olarak geliştirilmiştir. Etkin Erişilebilirlik, denetimleri ve uygulamaları erişilebilir hale getirmek için bir çözüm sağlamak üzere tasarlanan mevcut bir çerçevedir. Etkin Erişilebilirlik, erişilebilirlik ve otomasyonun çok benzer gereksinimleri nedeniyle bu role sahip olsa bile test otomasyonu ile tasarlanmadı. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]erişilebilirlik için daha da çok daha fazla çözüm sağlamaya ek olarak, otomatik test için güçlü işlevler sağlamak üzere özel olarak tasarlanmıştır. Örneğin, Etkin Erişilebilirlik, her ikisi de Kullanıcı arabirimi hakkındaki bilgileri açığa çıkarmak ve ürünlerin gerektirdiği bilgileri toplamak için tek bir arabirime dayanır; [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] iki modeli ayırır.  
  
 Bir sağlayıcı ve istemci, otomatik test aracı olarak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] yararlı olması için uygulanması gerekir. UI Otomasyon sağlayıcıları, Microsoft Word, Excel ve diğer üçüncü taraf uygulamaları veya [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)] işletim sistemine bağlı diğer uygulamalar gibi uygulamalardır. UI Otomasyonu istemcileri otomatikleştirilmiş test betikleri ve yardımcı teknoloji uygulamaları içerir.  
  
> [!NOTE]
>  Bu genel bakışın amacı, ' nin [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]yeni ve geliştirilmiş otomatikleştirilmiş test yeteneklerini göstermaktır. Bu genel bakış, erişilebilirlik özellikleriyle ilgili bilgi sağlamaya yönelik değildir ve gerektiğinde erişilebilirliği farklı şekilde ele alır.  
  
<a name="Using_UI_Automation_During_Development"></a>   
## <a name="ui-automation-in-a-provider"></a>Bir sağlayıcıda UI Otomasyonu  
 Bir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] uygulamasının otomatik olması için, bir uygulama veya denetim geliştiricisi, standart klavye ve fare etkileşimi kullanarak bir son kullanıcının [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] nesne üzerinde gerçekleştirebileceği eylemleri göz önüne almalıdır.  
  
 Bu anahtar eylemler tanımlandıktan sonra, ilgili [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Denetim desenleri (yani, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğesinin işlevselliğini ve davranışını yansıtan Denetim desenleri) denetime uygulanmalıdır. Örneğin, bir açılan kutu denetimiyle (çalıştırma iletişim kutusu gibi) Kullanıcı etkileşimi genellikle bir öğe listesini gizlemek veya göstermek, bu listeden bir öğe seçmek veya klavye girişi aracılığıyla yeni bir değer eklemek için Birleşik giriş kutusunu genişletmeyi ve daraltmayı içerir.  
  
> [!NOTE]
>  Diğer erişilebilirlik modelleriyle, geliştiricilerin doğrudan ayrı düğmeler, menüler veya diğer denetimlerden bilgi toplaması gerekir. Ne yazık ki her denetim türü düzinelerce küçük çeşitliliğe gelir. Diğer bir deyişle, bir basma düğmeli on çeşitlerinin hepsi aynı şekilde çalışabilir ve aynı işlevi gerçekleştirse de, bunların hepsi benzersiz denetimler olarak değerlendirilmelidir. Bu denetimlerin işlevsel olarak eşdeğer olduğu bilinmenin bir yolu yoktur. Denetim desenleri, bu ortak denetim davranışlarını temsil edecek şekilde geliştirilmiştir. Daha fazla bilgi için bkz. [UI Otomasyonu Denetim düzenlerine genel bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
<a name="Implementing_UI_Automation"></a>   
### <a name="implementing-ui-automation"></a>UI Otomasyonu uygulama  
 Daha önce belirtildiği gibi, tarafından [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]sunulan birleştirilmiş model olmadan, test araçları ve geliştiricileri, bu çerçevede denetimlerin özelliklerini ve davranışlarını göstermek üzere çerçeveye özgü bilgileri bilmek için gereklidir. [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] ,[!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]Ve Windows Presentation Foundation (WPF) dahil olmak üzere Windows işletim sistemleri içinde herhangi bir zamanda çeşitli farklı kullanıcı arabirimi çerçeveleri mevcut olduğundan, birden çok uygulamayı test etmek için benzer görünen denetimler. Örneğin, aşağıdaki tablo, bir düğme denetimiyle ilişkilendirilen adı (veya metni) almak için gereken çerçeveye özgü özellik adlarını özetler ve tek denk [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özelliği gösterir.  
  
|UI Otomasyonu Denetim türü|UI çerçevesi|Çerçeveye özgü özellik|UI Otomasyon özelliği|  
|--------------------------------|------------------|---------------------------------|----------------------------|  
|Düğme|Windows Presentation Foundation|İçerik|NameProperty|  
|Düğme|Win32|Başlık|NameProperty|  
|Görüntü|HTML|Alternatif|NameProperty|  
  
 UI Otomasyon sağlayıcıları, denetimlerinin çerçeveye özgü özelliklerini eşdeğer [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özelliklerle eşleştirmekten sorumludur.  
  
 Bir sağlayıcıda uygulamayla [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ilgili bilgiler, [yönetilen kod için UI Otomasyon sağlayıcılarında](../../../docs/framework/ui-automation/ui-automation-providers-for-managed-code.md)bulunabilir. Denetim desenleri uygulamayla ilgili bilgiler [UI Otomasyon Denetim desenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns.md) ve [UI Otomasyonu metin deseninden](../../../docs/framework/ui-automation/ui-automation-text-pattern.md)edinilebilir.  
  
<a name="Testing_with_UI_Automation"></a>   
## <a name="ui-automation-in-a-client"></a>Istemcide UI Otomasyonu  
 Birçok otomatikleştirilmiş test araç ve senaryosunun hedefi, Kullanıcı arabiriminin tutarlı ve yinelenebilir şekilde işlenmesi ' dır. Bu, bir denetim grubu üzerinde bir dizi genel eylem boyunca yinelendiği test betikleri kaydetme ve kayıttan yürütme işlemleri aracılığıyla birim testi ile ilgili denetimleri içerebilir.  
  
 Otomatikleştirilmiş uygulamalardan oluşan karmaşıkma, bir testi dinamik hedefle eşitlerken zorluk ortaya çıkar. Örneğin, şu anda çalışan uygulamaların bir listesini görüntüleyen Windows Görev Yöneticisi 'nde yer alan bir liste kutusu denetimi. Liste kutusundaki öğeler test uygulaması denetimi dışında dinamik olarak güncelleştirildiğinden, liste kutusunda belirli bir öğe seçimini herhangi bir tutarlılık ile tekrarlamaya çalışmak imkansız olur. Aynı zamanda, test uygulamasının denetimi dışında bir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] içindeki basit odak değişikliklerinin tekrarlanması denenmeye çalışıldığında de benzer sorunlar ortaya çıkabilir.  
  
<a name="Programmatic_Access"></a>   
### <a name="programmatic-access"></a>Programlı erişim  
 Programlı erişim, geleneksel fare ve klavye girişi tarafından sunulan herhangi bir etkileşimi ve deneyimi kod aracılığıyla taklit etme yeteneği sağlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]beş bileşen aracılığıyla programlı erişime izin vermez:  
  
- Ağaç, ' [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]nin yapısına göre gezinmeyi kolaylaştırır. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağaç, hWnd 'nin koleksiyonundan oluşturulmuştur. Daha fazla bilgi için bkz. [UI Otomasyon ağacına genel bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
  
- Otomasyon öğeleri içindeki [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]tek bileşenleridir. Bunlar genellikle hWnd 'den daha ayrıntılı olabilir. Daha fazla bilgi için bkz. [UI Otomasyonu Denetim türlerine genel bakış](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md).  
  
- Otomasyon Özellikleri, öğeler hakkında [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] belirli bilgiler sağlar. Daha fazla bilgi için bkz. [UI Otomasyon özelliklerine genel bakış](../../../docs/framework/ui-automation/ui-automation-properties-overview.md).  
  
- Denetim desenleri, bir denetimin işlevselliğinin belirli bir yönlerini tanımlar; Özellik, yöntem, olay ve yapı bilgisinden oluşur. Daha fazla bilgi için bkz. [UI Otomasyonu Denetim düzenlerine genel bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
- Otomasyon olayları olay bildirimleri ve bilgileri sağlar. Daha fazla bilgi için bkz. [UI Otomasyonu olaylarına genel bakış](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
<a name="Key_properties_critical_to_test_automation"></a>   
### <a name="key-properties-for-test-automation"></a>Test otomasyonu için anahtar özellikler  
 İçinde [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] herhangi bir denetimi benzersiz bir şekilde belirleyip daha sonra bulma özelliği, otomatik test uygulamalarının bu [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]uygulamada çalışacağı temeli sağlar. Bu, istemciler [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] ve sağlayıcılar tarafından buna yardımcı olan çeşitli özellikler vardır.  
  
#### <a name="automationid"></a>AutomationId  
 Bir Otomasyon öğesini, eşlerinden bağımsız olarak tanımlar. <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>yerelleştirilmiş değildir; Örneğin, bir ürün birden çok <xref:System.Windows.Automation.AutomationElement.NameProperty> dilde sevk edildiğinde, bu özellik genellikle yereldir. Bkz. [AutomationID özelliğini kullanma](../../../docs/framework/ui-automation/use-the-automationid-property.md).  
  
> [!NOTE]
>  <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>Otomasyon ağacının tamamında benzersiz bir kimlik garantisi vermez. Örneğin, bir uygulama birden çok üst düzey menü öğesi olan bir menü denetimi içerebilir, buna karşılık birden çok alt menü öğesi vardır. Bu ikincil menü öğeleri, "Item1, Item 2, Item3, vb." gibi genel bir düzen tarafından tanımlanabilir ve üst düzey menü öğeleri arasında alt öğeler için yinelenen tanımlayıcılara izin verebilir.  
  
#### <a name="controltype"></a>ControlType  
 Otomasyon öğesi tarafından temsil edilen denetimin türünü tanımlar. Denetim türü bilgisine önemli bilgiler çıkarsanamıyor. Bkz. [UI Otomasyonu Denetim türlerine genel bakış](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md).  
  
#### <a name="nameproperty"></a>NameProperty  
 Bu, bir denetimi tanımlayan veya açıklayan bir metin dizesidir. <xref:System.Windows.Automation.AutomationElement.NameProperty>yerelleştirildiği için dikkatli kullanılmalıdır. Bkz. [UI Otomasyon özelliklerine genel bakış](../../../docs/framework/ui-automation/ui-automation-properties-overview.md).  
  
<a name="Steps_Required_To_Automate_the_UI_in_a_Test_Application"></a>   
### <a name="implementing-ui-automation-in-a-test-application"></a>Test uygulamasında UI Otomasyonu uygulama  
  
|||  
|-|-|  
|UI Otomasyon başvurularını ekleyin.|UI Otomasyon istemcileri için gereken DLL'lerburadalistelenmiştir.[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<br /><br /> -UIAutomationClient. dll, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] istemci tarafı API 'lerine erişim sağlar.<br />-UIAutomationClientSideProvider. dll, denetimleri otomatikleştirebilme [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] olanağı sağlar. Bkz. [standart denetimler Için UI Otomasyon desteği](../../../docs/framework/ui-automation/ui-automation-support-for-standard-controls.md).<br />-UIAutomationTypes. dll, içinde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]tanımlanan belirli türlere erişim sağlar.|  
|<xref:System.Windows.Automation> Ad alanını ekleyin.|Bu ad alanı, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Kullanıcı Arabirimi Otomasyonu istemcilerinin, metin işleme hariç yeteneklerini kullanması gereken her şeyi içerir.|  
|<xref:System.Windows.Automation.Text> Ad alanını ekleyin.|Bu ad alanı, Kullanıcı Arabirimi Otomasyonu istemcilerinin [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] metin işleme yeteneklerini kullanması gereken her şeyi içerir.|  
|İlgilendiğiniz denetimleri bulun|Otomatikleştirilmiş test betikleri, Otomasyon ağacı içinde ilgilendiğiniz denetimleri temsil eden UI Otomasyon öğelerini bulur.<br /><br /> Kodlu UI Otomasyon öğelerini almanın birden çok yolu vardır.<br /><br /> - [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] Using a <xref:System.Windows.Automation.Condition> ifadesini sorgulayın. Bu, genellikle dilden bağımsız <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> kullanıldığı yerdir. **Not:**  Bir <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> denetimin [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özelliklerini silmek için, ınspecable. exe gibi bir araç kullanılarak elde edilebilir. <br /><br /> -Tüm ağacın <xref:System.Windows.Automation.TreeWalker> veya alt kümenin tamamında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] çapraz geçiş yapmak için sınıfını kullanın.<br />-Odağı izleyin.<br />-Denetimin hWnd 'sini kullanın.<br />-Fare imlecinin konumu gibi ekran konumunu kullanın.<br /><br /> Bkz. [UI Otomasyonu öğelerini alma](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)|  
|Denetim desenleri alma|Denetim desenleri, işlevsel denetimler için ortak davranışları kullanıma sunar.<br /><br /> Test gerektiren denetimleri bulduktan sonra otomatik test betikleri, bu UI Otomasyon öğelerinden ilgilendiğiniz denetim düzenlerini elde eder. Örneğin, <xref:System.Windows.Automation.InvokePattern> tipik düğme işlevselliği için denetim deseninin <xref:System.Windows.Automation.WindowPattern> veya pencere işlevselliği için denetim deseninin.<br /><br /> Bkz. [UI Otomasyonu Denetim düzenlerine genel bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).|  
|Kullanıcı arabirimini otomatikleştirme|Otomatikleştirilmiş test betikleri artık [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Denetim desenleri tarafından kullanıma sunulan bilgileri ve [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] işlevleri kullanarak bir çerçeveden herhangi bir ilgi denetimini denetleyebilir.|  
  
<a name="Supporting_tools"></a>   
## <a name="related-tools-and-technologies"></a>İlgili araçlar ve teknolojiler  
 İle [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]otomatikleştirilmiş sınamayı destekleyen birçok ilgili araç ve teknoloji vardır.  
  
- İnceleme. exe, hem sağlayıcı hem de istemci geliştirme ve hata ayıklama için bilgi toplamak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] üzere kullanılabilecek bir grafik kullanıcı arabirimi (GUI) uygulamasıdır. İnceleme. exe Windows SDK eklenmiştir.  
  
- MSAABridge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Etkin Erişilebilirlik istemcilerine bilgi gösterir. Etkin Erişilebilirlik 'e köprülemenin [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] birincil hedefi var olan Etkin Erişilebilirlik istemcilerine, uygulanmış [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]olan herhangi bir çerçeve ile etkileşim kurma olanağı sağlamaktır.  
  
<a name="Security"></a>   
## <a name="security"></a>Güvenlik  
 Güvenlik bilgileri için bkz. [UI Otomasyonu güvenliğine genel bakış](../../../docs/framework/ui-automation/ui-automation-security-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Temelleri](../../../docs/framework/ui-automation/index.md)
