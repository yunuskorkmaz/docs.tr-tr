---
title: "WPF Kısmi Güven Güvenliği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "40"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 745a5b87119bbce3211332eee9f23d80c15c9c28
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="wpf-partial-trust-security"></a>WPF Kısmi Güven Güvenliği
<a name="introduction"></a>Genel olarak, Internet uygulamaları kötü amaçlı zarar önlemek için önemli sistem kaynaklarına doğrudan erişimi olmaktan sınırlandırılmalıdır. Varsayılan olarak, [!INCLUDE[TLA#tla_html](../../../includes/tlasharptla-html-md.md)] ve istemci tarafı komut dosyası dili önemli sistem kaynaklarına erişmek mümkün değildir. Çünkü [!INCLUDE[TLA#tla_wpf](../../../includes/tlasharptla-wpf-md.md)] tarayıcıda barındırılan uygulamalar tarayıcıdan başlatılabilir, kısıtlamaları benzer bir dizi uymalıdır. Bu kısıtlamaları zorlamak için [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] hem dayanır [!INCLUDE[TLA#tla_cas](../../../includes/tlasharptla-cas-md.md)] ve [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] (bkz [WPF güvenlik stratejisi - Platform güvenliği](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)). Varsayılan olarak, tarayıcıda barındırılan uygulamalar Internet bölgesi isteği [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] Internet, yerel intranet ya da yerel bilgisayar başlatıldığında yedeklemiş izinler kümesi. Herhangi bir şey izinler kümesini değerinden ile çalışan uygulamalar, kısmi güven ile çalışan söylenir.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]çok çeşitli kadar işlevselliği mümkün olduğunca güvenli bir şekilde kısmi güven ve ile birlikte kullanılabilir emin olmak için destek sağlar [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)], kısmi güven programlama için ek destek sağlar.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
-   [WPF özellik kısmi güven desteği](#WPF_Feature_Partial_Trust_Support)  
  
-   [Kısmi güven programlama](#Partial_Trust_Programming)  
  
-   [İzinleri yönetme](#Managing_Permissions)  
  
<a name="WPF_Feature_Partial_Trust_Support"></a>   
## <a name="wpf-feature-partial-trust-support"></a>WPF özellik kısmi güven desteği  
 Aşağıdaki tabloda, üst düzey özellikleri listeler [!INCLUDE[TLA#tla_wpf](../../../includes/tlasharptla-wpf-md.md)] Internet bölgesi izin kümesi sınırları içinde kullanmak güvenli olan.  
  
 Tablo 1: kısmi güven kasada WPF özellikleri  
  
|Özellik alanı|Özellik|  
|------------------|-------------|  
|Genel|Bir tarayıcı penceresi<br /><br /> Kaynak erişim site<br /><br /> IsolatedStorage (512KB sınırı)<br /><br /> UIAutomation sağlayıcıları<br /><br /> Komut verme<br /><br /> Giriş Yöntemi Düzenleyicileri (IME'ler)<br /><br /> Tablet kalem ve mürekkep<br /><br /> Fare yakalama ve taşıma olaylarını kullanarak sanal sürükle/bırak<br /><br /> OpenFileDialog<br /><br /> XAML seri durumdan çıkarma (aracılığıyla XamlReader.Load)|  
|Web tümleştirme|Tarayıcı indirme iletişim kutusu<br /><br /> Üst düzey kullanıcı tarafından başlatılan gezinme<br /><br /> mailto:Links<br /><br /> Tekdüzen Kaynak Tanımlayıcısı parametreleri<br /><br /> HTTPWebRequest<br /><br /> IFRAME içinde barındırılan WPF içeriği<br /><br /> Aynı sitede HTML sayfalarını çerçeve kullanarak barındırma<br /><br /> Aynı Site HTML WebBrowser kullanarak sayfaları barındırma<br /><br /> Web Hizmetleri (ASMX)<br /><br /> Web Hizmetleri (Windows Communication Foundation'ı kullanarak)<br /><br /> Betik Oluşturma<br /><br /> Belge nesne modeli|  
|Görsel|2B ve 3B<br /><br /> Animasyon<br /><br /> Ortam (kaynak etki alanları arası ve Site)<br /><br /> Görüntüleme/Ses/Video|  
|Okuma|FlowDocuments<br /><br /> XPS belgeleri<br /><br /> Katıştırılmış & yazı tipleri<br /><br /> CFF & TrueType yazı tipleri|  
|Düzenleme|Yazım denetimi<br /><br /> RichTextBox<br /><br /> Düz metin ve mürekkep Pano desteği<br /><br /> Kullanıcı tarafından başlatılan Yapıştır<br /><br /> Kopyalama içerik seçilmedi|  
|Denetimler|Genel denetimleri|  
  
 Bu tabloda yer almaktadır [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] yüksek bir düzeyde özellikler. Daha ayrıntılı bilgi, için [!INCLUDE[TLA#tla_lhsdk](../../../includes/tlasharptla-lhsdk-md.md)] içindeki her üyenin gerektirdiği izinler belgeleri [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. Ayrıca, aşağıdaki özellikleri daha kısmi güven yürütme, özel durumlar dahil olmak üzere ilgili ayrıntılı bilgiler.  
  
-   [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)](bkz [XAML genel bakış (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)).  
  
-   Açılan pencereler (bkz: <xref:System.Windows.Controls.Primitives.Popup?displayProperty=nameWithType>).  
  
-   Sürükleme ve bırakma (bkz [sürükle ve bırak genel bakış](../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)).  
  
-   Pano (bkz: <xref:System.Windows.Clipboard?displayProperty=nameWithType>).  
  
-   Imaging (bkz: <xref:System.Windows.Controls.Image?displayProperty=nameWithType>).  
  
-   Seri hale getirme (bkz <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>, <xref:System.Windows.Markup.XamlWriter.Save%2A?displayProperty=nameWithType>).  
  
-   Dosya iletişim kutusunu açın (bkz: <xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>).  
  
 Aşağıdaki tabloda ana hatlarını [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] Internet sınırları içinde çalıştırmak güvenli olmayan özellikler bölge izin kümesi.  
  
 Tablo 2: kısmi güven içinde güvenli WPF özellikleri  
  
|Özellik alanı|Özellik|  
|------------------|-------------|  
|Genel|Pencere (uygulama tanımlı Windows ve iletişim kutuları)<br /><br /> SaveFileDialog<br /><br /> Dosya sistemi<br /><br /> Kayıt defteri erişimi<br /><br /> Sürükleme ve Bırakma<br /><br /> XAML seri hale getirme (aracılığıyla XamlWriter.Save)<br /><br /> UIAutomation istemcileri<br /><br /> Kaynak pencere erişim (HwndHost)<br /><br /> Tam konuşma desteği<br /><br /> Windows Forms birlikte çalışabilirlik|  
|Görsel|Bit Eşlem Efektleri<br /><br /> Görüntü kodlama|  
|Düzenleme|Zengin metin biçimi Pano<br /><br /> XAML için tam destek|  
  
<a name="Partial_Trust_Programming"></a>   
## <a name="partial-trust-programming"></a>Kısmi güven programlama  
 İçin [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] uygulamalar, varsayılan izin kümesi aşan kodu güvenlik bölgesine bağlı olarak farklı davranışlar olacaktır. Yüklemeye çalıştığınızda bazı durumlarda, kullanıcı bir uyarı alırsınız. Kullanıcı, yükleme devam etmek seçebilirsiniz. Aşağıdaki tabloda her güvenlik bölgesi ve uygulama tam güven almak yapmanız gereken uygulamanın davranışını tanımlar.  
  
|Güvenlik Bölgesi|Davranış|Tam güven alma|  
|-------------------|--------------|------------------------|  
|Yerel bilgisayar|Otomatik tam güven|Eylem gerekmiyor.|  
|İntranet ve Güvenilen siteler|Tam güven istemi|Kullanıcı istemi kaynağında görebilmesi için XBAP bir sertifika ile oturum açın.|  
|Internet|"Güven yazma izni" ile başarısız oluyor|XBAP bir sertifika ile oturum açın.|  
  
> [!NOTE]
>  Yukarıdaki tabloda açıklanan için tam güven ClickOnce güvenilen dağıtım modeli izlemeyin XBAP davranıştır.  
  
 Genel olarak, izin verilen izinleri aşabilir kod tek başına ve tarayıcıda barındırılan uygulamalar arasında paylaşılan ortak kodun olması olasıdır. [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)]ve [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] bu senaryo yönetmek için çeşitli teknikler sunar.  
  
<a name="Detecting_Permissions_using_CAS"></a>   
### <a name="detecting-permissions-using-cas"></a>CA'ları kullanarak izinleri algılama  
 Bazı durumlarda, her iki tek başına uygulamaları tarafından kullanılmak üzere kitaplık derlemeleri paylaşılan kodda mümkündür ve [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)]. Bu durumlarda uygulamanın izin verilen kümesi izin verdiğinden daha fazla izin gerektirebilir işlevselliği kod yürütmek. Kullanarak bir belirli iznine sahip olup olmadığına bakılmaksızın, uygulamanızın algılayabilir [!INCLUDE[TLA#tla_winfx](../../../includes/tlasharptla-winfx-md.md)] güvenlik. Özellikle, çağırarak belirli bir izin sahip olup olmadığını sınayabilirsiniz <xref:System.Security.CodeAccessPermission.Demand%2A> istenen izin örneğinde yöntemi. Bu dosya yerel diske kaydetmeye özelliği olup bu sorguları koduna sahip aşağıdaki örnekte gösterilmiştir:  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](../../../samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](../../../samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode2)]  
  
 Bir uygulama çağrısı istenen izni yoksa <xref:System.Security.CodeAccessPermission.Demand%2A> güvenlik özel durum oluşturur. Aksi takdirde izin verildi. `IsPermissionGranted`Bu davranış yalıtır ve döndürür `true` veya `false` uygun şekilde.  
  
<a name="Graceful_Degradation_of_Functionality"></a>   
### <a name="graceful-degradation-of-functionality"></a>Normal düşmesine işlevi  
 Kod yapmanız gerekeni iznine sahip olup olmadığını algılamak için farklı bölgelerden yürütülen kod için ilginç olacaktır. Bölge olan tek şey, algılanırken mümkünse kullanıcı için alternatif sağlayacak kadar iyidir. Örneğin, bir tam güven uygulaması genellikle kullanıcıların dosyaları kısmi güven uygulama yalnızca yalıtılmış depolamada dosya oluşturabilirsiniz, ancak istedikleri her yerde oluşturmasını sağlar. Derlemedeki tam güven (tek başına) uygulamalar ve kısmi güven uygulamaları (tarayıcı barındırılan) tarafından paylaşılan bir dosya oluşturmak için kodu varsa ve her iki uygulamayı kullanıcıların dosyaları oluşturmak istediğiniz, paylaşılan kod olup olmadığını algılayan bir dosyayı uygun konumda oluşturmadan önce kısmi veya tam güvende çalıştırma. Aşağıdaki kod, her ikisi de gösterir.  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](../../../samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](../../../samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode2)]  
  
 Çoğu durumda, kısmi güven alternatif bulamıyor olması gerekir.  
  
 Bir intranet gibi denetimli bir ortamda özel yönetilen çerçeveleri içine temel istemci üzerinden yüklenebilir [!INCLUDE[TLA#tla_gac](../../../includes/tlasharptla-gac-md.md)]. Bu kitaplıklar tam güven gerektiren kod yürütebilir ve kısmi güven kullanarak yalnızca izin verilen uygulamaları başvurulan <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (daha fazla bilgi için bkz: [güvenlik](../../../docs/framework/wpf/security-wpf.md) ve [WPF Güvenliği Stratejisi - Platform güvenliği](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)).  
  
<a name="Browser_Host_Detection"></a>   
### <a name="browser-host-detection"></a>Tarayıcı konak algılama  
 Kullanarak [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] izinlerini denetlemek için bir izin başına temelinde denetlemek gerektiğinde uygun bir tekniği olan. Bu teknik çalýþýrçalýþma yakalama özel durumları normal bir parçası olarak işleme bağlı olsa da, genelde önerilmez ve performans sorunları olabilir. Bunun yerine, varsa, [!INCLUDE[TLA#tla_xbap](../../../includes/tlasharptla-xbap-md.md)] kullanabileceğiniz yalnızca çalıştığında Internet bölgesi korumalı alanı içinde <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> için true değerini döndürür özelliği [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)].  
  
> [!NOTE]
>  <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A>bir tarayıcıda, uygulama izinleri olmayan hangi kümesi ile çalışan bir uygulama çalışıp çalışmadığını yalnızca ayırır.  
  
<a name="Managing_Permissions"></a>   
## <a name="managing-permissions"></a>İzinleri yönetme  
 Varsayılan olarak, [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)] kısmi güven (varsayılan Internet bölgesi izin kümesi) çalıştırın. Ancak, uygulama gereksinimlerine bağlı olarak, varsayılan izinler kümesini değiştirmek mümkündür. Örneğin, bir [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)] başlatılan yerel intranet bağlantısı, aşağıdaki tabloda gösterilen bir artan izin kümesi özelliklerden yararlanabilirsiniz.  
  
 Tablo 3: LocalIntranet ve Internet izinleri  
  
|İzin|Öznitelik|LocalIntranet|Internet|  
|----------------|---------------|-------------------|--------------|  
|DNS|Erişim DNS sunucuları|Evet|Hayır|  
|Ortam Değişkenleri|Oku|Evet|Hayır|  
|Dosya iletişim kutuları|Open|Evet|Evet|  
|Dosya iletişim kutuları|Sınırsız|Evet|Hayır|  
|Yalıtılmış Depolama|Kullanıcı tarafından derleme yalıtımı|Evet|Hayır|  
|Yalıtılmış Depolama|Bilinmeyen yalıtım|Evet|Evet|  
|Yalıtılmış Depolama|Sınırsız kullanıcı kotası|Evet|Hayır|  
|Medya|Güvenli ses, video ve görüntü|Evet|Evet|  
|Yazdırma|Varsayılan yazdırma|Evet|Hayır|  
|Yazdırma|Güvenli Yazdırma|Evet|Evet|  
|Yansıma|Yayma|Evet|Hayır|  
|Güvenlik|Yönetilen kod yürütme|Evet|Evet|  
|Güvenlik|İzin verilenler onaylama|Evet|Hayır|  
|Kullanıcı arabirimi|Sınırsız|Evet|Hayır|  
|Kullanıcı arabirimi|Güvenli üst düzey windows|Evet|Evet|  
|Kullanıcı arabirimi|Pano sahibi|Evet|Evet|  
|Web tarayıcısı|Güvenli gezintiyi HTML|Evet|Evet|  
  
> [!NOTE]
>  Kesme ve yapıştırma izin verilir kısmi güvende kullanıcı başlatıldığında.  
  
 İzinleri artırmak gerekiyorsa, proje ayarlarını ve ClickOnce Uygulama bildirimi değiştirmeniz gerekir. Daha fazla bilgi için bkz: [WPF XAML tarayıcısı uygulamaları genel bakış](../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md). Aşağıdaki belgeler de yararlı olabilir.  
  
-   [Mage.exe (bildirim üretme ve düzenleme aracı)](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md).  
  
-   [MageUI.exe (bildirim üretme ve düzenleme aracı, grafik istemci)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).  
  
-   [ClickOnce uygulamalarının güvenliğini sağlama](/visualstudio/deployment/securing-clickonce-applications).  
  
 Varsa, [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] tam güven gerektiren istenen izinleri artırmak üzere aynı araçları kullanabilirsiniz. Ancak bir [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] yüklü olduğundan ve yerel bilgisayar, intranet veya tarayıcının güvenilen veya izin verilen siteler listelenir bir URL başlatılan yalnızca tam güven alırsınız. Uygulama intranet veya güvenilen bir site yüklediyseniz kullanıcı yükseltilmiş izinler bildiren standart ClickOnce ileti alacaksınız. Kullanıcı, yükleme devam etmek seçebilirsiniz.  
  
 Alternatif olarak, herhangi bir güvenlik bölgesi tam güven dağıtımından için ClickOnce güvenilen dağıtım modelini kullanabilirsiniz. Daha fazla bilgi için bkz: [güvenilir uygulama dağıtımına genel bakış](/visualstudio/deployment/trusted-application-deployment-overview) ve [güvenlik](../../../docs/framework/wpf/security-wpf.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenlik](../../../docs/framework/wpf/security-wpf.md)  
 [WPF Güvenlik Stratejisi - Platform Güvenliği](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)  
 [WPF Güvenlik Stratejisi - Güvenlik Mühendisliği](../../../docs/framework/wpf/wpf-security-strategy-security-engineering.md)
