---
title: Kısmi Güven Güvenliği
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
ms.openlocfilehash: 99c7d9cfae2b137053ca77d9e3d7055b4674ce5b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174582"
---
# <a name="wpf-partial-trust-security"></a>WPF Kısmi Güven Güvenliği
<a name="introduction"></a>Genel olarak, Internet uygulamalarının kötü amaçlı zararları önlemek için kritik sistem kaynaklarına doğrudan erişimi kısıtlanmalıdır. Varsayılan olarak, HTML ve istemci tarafı komut dosyası dilleri kritik sistem kaynaklarına erişemez. Windows Presentation Foundation (WPF) tarayıcı tarafından barındırılan uygulamalar tarayıcıdan başlatılabildiği için, benzer bir dizi kısıtlamaya uymaları gerekir. Bu kısıtlamaları uygulamak için WPF hem Kod Erişim Güvenliği 'ne (CAS) hem de ClickOnce'ye dayanır (bkz. [WPF Güvenlik Stratejisi - Platform Güvenliği).](wpf-security-strategy-platform-security.md) Varsayılan olarak, tarayıcı tarafından barındırılan uygulamalar, Internet'ten, yerel intranetten veya yerel bilgisayardan başlatılıp başlatılmadığına bakılmaksızın Internet bölgesi CAS izinleri kümesini ister. Tam izin kümesinden daha azıyla çalışan uygulamaların kısmi güvenle çalıştırDığı söylenir.  
  
 WPF, mümkün olduğunca çok işlevselliğin kısmi güven içinde güvenli bir şekilde kullanılabilmesini sağlamak için geniş bir destek yelpazesi sağlar ve CAS ile birlikte kısmi güven programlama için ek destek sağlar.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
- [WPF Özelliği Kısmi Güven Desteği](#WPF_Feature_Partial_Trust_Support)  
  
- [Kısmi Güven Programlama](#Partial_Trust_Programming)  
  
- [İzlikleri Yönetme](#Managing_Permissions)  
  
<a name="WPF_Feature_Partial_Trust_Support"></a>
## <a name="wpf-feature-partial-trust-support"></a>WPF Özelliği Kısmi Güven Desteği  
 Aşağıdaki tabloda, Windows Sunu Temeli'nin (WPF) Internet bölgesi izin kümesi sınırları içinde kullanımı güvenli olan üst düzey özellikleri listelenir.  
  
 Tablo 1: Kısmi Güvende Güvenli Olan WPF Özellikleri  
  
|Özellik Alanı|Özellik|  
|------------------|-------------|  
|Genel|Tarayıcı Penceresi<br /><br /> Menşe Erişim Sitesi<br /><br /> İzole Depolama (512KB Limit)<br /><br /> UIAutomation Sağlayıcıları<br /><br /> Komuta<br /><br /> Giriş Yöntemi Düzenleyicileri (IME'ler)<br /><br /> Tablet Kalemi ve Mürekçe<br /><br /> Fare Yakalama ve Taşıma Olaylarını Kullanarak Benzetimli Sürükle/Bırak<br /><br /> Openfiledialog<br /><br /> XAML Deserialization (XamlReader.Load üzerinden)|  
|Web Entegrasyonu|Tarayıcı İndir Diyajı<br /><br /> Üst Düzey Kullanıcı Tarafından Başlatılan Navigasyon<br /><br /> mailto:links<br /><br /> Tek düzen Kaynak Tanımlayıcı Parametreleri<br /><br /> HTTPWebRequest<br /><br /> IFRAME'de Barındırılan WPF İçeriği<br /><br /> Çerçeve yi kullanarak Aynı Site HTML Sayfalarının Barındırılmaya<br /><br /> WebBrowser kullanarak Aynı Site HTML Sayfalarının Barındırılmaya<br /><br /> Web Hizmetleri (ASMX)<br /><br /> Web Hizmetleri (Windows Communication Foundation kullanarak)<br /><br /> Betik Oluşturma<br /><br /> Belge Nesnesi Modeli|  
|Görseller|2B ve 3D<br /><br /> Animasyon<br /><br /> Medya (Site Origin ve Cross-Domain)<br /><br /> Görüntüleme/Ses/Video|  
|Okuma|FlowDocuments<br /><br /> XPS Belgeleri<br /><br /> Gömülü & Sistem Yazı Tipleri<br /><br /> CFF & TrueType Yazı Tipleri|  
|Düzenleme|Yazım Denetimi<br /><br /> RichTextBox<br /><br /> Düz metin ve Mürekkep Pano Desteği<br /><br /> Kullanıcı Tarafından Başlatılan Yapıştır<br /><br /> Seçili İçeriği Kopyalama|  
|Denetimler|Genel Kontroller|  
  
 Bu tablo, wpf özelliklerini yüksek düzeyde kapsar. Daha ayrıntılı bilgi için, Windows SDK WPF'deki her üye tarafından gerekli olan izinleri belgeler. Ayrıca, aşağıdaki özellikler, özel hususlar da dahil olmak üzere kısmi güven yürütme ile ilgili daha ayrıntılı bilgilere sahiptir.  
  
- [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)](bkz. [XAML Genel Bakış (WPF)](../../desktop-wpf/fundamentals/xaml.md)).  
  
- Açılır pencereler (bkz. <xref:System.Windows.Controls.Primitives.Popup?displayProperty=nameWithType>).  
  
- Sürükle ve Bırak (bkz. [Sürükle ve Bırak Genel Bakış](./advanced/drag-and-drop-overview.md)).  
  
- Pano (bkz. <xref:System.Windows.Clipboard?displayProperty=nameWithType>  
  
- Görüntüleme (bkz. <xref:System.Windows.Controls.Image?displayProperty=nameWithType>).  
  
- Serileştirme (bkz. <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType> <xref:System.Windows.Markup.XamlWriter.Save%2A?displayProperty=nameWithType>  
  
- Dosya İletişim Kutusunu Aç <xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>(bkz. ).  
  
 Aşağıdaki tabloda, Internet bölgesi izin kümesi sınırları içinde çalıştırılmak için güvenli olmayan WPF özellikleri özetlenir.  
  
 Tablo 2: Kısmi Güvende Güvenli Olmayan WPF Özellikleri  
  
|Özellik Alanı|Özellik|  
|------------------|-------------|  
|Genel|Pencere (Uygulama Tanımlı Windows ve İletişim Kutuları)<br /><br /> Savefiledialog<br /><br /> Dosya Sistemi<br /><br /> Kayıt Defteri Erişimi<br /><br /> Sürükleme ve Bırakma<br /><br /> XAML Serileştirme (XamlWriter.Save üzerinden)<br /><br /> UIAutomation Müşterileri<br /><br /> Kaynak Pencere Erişimi (HwndHost)<br /><br /> Tam Konuşma Desteği<br /><br /> Windows Formlar Birlikte Çalışabilirlik|  
|Görseller|Bit Eşlem Efektleri<br /><br /> Görüntü Kodlama|  
|Düzenleme|Zengin Metin Biçimi Panosu<br /><br /> Tam XAML desteği|  
  
<a name="Partial_Trust_Programming"></a>
## <a name="partial-trust-programming"></a>Kısmi Güven Programlama  
 XBAP uygulamalarında, varsayılan izin kümesini aşan kod, güvenlik bölgesine bağlı olarak farklı davranışa sahip olur. Bazı durumlarda, kullanıcı yüklemeye çalıştıklarında bir uyarı alır. Kullanıcı yüklemeyi devam etmeyi veya iptal etmeyi seçebilir. Aşağıdaki tabloda, her güvenlik bölgesi için uygulamanın davranışı ve uygulamanın tam güven alması için yapmanız gerekenler açıklanmaktadır.  
  
|Güvenlik Bölgesi|Davranış|Tam Güven Alma|  
|-------------------|--------------|------------------------|  
|Yerel bilgisayar|Otomatik tam güven|Hiçbir eylem gerekli değildir.|  
|Intranet ve güvenilir siteler|Tam güven için komut istemi|Kullanıcının kaynağı istekte görmesi için XBAP'yi bir sertifikayla imzalayın.|  
|Internet|"Güven Verilmedi" ile başarısız olur|XBAP'yi sertifikaile imzalayın.|  
  
> [!NOTE]
> Önceki tabloda açıklanan davranış, ClickOnce Trusted Deployment modelini izlemeyen tam güven XBAP'ları içindir.  
  
 Genel olarak, izin verilen izinleri aşan kod, hem bağımsız hem de tarayıcı tarafından barındırılan uygulamalar arasında paylaşılan ortak kod olabilir. CAS ve WPF bu senaryoyu yönetmek için çeşitli teknikler sunar.  
  
<a name="Detecting_Permissions_using_CAS"></a>
### <a name="detecting-permissions-using-cas"></a>CAS Kullanarak İzinleri Algılama  
 Bazı durumlarda, kitaplık derlemelerinde paylaşılan kodun hem bağımsız uygulamalar hem de XBAP'ler tarafından kullanılması mümkündür. Bu gibi durumlarda, kod, uygulamanın verilen izin kümesinin izin verdiğinden daha fazla izin gerektirebilecek işlevselliği yürütebilir. Uygulamanız, Microsoft .NET Framework security'yi kullanarak belirli bir izni olup olmadığını algılayabilir. Özellikle, istenen izin örneğinde <xref:System.Security.CodeAccessPermission.Demand%2A> yöntemi arayarak belirli bir izni olup olmadığını sınayabilirsiniz. Bu, bir dosyayı yerel diske kaydetme yeteneğine sahip olup olmadığını sorgulayan bir kodu olan aşağıdaki örnekte gösterilir:  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode2)]  
  
 Bir uygulama istenilen izine sahip değilse, <xref:System.Security.CodeAccessPermission.Demand%2A> arama bir güvenlik özel durum atacaktır. Aksi takdirde, izin verilmiştir. `IsPermissionGranted`bu davranışı kapsüller ve `true` döner `false` veya uygun olarak.  
  
<a name="Graceful_Degradation_of_Functionality"></a>
### <a name="graceful-degradation-of-functionality"></a>İşlevselliğin Zarif Bozulması  
 Kodun yapması gerekeni yapma izniolup olmadığını algılayabilmek, farklı bölgelerden yürütülebilen kodlar için ilginçtir. Bölge tespit bir şey olsa da, mümkünse, kullanıcı için bir alternatif sunmak için çok daha iyidir. Örneğin, tam güven uygulaması genellikle kullanıcıların istedikleri yerde dosya oluşturmasına olanak sağlarken, kısmi bir güven uygulaması yalnızca yalıtılmış depolama alanında dosya oluşturabilir. Dosya oluşturmak için kod hem tam güven (bağımsız) uygulamaları ve kısmi güven (tarayıcı barındırılan) uygulamalar tarafından paylaşılan bir derleme de varsa ve her iki uygulama da kullanıcıların dosya oluşturabilmesini istiyorsanız, paylaşılan kod bunun olup olmadığını algılamalıdır uygun konumda bir dosya oluşturmadan önce kısmi veya tam güven içinde çalışır. Aşağıdaki kod her ikisini de gösterir.  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode2)]  
  
 Çoğu durumda, kısmi bir güven alternatifi bulabilmelisin.  
  
 Intranet gibi denetlenen bir ortamda, istemci tabanına genel montaj önbelleğine (GAC) özel yönetilen çerçeveler yüklenebilir. Bu kitaplıklar tam güven gerektiren kodu yürütebilir ve yalnızca kısmi güvene <xref:System.Security.AllowPartiallyTrustedCallersAttribute> izin verilen uygulamalardan (daha fazla bilgi için [Güvenlik](security-wpf.md) ve [WPF Güvenlik Stratejisi - Platform Güvenliği'](wpf-security-strategy-platform-security.md)ne bakın) başvurulabilir.  
  
<a name="Browser_Host_Detection"></a>
### <a name="browser-host-detection"></a>Tarayıcı Ana Bilgisayar Algılama  
 İzinleri denetlemek için CAS kullanmak, izin başına kontrol etmeniz gerektiğinde uygun bir tekniktir. Ancak, bu teknik genel olarak tavsiye edilmez ve performans sorunları olabilir normal işleme, bir parçası olarak özel durumlar yakalama bağlıdır. Bunun yerine, XAML tarayıcı uygulamanız (XBAP) yalnızca Internet bölgesi sandbox içinde çalışıyorsa, XAML tarayıcı uygulamaları (XBAPs) için doğru döndüren <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> özelliği kullanabilirsiniz.  
  
> [!NOTE]
> <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A>yalnızca bir uygulamanın tarayıcıda çalışıp çalışmadığını, hangi izin kümesinin hangi izinlerle çalıştığını ayırt eder.  
  
<a name="Managing_Permissions"></a>
## <a name="managing-permissions"></a>İzlikleri Yönetme  
 Varsayılan olarak, XBAP'lar kısmi güvenle çalışır (varsayılan Internet bölgesi izni kümesi). Ancak, uygulamanın gereksinimlerine bağlı olarak, izin kümesini varsayılandan değiştirmek mümkündür. Örneğin, bir XBAP'ler yerel bir intranetten başlatılırsa, aşağıdaki tabloda gösterilen artırılmış izin kümesinden yararlanabilir.  
  
 Tablo 3: LocalIntranet ve Internet İzinleri  
  
|İzin|Öznitelik|Localıntranet|Internet|  
|----------------|---------------|-------------------|--------------|  
|DNS|DNS sunucularına erişin|Evet|Hayır|  
|Ortam Değişkenleri|Okuma|Evet|Hayır|  
|Dosya İletişim|Open|Evet|Evet|  
|Dosya İletişim|Sınırsız|Evet|Hayır|  
|Yalıtılmış Depolama|Kullanıcıya göre montaj yalıtımı|Evet|Hayır|  
|Yalıtılmış Depolama|Bilinmeyen yalıtım|Evet|Evet|  
|Yalıtılmış Depolama|Sınırsız kullanıcı kotası|Evet|Hayır|  
|Medya|Güvenli ses, video ve görüntüler|Evet|Evet|  
|Yazdırma|Varsayılan yazdırma|Evet|Hayır|  
|Yazdırma|Güvenli baskı|Evet|Evet|  
|Yansıma|Emit|Evet|Hayır|  
|Güvenlik|Yönetilen kod yürütme|Evet|Evet|  
|Güvenlik|Verilen izinleri ileri sa|Evet|Hayır|  
|Kullanıcı Arabirimi|Sınırsız|Evet|Hayır|  
|Kullanıcı Arabirimi|Güvenli üst düzey pencereler|Evet|Evet|  
|Kullanıcı Arabirimi|Kendi Panosu|Evet|Evet|  
|Web Tarayıcısı|HTML için güvenli çerçeve navigasyonu|Evet|Evet|  
  
> [!NOTE]
> Kesme ve Yapıştır'a yalnızca kullanıcı başlatıldığında kısmi güven olarak izin verilir.  
  
 İzinleri artırmanız gerekiyorsa, proje ayarlarını ve ClickOnce uygulama bildirimini değiştirmeniz gerekir. Daha fazla bilgi için [WPF XAML Tarayıcı Uygulamalarına Genel Bakış'a](./app-development/wpf-xaml-browser-applications-overview.md)bakın. Aşağıdaki belgeler de yararlı olabilir.  
  
- [Mage.exe (Manifesto Oluşturma ve Düzenleme Aracı)](../tools/mage-exe-manifest-generation-and-editing-tool.md).  
  
- [MageUI.exe (Manifesto Oluşturma ve Düzenleme Aracı, Grafik İstemci)](../tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).  
  
- [ClickOnce Uygulamaları Güvence .](/visualstudio/deployment/securing-clickonce-applications)  
  
 XBAP'ınız tam güven gerektiriyorsa, istenen izinleri artırmak için aynı araçları kullanabilirsiniz. Bir XBAP yalnızca yerel bilgisayara, intranete veya tarayıcının güvenilen veya izin verilen sitelerinde listelenen bir URL'ye yüklenir ve başlatılırsa tam güven alır. Uygulama intranet veya güvenilir bir siteden yüklenirse, kullanıcı yükseltilmiş izinleri bildiren standart ClickOnce istemini alır. Kullanıcı yüklemeyi devam etmeyi veya iptal etmeyi seçebilir.  
  
 Alternatif olarak, clickonce trusted deployment modelini herhangi bir güvenlik bölgesinden tam güven dağıtımı için kullanabilirsiniz. Daha fazla bilgi için bkz: [Güvenilir Uygulama Dağıtımına Genel Bakış](/visualstudio/deployment/trusted-application-deployment-overview) ve [Güvenlik.](security-wpf.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenlik](security-wpf.md)
- [WPF Güvenlik Stratejisi - Platform Güvenliği](wpf-security-strategy-platform-security.md)
- [WPF Güvenlik Stratejisi - Güvenlik Mühendisliği](wpf-security-strategy-security-engineering.md)
