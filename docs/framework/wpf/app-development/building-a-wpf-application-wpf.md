---
title: WPF Uygulaması Oluşturma (WPF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WPF application [WPF], building
ms.assetid: a58696fd-bdad-4b55-9759-136dfdf8b91c
ms.openlocfilehash: 02a86ea8d8d6b481044d6ca25d29df7edd2c73ee
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401685"
---
# <a name="building-a-wpf-application-wpf"></a>WPF Uygulaması Oluşturma (WPF)

Windows Presentation Foundation (WPF) uygulamaları, .NET Framework yürütülebilir dosyalar (. exe), kitaplıklar (. dll) veya her iki tür derleme birleşimi olarak oluşturulabilir. Bu konu, uygulama oluşturmayı [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ve yapı işlemindeki önemli adımları açıklar.

<a name="Building_a_WPF_Application_using_Command_Line"></a>

## <a name="building-a-wpf-application"></a>WPF Uygulaması Oluşturma

WPF uygulaması aşağıdaki yollarla derlenebilir:

- Komut satırı. Uygulamanın yalnızca kod (XAML yok) ve bir uygulama tanımı dosyası içermesi gerekir. Daha fazla bilgi için bkz. [CSC. exe Ile komut satırı oluşturma](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) veya [komut satırından oluşturma (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md).

- Microsoft Build Engine (MSBuild). Kod ve XAML dosyalarına ek olarak, uygulamanın bir MSBuild proje dosyası içermesi gerekir. Daha fazla bilgi için bkz. "MSBuild".

- Visual Studio. Visual Studio, MSBuild ile WPF uygulamalarını derlenen ve Kullanıcı arabirimi oluşturmaya yönelik bir görsel tasarımcı içeren tümleşik bir geliştirme ortamıdır. Daha fazla bilgi için bkz. Visual [Studio kullanarak kodu yazma ve yönetme](/visualstudio/ide/index-writing-code) ve [VISUAL Studio 'da xaml tasarlama](/visualstudio/designers/designing-xaml-in-visual-studio).

<a name="The_Windows_Presentation_Foundation_Build_Pipeline"></a>

## <a name="wpf-build-pipeline"></a>WPF derleme işlem hattı

Bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] proje oluşturulduğunda, dile özgü ve [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]özel hedeflerin birleşimi çağrılır. Bu hedefleri yürütme işlemine derleme işlem hattı denir ve anahtar adımları aşağıdaki şekilde gösterilmiştir.

![WPF derleme işlemi](./media/wpfbuildsystem-figure1.png "WPFBuildSystem_Figure1")

<a name="Pre_Build_Initializations"></a>

### <a name="pre-build-initializations"></a>Derleme öncesi başlatmalar

Oluşturmadan önce, aşağıdakiler de dahil olmak üzere önemli araçların ve kitaplıkların konumunu belirler:[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]

- .NET Framework.

- [!INCLUDE[TLA2#tla_wcsdk](../../../../includes/tla2sharptla-wcsdk-md.md)] Dizinler.

- [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Başvuru derlemelerinin konumu.

- Derleme arama yollarının özelliği.

Derlemeler için [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] arama yapılan ilk konum, başvuru derleme dizinidir (%ProgramFiles%\Reference birleştiriciler lies\microsoft\framework\v3.0\\). Bu adım sırasında yapı işlemi ayrıca çeşitli özellikleri ve öğe gruplarını başlatır ve gerekli temizleme çalışmalarını gerçekleştirir.

<a name="Resolving_references"></a>

### <a name="resolving-references"></a>Başvuruları çözme

Yapı işlemi, uygulama projesini oluşturmak için gereken derlemeleri bulur ve bağlar. Bu mantık `ResolveAssemblyReference` görevde bulunur. Proje dosyasında olarak `Reference` belirtilen tüm derlemeler, sistemde zaten yüklü olan derlemeler üzerindeki arama yolları ve meta veriler hakkındaki bilgilerle birlikte göreve sağlanır. Görev, derlemeleri arar ve çıkış bildirimlerinde gösterilmemelidir olması gereken temel [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] derlemeleri filtrelemek için yüklü derlemenin meta verilerini kullanır. Bu, ClickOnce bildirimlerinde gereksiz bilgilerin oluşmasını önlemek için yapılır. Örneğin, PresentationFramework. dll ' de ve için [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] oluşturulmuş bir uygulama temsilcisi olarak kabul edilebilir, çünkü tüm [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] derlemeler .NET Framework olan her makinede aynı konumda olduğundan. yüklü, tüm .NET Framework başvuru Derlemeleriyle ilgili tüm bilgileri bildirimlere dahil etme gereksinimi yoktur.

<a name="Markup_Compilation___Pass_1"></a>

### <a name="markup-compilationpass-1"></a>Biçimlendirme derlemesi — 1. geçiş

Bu adımda, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] çalışma zamanının özellik değerlerini ayrıştırma [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] ve doğrulama süresini harcamaması için dosyalar ayrıştırılır ve derlenir. Derlenen [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya önceden simgeleştirilir, böylece çalışma zamanında, yükleme bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyayı yüklemeden çok daha hızlı olmalıdır.

Bu adım sırasında, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] `Page` derleme öğesi olan her dosya için aşağıdaki etkinlikler gerçekleşir:

1. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Dosya, biçimlendirme derleyicisi tarafından ayrıştırılır.

2. Bunun için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] derlenmiş bir gösterim oluşturulur ve obj\Release klasörüne kopyalanır.

3. Yeni bir kısmi sınıfın CodeDOM temsili oluşturulup obj\Release klasörüne kopyalanır.

Ayrıca, her [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya için dile özgü bir kod dosyası oluşturulur. Örneğin, Visual Basic projesindeki bir Sayfa1. XAML sayfasında, bir Sayfa1. g. vb oluşturulur; bir C# projede bir Sayfa1. XAML sayfasında, bir Page1.g.cs oluşturulur. Dosya adında ". g", dosyanın, biçimlendirme dosyasının en üst düzey öğesi ( `Page` veya `Window`gibi) için kısmi bir sınıf bildirimine sahip bir kod oluşturulduğunu gösterir. Sınıf, genellikle arka plan kod `partial` dosyası Page1.xaml.cs C# içinde`Extends` , başka bir sınıf için başka bir bildirim olduğunu göstermek için içindeki değiştiriciyle (Visual Basic olarak) tanımlanır.

Kısmi sınıf uygun temel sınıftan ( <xref:System.Windows.Controls.Page> Örneğin, bir sayfa için) genişletilir ve <xref:System.Windows.Markup.IComponentConnector?displayProperty=nameWithType> arabirimini uygular. Arabirimin <xref:System.Windows.Markup.IComponentConnector> , bir bileşeni başlatma ve içeriğindeki öğelerin adlarını ve olaylarını bağlama yöntemleri vardır. Sonuç olarak, oluşturulan kod dosyası aşağıdaki gibi bir yöntem uygulamasına sahiptir:

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

Varsayılan olarak, biçimlendirme derlemesi altyapıda <xref:System.AppDomain> [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] aynı şekilde çalışır. Bu, önemli ölçüde performans artışı sağlar. Bu davranış, `AlwaysCompileMarkupFilesInSeparateDomain` özelliği ile değiştirilebilir. Bu, ayrı <xref:System.AppDomain>olarak kaldırarak tüm başvuru derlemelerini kaldırma avantajına sahiptir.

<a name="Pass_2_of_Markup_Compilation"></a>

### <a name="markup-compilationpass-2"></a>Biçimlendirme derlemesi — Pass 2

Biçimlendirme derlemesinin [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 1. geçişi sırasında tüm sayfalar derlenmez. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]Yerel olarak tanımlanmış tür başvuruları olan dosyalar (aynı projede başka bir yerde kodda tanımlanan türlere başvurular) Şu anda derlemeden muaf tutulur. Bunun nedeni yerel olarak tanımlanmış türlerin yalnızca kaynakta yer aldığı ve henüz derlenmediği içindir. Bunu belirleyebilmek için, ayrıştırıcı, biçimlendirme dosyasında gibi `x:Name` öğeler için arama içeren buluşsal yöntemler kullanır. Böyle bir örnek bulunduğunda, bu biçimlendirme dosyasının derlenmesi kod dosyaları derlenene kadar ertelenir, sonrasında ikinci biçimlendirme derleme geçişi bu dosyaları işler.

<a name="File_Classification"></a>

### <a name="file-classification"></a>Dosya sınıflandırması

Yapı işlemi, çıktı dosyalarını, hangi uygulama derlemesine yerleştirilebileceğini temel alarak farklı kaynak gruplarına koyar. Yerelleştirilmiş olmayan tipik bir uygulamada, olarak `Resource` işaretlenen tüm veri dosyaları ana derlemeye (yürütülebilir veya kitaplık) yerleştirilir. Projede ayarlandığında, derlenen [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tüm dosyalar ve özellikle dile özgü olarak işaretlenen kaynaklar uydu kaynak derlemesine yerleştirilir. `UICulture` Ayrıca, tüm dilden bağımsız kaynaklar ana derlemeye yerleştirilir. Yapı işleminin bu adımında, bu belirleme yapılır.

`Page` Projedosyasındaki`Resource` `true`,ve derleme eylemleri `false`meta verilerle genişletilebilir (kabul edilebilir değerler ve), dosyanın dile özgü olup olmadığını belirler. `Localizable` `ApplicationDefinition` dilden bağımsız.

<a name="Core_Compilation"></a>

### <a name="core-compilation"></a>Çekirdek derleme

Çekirdek derleme adımı kod dosyalarının derlemesini içerir. Bu, dile özgü hedef dosyalarındaki Microsoft. CSharp. targets ve Microsoft. VisualBasic. targets içindeki mantığa göre düzenlenir. Buluşsal yöntemler, biçimlendirme derleyicisinin tek bir geçişinin yeterli olduğunu belirleiyorsa, ana derleme oluşturulur. Ancak, projedeki bir veya daha [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fazla dosyanın yerel olarak tanımlanmış türlere başvuruları varsa, biçimlendirme derlemesinin ikinci geçişi tamamlandıktan sonra son uygulama derlemelerinin oluşturulabilmesi için geçici bir. dll dosyası oluşturulur.

<a name="Manifest_generation"></a>

### <a name="manifest-generation"></a>Bildirim oluşturma

Yapı işleminin sonunda, tüm uygulama derlemeleri ve içerik dosyaları hazırlandıktan sonra, uygulamanın ClickOnce bildirimleri oluşturulur.

Dağıtım bildirim dosyası, dağıtım modelini açıklar: geçerli sürüm, güncelleştirme davranışı ve Yayımcı kimliği ile birlikte dijital imza. Bu bildirim, dağıtımı işleyen yöneticiler tarafından yazılmak üzere tasarlanmıştır. Dosya uzantısı, yüklü uygulamalar için. xbap [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)](için) ve. Application ' dır. İlki `HostInBrowser` proje özelliği tarafından dikte edilir ve sonuç olarak bildirim, uygulamayı tarayıcıda barındırılan olarak tanımlar.

Uygulama bildirimi (bir. exe. manifest dosyası) uygulama derlemelerini ve bağımlı kitaplıkları açıklar ve uygulamanın gerektirdiği izinleri listeler. Bu dosya, uygulama geliştiricisi tarafından yazılmayı amaçlanır. Bir ClickOnce uygulamasını başlatmak için, kullanıcı uygulamanın dağıtım bildirim dosyasını açar.

Bu bildirim dosyaları her zaman için [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]oluşturulur. Yüklü uygulamalar için, `GenerateManifests` özelliği değeri `true`olan proje dosyasında belirtilmediği takdirde bunlar oluşturulmaz.

[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]tipik Internet bölgesi uygulamalarına atanan izinlerin üzerinde ve üzerinde iki ek izin alın: <xref:System.Security.Permissions.WebBrowserPermission> ve. <xref:System.Security.Permissions.MediaPermission> [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Yapı sistemi bu izinleri uygulama bildiriminde bildirir.

<a name="Incremental_Build_Support"></a>

## <a name="incremental-build-support"></a>Artımlı derleme desteği

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Yapı sistemi Artımlı derlemeler için destek sağlar. Biçimlendirme veya koda yapılan değişiklikleri algılamayla oldukça akıllı bir şeydir ve yalnızca değişikliğin etkilediği yapıtları derler. Artımlı derleme mekanizması aşağıdaki dosyaları kullanır:

- Geçerli derleyici durumunu korumak için bir $ (*AssemblyName*) _Markupcompiler. cache dosyası.

- [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Dosyaları yerel olarak tanımlanmış türlere başvurularla önbelleğe almak için $ (*AssemblyName*) _MarkupCompiler. lref dosyası.

Artımlı derlemeyi yöneten bir kurallar kümesi aşağıda verilmiştir:

- Dosya, derleme sisteminin değişikliği algıladığı en küçük birimdir. Bu nedenle, bir kod dosyası için, yapı sistemi bir türün değiştirilip değiştirilmediğini veya kodun eklenmiş olduğunu söyleyebilir. Proje dosyaları için aynı durum geçerlidir.

- Artımlı derleme mekanizması bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfanın bir sınıfı tanımladığından veya diğer sınıfları kullandığından emin olmalıdır.

- `Reference` Girişler değiştiğinde tüm sayfaları yeniden derleyin.

- Bir kod dosyası değişirse, tüm sayfaları yerel olarak tanımlanmış tür başvurularına yeniden derleyin.

- Bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya değişirse:

  - `Page` [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , Projede olarak bildirilirse: yerel olarak tanımlanmış tür başvurularına sahip değilse, bu ve tüm sayfaları yerel başvuruları ile yeniden derleyin; Eğer Eğer yerel [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] başvurular, tüm [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfaları yerel başvurularla yeniden derleyin.

  - <xref:System.Windows.Application> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Projede olarak `ApplicationDefinition` bildirilirse: tüm [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfaları yeniden derle (nedeni: her birinin değişmiş olabilecek bir türe başvurusu vardır). [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]

- Proje dosyası bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya yerine uygulama tanımı olarak bir kod dosyası bildirirse:

  - Proje dosyasındaki değerin değişip değişmediğini denetleyin (yeni bir uygulama türü mi var?). `ApplicationClassName` Bu durumda, tüm uygulamayı yeniden derleyin.

  - Aksi takdirde, tüm [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfaları yerel başvurularla yeniden derleyin.

- Bir proje dosyası değişirse: önceki tüm kuralları uygulayın ve nelerin yeniden derlenmesi gerektiğini görün. Aşağıdaki özelliklerde yapılan değişiklikler tüm yeniden derlemeyi tetikler `AssemblyName`:, `IntermediateOutputPath`, `RootNamespace`ve `HostInBrowser`.

Aşağıdaki yeniden derleme senaryoları mümkündür:

- Tüm uygulama yeniden derlenir.

- Yalnızca yerel olarak tanımlanmış tür başvurularına sahip dosyalaryenidenderlenir.[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]

- Hiçbir şey yeniden derlenmez (projedeki hiçbir şey değişmezse).

## <a name="see-also"></a>Ayrıca bkz.

- [WPF Uygulaması Dağıtma](deploying-a-wpf-application-wpf.md)
- [WPF MSBuild Başvurusu](/visualstudio/msbuild/wpf-msbuild-reference)
- [WPF İçinde URI'leri Paketleme](pack-uris-in-wpf.md)
- [WPF Uygulama Kaynağı, İçerik ve Veri Dosyaları](wpf-application-resource-content-and-data-files.md)
