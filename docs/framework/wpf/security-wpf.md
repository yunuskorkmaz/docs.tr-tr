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
ms.openlocfilehash: 019035247b1316eb236b025d4527c42bb6ef526c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962816"
---
# <a name="security-wpf"></a>Güvenlik (WPF)
<a name="introduction"></a>Windows Presentation Foundation (WPF) tek başına ve tarayıcıda barındırılan uygulamalar geliştirirken güvenlik modelini göz önünde bulundurmanız gerekir. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]tek başına uygulamalar, Windows Installer (. msi), XCopy veya ClickOnce kullanılarak dağıtılıp dağıtılmayacağı Kısıtlanmamış izinlerle (CAS**FullTrust** izin kümesi) yürütülür. ClickOnce ile kısmi güven dağıtma, tek başına WPF uygulamaları desteklenmez. Ancak, bir tam güven ana bilgisayar uygulaması .NET Framework eklentisi modelini kullanarak kısmi güven <xref:System.AppDomain> oluşturabilir. Daha fazla bilgi için bkz. [WPF Eklentilerine Genel Bakış](./app-development/wpf-add-ins-overview.md).  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]tarayıcıda barındırılan uygulamalar Windows Internet Explorer veya Firefox tarafından barındırılır ve daha fazla bilgi için ya da [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)] gevşek [!INCLUDE[TLA#tla_xaml](../../../includes/tlasharptla-xaml-md.md)] belgeler olabilir, bkz. [WPF XAML tarayıcı uygulamalarına genel bakış](./app-development/wpf-xaml-browser-applications-overview.md).  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]tarayıcıda barındırılan uygulamalar, varsayılan olarak varsayılan CA**Internet** bölgesi izin kümesiyle sınırlanan kısmi güven güvenlik alanı içinde yürütülür. Bu, tarayıcıda [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] barındırılan uygulamaları istemci bilgisayardan, normal web uygulamalarının yalıtılmasını bekleeceğiniz şekilde ayırır. Bir XBAP, dağıtım URL 'sinin güvenlik bölgesine ve istemcinin güvenlik yapılandırmasına bağlı olarak, ayrıcalıkları tam güvenle yükseltebilir. Daha fazla bilgi için bkz. [WPF Kısmi güven güvenliği](wpf-partial-trust-security.md).  
  
 Bu konuda Windows Presentation Foundation (WPF) tek başına ve tarayıcıda barındırılan uygulamalar için güvenlik modeli ele alınmaktadır.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
- [Güvenli gezinti](#SafeTopLevelNavigation)  
  
- [Web 'e göz atma yazılım güvenlik ayarları](#InternetExplorerSecuritySettings)  
  
- [WebBrowser denetimi ve özellik denetimleri](#webbrowser_control_and_feature_controls)  
  
- [Kısmen güvenilen Istemci uygulamaları için APTCA derlemelerini devre dışı bırakma](#APTCA)  
  
- [Gevşek XAML dosyaları için korumalı alan davranışı](#LooseContentSandboxing)  
  
- [Güvenliği geliştiren WPF uygulamaları geliştirmeye yönelik kaynaklar](#BestPractices)  
  
<a name="SafeTopLevelNavigation"></a>   
## <a name="safe-navigation"></a>Güvenli gezinti  
 İçin [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)] ,[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] iki gezinti türünü ayırır: uygulama ve tarayıcı.  
  
 *Uygulama gezintisi* , bir tarayıcı tarafından barındırılan bir uygulama içindeki içerik öğeleri arasında gezinmektedir. *Tarayıcı gezintisi* , tarayıcının içerik ve konum URL 'sini değiştiren gezinidir. Uygulama Gezintisi (genellikle XAML) ve tarayıcı Gezintisi (genellikle HTML) arasındaki ilişki aşağıdaki çizimde gösterilmiştir:
  
 ![Uygulama gezintisi ve tarayıcı gezintisi arasındaki ilişki.](./media/security-wpf/application-browser-navigation-relationship.png)  
  
 İçin güvenli [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] olarak kabul edilen içeriğin türü öncelikle uygulama gezintisi veya tarayıcı gezinmesinin kullanılıp kullanılmadığını belirler.  
  
<a name="Application_Navigation_Security"></a>   
### <a name="application-navigation-security"></a>Uygulama gezintisi güvenliği  
 Dört tür içeriği destekleyen bir paketle [!INCLUDE[TLA2#tla_uri](../../../includes/tla2sharptla-uri-md.md)]tanımlanabildiğinde uygulama gezintisi güvenli olarak değerlendirilir:  
  
|İçerik Türü|Açıklama|URI örneği|  
|------------------|-----------------|-----------------|  
|Kaynak|**Kaynak**yapı türüne sahip bir projeye eklenen dosyalar.|`pack://application:,,,/MyResourceFile.xaml`|  
|İçerik|**İçerik**yapı türü olan bir projeye eklenen dosyalar.|`pack://application:,,,/MyContentFile.xaml`|  
|Kaynak site|Derleme türü **none**olan bir projeye eklenen dosyalar.|`pack://siteoforigin:,,,/MySiteOfOriginFile.xaml`|  
|Uygulama kodu|Derlenmiş bir arka plan kodu olan XAML Kaynakları.<br /><br /> -veya-<br /><br /> Yapı türü **sayfa**olan bir projeye eklenen XAML dosyaları.|`pack://application:,,,/MyResourceFile``.xaml`|  
  
> [!NOTE]
> Uygulama verileri dosyaları ve paketi [!INCLUDE[TLA2#tla_uri#plural](../../../includes/tla2sharptla-urisharpplural-md.md)]hakkında daha fazla bilgi için bkz. [WPF uygulama kaynağı, içerik ve veri dosyaları](./app-development/wpf-application-resource-content-and-data-files.md).  
  
 Bu içerik türlerinin dosyalarına Kullanıcı veya program aracılığıyla gidilenebilir:  
  
- **Kullanıcı gezintisi**. Kullanıcı bir <xref:System.Windows.Documents.Hyperlink> öğeye tıklayarak gezinir.  
  
- **Programlı gezinti**. Uygulama, örneğin <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType> özelliğini ayarlayarak, kullanıcıyla ilgili olmaksızın gezinir.  
  
<a name="Browser_Navigation_Security"></a>   
### <a name="browser-navigation-security"></a>Tarayıcı gezintisi güvenliği  
 Tarayıcı gezintisi, yalnızca aşağıdaki koşullarda güvenli olarak kabul edilir:  
  
- **Kullanıcı gezintisi**. Kullanıcı, iç içe geçmiş <xref:System.Windows.Documents.Hyperlink> <xref:System.Windows.Controls.Frame>içinde değil, Main <xref:System.Windows.Navigation.NavigationWindow>içinde olan bir öğeye tıklayarak gezinir.  
  
- **Bölge**. Gezinmekte olan içerik Internet veya yerel intranette bulunuyor.  
  
- **Protokol**. Kullanılan protokol **http**, **https**, **File**ya da **mailto**'dir.  
  
 İçeriğe bu koşullara uymayan bir biçimde gitmeye <xref:System.Security.SecurityException> çalışırsa,biroluşturulur.[!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)]  
  
<a name="InternetExplorerSecuritySettings"></a>   
## <a name="web-browsing-software-security-settings"></a>Web 'e göz atma yazılım güvenlik ayarları  
 Bilgisayarınızdaki güvenlik ayarları Web 'e göz atma yazılımının verildiği erişimi tespit edilir. Web 'e göz atma yazılımı, Internet Explorer ve PresentationHost. exe dahil olmak üzere [Winınet](https://go.microsoft.com/fwlink/?LinkId=179379) veya [Urlmon](https://go.microsoft.com/fwlink/?LinkId=179383) API 'leri kullanan herhangi bir uygulama veya bileşeni içerir.  
  
 Internet Explorer, aşağıdakiler de dahil olmak üzere Internet Explorer tarafından veya Internet Explorer 'dan yürütülmesine izin verilen işlevselliği yapılandırabileceğiniz bir mekanizma sağlar:  
  
- .NET Framework bağımlı bileşenler  
  
- ActiveX denetimleri ve eklentileri  
  
- İndirmeler  
  
- Betik Oluşturma  
  
- Kullanıcı kimlik doğrulaması  
  
 Bu şekilde güvenli hale getirilmiş işlevsellik koleksiyonu, **Internet**, **Intranet**, **Güvenilen siteler**ve **Yasak siteler** bölgeleri için her bölgeye göre yapılandırılır. Aşağıdaki adımlarda güvenlik ayarlarınızın nasıl yapılandırılacağı açıklanır:  
  
1. **Denetim Masası**'nı açın.  
  
2. **Ağ ve internet** ' e ve ardından **İnternet seçenekleri**' ne tıklayın.  
  
     Internet Seçenekleri iletişim kutusu görüntülenir.  
  
3. **Güvenlik** sekmesinde, güvenlik ayarlarını yapılandırmak için bölgeyi seçin.  
  
4. **Özel düzey** düğmesine tıklayın.  
  
     **Güvenlik ayarları** iletişim kutusu görünür ve seçili bölgenin güvenlik ayarlarını yapılandırabilirsiniz.  
  
     ![Güvenlik ayarları iletişim kutusunu gösteren ekran görüntüsü.](./media/security-wpf/windows-presentation-foundation-security-settings.png)  
  
> [!NOTE]
> Internet Explorer 'ın Internet Seçenekleri iletişim kutusuna da ulaşabilirsiniz. **Araçlar** ' a ve ardından **Internet seçenekleri**' ne tıklayın.  
  
 Windows Internet Explorer 7 ' den itibaren, özellikle .NET Framework için aşağıdaki güvenlik ayarları dahil edilmiştir:  
  
- **Gevşek XAML**. Internet Explorer 'ın [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] dosyalara erişip erişemeyeceğini denetler. (Etkinleştir, devre dışı bırak ve sor seçenekleri).  
  
- **XAML tarayıcı uygulamaları**. Internet Explorer 'ın gidip çalışmasına [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)]erişip erişemeyeceğini denetler. (Etkinleştir, devre dışı bırak ve sor seçenekleri).  
  
 Varsayılan olarak, bu ayarların hepsi **Internet**, **Yerel intranet**ve **Güvenilen siteler** bölgeleri için etkindir ve **Yasak siteler** bölgesi için devre dışıdır.  
  
<a name="Security_Settings_for_IE6_and_Below"></a>   
### <a name="security-related-wpf-registry-settings"></a>Güvenlikle ilgili WPF kayıt defteri ayarları  
 Internet seçenekleri aracılığıyla kullanılabilen güvenlik ayarlarına ek olarak, bir dizi güvenliğe duyarlı WPF özelliğini seçmeli olarak engellemek için aşağıdaki kayıt defteri değerleri mevcuttur. Değerler aşağıdaki anahtar altında tanımlanmıştır:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\Windows Presentation Foundation\Features`  
  
 Aşağıdaki tabloda, ayarlankullanılabilecek değerler listelenmektedir.  
  
|Değer adı|Değer türü|Değer verisi|  
|----------------|----------------|----------------|  
|Xbapallow|REG_DWORD|1-izin verme; izin verilecek 0.|  
|Gevsexamlallow|REG_DWORD|1-izin verme; izin verilecek 0.|  
|Webbrowserallow|REG_DWORD|1-izin verme; izin verilecek 0.|  
|Mediaaudioallow|REG_DWORD|1-izin verme; izin verilecek 0.|  
|Mediaımageallow|REG_DWORD|1-izin verme; izin verilecek 0.|  
|Mediavideoallow|REG_DWORD|1-izin verme; izin verilecek 0.|  
|ScriptInteropDisallow|REG_DWORD|1-izin verme; izin verilecek 0.|  
  
<a name="webbrowser_control_and_feature_controls"></a>   
## <a name="webbrowser-control-and-feature-controls"></a>WebBrowser denetimi ve özellik denetimleri  
 WPF <xref:System.Windows.Controls.WebBrowser> denetimi Web içeriğini barındırmak için kullanılabilir. WPF <xref:System.Windows.Controls.WebBrowser> denetimi, temel alınan WebBrowser ActiveX denetimini sarmalanmış. WPF, güvenilmeyen Web içeriğini barındırmak için WPF <xref:System.Windows.Controls.WebBrowser> denetimini kullandığınızda uygulamanızın güvenliğini sağlamaya yönelik bazı destek sağlar. Ancak bazı güvenlik özelliklerinin, <xref:System.Windows.Controls.WebBrowser> denetimi kullanan uygulamalar tarafından doğrudan uygulanması gerekir. WebBrowser ActiveX denetimi hakkında daha fazla bilgi için bkz. [WebBrowser denetimi genel bakış ve öğreticiler](https://go.microsoft.com/fwlink/?LinkId=179388).  
  
> [!NOTE]
> Bu bölüm, <xref:System.Windows.Controls.WebBrowser> HTML içeriğine gitmek <xref:System.Windows.Controls.Frame> için öğesini kullandığından denetim için de geçerlidir.  
  
 WPF <xref:System.Windows.Controls.WebBrowser> denetimi güvenilmeyen Web içeriğini barındırmak için kullanılıyorsa, uygulamanız potansiyel olarak kötü amaçlı HTML betik kodundan uygulama kodunuzun korunmasını <xref:System.AppDomain> sağlamak için kısmi güven kullanmalıdır. Bu özellikle, uygulamanız barındırılan betiğe <xref:System.Windows.Controls.WebBrowser.InvokeScript%2A> yöntemi <xref:System.Windows.Controls.WebBrowser.ObjectForScripting%2A> ve özelliğini kullanarak etkileşimde bulunursa geçerlidir. Daha fazla bilgi için bkz. [WPF Eklentilerine Genel Bakış](./app-development/wpf-add-ins-overview.md).  
  
 Uygulamanız WPF <xref:System.Windows.Controls.WebBrowser> denetimini kullanıyorsa, güvenliği artırmanın ve saldırıları hafifletmek için başka bir yol, Internet Explorer Özellik denetimlerini etkinleştirmektir. Özellik denetimleri, yöneticilerin ve geliştiricilerin Internet Explorer 'ın ve WPF <xref:System.Windows.Controls.WebBrowser> denetiminin sarmaladığı WebBrowser ActiveX denetimini barındıran uygulamaların özelliklerini yapılandırmasına izin veren Internet Explorer 'ın eklemeleridir. Özellik denetimleri [CoInternetSetFeatureEnabled](https://go.microsoft.com/fwlink/?LinkId=179394) işlevi kullanılarak veya kayıt defterindeki değerler değiştirilerek yapılandırılabilir. Özellik denetimleri hakkında daha fazla bilgi için bkz. [özellik denetimlerine giriş](https://go.microsoft.com/fwlink/?LinkId=179390) ve [Internet Özellik denetimleri](https://go.microsoft.com/fwlink/?LinkId=179392).  
  
 WPF <xref:System.Windows.Controls.WebBrowser> denetimini kullanan tek başına bir WPF uygulaması geliştiriyorsanız, WPF, uygulamanız için aşağıdaki özellik denetimlerini otomatik olarak etkinleştirilir.  
  
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
  
 Bu özellik denetimleri koşullu olarak etkinleştirildiğinden, tam güven uygulaması onlar tarafından zayıflatılabilir. Bu durumda, belirli bir uygulama ve barındırdığı içerik için bir güvenlik riski yoksa, ilgili özellik denetimi devre dışı bırakılabilir.  
  
 Özellik denetimleri, WebBrowser ActiveX nesnesini örnekleyerek işlem tarafından uygulanır. Bu nedenle, güvenilmeyen içeriğe gidebileceğiniz tek başına bir uygulama oluşturuyorsanız, ek özellik denetimlerini etkinleştirmeyi ciddi bir şekilde dikkate almanız gerekir.  
  
> [!NOTE]
> Bu öneri, MSHTML ve SHDOCVW ana bilgisayar güvenliği için genel önerilere dayanır. Daha fazla bilgi için bkz [. MSHTML ana bilgisayar güvenlik SSS: II](https://go.microsoft.com/fwlink/?LinkId=179396) ve[Mshtml ana bilgisayar güvenlik SSS bölümü: II](https://go.microsoft.com/fwlink/?LinkId=179415)'ın Bölüm II.  
  
 Yürütülebilir dosya için, kayıt defteri değerini 1 olarak ayarlayarak aşağıdaki özellik denetimlerini etkinleştirmeyi düşünün.  
  
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
  
 Yürütülebilir dosya için, kayıt defteri değerini 0 olarak ayarlayarak aşağıdaki Özellik denetimini devre dışı bırakmayı göz önünde bulundurun.  
  
|Özellik denetimi|  
|---------------------|  
|FEATURE_ENABLE_SCRIPT_PASTE_URLACTION_IF_PROMPT|  
  
 Windows Internet Explorer 'da WPF [!INCLUDE[TLA#tla_xbap](../../../includes/tlasharptla-xbap-md.md)] <xref:System.Windows.Controls.WebBrowser> denetimi içeren bir kısmi güven çalıştırırsanız WPF, Internet Explorer işleminin adres alanındaki WebBrowser ActiveX denetimini barındırır. WebBrowser ActiveX denetimi Internet Explorer işleminde barındırıldığından, Internet Explorer 'ın tüm özellik denetimleri de WebBrowser ActiveX denetimi için etkinleştirilmiştir.  
  
 Internet Explorer 'da çalışan XBAP 'ler, normal tek başına uygulamalara kıyasla ek bir güvenlik düzeyi de alır. Bu ek güvenlik, Internet Explorer 'ın ve dolayısıyla WebBrowser ActiveX denetiminin, [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] ve [!INCLUDE[win7](../../../includes/win7-md.md)]' de varsayılan olarak korumalı modda çalıştığı bir çalışmadır. Korumalı mod hakkında daha fazla bilgi için bkz. [korumalı modda anlama ve Internet Explorer 'Da çalışma](https://go.microsoft.com/fwlink/?LinkId=179393).  
  
> [!NOTE]
> Firefox 'ta WPF <xref:System.Windows.Controls.WebBrowser> denetimi içeren bir XBAP çalıştırmayı denerseniz, Internet bölgesinde bir <xref:System.Security.SecurityException> oluşturulur. Bunun nedeni WPF Güvenlik ilkesidir.  
  
<a name="APTCA"></a>   
## <a name="disabling-aptca-assemblies-for-partially-trusted-client-applications"></a>Kısmen güvenilen Istemci uygulamaları için APTCA derlemelerini devre dışı bırakma  
 Yönetilen derlemeler genel derleme önbelleği 'ne (GAC) yüklendiğinde, kullanıcının bunları yüklemek için açık izin sağlaması gerektiğinden, bunlar tamamen güvenilir hale gelir. Tam güvenilir oldukları için, yalnızca tam olarak güvenilen yönetilen istemci uygulamaları kullanabilir. Kısmen güvenilen uygulamaların bunları kullanmasına izin vermek için, <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (aptca) ile işaretlenmeleri gerekir. Yalnızca kısmi güvende yürütme için güvenli olarak test edilmiş derlemeler Bu öznitelikle işaretlenmelidir.  
  
 Ancak, bir APTCA derlemesinin GAC 'ye yüklendikten sonra bir güvenlik kusuru göstermesi mümkündür. Bir güvenlik kusurunu bulduktan sonra, derleme yayımcıları mevcut kurulumlarda sorunu gidermek ve sorun keşfedildiğinde oluşabilecek yüklemelere karşı korumak için bir güvenlik güncelleştirmesi oluşturabilir. Güncelleştirme için bir seçenek derlemeyi kaldırmakla birlikte, derlemeyi kullanan diğer tam güvenilir istemci uygulamaları da kesintiye uğramayabilir.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]APTCA derlemesini kaldırmadan kısmen güvenilir [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)] için bir aptca derlemesinin devre dışı bırakılabileceği bir mekanizma sağlar.  
  
 Bir APTCA derlemesini devre dışı bırakmak için özel bir kayıt defteri anahtarı oluşturmanız gerekir:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\<AssemblyFullName>, FileVersion=<AssemblyFileVersion>`  
  
 Aşağıda bir örnek gösterilmektedir:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\aptcagac, Version=1.0.0.0, Culture=neutral, PublicKeyToken=215e3ac809a0fea7, FileVersion=1.0.0.0`  
  
 Bu anahtar, APTCA derlemesi için bir giriş oluşturur. Ayrıca, bu anahtarda derlemeyi sağlayan veya devre dışı bırakan bir değer oluşturmanız gerekir. Aşağıda değerin ayrıntıları verilmiştir:  
  
- Değer adı: **APTCA_FLAG**.  
  
- Değer türü: **REG_DWORD**.  
  
- Değer verisi: devre dışı bırakmak için **1** ; etkinleştirmek için **0** .  
  
 Kısmen güvenilen istemci uygulamaları için bir derlemenin devre dışı bırakılması gerekiyorsa, kayıt defteri anahtarını ve değerini oluşturan bir güncelleştirme yazabilirsiniz.  
  
> [!NOTE]
> Temel .NET Framework derlemeleri, yönetilen uygulamaların çalışması için gerekli olduklarından, bu şekilde devre dışı bırakılarak etkilenmez. APTCA derlemelerini devre dışı bırakma desteği öncelikle üçüncü taraf uygulamalara yöneliktir.  
  
<a name="LooseContentSandboxing"></a>   
## <a name="sandbox-behavior-for-loose-xaml-files"></a>Gevşek XAML dosyaları için korumalı alan davranışı  
 Gevşek [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] dosyalar, herhangi bir kod, olay işleyicisine veya uygulamaya özgü derlemeye bağlı olmayan yalnızca biçimlendirme XAML dosyalarıdır. Gevşek [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] dosyalar doğrudan tarayıcıdan gezindiği zaman, varsayılan Internet bölgesi izin kümesine göre bir güvenlik korumalı alana yüklenir.  
  
 Ancak, gevşek [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] dosyalar tek başına bir <xref:System.Windows.Navigation.NavigationWindow> uygulamadaki veya <xref:System.Windows.Controls.Frame> arasında gezilebilir olduğunda güvenlik davranışı farklıdır.  
  
 Her iki durumda da gezinmiş [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] olan gevşek dosya, ana bilgisayar uygulamasının izinlerini devralır. Ancak, özellikle de güvenilir olmayan veya bilinmeyen bir varlık tarafından gevşek [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] bir dosya üretilirse, bu davranış bir güvenlik perspektifinden istenmeyen bir durum olabilir. Bu içerik türü, *dış içerik*olarak bilinir ve her ikisi de <xref:System.Windows.Controls.Frame> <xref:System.Windows.Navigation.NavigationWindow> ile gezindiğinde yalıtmak üzere yapılandırılabilir. Yalıtım, ve <xref:System.Windows.Controls.Frame> <xref:System.Windows.Navigation.NavigationWindow>için aşağıdaki örneklerde gösterildiği gibi **SandboxExternalContent** özelliği true olarak ayarlanarak elde edilir:  
  
 [!code-xaml[SecurityOverviewSnippets#FrameMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window2.xaml#framemarkup)]  
  
 [!code-xaml[SecurityOverviewSnippets#NavigationWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window1.xaml#navigationwindowmarkup)]  
  
 Bu ayarla, dış içerik, uygulamayı barındıran işlemden ayrı bir işleme yüklenir. Bu işlem, varsayılan Internet bölgesi izin kümesiyle kısıtlıdır ve bu, barındırma uygulamasından ve istemci bilgisayardan etkin bir şekilde yalımalıdır.  
  
> [!NOTE]
> Tek başına bir <xref:System.Windows.Navigation.NavigationWindow> uygulamadaki veya [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] <xref:System.Windows.Controls.Frame> bağımsız bir uygulamadaki gevşek dosyalara yönelik gezinmede, PresentationHost işlemini kapsayan, güvenlik düzeyi ise içerik üzerinde doğrudan Internet Explorer 'a [!INCLUDE[wiprlhext](../../../includes/wiprlhext-md.md)] yüklenen ve [!INCLUDE[win7](../../../includes/win7-md.md)] (PresentationHost aracılığıyla olmaya devam eden) biraz daha küçüktür. Bunun nedeni, bir Web tarayıcısı kullanan tek başına bir WPF uygulamasının Internet Explorer 'ın ek korumalı mod güvenliği özelliği sağlamasıdır.  
  
<a name="BestPractices"></a>   
## <a name="resources-for-developing-wpf-applications-that-promote-security"></a>Güvenliği geliştiren WPF uygulamaları geliştirmeye yönelik kaynaklar  
 Güvenliği geliştiren uygulamalar geliştirmeye [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] yardımcı olmak için bazı ek kaynaklar aşağıda verilmiştir:  
  
|Alan|Kaynak|  
|----------|--------------|  
|Yönetilen kod|[Uygulamalar için modeller ve uygulamalar güvenlik kılavuzu](https://go.microsoft.com/fwlink/?LinkId=117426)|  
|CAS|[Kod erişim güvenliği](../misc/code-access-security.md)|  
|ClickOnce|[ClickOnce Güvenliği ve Dağıtımı](/visualstudio/deployment/clickonce-security-and-deployment)|  
|[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]|[WPF Kısmi Güven Güvenliği](wpf-partial-trust-security.md)|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF Kısmi Güven Güvenliği](wpf-partial-trust-security.md)
- [WPF Güvenlik Stratejisi - Platform Güvenliği](wpf-security-strategy-platform-security.md)
- [WPF Güvenlik Stratejisi - Güvenlik Mühendisliği](wpf-security-strategy-security-engineering.md)
- [Uygulamalar için modeller ve uygulamalar güvenlik kılavuzu](https://go.microsoft.com/fwlink/?LinkId=117426)
- [Kod erişim güvenliği](../misc/code-access-security.md)
- [ClickOnce Güvenliği ve Dağıtımı](/visualstudio/deployment/clickonce-security-and-deployment)
- [XAML'ye Genel Bakış (WPF)](./advanced/xaml-overview-wpf.md)
