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
ms.openlocfilehash: 4fd8fe00fe6974bdcbf7b4af4da25150996de8c3
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401701"
---
# <a name="wpf-add-ins-overview"></a>WPF Eklentilerine Genel Bakış

<a name="Introduction"></a>.NET Framework, geliştiricilerin eklenti genişletilebilirliği destekleyen uygulamalar oluşturmak için kullanabileceği bir eklenti modeli içerir. Bu eklenti modeli, uygulama işlevselliğini tümleştirmede ve genişlettirecek eklentilerin oluşturulmasına olanak sağlar. Bazı senaryolarda uygulamalar, eklentiler tarafından sunulan kullanıcı arabirimlerini de görüntülemesi gerekir. Bu konu başlığı altında, WPF 'in bu senaryoları etkinleştirmek için .NET Framework eklenti modelini nasıl genişlettiğini, arkasındaki mimariyi, avantajlarını ve onun sınırlamalarını gösterir.

<a name="Requirements"></a>

## <a name="prerequisites"></a>Önkoşullar

.NET Framework eklentisi modeliyle benzerlik gerekli. Daha fazla bilgi için bkz. eklentiler [ve genişletilebilirlik](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).

<a name="AddInsOverview"></a>

## <a name="add-ins-overview"></a>Eklentilere genel bakış

Uygulama yeniden derleme ve yeni işlevsellik birleştirme için karmaşıklıklardan kaçınmak amacıyla, uygulamalar geliştiricilerin (birinci taraf ve üçüncü taraf), diğer uygulamaları oluşturmalarına olanak tanıyan genişletilebilirlik mekanizmaları uygular. bunlarla tümleştirin. Bu tür genişletilebilirliği desteklemeye yönelik en yaygın yol, Eklentiler ("Eklentiler" ve "Eklentiler" olarak da bilinir) kullanmaktır. Eklentilerle genişletilebilirlik sunan gerçek dünya uygulamalarının örnekleri şunlardır:

- Internet Explorer eklentileri.

- Windows Media Player eklentileri.

- Visual Studio eklentileri.

Örneğin, Windows Media Player eklenti modeli, üçüncü taraf geliştiricilerin Windows Media Player Windows tarafından desteklenmeyen medya biçimleri için kod çözücüleri ve kodlayıcıları oluşturma dahil olmak üzere çeşitli şekillerde genişletecek "Eklentiler" uygulamasına olanak tanır Media Player (örneğin, DVD, MP3), ses efektleri ve kaplamalar. Her eklenti modeli, bir uygulamaya özgü işlevselliği göstermek için oluşturulmuştur, ancak tüm eklenti modelleriyle ortak olan birkaç varlık ve davranış vardır.

Tipik eklenti genişletilebilirlik çözümlerinin üç ana varlığı *sözleşmeler*, *Eklentiler*ve *ana bilgisayar uygulamalarıdır*. Sözleşmeler, eklentilerin ana bilgisayar uygulamalarıyla nasıl tümleştirileceğini iki şekilde tanımlar:

- Eklentiler, ana bilgisayar uygulamaları tarafından uygulanan işlevlerle tümleştirilir.

- Konak uygulamalar, ile tümleştirilecek eklentiler için işlevselliği kullanıma sunar.

Eklentilerin kullanılabilmesi için, ana bilgisayar uygulamalarının bunları bulması ve çalışma zamanında yüklemesi gerekir. Sonuç olarak, eklentileri destekleyen uygulamalar aşağıdaki ek sorumluluklara sahiptir:

- **Bulma**: Konak uygulamaları tarafından desteklenen sözleşmelere bağlı olan eklentileri bulma.

- **Etkinleştirme**: Eklentilerle iletişim yükleme, çalıştırma ve kurma.

- **Yalıtım**: Uygulama etki alanlarını veya işlemlerini kullanarak, uygulamaları, eklentilerle ilgili olası güvenlik ve yürütme sorunlarından koruyan yalıtım sınırları oluşturmak için kullanabilirsiniz.

- **İletişim**: Eklentilerin ve konak uygulamaların, yöntemleri çağırarak ve verileri geçirerek yalıtım sınırları genelinde birbirleriyle iletişim kurmasına izin verme.

- **Ömür yönetimi**: Uygulama etki alanlarını ve süreçlerini temiz, öngörülebilir bir şekilde yükleme ve kaldırma (bkz. [uygulama etki alanları](../../app-domains/application-domains.md)).

- **Sürüm oluşturma**: Konak uygulamalarının ve eklentilerin, her birinin yeni sürümleri oluşturulduğunda iletişim kurabildiğinden emin olmak.

Son olarak, güçlü bir eklenti modelinin geliştirilmesi, önemsiz olmayan bir zorunluluğudur. Bu nedenle .NET Framework, eklenti modelleri oluşturmak için bir altyapı sağlar.

> [!NOTE]
> Eklentiler hakkında daha ayrıntılı bilgi için bkz. eklentiler [ve genişletilebilirlik](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).

<a name="NETFrameworkAddInModelOverview"></a>

## <a name="net-framework-add-in-model-overview"></a>.NET Framework eklenti modeline genel bakış

<xref:System.AddIn> Ad alanında bulunan .NET Framework eklenti modeli, eklenti genişletilebilirliği geliştirmeyi basitleştirmek için tasarlanan bir tür kümesi içerir. .NET Framework eklenti modelinin temel birimi, bir ana bilgisayar uygulamasının ve bir eklentinin birbirleriyle nasıl iletişim kuracağını tanımlayan *sözleşmedir*. Bir sözleşme, sözleşmenin ana uygulamaya özgü *görünümünü* kullanarak bir konak uygulamasına sunulur. Benzer şekilde, sözleşmenin eklentiye özgü *görünümü* , eklentiye sunulur. Bir *Bağdaştırıcı* , bir konak uygulamasına ve bir eklentinin sözleşmenin ilgili görünümleri arasında iletişim kurmasına izin vermek için kullanılır. Sözleşmeler, görünümler ve bağdaştırıcılar segment olarak adlandırılır ve ilgili bir kesim kümesi bir işlem *hattı*oluşturur. İşlem hatları, .NET Framework eklentisi modelinin bulma, etkinleştirme, güvenlik yalıtımı, yürütme yalıtımı (hem uygulama etki alanları, hem de süreçler kullanılarak), iletişim, ömür yönetimi ve sürüm oluşturmayı desteklediği temelidir.

Bu desteğin toplamı, geliştiricilerin ana bilgisayar uygulamasının işlevselliğiyle tümleştirilen eklentiler oluşturmalarına olanak tanır. Ancak, bazı senaryolarda konak uygulamalarının eklentiler tarafından belirtilen kullanıcı arabirimlerini görüntülemesi gerekir. .NET Framework her sunu teknolojisinin kullanıcı arabirimlerini uygulamak için kendi modeli olduğundan, .NET Framework eklenti modeli belirli bir sunum teknolojisini desteklemez. Bunun yerine WPF, eklentiler için UI desteğiyle .NET Framework eklenti modelini genişletir.

<a name="WPFAddInModel"></a>

## <a name="wpf-add-ins"></a>WPF eklentileri

WPF, .NET Framework eklentisi modeliyle birlikte, ana bilgisayar uygulamalarının eklentilerden kullanıcı arabirimlerini görüntülemesini gerektiren çok çeşitli senaryolara olanak tanır. Özellikle, bu senaryolar aşağıdaki iki programlama modeli ile WPF tarafından karşılanır:

1. **Eklenti bir kullanıcı arabirimi döndürür**. Bir eklenti, anlaşma tarafından tanımlanan bir yöntem çağrısı aracılığıyla konak uygulamasına bir kullanıcı arabirimi döndürür. Bu senaryo aşağıdaki durumlarda kullanılır:

    - Bir eklenti tarafından döndürülen bir kullanıcı arabiriminin görünümü, yalnızca çalışma zamanında bulunan, dinamik olarak oluşturulan raporlar gibi verilere veya koşullara bağlıdır.

    - Bir eklenti tarafından sunulan hizmetler için Kullanıcı arabirimi, eklentiyi kullanan konak uygulamalarının kullanıcı arabiriminden farklıdır.

    - Eklenti öncelikle konak uygulama için bir hizmet gerçekleştirir ve konak uygulamasına durumu bir kullanıcı arabirimi ile bildirir.

2. **Eklenti bir kullanıcı arabirimi**. Bir eklenti, anlaşma tarafından tanımlanan bir UI 'dir. Bu senaryo aşağıdaki durumlarda kullanılır:

    - Bir eklenti, bir reklam gibi gösterilenden farklı hizmetler sağlamaz.

    - Bir eklenti tarafından sunulan hizmetler için Kullanıcı arabirimi, hesap makinesi veya renk seçici gibi bu eklentiyi kullanan tüm konak uygulamaları için ortaktır.

Bu senaryolar, konak uygulama ve eklenti uygulama etki alanları arasında UI nesnelerinin geçirilmesini gerektirir. .NET Framework eklentisi modeli, uygulama etki alanları arasında iletişim kurmak için uzaktan iletişimi temel aldığından, aralarında geçen nesneler Uzaktan erişilebilir olmalıdır.

Uzaktan erişilebilen bir nesne, aşağıdakilerden birini veya birkaçını yapan bir sınıfın örneğidir:

- <xref:System.MarshalByRefObject> Sınıfından türetilir.

- <xref:System.Runtime.Serialization.ISerializable> Arabirimini uygular.

- <xref:System.SerializableAttribute> Özniteliği uygulandı.

> [!NOTE]
> Uzaktan erişilebilir .NET Framework nesnelerinin oluşturulmasıyla ilgili daha fazla bilgi için bkz. [nesneleri uzaktan](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/wcf3swha(v=vs.100))oluşturma.

WPF Kullanıcı arabirimi türleri uzaktan erişilebilir değildir. WPF, sorunu çözmek için, eklentiler tarafından oluşturulan WPF Kullanıcı arabirimini konak uygulamalardan görüntülenmek üzere .NET Framework eklenti modelini genişletir. Bu destek WPF tarafından iki tür <xref:System.AddIn.Contract.INativeHandleContract> tarafından sağlanır: arabirimi ve <xref:System.AddIn.Pipeline.FrameworkElementAdapters> sınıfı tarafından uygulanan iki statik yöntem: <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> ve <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>. Yüksek düzeyde, bu türler ve yöntemler aşağıdaki şekilde kullanılır:

1. WPF, Eklentiler, denetimler, Kullanıcı denetimleri, düzen bölmeleri ve sayfalar gibi doğrudan ya da dolaylı <xref:System.Windows.FrameworkElement>olarak türetilmiş bir sınıf olmalıdır.

2. Sözleşmenin, eklenti ile ana bilgisayar uygulaması arasında bir kullanıcı arabirimi geçirdiğini bildiren her yerde, bir <xref:System.AddIn.Contract.INativeHandleContract> ( <xref:System.Windows.FrameworkElement>değil) olarak bildirilmelidir; <xref:System.AddIn.Contract.INativeHandleContract> , yalıtım sınırları arasında geçirilebileceğini, eklenti Kullanıcı arabiriminin Uzaktan erişilebilir bir gösterimidir.

3. Eklentinin uygulama etki alanından geçirilmeden önce, bir <xref:System.Windows.FrameworkElement> , çağırarak <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>bir <xref:System.AddIn.Contract.INativeHandleContract> olarak paketlenmiştir.

4. Ana bilgisayar uygulamasının uygulama etki alanına geçtikten sonra, <xref:System.AddIn.Contract.INativeHandleContract> çağırarak <xref:System.Windows.FrameworkElement> <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>olarak yeniden paketlenmesi gerekir.

, Ve kullanılması,<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> belirli senaryoya bağlıdır. <xref:System.AddIn.Contract.INativeHandleContract> <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> Aşağıdaki bölümlerde her bir programlama modeli için ayrıntılar sağlanmaktadır.

<a name="ReturnUIFromAddInContract"></a>

## <a name="add-in-returns-a-user-interface"></a>Eklenti bir kullanıcı arabirimi döndürüyor

Bir eklentinin bir konak uygulamasına bir kullanıcı arabirimi döndürmesi için aşağıdakiler gereklidir:

1. Ana bilgisayar uygulaması, eklenti ve işlem hattı, .NET Framework [eklentileri ve genişletilebilirlik](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)) belgelerinde açıklandığı şekilde oluşturulmalıdır.

2. Sözleşmenin, bir Kullanıcı <xref:System.AddIn.Contract.IContract> arabirimi döndürmesi ve bir UI döndürmesi gerekir, sözleşmenin bir dönüş değeri türünde <xref:System.AddIn.Contract.INativeHandleContract>bir yöntem bildirmesi gerekir.

3. Eklenti ile konak uygulama arasında geçirilen kullanıcı arabirimi doğrudan veya dolaylı olarak türetilmiş <xref:System.Windows.FrameworkElement>olmalıdır.

4. Eklentinin döndürdüğü Kullanıcı arabiriminin, yalıtım sınırını geçmeden <xref:System.Windows.FrameworkElement> <xref:System.AddIn.Contract.INativeHandleContract> önce bir öğesine dönüştürülmesi gerekir.

5. Döndürülen Kullanıcı arabiriminin, yalıtım sınırını geçtikten <xref:System.AddIn.Contract.INativeHandleContract> <xref:System.Windows.FrameworkElement> sonra bir öğesine dönüştürülmesi gerekir.

6. Ana bilgisayar uygulaması döndürülen <xref:System.Windows.FrameworkElement>öğesini görüntüler.

UI döndüren bir eklentinin nasıl uygulanacağını gösteren bir örnek için, bkz. [Kullanıcı arabirimi döndüren eklenti oluşturma](how-to-create-an-add-in-that-returns-a-ui.md).

<a name="AddInIsAUI"></a>

## <a name="add-in-is-a-user-interface"></a>Eklenti bir kullanıcı arabirimidir

Bir eklenti bir kullanıcı arabirimi olduğunda aşağıdakiler gereklidir:

1. Ana bilgisayar uygulaması, eklenti ve işlem hattı, .NET Framework [eklentileri ve genişletilebilirlik](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)) belgelerinde açıklandığı şekilde oluşturulmalıdır.

2. Eklentiye ait sözleşme arabiriminin uygulanması <xref:System.AddIn.Contract.INativeHandleContract>gerekir.

3. Konak uygulamasına geçirilen eklenti doğrudan veya dolaylı olarak türetilmiş <xref:System.Windows.FrameworkElement>olmalıdır.

4. Eklenti, yalıtım sınırını geçmeden <xref:System.Windows.FrameworkElement> <xref:System.AddIn.Contract.INativeHandleContract> önce bir öğesinden öğesine dönüştürülmelidir.

5. Bu eklenti, yalıtım sınırını geçtikten <xref:System.AddIn.Contract.INativeHandleContract> <xref:System.Windows.FrameworkElement> sonra bir öğesinden öğesine dönüştürülmelidir.

6. Ana bilgisayar uygulaması döndürülen <xref:System.Windows.FrameworkElement>öğesini görüntüler.

Kullanıcı arabirimi olan bir eklentinin nasıl uygulanacağını gösteren bir örnek için, bkz. [UI olan eklenti oluşturma](how-to-create-an-add-in-that-is-a-ui.md).

<a name="ReturningMultipleUIsFromAnAddIn"></a>

## <a name="returning-multiple-uis-from-an-add-in"></a>Bir eklentiden birden çok Uıto döndürme

Eklentiler, ana bilgisayar uygulamalarının görüntülemesi için genellikle birden çok kullanıcı arabirimi sağlar. Örneğin, bir kullanıcı arabirimi olarak da konak uygulamasına durum bilgilerini sağlayan bir kullanıcı arabirimi olan bir eklentiyi düşünün. Bu gibi bir eklenti, her iki eklentinin de bir [Kullanıcı arabirimi döndürür](#ReturnUIFromAddInContract) ve [eklenti bir kullanıcı arabirimi](#AddInIsAUI) modelleridir.

<a name="AddInsAndXBAPs"></a>

## <a name="add-ins-and-xaml-browser-applications"></a>Eklentiler ve XAML tarayıcı uygulamaları

Bu örnekte, ana bilgisayar uygulaması yüklenmiş bir tek başına uygulamadır. Ancak [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] , aşağıdaki ek derleme ve uygulama gereksinimleriyle birlikte eklentileri de barındırabilirsiniz:

- Uygulama bildirimi, işlem hattını (klasörler ve derlemeler) ve eklenti derlemesini istemci makinedeki ClickOnce uygulama önbelleğine, ile aynı klasöre [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]indirmek için özel olarak yapılandırılmalıdır. [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]

- Eklentilerin keşfedilmesine ve yüklenmesine yönelik [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] kodun,işlemhattıveeklentikonumugibiClickOnceuygulamaönbelleğinikullanmasıgerekir.[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]

- Eklenti, kaynak sitesinde bulunan gevşek dosyalara başvuruyorsa, eklentileri özel bir güvenlik bağlamına yüklemesi [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] gerekir;tarafındanbarındırıldığındaeklentileryalnızcaanabilgisayaruygulamasınınsitesindebulunangevşekdosyalarabaşvurabilir[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] kaynak.

Bu görevler, aşağıdaki alt bölümlerde ayrıntılı olarak açıklanmıştır.

### <a name="configuring-the-pipeline-and-add-in-for-clickonce-deployment"></a>ClickOnce dağıtımı için işlem hattı ve eklentiyi yapılandırma

[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]ClickOnce dağıtım önbelleğindeki güvenli bir klasöre indirilir ve buradan çalıştırılır. Bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] eklentinin barındırmasını sağlamak için, işlem hattı ve eklenti derlemesi güvenli klasöre de indirilmelidir. Bunu başarmak için, uygulama bildirimini indirmek üzere hem işlem hattı hem de eklenti derlemesini içerecek şekilde yapılandırmanız gerekir. İşlem hattı ve eklenti derlemesinin, [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]ardışık düzen derlemelerini algılamak [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] için konak [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] projesinin kök klasöründe olması gerekir, ancak ' de bu en kolay şekilde yapılır.

Sonuç olarak, ilk adım, her bir ardışık düzen derlemesinin ve eklenti derleme projelerinin yapı çıkışını [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] ayarlayarak projenin köküne ardışık düzen ve eklenti derlemesini oluşturmak için kullanılır. Aşağıdaki tabloda, konak [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] projesi ile aynı çözümde ve kök klasörde bulunan işlem hattı derleme projeleri ve eklenti derleme projesi için yapı çıkış yolları gösterilmektedir.

Tablo 1: Bir XBAP tarafından barındırılan işlem hattı derlemeleri için derleme çıkış yolları

|Ardışık düzen derleme projesi|Derleme çıkış yolu|
|-------------------------------|-----------------------|
|Sözleşme|`..\HostXBAP\Contracts\`|
|Eklenti görünümü|`..\HostXBAP\AddInViews\`|
|Eklenti tarafı bağdaştırıcı|`..\HostXBAP\AddInSideAdapters\`|
|Konak tarafı bağdaştırıcısı|`..\HostXBAP\HostSideAdapters\`|
|Eklenti|`..\HostXBAP\AddIns\WPFAddIn1`|

Sonraki adım, aşağıdaki işlemleri gerçekleştirerek işlem hattı derlemelerini ve eklenti derlemesini [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] içerik [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] dosyaları olarak belirtmektir:

1. Çözüm Gezgini içindeki her bir işlem hattı klasörüne sağ tıklayıp projeye Ekle ' yi seçerek, işlem hattını ve eklenti derlemesini projeye dahil **edin**.

2. Her bir işlem hattı derlemesinin **derleme eylemini** ve **Özellikler** penceresinden **içeriğe** eklenti derlemesini ayarlama.

Son adım, uygulama bildirimini indirme için işlem hattı derleme dosyalarını ve eklenti derleme dosyasını içerecek şekilde yapılandırmaktır. Dosyalar, [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] uygulamanın kapladığı ClickOnce önbelleğindeki klasörün kökündeki klasörlerde bulunmalıdır. Yapılandırma, aşağıdaki işlemleri yaparak ' [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] de elde edilebilir:

1. [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Projeye sağ tıklayın, **Özellikler**' e tıklayın, **Yayımla**' ya tıklayın ve ardından **uygulama dosyaları** düğmesine tıklayın.

2. **Uygulama dosyaları** iletişim kutusunda her bir ardışık düzen ve eklenti dll 'Inin **Yayımla durumunu** **(otomatik) içerecek**şekilde ayarlayın ve her BIR işlem hattı ve eklenti dll 'si için **indirme grubunu** **(gerekli)** ayarlayın.

### <a name="using-the-pipeline-and-add-in-from-the-application-base"></a>Uygulama temelinden işlem hattını ve eklentiyi kullanma

İşlem hattı ve eklenti ClickOnce dağıtımı için yapılandırıldığında, ile aynı ClickOnce önbellek klasörüne [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]indirilir. [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]'Danişlem hattını ve eklentiyi kullanmak için, kodbunları[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] uygulama tabanından almalıdır. İşlem hatları ve eklentileri kullanmak için .NET Framework eklentisi modelinin çeşitli türleri ve üyeleri, bu senaryo için özel destek sağlar. İlk olarak, yol <xref:System.AddIn.Hosting.PipelineStoreLocation.ApplicationBase> numaralandırma değeri tarafından tanımlanır. Bu değeri, aşağıdakileri içeren işlem hatlarını kullanmak için ilgili eklenti üyelerinin aşırı yüklemeleri ile birlikte kullanırsınız:

- <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>

- <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%2CSystem.String%5B%5D%29?displayProperty=nameWithType>

- <xref:System.AddIn.Hosting.AddInStore.Rebuild%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>

- <xref:System.AddIn.Hosting.AddInStore.Update%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>

### <a name="accessing-the-hosts-site-of-origin"></a>Konağın kaynak sitesine erişme

Bir eklentinin kaynak sitesinden dosyalara başvurmasına olanak sağlamak için, eklenti konak uygulamasına denk gelen güvenlik yalıtımıyla birlikte yüklenmelidir. Bu güvenlik düzeyi, <xref:System.AddIn.Hosting.AddInSecurityLevel.Host?displayProperty=nameWithType> numaralandırma değeri tarafından tanımlanır ve bir eklenti etkinleştirildiğinde <xref:System.AddIn.Hosting.AddInToken.Activate%2A> yöntemine geçirilir.

<a name="WPFAddInModelArchitecture"></a>

## <a name="wpf-add-in-architecture"></a>WPF eklentisi mimarisi

En yüksek düzeyde, bu şekilde, WPF <xref:System.Windows.FrameworkElement>, ve <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>kullanarak <xref:System.AddIn.Contract.INativeHandleContract>kullanıcı arabirimlerini (doğrudan veya dolaylı olarak <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> türetilmiş) uygulamak için .NET Framework eklentilerin kullanılmasını sağlar. Sonuç olarak ana bilgisayar uygulamasının konak uygulamasındaki kullanıcı arabiriminden görüntülenen <xref:System.Windows.FrameworkElement> bir sonucu döndürülür.

Basit UI eklenti senaryolarında bu, geliştirici ihtiyaçlarına göre çok ayrıntıdır. Özellikle, düzen, kaynak ve veri bağlama gibi ek WPF hizmetlerinden yararlanmaya başlayan daha karmaşık senaryolar için WPF 'nin .NET Framework eklenti modelini nasıl genişlettiği hakkında daha ayrıntılı bilgi için bkz. avantajları anlamak için Kullanıcı arabirimi desteği ve sınırlamaları.

Temelde, WPF bir konak uygulamasına bir eklentinin Kullanıcı arabirimini geçirmez; Bunun yerine WPF, WPF birlikte çalışabilirliği kullanarak Kullanıcı arabirimi için Win32 pencere tanıtıcısını geçirir. Bu nedenle, bir eklentinin bir konak uygulamasına bir kullanıcı arabirimi geçirildiğinde aşağıdakiler gerçekleşir:

- Eklenti tarafında, WPF konak uygulama tarafından görüntülenecek kullanıcı arabirimi için bir pencere tutamacı alır. Pencere tutamacı, <xref:System.Windows.Interop.HwndSource> <xref:System.AddIn.Contract.INativeHandleContract>ve ' den türetilen bir iç WPF sınıfı tarafından kapsüllenir. Bu sınıfın bir örneği tarafından <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> döndürülür ve eklentinin uygulama etki alanından ana bilgisayar uygulamasının uygulama etki alanına sıralanır.

- Konak uygulama tarafında WPF, ' den <xref:System.Windows.Interop.HwndSource> <xref:System.Windows.Interop.HwndHost> türetilen ve tüketen <xref:System.AddIn.Contract.INativeHandleContract>dahili bir WPF sınıfı olarak yeniden paketler. Bu sınıfın bir örneği tarafından <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> ana bilgisayar uygulamasına döndürülür.

<xref:System.Windows.Interop.HwndHost>WPF kullanıcı arabirimlerinden, pencere tutamaçları tarafından tanımlanan kullanıcı arabirimlerini göstermek için mevcuttur. Daha fazla bilgi için bkz. [WPF ve Win32 birlikte](../advanced/wpf-and-win32-interoperation.md)çalışma.

<xref:System.AddIn.Contract.INativeHandleContract>Özet, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, ve <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> ' de bir WPF Kullanıcı arabirimi için pencere tutamacının bir eklentinin bir konak uygulamasına geçirilmesine izin vermek, burada bir <xref:System.Windows.Interop.HwndHost> , ve ana bilgisayar uygulamasının Kullanıcı arabirimini görüntülendiği yerdir.

> [!NOTE]
> Konak uygulama bir <xref:System.Windows.Interop.HwndHost>aldığından, konak uygulama tarafından <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> döndürülen nesneyi eklenti tarafından (örneğin, a <xref:System.Windows.Controls.UserControl>) olarak uygulandığı türüne dönüştüremiyor.

Doğası gereği, <xref:System.Windows.Interop.HwndHost> konak uygulamalarının bunları nasıl kullanabileceğinizi etkileyen belirli sınırlamalara sahiptir. Ancak WPF, eklenti <xref:System.Windows.Interop.HwndHost> senaryoları için çeşitli yetenekler ile genişletilir. Bu avantajlar ve sınırlamalar aşağıda açıklanmıştır.

<a name="WPFAddInModelBenefits"></a>

## <a name="wpf-add-in-benefits"></a>WPF eklentisi avantajları

WPF eklentisi kullanıcı arabirimleri, ' den <xref:System.Windows.Interop.HwndHost>türetilen bir iç sınıf kullanılarak konak uygulamalardan görüntülendiğinden, bu kullanıcı arabirimleri, düzen gibi WPF Kullanıcı arabirimi hizmetleriyle ilgili <xref:System.Windows.Interop.HwndHost> yetenekler ile kısıtlanır işleme, veri bağlama, stiller, şablonlar ve kaynaklar. Ancak WPF, iç <xref:System.Windows.Interop.HwndHost> alt sınıfını aşağıdakileri içeren ek yetenekler ile genişlettiğini:

- Ana bilgisayar uygulamasının Kullanıcı arabirimi ve bir eklentinin Kullanıcı arabirimi arasında sekme. "Eklenti bir kullanıcı arabirimi" programlama modelinin, eklentinin tam olarak güvenilir veya kısmen güvenilir olup olmadığına bakılmaksızın, sekmeye izin vermek <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> için eklenti tarafı bağdaştırıcısının geçersiz kılınmasını gerektirdiğini unutmayın.

- Ana bilgisayar uygulaması kullanıcı arabirimlerinden görüntülenen eklenti Kullanıcı arabirimleri için erişilebilirlik gereksinimlerini manlama.

- WPF uygulamalarının birden çok uygulama etki alanı senaryosunda güvenle çalışmasını sağlama.

- Eklentiler güvenlik yalıtımı (yani, kısmi güven güvenlik korumalı alanı) ile çalıştırıldığında eklenti UI penceresine geçersiz erişimi engellemek. Çağırma <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> bu güvenliği sağlar:

  - "Eklenti bir kullanıcı arabirimi döndürüyor" programlama modeli için, yalıtım sınırının içindeki bir eklenti Kullanıcı arabirimine yönelik pencere tanıtıcısını geçirmenin tek yolu çağrıladır <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>.

  - "Eklenti bir kullanıcı arabirimi" programlama modeli için, eklenti tarafı bağdaştırıcısını ve <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> çağrılmasını <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> (önceki örneklerde gösterildiği gibi) geçersiz kılmak, bu durumda eklenti tarafı bağdaştırıcısının `QueryContract` uygulamasını konak tarafı bağdaştırıcısı.

- Birden çok uygulama etki alanı yürütme koruması sağlama. Uygulama etki alanlarıyla ilgili sınırlamalar nedeniyle, eklenti uygulama etki alanlarında oluşturulan işlenmemiş özel durumlar, yalıtım sınırı var olsa bile tüm uygulamanın kilitlenmesine neden olur. Ancak WPF ve .NET Framework eklenti modeli, bu sorunu geçici olarak çözmek için basit bir yol sağlar ve uygulama kararlılığını geliştirir. Bir kullanıcı arabirimini görüntüleyen bir WPF eklentisi, uygulama etki alanının <xref:System.Windows.Threading.Dispatcher> üzerinde çalıştığı iş parçacığı için, konak uygulama bir WPF uygulaması ise bir oluşturur. WPF eklentisinin <xref:System.Windows.Threading.Dispatcher.UnhandledException> <xref:System.Windows.Threading.Dispatcher>olayını işleyerek uygulama etki alanında gerçekleşen tüm işlenmeyen özel durumları tespit edebilirsiniz. Özelliğinden ' i edinebilirsiniz <xref:System.Windows.Threading.Dispatcher>. <xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A>

<a name="WPFAddInModelLimitations"></a>

## <a name="wpf-add-in-limitations"></a>WPF eklentisi sınırlamaları

WPF 'in, <xref:System.Windows.Interop.HwndSource> <xref:System.Windows.Interop.HwndHost>, ve pencere tutamaçları tarafından sağlanan varsayılan davranışlara eklediği avantajların ötesinde, konak uygulamalardan görüntülenen eklenti Kullanıcı arabirimleri için de sınırlamalar vardır:

- Bir konak uygulamasından görüntülenmiş eklenti Kullanıcı arabirimleri, ana bilgisayar uygulamasının kırpma davranışına uymaz.

- Birlikte çalışabilirlik senaryolarında *hava sahası* kavramı, eklentiler için de geçerlidir (bkz. [teknoloji bölgelerine genel bakış](../advanced/technology-regions-overview.md)).

- Ana bilgisayar uygulamasının kaynak devralma, veri bağlama ve verme gibi kullanıcı ARABIRIMI Hizmetleri, eklenti Kullanıcı arabirimleri için otomatik olarak kullanılamaz. Bu hizmetleri eklentiye sağlamak için işlem hattını güncelleştirmeniz gerekir.

- Bir eklenti Kullanıcı arabirimi, dönüşümden döndürülemez, ölçeklendirilemez, çarpıtılmış veya başka bir şekilde etkilenilemez (bkz. [dönüşümler genel bakış](../graphics-multimedia/transforms-overview.md)).

- <xref:System.Drawing> Ad alanından çizim işlemleri tarafından oluşturulan eklenti kullanıcı arabirimlerinin içindeki içerikler, Alfa karışımı içerebilir. Ancak, hem eklenti Kullanıcı arabirimi hem de içeren konak uygulama kullanıcı arabirimi% 100 opak olmalıdır; diğer bir deyişle, `Opacity` her ikisinin de özelliğinin 1 olarak ayarlanması gerekir.

- Bir eklenti Kullanıcı arabirimi içeren konak uygulamasındaki bir pencerenin `true` özelliğiolarakayarlandıysa,eklentigörünmezolur.<xref:System.Windows.Window.AllowsTransparency%2A> Bu, eklenti Kullanıcı arabirimi% 100 donuk (yani, `Opacity` özelliğin değeri 1) olsa da geçerlidir.

- Bir eklenti Kullanıcı arabirimi, aynı üst düzey penceredeki diğer WPF öğelerinin üstünde yer almalıdır.

- Eklentiyi kullanarak bir <xref:System.Windows.Media.VisualBrush>eklentinin Kullanıcı arabiriminin hiçbir bölümünün işlenemeyeceğini. Bunun yerine, eklenti, anlaşma tarafından tanımlanan yöntemler kullanılarak konak uygulamasına geçirilebilecek bir bit eşlem oluşturmak için oluşturulan kullanıcı arabiriminin anlık görüntüsünü alabilir.

- Medya dosyaları bir <xref:System.Windows.Controls.MediaElement> eklenti Kullanıcı arabirimindeki içinden yürütülemez.

- Eklenti kullanıcı arabirimi için oluşturulan fare olayları, ana bilgisayar uygulaması tarafından alınmaz veya oluşturulmaz ve `IsMouseOver` konak uygulama kullanıcı arabirimine yönelik özelliğin bir `false`değeri vardır.

- Odak, eklenti Kullanıcı arabirimindeki `GotFocus` denetimler arasında kayıldığında, ve `LostFocus` olayları konak uygulama tarafından alınmaz veya oluşturulmaz.

- Eklenti kullanıcı arabirimi içeren bir ana bilgisayar uygulamasının bölümü yazdırıldığında beyaz görünür.

- Konak uygulama yürütmeye devam ederse <xref:System.Windows.Threading.Dispatcher>, eklenti Kullanıcı arabirimi tarafından oluşturulan tüm sevkiyatcıların (bkz.), sahip eklentisi kaldırılmadan önce el ile kapatılmalıdır. Sözleşme, Eklenti kaldırılmadan önce ana bilgisayar uygulamasının eklentiye sinyal vermesini sağlayan yöntemler uygulayabilir ve bu sayede eklenti Kullanıcı arabiriminin dispatchlarını kapatmasına izin vermiş olur.

- Bir eklenti Kullanıcı arabirimi bir <xref:System.Windows.Controls.InkCanvas> veya <xref:System.Windows.Controls.InkCanvas>içeriyorsa, eklentiyi kaldıramazsınız.

<a name="PerformanceOptimization"></a>

## <a name="performance-optimization"></a>Performans Iyileştirmesi

Varsayılan olarak, birden çok uygulama etki alanı kullanıldığında, her bir uygulama için gereken çeşitli .NET Framework derlemeleri bu uygulamanın etki alanına yüklenir. Sonuç olarak, yeni uygulama etki alanları oluşturmak için gereken süre ve içindeki uygulamaları başlatmak performansı etkileyebilir. Ancak .NET Framework, uygulamaların zaten yüklü olmaları durumunda derlemeleri uygulama etki alanları arasında paylaşmasını sağlayarak başlangıç zamanlarını düşürmeniz için bir yol sağlar. Bunu, giriş noktası yöntemine ( <xref:System.LoaderOptimizationAttribute> `Main`) uygulanması gereken özniteliğini kullanarak yapabilirsiniz. Bu durumda, uygulama tanımınızı uygulamak için yalnızca kod kullanmanız gerekir (bkz. [uygulama yönetimine genel bakış](application-management-overview.md)).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.LoaderOptimizationAttribute>
- [Eklentiler ve Genişletilebilirlik](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [Uygulama Etki Alanları](../../app-domains/application-domains.md)
- [.NET Framework uzaktan Iletişim genel bakış](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kwdt6w2k(v=vs.100))
- [Nesneleri Uzaktan erişilebilir hale getirme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/wcf3swha(v=vs.100))
- [Nasıl Yapılır Konuları](how-to-topics.md)
