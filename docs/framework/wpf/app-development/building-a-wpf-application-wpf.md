---
title: WPF Uygulaması Oluşturma (WPF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WPF application [WPF], building
ms.assetid: a58696fd-bdad-4b55-9759-136dfdf8b91c
ms.openlocfilehash: bf673195f06475daf8341fd17cd701b84a970b39
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740670"
---
# <a name="building-a-wpf-application-wpf"></a>WPF Uygulaması Oluşturma (WPF)

Windows Presentation Foundation (WPF) uygulamaları, .NET Framework yürütülebilir dosyalar (. exe), kitaplıklar (. dll) veya her iki tür derleme birleşimi olarak oluşturulabilir. Bu konu, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamalarının nasıl oluşturulacağını ve yapı işlemindeki önemli adımları açıklar.

<a name="Building_a_WPF_Application_using_Command_Line"></a>

## <a name="building-a-wpf-application"></a>WPF Uygulaması Oluşturma

WPF uygulaması aşağıdaki yollarla derlenebilir:

- Komut satırı. Uygulamanın yalnızca kod (XAML yok) ve bir uygulama tanımı dosyası içermesi gerekir. Daha fazla bilgi için bkz. [CSC. exe Ile komut satırı oluşturma](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) veya [komut satırından oluşturma (Visual Basic)](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).

- Microsoft Build Engine (MSBuild). Kod ve XAML dosyalarına ek olarak, uygulamanın bir MSBuild proje dosyası içermesi gerekir. Daha fazla bilgi için bkz. "MSBuild".

- Visual Studio. Visual Studio, MSBuild ile WPF uygulamalarını derlenen ve Kullanıcı arabirimi oluşturmaya yönelik bir görsel tasarımcı içeren tümleşik bir geliştirme ortamıdır. Daha fazla bilgi için bkz. Visual [Studio kullanarak kodu yazma ve yönetme](/visualstudio/ide/index-writing-code) ve [VISUAL Studio 'da xaml tasarlama](/visualstudio/xaml-tools/designing-xaml-in-visual-studio).

<a name="The_Windows_Presentation_Foundation_Build_Pipeline"></a>

## <a name="wpf-build-pipeline"></a>WPF derleme işlem hattı

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] bir proje yapılandırıldığında dile özgü ve [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]özgü hedeflerin birleşimi çağrılır. Bu hedefleri yürütme işlemine derleme işlem hattı denir ve anahtar adımları aşağıdaki şekilde gösterilmiştir.

![WPF derleme işlemi](./media/wpfbuildsystem-figure1.png "WPFBuildSystem_Figure1")

<a name="Pre_Build_Initializations"></a>

### <a name="pre-build-initializations"></a>Derleme öncesi başlatmalar

Derlemeden önce, MSBuild aşağıdakiler de dahil olmak üzere önemli araçların ve kitaplıkların konumunu belirler:

- .NET Framework.

- Windows SDK dizinleri.

- [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] başvuru derlemelerinin konumu.

- Derleme arama yollarının özelliği.

MSBuild 'in derlemeleri arayacağı ilk konum başvuru derleme dizinidir (%ProgramFiles%\Reference ayrıştırılmış Lies\microsoft\framework\v3,0\\). Bu adım sırasında yapı işlemi ayrıca çeşitli özellikleri ve öğe gruplarını başlatır ve gerekli temizleme çalışmalarını gerçekleştirir.

<a name="Resolving_references"></a>

### <a name="resolving-references"></a>Başvuruları çözme

Yapı işlemi, uygulama projesini oluşturmak için gereken derlemeleri bulur ve bağlar. Bu mantık `ResolveAssemblyReference` görevde bulunur. Proje dosyasında `Reference` olarak belirtilen tüm derlemeler, sistemde zaten yüklü olan derlemeler üzerindeki arama yolları ve meta veriler hakkındaki bilgilerle birlikte göreve sağlanır. Görev, derlemeleri arar ve çıkış bildirimlerinde gösterilmemelidir olması gereken temel [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] derlemelerini filtrelemek için yüklü derlemenin meta verilerini kullanır. Bu, ClickOnce bildirimlerinde gereksiz bilgilerin oluşmasını önlemek için yapılır. Örneğin, PresentationFramework. dll, üzerinde oluşturulmuş bir uygulama temsilcisi olarak kabul edilebilir ve [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] için ve üstelik, tüm [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] derlemelerinin .NET Framework yüklü olan her makinede aynı konumda mevcut olduğundan, bu, bildirimlerde tüm .NET Framework başvuru Derlemeleriyle ilgili tüm bilgileri ekleme gereksinimi yoktur.

<a name="Markup_Compilation___Pass_1"></a>

### <a name="markup-compilationpass-1"></a>Biçimlendirme derlemesi — 1. geçiş

Bu adımda, çalışma zamanının XML ayrıştırma ve özellik değerlerini doğrulama süresini harcamaması için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyalar ayrıştırılır ve derlenir. Derlenmiş [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyası önceden simgeleştirilir, böylece çalışma zamanında, yükleme bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyası yüklemeden çok daha hızlı olmalıdır.

Bu adım sırasında, bir `Page` derleme öğesi olan her [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyası için aşağıdaki etkinlikler gerçekleşir:

1. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyası, biçimlendirme derleyicisi tarafından ayrıştırılır.

2. Bu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] için derlenmiş bir temsili oluşturulur ve obj\Release klasörüne kopyalanır.

3. Yeni bir kısmi sınıfın CodeDOM temsili oluşturulup obj\Release klasörüne kopyalanır.

Ayrıca, her [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyası için dile özgü bir kod dosyası oluşturulur. Örneğin, Visual Basic projesindeki bir Sayfa1. XAML sayfasında, bir Sayfa1. g. vb oluşturulur; bir C# projede bir Sayfa1. XAML sayfasında, bir Page1.g.cs oluşturulur. Dosya adında ". g", dosyanın, biçimlendirme dosyasının en üst düzey öğesi (`Page` veya `Window`gibi) için kısmi bir sınıf bildirimine sahip bir kod oluşturulduğunu gösterir. Sınıf, genellikle arka plan kod dosyası Page1.xaml.cs içinde C# , başka bir sınıf için başka bir bildirim olduğunu göstermek için içinde `partial` değiştiricisi (Visual Basic`Extends`) ile bildirilmiştir.

Kısmi sınıf uygun temel sınıftan (örneğin, bir sayfa için <xref:System.Windows.Controls.Page>) genişletilir ve <xref:System.Windows.Markup.IComponentConnector?displayProperty=nameWithType> arabirimini uygular. <xref:System.Windows.Markup.IComponentConnector> arabirimi, bir bileşeni başlatma ve içeriğindeki öğelerin adlarını ve olaylarını bağlama yöntemlerine sahiptir. Sonuç olarak, oluşturulan kod dosyası aşağıdaki gibi bir yöntem uygulamasına sahiptir:

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

Varsayılan olarak, biçimlendirme derlemesi MSBuild altyapısıyla aynı <xref:System.AppDomain> çalışır. Bu, önemli ölçüde performans artışı sağlar. Bu davranış `AlwaysCompileMarkupFilesInSeparateDomain` özelliği ile değiştirilebilir. Bu, ayrı <xref:System.AppDomain>kaldırarak tüm başvuru derlemelerini kaldırma avantajına sahiptir.

<a name="Pass_2_of_Markup_Compilation"></a>

### <a name="markup-compilationpass-2"></a>Biçimlendirme derlemesi — Pass 2

[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfaların hepsi, biçimlendirme derlemesinin 1. geçişi sırasında derlenmez. Yerel olarak tanımlanmış tür başvurularına sahip [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyaları (aynı projede başka bir yerde kodda tanımlanan türlere başvurular), şu anda derlemeden muaf tutulur. Bunun nedeni yerel olarak tanımlanmış türlerin yalnızca kaynakta yer aldığı ve henüz derlenmediği içindir. Bunu belirleyebilmek için, ayrıştırıcı, biçimlendirme dosyasında `x:Name` gibi öğeleri bulmak için gereken buluşsal yöntemler kullanır. Böyle bir örnek bulunduğunda, bu biçimlendirme dosyasının derlenmesi kod dosyaları derlenene kadar ertelenir, sonrasında ikinci biçimlendirme derleme geçişi bu dosyaları işler.

<a name="File_Classification"></a>

### <a name="file-classification"></a>Dosya sınıflandırması

Yapı işlemi, çıktı dosyalarını, hangi uygulama derlemesine yerleştirilebileceğini temel alarak farklı kaynak gruplarına koyar. Yerelleştirilmiş olmayan tipik bir uygulamada, `Resource` olarak işaretlenen tüm veri dosyaları ana derlemeye (yürütülebilir veya kitaplık) yerleştirilir. Projede `UICulture` ayarlandığında, derlenen tüm [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyalar ve özellikle dile özgü olarak işaretlenen kaynaklar uydu kaynak derlemesine yerleştirilir. Ayrıca, tüm dilden bağımsız kaynaklar ana derlemeye yerleştirilir. Yapı işleminin bu adımında, bu belirleme yapılır.

Proje dosyasındaki `ApplicationDefinition`, `Page`ve `Resource` derleme eylemleri `Localizable` meta verilerle genişletilebilir (kabul edilebilir değerler `true` ve `false`), dosyanın dile özgü mi yoksa dilden bağımsız mi olduğunu belirler.

<a name="Core_Compilation"></a>

### <a name="core-compilation"></a>Çekirdek derleme

Çekirdek derleme adımı kod dosyalarının derlemesini içerir. Bu, dile özgü hedef dosyalarındaki Microsoft. CSharp. targets ve Microsoft. VisualBasic. targets içindeki mantığa göre düzenlenir. Buluşsal yöntemler, biçimlendirme derleyicisinin tek bir geçişinin yeterli olduğunu belirleiyorsa, ana derleme oluşturulur. Ancak, projedeki bir veya daha fazla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyası yerel olarak tanımlanmış türlere başvurular içeriyorsa, biçimlendirme derlemesinin ikinci geçişi tamamlandıktan sonra son uygulama derlemelerinin oluşturulabilmesi için geçici bir. dll dosyası oluşturulur.

<a name="Manifest_generation"></a>

### <a name="manifest-generation"></a>Bildirim oluşturma

Yapı işleminin sonunda, tüm uygulama derlemeleri ve içerik dosyaları hazırlandıktan sonra, uygulamanın ClickOnce bildirimleri oluşturulur.

Dağıtım bildirim dosyası, dağıtım modelini açıklar: geçerli sürüm, güncelleştirme davranışı ve Yayımcı kimliği ile birlikte dijital imza. Bu bildirim, dağıtımı işleyen yöneticiler tarafından yazılmak üzere tasarlanmıştır. Dosya uzantısı. XBAP (XAML tarayıcı uygulamaları (XBAP) için) ve yüklü uygulamalar için. Application. İlki `HostInBrowser` proje özelliği tarafından dikte edilir ve sonuç olarak bildirim, uygulamayı tarayıcıda barındırılan olarak tanımlar.

Uygulama bildirimi (bir. exe. manifest dosyası) uygulama derlemelerini ve bağımlı kitaplıkları açıklar ve uygulamanın gerektirdiği izinleri listeler. Bu dosya, uygulama geliştiricisi tarafından yazılmayı amaçlanır. Bir ClickOnce uygulamasını başlatmak için, kullanıcı uygulamanın dağıtım bildirim dosyasını açar.

Bu bildirim dosyaları her zaman XBAP için oluşturulur. Yüklü uygulamalar için, `GenerateManifests` özelliği proje dosyasında `true`değer ile belirtilmediği takdirde oluşturulmaz.

XBAP 'ler, tipik Internet bölgesi uygulamalarına atanan izinlerin üzerinde ve üzerinde iki ek izin alır: <xref:System.Security.Permissions.WebBrowserPermission> ve <xref:System.Security.Permissions.MediaPermission>. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] yapı sistemi bu izinleri uygulama bildiriminde bildirir.

<a name="Incremental_Build_Support"></a>

## <a name="incremental-build-support"></a>Artımlı derleme desteği

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] yapı sistemi Artımlı derlemeler için destek sağlar. Biçimlendirme veya koda yapılan değişiklikleri algılamayla oldukça akıllı bir şeydir ve yalnızca değişikliğin etkilediği yapıtları derler. Artımlı derleme mekanizması aşağıdaki dosyaları kullanır:

- Geçerli derleyici durumunu korumak için bir $ (*AssemblyName*) _Markupcompiler. cache dosyası.

- [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyalarını yerel olarak tanımlanmış türlere başvurularla önbelleğe almak için $ (*AssemblyName*) _MarkupCompiler. lref dosyası.

Artımlı derlemeyi yöneten bir kurallar kümesi aşağıda verilmiştir:

- Dosya, derleme sisteminin değişikliği algıladığı en küçük birimdir. Bu nedenle, bir kod dosyası için, yapı sistemi bir türün değiştirilip değiştirilmediğini veya kodun eklenmiş olduğunu söyleyebilir. Proje dosyaları için aynı durum geçerlidir.

- Artımlı derleme mekanizması, bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfasının bir sınıfı tanımladığından veya diğer sınıfları kullandığından emin olmanız gerekir.

- `Reference` girdileri değiştiğinde tüm sayfaları yeniden derleyin.

- Bir kod dosyası değişirse, tüm sayfaları yerel olarak tanımlanmış tür başvurularına yeniden derleyin.

- Bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya değişirse:

  - [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] projede `Page` olarak bildirilirse: [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] yerel olarak tanımlanmış tür başvurularına sahip değilse, bu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ve tüm [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfalarını yerel başvurularla yeniden derleyin; [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] yerel başvurular içeriyorsa, tüm [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfalarını yerel başvurularla yeniden derleyin.

  - [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] projede `ApplicationDefinition` olarak bildirilirse: tüm [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfaları yeniden derleyin (neden: her [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] değişmiş olabilecek bir <xref:System.Windows.Application> türüne başvuru içerir).

- Proje dosyası bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyası yerine uygulama tanımı olarak bir kod dosyası bildirirse:

  - Proje dosyasındaki `ApplicationClassName` değerinin değişip değişmediğini denetleyin (yeni bir uygulama türü mi var?). Bu durumda, tüm uygulamayı yeniden derleyin.

  - Aksi takdirde, tüm [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfalarını yerel başvurularla yeniden derleyin.

- Bir proje dosyası değişirse: önceki tüm kuralları uygulayın ve nelerin yeniden derlenmesi gerektiğini görün. Aşağıdaki özelliklerde yapılan değişiklikler tüm yeniden derlemeyi tetikler: `AssemblyName`, `IntermediateOutputPath`, `RootNamespace`ve `HostInBrowser`.

Aşağıdaki yeniden derleme senaryoları mümkündür:

- Tüm uygulama yeniden derlenir.

- Yalnızca yerel olarak tanımlanmış tür başvurularına sahip [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyaları yeniden derlenir.

- Hiçbir şey yeniden derlenmez (projedeki hiçbir şey değişmezse).

## <a name="see-also"></a>Ayrıca bkz.

- [WPF Uygulaması Dağıtma](deploying-a-wpf-application-wpf.md)
- [WPF MSBuild Başvurusu](/visualstudio/msbuild/wpf-msbuild-reference)
- [WPF İçinde URI'leri Paketleme](pack-uris-in-wpf.md)
- [WPF Uygulama Kaynağı, İçerik ve Veri Dosyaları](wpf-application-resource-content-and-data-files.md)
