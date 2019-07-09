---
title: WPF Uygulaması Oluşturma (WPF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WPF application [WPF], building
ms.assetid: a58696fd-bdad-4b55-9759-136dfdf8b91c
ms.openlocfilehash: 8d24314290e4f385362a3369836e4d18a23cc868
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663091"
---
# <a name="building-a-wpf-application-wpf"></a>WPF Uygulaması Oluşturma (WPF)

Windows Presentation Foundation (WPF) uygulamaları, .NET Framework yürütülebilir dosyalar (.exe), kütüphaneler (.dll) veya her iki tür derlemeleri bir birleşimi oluşturulabilir. Bu konu nasıl oluşturulacağını tanıtır [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamalar ve anahtar derleme işlemindeki adımları açıklar.

<a name="Building_a_WPF_Application_using_Command_Line"></a>

## <a name="building-a-wpf-application"></a>WPF Uygulaması Oluşturma

WPF uygulaması aşağıdaki yollarla derlenebilir:

- Komut satırı. Uygulama, yalnızca kod (hiçbir XAML) ve bir uygulama tanımı dosyası içermelidir. Daha fazla bilgi için [yapı komut satırı ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) veya [(Visual Basic) komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md).

- Microsoft Build Engine (MSBuild). Kod ve XAML dosyaları ek olarak, uygulamanın bir MSBuild proje dosyası içermesi gerekir. Daha fazla bilgi için "MSBuild" konusuna bakın.

- Visual Studio. Visual Studio WPF uygulamaları MSBuild ile derleme ve kullanıcı Arabirimi oluşturmak için bir görsel tasarımcı içeren bir tümleşik geliştirme ortamıdır. Daha fazla bilgi için [yazmak ve kodunuzu Visual Studio kullanarak yönetme](/visualstudio/ide/index-writing-code) ve [Visual Studio'da XAML tasarım](/visualstudio/designers/designing-xaml-in-visual-studio).

<a name="The_Windows_Presentation_Foundation_Build_Pipeline"></a>

## <a name="wpf-build-pipeline"></a>WPF derleme işlem hattı

Olduğunda bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] projesi yapılandırıldığında, dile özgü birleşimi ve [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]-belirli hedefler çağrılır. Bu hedefleri yürütme işleminin derleme işlem hattı olarak adlandırılır ve temel adımları aşağıdaki şekilde gösterilmiştir.

![WPF yapı işlemi](./media/wpfbuildsystem-figure1.png "WPFBuildSystem_Figure1")

<a name="Pre_Build_Initializations"></a>

### <a name="pre-build-initializations"></a>Derleme öncesi başlatmalar

Yapılandırmadan önce [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] önemli araçlar ve kitaplıklar, aşağıdakiler dahil olmak üzere konumunu belirler:

- .NET Framework.

- [!INCLUDE[TLA2#tla_wcsdk](../../../../includes/tla2sharptla-wcsdk-md.md)] Dizinleri.

- Konumunu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] başvuru derlemeleri.

- Arama yollarını derleme için özellik.

İlk konum burada [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] aramaları derlemeler için olan başvuru derleme dizini (%ProgramFiles%\Reference Assemblies\Microsoft\Framework\v3.0\\). Bu adım sırasında derleme işlemi ayrıca çeşitli özellikler ve öğesi grupları başlatır ve gerekli temizleme işini gerçekleştirir.

<a name="Resolving_references"></a>

### <a name="resolving-references"></a>Başvurular çözümleniyor

Derleme işlemi bulur ve uygulaması projesi oluşturmak için gerekli olan derlemeleri bağlar. Bu mantık bulunan `ResolveAssemblyReference` görev. Olarak bildirilen tüm derlemeler `Reference` proje dosyasında görev yanı sıra arama yolları hakkında bilgi ve sistemde zaten yüklü derlemeler hakkında meta veri sağlanır. Görev, derlemeleri arar ve bu çekirdek filtrelemek için yüklü derlemenin meta verilerini kullanan [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] çıkış Bildirimlerde yukarı gösterme gereken derlemeler. Bu, ClickOnce bildirimlerini yedekli bilgilerinde önlemek için yapılır. PresentationFramework.dll temsilcisi kabul edilebilir olduğundan Örneğin, bir uygulama için oluşturulan [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ve ayrıca tüm [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] derlemeleri mevcut .NET Framework'ün olduğu her makinede aynı konumda yüklü Bildirimlerde tüm .NET Framework başvuru bütünleştirilmiş kodları üzerindeki tüm bilgileri içerecek şekilde gerek yoktur.

<a name="Markup_Compilation___Pass_1"></a>

### <a name="markup-compilationpass-1"></a>Biçimlendirme derleme — geçiş 1

Bu adımda, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyaları ayrıştırılır ve çalışma zamanı ayrıştırma zaman harcamak için değil, derlenmiş [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] ve özellik değerlerini doğrulanıyor. Derlenmiş [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya öncesi simgeleştirilmiş yüklendikleri çalışma zamanında yüklemekten çok daha hızlı olmalıdır böylece bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya.

Bu adım sırasında aşağıdaki etkinlikleri gerçekleşmesi her [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] yani dosya bir `Page` öğesi oluşturun:

1. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Dosya biçimlendirme derleyici tarafından ayrıştırılır.

2. Derlenmiş bir gösterimi için oluşturulan [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ve obj\Release klasörüne kopyalanır.

3. Yeni bir kısmi sınıf CodeDOM gösterimini oluşturulur ve obj\Release klasörüne kopyalanır.

Dile özgü kod dosyası için ek olarak, oluşturulan her [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya. Örneğin, Visual Basic projesinde Page1.xaml sayfası için bir Page1.g.vb oluşturulur; C# projesinde Page1.xaml sayfası için bir Page1.g.cs oluşturulur. Dosya oluşturulduğunda dosya adı ".g" gösterir işaretleme dosyasının bir üst düzey öğe için bir kısmi sınıf bildirimine sahip kod (gibi `Page` veya `Window`). Sınıfı ile bildirilen `partial` C# değiştiricisi (`Extends` Visual Basic'te) sınıfın başka bir yerde başka bir bildirim belirtmek için genellikle arka plan kod içinde Page1.xaml.cs dosyası.

Uygun bir temel sınıftan kısmi sınıf genişletir (gibi <xref:System.Windows.Controls.Page> sayfası) ve uygulayan <xref:System.Windows.Markup.IComponentConnector?displayProperty=nameWithType> arabirimi. <xref:System.Windows.Markup.IComponentConnector> Arabirimi bir bileşen başlatıp adları ve olayları içeriğini öğelere bağlamak için yöntemleri vardır. Sonuç olarak, üretilen kod dosyasında aşağıdaki gibi bir yöntem uygulaması vardır:

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

Varsayılan olarak, biçimlendirme derleme aynı şekilde çalışır <xref:System.AppDomain> olarak [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] altyapısı. Bu, önemli ölçüde performans kazanımı sağlar. Bu davranışı ile değiştirilebilir `AlwaysCompileMarkupFilesInSeparateDomain` özelliği. Tüm başvuru bütünleştirilmiş kodları ayrı kaldırarak eklentiyi avantajı vardır <xref:System.AppDomain>.

<a name="Pass_2_of_Markup_Compilation"></a>

### <a name="markup-compilationpass-2"></a>Biçimlendirme derleme — 2 geçirin

Tüm [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfaları derlenir biçimlendirme derlemesinin 1 geçişi sırasında. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] yerel olarak tanımlanan türü başvuruları (kod başka bir yerde aynı projede tanımlanan türler için başvuru) dosyaları, şu anda derleme dışındadır. Bu yerel olarak tanımlanan türleri yalnızca kaynakta mevcut ve henüz derlenmiş olmasıdır. Bunu belirlemek için ayrıştırıcı gibi öğeler aranıyor gerektiren buluşsal yöntemler kullanır `x:Name` biçimlendirme dosyası. Bu tür bir örnek bulunduğunda biçimlendirme dosyanın derleme kod dosyaları, daha sonra derlenmiştir kadar ertelenir ikinci biçimlendirmesi derleme işlemleri bu dosyaları geçirin.

<a name="File_Classification"></a>

### <a name="file-classification"></a>Dosya sınıflandırması

Derleme işlemi puts çıktı dosyalarını farklı kaynak gruplarında hangi uygulama derlemesine bunlar yerleştirileceği temel. Tüm veri dosyalarının işaretlenmişi tipik olarak yerelleştirilmemiş uygulamada `Resource` ana derlemeye (yürütülebilir veya kitaplık) yerleştirilir. Zaman `UICulture` projede derlenen tüm ayarlandığında [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyaları ve özellikle dile bağlı olarak işaretlenmiş kaynakları uydu kaynak derlemesindeki yerleştirilir. Ayrıca, tüm dilden kaynakları ana derlemede yerleştirilir. Yapı işleminin bu adımında, o belirleme yapılır.

`ApplicationDefinition`, `Page`, Ve `Resource` proje dosyasındaki derleme Eylemler ile Genişletilebilir `Localizable` meta verileri (kabul edilebilir değerler `true` ve `false`), dosyanın dile bağlı olup olmadığını belirleyen veya dilden bağımsız.

<a name="Core_Compilation"></a>

### <a name="core-compilation"></a>Çekirdek derleme

Çekirdek derleme adımı kod dosyalarının derlenmesini gerektirir. Dile özgü MSBuild Microsoft.CSharp.targets ve Microsoft.VisualBasic.targets'daki mantığı tarafından yönetilir. Buluşsal yöntemler, karar verdiyseniz biçimlendirme derleyici tek bir geçişteki yeterlidir, ardından ana derleme oluşturulur. Ancak, bir veya daha fazla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] projeleri içindeki dosyaların yerel olarak tanımlanan türlere başvuru ve ardından biçimlendirme derleme ikinci geçişi tamamlandıktan sonra son uygulama derlemeleri oluşturulabilmesi için bir geçici bir .dll dosyası oluşturulur.

<a name="Manifest_generation"></a>

### <a name="manifest-generation"></a>Bildirim üretme

Tüm içerik dosyalarını ve uygulama derlemeleri hazır olduktan sonra yapı işleminin sonunda [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] uygulama için bildirimleri oluşturulur.

Dağıtım bildirimi dosyası dağıtım modeli açıklanmaktadır: geçerli sürümü, güncelleştirme davranışını ve dijital imza birlikte yayımcı kimliği. Bu bildirimi dağıtımını yönetmek yöneticiler tarafından yazılmış olarak görünür yöneliktir. .Xbap dosya uzantısıdır (için [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]) ve .application yüklü uygulamalar için. Önceki tarafından dikte `HostInBrowser` proje özelliği ve sonuç olarak uygulamayı tarayıcıda barındırılan olarak bildirim tanımlar.

Uygulama bildirimini (bir. exe.manifest dosyası) uygulama derlemeleri ve bağımlı kitaplıkları açıklar ve uygulama tarafından istenen izinleri listeler. Bu dosya, uygulama geliştiricisi tarafından yazılmış olarak görünür yöneliktir. Başlatmak için bir [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] uygulama, kullanıcı uygulamanın dağıtım bildirimi dosyasını açar.

Bu bildirim dosyaları için her zaman oluşturulan [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]. Yüklü uygulamalar için sürece oluşturulmaz `GenerateManifests` özellik değerine sahip proje dosyasında belirtilen `true`.

[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] Bu izinleri, tipik Internet bölgesi uygulamalarına atanan sağladığımız iki ek izinleri alın: <xref:System.Security.Permissions.WebBrowserPermission> ve <xref:System.Security.Permissions.MediaPermission>. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Derleme sistemi, bu izinleri uygulama bildiriminde bildirir.

<a name="Incremental_Build_Support"></a>

## <a name="incremental-build-support"></a>Artımlı derleme desteği

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Derleme sistemi, artımlı derlemeleri için destek sağlar. İşaretleme veya kod yapılan değişiklikler algılanıyor hakkında oldukça Akıllı ve yalnızca değişiklikten etkilenen yapıtları derler. Artımlı oluşturma mekanizması, aşağıdaki dosyaları kullanır:

- Bir (*AssemblyName*) geçerli derleme durumunu korumak üzere _MarkupCompiler.Cache dosyası.

- Bir (*AssemblyName*) önbellek _MarkupCompiler.lref dosyasına [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyaları yerel olarak tanımlanan türlere başvuru.

Aşağıdaki Artımlı derleme yöneten kurallar kümesidir:

- Dosya, derleme sistemi değişikliği algılar en küçük birimdir. Bu nedenle, bir kod dosyası için derleme sisteminin bir türü değişirse veya kod eklediyseniz bildiremez. Aynı proje dosyaları için geçerlidir.

- Artımlı oluşturma mekanizması cognizant olmalıdır, bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfasının bir sınıf tanımlar veya diğer sınıfları kullanır.

- Varsa `Reference` girişleri değiştirin, sonra tüm sayfaları yeniden derleyin.

- Bir kod dosyası değişirse, yerel olarak tanımlanan tür başvurularını içeren tüm sayfaları yeniden derleyin.

- Varsa bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya değişiklikleri:

  - Varsa [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] olarak bildirilen `Page` projedeki: varsa [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] değil yerel olarak tanımlanan tür başvurularını varsa, yeniden derleyin [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] artı tüm [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] yerel başvurular ile; sayfaları [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] yerel sahip tüm başvuruları yeniden derleyin [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] yerel başvurular sayfaları.

  - [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Olarak bildirilen `ApplicationDefinition` projedeki: tümünü yeniden derle [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfaları (neden: her [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] başvuru yapan bir <xref:System.Windows.Application> değişmiş olabilir bir tür).

- Proje dosyası yerine uygulama tanımı olarak bir kod dosyası bildiriyorsa bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyası:

  - Kontrol `ApplicationClassName` proje dosyasındaki değeri değiştirildi (yeni bir uygulama türü mi?). Bu durumda, uygulamanın tamamını yeniden derleyin.

  - Aksi takdirde, tümünü yeniden derle [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] yerel başvurular sayfaları.

- Bir proje dosyası değişirse: Yukarıdaki tüm kuralları uygulamak ve derlenmesi için gerekenler bakın. Tam çalışabilmeleri için aşağıdaki özellikleri tetikleyici değiştirir: `AssemblyName`, `IntermediateOutputPath`, `RootNamespace`, ve `HostInBrowser`.

Aşağıdaki yeniden derleyin senaryoları şunlardır:

- Uygulamanın tamamı yeniden derlenir.

- Yalnızca [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] yerel olarak tanımlanan tür başvuruları dosyaları derlenir.

- (Projede olmadıysa) hiçbir şey derlenir.

## <a name="see-also"></a>Ayrıca bkz.

- [WPF Uygulaması Dağıtma](deploying-a-wpf-application-wpf.md)
- [WPF MSBuild Başvurusu](/visualstudio/msbuild/wpf-msbuild-reference)
- [WPF İçinde URI'leri Paketleme](pack-uris-in-wpf.md)
- [WPF Uygulama Kaynağı, İçerik ve Veri Dosyaları](wpf-application-resource-content-and-data-files.md)
