---
title: "WPF Eklentilerine Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "36"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ffd45957b41cdfd8488aedd865aa70ef5b2634b2
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="wpf-add-ins-overview"></a>WPF Eklentilerine Genel Bakış
<a name="Introduction"></a>[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Geliştiricilerin eklenti genişletilebilirliği destekleyen uygulamalar oluşturmak için kullanabileceği bir eklenti modeli içerir. Bu eklenti modeli ile tümleştirilebilen ve uygulama işlevselliğini genişleten eklentiler oluşturulmasına izin verir. Bazı senaryolarda uygulamalar da görüntülemeniz [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] eklentileri tarafından sağlanır. Bu konuda gösterilmektedir nasıl [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] güçlendirir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] bu senaryolar, arkasındaki mimariyi, faydalarını ve kısıtlamalarını sağlamak için eklenti modeli.  
  

  
<a name="Requirements"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Aşina [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] modeli gereklidir eklentisi. Daha fazla bilgi için bkz: [eklentiler ve genişletilebilirlik](../../../../docs/framework/add-ins/index.md).  
  
<a name="AddInsOverview"></a>   
## <a name="add-ins-overview"></a>Eklentilere genel bakış  
 Uygulama yeniden derlenmek ve yeni işlevsellikler eklemek için yeniden dağıtım karmaşıklığını önlemek için için geliştiricilerin (birinci taraf ve üçüncü taraf) izin genişletilebilirlik mekanizmalar uygulamaları uygulaması diğer uygulamaları oluşturma bunları ile tümleştirin. Eklentiler kullanımı ile ("eklentiler" ve "eklentiler" olarak da bilinir) bu tür genişletilebilirliği desteklemek için en yaygın yoludur. Eklentiler genişletilebilirlik kullanıma gerçek uygulamalar örnekleri şunlardır:  
  
-   Internet Explorer eklentileri.  
  
-   Windows Media Player eklentileri.  
  
-   Visual Studio eklentileri.  
  
 Örneğin, "Windows Media Player kod çözücüleri ve Windows tarafından yerel olarak desteklenmeyen medya biçimleri için kodlayıcılar oluşturma dahil olmak üzere çeşitli genişleten eklentileri" uygulamak üçüncü taraf geliştiricilerin eklenti Windows Media Player modeli sağlar Media Player (örneğin, DVD, MP3), ses etkiler ve görünümler. Her eklenti modeli vardır, ancak çeşitli varlıkları ve eklenti tüm modelleri için ortak olan davranışları bir uygulama için benzersiz olan işlevselliği kullanıma sunmak için yerleşik olarak bulunur.  
  
 Üç ana varlıklardır tipik Genişletilebilirlik çözümlerinin *sözleşmeleri*, *eklentileri*, ve *konak uygulamalar*. İki yolla konak uygulamaların nasıl eklentiler tümleştirileceğini sözleşmeleri tanımlayın:  
  
-   Eklentiler konak uygulamalar tarafından uygulanan işlevselliği ile tümleştirin.  
  
-   Ana bilgisayar uygulamaları ile tümleştirmek eklentiler için işlevselliği kullanıma sunar.  
  
 Kullanılacak eklentiler için konak uygulamalar bulup bunları çalışma zamanında yük gerekir. Sonuç olarak, eklentiler destekleyen uygulamalar aşağıdaki ek sorumlulukları vardır:  
  
-   **Bulma**: konak uygulamalar tarafından desteklenen sözleşmeleri uygun Eklentiler bulma.  
  
-   **Etkinleştirme**: çalıştıran ve eklentiler ile iletişim kurma yükleniyor.  
  
-   **Yalıtım**: uygulama etki alanları veya işlemler uygulamaları eklentiler olası güvenlik ve yürütme sorunları korunmasına yalıtım sınırları kurulacak kullanarak.  
  
-   **İletişim**: eklentiler izin vererek ve birbirleri ile yalıtım sınırlarında yöntemleri çağırma ve veri geçirerek iletişim kurmak için uygulamaları barındırmak.  
  
-   **Ömür yönetimini**: yükleme ve yüklemeyi kaldırma uygulama etki alanları ve işlemleri temiz, tahmin edilebilir şekilde (bkz [uygulama etki alanları](../../../../docs/framework/app-domains/application-domains.md)).  
  
-   **Sürüm oluşturma**: ya da yeni sürümlerini oluşturulduğunda konak uygulamalar ve eklentiler hala iletişim kurabildiklerinden emin olma.  
  
 Sonuç olarak, sağlam bir eklenti modeli geliştirmek Önemsiz olmayan bir iş değil. Bu nedenle, [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] eklenti modeli oluşturmak için bir altyapı sağlar.  
  
> [!NOTE]
>  Eklentiler hakkında daha ayrıntılı bilgi için bkz: [eklentiler ve genişletilebilirlik](../../../../docs/framework/add-ins/index.md).  
  
<a name="NETFrameworkAddInModelOverview"></a>   
## <a name="net-framework-add-in-model-overview"></a>.NET framework eklenti modeli genel bakış  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Bulunan eklenti modeli, <xref:System.AddIn> ad alanı, eklenti genişletilebilirliği geliştirilmesini basitleştirmek üzere tasarlanmış türleri kümesi içerir. Temel birimi [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] eklenti modeli *sözleşme*bir eklenti birbiriyle ve bir ana bilgisayar uygulaması nasıl tanımlar. Bir anlaşma bir konak uygulamaya özgü kullanarak bir ana bilgisayar uygulaması sunulur *Görünüm* sözleşme. Benzer şekilde, bir ekleme-içinde özgü *Görünüm* anlaşma Ekle bileşenini sunulur. Bir *bağdaştırıcısı* bir konak uygulama ve bir eklenti ilgili kendi anlaşma görünümler arasında iletişim kurmasına izin vermek için kullanılır. Sözleşmeler, görünümler ve bağdaştırıcıları adlandırılır parçaları olarak ve ilgili kesimleri kümesi oluşturan bir *ardışık düzen*. Ardışık Düzen temelidir bağlı [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] modelini destekleyen bulma, etkinleştirme, güvenlik yalıtımı, yürütme yalıtımı (uygulama etki alanları ve işlemleri kullanarak), iletişim, ömür yönetimi ve sürüm oluşturma eklentisi.  
  
 Bu destek toplamını geliştiricilerin bir ana bilgisayar uygulaması işlevselliği ile tümleştirmek eklentiler oluşturmasını sağlar. Ancak, bazı senaryolar görüntülemek için konak uygulamaların gerektiren [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] eklenti tarafından sağlanan. Çünkü her sunu teknolojisinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] uygulamak için kendi modelinin [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)], [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] modeli herhangi belirli sunu teknolojisi desteklemediği eklentisi. Bunun yerine, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] genişletir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] eklenti modeliyle [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] eklentileri için destek.  
  
<a name="WPFAddInModel"></a>   
## <a name="wpf-add-ins"></a>WPF eklentileri  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], birlikte [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] eklenti modeli, çok çeşitli görüntülemek için konak uygulamaların gerektiren senaryolar adres sayesinde [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] eklentileri gelen. Özellikle, bu senaryo tarafından ele alınan [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aşağıdaki iki programlama modeli ile:  
  
1.  **Eklenti bir UI döndürür**. Bir eklenti döndüren bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] anlaşma tarafından tanımlandığı şekilde bir yöntem çağrısı aracılığıyla konak uygulamaya. Bu senaryoda aşağıdaki durumlarda kullanılır:  
  
    -   Görünümünü bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] tarafından döndürülen bir eklenti ya da verilere bağımlı veya yalnızca çalışma zamanında dinamik olarak gibi mevcut koşullar oluşturulan raporlar.  
  
    -   [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Eklenti tarafından sağlanan hizmetler için farklı [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] konak uygulamalarının eklenti kullanabilirsiniz.  
  
    -   Eklenti öncelikle konak uygulama için bir hizmet gerçekleştirir ve durum raporları ile ana bilgisayar uygulaması için bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
2.  **Bir kullanıcı Arabirimi eklentidir**. Bir eklenti bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], anlaşma tarafından tanımlandığı şekilde. Bu senaryoda aşağıdaki durumlarda kullanılır:  
  
    -   Bir eklenti gibi bir reklam görüntülenmesini dışında bir hizmet sağlamaz.  
  
    -   [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Eklenti tarafından sağlanan hizmetlerin hesaplayıcı veya Renk Seçici gibi eklenti kullanabileceğiniz tüm ana bilgisayar uygulamaları için ortak içindir.  
  
 Bu senaryolar gerektiren [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] konak uygulama ve eklenti uygulama etki alanları arasında nesneleri geçirilebilir. Bu yana [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] modeli kullanır iletişim kurmak için uygulama etki alanları arasında bunlar arasında geçirilen nesneleri, Uzaktan erişilebilir olmalıdır uzaktan iletişim eklentisi.  
  
 Bir veya daha fazlasını yapar sınıfının bir örneği Uzaktan erişilebilir nesnesidir:  
  
-   Türetilen <xref:System.MarshalByRefObject> sınıfı.  
  
-   Implements <xref:System.Runtime.Serialization.ISerializable> arabirimi.  
  
-   Sahip <xref:System.SerializableAttribute> özniteliği uygulanmıştır.  
  
> [!NOTE]
>  Uzaktan erişilebilir oluşturulmasına ilişkin daha fazla bilgi için [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] nesneleri bkz [nesneleri Uzaktan erişilebilir hale getirme](http://msdn.microsoft.com/library/01197253-3f13-43b7-894d-9683e431192a).  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Türleri Uzaktan erişilebilir değil. Sorunu çözmek için [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] genişletir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] etkinleştirmek için eklenti modeli [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] konak uygulamadan görüntülenecek eklentileri tarafından oluşturulmuş. Bu destek tarafından sağlanan [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] iki tür tarafından: <xref:System.AddIn.Contract.INativeHandleContract> arabirimi ve tarafından uygulanan iki statik yöntemler <xref:System.AddIn.Pipeline.FrameworkElementAdapters> sınıfı: <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> ve <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>. Yüksek düzeyde, aşağıdaki şekilde bu türleri ve yöntemleri kullanılır:  
  
1.  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]gerektiren [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] tarafından sağlanan eklentiler doğrudan veya dolaylı olarak türetilen sınıflardır <xref:System.Windows.FrameworkElement>şekiller, denetimler, kullanıcı denetimleri, Düzen panelleri ve sayfalar gibi.  
  
2.  Bir kullanıcı Arabirimi eklentisi ve konak uygulama arasında geçirilir sözleşme bildirir olduğunda, onu olarak bildirilmelidir bir <xref:System.AddIn.Contract.INativeHandleContract> (olmayan bir <xref:System.Windows.FrameworkElement>); <xref:System.AddIn.Contract.INativeHandleContract> bir eklenti Uzaktan erişilebilir gösterimidir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] yalıtım sınırlarında geçirilebilir.  
  
3.  Eklentinin uygulama etki alanından iletilmeden önce bir <xref:System.Windows.FrameworkElement> olarak paketlenmiş bir <xref:System.AddIn.Contract.INativeHandleContract> çağırarak <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>.  
  
4.  Konak uygulamanın uygulama etki alanı için geçirilen sonra <xref:System.AddIn.Contract.INativeHandleContract> olarak paketlenmiş gerekir bir <xref:System.Windows.FrameworkElement> çağırarak <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>.  
  
 Nasıl <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, ve <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> kullanılan belirli senaryoya bağlıdır. Aşağıdaki bölümler, her bir programlama modeli için ayrıntıları sağlar.  
  
<a name="ReturnUIFromAddInContract"></a>   
## <a name="add-in-returns-a-user-interface"></a>Bir kullanıcı arabirimi eklentisi döndürür  
 Döndürülecek eklenti için bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] bir ana bilgisayar uygulaması için aşağıdakiler gereklidir:  
  
1.  Konak uygulama, eklenti ve ardışık düzen, tarafından açıklandığı şekilde oluşturulmalıdır [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] [eklentiler ve genişletilebilirlik](../../../../docs/framework/add-ins/index.md) belgeleri.  
  
2.  Sözleşme uygulamalıdır <xref:System.AddIn.Contract.IContract> ve döndürmek için bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], sözleşme türü dönüş değeri olan bir yöntem bildirmelidir <xref:System.AddIn.Contract.INativeHandleContract>.  
  
3.  [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , Geçirilen eklenti ve ana bilgisayar arasında uygulama doğrudan veya dolaylı olarak öğesinden türetilmelidir <xref:System.Windows.FrameworkElement>.  
  
4.  [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Tarafından döndürdü eklenti gelen dönüştürülmelidir bir <xref:System.Windows.FrameworkElement> için bir <xref:System.AddIn.Contract.INativeHandleContract> yalıtım sınırı geçmeden önce.  
  
5.  [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Dönüştürülmesi gerekir öğesinden döndürülen bir <xref:System.AddIn.Contract.INativeHandleContract> için bir <xref:System.Windows.FrameworkElement> yalıtım sınırını geçmesinden sonra.  
  
6.  Konak uygulama döndürülen görüntüler <xref:System.Windows.FrameworkElement>.  
  
 Döndüren bir eklenti uygulamak nasıl gösteren bir örnek için bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], bkz: [bir eklenti döndüren bir kullanıcı Arabirimi oluşturma](../../../../docs/framework/wpf/app-development/how-to-create-an-add-in-that-returns-a-ui.md).  
  
<a name="AddInIsAUI"></a>   
## <a name="add-in-is-a-user-interface"></a>Olan bir kullanıcı arabirimi eklentisi  
 Bir eklenti olduğunda bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], aşağıdakiler gereklidir:  
  
1.  Konak uygulama, eklenti ve ardışık düzen, tarafından açıklandığı şekilde oluşturulmalıdır [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] [eklentiler ve genişletilebilirlik](../../../../docs/framework/add-ins/index.md) belgeleri.  
  
2.  Eklenti için sözleşme arabirimi uygulamalıdır <xref:System.AddIn.Contract.INativeHandleContract>.  
  
3.  Konak uygulamaya geçirilen eklenti doğrudan veya dolaylı olarak öğesinden türetilmelidir <xref:System.Windows.FrameworkElement>.  
  
4.  Eklenti gelen dönüştürülmelidir bir <xref:System.Windows.FrameworkElement> için bir <xref:System.AddIn.Contract.INativeHandleContract> yalıtım sınırı geçmeden önce.  
  
5.  Eklenti gelen dönüştürülmelidir bir <xref:System.AddIn.Contract.INativeHandleContract> için bir <xref:System.Windows.FrameworkElement> yalıtım sınırını geçmesinden sonra.  
  
6.  Konak uygulama döndürülen görüntüler <xref:System.Windows.FrameworkElement>.  
  
 Bir eklenti uygulamak nasıl gösteren bir örnek için bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], bkz: [bir eklenti olan bir kullanıcı Arabirimi oluşturma](../../../../docs/framework/wpf/app-development/how-to-create-an-add-in-that-is-a-ui.md).  
  
<a name="ReturningMultipleUIsFromAnAddIn"></a>   
## <a name="returning-multiple-uis-from-an-add-in"></a>Bir Eklentiden Çoklu UI Döndürme  
 Eklentiler genellikle birden çok sağlar [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] görüntülemek ana bilgisayar uygulamaları için. Örneğin, bir eklenti düşünün bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de sağlayan konak uygulama durum bilgilerini de olarak bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Böyle bir eklenti hem teknikler birleşimini kullanarak uygulanabilir [bir kullanıcı arayüzü eklenti döndürür](#ReturnUIFromAddInContract) ve [eklenti kullanıcı arayüzü](#AddInIsAUI) modeller.  
  
<a name="AddInsAndXBAPs"></a>   
## <a name="add-ins-and-xaml-browser-applications"></a>Eklentiler ve XAML tarayıcısı uygulamaları  
 Örneklerde, o ana kadarki yüklü tek başına uygulama konak uygulama olmuştur. Ancak [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] eklentiler, aşağıdaki ek yapı ve uygulama gereksinimleri ile barındırabilir de barındırabilir:  
  
-   [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Uygulama bildirimi yapılandırılmış, ardışık düzen (klasörleri ve derlemeler) ve eklenti derlemesi için özel olarak indirmek için [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] uygulama önbelleği istemci makinesinde aynı klasöre [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)].  
  
-   [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Bulmak ve eklentiler yüklemek için kodu kullanmalıdır [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] uygulama önbelleği için [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] ardışık düzen ve eklenti konumu olarak.  
  
-   [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Eklenti tarafından barındırıldığında kaynak; sitesinde bulunan gevşek dosyalara erişiyorsa eklentisi bir özel güvenlik bağlamına yüklemelidir [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], Eklentiler yalnızca konak uygulamanın sitede bulunan gevşek dosyalarını başvurusu kaynağı.  
  
 Bu görevler, aşağıdaki alt bölümlerde ayrıntılı olarak açıklanmıştır.  
  
### <a name="configuring-the-pipeline-and-add-in-for-clickonce-deployment"></a>Ardışık Düzen ve eklenti ClickOnce dağıtım için yapılandırma  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]için indirilir ve güvenli bir klasörde çalıştırma [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] dağıtım önbelleği. Sırayla bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] bir eklenti barındırmak için ardışık düzen ve eklenti derlemesi da güvenli klasöre karşıdan yüklenmesi gerekir. Bunun için uygulama bildirimini ardışık düzen ve eklenti derlemesini içerecek biçimde yapılandırmanız gerekir. Bu en kolay yapılır [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], ardışık düzen ve eklenti derlemesi ana bilgisayar olması gerekiyor ancak [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] projenin kök klasörü için sırayla [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] ardışık düzen derlemeleri algılamak için.  
  
 Sonuç olarak, ilk adım ardışık düzen ve eklenti derlemesi için oluşturmaktır [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] derleme ve eklenti derleme projeleri her ardışık düzen derleme çıktısı ayarlayarak projenin kök. Aşağıdaki tabloda aynı klasörde çözüm ve kök konak ardışık düzen derleme projeleri ve eklenti derleme projesi derleme çıktı yolları gösterilmektedir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] projesi.  
  
 Tablo 1: Bir XBAP tarafından barındırılan ardışık düzen derlemeler için çıktı yolları derleme  
  
|Ardışık düzen derleme projesi|Derleme çıktı yolu|  
|-------------------------------|-----------------------|  
|Daralma|`..\HostXBAP\Contracts\`|  
|Eklenti görünümü|`..\HostXBAP\AddInViews\`|  
|Ekleme tarafı bağdaştırıcı|`..\HostXBAP\AddInSideAdapters\`|  
|Konak tarafındaki bağdaştırıcı|`..\HostXBAP\HostSideAdapters\`|  
|Eklentisi|`..\HostXBAP\AddIns\WPFAddIn1`|  
  
 Ardışık Düzen derlemeler ve eklenti derleme olarak belirtmek için sonraki adımdır [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] içerik dosyalarını [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] aşağıdakileri yaparak:  
  
1.  Ardışık Düzen ve eklenti derlemesi projede Çözüm Gezgini'ndeki her ardışık düzen klasörüne sağ tıklayıp seçerek de dahil olmak üzere **projeye dahil et**.  
  
2.  Ayarı **yapı eylemi** her bir ardışık düzen derleme ve eklenti derlemesi için **içerik** gelen **özellikleri** penceresi.  
  
 Uygulama bildirimini eklenti derleme dosyası indirmek ve ardışık düzen derleme dosyalarını içerecek biçimde yapılandırmak için son adım olacaktır. Klasörlerde kökünde klasöründe bulunan dosyaları bulunan [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] önbelleğindeki [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] uygulama kaplar. Yapılandırma, elde edilebilir [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] aşağıdakileri yaparak:  
  
1.  Sağ tıklatın [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] projesi,'ı tıklatın **özellikleri**, tıklatın **Yayımla**ve ardından **uygulama dosyalarını** düğmesi.  
  
2.  İçinde **uygulama dosyalarını** iletişim, kümesi **yayımlama durumu** her kanal ve DLL eklentisi **Ekle (otomatik)**ve **indirme grubu** her ardışık düzen ve eklenti DLL'e **(gerekli)**.  
  
### <a name="using-the-pipeline-and-add-in-from-the-application-base"></a>Ardışık Düzen ve kullanarak uygulama temel gelen  
 Ne zaman ardışık düzen ve için yapılandırıldığında [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] dağıtımı, bunlar aynı indirilir [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] Önbellek klasörü olarak [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]. İşlem hattını kullanma ve gelen eklentisi için [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] kod gerekir alın bunları uygulamadan temel. Çeşitli türleri ve üyeleri [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ardışık düzen ve eklentiler kullanmak için eklenti modeli, bu senaryo için özel destek sağlar. İlk olarak, yol tarafından tanımlanan <xref:System.AddIn.Hosting.PipelineStoreLocation.ApplicationBase> numaralandırma değeri. İle ilgili eklenti üyelerinin aşırı şunlardır ardışık düzen kullanmak için bu değeri kullanın:  
  
-   <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>  
  
-   <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%2CSystem.String%5B%5D%29?displayProperty=nameWithType>  
  
-   <xref:System.AddIn.Hosting.AddInStore.Rebuild%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>  
  
-   <xref:System.AddIn.Hosting.AddInStore.Update%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>  
  
### <a name="accessing-the-hosts-site-of-origin"></a>Kaynak ana bilgisayarın Site erişme  
 Bir eklenti dosyaları kaynak sitesinden başvurabilir emin olmak için eklentinin konak uygulamaya denktir güvenlik yalıtım ile yüklenmesi gerekir. Bu güvenlik düzeyi tarafından tanımlanan <xref:System.AddIn.Hosting.AddInSecurityLevel.Host?displayProperty=nameWithType> sabit listesi değeri ve geçirilen <xref:System.AddIn.Hosting.AddInToken.Activate%2A> bir eklenti etkinleştirildiğinde yöntemi.  
  
<a name="WPFAddInModelArchitecture"></a>   
## <a name="wpf-add-in-architecture"></a>WPF Eklenti mimarisi  
 En üst düzeyde anlatıldığı gibi [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sağlayan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] uygulamak için eklentiler [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] (, türetilen doğrudan veya dolaylı olarak <xref:System.Windows.FrameworkElement>) kullanarak <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> ve <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>. Konak uygulama döndürülür sonucu olan bir <xref:System.Windows.FrameworkElement> gelen görüntülenen [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] konak uygulamanın içindeki.  
  
 Basit için [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] eklenti senaryoları, bu olan bir geliştirici gerektiği kadar ayrıntı. Daha karmaşık senaryolar için özellikle, deneyin ek kullanmaya [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] düzeni, kaynakları ve veri bağlama, bilgiye daha ayrıntılı gibi hizmetleri [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] genişletir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] eklenti modeli ile [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Destek, avantajları ve sınırlamaları anlamak için gereklidir.  
  
 Temelde, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] geçmiyor bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] gelen bir eklenti için bir ana bilgisayar uygulaması; bunun yerine, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Win32 pencere tanıtıcısı geçirir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] kullanarak [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] birlikte çalışabilirlik. Bu nedenle, bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] bir eklentiyi bir ana bilgisayar uygulaması için aşağıdakiler gerçekleşir geçirilir:  
  
-   Eklenti tarafında [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] bir pencere tanıtıcısını edinir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] konak uygulama tarafından görüntülenir. Bir pencere tanıtıcının iç tarafından kapsüllenir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] öğesinden türetilen sınıf <xref:System.Windows.Interop.HwndSource> ve uygulayan <xref:System.AddIn.Contract.INativeHandleContract>. Bu sınıfın bir örneği tarafından döndürülen <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> ve eklentinin uygulama etki alanından konak uygulamanın uygulama etki alanına taşınır.  
  
-   Konak uygulama tarafında [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tüketen <xref:System.Windows.Interop.HwndSource> bir iç [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] öğesinden türetilen sınıf <xref:System.Windows.Interop.HwndHost> ve <xref:System.AddIn.Contract.INativeHandleContract>. Bu sınıfın bir örneği tarafından döndürülen <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> konak uygulamaya.  
  
 <xref:System.Windows.Interop.HwndHost>Görüntülenecek var. [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)], gelen pencere işleyicileri tarafından tanımlanan [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]. Daha fazla bilgi için bkz: [WPF ve Win32 birlikte çalışabilirlik](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md).  
  
 Özet olarak, <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, ve <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> pencere tanıtıcısını izin vermek için mevcut bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] bir eklentiyi kapsüllenip tarafından bir ana bilgisayar uygulaması geçirilecek bir <xref:System.Windows.Interop.HwndHost> ve ana bilgisayar görüntülenir uygulamanın [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
> [!NOTE]
>  Ana bilgisayar uygulamasını alır çünkü bir <xref:System.Windows.Interop.HwndHost>, konak uygulama tarafından döndürülen nesne dönüştürülemiyor <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> eklenti tarafından uygulanan türüne (örneğin, bir <xref:System.Windows.Controls.UserControl>).  
  
 Doğası, <xref:System.Windows.Interop.HwndHost> konak uygulamaların bunları nasıl kullanılacağını etkileyen belirli sınırlamaları vardır. Ancak, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] genişletir <xref:System.Windows.Interop.HwndHost> eklenti senaryoları için çeşitli özellikleri ile. Bu avantajlar ve sınırlamalar aşağıda açıklanmıştır.  
  
<a name="WPFAddInModelBenefits"></a>   
## <a name="wpf-add-in-benefits"></a>WPF Eklenti faydaları  
 Çünkü [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] eklenti [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] türeyen bir iç sınıf kullanarak ana bilgisayar uygulamalardan görüntülenen <xref:System.Windows.Interop.HwndHost>, bu [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] özellikleri tarafından kısıtlı <xref:System.Windows.Interop.HwndHost> ilişkilendirilebilmesi için [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] düzeni, işleme, veri bağlama, stiller, şablonlar ve kaynaklar gibi hizmetleri. Ancak, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] iç güçlendirir <xref:System.Windows.Interop.HwndHost> aşağıdakiler dahil ek özellikler içeren bir alt kümesi:  
  
-   Bir konak uygulamanın arasında sekmeyle gitmeyi [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ve bir eklentinin [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Unutmayın "eklenti bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]" programlama modeli geçersiz kılmak Ekle tarafı bağdaştırıcısı gerektirir <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> sekmeyi, eklenti tam olarak güvenilen veya kısmen güvenilir olup olmadığını etkinleştirmek için.  
  
-   Eklenti için erişilebilirlik gereksinimleri uygularken [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] konak uygulamadan görüntülenen [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)].  
  
-   Etkinleştirme [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamaları birden çok uygulama etki alanı senaryolarında güvenli bir şekilde çalıştırmak için.  
  
-   Eklenti geçersiz erişimi önleme [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pencere işleyicilerine eklentileri güvenlik yalıtım (yani, kısmi güven güvenlik sandbox) ile çalıştırıldığında. Çağırma <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> bu güvenliği sağlar:  
  
    -   İçin "Ekle-döndürür bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]" programlama modeli, bir eklenti için bir pencere tanıtıcının geçirmek için tek yolu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] arasında yalıtım sınır çağırmaktır <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>.  
  
    -   İçin "eklenti bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]" programlama modeli, geçersiz kılma <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> Ekle tarafı bağdaştırıcısı ve arama <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> (önceki örneklerde gösterildiği gibi), Ekle tarafı bağdaştırıcının çağırma gibi gereklidir `QueryContract` uygulama konak tarafındaki bağdaştırıcısından.  
  
-   Birden çok uygulama etki alanı yürütme koruması sağlama. Yalıtım sınırı yer alsa bile uygulama etki alanları ile sınırlamaları nedeniyle, eklenti uygulama etki alanında oluşturulan işlenmeyen özel durumlar tüm uygulamanın çökmesine neden. Ancak, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ve [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] eklenti modeli Bu soruna geçici bir çözüm ve uygulama kararlılığını artırmak için basit bir yol sunar. A [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] görüntüleyen eklentisi bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] oluşturur bir <xref:System.Windows.Threading.Dispatcher> konak uygulama ise, uygulama etki alanı çalışan iş parçacığı için bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulama. Uygulama etki alanında işleyerek oluşan tüm işlenmemiş özel durumlarını algılayabilir <xref:System.Windows.Threading.Dispatcher.UnhandledException> olayı [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] eklentinin <xref:System.Windows.Threading.Dispatcher>. Alma <xref:System.Windows.Threading.Dispatcher> gelen <xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A> özelliği.  
  
<a name="WPFAddInModelLimitations"></a>   
## <a name="wpf-add-in-limitations"></a>WPF Eklenti kısıtlamaları  
 Avantajları ötesinde, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tarafından sağlanan varsayılan davranışlar ekler <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost>ve pencere işleyicileri de eklentisi için sınırlamalar vardır [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] konak uygulamadan görüntülenir:  
  
-   Eklenti [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] görüntülenen bir ana bilgisayardan uygulama konak uygulamanın kırpma davranışını almaz.  
  
-   Kavramı *hava sahası* birlikte çalışabilirlik senaryoları de eklentiler için geçerlidir (bkz [teknoloji bölgeleri genel bakış](../../../../docs/framework/wpf/advanced/technology-regions-overview.md)).  
  
-   Bir konak uygulamanın [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] kaynağı devralma, veri bağlama ve kumanda gibi hizmetleri eklentisi otomatik olarak kullanılabilir olmayan [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]. Eklenti bu hizmetleri sağlamak üzere ardışık düzeni güncelleştirmeniz gerekir.  
  
-   Bir eklenti [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] döndürülemez, ölçeği, eğri veya aksi halde bir dönüşüm tarafından etkilenen (bkz [dönüştüren genel bakış](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)).  
  
-   Eklenti içinde içerik [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] işlemlerinden çizim tarafından işlenen <xref:System.Drawing> ad alanı, Alfa karışım içerebilir. Ancak, hem bir eklenti [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ve konak uygulama [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] içerdiği % 100 donuk olmalıdır; diğer bir deyişle, `Opacity` her iki özelliği 1 olarak ayarlanmalıdır.  
  
-   Varsa <xref:System.Windows.Window.AllowsTransparency%2A> bir eklenti içerir konak uygulama penceresinde özelliğinin [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ayarlanır `true`, eklenti görünmez olur. Bu durum geçerlidir olsa bile eklenti [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] % 100 donuk olan (diğer bir deyişle, `Opacity` özelliği 1 değerine sahip).  
  
-   Bir eklenti [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] diğer en üstünde yer almalıdır [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aynı üst düzey pencere öğeleri.  
  
-   Bir eklentinin hiçbir bölümünün [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] kullanılarak oluşturulması bir <xref:System.Windows.Media.VisualBrush>. Bunun yerine, eklenti bir anlık görüntüsünü oluşturulan alabilir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] anlaşma tarafından tanımlanan yöntemleri kullanarak konak uygulamaya geçirilen bir bitmap oluşturmak için.  
  
-   Medya dosyalarını ten yürütülemez bir <xref:System.Windows.Controls.MediaElement> eklentide bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
-   Fare eklenti için oluşturulan olayları [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ne alınan ne de konak uygulama tarafından oluşturulur ve `IsMouseOver` özelliği ana bilgisayar uygulaması için [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] değerine sahip `false`.  
  
-   Ne zaman odağını kaydırır bir eklenti denetimlerinde arasında [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], `GotFocus` ve `LostFocus` olayları ne alınan ne de konak uygulama tarafından oluşturulur.  
  
-   Bir eklenti içeren bir ana bilgisayar uygulaması kısmı [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] yazdırıldığında beyaz görünür.  
  
-   Tüm dağıtıcıları (bkz <xref:System.Windows.Threading.Dispatcher>) tarafından oluşturulan [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] konak uygulama yürütme devam ederse sahibi Eklenti kaldırılmadan önce el ile kapatılmalıdır. Sözleşme konak uygulamanın eklenti eklenti, böylece Eklenti kaldırılmadan önce sinyal izin yöntemleri uygulayabilirsiniz [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] kendi Dispatcher için.  
  
-   Eğer bir eklenti [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] olan bir <xref:System.Windows.Controls.InkCanvas> veya içeren bir <xref:System.Windows.Controls.InkCanvas>, eklenti kaldıramıyor.  
  
<a name="PerformanceOptimization"></a>   
## <a name="performance-optimization"></a>Performansı iyileştirme  
 Birden çok uygulama etki alanları kullanıldığında, varsayılan olarak, çeşitli [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] her uygulama tarafından gerekli derlemeleri uygulamanın etki alanına yüklenir. Sonuç olarak, yeni uygulama etki alanları oluşturma ve bunlarda uygulamalar başlatma için gereken süre performansı etkileyebilir. Ancak, [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zaten yüklü olup olmadığını derlemeleri uygulama etki alanları arasında paylaşmak için uygulamaları yönlendirerek başlangıç zamanlarını azaltmak bir yol sağlar. Kullanarak bunu <xref:System.LoaderOptimizationAttribute> giriş noktası yöntemin uygulanması gereken özniteliği (`Main`). Bu durumda, uygulama tanımının uygulamak için yalnızca kod kullanmanız gerekir (bkz [uygulama yönetimine genel bakış](../../../../docs/framework/wpf/app-development/application-management-overview.md)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.LoaderOptimizationAttribute>  
 [Eklentiler ve Genişletilebilirlik](../../../../docs/framework/add-ins/index.md)  
 [Uygulama Etki Alanları](../../../../docs/framework/app-domains/application-domains.md)  
 [.NET framework Remoting genel bakış](http://msdn.microsoft.com/library/eccb1d31-0a22-417a-97fd-f4f1f3aa4462)  
 [Nesneleri Uzaktan erişilebilir hale getirme](http://msdn.microsoft.com/library/01197253-3f13-43b7-894d-9683e431192a)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/app-development/how-to-topics.md)
