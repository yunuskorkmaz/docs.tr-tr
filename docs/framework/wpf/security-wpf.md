---
title: Güvenlik (WPF)
ms.date: 03/30/2017
helpviewer_keywords:
- XAML files [WPF], sandbox behavior
- browser-hosted application security [WPF]
- application security [WPF]
- navigation security [WPF]
- loose XAML files [WPF], sandbox behavior
- WPF security [WPF]
- WebBrowser control [WPF], security
- feature controls [WPF], security
- XBAP security [WPF]
- Internet Explorer security settings [WPF]
ms.assetid: ee1baea0-3611-4e36-9ad6-fcd5205376fb
ms.openlocfilehash: 699c03d379d105806292a23b09a63d0634a7a2e4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54592691"
---
# <a name="security-wpf"></a>Güvenlik (WPF)
<a name="introduction"></a> Güvenlik modeli, Windows Presentation Foundation (WPF) tek başına ve tarayıcıda tutulan uygulamalar geliştirirken dikkate almanız gerekir. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] tek başına uygulamalar Kısıtlanmamış izinlere sahip yürütün ( [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] **FullTrust** izin kümesi), Windows Installer (.msi), XCopy kullanarak dağıtılmış olup olmadığını veya [!INCLUDE[TLA2#tla_clickonce](../../../includes/tla2sharptla-clickonce-md.md)]. Kısmi güven, ClickOnce ile tek başına WPF uygulamalarını dağıtmak desteklenmez. Ancak, tam güven uygulaması kısmi güven oluşturabilirsiniz <xref:System.AppDomain> .NET Framework eklenti modeli kullanarak. Daha fazla bilgi için [WPF eklentileri genel bakış](../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md).  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] tarayıcıda tutulan uygulamalar tarafından barındırılan [!INCLUDE[TLA#tla_iegeneric](../../../includes/tlasharptla-iegeneric-md.md)] ya da Firefox ve olabilir [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)] veya gevşek [!INCLUDE[TLA#tla_xaml](../../../includes/tlasharptla-xaml-md.md)] daha fazla bilgi için belgelere bakın [WPF XAML tarayıcı uygulamalarına genel bakış](../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md).  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] tarayıcıda tutulan uygulamalar kısmi güven güvenliği korumalı alanı içinde varsayılan olarak sınırlıdır varsayılan olarak yürütmek [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] **Internet** bölge izin kümesi. Bu etkili bir şekilde yalıtır [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] tarayıcıda barındırılan uygulamaları istemci bilgisayardan, tipik Web uygulamalarının yalıtılmış olmasını beklediğiniz gibi aynı şekilde. Bir XBAP ayrıcalıklarını, tam güven kadar dağıtım URL'si ve istemcinin güvenlik yapılandırması, güvenlik bölgesi bağlı olarak yükseltme. Daha fazla bilgi için [WPF kısmi güven güvenliği](../../../docs/framework/wpf/wpf-partial-trust-security.md).  
  
 Bu konu, Windows Presentation Foundation (WPF) tek başına ve tarayıcıda tutulan uygulamalar için güvenlik modeli açıklanır.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
-   [Güvenli gezinti](#SafeTopLevelNavigation)  
  
-   [Web gözatma yazılım güvenlik ayarları](#InternetExplorerSecuritySettings)  
  
-   [WebBrowser denetimi ve özellik denetimleri](#webbrowser_control_and_feature_controls)  
  
-   [APTCA derlemelerini kısmen güvenilen istemci uygulamaları için devre dışı bırakma](#APTCA)  
  
-   [Gevşek XAML dosyaları için sandbox davranışı](#LooseContentSandboxing)  
  
-   [Güvenlik Yükselt WPF uygulamaları geliştirme kaynakları](#BestPractices)  
  
<a name="SafeTopLevelNavigation"></a>   
## <a name="safe-navigation"></a>Güvenli gezinti  
 İçin [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)], [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] Gezinti iki tür ayırır: uygulama ve tarayıcı.  
  
 *Uygulama gezinti* tarayıcı tarafından barındırılan bir uygulamadaki içerik öğeleri arasında gezintisi. *Tarayıcı gezintisi* değişen içeriği ve konum URL'sini bir tarayıcı gezintisi. (Genellikle XAML) uygulama gezinti ve tarayıcı gezintisi (genellikle HTML) arasındaki ilişki aşağıda gösterilmiştir:
  
 ![Gezinti diyagramı](../../../docs/framework/wpf/media/safetoplevelnavigationfigure.png "SafeTopLevelNavigationFigure")  
  
 İçin güvenli olarak kabul edilen içerik türünü bir [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] gitmek için öncelikle uygulama tarayıcı Gezinti veya kullanılıp kullanılmadığını tarafından belirlenir.  
  
<a name="Application_Navigation_Security"></a>   
### <a name="application-navigation-security"></a>Uygulama gezinti güvenliği  
 Uygulama gezinti paketi ile tanımlanabilir güvenli olarak değerlendirilir [!INCLUDE[TLA2#tla_uri](../../../includes/tla2sharptla-uri-md.md)], dört içerik türlerini destekler:  
  
|İçerik Türü|Açıklama|URI örneği|  
|------------------|-----------------|-----------------|  
|Kaynak|Bir yapı türüne sahip bir projeye eklenen dosyaları **kaynak**.|`pack://application:,,,/MyResourceFile.xaml`|  
|İçerik|Bir yapı türüne sahip bir projeye eklenen dosyaları **içerik**.|`pack://application:,,,/MyContentFile.xaml`|  
|Kaynak site|Bir yapı türüne sahip bir projeye eklenen dosyaları **hiçbiri**.|`pack://siteoforigin:,,,/MySiteOfOriginFile.xaml`|  
|Uygulama kodu|Derlenmiş kod arka plan olan XAML kaynakları.<br /><br /> -veya-<br /><br /> Bir yapı türüne sahip bir projeye eklenen XAML dosyaları **sayfa**.|`pack://application:,,,/MyResourceFile``.xaml`|  
  
> [!NOTE]
>  Uygulama verileri dosyaları ve paketi hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uri#plural](../../../includes/tla2sharptla-urisharpplural-md.md)], bkz: [WPF Uygulama kaynağı, içerik ve veri dosyalarını](../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md).  
  
 İçerik bu tür dosyalar için ya da kullanıcı tarafından veya programlama yoluyla gezinilebilir:  
  
-   **Kullanıcı Gezinti**. Tıklayarak kullanıcı gittiğinde bir <xref:System.Windows.Documents.Hyperlink> öğesi.  
  
-   **Programlı Gezinti**. Uygulama ayarlayarak kullanıcının, örneğin, işe karıştırılmaksızın gider <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType> özelliği.  
  
<a name="Browser_Navigation_Security"></a>   
### <a name="browser-navigation-security"></a>Tarayıcı gezinti güvenliği  
 Tarayıcı gezintisi yalnızca aşağıdaki koşullarda güvenli olarak kabul edilir:  
  
-   **Kullanıcı Gezinti**. Tıklayarak kullanıcı gittiğinde bir <xref:System.Windows.Documents.Hyperlink> içinde ana öğesi <xref:System.Windows.Navigation.NavigationWindow>değil içinde iç içe bir <xref:System.Windows.Controls.Frame>.  
  
-   **Bölge**. Geçtiğiniz için içeriği, Internet veya yerel intranet üzerindeki bulunur.  
  
-   **Protokol**. Kullanılan protokol geçerli **http**, **https**, **dosya**, veya **mailto**.  
  
 Varsa bir [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] Bu koşullar ile uyumlu olmayan bir şekilde içerik gitmek çalışır bir <xref:System.Security.SecurityException> oluşturulur.  
  
<a name="InternetExplorerSecuritySettings"></a>   
## <a name="web-browsing-software-security-settings"></a>Web gözatma yazılım güvenlik ayarları  
 Tüm Web yazılım tarama verilen erişim bilgisayarınızın güvenlik ayarlarını belirleyin. Yazılım Web'de içeren herhangi bir uygulama veya kullanan bileşen [WinINet](https://go.microsoft.com/fwlink/?LinkId=179379) veya [UrlMon](https://go.microsoft.com/fwlink/?LinkId=179383) API'ler, Internet Explorer ve PresentationHost.exe dahil.  
  
 [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)] göre ya da yürütülecek izin işlevi olarak yapılandırabileceğiniz bir mekanizma sağlar [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)], aşağıdakiler dahil:  
  
-   .NET framework bağımlı bileşenler  
  
-   ActiveX denetimleri ve eklentiler  
  
-   İndirmeler  
  
-   Betik Oluşturma  
  
-   Kullanıcı kimlik doğrulaması  
  
 Bu şekilde güvenli hale getirilebilir işlevler koleksiyonu için bölge başına temelinde yapılandırılmış **Internet**, **Intranet**, **Güvenilen siteler**, ve  **Yasak siteler** bölgeleri. Aşağıdaki adımlar, güvenlik ayarlarının nasıl yapılandırılacağı açıklanmaktadır:  
  
1.  **Denetim Masası**'nı açın.  
  
2.  Tıklayın **ağ ve Internet** ve ardından **Internet Seçenekleri**.  
  
     Internet Seçenekleri iletişim kutusu görüntülenir.  
  
3.  Üzerinde **güvenlik** sekmesinde, güvenlik ayarlarını yapılandırmak için bir bölge seçin.  
  
4.  Tıklayın **Özel düzey** düğmesi.  
  
     **Güvenlik ayarları** iletişim kutusu görünür ve seçili bölgesi için güvenlik ayarlarını yapılandırabilirsiniz.  
  
     ![Güvenlik Ayarları iletişim kutusu](../../../docs/framework/wpf/media/wpfsecurityfigure1.PNG "WPFSecurityFigure1")  
  
> [!NOTE]
>  Ayrıca, Internet Seçenekleri iletişim kutusu için Internet Explorer'dan alabilirsiniz. Tıklayın **Araçları** ve ardından **Internet Seçenekleri**.  
  
 İle başlayarak [!INCLUDE[TLA#tla_ie7](../../../includes/tlasharptla-ie7-md.md)], özellikle .NET Framework için aşağıdaki güvenlik ayarları dahil edilir:  
  
-   **XAML kaybetmiş**. Denetimleri olmadığını [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)] gidin ve kaybedilir [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] dosyaları. (, Devre dışı bırakma, etkinleştirme ve seçenekleri isteyebilir).  
  
-   **XAML tarayıcı uygulamaları**. Denetimleri olmadığını [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)] gidin ve çalıştırma [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)]. (, Devre dışı bırakma, etkinleştirme ve seçenekleri isteyebilir).  
  
 Varsayılan olarak, bu ayarlar tüm için etkin olan **Internet**, **yerel intranet**, ve **Güvenilen siteler** bölgeleri ve için devre dışı **Kısıtlanmış siteler**  bölge.  
  
<a name="Security_Settings_for_IE6_and_Below"></a>   
### <a name="security-related-wpf-registry-settings"></a>WPF güvenlikle ilgili kayıt defteri ayarları  
 Internet Seçenekleri güvenlik ayarlarının yanı sıra çok sayıda güvenlik açısından duyarlı WPF özelliği seçerek engellemek için aşağıdaki kayıt defteri değerleri kullanılabilir. Değerler, aşağıdaki anahtarı altında tanımlanır:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\Windows Presentation Foundation\Features`  
  
 Aşağıdaki tabloda ayarlanabilir değerleri listelenmektedir.  
  
|Değer adı|Değer türü|Değer verisi|  
|----------------|----------------|----------------|  
|XBAPDisallow|REG_DWORD|engellemek için 1; izin vermek için 0'ı tıklatın.|  
|LooseXamlDisallow|REG_DWORD|engellemek için 1; izin vermek için 0'ı tıklatın.|  
|WebBrowserDisallow|REG_DWORD|engellemek için 1; izin vermek için 0'ı tıklatın.|  
|MediaAudioDisallow|REG_DWORD|engellemek için 1; izin vermek için 0'ı tıklatın.|  
|MediaImageDisallow|REG_DWORD|engellemek için 1; izin vermek için 0'ı tıklatın.|  
|MediaVideoDisallow|REG_DWORD|engellemek için 1; izin vermek için 0'ı tıklatın.|  
|ScriptInteropDisallow|REG_DWORD|engellemek için 1; izin vermek için 0'ı tıklatın.|  
  
<a name="webbrowser_control_and_feature_controls"></a>   
## <a name="webbrowser-control-and-feature-controls"></a>WebBrowser denetimi ve özellik denetimleri  
 WPF <xref:System.Windows.Controls.WebBrowser> denetimi, Web içeriğini barındırmak için kullanılabilir. WPF <xref:System.Windows.Controls.WebBrowser> denetim temel alınan WebBrowser ActiveX denetimini sarar. WPF WPF kullandığınız zaman uygulamanızın güvenliğini sağlamak için bazı desteği sağlar <xref:System.Windows.Controls.WebBrowser> barındırmak için Web içeriği güvenilmeyen. Ancak, bazı güvenlik özellikleri kullanarak uygulamalar tarafından doğrudan uygulanmalıdır <xref:System.Windows.Controls.WebBrowser> denetimi. WebBrowser ActiveX denetimi hakkında daha fazla bilgi için bkz. [WebBrowser denetimine genel bakış ve öğreticiler](https://go.microsoft.com/fwlink/?LinkId=179388).  
  
> [!NOTE]
>  Bu bölüm için de geçerlidir. <xref:System.Windows.Controls.Frame> kullandığından, Denetim <xref:System.Windows.Controls.WebBrowser> HTML içeriğini gidin.  
  
 WPF <xref:System.Windows.Controls.WebBrowser> denetimi güvenilmeyen Web içeriğini barındırmak için kullanılır, uygulamanızı kısmi güven kullanmalısınız <xref:System.AppDomain> uygulama kodunuz içinden kötü amaçlı olabilecek HTML kodu verenlerden yardımcı olmak için. Bu, uygulamanızın barındırılan komut dosyasını kullanarak etkileşim, özellikle doğrudur <xref:System.Windows.Controls.WebBrowser.InvokeScript%2A> yöntemi ve <xref:System.Windows.Controls.WebBrowser.ObjectForScripting%2A> özelliği. Daha fazla bilgi için [WPF eklentileri genel bakış](../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md).  
  
 Uygulamanız bir WPF kullanıyorsa <xref:System.Windows.Controls.WebBrowser> denetimi, güvenliği artırmak ve saldırıları azaltmak için başka bir yolu ise Internet Explorer özellik denetimleri etkinleştirmek için. Özellik denetimleri olan Internet Explorer'ın Internet Explorer WebBrowser ActiveX denetimi barındıran uygulamalar ve özellikleri yapılandırmak, Yöneticiler ve geliştiriciler izin eklemeler, WPF <xref:System.Windows.Controls.WebBrowser> denetim sarar. Özellik denetimleri kullanarak yapılandırılabilir [CoInternetSetFeatureEnabled](https://go.microsoft.com/fwlink/?LinkId=179394) işlevi veya kayıt defteri değerlerini değiştirerek. Özellik denetimleri hakkında daha fazla bilgi için bkz: [özellik denetimleri için giriş](https://go.microsoft.com/fwlink/?LinkId=179390) ve [Internet özellik denetimleri](https://go.microsoft.com/fwlink/?LinkId=179392).  
  
 WPF kullanan tek başına bir WPF uygulaması geliştiriyorsanız, <xref:System.Windows.Controls.WebBrowser> denetimi, WPF, uygulamanız için aşağıdaki özellik denetimleri otomatik olarak etkinleştirir.  
  
|Özellik denetimi|  
|---------------------|  
|FEATURE_MIME_HANDLING|  
|FEATURE_MIME_SNIFFING|  
|FEATURE_OBJECT_CACHING|  
|FEATURE_SAFE_BINDTOOBJECT|  
|FEATURE_WINDOW_RESTRICTIONS|  
|FEATURE_ZONE_ELEVATION|  
|FEATURE_RESTRICT_FILEDOWNLOAD|  
|FEATURE_RESTRICT_ACTIVEXINSTALL|  
|FEATURE_ADDON_MANAGEMENT|  
|FEATURE_HTTP_USERNAME_PASSWORD_DISABLE|  
|FEATURE_SECURITYBAND|  
|FEATURE_UNC_SAVEDFILECHECK|  
|FEATURE_VALIDATE_NAVIGATE_URL|  
|FEATURE_DISABLE_TELNET_PROTOCOL|  
|FEATURE_WEBOC_POPUPMANAGEMENT|  
|FEATURE_DISABLE_LEGACY_COMPRESSION|  
|FEATURE_SSLUX|  
  
 Bu özellik denetimler koşulsuz olarak etkin olduğundan, bunları tarafından tam güvenilir uygulamanızı engellenmiş. Belirli bir uygulamayı ve onu barındıran içeriği için herhangi bir güvenlik riski varsa, bu durumda, karşılık gelen özellik denetim devre dışı bırakılabilir.  
  
 Özellik denetimleri WebBrowser ActiveX nesnesini örnekleme işlemi tarafından uygulanır. Güvenilmeyen içerik gidebilirsiniz tek başına bir uygulama oluşturuyorsanız, bu nedenle, ciddi ek özellik denetimleri etkinleştirmek isteyebilirsiniz.  
  
> [!NOTE]
>  Bu öneri MSHTML ve SHDOCVW konak güvenlik için genel öneriler temel alır. Daha fazla bilgi için [MSHTML konak güvenlik SSS: Bölüm ı II](https://go.microsoft.com/fwlink/?LinkId=179396) ve [MSHTML konak güvenlik SSS: Bölüm II, II](https://go.microsoft.com/fwlink/?LinkId=179415).  
  
 Yürütülebilir dosya için aşağıdaki özellik denetimleri kayıt defteri değerini 1 olarak ayarlayarak etkinleştirmeyi düşünün.  
  
|Özellik denetimi|  
|---------------------|  
|FEATURE_ACTIVEX_REPURPOSEDETECTION|  
|FEATURE_BLOCK_LMZ_IMG|  
|FEATURE_BLOCK_LMZ_OBJECT|  
|FEATURE_BLOCK_LMZ_SCRIPT|  
|FEATURE_RESTRICT_RES_TO_LMZ|  
|FEATURE_RESTRICT_ABOUT_PROTOCOL_IE7|  
|FEATURE_SHOW_APP_PROTOCOL_WARN_DIALOG|  
|FEATURE_LOCALMACHINE_LOCKDOWN|  
|FEATURE_FORCE_ADDR_AND_STATUS|  
|FEATURE_RESTRICTED_ZONE_WHEN_FILE_NOT_FOUND|  
  
 Yürütülebilir dosya için kayıt defteri değerini 0 olarak ayarlayarak özellik denetimini devre dışı bırakmayı düşünün.  
  
|Özellik denetimi|  
|---------------------|  
|FEATURE_ENABLE_SCRIPT_PASTE_URLACTION_IF_PROMPT|  
  
 Kısmi güven çalıştırırsanız [!INCLUDE[TLA#tla_xbap](../../../includes/tlasharptla-xbap-md.md)] içeren bir WPF <xref:System.Windows.Controls.WebBrowser> denetim [!INCLUDE[TLA#tla_iegeneric](../../../includes/tlasharptla-iegeneric-md.md)], WPF, Internet Explorer işlemin adres alanında WebBrowser ActiveX denetimini barındırır. WebBrowser ActiveX denetimi içinde barındırıldığından [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)] işlem, tüm Internet Explorer için özellik denetimleri de etkin WebBrowser ActiveX denetimi.  
  
 Internet Explorer'da de çalışmasını XBAP'ler ek bir karşılaştırma normal tek başına uygulamalar için güvenlik düzeyi alın. Bu ek güvenlik olduğundan, Internet Explorer ve bu nedenle WebBrowser ActiveX denetimi çalıştığı için korumalı modu varsayılan olarak [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] ve [!INCLUDE[win7](../../../includes/win7-md.md)]. Korumalı mod hakkında daha fazla bilgi için bkz: [anlama ve korumalı modda Internet Explorer'ın çalışma](https://go.microsoft.com/fwlink/?LinkId=179393).  
  
> [!NOTE]
>  Bir WPF içeren bir XBAP çalıştırmayı denerseniz <xref:System.Windows.Controls.WebBrowser> Internet bölgesi,'de Firefox denetiminde bir <xref:System.Security.SecurityException> oluşturulur. WPF güvenlik ilkesi nedeniyle budur.  
  
<a name="APTCA"></a>   
## <a name="disabling-aptca-assemblies-for-partially-trusted-client-applications"></a>APTCA derlemelerini kısmen güvenilen istemci uygulamaları için devre dışı bırakma  
 Ne zaman Yönetilen derlemeler yüklenir [!INCLUDE[TLA#tla_gac](../../../includes/tlasharptla-gac-md.md)], kullanıcı bunları yüklemek için açık izin sağlaması gerektiğinden, bunlar tam olarak güvenilen olur. Bunlar tam güvenilir olduğundan, yalnızca tam olarak güvenilen yönetilen istemci uygulamaları bunları kullanabilir. Kısmen güvenilen uygulamalara bunları kullanabilmeleri izin vermek için bunlar ile işaretlenmelidir <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA). Kısmi güvende yürütme için güvenli olarak test derlemeleri, bu özniteliği ile işaretlenmiş.  
  
 Ancak, bir güvenlik açığı uygulamasına yüklendikten sonra sergilemesini APTCA derlemesi mümkündür [!INCLUDE[TLA2#tla_gac](../../../includes/tla2sharptla-gac-md.md)]. Bir güvenlik açığı bulununca derleme yayımcılar mevcut yüklemelerinde sorunu gidermek için bir güvenlik güncelleştirmesi oluşturabilir ve sonra bu sorun oluşabilir yüklemelerine karşı korumak için bulunan. Derleme kullanan diğer tam olarak güvenilen istemci uygulamaları, kesilebilir olsa da bir güncelleştirme için derlemeyi kaldırmak için seçenektir.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] tarafından APTCA derlemesi devre dışı bırakılabilir kısmen güvenilen için bir mekanizma sağlar [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)] APTCA derlemesi kaldırma olmadan.  
  
 APTCA derlemesi devre dışı bırakmak için bir özel kayıt defteri anahtarı oluşturmanız gerekir:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\<AssemblyFullName>, FileVersion=<AssemblyFileVersion>`  
  
 Aşağıda bir örnek gösterilmektedir:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\aptcagac, Version=1.0.0.0, Culture=neutral, PublicKeyToken=215e3ac809a0fea7, FileVersion=1.0.0.0`  
  
 Bu anahtar APTCA derlemesi için bir giriş oluşturur. Ayrıca, bir değer sağlar veya derlemeyi devre dışı bırakır. Bu anahtar oluşturmak gerekir. Değerin ayrıntıları aşağıda verilmiştir:  
  
-   Değer adı: **APTCA_FLAG**.  
  
-   Değer türü: **REG_DWORD**.  
  
-   Değer verisi: **1** devre dışı bırakmak için; **0** etkinleştirmek için.  
  
 Bir derlemeyi kısmen güvenilen istemci uygulamaları için devre dışı bırakılması varsa, kayıt defteri anahtarı ve değeri oluşturan bir güncelleştirme yazabilirsiniz.  
  
> [!NOTE]
>  Temel .NET Framework derlemeleri çalıştırmak yönetilen uygulamalar için gerekli olduğundan bunları bu şekilde devre dışı bırakarak etkilenmez. APTCA derlemelerini devre dışı bırakmak için destek, üçüncü taraf uygulamaları için öncelikle hedef alır.  
  
<a name="LooseContentSandboxing"></a>   
## <a name="sandbox-behavior-for-loose-xaml-files"></a>Gevşek XAML dosyaları için sandbox davranışı  
 Gevşek [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] tüm arka plan kod, olay işleyicisi veya uygulamaya özel derleme bağımlı olmadan yalnızca XAML dosyaları dosyalarıdır. Ne zaman kaybetmiş [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] dosyaları geçtiğiniz için doğrudan tarayıcıdan, bunlar varsayılan Internet bölgesi izin kümesi temel alınarak bir güvenlik korumalı alanı içinde yüklenir.  
  
 Ancak güvenlik farklı gevşek, davranıştır [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] dosyaları geçtiğiniz için'nden ya da bir <xref:System.Windows.Navigation.NavigationWindow> veya <xref:System.Windows.Controls.Frame> bir tek başına uygulamadaki.  
  
 Her iki durumda da gevşek [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] için çıkıldığında dosya, kendi ana bilgisayar uygulaması izinlerini devralır. Ancak, bu davranışı istenmeyen güvenlik açısından bakıldığında, özellikle boştaki durumunda olabilir [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] dosya güvenilir değil veya bilinmeyen bir varlık tarafından üretilen. Bu tür içeriği olarak da bilinen *dış içerik*, her ikisi <xref:System.Windows.Controls.Frame> ve <xref:System.Windows.Navigation.NavigationWindow> için çıkıldığında sırasında yalıtmak için yapılandırılabilir. Yalıtım ayarlayarak gerçekleştirilir **SandboxExternalContent** özelliğini ilişkin aşağıdaki örneklerde gösterildiği gibi true olarak <xref:System.Windows.Controls.Frame> ve <xref:System.Windows.Navigation.NavigationWindow>:  
  
 [!code-xaml[SecurityOverviewSnippets#FrameMARKUP](../../../samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window2.xaml#framemarkup)]  
  
 [!code-xaml[SecurityOverviewSnippets#NavigationWindowMARKUP](../../../samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window1.xaml#navigationwindowmarkup)]  
  
 Bu ayar, dış içerik uygulamayı barındıran işleminden ayrı bir işlem içine yüklenir. Bu işlem, etkili bir şekilde barındırma uygulaması ve istemci bilgisayar yalıtma varsayılan Internet bölgesi izin kümesi sınırlıdır.  
  
> [!NOTE]
>  Olsa da gevşek gitme [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] dosyaları ya da bir <xref:System.Windows.Navigation.NavigationWindow> veya <xref:System.Windows.Controls.Frame> bir tek başına uygulama uygulanır PresentationHost işlem içeren, altyapı barındıran WPF tarayıcı üzerinde güvenlik düzeyini dayalıdır biraz daha küçüktür içerik üzerinde doğrudan Internet Explorer'da ne zaman yüklendi [!INCLUDE[wiprlhext](../../../includes/wiprlhext-md.md)] ve [!INCLUDE[win7](../../../includes/win7-md.md)] (hala olacak PresentationHost). Bir Web tarayıcısı kullanarak tek başına bir WPF uygulaması, Internet Explorer'ın ek korumalı mod güvenlik özelliği sağlamaz olmasıdır.  
  
<a name="BestPractices"></a>   
## <a name="resources-for-developing-wpf-applications-that-promote-security"></a>Güvenlik Yükselt WPF uygulamaları geliştirme kaynakları  
 Geliştirmenize yardımcı olacak bazı ek kaynaklar verilmiştir [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] güvenlik Yükselt uygulamalar:  
  
|Alan|Kaynak|  
|----------|--------------|  
|Yönetilen kod|[Desenler ve uygulamalar için uygulamalar güvenlik kılavuzu](https://go.microsoft.com/fwlink/?LinkId=117426)|  
|[!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)]|[Kod erişimi güvenliği](../../../docs/framework/misc/code-access-security.md)|  
|[!INCLUDE[TLA2#tla_clickonce](../../../includes/tla2sharptla-clickonce-md.md)]|[ClickOnce Güvenliği ve Dağıtımı](/visualstudio/deployment/clickonce-security-and-deployment)|  
|[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]|[WPF Kısmi Güven Güvenliği](../../../docs/framework/wpf/wpf-partial-trust-security.md)|  
  
## <a name="see-also"></a>Ayrıca bkz.
- [WPF Kısmi Güven Güvenliği](../../../docs/framework/wpf/wpf-partial-trust-security.md)
- [WPF Güvenlik Stratejisi - Platform Güvenliği](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)
- [WPF Güvenlik Stratejisi - Güvenlik Mühendisliği](../../../docs/framework/wpf/wpf-security-strategy-security-engineering.md)
- [Desenler ve uygulamalar için uygulamalar güvenlik kılavuzu](https://go.microsoft.com/fwlink/?LinkId=117426)
- [Kod erişimi güvenliği](../../../docs/framework/misc/code-access-security.md)
- [ClickOnce Güvenliği ve Dağıtımı](/visualstudio/deployment/clickonce-security-and-deployment)
- [XAML'ye Genel Bakış (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
