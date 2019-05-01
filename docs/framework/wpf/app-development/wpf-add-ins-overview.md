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
ms.openlocfilehash: 7c02ddca01260a68880630bcb014c5cc4dc4370b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61971320"
---
# <a name="wpf-add-ins-overview"></a>WPF Eklentilerine Genel Bakış
<a name="Introduction"></a> .NET Framework, geliştiricilerin eklentiyi genişletilebilirlik destekleyen uygulamalar oluşturmak için kullanabileceğiniz bir eklenti modeli içerir. Bu eklenti modeli ile tümleştirin ve uygulama işlevselliğini genişleten eklentileri oluşturulmasına izin verir. Bazı senaryolarda uygulamalar eklenti tarafından sağlanan kullanıcı arabirimlerini görüntülemek de gerekir. Bu konuda, WPF bu senaryolar, mimarisi, aboneliğin avantajları ve kısıtlamalarını arkasında etkinleştirmek için .NET Framework eklenti modeli nasıl artırmaktadır gösterilmektedir.  

<a name="Requirements"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 .NET Framework eklenti modeli konusunda gereklidir. Daha fazla bilgi için [eklentiler ve genişletilebilirlik](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).  
  
<a name="AddInsOverview"></a>   
## <a name="add-ins-overview"></a>Eklentilere genel bakış  
 Karmaşıklığını uygulama yeniden derleme ve yeni işlevsellikler eklemek için yeniden dağıtım kaçınmak için geliştiricilerin (hem birinci taraf hem de üçüncü taraf) genişletilebilirlik mekanizması uygulamaları uygular, diğer uygulamalar oluşturma onlarla tümleştirin. Add-INS kullanımı ("eklentiler" ve "eklentiler" olarak da bilinir) bu tür bir genişletilebilirlik desteklemek için en yaygın yoludur. Genişletilebilirlik eklentiler ile kullanıma gerçek uygulamaları örnekleri şunlardır:  
  
- Internet Explorer eklentiler.  
  
- Windows Media Player eklentiler.  
  
- Visual Studio eklentileri.  
  
 Örneğin, "kod çözücüleri ve Windows tarafından yerel olarak desteklenmeyen medya biçimleri Kodlayıcıları oluşturma dahil olmak üzere çeşitli Windows Media Player'ı genişleten eklentiler" uygulamak üçüncü taraf geliştiriciler Windows Media Player eklenti modeli sağlar Media Player (örneğin, DVD, MP3), ses efekti ve dış. Her eklenti modeli, varlıklar ve eklenti tüm modelleri için ortak olan davranışları olsa bir uygulama için benzersiz olan işlevselliği göstermek için oluşturulmuştur.  
  
 Üç ana varlıklardır tipik eklenti genişletilebilirliği çözümlerinin *sözleşmeleri*, *eklentileri*, ve *ana bilgisayar uygulamalarını*. Sözleşmeler, eklentiler iki yolla konak uygulamalarıyla tümleştirmek tanımlar:  
  
- Eklentiler, konak uygulamalar tarafından uygulanan işlevleri ile tümleştirin.  
  
- Ana bilgisayar uygulamaları tümleştirmek eklentiler için işlevselliği kullanıma sunar.  
  
 Kullanılacak eklentiler için konak uygulamalar bulup bunları çalışma zamanında yük gerekir. Sonuç olarak, eklentiler destekleyen uygulamalar, aşağıdaki ek sorumluluklara sahiptir:  
  
- **Bulma**: Konak uygulamalar tarafından desteklenen sözleşmeleri izliyor eklentiler bulma.  
  
- **Etkinleştirme**: Yükleniyor, çalıştırma ve eklentiler ile iletişim kurma.  
  
- **Yalıtım**: Uygulama olası güvenlik ve eklentileri yürütme sorunlarını korumak, yalıtım sınırlarını kurmak için uygulama etki alanları veya işlemleri kullanarak.  
  
- **İletişim**: Eklentileri izin vererek ve birbirleriyle yöntemlerini çağırmaya ve veri geçirme yalıtım sınırlarının arasında iletişim için uygulamaları barındırın.  
  
- **Ömür Yönetimi**: Yükleme ve temiz, tahmin edilebilir bir biçimde uygulama etki alanları ve işlemleri kaldırma (bkz [uygulama etki alanları](../../app-domains/application-domains.md)).  
  
- **Sürüm oluşturma**: Ya da yeni sürümlerini oluşturulduğunda konak uygulamalar ve eklentiler hala iletişim kurabildiğinden emin olma.  
  
 Sonuç olarak, sağlam bir eklenti modeli geliştirme Önemsiz olmayan bir iş değil. Bu nedenle, .NET Framework eklenti modeli oluşturmaya yönelik bir altyapı sağlar.  
  
> [!NOTE]
>  Eklentiler hakkında daha ayrıntılı bilgi için bkz: [eklentiler ve genişletilebilirlik](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).  
  
<a name="NETFrameworkAddInModelOverview"></a>   
## <a name="net-framework-add-in-model-overview"></a>.NET framework eklenti modeli genel bakış  
 .NET Framework eklenti modeli bulunan <xref:System.AddIn> ad alanı, eklenti genişletilebilirliği geliştirilmesini basitleştirmek için tasarlanmış türleri kümesi içerir. .NET Framework eklenti modeli temel birimidir *sözleşme*eklenti birbiriyle ve ana bilgisayar uygulamasına nasıl tanımlar. Bir anlaşma kullanarak bir konak uygulamaya özgü bir ana bilgisayar uygulamasına sunulur *görünümü* sözleşme. Benzer şekilde, bir ekleme-özel *görünümü* sözleşme eklenti için sunulur. Bir *bağdaştırıcısı* bir konak uygulama ve bir eklenti ilgili kendi ilgili görünümler arasında iletişim kurmasına izin vermek için kullanılır. Sözleşmeler, görünümler ve bağdaştırıcılar adlandırılır segmentler ve ilgili kesimleri kümesi oluşturan bir *işlem hattı*. İşlem hatları, bulma, etkinleştirme, güvenlik yalıtımı, yürütme yalıtım (uygulama etki alanları ve işlemleri kullanarak), iletişim, ömür yönetimi ve sürüm oluşturma .NET Framework eklenti modeli destekler temelidir.  
  
 Bu destek toplamını konak uygulamanın işlevselliğini tümleştirmek eklentileri geliştiricilerin sağlar. Ancak, bazı senaryolar eklentiler tarafından sağlanan kullanıcı arabirimlerini görüntülemek için konak uygulamalar gerektirir. .NET Framework içindeki her bir sunu teknolojiyi kullanıcı arabirimlerini uygulamak için kendi modeli olduğundan, .NET Framework eklenti modeli herhangi belirli sunu teknolojisi desteklemez. Bunun yerine, WPF, .NET Framework eklenti modeli eklentiler için kullanıcı Arabirimi desteği genişletir.  
  
<a name="WPFAddInModel"></a>   
## <a name="wpf-add-ins"></a>WPF eklentileri  
 WPF, .NET Framework eklenti modeli ile birlikte, çok çeşitli eklentiler kullanıcı arabirimlerini görüntülemek için uygulamaları barındırmak gerektiren senaryolar adresi sağlar. Özellikle, bu senaryolar aşağıdaki iki programlama modeli ile WPF tarafından ele alınır:  
  
1. **Eklenti UI döndüren**. Bir eklentiyi bir kullanıcı Arabirimi ana bilgisayar uygulamasına bir yöntem çağrısının anlaşma tarafından tanımlandığı şekilde döndürür. Bu senaryo, aşağıdaki durumlarda kullanılır:  
  
    - Bir kullanıcı Arabirimi eklentisi tarafından döndürülen görünümünün ya da verilere bağımlı olduğundan veya yalnızca çalışma zamanında dinamik olarak gibi mevcut koşulları oluşturulan raporlar.  
  
    - Kullanıcı Arabirimi eklentisi tarafından sağlanan hizmetleri için eklentiyi kullanan konak uygulamalar Arabiriminden farklıdır.  
  
    - Eklentiyi öncelikle ana uygulama için bir hizmet gerçekleştirir ve bir kullanıcı Arabirimi ile ana bilgisayar uygulaması durumu bildirir.  
  
2. **Eklenti UI olan**. Bir eklenti, sözleşmesi tarafından tanımlandığı şekilde UI'dir. Bu senaryo, aşağıdaki durumlarda kullanılır:  
  
    - Bir eklenti gibi bir reklam görüntülenen dışındaki hizmetleri sağlamaz.  
  
    - Hesaplayıcı veya Renk Seçici gibi eklenti kullanan tüm konak uygulamalar için kullanıcı Arabirimi eklentisi tarafından sağlanan hizmetleri için yaygındır.  
  
 Bu senaryolar, eklenti uygulama etki alanları ve ana bilgisayar uygulaması arasında UI nesneleri geçirilebilir gerektirir. Eklenti modeli uygulama etki alanları arasında iletişim kurmak için uzaktan iletişim kullanır olan .NET Framework beri bunlar arasında geçirilen nesneleri, Uzaktan erişilebilir olması gerekir.  
  
 Uzaktan erişilebilir bir veya daha fazlasını yapan bir sınıf örneği nesnedir:  
  
- Öğesinden türetilen <xref:System.MarshalByRefObject> sınıfı.  
  
- Implements <xref:System.Runtime.Serialization.ISerializable> arabirimi.  
  
- Sahip <xref:System.SerializableAttribute> özniteliği uygulandı.  
  
> [!NOTE]
>  Uzaktan erişilebilir .NET Framework nesneleri oluşturma hakkında daha fazla bilgi için bkz. [nesneleri Uzaktan erişilebilir hale getirme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/wcf3swha(v=vs.100)).  
  
 WPF UI türleri Uzaktan erişilebilir değildir. Sorunu çözmek için ana uygulamalardan görüntülenecek WPF UI eklentileri tarafından oluşturulan etkinleştirmek için .NET Framework eklenti modeli WPF genişletir. Bu destek, iki tür tarafından WPF sağladığı: <xref:System.AddIn.Contract.INativeHandleContract> arabirimi ve iki statik yöntemler tarafından uygulanan <xref:System.AddIn.Pipeline.FrameworkElementAdapters> sınıfı: <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> ve <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>. Yüksek düzeyde, bu türleri ve yöntemleri şu şekilde kullanılır:  
  
1. WPF gerektiren eklentiler tarafından sağlanan kullanıcı arabirimleri doğrudan veya dolaylı olarak türetilen sınıflar olduklarını <xref:System.Windows.FrameworkElement>şekiller, denetimleri, kullanıcı denetimleri, Düzen bölmeleri ve sayfaları gibi.  
  
2. Sözleşme, eklenti ve barındırma uygulaması UI'dir geçirilecek bildirir her yerde, onu olarak bildirilmelidir bir <xref:System.AddIn.Contract.INativeHandleContract> (değil bir <xref:System.Windows.FrameworkElement>); <xref:System.AddIn.Contract.INativeHandleContract> yalıtım sınırlarında geçirilebilir eklenti UI Uzaktan erişilebilir gösterimidir.  
  
3. Eklentinin uygulama etki alanından geçirilmeden önce bir <xref:System.Windows.FrameworkElement> olarak paketlenmiş bir <xref:System.AddIn.Contract.INativeHandleContract> çağırarak <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>.  
  
4. Konak uygulamanın uygulama etki alanı için geçirilen sonra <xref:System.AddIn.Contract.INativeHandleContract> olarak paketlenmiş gereken bir <xref:System.Windows.FrameworkElement> çağırarak <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>.  
  
 Nasıl <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, ve <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> kullanılan belirli bir senaryoya bağlıdır. Aşağıdaki bölümlerde, her bir programlama modeli için ayrıntıları sağlayın.  
  
<a name="ReturnUIFromAddInContract"></a>   
## <a name="add-in-returns-a-user-interface"></a>Eklenti kullanıcı arayüzü döndürür.  
 Bir kullanıcı Arabirimi bir ana bilgisayar uygulamasına döndürülecek eklenti için aşağıdakiler gereklidir:  
  
1. Ana bilgisayar uygulaması, eklenti ve işlem hattı, .NET Framework tarafından açıklandığı oluşturulmalıdır [eklentiler ve genişletilebilirlik](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)) belgeleri.  
  
2. Sözleşme uygulamalıdır <xref:System.AddIn.Contract.IContract> ve bir kullanıcı Arabirimi döndürülecek sözleşme türü dönüş değerine sahip bir yöntemi bildirmeniz gerekir <xref:System.AddIn.Contract.INativeHandleContract>.  
  
3. Eklenti ile ana bilgisayar uygulaması arasında geçirilen kullanıcı Arabirimi öğesinden türetilmelidir doğrudan veya dolaylı olarak <xref:System.Windows.FrameworkElement>.  
  
4. Kullanıcı Arabirimi eklentisi tarafından döndürülen dönüştürülmüş olmalıdır bir <xref:System.Windows.FrameworkElement> için bir <xref:System.AddIn.Contract.INativeHandleContract> yalıtım sınırı geçmeden önce.  
  
5. Öğesinden döndürülen UI dönüştürülmelidir bir <xref:System.AddIn.Contract.INativeHandleContract> için bir <xref:System.Windows.FrameworkElement> yalıtım sınırı geçmesinden sonra.  
  
6. Konak uygulama döndürülen görüntüler <xref:System.Windows.FrameworkElement>.  
  
 UI döndüren eklenti uygulama yapmayı gösteren bir örnek için bkz: [bir eklenti döndüren bir kullanıcı Arabirimi oluşturma](how-to-create-an-add-in-that-returns-a-ui.md).  
  
<a name="AddInIsAUI"></a>   
## <a name="add-in-is-a-user-interface"></a>Bir kullanıcı arabirimi eklentisi olan  
 Bir eklenti UI olduğunda, aşağıdakiler gereklidir:  
  
1. Ana bilgisayar uygulaması, eklenti ve işlem hattı, .NET Framework tarafından açıklandığı oluşturulmalıdır [eklentiler ve genişletilebilirlik](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)) belgeleri.  
  
2. Eklenti anlaşma arabirimi uygulamalıdır <xref:System.AddIn.Contract.INativeHandleContract>.  
  
3. Ana uygulamaya geçirilen eklentiyi doğrudan veya dolaylı olarak öğesinden türetilmelidir <xref:System.Windows.FrameworkElement>.  
  
4. Eklenti gelen dönüştürülmelidir bir <xref:System.Windows.FrameworkElement> için bir <xref:System.AddIn.Contract.INativeHandleContract> yalıtım sınırı geçmeden önce.  
  
5. Eklenti gelen dönüştürülmelidir bir <xref:System.AddIn.Contract.INativeHandleContract> için bir <xref:System.Windows.FrameworkElement> yalıtım sınırı geçmesinden sonra.  
  
6. Konak uygulama döndürülen görüntüler <xref:System.Windows.FrameworkElement>.  
  
 UI olan eklenti uygulama yapmayı gösteren bir örnek için bkz: [bir eklenti olan bir kullanıcı Arabirimi oluşturma](how-to-create-an-add-in-that-is-a-ui.md).  
  
<a name="ReturningMultipleUIsFromAnAddIn"></a>   
## <a name="returning-multiple-uis-from-an-add-in"></a>Eklenti birden çok UI döndüren  
 Eklentiler, genellikle görüntülemek uygulamaları barındırmak için birden çok kullanıcı arabirimi sağlar. Ayrıca konak uygulama durum bilgilerini de bir kullanıcı Arabirimi olarak sağlayan UI olan eklenti gibi göz önünde bulundurun. Böyle bir eklenti hem tekniklerinin bir bileşimini kullanarak uygulanabilir [bir kullanıcı arayüzü döndürür eklenti](#ReturnUIFromAddInContract) ve [eklenti kullanıcı arayüzü](#AddInIsAUI) modelleri.  
  
<a name="AddInsAndXBAPs"></a>   
## <a name="add-ins-and-xaml-browser-applications"></a>Eklentiler ve XAML tarayıcı uygulamaları  
 Örneklerde, şu ana kadar yüklü tek başına uygulama konak uygulama olmuştur. Ancak [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] eklentileri, aşağıdaki ek derleme ve uygulama gereksinimleri paralelleştirmeye da barındırabilirsiniz:  
  
- [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Uygulama bildirimi, işlem hattını (klasörleri ve derlemeleri) ve eklenti derlemesi için özel olarak indirmek için yapılandırılmalıdır [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] aynı klasörde bir istemci makine üzerinde uygulama önbelleğine [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)].  
  
- [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Keşfedip eklentileri yükleyecek kod kullanmalıdır [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] uygulama önbelleği için [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] eklentisi ardışık düzen ve konum olarak.  
  
- [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Eklenti tarafından barındırıldığında; kaynak sitede bulunan gevşek dosyalar başvuruyorsa bir özel güvenlik bağlamına eklenti gerekir [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], add-INS konak uygulamanın sitede bulunan gevşek dosyalar yalnızca başvurabilir kaynağı.  
  
 Bu görevleri, aşağıdaki alt bölümlerde ayrıntılı olarak açıklanmıştır.  
  
### <a name="configuring-the-pipeline-and-add-in-for-clickonce-deployment"></a>İşlem hattı ve ClickOnce dağıtımı için eklentiyi yapılandırma  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] için indirilir ve güvenli bir klasörde çalıştırılan [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] dağıtım önbellek. Sırayla bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] eklenti barındırmak için işlem hattı ve eklenti bütünleştirilmiş kod da güvenli klasöre yüklenmelidir. Bunu başarmak için uygulama bildirimini işlem hattı ve eklenti derlemesini içerecek şekilde yapılandırmanız gerekir. Bu en bir kolayca yapılabilir [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], işlem hattı ve eklenti derlemesi konak olması gerekiyor ancak [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] projesinin kök klasörüne sırayla [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] ardışık düzen derlemeleri algılamak için.  
  
 Sonuç olarak, Eklenti derlemesine ve işlem hattı oluşturmak için ilk adım olan [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] yapı çıkışını her işlem hattı ayarlayarak derleme projeleri derleme ve Eklenti projesinin kök. Aşağıdaki tabloda çözüm ve kök klasörde konağı olarak işlem hattı derleme projeleri ve derleme eklenti projesi yapı çıkış yolları gösterilmektedir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] proje.  
  
 Tablo 1: Çıkış yolu bir XBAP tarafından barındırılan işlem hattı derlemeler için derleme  
  
|İşlem hattı derleme projesi|Yapı çıkış yolu|  
|-------------------------------|-----------------------|  
|Sözleşme|`..\HostXBAP\Contracts\`|  
|Eklenti görünümü|`..\HostXBAP\AddInViews\`|  
|Ekleme tarafı bağdaştırıcısı|`..\HostXBAP\AddInSideAdapters\`|  
|Konak tarafı bağdaştırıcısı|`..\HostXBAP\HostSideAdapters\`|  
|Eklentisi|`..\HostXBAP\AddIns\WPFAddIn1`|  
  
 Eklenti derleme olarak ve işlem hattı derlemeleri belirtmek için sonraki adımdır [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] içerik dosyaları [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] aşağıdakileri yaparak:  
  
1. Her işlem hattı klasör Çözüm Gezgini'nde sağ tıklayıp seçerek işlem hattı ve eklenti bütünleştirilmiş kod projesinde dahil **projeye dahil et**.  
  
2. Ayarı **derleme eylemi** her işlem hattı derleme ve Eklenti derlemesine **içerik** gelen **özellikleri** penceresi.  
  
 Son adım, işlem hattı derleme dosyaları ve derleme eklenti dosyası indirme için eklenecek uygulama bildirimi yapılandırmaktır. Klasörün kökünde klasörlerdeki dosyaları yerleştirilmelidir [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] önbelleğindeki [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] uygulama kaplar. Yapılandırma sağlanabilir [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] aşağıdakileri yaparak:  
  
1. Sağ tıklayın [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] proje, tıklayın **özellikleri**, tıklayın **Yayımla**ve ardından **uygulama dosyaları** düğmesi.  
  
2. İçinde **uygulama dosyaları** iletişim kutusunda, kümesi **yayımlama durumu** her işlem hattı ve DLL eklentisini **Ekle (otomatik)** ve **indirmegrubu** her işlem hattı ve DLL eklentisini **(gerekli)**.  
  
### <a name="using-the-pipeline-and-add-in-from-the-application-base"></a>İşlem hattı ve kullanarak uygulama tabanından  
 Ne zaman işlem hattı ve için yapılandırıldığında [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] dağıtım, aynı yüklenen [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] Önbellek klasörü olarak [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]. İşlem hattını kullanma ve gelen eklentisi için [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] kodu gerekir alma bunları uygulamadan temel. Çeşitli türleri ve üyeleri için işlem hatları ve eklentiler kullanarak .NET Framework eklenti modeli, bu senaryo için özel desteği sağlar. İlk olarak, yol ile tanımlanan <xref:System.AddIn.Hosting.PipelineStoreLocation.ApplicationBase> numaralandırma değeri. Aşağıdakileri içeren işlem hattı kullanmak için uygun eklenti üyeleri aşırı yüklemeleri ile bu değeri kullanın:  
  
- <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>  
  
- <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%2CSystem.String%5B%5D%29?displayProperty=nameWithType>  
  
- <xref:System.AddIn.Hosting.AddInStore.Rebuild%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>  
  
- <xref:System.AddIn.Hosting.AddInStore.Update%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>  
  
### <a name="accessing-the-hosts-site-of-origin"></a>Ana bilgisayarın Site kaynak erişimi  
 Eklenti dosyaları kaynak siteden başvurabileceğini emin olmak için eklentinin ana bilgisayar uygulamasına eşdeğerdir ve güvenlik yalıtımı ile yüklenmesi gerekir. Bu güvenlik düzeyi tarafından tanımlanan <xref:System.AddIn.Hosting.AddInSecurityLevel.Host?displayProperty=nameWithType> numaralandırma değeri geçirilir <xref:System.AddIn.Hosting.AddInToken.Activate%2A> eklenti etkinleştirildiğinde yöntemi.  
  
<a name="WPFAddInModelArchitecture"></a>   
## <a name="wpf-add-in-architecture"></a>WPF eklentisi mimarisi  
 Anlatıldığı gibi en üst düzeyde, WPF .NET Framework kullanıcı arabirimlerini eklentiler sağlar. (Bu türetilen doğrudan veya dolaylı olarak <xref:System.Windows.FrameworkElement>) kullanarak <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> ve <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>. Ana bilgisayar uygulaması döndürülür sonucu olan bir <xref:System.Windows.FrameworkElement> görüntülenen kullanıcı Arabiriminden ana uygulamada.  
  
 Basit kullanıcı Arabirimi eklentisi senaryolar için bir geliştiricinin ihtiyaç duyduğu kadar ayrıntı budur. Daha karmaşık senaryolarda, düzen, kaynakları ve veri bağlama gibi ek WPF hizmetlerini kullanan denemek için WPF UI desteği ile .NET Framework eklenti modeli nasıl genişlettiğini, daha ayrıntılı bilgiye faydalarını anlamak için gereklidir ve sınırlamaları.  
  
 Temelde, WPF bir ana bilgisayar uygulaması için bir eklentiyi bir UI geçirmez; Bunun yerine, WPF WPF birlikte çalışabilirliği kullanılarak Win32 pencere tanıtıcısı kullanıcı Arabiriminde geçirir. Bir kullanıcı Arabiriminden bir eklenti için bir ana bilgisayar uygulaması geçirildiğinde, bu nedenle, aşağıdakiler gerçekleşir:  
  
- Eklenti tarafında WPF konak uygulama tarafından görüntülenen kullanıcı Arabirimi için bir pencere tutucu devralır. Türetilen bir iç WPF sınıf pencere tanıtıcısı yalıtılan <xref:System.Windows.Interop.HwndSource> ve uygulayan <xref:System.AddIn.Contract.INativeHandleContract>. Bu sınıfın bir örneği tarafından döndürülen <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> ve eklentinin uygulama etki alanından konak uygulamanın uygulama etki alanına taşınır.  
  
- Konak uygulama tarafında WPF tüketen <xref:System.Windows.Interop.HwndSource> türetildiği bir iç WPF sınıf olarak <xref:System.Windows.Interop.HwndHost> ve <xref:System.AddIn.Contract.INativeHandleContract>. Bu sınıfın bir örneği tarafından döndürülen <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> konak uygulama.  
  
 <xref:System.Windows.Interop.HwndHost> pencere tanıtıcısı, WPF kullanıcı arabirimleri ile tanımlanan kullanıcı arabirimlerini görüntülemek için var. Daha fazla bilgi için [WPF ve Win32 birlikte çalışması](../advanced/wpf-and-win32-interoperation.md).  
  
 Özet olarak, <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, ve <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> bir eklentiyi bir ana bilgisayar uygulamasına Burada, saklanmış olduğu tarafından geçirilecek bir WPF UI için Pencere işleyicisi izin vermek için mevcut bir <xref:System.Windows.Interop.HwndHost> ve konak uygulamanın kullanıcı Arabiriminde görüntülenir.  
  
> [!NOTE]
>  Ana bilgisayar uygulaması aldığından bir <xref:System.Windows.Interop.HwndHost>, ana bilgisayar uygulaması tarafından döndürülen nesne dönüştürülemiyor <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> eklenti tarafından uygulanan türüne (örneğin, bir <xref:System.Windows.Controls.UserControl>).  
  
 Doğası, <xref:System.Windows.Interop.HwndHost> uygulamalarını barındırmak bunları nasıl kullanabileceğiniz etkileyen belirli sınırlamaları vardır. Ancak WPF genişletir <xref:System.Windows.Interop.HwndHost> eklenti senaryoları için çeşitli özelliklere sahip. Bu avantajlar ve sınırlamalar aşağıda açıklanmıştır.  
  
<a name="WPFAddInModelBenefits"></a>   
## <a name="wpf-add-in-benefits"></a>WPF eklentisi avantajları  
 WPF eklentisi kullanıcı arabirimleri, türetilen bir iç sınıf kullanarak ana uygulamadan görüntülendiğinden <xref:System.Windows.Interop.HwndHost>, bu kullanıcı arabirimleri yeteneklerini tarafından kısıtlanmıştır <xref:System.Windows.Interop.HwndHost> düzeni gibi bir WPF UI Hizmetleri göre işleme, veri bağlama, stiller, şablonlar ve kaynaklar. Ancak WPF iç artırmaktadır <xref:System.Windows.Interop.HwndHost> aşağıdakiler dahil ek özellikler olan alt sınıf:  
  
- Konak uygulamanın kullanıcı Arabirimi ile bir eklentinin kullanıcı Arabirimi arasında sekmeyle gitmeyi. "Eklenti UI'dir." bir programlama modeli için geçersiz kılmak Ekle tarafı bağdaştırıcısı gerektiğini unutmayın <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> sekmeyi, eklentinin tam güvenilir veya kısmen güvenilen etkinleştirmek için.  
  
- Konak uygulama kullanıcı arabirimlerinden görüntülenen bir eklenti kullanıcı arabirimleri için erişilebilirlik gereksinimleri uygularken.  
  
- WPF uygulamaları birden çok uygulama etki alanı senaryolarında güvenli bir şekilde çalıştırmak etkinleştiriliyor.  
  
- Eklentileri (diğer bir deyişle, kısmi güven güvenliği sandbox) güvenlik yalıtımı ile çalıştırdığınızda kullanıcı Arabirimi eklentisi için geçersiz erişimi önleme penceresi işler. Çağırma <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> bu güvenlik sağlar:  
  
    - "Eklenti UI döndüren" programlama modeli için Pencere işleyicisi eklenti UI için yalıtım sınırı arasında geçirmek için tek yolu çağırmaktır <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>.  
  
    - "Eklenti UI olan" programlama modeli için geçersiz kılma <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> arama ve ekleme tarafı bağdaştırıcısı <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> (önceki örneklerde gösterildiği gibi), ekleme tarafı bağdaştırıcının çağırma gibi gereklidir `QueryContract` uygulamasından konak tarafı bağdaştırıcısı.  
  
- Birden çok uygulama etki alanı yürütme korumasını sağlama. Yalıtım sınırı yer alsa bile uygulama etki alanlarıyla sınırlamaları nedeniyle, eklenti uygulama etki alanında oluşturulan işlenmeyen özel durumları uygulamanın tamamı çökmesine neden. Ancak, WPF ve .NET Framework eklenti modeli, bu sorunu gidermek ve uygulama kararlılığını artırmak için basit bir yol sağlar. Bir kullanıcı Arabirimi görüntüler WPF eklentisi oluşturur bir <xref:System.Windows.Threading.Dispatcher> konak uygulama WPF uygulaması ise, uygulama etki alanı üzerinde çalıştığı iş parçacığı için. Uygulama etki alanında işleyerek meydana gelen tüm işlenmemiş özel durumları algılayabilirsiniz <xref:System.Windows.Threading.Dispatcher.UnhandledException> WPF eklentisi olayı <xref:System.Windows.Threading.Dispatcher>. Alabileceğiniz <xref:System.Windows.Threading.Dispatcher> gelen <xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A> özelliği.  
  
<a name="WPFAddInModelLimitations"></a>   
## <a name="wpf-add-in-limitations"></a>WPF eklentisi sınırlamaları  
 WPF tarafından sağlanan varsayılan davranışlar ekler avantajları ötesinde <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost>ve pencere işleyicilerini, aynı zamanda ana uygulamalardan görüntülenen bir eklenti kullanıcı arabirimleri için sınırlamalar vardır:  
  
- Bir konak uygulamasından görüntülenen eklenti kullanıcı arabirimleri konak uygulamanın kırpma davranışını dikkate almaz.  
  
- Kavramını *hava sahası* birlikte çalışabilirlik senaryolarında de eklentiler için geçerlidir (bkz [teknoloji bölgelerine genel bakış](../advanced/technology-regions-overview.md)).  
  
- Kaynağın devralmayı, veri bağlama ve komut vermeye genel, eklenti otomatik olarak kullanılabilir değil gibi bir konak uygulamanın UI Hizmetleri kullanıcı arabirimleri. Eklenti, bu hizmetleri sağlamak üzere işlem hattı güncelleştirmeniz gerekiyor.  
  
- Eklentinin kullanıcı Arabirimi döndürülemez, ölçeği, dengesiz veya aksi halde bir dönüştürme tarafından etkilenen (bkz [dönüştüren genel bakış](../graphics-multimedia/transforms-overview.md)).  
  
- İçerik işlemlerinden çizerek işlenen eklenti kullanıcı arabirimi içinde <xref:System.Drawing> ad alanı, alfa karıştırma içerebilir. Ancak, hem eklenti kullanıcı Arabirimi hem de ana bilgisayar uygulaması içerdiği UI % 100 donuk olmalıdır; diğer bir deyişle, `Opacity` hem de özelliği 1 olarak ayarlanması gerekir.  
  
- Varsa <xref:System.Windows.Window.AllowsTransparency%2A> özelliği eklenti kullanıcı Arabirimi içeren konak uygulama pencerenin `true`, eklentiyi görünmezdir. Eklentinin kullanıcı Arabirimi % 100 donuk olsa bile bu geçerlidir (yani `Opacity` özelliği 1 değerine sahip).  
  
- Eklentinin kullanıcı Arabirimi, aynı üst düzey penceresinde diğer WPF öğeleri üzerinde yer almalıdır.  
  
- Hiçbir kısmı bir eklentinin kullanıcı Arabirimi kullanarak işlenebilecek bir <xref:System.Windows.Media.VisualBrush>. Bunun yerine, eklenti anlaşmada tanımlanan yöntemleri kullanarak konak uygulamaya geçirilen bir bit eşlem oluşturmak için oluşturulan kullanıcı arabirimini anlık görüntüsünü alabilir.  
  
- Medya dosyaları, gelen yürütülemez bir <xref:System.Windows.Controls.MediaElement> eklenti kullanıcı arabiriminde.  
  
- Fare olayları için eklenti kullanıcı Arabirimi tarafından üretilen almaz veya konak uygulama tarafından oluşturulan ve `IsMouseOver` konak uygulama kullanıcı Arabirimi için özellik değerine sahip `false`.  
  
- Odak bir eklenti UI denetimleri arasındaki geçtiğinde `GotFocus` ve `LostFocus` olayları almaz veya konak uygulama tarafından oluşturulur.  
  
- Eklentinin kullanıcı Arabirimi içeren bir ana bilgisayar uygulaması bölümünü yazdırıldığında beyaz görünür.  
  
- Tüm dağıtıcıları (bkz <xref:System.Windows.Threading.Dispatcher>) tarafından oluşturulan kullanıcı Arabirimi kapatılması gerekiyor el ile ana bilgisayar uygulaması yürütme devam ederse sahibi Eklenti kaldırılmadan önce. Sözleşme, eklenti, böylece kendi Dispatcher eklenti UI kaldırılmadan önce eklentiyi göstermek konak uygulama izin yöntemleri uygulayabilirsiniz.  
  
- Eklentinin kullanıcı Arabirimi ise bir <xref:System.Windows.Controls.InkCanvas> ya da içeren bir <xref:System.Windows.Controls.InkCanvas>, eklentiyi kaldıramıyor.  
  
<a name="PerformanceOptimization"></a>   
## <a name="performance-optimization"></a>Performansı iyileştirme  
 Birden çok uygulama etki alanı kullanıldığında, varsayılan olarak, her uygulama için gereken çeşitli .NET Framework derlemeleri tüm uygulamanın etki alanına yüklenir. Sonuç olarak, yeni uygulama etki alanları oluşturma ve uygulamalar bunları başlatmak için gereken süreyi performansını etkileyebilir. Ancak, .NET Framework uygulamaları zaten yüklü olduğundan, derlemeleri uygulama etki alanları arasında paylaşmak için yönlendirerek başlangıç zamanı azaltmak bir yol sağlar. Kullanarak bunu <xref:System.LoaderOptimizationAttribute> giriş noktası yöntemi için uygulanması gereken özniteliği (`Main`). Bu durumda, uygulama tanımınız uygulamak için yalnızca kod kullanmanız gerekir (bkz [uygulama yönetimine genel bakış](application-management-overview.md)).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.LoaderOptimizationAttribute>
- [Eklentiler ve Genişletilebilirlik](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [Uygulama Etki Alanları](../../app-domains/application-domains.md)
- [.NET framework uzaktan iletişimi genel bakış](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kwdt6w2k(v=vs.100))
- [Nesneleri Uzaktan erişilebilir hale getirme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/wcf3swha(v=vs.100))
- [Nasıl Yapılır Konuları](how-to-topics.md)
