---
title: Otomatik Test İçin UI Otomasyonunu Kullanma
description: Otomatik test senaryolarında programlı erişim için bir çerçeve olarak UI Otomasyonu 'nu nasıl kullanacağınızı açıklayan bir genel bakış makalesini okuyun.
ms.date: 03/30/2017
helpviewer_keywords:
- automated testing
- testing, UI Automation
- UI Automation, automated testing
ms.assetid: 3a0435c0-a791-4ad7-ba92-a4c1d1231fde
ms.openlocfilehash: a38efd30e6f7f4cd05664d847c525dcf59ded61a
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86924480"
---
# <a name="using-ui-automation-for-automated-testing"></a>Otomatik Test İçin UI Otomasyonunu Kullanma
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu genel bakışta [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] , otomatikleştirilmiş test senaryolarında programlı erişim için bir çerçeve olarak nasıl yararlı olduğu açıklanır.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]tüm çerçevelerin, [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] erişilebilir ve kolay bir şekilde otomatik olarak karmaşık ve zengin işlevsellik sergilemesini sağlayan birleştirilmiş bir nesne modeli sağlar.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], Microsoft Etkin Erişilebilirlik için bir ardıl olarak geliştirilmiştir. Etkin Erişilebilirlik, denetimleri ve uygulamaları erişilebilir hale getirmek için bir çözüm sağlamak üzere tasarlanan mevcut bir çerçevedir. Etkin Erişilebilirlik, erişilebilirlik ve otomasyonun çok benzer gereksinimleri nedeniyle bu role sahip olsa bile test otomasyonu ile tasarlanmadı. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]erişilebilirlik için daha da çok daha fazla çözüm sağlamaya ek olarak, otomatik test için güçlü işlevler sağlamak üzere özel olarak tasarlanmıştır. Örneğin, Etkin Erişilebilirlik, her ikisi de Kullanıcı arabirimi hakkındaki bilgileri açığa çıkarmak ve ürünlerin gerektirdiği bilgileri toplamak için tek bir arabirime dayanır; [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]iki modeli ayırır.  
  
 Bir sağlayıcı ve istemci, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] otomatik test aracı olarak yararlı olması için uygulanması gerekir. UI Otomasyonu sağlayıcıları Microsoft Word, Excel ve diğer üçüncü taraf uygulamaları veya Microsoft Windows işletim sistemi tabanlı denetimler gibi uygulamalardır. UI Otomasyonu istemcileri otomatikleştirilmiş test betikleri ve yardımcı teknoloji uygulamaları içerir.  
  
> [!NOTE]
> Bu genel bakışın amacı, ' nin yeni ve geliştirilmiş otomatikleştirilmiş test yeteneklerini göstermaktır [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] . Bu genel bakış, erişilebilirlik özellikleriyle ilgili bilgi sağlamaya yönelik değildir ve gerektiğinde erişilebilirliği farklı şekilde ele alır.  
  
## <a name="ui-automation-in-a-provider"></a>Bir sağlayıcıda UI Otomasyonu  
 Bir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] uygulamasının otomatik olması için, bir uygulama veya denetim geliştiricisi, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] Standart klavye ve fare etkileşimi kullanarak bir son kullanıcının nesne üzerinde gerçekleştirebileceği eylemleri göz önüne almalıdır.  
  
 Bu anahtar eylemler tanımlandıktan sonra, ilgili [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Denetim desenleri (yani, öğesinin işlevselliğini ve davranışını yansıtan Denetim desenleri [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] ) denetime uygulanmalıdır. Örneğin, bir açılan kutu denetimiyle (çalıştırma iletişim kutusu gibi) Kullanıcı etkileşimi genellikle bir öğe listesini gizlemek veya göstermek, bu listeden bir öğe seçmek veya klavye girişi aracılığıyla yeni bir değer eklemek için Birleşik giriş kutusunu genişletmeyi ve daraltmayı içerir.  
  
> [!NOTE]
> Diğer erişilebilirlik modelleriyle, geliştiricilerin doğrudan ayrı düğmeler, menüler veya diğer denetimlerden bilgi toplaması gerekir. Ne yazık ki her denetim türü düzinelerce küçük çeşitliliğe gelir. Diğer bir deyişle, bir basma düğmeli on çeşitlerinin hepsi aynı şekilde çalışabilir ve aynı işlevi gerçekleştirse de, bunların hepsi benzersiz denetimler olarak değerlendirilmelidir. Bu denetimlerin işlevsel olarak eşdeğer olduğu bilinmenin bir yolu yoktur. Denetim desenleri, bu ortak denetim davranışlarını temsil edecek şekilde geliştirilmiştir. Daha fazla bilgi için bkz. [UI Otomasyonu Denetim düzenlerine genel bakış](ui-automation-control-patterns-overview.md).  
  
### <a name="implementing-ui-automation"></a>UI Otomasyonu uygulama  
 Daha önce belirtildiği gibi, tarafından sunulan birleştirilmiş model olmadan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , test araçları ve geliştiricileri, bu çerçevede denetimlerin özelliklerini ve davranışlarını göstermek üzere çerçeveye özgü bilgileri bilmek için gereklidir. Win32, Windows Forms ve Windows Presentation Foundation (WPF) dahil olmak üzere Windows işletim sistemleri içinde herhangi bir anda çeşitli farklı kullanıcı arabirimi çerçeveleri mevcut olduğundan, benzer denetimlerle birden çok uygulamayı test etmek için zaman korkdırıcı bir görev olabilir. Örneğin, aşağıdaki tablo, bir düğme denetimiyle ilişkilendirilen adı (veya metni) almak için gereken çerçeveye özgü özellik adlarını özetler ve tek denk [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özelliği gösterir.  
  
|UI Otomasyonu Denetim türü|UI çerçevesi|Çerçeveye özgü özellik|UI Otomasyon özelliği|  
|--------------------------------|------------------|---------------------------------|----------------------------|  
|Düğme|Windows Presentation Foundation|İçerik|NameProperty|  
|Düğme|Win32|Başlık|NameProperty|  
|Görüntü|HTML|Alternatif|NameProperty|  
  
 UI Otomasyon sağlayıcıları, denetimlerinin çerçeveye özgü özelliklerini eşdeğer özelliklerle eşleştirmekten sorumludur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .  
  
 Bir sağlayıcıda uygulamayla ilgili bilgiler [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , [yönetilen kod Için UI Otomasyon sağlayıcılarında](ui-automation-providers-for-managed-code.md)bulunabilir. Denetim desenleri uygulamayla ilgili bilgiler [UI Otomasyon Denetim desenleri](ui-automation-control-patterns.md) ve [UI Otomasyonu metin deseninden](ui-automation-text-pattern.md)edinilebilir.  
  
## <a name="ui-automation-in-a-client"></a>Istemcide UI Otomasyonu  
 Birçok otomatikleştirilmiş test araç ve senaryosunun hedefi, Kullanıcı arabiriminin tutarlı ve yinelenebilir şekilde işlenmesi ' dır. Bu, bir denetim grubu üzerinde bir dizi genel eylem boyunca yinelendiği test betikleri kaydetme ve kayıttan yürütme işlemleri aracılığıyla birim testi ile ilgili denetimleri içerebilir.  
  
 Otomatikleştirilmiş uygulamalardan oluşan karmaşıkma, bir testi dinamik hedefle eşitlerken zorluk ortaya çıkar. Örneğin, şu anda çalışan uygulamaların bir listesini görüntüleyen Windows Görev Yöneticisi 'nde yer alan bir liste kutusu denetimi. Liste kutusundaki öğeler test uygulaması denetimi dışında dinamik olarak güncelleştirildiğinden, liste kutusunda belirli bir öğe seçimini herhangi bir tutarlılık ile tekrarlamaya çalışmak imkansız olur. Aynı zamanda [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] , test uygulamasının denetimi dışında bir içindeki basit odak değişikliklerinin tekrarlanması denenmeye çalışıldığında de benzer sorunlar ortaya çıkabilir.  
  
### <a name="programmatic-access"></a>Programlı Erişim  
 Programlı erişim, geleneksel fare ve klavye girişi tarafından sunulan herhangi bir etkileşimi ve deneyimi kod aracılığıyla taklit etme yeteneği sağlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]beş bileşen aracılığıyla programlı erişime izin vermez:  
  
- Ağaç, ' [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nin yapısına göre gezinmeyi kolaylaştırır [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] . Ağaç, hWnd 'nin koleksiyonundan oluşturulmuştur. Daha fazla bilgi için bkz. [UI Otomasyon ağacına genel bakış](ui-automation-tree-overview.md)  
  
- Otomasyon öğeleri içindeki tek bileşenleridir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] . Bunlar genellikle hWnd 'den daha ayrıntılı olabilir. Daha fazla bilgi için bkz. [UI Otomasyonu Denetim türlerine genel bakış](ui-automation-control-types-overview.md).  
  
- Otomasyon Özellikleri, öğeler hakkında belirli bilgiler sağlar [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] . Daha fazla bilgi için bkz. [UI Otomasyon özelliklerine genel bakış](ui-automation-properties-overview.md).  
  
- Denetim desenleri, bir denetimin işlevselliğinin belirli bir yönlerini tanımlar; Özellik, yöntem, olay ve yapı bilgisinden oluşur. Daha fazla bilgi için bkz. [UI Otomasyonu Denetim düzenlerine genel bakış](ui-automation-control-patterns-overview.md).  
  
- Otomasyon olayları olay bildirimleri ve bilgileri sağlar. Daha fazla bilgi için bkz. [UI Otomasyonu olaylarına genel bakış](ui-automation-events-overview.md).  
  
### <a name="key-properties-for-test-automation"></a>Test otomasyonu için anahtar özellikler  
 İçinde herhangi bir denetimi benzersiz bir şekilde belirleyip daha sonra bulma özelliği, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] otomatik test uygulamalarının bu uygulamada çalışacağı temeli sağlar [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] . [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]Bu, istemciler ve sağlayıcılar tarafından buna yardımcı olan çeşitli özellikler vardır.  
  
#### <a name="automationid"></a>AutomationId  
 Bir Otomasyon öğesini, eşlerinden bağımsız olarak tanımlar. <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>yerelleştirilmiş değildir; Örneğin, <xref:System.Windows.Automation.AutomationElement.NameProperty> bir ürün birden çok dilde sevk edildiğinde, bu özellik genellikle yereldir. Bkz. [AutomationID özelliğini kullanma](use-the-automationid-property.md).  
  
> [!NOTE]
> <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>Otomasyon ağacının tamamında benzersiz bir kimlik garantisi vermez. Örneğin, bir uygulama birden çok üst düzey menü öğesi olan bir menü denetimi içerebilir, buna karşılık birden çok alt menü öğesi vardır. Bu ikincil menü öğeleri, "Item1, Item 2, Item3, vb." gibi genel bir düzen tarafından tanımlanabilir ve üst düzey menü öğeleri arasında alt öğeler için yinelenen tanımlayıcılara izin verebilir.  
  
#### <a name="controltype"></a>ControlType  
 Otomasyon öğesi tarafından temsil edilen denetimin türünü tanımlar. Denetim türü bilgisine önemli bilgiler çıkarsanamıyor. Bkz. [UI Otomasyonu Denetim türlerine genel bakış](ui-automation-control-types-overview.md).  
  
#### <a name="nameproperty"></a>NameProperty  
 Bu, bir denetimi tanımlayan veya açıklayan bir metin dizesidir. <xref:System.Windows.Automation.AutomationElement.NameProperty>yerelleştirildiği için dikkatli kullanılmalıdır. Bkz. [UI Otomasyon özelliklerine genel bakış](ui-automation-properties-overview.md).  
  
### <a name="implementing-ui-automation-in-a-test-application"></a>Test uygulamasında UI Otomasyonu uygulama  
  
|||  
|-|-|  
|UI Otomasyon başvurularını ekleyin.|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]UI Otomasyon istemcileri için gereken dll 'ler burada listelenmiştir.<br /><br /> -UIAutomationClient.dll [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] istemci tarafı API 'lerine erişim sağlar.<br />-UIAutomationClientSideProvider.dll Win32 denetimlerini otomatikleştirebilme olanağı sağlar. Bkz. [standart denetimler Için UI Otomasyon desteği](ui-automation-support-for-standard-controls.md).<br />-UIAutomationTypes.dll içinde tanımlanan belirli türlere erişim sağlar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation>Ad alanını ekleyin.|Bu ad alanı, Kullanıcı Arabirimi Otomasyonu istemcilerinin, metin işleme hariç yeteneklerini kullanması gereken her şeyi içerir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation.Text>Ad alanını ekleyin.|Bu ad alanı, Kullanıcı Arabirimi Otomasyonu istemcilerinin metin işleme yeteneklerini kullanması gereken her şeyi içerir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|İlgilendiğiniz denetimleri bulun|Otomatikleştirilmiş test betikleri, Otomasyon ağacı içinde ilgilendiğiniz denetimleri temsil eden UI Otomasyon öğelerini bulur.<br /><br /> Kodlu UI Otomasyon öğelerini almanın birden çok yolu vardır.<br /><br /> - [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] Using a ifadesini sorgulayın <xref:System.Windows.Automation.Condition> . Bu, genellikle dilden bağımsız <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> kullanıldığı yerdir. **Note:**  Bir <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> denetimin özelliklerini kaydedebilecek Inspect.exe gibi bir araç kullanılarak elde edilebilir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] . <br /><br /> - <xref:System.Windows.Automation.TreeWalker> Tüm [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacın veya alt kümenin tamamında çapraz geçiş yapmak için sınıfını kullanın.<br />-Odağı izleyin.<br />-Denetimin hWnd 'sini kullanın.<br />-Fare imlecinin konumu gibi ekran konumunu kullanın.<br /><br /> Bkz. [UI Otomasyonu öğelerini alma](obtaining-ui-automation-elements.md)|  
|Denetim desenleri alma|Denetim desenleri, işlevsel denetimler için ortak davranışları kullanıma sunar.<br /><br /> Test gerektiren denetimleri bulduktan sonra otomatik test betikleri, bu UI Otomasyon öğelerinden ilgilendiğiniz denetim düzenlerini elde eder. Örneğin, <xref:System.Windows.Automation.InvokePattern> tipik düğme işlevselliği için denetim deseninin veya <xref:System.Windows.Automation.WindowPattern> pencere işlevselliği için denetim deseninin.<br /><br /> Bkz. [UI Otomasyonu Denetim düzenlerine genel bakış](ui-automation-control-patterns-overview.md).|  
|Kullanıcı arabirimini otomatikleştirme|Otomatikleştirilmiş test betikleri artık [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] Denetim desenleri tarafından kullanıma sunulan bilgileri ve işlevleri kullanarak bir çerçeveden herhangi bir ilgi denetimini denetleyebilir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
  
## <a name="related-tools-and-technologies"></a>İlgili araçlar ve teknolojiler  
 İle otomatikleştirilmiş sınamayı destekleyen birçok ilgili araç ve teknoloji vardır [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .  
  
- Inspect.exe, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hem sağlayıcı hem de istemci geliştirme ve hata ayıklama için bilgi toplamak üzere kullanılabilecek bir grafik kullanıcı arabirimi (GUI) uygulamasıdır. Inspect.exe, Windows SDK dahil edilir.  
  
- MSAABridge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Etkin Erişilebilirlik istemcilerine bilgi gösterir. Etkin Erişilebilirlik 'e köprülemenin birincil hedefi [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] var olan Etkin Erişilebilirlik istemcilerine, uygulanmış olan herhangi bir çerçeve ile etkileşim kurma olanağı sağlamaktır [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .  
  
## <a name="security"></a>Güvenlik  
 Güvenlik bilgileri için bkz. [UI Otomasyonu güvenliğine genel bakış](ui-automation-security-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyon Temelleri](index.md)
