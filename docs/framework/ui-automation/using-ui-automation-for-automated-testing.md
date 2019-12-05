---
title: Otomatik Test İçin UI Otomasyonunu Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- automated testing
- testing, UI Automation
- UI Automation, automated testing
ms.assetid: 3a0435c0-a791-4ad7-ba92-a4c1d1231fde
ms.openlocfilehash: 2da0f994e809ff0ea9cd3165cd788ac467a87aef
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74800789"
---
# <a name="using-ui-automation-for-automated-testing"></a>Otomatik Test İçin UI Otomasyonunu Kullanma
> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu genel bakışta, [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] otomatikleştirilmiş test senaryolarında programlı erişim için bir çerçeve olarak nasıl yararlı olacağı açıklanmaktadır.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], tüm [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] çerçevelerin, erişilebilir ve kolay bir şekilde otomatik olarak karmaşık ve zengin işlevler sergilemesini sağlayan birleştirilmiş bir nesne modeli sağlar.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], Microsoft Etkin Erişilebilirlik 'in bir ardıl olarak geliştirilmiştir. Etkin Erişilebilirlik, denetimleri ve uygulamaları erişilebilir hale getirmek için bir çözüm sağlamak üzere tasarlanan mevcut bir çerçevedir. Etkin Erişilebilirlik, erişilebilirlik ve otomasyonun çok benzer gereksinimleri nedeniyle bu role sahip olsa bile test otomasyonu ile tasarlanmadı. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], erişilebilirlik için daha fazla sayıda çözüm sağlamaya ek olarak, otomatik test için güçlü işlevler sağlamak üzere de özel olarak tasarlanmıştır. Örneğin, Etkin Erişilebilirlik, her ikisi de Kullanıcı arabirimi hakkındaki bilgileri açığa çıkarmak ve ürünlerin gerektirdiği bilgileri toplamak için tek bir arabirime dayanır; [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] iki modeli ayırır.  
  
 Bir sağlayıcı ve istemci, otomatik test aracı olarak yararlı olması için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] uygulamak için gereklidir. UI Otomasyonu sağlayıcıları Microsoft Word, Excel ve diğer üçüncü taraf uygulamaları veya Microsoft Windows işletim sistemi tabanlı denetimler gibi uygulamalardır. UI Otomasyonu istemcileri otomatikleştirilmiş test betikleri ve yardımcı teknoloji uygulamaları içerir.  
  
> [!NOTE]
> Bu genel bakışın amacı, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]yeni ve geliştirilmiş otomatikleştirilmiş test yeteneklerini göstermaktır. Bu genel bakış, erişilebilirlik özellikleriyle ilgili bilgi sağlamaya yönelik değildir ve gerektiğinde erişilebilirliği farklı şekilde ele alır.  
  
## <a name="ui-automation-in-a-provider"></a>Bir sağlayıcıda UI Otomasyonu  
 Bir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] otomatikleştirilmesi için, bir uygulamanın veya denetimin geliştiricisi, standart klavye ve fare etkileşimi kullanarak bir son kullanıcının [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] nesnesi üzerinde gerçekleştirebileceği eylemlere bakmalıdır.  
  
 Bu anahtar eylemler tanımlandıktan sonra, karşılık gelen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Denetim desenleri (yani, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğesinin işlevlerini ve davranışını yansıtan Denetim desenleri) denetime uygulanmalıdır. Örneğin, bir açılan kutu denetimiyle (çalıştırma iletişim kutusu gibi) Kullanıcı etkileşimi genellikle bir öğe listesini gizlemek veya göstermek, bu listeden bir öğe seçmek veya klavye girişi aracılığıyla yeni bir değer eklemek için Birleşik giriş kutusunu genişletmeyi ve daraltmayı içerir.  
  
> [!NOTE]
> Diğer erişilebilirlik modelleriyle, geliştiricilerin doğrudan ayrı düğmeler, menüler veya diğer denetimlerden bilgi toplaması gerekir. Ne yazık ki her denetim türü düzinelerce küçük çeşitliliğe gelir. Diğer bir deyişle, bir basma düğmeli on çeşitlerinin hepsi aynı şekilde çalışabilir ve aynı işlevi gerçekleştirse de, bunların hepsi benzersiz denetimler olarak değerlendirilmelidir. Bu denetimlerin işlevsel olarak eşdeğer olduğu bilinmenin bir yolu yoktur. Denetim desenleri, bu ortak denetim davranışlarını temsil edecek şekilde geliştirilmiştir. Daha fazla bilgi için bkz. [UI Otomasyonu Denetim düzenlerine genel bakış](ui-automation-control-patterns-overview.md).  
  
### <a name="implementing-ui-automation"></a>UI Otomasyonu uygulama  
 Daha önce belirtildiği gibi, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]tarafından sunulan birleştirilmiş model olmadan test araçları ve geliştiricileri, bu çerçevede denetimlerin özelliklerini ve davranışlarını göstermek için çerçeveye özgü bilgileri bilmek için gereklidir. [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)], [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]ve Windows Presentation Foundation (WPF) dahil olmak üzere Windows işletim sistemleri içinde herhangi bir anda çeşitli farklı kullanıcı arabirimi çerçeveleri mevcut olduğundan, benzer denetimlerle birden çok uygulamayı test etmek için zaman korkdırıcı bir görev olabilir. Örneğin, aşağıdaki tablo, bir düğme denetimiyle ilişkilendirilen adı (veya metni) almak için gereken çerçeveye özgü özellik adlarını özetler ve tek eşdeğer [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özelliğini gösterir.  
  
|UI Otomasyonu Denetim türü|UI çerçevesi|Çerçeveye özgü özellik|UI Otomasyon özelliği|  
|--------------------------------|------------------|---------------------------------|----------------------------|  
|Düğme|Windows Presentation Foundation|İçerik|NameProperty|  
|Düğme|Win32|Başlık|NameProperty|  
|Görüntü|HTML|Alternatif|NameProperty|  
  
 UI Otomasyon sağlayıcıları, denetimlerinin çerçeveye özgü özelliklerini eşdeğer [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleriyle eşleştirmekten sorumludur.  
  
 Bir sağlayıcıda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] uygulamayla ilgili bilgiler, [yönetilen kod Için UI Otomasyon sağlayıcılarında](ui-automation-providers-for-managed-code.md)bulunabilir. Denetim desenleri uygulamayla ilgili bilgiler [UI Otomasyon Denetim desenleri](ui-automation-control-patterns.md) ve [UI Otomasyonu metin deseninden](ui-automation-text-pattern.md)edinilebilir.  
  
## <a name="ui-automation-in-a-client"></a>Istemcide UI Otomasyonu  
 Birçok otomatikleştirilmiş test araç ve senaryosunun hedefi, Kullanıcı arabiriminin tutarlı ve yinelenebilir şekilde işlenmesi ' dır. Bu, bir denetim grubu üzerinde bir dizi genel eylem boyunca yinelendiği test betikleri kaydetme ve kayıttan yürütme işlemleri aracılığıyla birim testi ile ilgili denetimleri içerebilir.  
  
 Otomatikleştirilmiş uygulamalardan oluşan karmaşıkma, bir testi dinamik hedefle eşitlerken zorluk ortaya çıkar. Örneğin, şu anda çalışan uygulamaların bir listesini görüntüleyen Windows Görev Yöneticisi 'nde yer alan bir liste kutusu denetimi. Liste kutusundaki öğeler test uygulaması denetimi dışında dinamik olarak güncelleştirildiğinden, liste kutusunda belirli bir öğe seçimini herhangi bir tutarlılık ile tekrarlamaya çalışmak imkansız olur. Ayrıca, test uygulamasının denetimi dışında bir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] basit odak değişikliklerini tekrarlamaya çalışırken de benzer sorunlar ortaya çıkabilir.  
  
### <a name="programmatic-access"></a>Programlı Erişim  
 Programlı erişim, geleneksel fare ve klavye girişi tarafından sunulan herhangi bir etkileşimi ve deneyimi kod aracılığıyla taklit etme yeteneği sağlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] beş bileşen aracılığıyla programlı erişime izin verebilir:  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]yapısına gezinmeyi kolaylaştırır. Ağaç, hWnd 'nin koleksiyonundan oluşturulmuştur. Daha fazla bilgi için bkz. [UI Otomasyon ağacına genel bakış](ui-automation-tree-overview.md)  
  
- Otomasyon öğeleri [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]bağımsız bileşenleridir. Bunlar genellikle hWnd 'den daha ayrıntılı olabilir. Daha fazla bilgi için bkz. [UI Otomasyonu Denetim türlerine genel bakış](ui-automation-control-types-overview.md).  
  
- Otomasyon özellikleri [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğeleriyle ilgili belirli bilgileri sağlar. Daha fazla bilgi için bkz. [UI Otomasyon özelliklerine genel bakış](ui-automation-properties-overview.md).  
  
- Denetim desenleri, bir denetimin işlevselliğinin belirli bir yönlerini tanımlar; Özellik, yöntem, olay ve yapı bilgisinden oluşur. Daha fazla bilgi için bkz. [UI Otomasyonu Denetim düzenlerine genel bakış](ui-automation-control-patterns-overview.md).  
  
- Otomasyon olayları olay bildirimleri ve bilgileri sağlar. Daha fazla bilgi için bkz. [UI Otomasyonu olaylarına genel bakış](ui-automation-events-overview.md).  
  
### <a name="key-properties-for-test-automation"></a>Test otomasyonu için anahtar özellikler  
 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] içinde herhangi bir denetimi benzersiz bir şekilde tanımlayıp bulma özelliği, otomatik test uygulamalarının bu [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]üzerinde çalışması için temel sağlar. Bu, istemciler ve sağlayıcılar tarafından buna yardımcı olan birkaç [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] özelliği vardır.  
  
#### <a name="automationid"></a>AutomationId  
 Bir Otomasyon öğesini, eşlerinden bağımsız olarak tanımlar. <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>, bir ürün birden çok dilde sevk edildiğinde, genellikle yerelleştirilmiş <xref:System.Windows.Automation.AutomationElement.NameProperty> gibi bir özelliğin aksine yerelleştirilmemiştir. Bkz. [AutomationID özelliğini kullanma](use-the-automationid-property.md).  
  
> [!NOTE]
> <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>, Otomasyon ağacının tamamında benzersiz bir kimlik garantisi vermez. Örneğin, bir uygulama birden çok üst düzey menü öğesi olan bir menü denetimi içerebilir, buna karşılık birden çok alt menü öğesi vardır. Bu ikincil menü öğeleri, "Item1, Item 2, Item3, vb." gibi genel bir düzen tarafından tanımlanabilir ve üst düzey menü öğeleri arasında alt öğeler için yinelenen tanımlayıcılara izin verebilir.  
  
#### <a name="controltype"></a>ControlType  
 Otomasyon öğesi tarafından temsil edilen denetimin türünü tanımlar. Denetim türü bilgisine önemli bilgiler çıkarsanamıyor. Bkz. [UI Otomasyonu Denetim türlerine genel bakış](ui-automation-control-types-overview.md).  
  
#### <a name="nameproperty"></a>NameProperty  
 Bu, bir denetimi tanımlayan veya açıklayan bir metin dizesidir. <xref:System.Windows.Automation.AutomationElement.NameProperty>, yerelleştirilemediğinden dikkatli kullanılmalıdır. Bkz. [UI Otomasyon özelliklerine genel bakış](ui-automation-properties-overview.md).  
  
### <a name="implementing-ui-automation-in-a-test-application"></a>Test uygulamasında UI Otomasyonu uygulama  
  
|||  
|-|-|  
|UI Otomasyon başvurularını ekleyin.|UI Otomasyon istemcileri için gereken [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dll 'si burada listelenmiştir.<br /><br /> -UIAutomationClient. dll [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] istemci tarafı API 'Lerine erişim sağlar.<br />-UIAutomationClientSideProvider. dll [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] denetimlerini otomatikleştirebilme olanağı sağlar. Bkz. [standart denetimler Için UI Otomasyon desteği](ui-automation-support-for-standard-controls.md).<br />-UIAutomationTypes. dll [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]tanımlı belirli türlere erişim sağlar.|  
|<xref:System.Windows.Automation> ad alanını ekleyin.|Bu ad alanı, Kullanıcı Arabirimi Otomasyonu istemcilerinin, metin işleme hariç [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] yeteneklerini kullanması gereken her şeyi içerir.|  
|<xref:System.Windows.Automation.Text> ad alanını ekleyin.|Bu ad alanı, Kullanıcı Arabirimi Otomasyonu istemcilerinin [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] metin işleme yeteneklerini kullanması gereken her şeyi içerir.|  
|İlgilendiğiniz denetimleri bulun|Otomatikleştirilmiş test betikleri, Otomasyon ağacı içinde ilgilendiğiniz denetimleri temsil eden UI Otomasyon öğelerini bulur.<br /><br /> Kodlu UI Otomasyon öğelerini almanın birden çok yolu vardır.<br /><br /> -[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] bir <xref:System.Windows.Automation.Condition> ifadesini kullanarak sorgulayın. Bu, genellikle dilden bağımsız <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> kullanıldığı yerdir. **Note:**  Bir <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>, bir denetimin [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özelliklerini seçebilecek Inceleme. exe gibi bir araç kullanılarak elde edilebilir. <br /><br /> -Tüm [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı veya alt kümele çapraz geçiş yapmak için <xref:System.Windows.Automation.TreeWalker> sınıfını kullanın.<br />-Odağı izleyin.<br />-Denetimin hWnd 'sini kullanın.<br />-Fare imlecinin konumu gibi ekran konumunu kullanın.<br /><br /> Bkz. [UI Otomasyonu öğelerini alma](obtaining-ui-automation-elements.md)|  
|Denetim desenleri alma|Denetim desenleri, işlevsel denetimler için ortak davranışları kullanıma sunar.<br /><br /> Test gerektiren denetimleri bulduktan sonra otomatik test betikleri, bu UI Otomasyon öğelerinden ilgilendiğiniz denetim düzenlerini elde eder. Örneğin, tipik düğme işlevselliği için <xref:System.Windows.Automation.InvokePattern> denetim deseninin veya pencere işlevleri için <xref:System.Windows.Automation.WindowPattern> denetim deseninin.<br /><br /> Bkz. [UI Otomasyonu Denetim düzenlerine genel bakış](ui-automation-control-patterns-overview.md).|  
|Kullanıcı arabirimini otomatikleştirme|Otomatikleştirilmiş test betikleri artık, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Denetim desenleri tarafından kullanıma sunulan bilgileri ve işlevleri kullanarak bir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] çerçevesinden tüm ilgi [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] kontrol edebilir.|  
  
## <a name="related-tools-and-technologies"></a>İlgili araçlar ve teknolojiler  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ile otomatikleştirilmiş sınamayı destekleyen birçok ilgili araç ve teknoloji vardır.  
  
- İnceleme. exe, hem sağlayıcı hem de istemci geliştirme ve hata ayıklama için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bilgilerini toplamak üzere kullanılabilecek bir grafik kullanıcı arabirimi (GUI) uygulamasıdır. İnceleme. exe Windows SDK eklenmiştir.  
  
- MSAABridge, Etkin Erişilebilirlik istemcilerine [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bilgilerini gösterir. Active Accessibility [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] köprülemenin birincil hedefi var olan Etkin Erişilebilirlik istemcilerine, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]uygulanmış olan herhangi bir çerçeve ile etkileşim kurma olanağı sağlamaktır.  
  
## <a name="security"></a>Güvenlik  
 Güvenlik bilgileri için bkz. [UI Otomasyonu güvenliğine genel bakış](ui-automation-security-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Temelleri](index.md)
