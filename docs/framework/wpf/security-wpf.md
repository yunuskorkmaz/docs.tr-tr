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
ms.openlocfilehash: 7b58368539ed1e41c1367e0cd1da7e4181a8af7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565931"
---
# <a name="security-wpf"></a>Güvenlik (WPF)
<a name="introduction"></a> Windows Presentation Foundation (WPF) tek başına ve tarayıcıda barındırılan uygulamalar geliştirirken, güvenlik modeli dikkate almanız gerekir. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] tek başına uygulamalarını yürütmek Kısıtlanmamış izinlerle ( [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] **FullTrust** izin kümesi), Windows Installer (.msi), XCopy, kullanılarak dağıtılan olup olmadığını veya [!INCLUDE[TLA2#tla_clickonce](../../../includes/tla2sharptla-clickonce-md.md)]. Kısmi güven, tek başına WPF uygulamaları ClickOnce ile dağıtma desteklenmiyor. Ancak, bir tam güven ana bilgisayar uygulaması kısmi güven oluşturabilirsiniz <xref:System.AppDomain> kullanarak .NET Framework eklenti modeli. Daha fazla bilgi için bkz: [WPF eklentileri genel bakış](../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md).  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] tarayıcıda barındırılan uygulamalar tarafından barındırılan [!INCLUDE[TLA#tla_iegeneric](../../../includes/tlasharptla-iegeneric-md.md)] ya da Firefox ve ya da olabilir [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)] veya gevşek [!INCLUDE[TLA#tla_xaml](../../../includes/tlasharptla-xaml-md.md)] belgeler hakkında daha fazla bilgi için bkz: [WPF XAML tarayıcısı uygulamaları genel bakış](../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md).  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] tarayıcıda barındırılan uygulamalar için varsayılan sınırlıdır varsayılan olarak kısmi güven güvenlik sandbox içinde yürütme [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] **Internet** bölge izin kümesi. Bu etkili bir şekilde yalıtır [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] yalıtılması normal Web uygulamaları beklediğiniz şekilde istemci bilgisayardan tarayıcıda barındırılan uygulamalar. Bir XBAP ayrıcalıkları, tam güven kadar dağıtım URL'si ve istemcinin güvenlik yapılandırması güvenlik bölgesi bağlı olarak yükseltebilirsiniz. Daha fazla bilgi için bkz: [WPF kısmi güven güvenlik](../../../docs/framework/wpf/wpf-partial-trust-security.md).  
  
 Bu konu Windows Presentation Foundation (WPF) tek başına ve tarayıcıda barındırılan uygulamalar için güvenlik modeli açıklanır.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
-   [Güvenli gezinme](#SafeTopLevelNavigation)  
  
-   [Web gözatma yazılım güvenlik ayarları](#InternetExplorerSecuritySettings)  
  
-   [WebBrowser denetimi ve özellik denetimleri](#webbrowser_control_and_feature_controls)  
  
-   [Kısmen güvenilen istemci uygulamaları için APTCA derlemeleri devre dışı bırakma](#APTCA)  
  
-   [Gevşek XAML dosyaları için korumalı alan davranışı](#LooseContentSandboxing)  
  
-   [Güvenlik Yükselt WPF uygulamaları geliştirmek için kaynaklar](#BestPractices)  
  
<a name="SafeTopLevelNavigation"></a>   
## <a name="safe-navigation"></a>Güvenli gezinme  
 İçin [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)], [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] Gezinti iki tür ayırt: uygulama ve tarayıcı.  
  
 *Uygulama gezinti* tarayıcı tarafından barındırılan bir uygulamadaki içerik öğeleri arasında gezinme değil. *Tarayıcı Gezinti* bir tarayıcı içeriği ve konum URL'sini değiştirir Gezinti bölmesinde bulunuyor. Uygulama gezinti (genellikle XAML) ve tarayıcı gezinme (genel olarak HTML) arasındaki ilişki aşağıda gösterilmiştir:
  
 ![Gezinti diyagramı](../../../docs/framework/wpf/media/safetoplevelnavigationfigure.png "SafeTopLevelNavigationFigure")  
  
 İçin güvenli olarak kabul edilen içerik türünü bir [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] gitmek için öncelikle uygulamayı tarayıcı Gezinti veya kullanılıp kullanılmadığını tarafından belirlenir.  
  
<a name="Application_Navigation_Security"></a>   
### <a name="application-navigation-security"></a>Uygulama gezinti güvenliği  
 Uygulama gezinti sahip bir paketi belirlediyseniz, güvenli kabul [!INCLUDE[TLA2#tla_uri](../../../includes/tla2sharptla-uri-md.md)], dört içerik türlerini destekler:  
  
|İçerik türü|Açıklama|URI örneği|  
|------------------|-----------------|-----------------|  
|Kaynak|Bir yapı türüne sahip bir projeye eklenen dosyalar **kaynak**.|`pack://application:,,,/MyResourceFile.xaml`|  
|İçerik|Bir yapı türüne sahip bir projeye eklenen dosyalar **içerik**.|`pack://application:,,,/MyContentFile.xaml`|  
|Kaynak site|Bir yapı türüne sahip bir projeye eklenen dosyalar **hiçbiri**.|`pack://siteoforigin:,,,/MySiteOfOriginFile.xaml`|  
|Uygulama kodu|Bir derlenmiş arka plan kod sahip XAML kaynaklar.<br /><br /> -veya-<br /><br /> Bir yapı türüne sahip bir projeye eklenen XAML dosyaları **sayfa**.|`pack://application:,,,/MyResourceFile``.xaml`|  
  
> [!NOTE]
>  Uygulama verileri dosyaları ve paketi hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uri#plural](../../../includes/tla2sharptla-urisharpplural-md.md)], bkz: [WPF Uygulama kaynağı, içerik ve veri dosyalarını](../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md).  
  
 İçerik bu tür dosyalar için ya da kullanıcı tarafından veya program aracılığıyla gittiğinizde:  
  
-   **Kullanıcı Gezinti**. Kullanıcı tıklayarak gider bir <xref:System.Windows.Documents.Hyperlink> öğesi.  
  
-   **Programlı Gezinti**. Bu gibi bir durumda kullanıcı ayarlayarak karıştırılmaksızın uygulama gider <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType> özelliği.  
  
<a name="Browser_Navigation_Security"></a>   
### <a name="browser-navigation-security"></a>Tarayıcı gezinti güvenliği  
 Tarayıcı Gezinti yalnızca aşağıdaki koşullar altında güvenli olarak kabul edilir:  
  
-   **Kullanıcı Gezinti**. Kullanıcı tıklayarak gider bir <xref:System.Windows.Documents.Hyperlink> ana içinde olan öğeyi <xref:System.Windows.Navigation.NavigationWindow>değil içinde iç içe bir <xref:System.Windows.Controls.Frame>.  
  
-   **Bölge**. İçin ilk içeriği, Internet veya yerel intranet üzerindeki bulunur.  
  
-   **Protokol**. Kullanılan protokol olan **http**, **https**, **dosya**, veya **mailto**.  
  
 Varsa bir [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] Bu koşullar ile uyumlu değil bir şekilde içeriği gitmek çalışır bir <xref:System.Security.SecurityException> oluşturulur.  
  
<a name="InternetExplorerSecuritySettings"></a>   
## <a name="web-browsing-software-security-settings"></a>Web gözatma yazılım güvenlik ayarları  
 Güvenlik ayarları, bilgisayarınızdaki tüm Web yazılım taraması verilen erişim belirler. Web yazılım taraması içeren herhangi bir uygulama veya kullandığı bileşenin [WinINet](http://go.microsoft.com/fwlink/?LinkId=179379) veya [UrlMon](http://go.microsoft.com/fwlink/?LinkId=179383) API'leri, Internet Explorer ve PresentationHost.exe dahil olmak üzere.  
  
 [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)] göre ya da çalıştırılmasına izin işlevselliği, yapılandırabileceğiniz bir mekanizma sağlar [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)], aşağıdakiler dahil:  
  
-   .NET framework bağımlı bileşenler  
  
-   ActiveX denetimleri ve eklentiler  
  
-   İndirmeler  
  
-   Betik Oluşturma  
  
-   Kullanıcı kimlik doğrulaması  
  
 Bu şekilde güvenli hale getirilebilir işlevselliği koleksiyonu için bir bölge başına temelinde yapılandırılır **Internet**, **Intranet**, **Güvenilen siteler**, ve  **Yasak siteler** bölgeleri. Aşağıdaki adımlar, güvenlik ayarlarının nasıl yapılandırılacağı açıklamaktadır:  
  
1.  Açık **Denetim Masası**.  
  
2.  Tıklatın **ağ ve Internet** ve ardından **Internet Seçenekleri**.  
  
     Internet Seçenekleri iletişim kutusu görüntülenir.  
  
3.  Üzerinde **güvenlik** sekmesinde, güvenlik ayarlarını yapılandırmak için bölge seçin.  
  
4.  Tıklatın **Özel düzey** düğmesi.  
  
     **Güvenlik ayarları** iletişim kutusu belirir ve seçilen bölge için güvenlik ayarlarını yapılandırabilirsiniz.  
  
     ![Güvenlik Ayarları iletişim kutusu](../../../docs/framework/wpf/media/wpfsecurityfigure1.PNG "WPFSecurityFigure1")  
  
> [!NOTE]
>  Ayrıca, Internet Seçenekleri iletişim kutusu için Internet Explorer'dan alabilirsiniz. Tıklatın **Araçları** ve ardından **Internet Seçenekleri**.  
  
 İle başlayarak [!INCLUDE[TLA#tla_ie7](../../../includes/tlasharptla-ie7-md.md)], özellikle .NET Framework için aşağıdaki güvenlik ayarları eklenmiştir:  
  
-   **Esnek XAML'i**. Denetimleri olup olmadığını [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)] gidin ve kaybetmiş [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] dosyaları. (Etkinleştir, devre dışı bırakın ve seçenekleri ister).  
  
-   **XAML tarayıcısı uygulamaları**. Denetimleri olup olmadığını [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)] gidin ve Çalıştır [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)]. (Etkinleştir, devre dışı bırakın ve seçenekleri ister).  
  
 Varsayılan olarak, bu ayarlar tüm için etkinleştirilen **Internet**, **yerel intranet**, ve **Güvenilen siteler** bölgeleri ve devre dışı **Kısıtlanmış siteler**  bölgesi.  
  
<a name="Security_Settings_for_IE6_and_Below"></a>   
### <a name="security-related-wpf-registry-settings"></a>WPF güvenlikle ilgili kayıt defteri ayarları  
 Internet seçenekleri kullanılabilir güvenlik ayarlarına ek seçmeli olarak çok sayıda güvenlik açısından duyarlı WPF özelliği engellemek için aşağıdaki kayıt defteri değerlerini kullanılabilir. Değerleri aşağıdaki anahtarı altında tanımlanmıştır:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\Windows Presentation Foundation\Features`  
  
 Aşağıdaki tabloda ayarlanabilir değerleri listeler.  
  
|Değer adı|Değer türü|Değer verisi|  
|----------------|----------------|----------------|  
|XBAPDisallow|REG_DWORD|izin vermeyecek şekilde 1; izin vermek için 0'ı tıklatın.|  
|LooseXamlDisallow|REG_DWORD|izin vermeyecek şekilde 1; izin vermek için 0'ı tıklatın.|  
|WebBrowserDisallow|REG_DWORD|izin vermeyecek şekilde 1; izin vermek için 0'ı tıklatın.|  
|MediaAudioDisallow|REG_DWORD|izin vermeyecek şekilde 1; izin vermek için 0'ı tıklatın.|  
|MediaImageDisallow|REG_DWORD|izin vermeyecek şekilde 1; izin vermek için 0'ı tıklatın.|  
|MediaVideoDisallow|REG_DWORD|izin vermeyecek şekilde 1; izin vermek için 0'ı tıklatın.|  
|ScriptInteropDisallow|REG_DWORD|izin vermeyecek şekilde 1; izin vermek için 0'ı tıklatın.|  
  
<a name="webbrowser_control_and_feature_controls"></a>   
## <a name="webbrowser-control-and-feature-controls"></a>WebBrowser denetimi ve özellik denetimleri  
 WPF <xref:System.Windows.Controls.WebBrowser> denetimi, Web içeriğini barındırmak için kullanılabilir. WPF <xref:System.Windows.Controls.WebBrowser> denetim temel WebBrowser ActiveX denetimi sarmalar. WPF WPF kullandığınızda, uygulamanızın güvenliğini sağlamak için bazı destek sağlar <xref:System.Windows.Controls.WebBrowser> barındırmak için güvenilmeyen Web içeriği. Ancak, bazı güvenlik özellikleri kullanarak uygulamalar tarafından doğrudan uygulanmalıdır <xref:System.Windows.Controls.WebBrowser> denetim. WebBrowser ActiveX denetimi hakkında daha fazla bilgi için bkz: [WebBrowser denetimine genel bakış ve öğreticiler](http://go.microsoft.com/fwlink/?LinkId=179388).  
  
> [!NOTE]
>  Bu bölüm için de geçerlidir. <xref:System.Windows.Controls.Frame> onu kullandığından kontrol <xref:System.Windows.Controls.WebBrowser> HTML içeriğini gidin.  
  
 Varsa WPF <xref:System.Windows.Controls.WebBrowser> denetimi güvenilmeyen Web içeriğini barındırmak için kullanılır, uygulamanızın kısmi güven kullanması gereken <xref:System.AppDomain> uygulama kodunuzdan zararlı HTML komut dosyası kodu verenlerden yardımcı olacak. Bu, uygulamanızın kullanarak barındırılan komut dosyası ile etkileşim, özellikle doğrudur <xref:System.Windows.Controls.WebBrowser.InvokeScript%2A> yöntemi ve <xref:System.Windows.Controls.WebBrowser.ObjectForScripting%2A> özelliği. Daha fazla bilgi için bkz: [WPF eklentileri genel bakış](../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md).  
  
 Uygulamanız WPF kullanıyorsa <xref:System.Windows.Controls.WebBrowser> denetim, güvenliği artırmak ve saldırıları azaltmak için başka bir yoldur Internet Explorer özellik denetimleri etkinleştirmek için. Özellik denetimleridir Internet Explorer'ın Yöneticiler ve geliştiriciler Internet Explorer ve WebBrowser ActiveX denetimini barındırmasına uygulamaların özelliklerini yapılandırmak izin eklemeler, WPF <xref:System.Windows.Controls.WebBrowser> kontrol sarar. Özellik denetimleri kullanarak yapılandırılabilir [CoInternetSetFeatureEnabled](http://go.microsoft.com/fwlink/?LinkId=179394) işlevi veya kayıt defteri değerlerini değiştirerek. Özellik denetimleri hakkında daha fazla bilgi için bkz: [özelliği denetimlerine giriş](http://go.microsoft.com/fwlink/?LinkId=179390) ve [Internet özellik denetimleri](http://go.microsoft.com/fwlink/?LinkId=179392).  
  
 WPF kullanan bir tek başına WPF uygulaması geliştirme varsa <xref:System.Windows.Controls.WebBrowser> denetimi, WPF uygulamanız için aşağıdaki özellik denetimleri otomatik olarak etkinleştirir.  
  
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
  
 Bu özellik denetimlerinin koşulsuz olarak etkinleştirilmiş olduğundan, bunlar tam güven uygulama engellenmiş. Belirli bir uygulamayı ve onu barındıran içerik için herhangi bir güvenlik riski varsa, bu durumda, karşılık gelen özellik denetimi devre dışı bırakılabilir.  
  
 Özellik denetimleri WebBrowser ActiveX nesnesi örneği işlem tarafından uygulanır. Güvenilmeyen içeriği gidebilirsiniz tek başına bir uygulama oluşturuyorsanız, bu nedenle, ciddi ek özellik denetimleri etkinleştirmek isteyebilirsiniz.  
  
> [!NOTE]
>  Bu öneri, ana bilgisayar güvenlik MSHTML ve SHDOCVW yönelik genel öneriler dayanır. Daha fazla bilgi için bkz: [MSHTML ana bilgisayar güvenlik ile ilgili SSS: bölümü ı II,](http://go.microsoft.com/fwlink/?LinkId=179396) ve [MSHTML ana bilgisayar güvenlik ile ilgili SSS: Bölüm II II,](http://go.microsoft.com/fwlink/?LinkId=179415).  
  
 Yürütülebilir dosyası için kayıt defteri değerini 1 olarak ayarlayarak aşağıdaki özellik denetimleri etkinleştirmeyi düşünün.  
  
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
  
 Yürütülebilir dosyası için aşağıdaki özellik denetimi kayıt defteri değerini 0 olarak ayarlayarak devre dışı bırakmayı düşünün.  
  
|Özellik denetimi|  
|---------------------|  
|FEATURE_ENABLE_SCRIPT_PASTE_URLACTION_IF_PROMPT|  
  
 Kısmi güven çalıştırırsanız [!INCLUDE[TLA#tla_xbap](../../../includes/tlasharptla-xbap-md.md)] bir WPF içeren <xref:System.Windows.Controls.WebBrowser> denetim [!INCLUDE[TLA#tla_iegeneric](../../../includes/tlasharptla-iegeneric-md.md)], WPF barındıran Internet Explorer işlemi adres alanındaki WebBrowser ActiveX denetimi. WebBrowser ActiveX denetimi içinde barındırılan beri [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)] işlem, tüm Internet Explorer için özellik denetimleri de etkindir WebBrowser ActiveX denetimi için.  
  
 Internet Explorer'da de çalışıyor XBAP ek bir karşılaştırıldığında normal bağımsız uygulamalar için güvenlik düzeyi alın. Internet Explorer ve bu nedenle WebBrowser ActiveX denetimi çalıştığı için korumalı bu ek güvenliği, varsayılan olarak modu [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] ve [!INCLUDE[win7](../../../includes/win7-md.md)]. Korumalı modu hakkında daha fazla bilgi için bkz: [anlama ve korumalı mod Internet Explorer'da çalışma](http://go.microsoft.com/fwlink/?LinkId=179393).  
  
> [!NOTE]
>  Bir WPF içeren bir XBAP çalıştırmayı deneyin <xref:System.Windows.Controls.WebBrowser> Internet bölgesinde, Firefox denetiminde bir <xref:System.Security.SecurityException> oluşturulur. WPF güvenlik ilkesi nedeniyle budur.  
  
<a name="APTCA"></a>   
## <a name="disabling-aptca-assemblies-for-partially-trusted-client-applications"></a>Kısmen güvenilen istemci uygulamaları için APTCA derlemeleri devre dışı bırakma  
 Yönetilen derlemeler yüklü olduğunda içine [!INCLUDE[TLA#tla_gac](../../../includes/tlasharptla-gac-md.md)], kullanıcı onları yüklemek için açık izin sağlamanız gerekir çünkü tam olarak güvenilmeyen olduklarında. Tam güvenilir olduklarından, yalnızca tam güvenilir yönetilen istemci uygulamaları bunları kullanabilir. Kısmen güvenilir uygulamalar bunları kullanmaya izin vermek için bunlar ile işaretlenmelidir <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA). Bu öznitelik ile kısmi güvende yürütme için güvenli olması için test derlemeleri işaretlenmelidir.  
  
 Ancak, bir APTCA derleme uygulamasına yüklendikten sonra bir güvenlik açığı sergilemesine mümkündür [!INCLUDE[TLA2#tla_gac](../../../includes/tla2sharptla-gac-md.md)]. Bir güvenlik açığı bulunduktan sonra derleme yayımcılar mevcut yüklemelerinde sorunu gidermek için bir güvenlik güncelleştirmesi oluşturabilir ve sonra bu sorun oluşabilir yüklemelere karşı korumak için bulunan. Derleme kullanan diğer tam olarak güvenilmeyen istemci uygulamaları değiştirmiş olabilir ancak bir güncelleştirme için derlemesini kaldırmak için seçenektir.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] tarafından APTCA derlemeyi devre dışı bırakılabilir kısmen güvenilir bir mekanizma sağlar [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)] APTCA derleme kaldırma olmadan.  
  
 APTCA derlemeyi devre dışı bırakmak için özel kayıt defteri anahtarı oluşturmanız gerekir:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\<AssemblyFullName>, FileVersion=<AssemblyFileVersion>`  
  
 Bir örnek gösterilmektedir:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\aptcagac, Version=1.0.0.0, Culture=neutral, PublicKeyToken=215e3ac809a0fea7, FileVersion=1.0.0.0`  
  
 Bu anahtar APTCA derleme için bir giriş oluşturur. Ayrıca bir değer etkinleştirir ya da derlemeyi devre dışı bırakır Bu anahtar oluşturmanız gerekir. Değerin ayrıntıları verilmiştir:  
  
-   Değer adı: **APTCA_FLAG**.  
  
-   Değer türü: **REG_DWORD**.  
  
-   Değer verisi: **1** devre dışı bırakmak için; **0** etkinleştirmek için.  
  
 Bir derlemeyi kısmen güvenilen istemci uygulamalar için devre dışı bırakılması varsa, kayıt defteri anahtarı ve değeri oluşturan bir güncelleştirme yazabilirsiniz.  
  
> [!NOTE]
>  Çekirdek .NET Framework derlemeler için yönetilen uygulamaları çalıştırmak gerekli olduğundan bunları bu şekilde devre dışı bırakarak etkilenmez. APTCA derlemeleri devre dışı bırakmak için destek, üçüncü taraf uygulamaları için öncelikle yöneliktir.  
  
<a name="LooseContentSandboxing"></a>   
## <a name="sandbox-behavior-for-loose-xaml-files"></a>Gevşek XAML dosyaları için korumalı alan davranışı  
 Gevşek [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] tüm arka plan kodu, olay işleyicisi veya uygulamaya özgü derleme dayanmayan yalnızca biçimlendirme XAML dosyaları dosyalarıdır. Ne zaman kaybetmiş [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] dosyaları gittiğinizde için doğrudan tarayıcıdan, varsayılan Internet bölgesi izin kümesini temel alan bir güvenlik korumalı alanı içinde yüklü.  
  
 Ancak, güvenlik davranış gevşek zaman farklıdır [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] dosyaları gittiğinizde için herhangi birinden bir <xref:System.Windows.Navigation.NavigationWindow> veya <xref:System.Windows.Controls.Frame> bir tek başına uygulamasında.  
  
 Her iki durumda da gevşek [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] için gittiğinizde dosya kendi ana uygulaması izinlerini devralır. Ancak, bu davranış istenmeyen güvenlik açısından bakıldığında, özellikle gevşek varsa olabilir [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] dosya güvenilir değil veya bilinmeyen bir varlık tarafından üretilen. Bu tür içeriği olarak bilinen *dış içeriği*, her ikisi <xref:System.Windows.Controls.Frame> ve <xref:System.Windows.Navigation.NavigationWindow> için gittiğinizde sırasında yalıtmak için yapılandırılabilir. Yalıtım ayarlayarak elde edilir **SandboxExternalContent** özelliğini ilişkin aşağıdaki örneklerde gösterildiği gibi true olarak <xref:System.Windows.Controls.Frame> ve <xref:System.Windows.Navigation.NavigationWindow>:  
  
 [!code-xaml[SecurityOverviewSnippets#FrameMARKUP](../../../samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window2.xaml#framemarkup)]  
  
 [!code-xaml[SecurityOverviewSnippets#NavigationWindowMARKUP](../../../samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window1.xaml#navigationwindowmarkup)]  
  
 Bu ayar, dış içeriği uygulamasını barındıran işleminden ayrı bir işlemin içine yüklenir. Bu işlem etkin barındırma uygulama ile istemci bilgisayar yalıtma varsayılan Internet bölgesi izin kümesi sınırlıdır.  
  
> [!NOTE]
>  Olsa bile gezinme gevşek [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] ya da dosyalarından bir <xref:System.Windows.Navigation.NavigationWindow> veya <xref:System.Windows.Controls.Frame> tek başına uygulama uygulanır PresentationHost işlem içeren altyapı, barındırma WPF tarayıcısında dayalıdır güvenlik düzeyi biraz daha az içerik üzerinde doğrudan Internet Explorer'da ne zaman yüklendi [!INCLUDE[wiprlhext](../../../includes/wiprlhext-md.md)] ve [!INCLUDE[win7](../../../includes/win7-md.md)] (hala olacak PresentationHost). Bu durum, bir Web tarayıcısı kullanarak tek başına WPF uygulaması Internet Explorer'ın ek korumalı mod güvenlik özelliği sağlamaz çünkü.  
  
<a name="BestPractices"></a>   
## <a name="resources-for-developing-wpf-applications-that-promote-security"></a>Güvenlik Yükselt WPF uygulamaları geliştirmek için kaynaklar  
 Geliştirmeye yardımcı olmak için bazı ek kaynaklar verilmiştir [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] güvenlik Yükselt uygulamalar:  
  
|Alan|Kaynak|  
|----------|--------------|  
|Yönetilen kod|[Desenleri ve uygulamalar için yöntemler Güvenlik Kılavuzu](http://go.microsoft.com/fwlink/?LinkId=117426)|  
|[!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)]|[Kod erişimi güvenliği](../../../docs/framework/misc/code-access-security.md)|  
|[!INCLUDE[TLA2#tla_clickonce](../../../includes/tla2sharptla-clickonce-md.md)]|[ClickOnce Güvenliği ve Dağıtımı](/visualstudio/deployment/clickonce-security-and-deployment)|  
|[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]|[WPF Kısmi Güven Güvenliği](../../../docs/framework/wpf/wpf-partial-trust-security.md)|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF Kısmi Güven Güvenliği](../../../docs/framework/wpf/wpf-partial-trust-security.md)  
 [WPF Güvenlik Stratejisi - Platform Güvenliği](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)  
 [WPF Güvenlik Stratejisi - Güvenlik Mühendisliği](../../../docs/framework/wpf/wpf-security-strategy-security-engineering.md)  
 [Desenleri ve uygulamalar için yöntemler Güvenlik Kılavuzu](http://go.microsoft.com/fwlink/?LinkId=117426)  
 [Kod erişimi güvenliği](../../../docs/framework/misc/code-access-security.md)  
 [ClickOnce Güvenliği ve Dağıtımı](/visualstudio/deployment/clickonce-security-and-deployment)  
 [XAML'ye Genel Bakış (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
