---
title: "WPF Uygulaması Oluşturma (WPF)"
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
helpviewer_keywords: WPF application [WPF], building
ms.assetid: a58696fd-bdad-4b55-9759-136dfdf8b91c
caps.latest.revision: "45"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1e8773b0b99e6394dcc3675b21f4a9454444b617
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="building-a-wpf-application-wpf"></a>WPF Uygulaması Oluşturma (WPF)
[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]uygulamalar, olarak oluşturulabilen [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] yürütülebilir dosyalar (.exe) kitaplıkları (.dll) veya her iki tür derlemeleri birleşimi. Bu konu nasıl oluşturulacağını tanıtır [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamaları ve derleme işlemindeki anahtar adımları açıklar.  
  
  
<a name="Building_a_WPF_Application_using_Command_Line"></a>   
## <a name="building-a-wpf-application"></a>WPF Uygulaması Oluşturma  
 WPF uygulaması aşağıdaki yollarla derlenebilir:  
  
-   Komut satırı. Uygulama, yalnızca kod (XAML yok) ve uygulama tanımı dosyası içermesi gerekir. Daha fazla bilgi için bkz: [komut satırı yapı ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) veya [(Visual Basic) komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md).  
  
-   Microsoft Build Engine (MSBuild). Kod ve XAML dosyaları ek olarak, uygulamanın bir MSBuild proje dosyası içermesi gerekir. Daha fazla bilgi için "MSBuild" konusuna bakın.  
  
-   Visual Studio. Visual Studio WPF MSBuild uygulamalarla derler ve kullanıcı Arabirimi oluşturma için görsel tasarımcı içeren bir tümleşik geliştirme ortamıdır. Daha fazla bilgi için bkz: [Visual Studio'da uygulama geliştirme](http://msdn.microsoft.com/en-us/97490c1b-a247-41fb-8f2c-bc4c201eff68) ve [WPF Tasarımcısı](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26).  
  
<a name="The_Windows_Presentation_Foundation_Build_Pipeline"></a>   
## <a name="wpf-build-pipeline"></a>WPF yapı ardışık düzen  
 Zaman bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] projesi yapılandırıldığında, dile özgü birleşimi ve [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]-belirli hedefler çağrılır. Bu hedefleri yürütme işleminin yapı ardışık düzen adı verilir ve anahtar adımlar aşağıdaki şekilde gösterilmiştir.  
  
 ![WPF yapı işlemi](../../../../docs/framework/wpf/app-development/media/wpfbuildsystem-figure1.png "WPFBuildSystem_Figure1")  
  
<a name="Pre_Build_Initializations"></a>   
### <a name="pre-build-initializations"></a>Derleme öncesi başlatmaları  
 Yapılandırmadan önce [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] önemli araçlar ve kitaplıkları, aşağıdakiler dahil konumunu belirler:  
  
-   [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)].  
  
-   [!INCLUDE[TLA2#tla_wcsdk](../../../../includes/tla2sharptla-wcsdk-md.md)] Dizinleri.  
  
-   Konumunu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] başvuru derlemeleri.  
  
-   Derleme arama yollarının özelliği.  
  
 İlk konum nerede [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] derlemeleri arar olan başvuru derleme dizini (%ProgramFiles%\Reference Assemblies\Microsoft\Framework\v3.0\\). Bu adım sırasında yapı işlemi ayrıca çeşitli özellikler ile öğe gruplarını başlatır ve gerekli temizleme işini gerçekleştirir.  
  
<a name="Resolving_references"></a>   
### <a name="resolving-references"></a>Başvuruları çözme  
 Derleme işlemi bulur ve uygulama projesi oluşturmak için gerekli olan derlemeleri bağlar. Bu mantık yer `ResolveAssemblyReference` görev. Olarak bildirilen tüm derlemeler `Reference` proje dosyasında görev arama yolları hakkında bilgi ve sistemde zaten yüklü derlemeleri meta verileri ile birlikte sağlanır. Görev derlemeleri arar ve bu çekirdek filtrelemek için yüklü derlemenin meta verilerini kullanır [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] gösterme çıkış bildirimleri gereksinim derlemeler. Bu, yedek bilgilerin ClickOnce bildirimlerinde önlemek için yapılır. PresentationFramework.dll temsilcisi kabul edilebilir olduğundan Örneğin, bir uygulama ve yerleşik [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ve dahası tüm bu yana [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] derlemeler var olan her makinede aynı konumda [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] yüklü tüm tüm bilgileri içerecek şekilde gerek yoktur [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] başvuru derlemeleri bildirimlerinde.  
  
<a name="Markup_Compilation___Pass_1"></a>   
### <a name="markup-compilationpass-1"></a>Biçimlendirme derleme — geçiş 1  
 Bu adımda, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyaları ayrıştırılır ve böylece çalışma zamanı ayrıştırma harcamanız değil derlenmiş [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] ve özellik değerlerini doğrulama. Derlenmiş [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya öncesi simgeleştirilmiş çalışma zamanında, yükleme yüklemekten daha hızlı olması gerekir böylece bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyası.  
  
 Bu adım sırasında aşağıdaki etkinliklerin gerçekleşmesi her [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] yani dosya bir `Page` öğesi oluşturun:  
  
1.  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Dosyası biçimlendirme derleyicisi tarafından ayrıştırılır.  
  
2.  Derlenmiş gösterim için oluşturulan [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ve obj\Release klasörüne kopyalanır.  
  
3.  Yeni bir parçalı sınıf CodeDOM gösterimi oluşturulur ve obj\Release klasörüne kopyalanır.  
  
 Dile özgü kod dosyası için ek olarak, oluşturulan her [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya. Örneğin, Page1.xaml sayfası için bir [!INCLUDE[TLA2#tla_visualb](../../../../includes/tla2sharptla-visualb-md.md)] project, bir Page1.g.vb oluşturulur; bir Page1.xaml için sayfa bir [!INCLUDE[TLA2#tla_cshrp](../../../../includes/tla2sharptla-cshrp-md.md)] proje, bir Page1.g.cs oluşturulur. Dosya adı ".g" dosyası oluşturulur gösterir biçimlendirme dosyasının en üst düzey öğesi için bir parçalı sınıf bildirimi sahip code (gibi `Page` veya `Window`). Sınıf ile bildirilmiş `partial` değiştiricisi [!INCLUDE[TLA2#tla_cshrp](../../../../includes/tla2sharptla-cshrp-md.md)] (`Extends` içinde [!INCLUDE[TLA2#tla_visualb](../../../../includes/tla2sharptla-visualb-md.md)]) başka bir sınıf için başka bir bildirim belirtmek için genellikle kod arkasında Page1.xaml.cs dosya.  
  
 Uygun temel sınıfından kısmi sınıfını genişleten (gibi <xref:System.Windows.Controls.Page> bir sayfa için) ve uygulayan <xref:System.Windows.Markup.IComponentConnector?displayProperty=nameWithType> arabirimi. <xref:System.Windows.Markup.IComponentConnector> Arabirimi bileşeni başlatmak ve adları ve içeriği öğelerinde olaylarına bağlanmak için yöntemler vardır. Sonuç olarak, oluşturulan kod dosyası aşağıdakine benzer bir yöntem uygulamasına sahiptir:  
  
```csharp  
public void InitializeComponent() {  
    if (_contentLoaded) {  
        return;  
    }  
    _contentLoaded = true;  
    System.Uri resourceLocater =   
        new System.Uri(  
            "window1.xaml",   
            System.UriKind.RelativeOrAbsolute);  
    System.Windows.Application.LoadComponent(this, resourceLocater);  
}  
```  
  
```vb  
Public Sub InitializeComponent() _  
  
    If _contentLoaded Then  
        Return  
    End If  
  
    _contentLoaded = True  
    Dim resourceLocater As System.Uri = _  
        New System.Uri("mainwindow.xaml", System.UriKind.Relative)  
  
    System.Windows.Application.LoadComponent(Me, resourceLocater)  
  
End Sub  
```  
  
 Varsayılan olarak, biçimlendirmesi derleme aynı şekilde çalışır <xref:System.AppDomain> olarak [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] altyapısı. Bu, önemli ölçüde performans artışı sağlar. Bu davranış ile değiştirilebilir `AlwaysCompileMarkupFilesInSeparateDomain` özelliği. Tüm başvuru derlemeleri ayrı kaldırarak eklentiyi avantajı vardır <xref:System.AppDomain>.  
  
<a name="Pass_2_of_Markup_Compilation"></a>   
### <a name="markup-compilationpass-2"></a>Biçimlendirme derleme — 2 geçirin  
 Tüm [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfaları derlenen adresindeki biçimlendirme derlemesinin 1 geçişi sırasında. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]yerel olarak tanımlanan tür başvuruları (aynı projesi herhangi bir yerde kodda tanımlanan türlere başvurular) dosyaları, şu anda derleme dışındadır. Bu yerel olarak tanımlanmış türleri yalnızca kaynağında var ve henüz derlenmiş olmasıdır. Bunu belirlemek için ayrıştırıcı gibi öğeler için aramayı içeren buluşsal yöntemler kullanır `x:Name` biçimlendirme dosyasında. Bu tür bir örnek bulunduğunda biçimlendirme dosyanın derleme kod dosyaları, daha sonra derlenmiştir kadar ertelenir ikinci biçimlendirme derleme bu dosyaları işlemleri geçişi.  
  
<a name="File_Classification"></a>   
### <a name="file-classification"></a>Dosya Sınıflandırma  
 Derleme işlemi koyar çıktı dosyalarını farklı kaynak grupları, hangi uygulama derlemesine bunlar yerleştirilecek temel. Tüm veri dosyalarının tipik olarak yerelleştirilmemiş uygulamada işaretlenen `Resource` ana derleme (yürütülebilir dosya veya kitaplığa) yerleştirilir. Zaman `UICulture` projede derlenen tüm ayarlandığında [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyaları ve özellikle dile özgü olarak işaretlenmiş kaynakları uydu kaynak derlemesine yerleştirilir. Ayrıca, tüm dilden kaynakları ana derlemede yerleştirilir. Derleme işleminin bu adımında, o belirleme yapılır.  
  
 `ApplicationDefinition`, `Page`, Ve `Resource` proje dosyasında yapı eylemleri ile Genişletilebilir `Localizable` meta veriler (kabul edilebilir değerler `true` ve `false`), dosyanın dile özgü olup olmadığını belirleyen veya dilden.  
  
<a name="Core_Compilation"></a>   
### <a name="core-compilation"></a>Çekirdek derleme  
 Çekirdek derleme adımı kod dosyalarının derlenmesini içerir. Bu, dile özgü hedef dosyaları Microsoft.CSharp.targets ve Microsoft.VisualBasic.targets mantığı tarafından yönetilir. Buluşsal yöntemler belirlediyseniz biçimlendirme derleyici tek bir geçiş yeterlidir, ardından ana derleme oluşturulur. Ancak, bir veya daha fazla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] projedeki dosyaları yerel olarak tanımlanmış tür başvuruları sahiptir ve biçimlendirme derlemesinin ikinci geçişi tamamlandıktan sonra son uygulama derlemesinin oluşturulabilmesi için geçici .dll dosyası oluşturulur.  
  
<a name="Manifest_generation"></a>   
### <a name="manifest-generation"></a>Bildirim üretme  
 Tüm uygulama derlemeleri ve içerik dosyaları hazır olduktan sonra yapı işleminin sonunda [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] bildirimleri uygulama için oluşturulur.  
  
 Dağıtım bildirimi dosyası dağıtım modelini açıklar: geçerli sürüm, güncelleştirme davranışını ve dijital imza birlikte yayımcı kimliği. Bu bildirimi dağıtımı işleyen yöneticiler tarafından yazılmayı amaçlanmıştır. .Xbap dosya uzantısıdır (için [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]) ve yüklü uygulamaları için .application. Önceki tarafından dikte edilir `HostInBrowser` proje özelliği ve sonuç olarak uygulamayı tarayıcıda barındırılan olarak bildirim tanımlar.  
  
 Uygulama bildirimini (bir. exe.manifest dosyası) uygulama derlemeler ile bağımlı kitaplıkları açıklar ve uygulama için gereken izinleri listeler. Bu dosya uygulama geliştiricisi tarafından yazılmayı amaçlanmıştır. Başlatmak için bir [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] uygulama, bir kullanıcı uygulamanın dağıtım bildirim dosyasını açar.  
  
 Bu bildirim dosyaları her zaman için oluşturulan [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]. Yüklü uygulamalar için sürece oluşturulmaz `GenerateManifests` özelliği belirtilen değerle proje dosyasında `true`.  
  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]tipik Internet bölgesi uygulamalarına atanan bu izinleri üzerine iki ek izin alma: <xref:System.Security.Permissions.WebBrowserPermission> ve <xref:System.Security.Permissions.MediaPermission>. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Yapı sistem uygulama bildiriminde bu izinleri bildirir.  
  
<a name="Incremental_Build_Support"></a>   
## <a name="incremental-build-support"></a>Artımlı derleme desteği  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Yapılandırma sistemi artımlı derlemeler için destek sağlar. İşaretleme veya kod yapılan değişiklikleri algılama oldukça mantıklıdır ve yalnızca değişiklikten etkilenen yapıları derler. Artımlı derleme mekanizması aşağıdaki dosyaları kullanır:  
  
-   Bir $(*AssemblyName*) geçerli derleyici durumunu korumak üzere _MarkupCompiler.Cache dosyası.  
  
-   Bir $(*AssemblyName*) _MarkupCompiler.lref dosyayı önbelleğe [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyaları yerel olarak tanımlanmış tür başvuruları.  
  
 Aşağıdaki Artımlı derlemeyi yöneten kurallar kümesidir:  
  
-   Dosya, yapı sistem değişikliği algılar en küçük birimdir. Bu nedenle, bir kod dosyası için bir türü değişirse veya kod eklediyseniz yapı sistem bildiremez. Aynı proje dosyaları için geçerlidir.  
  
-   Artımlı derleme mekanizmasının olması gerekir, bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfa bir sınıfı tanımlar veya diğer sınıfları kullanır.  
  
-   Varsa `Reference` girişleri değiştirmek ve tüm sayfaları yeniden derleyin.  
  
-   Bir kod dosyası değişirse, yerel olarak tanımlanmış tür başvuruları içeren tüm sayfaları yeniden derleyin.  
  
-   Varsa bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya değişiklikleri:  
  
    -   Varsa [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] olarak bildirilen `Page` projesinde: varsa [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] yok yerel olarak tanımlanmış tür başvuruları yoksa, yeniden derleyin [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tüm artı [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] yerel başvurularla; sayfaları [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] yerel sahip tüm başvuruları yeniden derleyin [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] yerel başvuruları içeren sayfaları.  
  
    -   Varsa [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] olarak bildirilen `ApplicationDefinition` projesinde: tümünü yeniden derle [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfaları (neden: her [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] başvuruyor bir <xref:System.Windows.Application> değişmiş olabilir türü).  
  
-   Proje dosyası yerine uygulama tanımı bir kod dosyası bildirir, bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyası:  
  
    -   Olup olmadığını denetleyin `ApplicationClassName` proje dosyasında değeri değişti (yeni bir uygulama türü var mı?). Bu durumda, tüm uygulama yeniden derleyin.  
  
    -   Aksi takdirde, tüm derlenir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] yerel başvuruları içeren sayfaları.  
  
-   Proje dosyası değişirse: tüm önceki kuralları uygulayın ve derlenmesi gerekiyor bakın. Aşağıdaki özellikler tetikleyiciye tam yeniden derlemeye değiştirir: `AssemblyName`, `IntermediateOutputPath`, `RootNamespace`, ve `HostInBrowser`.  
  
 Aşağıdaki yeniden derleme senaryoları desteklenir:  
  
-   Tüm uygulama derlenir.  
  
-   Yalnızca [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] yerel olarak tanımlanan tür başvuruları dosyaları yeniden derlenir.  
  
-   Hiçbir şey (projedeki hiçbir şey değiştirilmişse) derlenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF Uygulaması Dağıtma](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md)  
 [WPF MSBuild Başvurusu](/visualstudio/msbuild/wpf-msbuild-reference)  
 [WPF İçinde URI'leri Paketleme](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)  
 [WPF Uygulama Kaynağı, İçerik ve Veri Dosyaları](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)
