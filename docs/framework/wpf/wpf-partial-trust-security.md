---
title: WPF Kısmi Güven Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- partial trust security [WPF]
- detecting permissions [WPF]
- security settings for Internet Explorer [WPF]
- partial trust applications [WPF], debugging
- permissions [WPF], managing
- debugging partial trust applications [WPF]
- permissions [WPF], detecting
- feature security requirements [WPF]
- managing permissions [WPF]
ms.assetid: ef2c0810-1dbf-4511-babd-1fab95b523b5
ms.openlocfilehash: 683d0a28fa151cf2116b4125dfb7a604605c7c4a
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972237"
---
# <a name="wpf-partial-trust-security"></a>WPF Kısmi Güven Güvenliği
<a name="introduction"></a>Genel olarak, kötü amaçlı hasar engellemek için Internet uygulamalarının kritik sistem kaynaklarına doğrudan erişimi olması kısıtlanmalıdır. Varsayılan olarak, HTML ve istemci tarafı komut dosyası dilleri kritik sistem kaynaklarına erişemez. Windows Presentation Foundation (WPF) tarayıcıda barındırılan uygulamalar tarayıcıdan başlatılabildiğinden, benzer bir kısıtlama kümesine uymalıdır. Bu kısıtlamaları [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] zorlamak için hem kod erişim güvenliği (CAS) hem de ClickOnce kullanır (bkz. [WPF Güvenlik Stratejisi-Platform güvenliği](wpf-security-strategy-platform-security.md)). Varsayılan olarak, tarayıcıda barındırılan uygulamalar Internet, yerel intranet veya yerel bilgisayar tarafından başlatıldıklarından bağımsız olarak Internet bölgesi CA 'ları izin kümesi ister. Tüm izin kümesinden daha az bir şekilde çalışan uygulamalar kısmi güvenle çalışıyor olarak kabul edilir.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)], olabildiğince fazla işlevselliğin kısmi güvende güvenli şekilde kullanılabileceği ve CA 'ların yanı sıra, kısmi güven programlama için ek destek sağlayan çok çeşitli destek sağlar.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
- [WPF özelliği kısmi güven desteği](#WPF_Feature_Partial_Trust_Support)  
  
- [Kısmi güven programlama](#Partial_Trust_Programming)  
  
- [Izinleri yönetme](#Managing_Permissions)  
  
<a name="WPF_Feature_Partial_Trust_Support"></a>   
## <a name="wpf-feature-partial-trust-support"></a>WPF özelliği kısmi güven desteği  
 Aşağıdaki tabloda, Internet bölgesi izin kümesi sınırları içinde kullanılmak üzere güvenli olan Windows Presentation Foundation (WPF) üst düzey özellikleri listelenmektedir.  
  
 Tablo 1: Kısmi güvende güvenli olan WPF özellikleri  
  
|Özellik alanı|Özellik|  
|------------------|-------------|  
|Genel|Tarayıcı penceresi<br /><br /> Kaynak erişimi sitesi<br /><br /> IsolatedStorage (512KB sınırı)<br /><br /> UIAutomation sağlayıcıları<br /><br /> Verme<br /><br /> Giriş Yöntemi Düzenleyicileri (IME'ler)<br /><br /> Tablet ekran kalemi ve mürekkep<br /><br /> Fare yakalama ve taşıma olayları kullanılarak sanal sürükleyip bırakma<br /><br /> OpenFileDialog<br /><br /> XAML serisini kaldırma (XamlReader. Load aracılığıyla)|  
|Web tümleştirmesi|Tarayıcı Indirme Iletişim kutusu<br /><br /> En üst düzey kullanıcı tarafından başlatılan Gezinti<br /><br /> mailto: bağlantılar<br /><br /> Tekdüzen Kaynak tanımlayıcısı parametreleri<br /><br /> HTTPWebRequest<br /><br /> IFRAME 'de barındırılan WPF Içeriği<br /><br /> Çerçeve kullanarak aynı site HTML sayfalarının barındırılması<br /><br /> WebBrowser kullanarak aynı site HTML sayfalarının barındırılması<br /><br /> Web Hizmetleri (ASMX)<br /><br /> Web Hizmetleri (Windows Communication Foundation kullanarak)<br /><br /> Betik Oluşturma<br /><br /> Belge Nesne Modeli|  
|Öğeleri|2B ve 3B<br /><br /> Animasyon<br /><br /> Medya (kaynak ve etki alanları arası)<br /><br /> Görüntü/ses/video|  
|Okuyamadı|FlowDocuments<br /><br /> XPS belgeleri<br /><br /> Katıştırılmış & sistem yazı tipleri<br /><br /> CFF & TrueType yazı tipleri|  
|Düzenleme|Yazım denetimi<br /><br /> RichTextBox<br /><br /> Düz metin ve mürekkep panosu desteği<br /><br /> Kullanıcı tarafından başlatılan yapıştırma<br /><br /> Seçili Içerik kopyalanıyor|  
|Denetimler|Genel denetimler|  
  
 Bu tablo, [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] yüksek düzeydeki özellikleri içerir. Daha ayrıntılı bilgi için, Windows yazılım geliştirme seti (SDK), içindeki [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]her üye için gereken izinleri belgeler. Ayrıca, aşağıdaki özellikler, kısmi güven yürütme ile ilgili özel konular da dahil olmak üzere daha ayrıntılı bilgiler sunar.  
  
- [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)](bkz. [xaml 'ye Genel Bakış (WPF)](./advanced/xaml-overview-wpf.md)).  
  
- Açılır pencereler ( <xref:System.Windows.Controls.Primitives.Popup?displayProperty=nameWithType>bkz.).  
  
- Sürükleyip Bırakın (bkz. [sürükleme ve bırakmaya genel bakış](./advanced/drag-and-drop-overview.md)).  
  
- Pano (bkz <xref:System.Windows.Clipboard?displayProperty=nameWithType>.).  
  
- Görüntüleme (bkz <xref:System.Windows.Controls.Image?displayProperty=nameWithType>.).  
  
- Serileştirme (bkz <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>. <xref:System.Windows.Markup.XamlWriter.Save%2A?displayProperty=nameWithType>,).  
  
- Dosya Aç Iletişim kutusu (bkz <xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>.).  
  
 Aşağıdaki tabloda Internet bölgesi izin [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] kümesi sınırları içinde çalıştırılması güvenli olmayan özellikler özetlenmektedir.  
  
 Tablo 2: Kısmi güvende güvenli olmayan WPF özellikleri  
  
|Özellik alanı|Özellik|  
|------------------|-------------|  
|Genel|Pencere (uygulama tanımlı pencereler ve Iletişim kutuları)<br /><br /> SaveFileDialog<br /><br /> Dosya sistemi<br /><br /> Kayıt defteri erişimi<br /><br /> Sürükleme ve Bırakma<br /><br /> XAML serileştirme (XamlWriter. Save aracılığıyla)<br /><br /> UIAutomation Istemcileri<br /><br /> Kaynak pencere erişimi (HwndHost)<br /><br /> Tam konuşma desteği<br /><br /> Windows Forms birlikte çalışabilirlik|  
|Öğeleri|Bit Eşlem Efektleri<br /><br /> Görüntü kodlama|  
|Düzenleme|Zengin metin biçimi panosu<br /><br /> Tam XAML desteği|  
  
<a name="Partial_Trust_Programming"></a>   
## <a name="partial-trust-programming"></a>Kısmi güven programlama  
 Uygulamalar [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] için, varsayılan izin kümesini aşan kod, güvenlik bölgesine bağlı olarak farklı davranışa sahip olur. Bazı durumlarda, Kullanıcı yüklemeyi denediklerinde bir uyarı alır. Kullanıcı devam etmeyi seçebilir veya yüklemeyi iptal edebilir. Aşağıdaki tabloda her güvenlik bölgesi için uygulamanın davranışı ve uygulamanın tam güven alması için yapmanız gerekenler açıklanmaktadır.  
  
|Güvenlik Bölgesi|Davranış|Tam güven alma|  
|-------------------|--------------|------------------------|  
|Yerel bilgisayar|Otomatik tam güven|Eylem gerekmiyor.|  
|Intranet ve güvenilen siteler|Tam güven iste|Kullanıcının istemde kaynağı görmesi için XBAP 'yi bir sertifikayla imzalayın.|  
|Internet|"Güven verilmedi" ile başarısız olur|XBAP 'yi bir sertifikayla imzalayın.|  
  
> [!NOTE]
>  Önceki tabloda açıklanan davranış, ClickOnce güvenilir dağıtım modelini takip eden tam güven XBAP 'ler içindir.  
  
 Genel olarak, izin verilen izinleri aşabilir kod büyük olasılıkla hem tek başına hem de tarayıcıda barındırılan uygulamalar arasında paylaşılan ortak koddur. CA 'lar [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] ve bu senaryonun yönetilmesi için çeşitli teknikler sunmaktadır.  
  
<a name="Detecting_Permissions_using_CAS"></a>   
### <a name="detecting-permissions-using-cas"></a>CA 'ları kullanarak Izinleri algılama  
 Bazı durumlarda, kitaplık derlemelerindeki paylaşılan kodun hem tek başına uygulamalar [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)]hem de tarafından kullanılabilmesi mümkündür. Bu durumlarda kod, uygulamanın verilen izin kümesinden izin verdiğinden daha fazla izin gerektirebilecek işlevselliği yürütebilir. Uygulamanız, Microsoft .NET Framework güvenliğini kullanarak belirli bir izin olup olmadığını algılayabilir. Özellikle, istenen iznin örneğinde <xref:System.Security.CodeAccessPermission.Demand%2A> yöntemini çağırarak belirli bir izne sahip olup olmadığını test edebilir. Bu, bir dosyayı yerel diske kaydetme yeteneğine sahip olup olmadığını sorgulayan kodu içeren aşağıdaki örnekte gösterilmiştir:  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode2)]  
  
 Bir uygulamada istenen izin yoksa, çağrısı <xref:System.Security.CodeAccessPermission.Demand%2A> bir güvenlik özel durumu oluşturur. Aksi takdirde, izin verildi. `IsPermissionGranted`Bu davranışı kapsüller ve uygun `true` `false` şekilde döndürür.  
  
<a name="Graceful_Degradation_of_Functionality"></a>   
### <a name="graceful-degradation-of-functionality"></a>Işlevsellikten oluşan düzgün düşme  
 Kodun, farklı bölgelerde yürütülebilecek kod için ne yapılması gerektiğini belirlemek için gereken izne sahip olup olmadığını tespit edebilirsiniz. Bölgenin bir şeyi algılarken, mümkünse Kullanıcı için bir alternatif sağlamak daha iyi bir seçenektir. Örneğin, bir tam güven uygulaması genellikle kullanıcıların istedikleri yerde dosya oluşturmasını sağlar, ancak kısmi bir güven uygulaması yalnızca yalıtılmış depolamada dosya oluşturabilir. Hem tam güven (tek başına) uygulamalar hem de kısmi güven (tarayıcı tarafından barındırılan) uygulamaları tarafından paylaşılan bir derlemede bir dosya oluşturmak için kod varsa ve her iki uygulama da kullanıcıların dosya oluşturabilmesini istiyorsanız, paylaşılan kod olup olmadığını algılaması gerekir uygun konumda bir dosya oluşturmadan önce kısmi veya tam güvende çalışıyor. Aşağıdaki kod her ikisini de göstermektedir.  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode2)]  
  
 Çoğu durumda, kısmi bir güvenin alternatif olarak bulunması gerekir.  
  
 İntranet gibi denetlenen bir ortamda, özel yönetilen çerçeveler, genel derleme önbelleği 'ne (GAC) istemci tabanı üzerinden yüklenebilir. Bu kitaplıklar, tam güven gerektiren ve yalnızca kullanarak <xref:System.Security.AllowPartiallyTrustedCallersAttribute> kısmi güvenle izin verilen uygulamalardan başvurulabilen kodu yürütebilir (daha fazla bilgi için bkz. [güvenlik](security-wpf.md) ve [WPF Güvenlik Stratejisi-Platform güvenliği](wpf-security-strategy-platform-security.md)).  
  
<a name="Browser_Host_Detection"></a>   
### <a name="browser-host-detection"></a>Tarayıcı ana bilgisayar algılama  
 İzinleri denetlemek için CAS kullanılması, izin temelinde denetim yapmanız gerektiğinde uygun bir tekniktir. Bu teknik, genel olarak önerilmeyen ve performans sorunlarına sahip olabilen normal işlemenin bir parçası olarak özel durumları yakalama konusuna bağımlıdır. Bunun yerine, <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)]yalnızca Internet bölgesi korumalı alanı içinde çalıştırılıyorsa, için true döndüren özelliğini kullanabilirsiniz. [!INCLUDE[TLA#tla_xbap](../../../includes/tlasharptla-xbap-md.md)]  
  
> [!NOTE]
>  <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A>yalnızca bir uygulamanın bir tarayıcıda çalışıp çalışmadığını ayırt eder, bu, bir uygulamanın hangi izin kümesiyle çalıştığını belirtir.  
  
<a name="Managing_Permissions"></a>   
## <a name="managing-permissions"></a>Izinleri yönetme  
 Varsayılan olarak, [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)] kısmi güvenle çalıştırın (varsayılan Internet bölgesi izin kümesi). Ancak, uygulamanın gereksinimlerine bağlı olarak, varsayılan olarak izin kümesini değiştirmek mümkündür. Örneğin, bir [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)] yerel intranetten başlatılmışsa, aşağıdaki tabloda gösterilen daha yüksek bir izin kümesinden yararlanabilir.  
  
 Tablo 3: LocalIntranet ve Internet Izinleri  
  
|İzin|Öznitelik|Yerel Intranet|Internet|  
|----------------|---------------|-------------------|--------------|  
|DNS|DNS sunucularına erişme|Evet|Hayır|  
|Ortam Değişkenleri|Oku|Evet|Hayır|  
|Dosya Iletişimleri|Open|Evet|Evet|  
|Dosya Iletişimleri|Edin|Evet|Hayır|  
|Yalıtılmış Depolama|Kullanıcıya göre derleme yalıtımı|Evet|Hayır|  
|Yalıtılmış Depolama|Bilinmeyen yalıtım|Evet|Evet|  
|Yalıtılmış Depolama|Sınırsız Kullanıcı kotası|Evet|Hayır|  
|Medyasını|Güvenli ses, video ve görüntüler|Evet|Evet|  
|Yazdırma|Varsayılan yazdırma|Evet|Hayır|  
|Yazdırma|Güvenli yazdırma|Evet|Evet|  
|Yansıma|Pdb|Evet|Hayır|  
|Güvenlik|Yönetilen kod yürütme|Evet|Evet|  
|Güvenlik|İzin verilen izinler|Evet|Hayır|  
|Kullanıcı Arabirimi|Edin|Evet|Hayır|  
|Kullanıcı Arabirimi|Güvenli üst düzey pencereler|Evet|Evet|  
|Kullanıcı Arabirimi|Kendi Pano|Evet|Evet|  
|Web tarayıcısı|HTML 'e güvenli çerçeve gezintisi|Evet|Evet|  
  
> [!NOTE]
>  Kesme ve yapıştırmaya yalnızca Kullanıcı başlatıldığında kısmi güvende izin verilir.  
  
 İzinleri artırmanız gerekiyorsa proje ayarlarını ve ClickOnce uygulama bildirimini değiştirmeniz gerekir. Daha fazla bilgi için bkz. [WPF XAML tarayıcı uygulamalarına genel bakış](./app-development/wpf-xaml-browser-applications-overview.md). Aşağıdaki belgeler de yararlı olabilir.  
  
- [Mage. exe (bildirim oluşturma ve düzenleme aracı)](../tools/mage-exe-manifest-generation-and-editing-tool.md).  
  
- [MageUI. exe (bildirim oluşturma ve düzenleme aracı, grafik istemci)](../tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).  
  
- [ClickOnce uygulamalarının güvenliğini sağlama](/visualstudio/deployment/securing-clickonce-applications).  
  
 Tam güven [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] gerektiriyorsa, istenen izinleri artırmak için aynı araçları kullanabilirsiniz. [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] Yalnızca, üzerinde yüklü ve yerel bilgisayar, intranet veya tarayıcının güvenilen ya da izin verilen sitelerde listelenen bir URL 'den başlatılmış olması durumunda yalnızca tam güven alırlar. Uygulama intranetten veya güvenilen bir siteden yüklendiyse, Kullanıcı, yükseltilmiş izinleri bildiren standart ClickOnce istemi alır. Kullanıcı devam etmeyi seçebilir veya yüklemeyi iptal edebilir.  
  
 Alternatif olarak, herhangi bir güvenlik bölgesinden tam güven dağıtımı için ClickOnce güvenilir dağıtım modelini kullanabilirsiniz. Daha fazla bilgi için bkz. [Güvenilen uygulama dağıtımına genel bakış](/visualstudio/deployment/trusted-application-deployment-overview) ve [güvenlik](security-wpf.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenlik](security-wpf.md)
- [WPF Güvenlik Stratejisi - Platform Güvenliği](wpf-security-strategy-platform-security.md)
- [WPF Güvenlik Stratejisi - Güvenlik Mühendisliği](wpf-security-strategy-security-engineering.md)
