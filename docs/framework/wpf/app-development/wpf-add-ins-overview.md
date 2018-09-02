---
title: WPF Eklentilerine Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- add-ins and XAML browser applications [WPF]
- add-ins overview [WPF]
- add-ins [WPF], performance
- add-ins [WPF], benefits
- .NET Framework add-in model [WPF]
- add-ins [WPF], user interface
- add-ins and the user interface [WPF]
- add-ins [WPF], architecture
- add-ins [WPF], limitations
ms.assetid: 00b4c776-29a8-4dba-b603-280a0cdc2ade
ms.openlocfilehash: 2e5d133a4744124723c0373e3d5974b505936190
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43402107"
---
# <a name="wpf-add-ins-overview"></a>WPF Eklentilerine Genel Bakış
<a name="Introduction"></a> [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Geliştiriciler eklenti genişletilebilirliği destekleyen uygulamalar oluşturmak için kullanabileceğiniz bir eklenti modeli içerir. Bu eklenti modeli ile tümleştirin ve uygulama işlevselliğini genişleten eklentileri oluşturulmasına izin verir. Bazı senaryolarda uygulamalar da görüntülemeniz [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] eklentiler tarafından sağlanır. Bu konu başlığı altında gösterilir nasıl [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] artırmaktadır [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] bu senaryolar, arkasındaki mimarisi, aboneliğin avantajları ve kısıtlamalarını etkinleştirmek için eklenti modeli.  
  

  
<a name="Requirements"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Konusunda [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] modelidir gerekli eklenti. Daha fazla bilgi için [eklentiler ve genişletilebilirlik](../../../../docs/framework/add-ins/index.md).  
  
<a name="AddInsOverview"></a>   
## <a name="add-ins-overview"></a>Eklentilere genel bakış  
 Karmaşıklığını uygulama yeniden derleme ve yeni işlevsellikler eklemek için yeniden dağıtım kaçınmak için geliştiricilerin (hem birinci taraf hem de üçüncü taraf) genişletilebilirlik mekanizması uygulamaları uygular, diğer uygulamalar oluşturma onlarla tümleştirin. Add-INS kullanımı ("eklentiler" ve "eklentiler" olarak da bilinir) bu tür bir genişletilebilirlik desteklemek için en yaygın yoludur. Genişletilebilirlik eklentiler ile kullanıma gerçek uygulamaları örnekleri şunlardır:  
  
-   Internet Explorer eklentiler.  
  
-   Windows Media Player eklentiler.  
  
-   Visual Studio eklentileri.  
  
 Örneğin, "kod çözücüleri ve Windows tarafından yerel olarak desteklenmeyen medya biçimleri Kodlayıcıları oluşturma dahil olmak üzere çeşitli Windows Media Player'ı genişleten eklentiler" uygulamak üçüncü taraf geliştiriciler Windows Media Player eklenti modeli sağlar Media Player (örneğin, DVD, MP3), ses efekti ve dış. Her eklenti modeli, varlıklar ve eklenti tüm modelleri için ortak olan davranışları olsa bir uygulama için benzersiz olan işlevselliği göstermek için oluşturulmuştur.  
  
 Üç ana varlıklardır tipik eklenti genişletilebilirliği çözümlerinin *sözleşmeleri*, *eklentileri*, ve *ana bilgisayar uygulamalarını*. Sözleşmeler, eklentiler iki yolla konak uygulamalarıyla tümleştirmek tanımlar:  
  
-   Eklentiler, konak uygulamalar tarafından uygulanan işlevleri ile tümleştirin.  
  
-   Ana bilgisayar uygulamaları tümleştirmek eklentiler için işlevselliği kullanıma sunar.  
  
 Kullanılacak eklentiler için konak uygulamalar bulup bunları çalışma zamanında yük gerekir. Sonuç olarak, eklentiler destekleyen uygulamalar, aşağıdaki ek sorumluluklara sahiptir:  
  
-   **Bulma**: konak uygulamalar tarafından desteklenen sözleşmeleri izliyor eklentiler bulma.  
  
-   **Etkinleştirme**: çalıştıran ve eklentiler ile iletişim kurma yükleniyor.  
  
-   **Yalıtım**: eklentiler olası güvenlik ve yürütme sorunları uygulamaları korumak, yalıtım sınırlarını kurmak için uygulama etki alanları veya işlemleri kullanarak.  
  
-   **İletişim**: birbirleriyle yöntemlerini çağırmaya ve veri geçirme yalıtım sınırlarının arasında iletişim için uygulamaları barındırmak ve eklentiler sağlar.  
  
-   **Ömür Yönetimi**: yükleme ve kaldırma uygulama etki alanları ve temiz, öngörülebilir bir şekilde işlemde (bkz [uygulama etki alanları](../../../../docs/framework/app-domains/application-domains.md)).  
  
-   **Sürüm oluşturma**: ya da yeni sürümlerini oluşturulduğunda konak uygulamalar ve eklentiler hala iletişim kurabildiklerinden emin olma.  
  
 Sonuç olarak, sağlam bir eklenti modeli geliştirme Önemsiz olmayan bir iş değil. Bu nedenle, [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] eklenti modeli oluşturmak için bir altyapı sağlar.  
  
> [!NOTE]
>  Eklentiler hakkında daha ayrıntılı bilgi için bkz: [eklentiler ve genişletilebilirlik](../../../../docs/framework/add-ins/index.md).  
  
<a name="NETFrameworkAddInModelOverview"></a>   
## <a name="net-framework-add-in-model-overview"></a>.NET framework eklenti modeli genel bakış  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Bulunan eklenti modeli, <xref:System.AddIn> ad alanı, eklenti genişletilebilirliği geliştirilmesini basitleştirmek için tasarlanmış türleri kümesi içerir. Temel birimini [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] eklenti modeli *sözleşme*eklenti birbiriyle ve ana bilgisayar uygulamasına nasıl tanımlar. Bir anlaşma kullanarak bir konak uygulamaya özgü bir ana bilgisayar uygulamasına sunulur *görünümü* sözleşme. Benzer şekilde, bir ekleme-özel *görünümü* sözleşme eklenti için sunulur. Bir *bağdaştırıcısı* bir konak uygulama ve bir eklenti ilgili kendi ilgili görünümler arasında iletişim kurmasına izin vermek için kullanılır. Sözleşmeler, görünümler ve bağdaştırıcılar adlandırılır segmentler ve ilgili kesimleri kümesi oluşturan bir *işlem hattı*. İşlem hatları temelini bağlı olan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] modelini destekleyen bulma, etkinleştirme, güvenlik yalıtımı, yürütme yalıtım (uygulama etki alanları ve işlemleri kullanarak), iletişim, ömür yönetimi ve sürüm oluşturma eklentisi.  
  
 Bu destek toplamını konak uygulamanın işlevselliğini tümleştirmek eklentileri geliştiricilerin sağlar. Ancak bazı senaryolar ana bilgisayar uygulamaları görüntülemek için gerekli [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] eklentiler tarafından sağlanan. Çünkü her sunu teknolojisinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] uygulamak için kendi modeline sahiptir [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)], [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] modeli, herhangi belirli sunu teknolojisi desteklemiyor eklentisi. Bunun yerine, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] genişletir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] eklenti modeli ile [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] eklentileri için destek.  
  
<a name="WPFAddInModel"></a>   
## <a name="wpf-add-ins"></a>WPF eklentileri  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], birlikte [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] eklenti modeli, çok çeşitli uygulamaları görüntülemek için barındırmak gerektiren senaryolar adresi olanak tanır [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] gelen eklentileri. Özellikle, bu senaryolar tarafından gönderilen [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aşağıdaki iki programlama modeli:  
  
1.  **Eklenti UI döndüren**. Bir eklenti döndürür bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] anlaşmada tanımlanan bir yöntem çağrısının üzerinden konak uygulama. Bu senaryo, aşağıdaki durumlarda kullanılır:  
  
    -   Görünümünü bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] tarafından döndürülen bir eklenti ya da verilere bağımlı veya yalnızca çalışma zamanında dinamik olarak gibi mevcut koşulları oluşturulan raporlar.  
  
    -   [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Eklentisi tarafından sağlanan hizmetleri için farklıdır [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ana bilgisayar uygulamalarının eklentiyi kullanabilirsiniz.  
  
    -   Eklenti öncelikle bir hizmet için ana bilgisayar uygulaması gerçekleştirir ve durumu raporları ile ana bilgisayar uygulaması için bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
2.  **Eklenti UI olan**. Bir eklentinin bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], sözleşmesi tarafından tanımlandığı şekilde. Bu senaryo, aşağıdaki durumlarda kullanılır:  
  
    -   Bir eklenti gibi bir reklam görüntülenen dışındaki hizmetleri sağlamaz.  
  
    -   [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Eklentisi tarafından sağlanan hizmetleri hesaplayıcıya veya Renk Seçici gibi eklenti kullanabileceğiniz tüm uygulamalarını barındırmak için yaygındır.  
  
 Bu senaryolar gerektiren [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] konak uygulama ve eklenti uygulama etki alanları arasında nesnelerin geçirilebilir. Bu yana [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] model iletişim kurmak için uygulama etki alanları arasında aralarında aktarılan nesneleri, Uzaktan erişilebilir olmalıdır uzaktan iletişim kullanır eklentisi.  
  
 Uzaktan erişilebilir bir veya daha fazlasını yapan bir sınıf örneği nesnedir:  
  
-   Öğesinden türetilen <xref:System.MarshalByRefObject> sınıfı.  
  
-   Implements <xref:System.Runtime.Serialization.ISerializable> arabirimi.  
  
-   Sahip <xref:System.SerializableAttribute> özniteliği uygulandı.  
  
> [!NOTE]
>  Uzaktan erişilebilir oluşturma hakkında daha fazla bilgi için [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] nesneleri bkz [nesneleri Uzaktan erişilebilir hale getirme](https://msdn.microsoft.com/library/01197253-3f13-43b7-894d-9683e431192a).  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Türleri Uzaktan erişilebilir değil. Sorunu çözmek için [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] genişletir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] etkinleştirmek için eklenti modeli [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ana uygulamalardan görüntülenmesi eklentiler tarafından oluşturulmuş. Bu destek tarafından sağlanan [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] iki tür tarafından: <xref:System.AddIn.Contract.INativeHandleContract> arabirimi ve iki statik yöntemler tarafından uygulanan <xref:System.AddIn.Pipeline.FrameworkElementAdapters> sınıfı: <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> ve <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>. Yüksek düzeyde, bu türleri ve yöntemleri şu şekilde kullanılır:  
  
1.  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] gerektiren [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] tarafından sağlanan eklentileri doğrudan veya dolaylı olarak türetilen sınıflardır <xref:System.Windows.FrameworkElement>şekiller, denetimleri, kullanıcı denetimleri, Düzen bölmeleri ve sayfaları gibi.  
  
2.  Sözleşme, eklenti ve barındırma uygulaması UI'dir geçirilecek bildirir her yerde, onu olarak bildirilmelidir bir <xref:System.AddIn.Contract.INativeHandleContract> (değil bir <xref:System.Windows.FrameworkElement>); <xref:System.AddIn.Contract.INativeHandleContract> eklenti, Uzaktan erişilebilir temsilidir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] yalıtım sınırlarında geçirilebilir.  
  
3.  Eklentinin uygulama etki alanından geçirilmeden önce bir <xref:System.Windows.FrameworkElement> olarak paketlenmiş bir <xref:System.AddIn.Contract.INativeHandleContract> çağırarak <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>.  
  
4.  Konak uygulamanın uygulama etki alanı için geçirilen sonra <xref:System.AddIn.Contract.INativeHandleContract> olarak paketlenmiş gereken bir <xref:System.Windows.FrameworkElement> çağırarak <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>.  
  
 Nasıl <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, ve <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> kullanılan belirli bir senaryoya bağlıdır. Aşağıdaki bölümlerde, her bir programlama modeli için ayrıntıları sağlayın.  
  
<a name="ReturnUIFromAddInContract"></a>   
## <a name="add-in-returns-a-user-interface"></a>Eklenti kullanıcı arayüzü döndürür.  
 Döndürülecek eklenti için bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] bir ana bilgisayar uygulaması için aşağıdakiler gereklidir:  
  
1.  Ana bilgisayar uygulaması, eklenti ve işlem hattı, açıklandığı oluşturulmalıdır [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] [eklentiler ve genişletilebilirlik](../../../../docs/framework/add-ins/index.md) belgeleri.  
  
2.  Sözleşme uygulamalıdır <xref:System.AddIn.Contract.IContract> ve döndürmek için bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], sözleşme türü dönüş değerine sahip bir yöntemi bildirmelidir <xref:System.AddIn.Contract.INativeHandleContract>.  
  
3.  [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Yapan eklenti ile konak uygulama doğrudan veya dolaylı olarak öğesinden türetilmelidir <xref:System.Windows.FrameworkElement>.  
  
4.  [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Tarafından döndürülen eklenti gelen dönüştürülmelidir bir <xref:System.Windows.FrameworkElement> için bir <xref:System.AddIn.Contract.INativeHandleContract> yalıtım sınırı geçmeden önce.  
  
5.  [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Dönüştürülmesi gerekir öğesinden döndürülen bir <xref:System.AddIn.Contract.INativeHandleContract> için bir <xref:System.Windows.FrameworkElement> yalıtım sınırı geçmesinden sonra.  
  
6.  Konak uygulama döndürülen görüntüler <xref:System.Windows.FrameworkElement>.  
  
 Döndürür bir eklenti uygulama gösteren bir örnek için bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], bkz: [bir eklenti döndüren bir kullanıcı Arabirimi oluşturma](../../../../docs/framework/wpf/app-development/how-to-create-an-add-in-that-returns-a-ui.md).  
  
<a name="AddInIsAUI"></a>   
## <a name="add-in-is-a-user-interface"></a>Bir kullanıcı arabirimi eklentisi olan  
 Bir eklenti olduğunda bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], aşağıdakiler gereklidir:  
  
1.  Ana bilgisayar uygulaması, eklenti ve işlem hattı, açıklandığı oluşturulmalıdır [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] [eklentiler ve genişletilebilirlik](../../../../docs/framework/add-ins/index.md) belgeleri.  
  
2.  Eklenti anlaşma arabirimi uygulamalıdır <xref:System.AddIn.Contract.INativeHandleContract>.  
  
3.  Ana uygulamaya geçirilen eklentiyi doğrudan veya dolaylı olarak öğesinden türetilmelidir <xref:System.Windows.FrameworkElement>.  
  
4.  Eklenti gelen dönüştürülmelidir bir <xref:System.Windows.FrameworkElement> için bir <xref:System.AddIn.Contract.INativeHandleContract> yalıtım sınırı geçmeden önce.  
  
5.  Eklenti gelen dönüştürülmelidir bir <xref:System.AddIn.Contract.INativeHandleContract> için bir <xref:System.Windows.FrameworkElement> yalıtım sınırı geçmesinden sonra.  
  
6.  Konak uygulama döndürülen görüntüler <xref:System.Windows.FrameworkElement>.  
  
 Nasıl bir eklentisi uygulayacağınızı gösteren bir örnek için bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], bkz: [bir eklenti olan bir kullanıcı Arabirimi oluşturma](../../../../docs/framework/wpf/app-development/how-to-create-an-add-in-that-is-a-ui.md).  
  
<a name="ReturningMultipleUIsFromAnAddIn"></a>   
## <a name="returning-multiple-uis-from-an-add-in"></a>Eklenti birden çok UI döndüren  
 Eklentiler, genellikle birden çok sağlar [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] görüntülenecek uygulamalarını barındırmak için. Örneğin, bir eklenti göz önünde bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ayrıca sağlayan konak uygulama durum bilgilerini de olarak bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Böyle bir eklenti hem tekniklerinin bir bileşimini kullanarak uygulanabilir [bir kullanıcı arayüzü döndürür eklenti](#ReturnUIFromAddInContract) ve [eklenti kullanıcı arayüzü](#AddInIsAUI) modelleri.  
  
<a name="AddInsAndXBAPs"></a>   
## <a name="add-ins-and-xaml-browser-applications"></a>Eklentiler ve XAML tarayıcı uygulamaları  
 Örneklerde, şu ana kadar yüklü tek başına uygulama konak uygulama olmuştur. Ancak [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] eklentileri, aşağıdaki ek derleme ve uygulama gereksinimleri paralelleştirmeye da barındırabilirsiniz:  
  
-   [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Uygulama bildirimi, işlem hattını (klasörleri ve derlemeleri) ve eklenti derlemesi için özel olarak indirmek için yapılandırılmalıdır [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] aynı klasörde bir istemci makine üzerinde uygulama önbelleğine [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)].  
  
-   [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Keşfedip eklentileri yükleyecek kod kullanmalıdır [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] uygulama önbelleği için [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] eklentisi ardışık düzen ve konum olarak.  
  
-   [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Eklenti tarafından barındırıldığında; kaynak sitede bulunan gevşek dosyalar başvuruyorsa bir özel güvenlik bağlamına eklenti gerekir [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], add-INS konak uygulamanın sitede bulunan gevşek dosyalar yalnızca başvurabilir kaynağı.  
  
 Bu görevleri, aşağıdaki alt bölümlerde ayrıntılı olarak açıklanmıştır.  
  
### <a name="configuring-the-pipeline-and-add-in-for-clickonce-deployment"></a>İşlem hattı ve ClickOnce dağıtımı için eklentiyi yapılandırma  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] için indirilir ve güvenli bir klasörde çalıştırılan [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] dağıtım önbellek. Sırayla bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] eklenti barındırmak için işlem hattı ve eklenti bütünleştirilmiş kod da güvenli klasöre yüklenmelidir. Bunu başarmak için uygulama bildirimini işlem hattı ve eklenti derlemesini içerecek şekilde yapılandırmanız gerekir. Bu en bir kolayca yapılabilir [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], işlem hattı ve eklenti derlemesi konak olması gerekiyor ancak [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] projesinin kök klasörüne sırayla [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] ardışık düzen derlemeleri algılamak için.  
  
 Sonuç olarak, Eklenti derlemesine ve işlem hattı oluşturmak için ilk adım olan [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] yapı çıkışını her işlem hattı ayarlayarak derleme projeleri derleme ve Eklenti projesinin kök. Aşağıdaki tabloda çözüm ve kök klasörde konağı olarak işlem hattı derleme projeleri ve derleme eklenti projesi yapı çıkış yolları gösterilmektedir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] proje.  
  
 Tablo 1: Bir XBAP tarafından barındırılan işlem hattı derlemeler için çıktı yollarında oluşturun.  
  
|İşlem hattı derleme projesi|Yapı çıkış yolu|  
|-------------------------------|-----------------------|  
|Daralma|`..\HostXBAP\Contracts\`|  
|Eklenti görünümü|`..\HostXBAP\AddInViews\`|  
|Ekleme tarafı bağdaştırıcısı|`..\HostXBAP\AddInSideAdapters\`|  
|Konak tarafı bağdaştırıcısı|`..\HostXBAP\HostSideAdapters\`|  
|Eklentisi|`..\HostXBAP\AddIns\WPFAddIn1`|  
  
 Eklenti derleme olarak ve işlem hattı derlemeleri belirtmek için sonraki adımdır [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] içerik dosyaları [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] aşağıdakileri yaparak:  
  
1.  Her işlem hattı klasör Çözüm Gezgini'nde sağ tıklayıp seçerek işlem hattı ve eklenti bütünleştirilmiş kod projesinde dahil **projeye dahil et**.  
  
2.  Ayarı **derleme eylemi** her işlem hattı derleme ve Eklenti derlemesine **içerik** gelen **özellikleri** penceresi.  
  
 Son adım, işlem hattı derleme dosyaları ve derleme eklenti dosyası indirme için eklenecek uygulama bildirimi yapılandırmaktır. Klasörün kökünde klasörlerdeki dosyaları yerleştirilmelidir [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] önbelleğindeki [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] uygulama kaplar. Yapılandırma sağlanabilir [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] aşağıdakileri yaparak:  
  
1.  Sağ tıklayın [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] proje, tıklayın **özellikleri**, tıklayın **Yayımla**ve ardından **uygulama dosyaları** düğmesi.  
  
2.  İçinde **uygulama dosyaları** iletişim kutusunda, kümesi **yayımlama durumu** her işlem hattı ve DLL eklentisini **Ekle (otomatik)** ve **indirmegrubu** her işlem hattı ve DLL eklentisini **(gerekli)**.  
  
### <a name="using-the-pipeline-and-add-in-from-the-application-base"></a>İşlem hattı ve kullanarak uygulama tabanından  
 Ne zaman işlem hattı ve için yapılandırıldığında [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] dağıtım, aynı yüklenen [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] Önbellek klasörü olarak [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]. İşlem hattını kullanma ve gelen eklentisi için [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] kodu gerekir alma bunları uygulamadan temel. Çeşitli türleri ve üyeleri [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] işlem hatları ve eklentileri kullanma eklenti modeli, bu senaryo için özel destek sağlar. İlk olarak, yol ile tanımlanan <xref:System.AddIn.Hosting.PipelineStoreLocation.ApplicationBase> numaralandırma değeri. Aşağıdakileri içeren işlem hattı kullanmak için uygun eklenti üyeleri aşırı yüklemeleri ile bu değeri kullanın:  
  
-   <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>  
  
-   <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%2CSystem.String%5B%5D%29?displayProperty=nameWithType>  
  
-   <xref:System.AddIn.Hosting.AddInStore.Rebuild%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>  
  
-   <xref:System.AddIn.Hosting.AddInStore.Update%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>  
  
### <a name="accessing-the-hosts-site-of-origin"></a>Ana bilgisayarın Site kaynak erişimi  
 Eklenti dosyaları kaynak siteden başvurabileceğini emin olmak için eklentinin ana bilgisayar uygulamasına eşdeğerdir ve güvenlik yalıtımı ile yüklenmesi gerekir. Bu güvenlik düzeyi tarafından tanımlanan <xref:System.AddIn.Hosting.AddInSecurityLevel.Host?displayProperty=nameWithType> numaralandırma değeri geçirilir <xref:System.AddIn.Hosting.AddInToken.Activate%2A> eklenti etkinleştirildiğinde yöntemi.  
  
<a name="WPFAddInModelArchitecture"></a>   
## <a name="wpf-add-in-architecture"></a>WPF eklentisi mimarisi  
 En üst düzeyde anlatıldığı gibi [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sağlayan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] uygulamak için eklentiler [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] (, türetilen doğrudan veya dolaylı olarak <xref:System.Windows.FrameworkElement>) kullanarak <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> ve <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>. Ana bilgisayar uygulaması döndürülür sonucu olan bir <xref:System.Windows.FrameworkElement> den görüntülenen [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] konak uygulama.  
  
 Basit için [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] eklenti senaryoları için bu, bir geliştiricinin ihtiyaç duyduğu kadar ayrıntı. Daha karmaşık senaryolarda, özellikle de, denemek için ek yazılımınız [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] düzen, kaynakları ve veri bağlama, bilgi ilişkin daha ayrıntılı gibi hizmetleri [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] genişletir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] eklenti modeli ile [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Destek, avantajları ve sınırlamaları anlamak için gereklidir.  
  
 Temelde, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] geçmiyor bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ndan bir eklenti için bir ana bilgisayar uygulaması; bunun yerine, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Win32 pencere tanıtıcısı geçirir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] kullanarak [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] birlikte çalışabilirlik. Bu nedenle, bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] bir eklentiyi bir ana bilgisayar uygulamasına aşağıdakiler gerçekleşir geçirilir:  
  
-   Eklenti tarafında [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] alması için bir pencere tutucu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] konak uygulama tarafından görüntülenir. Pencere tanıtıcısı bir iç kapsüllenir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] türetilen sınıf <xref:System.Windows.Interop.HwndSource> ve uygulayan <xref:System.AddIn.Contract.INativeHandleContract>. Bu sınıfın bir örneği tarafından döndürülen <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> ve eklentinin uygulama etki alanından konak uygulamanın uygulama etki alanına taşınır.  
  
-   Konak uygulama tarafında [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tüketen <xref:System.Windows.Interop.HwndSource> bir iç [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] türetilen sınıf <xref:System.Windows.Interop.HwndHost> ve <xref:System.AddIn.Contract.INativeHandleContract>. Bu sınıfın bir örneği tarafından döndürülen <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> konak uygulama.  
  
 <xref:System.Windows.Interop.HwndHost> Görüntülenecek var. [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)], gelen pencere işleyicisi ile tanımlanan [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]. Daha fazla bilgi için [WPF ve Win32 birlikte çalışması](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md).  
  
 Özet olarak, <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, ve <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> için Pencere işleyicisi izin vermek için mevcut bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] bir eklentiyi Burada, saklanmış olduğu tarafından bir ana bilgisayar uygulaması geçirilecek bir <xref:System.Windows.Interop.HwndHost> ve konak görüntülenir uygulamanın [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
> [!NOTE]
>  Ana bilgisayar uygulaması aldığından bir <xref:System.Windows.Interop.HwndHost>, ana bilgisayar uygulaması tarafından döndürülen nesne dönüştürülemiyor <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> eklenti tarafından uygulanan türüne (örneğin, bir <xref:System.Windows.Controls.UserControl>).  
  
 Doğası, <xref:System.Windows.Interop.HwndHost> uygulamalarını barındırmak bunları nasıl kullanabileceğiniz etkileyen belirli sınırlamaları vardır. Ancak, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] genişletir <xref:System.Windows.Interop.HwndHost> eklenti senaryoları için çeşitli özelliklere sahip. Bu avantajlar ve sınırlamalar aşağıda açıklanmıştır.  
  
<a name="WPFAddInModelBenefits"></a>   
## <a name="wpf-add-in-benefits"></a>WPF eklentisi avantajları  
 Çünkü [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] eklentisi [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] türetildiği bir iç sınıf kullanarak ana uygulamadan görüntülenen <xref:System.Windows.Interop.HwndHost>, bu [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] yeteneklerini tarafından kısıtlanmış <xref:System.Windows.Interop.HwndHost> ilişkilendirilebilmesi için [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] düzen, işleme, veri bağlama, stiller, şablonlar ve kaynakları gibi hizmetler. Ancak, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] iç artırmaktadır <xref:System.Windows.Interop.HwndHost> aşağıdakiler dahil ek özellikler olan alt sınıf:  
  
-   Konak uygulamanın arasında sekmeyle gitmeyi [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ve bir eklentinin [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Dikkat "eklenti bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]" programlama modeli, geçersiz kılmak Ekle tarafı bağdaştırıcısı gerektirir <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> sekmeyi, eklentinin tam güvenilir veya kısmen güvenilen etkinleştirmek için.  
  
-   Eklenti için erişilebilirlik gereksinimleri uygularken [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] konak uygulama görüntülenen [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)].  
  
-   Etkinleştirme [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamaları birden çok uygulama etki alanı senaryolarında güvenli bir şekilde çalıştırmak için.  
  
-   Eklenti için geçersiz erişimi önleme [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] penceresi eklentileri (diğer bir deyişle, kısmi güven güvenliği sandbox) güvenlik yalıtımı ile çalıştırdığınızda işler. Çağırma <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> bu güvenlik sağlar:  
  
    -   İçin "eklenti döndürür bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]" programlama modeli, eklenti için Pencere işleyicisi geçirilecek tek yolu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] arasında yalıtım sınırı çağırmaktır <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>.  
  
    -   İçin "eklenti bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]" programlama modeli, geçersiz kılma <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> arama ve ekleme tarafı bağdaştırıcısı <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> (önceki örneklerde gösterildiği gibi), ekleme tarafı bağdaştırıcının çağırma gibi gereklidir `QueryContract` uygulama konak tarafı bağdaştırıcısından.  
  
-   Birden çok uygulama etki alanı yürütme korumasını sağlama. Yalıtım sınırı yer alsa bile uygulama etki alanlarıyla sınırlamaları nedeniyle, eklenti uygulama etki alanında oluşturulan işlenmeyen özel durumları uygulamanın tamamı çökmesine neden. Ancak, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ve [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] eklenti modeli Bu sorunu gidermek ve uygulama kararlılığını artırmak için basit bir yol sağlar. A [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] görüntüler eklenti bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] oluşturur bir <xref:System.Windows.Threading.Dispatcher> ana bilgisayar uygulaması ise, uygulama etki alanı üzerinde çalıştığı iş parçacığı için bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulama. Uygulama etki alanında işleyerek meydana gelen tüm işlenmemiş özel durumları algılayabilirsiniz <xref:System.Windows.Threading.Dispatcher.UnhandledException> olayı [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] eklentinin <xref:System.Windows.Threading.Dispatcher>. Alabileceğiniz <xref:System.Windows.Threading.Dispatcher> gelen <xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A> özelliği.  
  
<a name="WPFAddInModelLimitations"></a>   
## <a name="wpf-add-in-limitations"></a>WPF eklentisi sınırlamaları  
 Avantajları ötesinde, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tarafından sağlanan varsayılan davranışlar ekler <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost>ve pencere işleyicileri da eklenti için sınırlamalar vardır [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] ana uygulamalardan görüntülenir:  
  
-   Eklenti [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] görüntülenen bir konaktan uygulama konak uygulamanın kırpma davranışını almaz.  
  
-   Kavramını *hava sahası* birlikte çalışabilirlik senaryolarında de eklentiler için geçerlidir (bkz [teknoloji bölgelerine genel bakış](../../../../docs/framework/wpf/advanced/technology-regions-overview.md)).  
  
-   Konak uygulamanın [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] kaynağı devralma, veri bağlama ve kumanda gibi hizmetler eklenti otomatik olarak kullanılabilir olmayan [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]. Eklenti, bu hizmetleri sağlamak üzere işlem hattı güncelleştirmeniz gerekiyor.  
  
-   Bir eklenti [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] döndürülemez, ölçeği, dengesiz veya aksi halde bir dönüştürme tarafından etkilenen (bkz [dönüştüren genel bakış](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)).  
  
-   İçerik Eklentisi içinde [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] işlemlerinden çizerek işlenen <xref:System.Drawing> ad alanı, alfa karıştırma içerebilir. Ancak, her iki eklentiyi [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ve ana bilgisayar uygulaması [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] içerdiği % 100 katı olmalıdır; diğer bir deyişle, `Opacity` hem de özelliği 1 olarak ayarlanması gerekir.  
  
-   Varsa <xref:System.Windows.Window.AllowsTransparency%2A> eklenti içeren konak uygulama penceresinde özelliği [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ayarlanır `true`, eklentiyi görünmezdir. Bu durum geçerlidir bile eklenti [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] % 100 donuktur (diğer bir deyişle, `Opacity` özelliği 1 değerine sahip).  
  
-   Bir eklenti [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] diğer üzerine görünmelidir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aynı üst düzey pencere öğeleri.  
  
-   Bir eklentinin hiçbir kısmı [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] kullanarak işlenebilecek bir <xref:System.Windows.Media.VisualBrush>. Bunun yerine, eklenti oluşturulan anlık [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] anlaşmada tanımlanan yöntemleri kullanarak konak uygulamaya geçirilen bir bit eşlem oluşturmak için.  
  
-   Medya dosyaları, gelen yürütülemez bir <xref:System.Windows.Controls.MediaElement> içinde bir eklenti [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
-   Fare olayları için oluşturulan [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] almaz veya konak uygulama tarafından oluşturulan ve `IsMouseOver` özelliği için ana bilgisayar uygulaması [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] değeri `false`.  
  
-   Zaman içinde bir eklenti denetimler arasındaki kaydırır [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], `GotFocus` ve `LostFocus` olayları almaz veya konak uygulama tarafından oluşturulur.  
  
-   Bir eklenti içeren bir ana bilgisayar uygulaması bölümünü [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] yazdırıldığında beyaz görünür.  
  
-   Tüm dağıtıcıları (bkz <xref:System.Windows.Threading.Dispatcher>) tarafından oluşturulan [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] konak uygulama yürütme devam ederse sahibi Eklenti kaldırılmadan önce el ile kapatılmalıdır. Sözleşme, eklenti eklenti, böylece Eklenti kaldırılmadan önce göstermek konak uygulama izin yöntemleri uygulayabilirsiniz [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] kendi Dispatcher için.  
  
-   Eğer bir eklenti [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] olduğu bir <xref:System.Windows.Controls.InkCanvas> ya da içeren bir <xref:System.Windows.Controls.InkCanvas>, eklenti kaldıramıyor.  
  
<a name="PerformanceOptimization"></a>   
## <a name="performance-optimization"></a>Performansı iyileştirme  
 Birden çok uygulama etki alanı kullanıldığında, varsayılan olarak çeşitli [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] her uygulama için gereken derlemeler bu uygulama etki alanına yüklenir. Sonuç olarak, yeni uygulama etki alanları oluşturma ve uygulamalar bunları başlatmak için gereken süreyi performansını etkileyebilir. Ancak, [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zaten yüklü olduğundan, derlemeleri uygulama etki alanları arasında paylaşmak için uygulamaları yönlendirerek başlangıç zamanı azaltmak bir yol sağlar. Kullanarak bunu <xref:System.LoaderOptimizationAttribute> giriş noktası yöntemi için uygulanması gereken özniteliği (`Main`). Bu durumda, uygulama tanımınız uygulamak için yalnızca kod kullanmanız gerekir (bkz [uygulama yönetimine genel bakış](../../../../docs/framework/wpf/app-development/application-management-overview.md)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.LoaderOptimizationAttribute>  
 [Eklentiler ve Genişletilebilirlik](../../../../docs/framework/add-ins/index.md)  
 [Uygulama Etki Alanları](../../../../docs/framework/app-domains/application-domains.md)  
 [.NET framework uzaktan iletişimi genel bakış](https://msdn.microsoft.com/library/eccb1d31-0a22-417a-97fd-f4f1f3aa4462)  
 [Nesneleri Uzaktan erişilebilir hale getirme](https://msdn.microsoft.com/library/01197253-3f13-43b7-894d-9683e431192a)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/app-development/how-to-topics.md)
