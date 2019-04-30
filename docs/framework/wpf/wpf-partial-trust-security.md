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
ms.openlocfilehash: 75ebf605e9abb844e7a713b448aefe2ec4cd1a27
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61696599"
---
# <a name="wpf-partial-trust-security"></a>WPF Kısmi Güven Güvenliği
<a name="introduction"></a> Genel olarak, Internet uygulamaları kötü amaçlı hasarı önlemek için kritik sistem kaynaklarına doğrudan erişimini sınırlı olmalıdır. Varsayılan olarak, [!INCLUDE[TLA#tla_html](../../../includes/tlasharptla-html-md.md)] ve istemci tarafı komut dosyası dilleri önemli sistem kaynaklarına erişmek mümkün değildir. Windows Presentation Foundation (WPF) tarayıcıda tutulan uygulamalar tarayıcıdan başlatılabilir çünkü kısıtlamaları benzer bir kümesi için uygun olmalıdır. Bu kısıtlamalar uygulamak [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] hem de bağımlı [!INCLUDE[TLA#tla_cas](../../../includes/tlasharptla-cas-md.md)] ve [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] (bkz [WPF güvenlik stratejisi - Platform güvenliği](wpf-security-strategy-platform-security.md)). Varsayılan olarak, tarayıcıda tutulan uygulamalar Internet bölgesine istek [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] Internet, yerel intranet veya yerel bilgisayarda başlatılan fark etmeksizin izin kümesi. Şey tam izinler kümesini değerinden ile çalışan uygulamalar kısmi güven ile çalıştırılması söylenir.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] çok çeşitli kadar işlevselliği mümkün olduğunca güvenli bir şekilde kısmi güvende ve birlikte kullanılabileceğini emin olmak için destek sağlayan [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)], kısmi güven programlama için ek destek sağlar.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
- [WPF özellik kısmi güven desteği](#WPF_Feature_Partial_Trust_Support)  
  
- [Kısmi güven programlama](#Partial_Trust_Programming)  
  
- [İzinleri yönetme](#Managing_Permissions)  
  
<a name="WPF_Feature_Partial_Trust_Support"></a>   
## <a name="wpf-feature-partial-trust-support"></a>WPF özellik kısmi güven desteği  
 Internet bölgesi izin kümesinin sınırlar içinde kullanmak üzere güvenli üst düzey özellikler Windows Presentation Foundation (WPF) aşağıdaki tabloda listelenmektedir.  
  
 Tablo 1: WPF kısmi güven güvenli olan özellikleri  
  
|Özellik alanı|Özellik|  
|------------------|-------------|  
|Genel|Tarayıcı penceresi<br /><br /> Site kaynak erişimi<br /><br /> IsolatedStorage (512KB sınırını)<br /><br /> UIAutomation sağlayıcıları<br /><br /> Komut vermeye genel<br /><br /> Giriş Yöntemi Düzenleyicileri (IME'ler)<br /><br /> Tablet kalem ve mürekkebi<br /><br /> Fare yakalama ve taşıma olaylarını kullanarak sanal sürükle/bırak<br /><br /> OpenFileDialog<br /><br /> XAML seri durumundan çıkarma (aracılığıyla XamlReader.Load)|  
|Web tümleştirme|Tarayıcı indirme iletişim kutusu<br /><br /> Kullanıcı tarafından başlatılan en üst düzey Gezinti<br /><br /> mailto:Links<br /><br /> Tekdüzen Kaynak Tanımlayıcısı parametreleri<br /><br /> HTTPWebRequest<br /><br /> Bir IFRAME içinde barındırılan bir WPF içeriği<br /><br /> Aynı sitede HTML sayfaları çerçevesini kullanarak barındırma<br /><br /> Aynı Site HTML WebBrowser kullanan sayfaları barındırma<br /><br /> Web Hizmetleri (ASMX)<br /><br /> Web Hizmetleri (Windows Communication Foundation'ı kullanarak)<br /><br /> Betik Oluşturma<br /><br /> Belge nesne modeli|  
|Görselleri|2B ve 3B<br /><br /> Animasyon<br /><br /> Medya (kaynak etki alanları arası ve Site)<br /><br /> Görüntüleme/Ses/Video|  
|Okuma|FlowDocuments<br /><br /> XPS belgeleri<br /><br /> Katıştırılmış & sistem yazı tipleri<br /><br /> CFF & TrueType yazı tipleri|  
|Düzenleme|Yazım denetimi<br /><br /> RichTextBox<br /><br /> Düz metin ve mürekkep Pano desteği<br /><br /> Kullanıcı tarafından başlatılan Yapıştır<br /><br /> İçerik seçili kopyalama|  
|Denetimler|Genel denetimleri|  
  
 Bu tabloda yer almaktadır [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] yüksek bir düzeyde özellikleri. Daha ayrıntılı bilgi edinmek için [!INCLUDE[TLA#tla_lhsdk](../../../includes/tlasharptla-lhsdk-md.md)] her üye tarafından gerekli olan izinleri belgeleri [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. Ayrıca, aşağıdaki özellikleri kısmi güven yürütme, özel durumlar dahil olmak üzere ilgili bilgileri daha ayrıntılı.  
  
- [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] (bkz [XAML genel bakış (WPF)](./advanced/xaml-overview-wpf.md)).  
  
- Açılan pencereler (bkz <xref:System.Windows.Controls.Primitives.Popup?displayProperty=nameWithType>).  
  
- Sürükleme ve bırakma (bkz [sürükle ve bırak genel bakış](./advanced/drag-and-drop-overview.md)).  
  
- Pano (bkz <xref:System.Windows.Clipboard?displayProperty=nameWithType>).  
  
- Görüntüleme (bkz <xref:System.Windows.Controls.Image?displayProperty=nameWithType>).  
  
- Seri hale getirme (bkz <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>, <xref:System.Windows.Markup.XamlWriter.Save%2A?displayProperty=nameWithType>).  
  
- Dosya iletişim kutusunu açın (bkz <xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>).  
  
 Aşağıdaki tabloda ana hatlarını [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] bölge izin kümesi Internet sınırlarda çalıştırılmasının güvenli olmayan özellikleri.  
  
 Tablo 2: WPF kısmi güven içinde güvenli olan özellikler  
  
|Özellik alanı|Özellik|  
|------------------|-------------|  
|Genel|Pencere (uygulama tanımlı Windows ve iletişim kutuları)<br /><br /> SaveFileDialog<br /><br /> Dosya sistemi<br /><br /> Registry Access<br /><br /> Sürükleme ve Bırakma<br /><br /> XAML serileştirme (aracılığıyla XamlWriter.Save)<br /><br /> UIAutomation istemciler<br /><br /> Kaynak penceresi erişim (HwndHost)<br /><br /> Tam konuşma desteği<br /><br /> Windows Forms birlikte çalışabilirlik|  
|Görselleri|Bit Eşlem Efektleri<br /><br /> Görüntü kodlama|  
|Düzenleme|Zengin metin biçimi Pano<br /><br /> XAML için tam destek|  
  
<a name="Partial_Trust_Programming"></a>   
## <a name="partial-trust-programming"></a>Kısmi güven programlama  
 İçin [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] uygulamaları varsayılan izin kümesinin aşan kodu güvenlik bölgesine bağlı olarak farklı bir davranış olacaktır. Bazı durumlarda, kullanıcı, yüklemeye çalıştığınızda bir uyarı alırsınız. Kullanıcı yüklemeyi iptal devam etmek seçebilirsiniz. Aşağıdaki tabloda her güvenlik bölgesi ve hangi uygulama tam güven almak yapmanız gereken uygulama davranışını açıklar.  
  
|Güvenlik Bölgesi|Davranış|Tam güven alma|  
|-------------------|--------------|------------------------|  
|Yerel bilgisayar|Otomatik tam güven|Eylem gerekmiyor.|  
|İntranet ve Güvenilen siteler|İçin tam güven istemi|Kullanıcı istemi kaynakta görebilmesi için XBAP bir sertifika ile oturum açın.|  
|Internet|"Güven verilmeyen" ile başarısız oluyor|XBAP bir sertifika ile oturum açın.|  
  
> [!NOTE]
>  Önceki tabloda açıklanan tam güven güvenilen ClickOnce dağıtım modeline izlemeyin XBAP'ler davranıştır.  
  
 Genel olarak, izin verilen izinleri aşabilir kod tek başına ve tarayıcıda tutulan uygulamalar arasında paylaşılan ortak kod olacak şekilde olasıdır. [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] ve [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] bu senaryo yönetmek için çeşitli teknikler sunar.  
  
<a name="Detecting_Permissions_using_CAS"></a>   
### <a name="detecting-permissions-using-cas"></a>CA'ları kullanarak izinleri algılama  
 Bazı durumlarda, iki tek başına uygulamalar tarafından kullanılmak üzere kitaplık derlemeleri, paylaşılan kod için mümkündür ve [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)]. Bu durumlarda, kod uygulamanın ödül kazanmış bir izin kümesi izin verdiğinden daha fazla izin gerektirebilecek işlevi yürütebilir. Microsoft .NET Framework güvenliği kullanarak belirli bir izni sahip olup olmadığını, uygulamanızın algılayabilir. Özellikle, belirli bir izni çağırarak sahip olup olmadığını sınayabilirsiniz <xref:System.Security.CodeAccessPermission.Demand%2A> istenen izin örneğinde yöntemi. Bu, yerel diskteki bir dosya kaydetme olanağı sahip olup olmadığı için bu sorguları koduna sahip aşağıdaki örnekte gösterilmiştir:  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode2)]  
  
 Bir uygulama çağrısı istenen izni yoksa <xref:System.Security.CodeAccessPermission.Demand%2A> bir güvenlik özel durum oluşturur. Aksi takdirde, izin verildi. `IsPermissionGranted` Bu davranış kapsüller ve döndürür `true` veya `false` uygun şekilde.  
  
<a name="Graceful_Degradation_of_Functionality"></a>   
### <a name="graceful-degradation-of-functionality"></a>Normal performansında işlevi  
 Kod ne yapması gereken iznine sahip olup olmadığını algılayabilmeniz için farklı bölgelerden yürütülebilir kod ilginçtir. Bölgesi olan tek şey, algılanırken mümkünse kullanıcı için alternatif sağlayacak kadar iyidir. Örneğin, bir tam güven uygulaması, genellikle kullanıcıların dosyaları kısmen güvenilen uygulamada yalnızca yalıtılmış depolamada dosya oluşturabilirsiniz, ancak istedikleri her yerde oluşturmasına olanak tanır. Bir dosya oluşturmak için kod tam güven (tek başına) uygulamaları ve kısmi güven uygulamaları (tarayıcı tarafından barındırılan) tarafından paylaşılan bir derleme var ve kullanıcıların dosyaları oluşturmak her iki uygulama istediğiniz, paylaşılan kod olup olmadığını algılanmalıdır bir dosyanın uygun konumda oluşturmadan önce kısmi veya tam güvende çalıştırma. Aşağıdaki kod, her ikisi de gösterir.  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode2)]  
  
 Çoğu durumda, kısmi güven alternatif bulamadı olmalıdır.  
  
 Bir intranet gibi denetimli bir ortamda özel bir yönetilen çerçeve içine temel istemci arasında yüklenebilir [!INCLUDE[TLA#tla_gac](../../../includes/tlasharptla-gac-md.md)]. Bu kitaplıklar, tam güven gerektiren kod yürütebilir ve yalnızca kısmi güven kullanarak izin verilen uygulamalar başvurulan <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (daha fazla bilgi için [güvenlik](security-wpf.md) ve [WPF Güvenliği Stratejisi - Platform güvenliği](wpf-security-strategy-platform-security.md)).  
  
<a name="Browser_Host_Detection"></a>   
### <a name="browser-host-detection"></a>Tarayıcı konak algılama  
 Kullanarak [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] izni başına temelinde denetlemek gerektiğinde izinlerini denetlemek için bir uygun tekniğidir. Bu teknik çalýþýrçalýþma yakalama özel durumlarda normal bir parçası olarak işleme bağlı olsa da, genel olarak önerilmez ve performans sorunları olabilir. Bunun yerine, varsa, [!INCLUDE[TLA#tla_xbap](../../../includes/tlasharptla-xbap-md.md)] kullanabileceğiniz Internet bölgesi korumalı alan içinde yalnızca çalışır, <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> true döndüren özellik [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)].  
  
> [!NOTE]
>  <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A> yalnızca bir uygulama değil hangi uygulama izin kümesi ile çalışan bir tarayıcıda çalışıyor olsun ayırır.  
  
<a name="Managing_Permissions"></a>   
## <a name="managing-permissions"></a>İzinleri yönetme  
 Varsayılan olarak, [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)] (varsayılan Internet bölgesi izin kümesi) kısmi güven ile çalıştırın. Ancak, uygulama gereksinimlerine bağlı olarak, varsayılan izinler kümesini değiştirmek mümkündür. Örneğin, bir [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)] başlatılan bir yerel intranetten, aşağıdaki tabloda gösterilen bir artan izin kümesinin yararlanabilirsiniz.  
  
 Tablo 3: LocalIntranet ve Internet izinleri  
  
|İzin|Öznitelik|LocalIntranet|Internet|  
|----------------|---------------|-------------------|--------------|  
|DNS|Erişim DNS sunucuları|Evet|Hayır|  
|Ortam Değişkenleri|Oku|Evet|Hayır|  
|Dosya iletişim kutuları|Open|Evet|Evet|  
|Dosya iletişim kutuları|Sınırsız|Evet|Hayır|  
|Yalıtılmış Depolama|Derleme kullanıcıya göre yalıtım|Evet|Hayır|  
|Yalıtılmış Depolama|Bilinmeyen yalıtım|Evet|Evet|  
|Yalıtılmış Depolama|Sınırsız kullanıcı kotası|Evet|Hayır|  
|Medya|Güvenli ses, video ve görüntü|Evet|Evet|  
|Yazdırma|Varsayılan yazdırma|Evet|Hayır|  
|Yazdırma|Güvenli Yazdırma|Evet|Evet|  
|Yansıma|Yayma|Evet|Hayır|  
|Güvenlik|Yönetilen kod yürütmesi|Evet|Evet|  
|Güvenlik|Verilen izinler onaylama|Evet|Hayır|  
|Kullanıcı Arabirimi|Sınırsız|Evet|Hayır|  
|Kullanıcı Arabirimi|Güvenli üst düzey windows|Evet|Evet|  
|Kullanıcı Arabirimi|Kendi Pano|Evet|Evet|  
|Web tarayıcısı|Güvenli gezintiyi HTML|Evet|Evet|  
  
> [!NOTE]
>  Kes ve Yapıştır yalnızca izin verilir kısmi güvende kullanıcı tarafından başlatılan olduğunda.  
  
 İzinleri artırmanız gerekiyorsa, ClickOnce Uygulama bildirimi ve proje ayarları değiştirmeniz gerekir. Daha fazla bilgi için [WPF XAML tarayıcı uygulamalarına genel bakış](./app-development/wpf-xaml-browser-applications-overview.md). Aşağıdaki belgeler de yararlı olabilir.  
  
- [Mage.exe (bildirim üretme ve düzenleme aracı)](../tools/mage-exe-manifest-generation-and-editing-tool.md).  
  
- [MageUI.exe (bildirim üretme ve düzenleme aracı, grafik istemci)](../tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).  
  
- [ClickOnce uygulamalarının güvenliğini sağlama](/visualstudio/deployment/securing-clickonce-applications).  
  
 Varsa, [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] tam güven gerektirir istenen izinleri artırmak için kullandığınız araçları kullanabilirsiniz. Ancak bir [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] yüklü ve yerel bilgisayardan, intranet veya güvenilen veya izin verilen siteler tarayıcının listelenen bir URL'den başlatılan yalnızca tam güven alırsınız. İntranet veya güvenilen sitesinden uygulama yüklü değilse, kullanıcı yükseltilmiş izinler göndermeyeceğinizi standart ClickOnce istemi alırsınız. Kullanıcı yüklemeyi iptal devam etmek seçebilirsiniz.  
  
 Alternatif olarak, herhangi bir güvenlik bölgesi dağıtımından tam güven için ClickOnce dağıtımı güvenilen modelini kullanabilirsiniz. Daha fazla bilgi için [Trusted Application Deployment Overview](/visualstudio/deployment/trusted-application-deployment-overview) ve [güvenlik](security-wpf.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenlik](security-wpf.md)
- [WPF Güvenlik Stratejisi - Platform Güvenliği](wpf-security-strategy-platform-security.md)
- [WPF Güvenlik Stratejisi - Güvenlik Mühendisliği](wpf-security-strategy-security-engineering.md)
