---
title: Güvenlik
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
ms.openlocfilehash: e0a56dcbf8d151fcb0d4f6271ecba15c0ff955a4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174621"
---
# <a name="security-wpf"></a>Güvenlik (WPF)
<a name="introduction"></a>Windows Presentation Foundation (WPF) bağımsız ve tarayıcı tarafından barındırılan uygulamaları geliştirirken, güvenlik modelini göz önünde bulundurmanız gerekir. WPF bağımsız uygulamaları, Windows Installer (.msi), XCopy veya ClickOnce kullanılarak dağıtılıp dağıtılmayacağı sınırsız izinlerle (CAS**FullTrust** izin kümesi) yürütülür. ClickOnce ile kısmi güven, bağımsız WPF uygulamaları nın dağıtılması desteklenmez. Ancak, tam güven ana bilgisayar uygulaması .NET Framework Add-in modelini kullanarak kısmi güven <xref:System.AppDomain> oluşturabilir. Daha fazla bilgi için [WPF Eklentilerine Genel Bakış'a](./app-development/wpf-add-ins-overview.md)bakın.  
  
 WPF tarayıcı tarafından barındırılan uygulamalar Windows Internet Explorer veya Firefox tarafından barındırılan ve xaml tarayıcı uygulamaları (XBAPs) veya gevşek [!INCLUDE[TLA#tla_xaml](../../../includes/tlasharptla-xaml-md.md)] belgeler daha fazla bilgi için, [WPF XAML Tarayıcı Uygulamaları Genel Bakış](./app-development/wpf-xaml-browser-applications-overview.md)bakın olabilir.  
  
 WPF tarayıcı tarafından barındırılan uygulamalar, varsayılan OLARAK CAS**Internet** bölgesi izin kümesiyle sınırlı olan kısmi güven güvenliği sandbox içinde yürütülür. Bu, WPF tarayıcı tarafından barındırılan uygulamaları, tipik Web uygulamalarının yalıtılmış olmasını beklediğiniz şekilde istemci bilgisayardan etkin bir şekilde yalıtır. Bir XBAP, dağıtım URL'sinin güvenlik bölgesine ve istemcinin güvenlik yapılandırmasına bağlı olarak ayrıcalıkları Full Trust'a yükseltebilir. Daha fazla bilgi için [WPF Kısmi Güven Güvenliği'ne](wpf-partial-trust-security.md)bakın.  
  
 Bu konu, Windows Presentation Foundation (WPF) bağımsız ve tarayıcı tarafından barındırılan uygulamalar için güvenlik modelini tartışır.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
- [Güvenli Navigasyon](#SafeTopLevelNavigation)  
  
- [Web Tarama Yazılımı Güvenlik Ayarları](#InternetExplorerSecuritySettings)  
  
- [WebBrowser Kontrol ve Özellik Denetimleri](#webbrowser_control_and_feature_controls)  
  
- [Kısmen Güvenilen İstemci Uygulamaları için APTCA Montajlarının Devre Dışı Bırakılması](#APTCA)  
  
- [Gevşek XAML Dosyaları için Sandbox Davranışı](#LooseContentSandboxing)  
  
- [Güvenliği Teşvik Eden WPF Uygulamaları Geliştirme Kaynakları](#BestPractices)  
  
<a name="SafeTopLevelNavigation"></a>
## <a name="safe-navigation"></a>Güvenli Navigasyon  
 XBAP'lar için WPF iki tür gezinmeyi ayırt eder: uygulama ve tarayıcı.  
  
 *Uygulama* gezintisi, bir tarayıcı tarafından barındırılan bir uygulamadaki içerik öğeleri arasında gezinmedir. *Tarayıcı* gezintisi, bir tarayıcının içeriğini ve konum URL'sini değiştiren gezintidir. Uygulama gezintisi (genellikle XAML) ve tarayıcı gezintisi (genellikle HTML) arasındaki ilişki aşağıdaki resimde gösterilmiştir:
  
 ![Uygulama gezintisi ve tarayıcı gezintisi arasındaki ilişki.](./media/security-wpf/application-browser-navigation-relationship.png)  
  
 Bir XBAP'ın gezinmesi için güvenli kabul edilen içerik türü, öncelikle uygulama gezintisinin veya tarayıcı gezintisinin kullanılıp kullanılmadığına göre belirlenir.  
  
<a name="Application_Navigation_Security"></a>
### <a name="application-navigation-security"></a>Uygulama Navigasyon Güvenliği  
 Uygulama gezintisi, dört tür içeriği destekleyen bir paket URI ile tanımlanabiliyorsa güvenli kabul edilir:  
  
|İçerik Türü|Açıklama|URI Örneği|  
|------------------|-----------------|-----------------|  
|Kaynak|Yapı Türü **Kaynak**olan bir projeye eklenen dosyalar.|`pack://application:,,,/MyResourceFile.xaml`|  
|İçerik|Yapı Türü **İçerik**olan bir projeye eklenen dosyalar.|`pack://application:,,,/MyContentFile.xaml`|  
|Menşe sitesi|Yapı türü **Yok**olan bir projeye eklenen dosyalar.|`pack://siteoforigin:,,,/MySiteOfOriginFile.xaml`|  
|Uygulama kodu|Derlenmiş bir kod arkası olan XAML kaynakları.<br /><br /> -veya-<br /><br /> **Bir projeye sayfa**yapı türüne sahip xaml dosyaları eklendi.|`pack://application:,,,/MyResourceFile` `.xaml`|  
  
> [!NOTE]
> Uygulama veri dosyaları ve paket URL'leri hakkında daha fazla bilgi için [WPF Uygulama Kaynağı, İçerik ve Veri Dosyaları'na](./app-development/wpf-application-resource-content-and-data-files.md)bakın.  
  
 Bu içerik türlerinin dosyaları kullanıcı tarafından veya programlı olarak gezinilebilir:  
  
- **Kullanıcı Navigasyon**. Kullanıcı bir <xref:System.Windows.Documents.Hyperlink> öğeyi tıklatarak gezinir.  
  
- **Programlı Navigasyon**. Uygulama, <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType> örneğin, özelliği ayarlayarak, kullanıcıdahil olmadan gezinir.  
  
<a name="Browser_Navigation_Security"></a>
### <a name="browser-navigation-security"></a>Tarayıcı Navigasyon Güvenliği  
 Tarayıcı gezintisi yalnızca aşağıdaki koşullar altında güvenli olarak kabul edilir:  
  
- **Kullanıcı Navigasyon**. Kullanıcı, iç içe değil, ana <xref:System.Windows.Documents.Hyperlink> <xref:System.Windows.Navigation.NavigationWindow>içinde bulunan bir öğeyi <xref:System.Windows.Controls.Frame>tıklatarak gezinir.  
  
- **Bölge**. Gezinilen içerik Internet'te veya yerel intranette bulunur.  
  
- **Protokol.** Kullanılan protokol ya **http**, **https**, **dosya**, ya da **mailto**.  
  
 Bir XBAP içeriğe bu koşullara uymayan bir şekilde gezinmeye <xref:System.Security.SecurityException> çalışırsa, bir atLanır.  
  
<a name="InternetExplorerSecuritySettings"></a>
## <a name="web-browsing-software-security-settings"></a>Web Tarama Yazılımı Güvenlik Ayarları  
 Bilgisayarınızdaki güvenlik ayarları, herhangi bir Web tarama yazılımının erişilen erişimi belirler. Web tarama yazılımı, Internet Explorer ve PresentationHost.exe dahil olmak üzere [WinINet](/windows/win32/wininet/portal) veya [UrlMon](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa767916(v=vs.85)) API'lerini kullanan herhangi bir uygulama veya bileşen içerir.  
  
 Internet Explorer, aşağıdakiler de dahil olmak üzere Internet Explorer tarafından veya Internet Explorer tarafından yürütülmesine izin verilen işlevselliği yapılandırabileceğiniz bir mekanizma sağlar:  
  
- .NET Çerçeveye dayalı bileşenler  
  
- ActiveX kontrolleri ve eklentileri  
  
- İndirmeler  
  
- Betik Oluşturma  
  
- Kullanıcı Kimlik Doğrulaması  
  
 Bu şekilde güvence altına alınabilen işlevsellik **koleksiyonu, Internet,** **Intranet,** **Trusted Sites**ve **Restricted Sites** bölgeleri için bölge bazında yapılandırılır. Aşağıdaki adımlar, güvenlik ayarlarınızı nasıl yapılandırıştırılayarılanızı açıklar:  
  
1. Açık **Kontrol Paneli**.  
  
2. **Ağ ve Internet'i tıklatın** ve ardından Internet **Seçenekleri'ni**tıklatın.  
  
     Internet Seçenekleri iletişim kutusu görüntülenir.  
  
3. **Güvenlik** sekmesinde, güvenlik ayarlarını yapılandırmak için bölgeyi seçin.  
  
4. Özel **Düzey** düğmesini tıklatın.  
  
     **Güvenlik Ayarları** iletişim kutusu görüntülenir ve seçili bölgenin güvenlik ayarlarını yapılandırabilirsiniz.  
  
     ![Güvenlik Ayarları iletişim kutusunu gösteren ekran görüntüsü.](./media/security-wpf/windows-presentation-foundation-security-settings.png)  
  
> [!NOTE]
> Internet Explorer'dan Internet Seçenekleri iletişim kutusuna da ulaşabilirsiniz. **Araçlar'ı** tıklatın ve ardından **Internet Seçenekleri'ni**tıklatın.  
  
 Windows Internet Explorer 7 ile başlayarak, özellikle .NET Framework için aşağıdaki güvenlik ayarları dahildir:  
  
- **Gevşek XAML**. Internet Explorer'ın dosyalara [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] gidip gidemeyeceğini ve dosyaları serbest bırakabileceğini denetler. (Etkinleştir, Devre Dışı Ve İstem seçeneklerini).  
  
- **XAML tarayıcı uygulamaları**. Internet Explorer'ın XBAP'lara gidip gidemeyeceğini ve çalıştırıp çalıştıramayacağını denetler. (Etkinleştir, Devre Dışı Ve İstem seçeneklerini).  
  
 Varsayılan olarak, bu ayarların tümü **Internet,** **Yerel intranet**ve **Güvenilen siteler** bölgeleri için etkinleştirilir ve **Kısıtlı siteler** bölgesi için devre dışı bırakılır.  
  
<a name="Security_Settings_for_IE6_and_Below"></a>
### <a name="security-related-wpf-registry-settings"></a>Güvenlikle ilgili WPF Kayıt Defteri Ayarları  
 Internet Seçenekleri aracılığıyla kullanılabilen güvenlik ayarlarına ek olarak, güvenliğe duyarlı wpf özelliklerinin bir dizisini seçerek engellemek için aşağıdaki kayıt defteri değerleri kullanılabilir. Değerler aşağıdaki anahtar altında tanımlanır:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\Windows Presentation Foundation\Features`  
  
 Aşağıdaki tabloda ayarlanabilecek değerler listelenecek.  
  
|Değer Adı|Değer Türü|Değer Verileri|  
|----------------|----------------|----------------|  
|XBAPDisallow|REG_DWORD|1 izin vermemek için; 0 izin vermek.|  
|LooseXamlDisallow|REG_DWORD|1 izin vermemek için; 0 izin vermek.|  
|WebBrowserDisallow|REG_DWORD|1 izin vermemek için; 0 izin vermek.|  
|MediaAudioDisallow|REG_DWORD|1 izin vermemek için; 0 izin vermek.|  
|MediaImageDisallow|REG_DWORD|1 izin vermemek için; 0 izin vermek.|  
|MediaVideoDisallow|REG_DWORD|1 izin vermemek için; 0 izin vermek.|  
|ScriptInteropDisallow|REG_DWORD|1 izin vermemek için; 0 izin vermek.|  
  
<a name="webbrowser_control_and_feature_controls"></a>
## <a name="webbrowser-control-and-feature-controls"></a>WebBrowser Kontrol ve Özellik Denetimleri  
 WPF <xref:System.Windows.Controls.WebBrowser> denetimi Web içeriğini barındırmak için kullanılabilir. WPF <xref:System.Windows.Controls.WebBrowser> denetimi, temel WebBrowser ActiveX denetimini sarar. WPF, wpf <xref:System.Windows.Controls.WebBrowser> denetimini güvenilmeyen Web içeriğini barındırmak için kullandığınızda uygulamanızı güvence altına almak için bazı destek sağlar. Ancak, bazı güvenlik özellikleri <xref:System.Windows.Controls.WebBrowser> denetimi kullanarak uygulamalar tarafından doğrudan uygulanmalıdır. WebBrowser ActiveX denetimi hakkında daha fazla bilgi için [WebBrowser Denetimigenel Bakışları ve Eğitimleri'ne](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752041(v=vs.85))bakın.  
  
> [!NOTE]
> Bu bölüm, HTML <xref:System.Windows.Controls.Frame> içeriğine gitmek <xref:System.Windows.Controls.WebBrowser> için kullandığından denetim için de geçerlidir.  
  
 WPF <xref:System.Windows.Controls.WebBrowser> denetimi güvenilmeyen Web içeriğini barındırmak için kullanılıyorsa, uygulamanızın uygulama kodunuzu kötü amaçlı HTML komut dosyası kodundan izole etmeye yardımcı olmak için kısmi bir güven <xref:System.AppDomain> kullanması gerekir. Bu, özellikle uygulamanız metodunu <xref:System.Windows.Controls.WebBrowser.InvokeScript%2A> ve <xref:System.Windows.Controls.WebBrowser.ObjectForScripting%2A> özelliği ni kullanarak barındırılan komut dosyasıyla etkileşim halindeyse geçerlidir. Daha fazla bilgi için [WPF Eklentilerine Genel Bakış'a](./app-development/wpf-add-ins-overview.md)bakın.  
  
 Uygulamanız WPF <xref:System.Windows.Controls.WebBrowser> denetimini kullanıyorsa, güvenliği artırmanın ve saldırıları azaltmanın başka bir yolu Internet Explorer özellik denetimlerini etkinleştirmektir. Özellik denetimleri, yöneticilerin ve geliştiricilerin Internet Explorer özelliklerini yapılandırmasına ve WPF <xref:System.Windows.Controls.WebBrowser> denetiminin kaydırdığı WebBrowser ActiveX denetimini barındıran uygulamaların özelliklerini yapılandırmasına olanak tanıyan Internet Explorer'a eklemelerdir. Özellik denetimleri [CoInternetSetFeatureEnabled](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537168(v=vs.85)) işlevi kullanılarak veya kayıt defterindeki değerleri değiştirerek yapılandırılabilir. [Özellik](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537184(v=vs.85)) denetimleri hakkında daha fazla bilgi için [bkz.](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/general-info/ee330720(v=vs.85))  
  
 WPF <xref:System.Windows.Controls.WebBrowser> denetimini kullanan bağımsız bir WPF uygulaması geliştiriyorsanız, WPF uygulamanız için aşağıdaki özellik denetimlerini otomatik olarak etkinleştirir.  
  
|Özellik Kontrolü|  
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
  
 Bu özellik denetimleri koşulsuz olarak etkinleştirildiğinden, tam güven uygulaması onlar tarafından bozulabilir. Bu durumda, belirli bir uygulama ve barındıran içerik için güvenlik riski yoksa, ilgili özellik denetimi devre dışı bırakılır.  
  
 Özellik denetimleri, WebBrowser ActiveX nesnesini anında sağlayan işlem tarafından uygulanır. Bu nedenle, güvenilmeyen içeriğe gidebilecek tek başına bir uygulama oluşturuyorsanız, ek özellik denetimlerini etkinleştirmeyi ciddi şekilde düşünmelisiniz.  
  
> [!NOTE]
> Bu öneri, MSHTML ve SHDOCVW ana bilgisayar güvenliği için genel önerilere dayanmaktadır. Daha fazla bilgi için, [Bkz. MSHTML Ana Bilgisayar Güvenlik SSS: Bölüm I I](https://msrc-blog.microsoft.com/2009/04/02/the-mshtml-host-security-faq-part-i-of-ii/) ve [MSHTML Ana Bilgisayar Güvenlik SSS: Bölüm II II](https://msrc-blog.microsoft.com/2009/04/03/the-mshtml-host-security-faq-part-ii-of-ii/).  
  
 Çalıştırılabilir liğiniz için, kayıt defteri değerini 1 olarak ayarlayarak aşağıdaki özellik denetimlerini etkinleştirmeyi düşünün.  
  
|Özellik Kontrolü|  
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
  
 Çalıştırılabilir liğiniz için, kayıt defteri değerini 0 olarak ayarlayarak aşağıdaki özellik denetimini devre dışı bırakmayı düşünün.  
  
|Özellik Kontrolü|  
|---------------------|  
|FEATURE_ENABLE_SCRIPT_PASTE_URLACTION_IF_PROMPT|  
  
 Windows Internet Explorer'da WPF <xref:System.Windows.Controls.WebBrowser> denetimi içeren kısmi güven xaml tarayıcı uygulaması (XBAP) çalıştırırsanız, WPF Internet Explorer işleminin adres alanında WebBrowser ActiveX denetimini barındırır. WebBrowser ActiveX denetimi Internet Explorer işleminde barındırılan olduğundan, Internet Explorer için tüm özellik denetimleri de WebBrowser ActiveX denetimi için etkinleştirilir.  
  
 Internet Explorer'da çalışan XBAP'lar, normal bağımsız uygulamalara kıyasla ek bir güvenlik düzeyi de elde eder. Bu ek güvenlik, Internet Explorer'ın ve dolayısıyla WebBrowser ActiveX denetiminin Windows Vista ve Windows 7'de varsayılan olarak korumalı modda çalıştırıştırı. Korumalı mod hakkında daha fazla bilgi için [bkz.](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/)  
  
> [!NOTE]
> Firefox'ta WPF <xref:System.Windows.Controls.WebBrowser> denetimi içeren bir XBAP çalıştırmayı denerseniz, <xref:System.Security.SecurityException> Internet bölgesinde yken bir a atılır. Bunun nedeni WPF güvenlik ilkesidir.  
  
<a name="APTCA"></a>
## <a name="disabling-aptca-assemblies-for-partially-trusted-client-applications"></a>Kısmen Güvenilen İstemci Uygulamaları için APTCA Montajlarının Devre Dışı Bırakılması  
 Yönetilen derlemeler genel derleme önbelleğine (GAC) yüklendiğinde, kullanıcının bunları yüklemek için açık izin vermesi gerektiğinden tam olarak güvenilir. Bunlar tam olarak güvenilen olduğundan, yalnızca tam olarak güvenilen yönetilen istemci uygulamaları bunları kullanabilir. Kısmen güvenilen uygulamaların bunları kullanmasına izin vermek için, bu uygulamaların <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) ile işaretlenmiş olması gerekir. Yalnızca kısmi güven içinde yürütülmesi için güvenli olması için sınanmış derlemeler bu öznitelik ile işaretlenmiş olmalıdır.  
  
 Ancak, bir APTCA derlemesi GAC'ye yüklendikten sonra bir güvenlik kusuru sergilemesi mümkündür. Bir güvenlik kusuru keşfedildikten sonra, derleme yayımcılar varolan yüklemeler üzerindeki sorunu gidermek ve sorun keşfedildikten sonra oluşabilecek yüklemelere karşı korumak için bir güvenlik güncelleştirmesi üretebilir. Güncelleştirme için bir seçenek, derlemeyi kullanan diğer tam güvenilen istemci uygulamalarını bozabilir, ancak derlemeyi kaldırmaktır.  
  
 WPF, APTCA derlemesini kaldırmadan kısmen güvenilen XBA'lar için bir APTCA derlemesinin devre dışı açılabilir bir mekanizma sağlar.  
  
 Bir APTCA derlemesini devre dışı kılabilirse, özel bir kayıt defteri anahtarı oluşturmanız gerekir:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\<AssemblyFullName>, FileVersion=<AssemblyFileVersion>`  
  
 Aşağıdaki bir örnek gösterilmektedir:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\aptcagac, Version=1.0.0.0, Culture=neutral, PublicKeyToken=215e3ac809a0fea7, FileVersion=1.0.0.0`  
  
 Bu anahtar, APTCA derlemesi için bir giriş belirler. Ayrıca, bu anahtarda derlemeyi etkinleştiren veya devre dışı düşüren bir değer oluşturmanız gerekir. Değerin ayrıntıları şunlardır:  
  
- Değer Adı: **APTCA_FLAG**.  
  
- Değer Türü: **REG_DWORD**.  
  
- Değer Verileri: **1** devre dışı kalmak için; **0** etkinleştirmek için.  
  
 Kısmen güvenilen istemci uygulamaları için bir derlemenin devre dışı edilmesi gerekiyorsa, kayıt defteri anahtarını ve değerini oluşturan bir güncelleştirme yazabilirsiniz.  
  
> [!NOTE]
> Çekirdek .NET Framework derlemeleri, yönetilen uygulamaların çalışması için gerekli olduğundan, bu şekilde devre dışı bırakılmaz. APTCA derlemelerinin devre dışı bırakılması için destek öncelikle üçüncü taraf uygulamaları hedeflenir.  
  
<a name="LooseContentSandboxing"></a>
## <a name="sandbox-behavior-for-loose-xaml-files"></a>Gevşek XAML Dosyaları için Sandbox Davranışı  
 Gevşek [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] dosyalar, herhangi bir kod arkası, olay işleyicisi veya uygulamaya özgü derlemeye bağlı olmayan yalnızca biçimlendirmeye dayalı XAML dosyalarıdır. Gevşek [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] dosyalar doğrudan tarayıcıdan yönlendirildiğinde, varsayılan Internet bölgesi izin kümesine göre bir güvenlik sandbox'ına yüklenirler.  
  
 Ancak, gevşek [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] dosyalar a <xref:System.Windows.Navigation.NavigationWindow> veya <xref:System.Windows.Controls.Frame> bağımsız bir uygulamada gezinildiğinde güvenlik davranışı farklıdır.  
  
 Her iki durumda [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] da, ana bilgisayar uygulamasının izinlerini devralmak üzere gezinilen gevşek dosya. Ancak, bu davranış, özellikle gevşek [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] bir dosya güvenilmeyen veya bilinmeyen bir varlık tarafından üretilmişse, güvenlik açısından istenmeyen olabilir. Bu tür içerik *dış içerik*olarak <xref:System.Windows.Controls.Frame> bilinir <xref:System.Windows.Navigation.NavigationWindow> ve her ikisi de ve gezinildiğinde onu yalıtmak için yapılandırılabilir. İzolasyon, Aşağıdaki örneklerde gösterildiği **gibi, SandboxExternalContent** özelliğini doğru olarak ayarlayarak elde <xref:System.Windows.Controls.Frame> edilir: <xref:System.Windows.Navigation.NavigationWindow>  
  
 [!code-xaml[SecurityOverviewSnippets#FrameMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window2.xaml#framemarkup)]  
  
 [!code-xaml[SecurityOverviewSnippets#NavigationWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window1.xaml#navigationwindowmarkup)]  
  
 Bu ayar ile, dış içerik uygulamayı barındıran işlemden ayrı bir işleme yüklenir. Bu işlem, barındırma uygulamasından ve istemci bilgisayardan etkin bir şekilde yalıtarak varsayılan Internet bölgesi izin kümesiyle sınırlıdır.  
  
> [!NOTE]
> <xref:System.Windows.Navigation.NavigationWindow> Bir <xref:System.Windows.Controls.Frame> veya bağımsız [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] bir uygulamadan gevşek dosyalara gezinme PresentationHost işlemini içeren WPF tarayıcı barındırma altyapısına dayalı olarak uygulansa da, güvenlik düzeyi içeriğin Doğrudan Windows Vista ve Windows 7'deki Internet Explorer'a yüklendiğinden biraz daha azdır (hala PresentationHost aracılığıyla olacaktır). Bunun nedeni, Web tarayıcısı kullanan bağımsız bir WPF uygulamasının Internet Explorer'ın ek Korumalı Modu güvenlik özelliğini sağlamamasıdır.  
  
<a name="BestPractices"></a>
## <a name="resources-for-developing-wpf-applications-that-promote-security"></a>Güvenliği Teşvik Eden WPF Uygulamaları Geliştirme Kaynakları  
 Güvenliği teşvik eden WPF uygulamaları geliştirmeye yardımcı olacak bazı ek kaynaklar şunlardır:  
  
|Alan|Kaynak|  
|----------|--------------|  
|Yönetilen kod|[Uygulamalar için Örüntü ler ve Uygulamalar Güvenlik Rehberi](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))|  
|CAS|[Kod Erişimi Güvenliği](../misc/code-access-security.md)|  
|ClickOnce|[ClickOnce Güvenliği ve Dağıtımı](/visualstudio/deployment/clickonce-security-and-deployment)|  
|WPF|[WPF Kısmi Güven Güvenliği](wpf-partial-trust-security.md)|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF Kısmi Güven Güvenliği](wpf-partial-trust-security.md)
- [WPF Güvenlik Stratejisi - Platform Güvenliği](wpf-security-strategy-platform-security.md)
- [WPF Güvenlik Stratejisi - Güvenlik Mühendisliği](wpf-security-strategy-security-engineering.md)
- [Uygulamalar için Örüntü ler ve Uygulamalar Güvenlik Rehberi](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))
- [Kod Erişimi Güvenliği](../misc/code-access-security.md)
- [ClickOnce Güvenliği ve Dağıtımı](/visualstudio/deployment/clickonce-security-and-deployment)
- [XAML'ye Genel Bakış (WPF)](../../desktop-wpf/fundamentals/xaml.md)
