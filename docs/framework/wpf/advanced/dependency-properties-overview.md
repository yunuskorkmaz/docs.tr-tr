---
title: Bağımlılık özelliklerine genel bakış
description: WPF özellik sistemi tarafından desteklenen bir özellik bağımlılık özelliği olarak bilinir. Bu genel bakış, WPF özellik sistemini ve bağımlılık özelliğinin yeteneklerini açıklar.
ms.date: 06/06/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties [WPF], attached
- properties [WPF], overview
- styles [WPF]
- attached properties [WPF]
- data binding [WPF]
- dependency properties [WPF]
- resources [WPF], references to
ms.assetid: d119d00c-3afb-48d6-87a0-c4da4f83dee5
ms.openlocfilehash: 1df75814c45a6f1c245d43e2390b8a6ce692a779
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80587804"
---
# <a name="dependency-properties-overview"></a>Bağımlılık özelliklerine genel bakış

Windows Sunu Temeli (WPF), bir türün [özelliğinin](../../../standard/base-types/common-type-system.md#properties)işlevselliğini genişletmek için kullanılabilecek bir dizi hizmet sağlar. Toplu olarak, bu hizmetler genellikle WPF özellik sistemi olarak adlandırılır. WPF özellik sistemi tarafından desteklenen bir özellik bağımlılık özelliği olarak bilinir. Bu genel bakış, WPF özellik sistemini ve bağımlılık özelliğinin yeteneklerini açıklar. Bu, XAML'deki ve koddaki varolan bağımlılık özelliklerinin nasıl kullanılacağını içerir. Bu genel bakış, bağımlılık özelliği meta verileri ve özel bir sınıfta kendi bağımlılık özelliğinizi nasıl oluşturabilirsiniz gibi bağımlılık özelliklerinin özelleştirilmiş yönlerini de tanıtır.

## <a name="prerequisites"></a>Ön koşullar
Bu konu, .NET türü sistemi ve nesne yönelimli programlama hakkında bazı temel bilgilere sahip olduğunuzu varsayar. Bu konudaki örnekleri takip etmek için XAML'yi de anlamanız ve WPF uygulamalarının nasıl yazılabildiğini bilmeniz gerekir. Daha fazla bilgi için [Walkthrough: İlk WPF masaüstü uygulamam.](../getting-started/walkthrough-my-first-wpf-desktop-application.md)  
  
## <a name="dependency-properties-and-clr-properties"></a>Bağımlılık özellikleri ve CLR özellikleri
 WPF'de özellikler genellikle standart .NET [özellikleri](../../../standard/base-types/common-type-system.md#properties)olarak ortaya çıkarır. Temel düzeyde, bu özelliklerle doğrudan etkileşimkurabilir ve bunların bir bağımlılık özelliği olarak uygulandığını asla bilemezsin. Ancak, bu özelliklerden yararlanabilmeniz için WPF özellik sisteminin bazı larını veya tüm özelliklerini bilmeniz gerekir.

Bağımlılık özelliklerinin amacı, diğer girdilerin değerini temel alan bir özelliğin değerini hesaplamak için bir yol sağlamaktır. Bu diğer girdiler, temalar ve kullanıcı tercihi, veri bağlama ve animasyonlar/film şeridi gibi tam zamanında özellik belirleme mekanizmaları, kaynaklar ve stiller gibi çok kullanımlı şablonlar veya öğe ağacındaki diğer öğelerle üst-alt ilişkileri yoluyla bilinen değerler gibi sistem özelliklerini içerebilir. Ayrıca, bağımsız doğrulama, varsayılan değerler, diğer özelliklerdeki değişiklikleri izleyen geri aramalar ve potansiyel çalışma zamanı bilgilerine dayalı özellik değerlerini zorlayabilecek bir sistem sağlamak için bir bağımlılık özelliği uygulanabilir. Türetilen sınıflar, varolan özelliklerin fiili uygulanmasını geçersiz kılmak veya yeni özellikler oluşturmak yerine bağımlılık özelliği meta verilerini geçersiz kılarak varolan bir özelliğin bazı belirli özelliklerini de değiştirebilir.

SDK başvurusunda, bu özellik için yönetilen başvuru sayfasında Bağımlılık Özelliği Bilgileri bölümünün varlığıyla hangi özelliğin bağımlılık özelliği olduğunu belirleyebilirsiniz. Bağımlılık Özelliği Bilgileri bölümü, bu <xref:System.Windows.DependencyProperty> bağımlılık özelliği için tanımlayıcı alanına bir bağlantı içerir ve ayrıca bu özellik için ayarlanan meta veri seçeneklerinin, sınıf başına geçersiz kılma bilgilerinin ve diğer ayrıntıların bir listesini içerir.

## <a name="dependency-properties-back-clr-properties"></a>Bağımlılık özellikleri CLR özelliklerini geri
Bağımlılık özellikleri ve WPF özellik sistemi, özelliği özel bir alanla desteklemenin standart desenine alternatif bir uygulama olarak, bir özelliği destekleyen bir tür sağlayarak özellik işlevselliğini genişletir. Bu türün adı <xref:System.Windows.DependencyProperty>. WPF özellik sistemini tanımlayan diğer önemli <xref:System.Windows.DependencyObject>tür. <xref:System.Windows.DependencyObject>bir bağımlılık özelliğini kaydedip sahip olabilecek taban sınıfı tanımlar.

Bağımlılık özellikleriyle birlikte kullanılan terminoloji aşağıda listelenir:

- **Bağımlılık özelliği:** Bir <xref:System.Windows.DependencyProperty>.

- **Bağımlılık özelliği tanımlayıcısı:** Bağımlılık <xref:System.Windows.DependencyProperty> özelliğini kaydederken iade değeri olarak alınan ve daha sonra sınıfın statik üyesi olarak depolanan bir örnek. Bu tanımlayıcı, WPF özellik sistemiyle etkileşimde olan API'lerin çoğu için bir parametre olarak kullanılır.

- **CLR "sarıcı":** Gerçek almak ve özellik için uygulamaları ayarlayın. Bu uygulamalar bağımlılık özelliği tanımlayıcısını, wpf özellik sistemini <xref:System.Windows.DependencyObject.GetValue%2A> kullanarak <xref:System.Windows.DependencyObject.SetValue%2A> özellik için destek sağlayarak, arama larda ve aramalarda kullanarak içerir.

Aşağıdaki örnekbağımlılık özelliğini `IsSpinning` tanımlar ve tanımlayıcının <xref:System.Windows.DependencyProperty> desteklediği özellik ile ilişkisini gösterir.

[!code-csharp[PropertiesOvwSupport#DPFormBasic](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#dpformbasic)]
[!code-vb[PropertiesOvwSupport#DPFormBasic](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#dpformbasic)]  
  
Mülkiyet in adlandırma kuralı ve <xref:System.Windows.DependencyProperty> destek alanı önemlidir. Alanın adı her zaman özelliğin adıdır ve sonek `Property` eklenir. Bu kural ve bunun nedenleri hakkında daha fazla bilgi için [bkz.](custom-dependency-properties.md)  

## <a name="setting-property-values"></a>Özellik değerlerini ayarlama
Özellikleri kod veya XAML olarak ayarlayabilirsiniz.

### <a name="setting-property-values-in-xaml"></a>XAML'de özellik değerlerini ayarlama
Aşağıdaki XAML örneği, bir düğmenin arka plan rengini kırmızı olarak belirtir. Bu örnek, xaml özniteliği için basit dize değerinin WPF XAML parer tarafından oluşturulan koddaki WPF türüne <xref:System.Windows.Media.Color> <xref:System.Windows.Media.SolidColorBrush>(a, a) dönüştürüldüğü bir durumu göstermektedir.

[!code-xaml[PropertiesOvwSupport#MostBasicProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml#mostbasicproperty)]

XAML özellikleri ayarlamak için çeşitli sözdizimi formlarını destekler. Belirli bir özellik için hangi sözdizimi nin kullanılacağı, bir özelliğin kullandığı değer türüne ve bir tür dönüştürücünün varlığı gibi diğer etkenlere bağlıdır. Özellik ayarı için XAML sözdizimi hakkında daha fazla bilgi için Bkz. [XAML Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md) ve [XAML Sözdizimi Ayrıntılı](xaml-syntax-in-detail.md)olarak.

Öznitelik olmayan sözdizimine örnek olarak, aşağıdaki XAML örneği başka bir düğme arka planını gösterir. Bu kez basit bir düz renk ayarlamak yerine, arka plan, bu görüntüyü ve iç içe geçmiş öğenin bir özniteliği olarak belirtilen bu görüntünün kaynağını temsil eden bir öğe ile bir görüntü olarak ayarlanır. Bu özellik öğesi sözdizimi bir örnektir.

[!code-xaml[PropertiesOvwSupport#PESyntaxProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml#pesyntaxproperty)]

### <a name="setting-properties-in-code"></a>Kodda özellikleri ayarlama
 Bağımlılık özelliği değerlerini kodda ayarlamak genellikle CLR "sarıcı" tarafından açığa çıkarılan ayarlanmış uygulamaya yapılan bir çağrıdır.

[!code-csharp[PropertiesOvwSupport#ProceduralPropertySet](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml.cs#proceduralpropertyset)]
[!code-vb[PropertiesOvwSupport#ProceduralPropertySet](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page1.xaml.vb#proceduralpropertyset)]

Bir özellik değeri başlarken de aslında "sarmalayıcı" uygulaması almak için bir çağrıdır:

[!code-csharp[PropertiesOvwSupport#ProceduralPropertyGet](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml.cs#proceduralpropertyget)]
 [!code-vb[PropertiesOvwSupport#ProceduralPropertyGet](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page1.xaml.vb#proceduralpropertyget)]

Ayrıca özellik sistemi <xref:System.Windows.DependencyObject.GetValue%2A> API'lerini <xref:System.Windows.DependencyObject.SetValue%2A> ve doğrudan arayabilirsiniz. Varolan özellikleri kullanıyorsanız (sarmalayıcılar daha kullanışlıdır ve geliştirici araçları için özelliğin daha iyi pozanması sağlar) genellikle gerekli değildir, ancak API'leri doğrudan çağırmak belirli senaryolar için uygundur.

Özellikler XAML'de de ayarlanabilir ve daha sonra kod la kod arkasında erişilebilir. Ayrıntılar için [WPF'de Kod Arkası ve XAML'ye](code-behind-and-xaml-in-wpf.md)bakın.

## <a name="property-functionality-provided-by-a-dependency-property"></a>Bağımlılık özelliği tarafından sağlanan özellik işlevselliği
Bağımlılık özelliği, bir alan tarafından desteklenen bir özelliğin aksine, bir özelliğin işlevselliğini genişleten işlevsellik sağlar. Genellikle, bu tür işlevler aşağıdaki belirli özelliklerden birini temsil eder veya destekler:

- [Kaynaklar](#resources)

- [Veri bağlama](#data-binding)

- [Stiller](#styles)

- [Animasyonlar](#animations)

- [Meta veri geçersiz kılar](#metadata-overrides)

- [Özellik değeri devralma](#property-value-inheritance)

- [WPF Designer entegrasyonu](#wpf-designer-integration)

### <a name="resources"></a>Kaynaklar
Bağımlılık özelliği değeri bir kaynağa başvurarak ayarlanabilir. Kaynaklar genellikle bir sayfa `Resources` kökü öğesinin veya uygulamanın özellik değeri olarak belirtilir (bu konumlar kaynağa en kolay erişimi sağlar). Aşağıdaki örnekte, bir <xref:System.Windows.Media.SolidColorBrush> kaynağın nasıl tanımlanılıgı gösterilmektedir.

[!code-xaml[PropertiesOvwSupport#ResourcesResource](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page2.xaml#resourcesresource)]

Kaynak tanımlandıktan sonra, kaynağa başvuruyapabilir ve bir özellik değeri sağlamak için kullanabilirsiniz:

[!code-xaml[PropertiesOvwSupport#ResourcesReference](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page2.xaml#resourcesreference)]

Bu özel kaynak Dinamik [Kaynak Biçimlendirme Uzantısı](dynamicresource-markup-extension.md) olarak başvurur (WPF XAML'de statik veya dinamik kaynak başvurusu kullanabilirsiniz). Dinamik bir kaynak başvurusu kullanmak için bir bağımlılık özelliğine ayarlıyor olmalısınız, bu nedenle özellikle WPF özellik sistemi tarafından etkinleştirilen dinamik kaynak başvurusu kullanımıdır. Daha fazla bilgi için [Bkz. XAML Kaynakları.](xaml-resources.md)

> [!NOTE]
> Kaynaklar yerel bir değer olarak kabul edilir, bu da başka bir yerel değer ayarlarsanız kaynak başvuruyu ortadan kaldıracağınız anlamına gelir. Daha fazla bilgi için Bağımlılık [Özelliği Değeri Önceliği'ne](dependency-property-value-precedence.md)bakın.

### <a name="data-binding"></a>Veri bağlama
Bağımlılık özelliği, veri bağlama yoluyla bir değere başvuruyapabilir. Veri bağlama XAML'de belirli bir biçimlendirme uzantısı <xref:System.Windows.Data.Binding> sözdizimi veya koddaki nesne aracılığıyla çalışır. Veri bağlama ile, son özellik değeri belirleme söylenme zamanına kadar ertelenir ve bu sırada değer bir veri kaynağından elde edilir.

Aşağıdaki örnek, <xref:System.Windows.Controls.ContentControl.Content%2A> XAML'de bildirilen bir bağlama kullanarak bir , özelliği <xref:System.Windows.Controls.Button>ni ayarlar. Bağlama, devralınan bir veri <xref:System.Windows.Data.XmlDataProvider> bağlamı ve bir veri kaynağı (gösterilmez) kullanır. Bağlama nın kendisi, veri kaynağı <xref:System.Windows.Data.Binding.XPath%2A> içinde istenilen kaynak özelliğini belirtir.

[!code-xaml[PropertiesOvwSupport#BasicInlineBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#basicinlinebinding)]

> [!NOTE]
> Bağlamalar yerel bir değer olarak kabul edilir, bu da başka bir yerel değer ayarlarsanız, bağlamayı ortadan kaldıracağınız anlamına gelir. Ayrıntılar için Bkz. [Bağımlılık Özelliği Değeri Önceliği.](dependency-property-value-precedence.md)

Bağımlılık özellikleri veya <xref:System.Windows.DependencyObject> sınıf, veri bağlama <xref:System.ComponentModel.INotifyPropertyChanged> işlemleri için <xref:System.Windows.DependencyObject> kaynak özellik değerinde değişiklik bildirimleri üretmek amacıyla doğal olarak desteklemez. Verileri bağlama hedefine değişiklikleri bildirebilecek veri bağlamada kullanılmak üzere nasıl özellikler oluşturulabileceği hakkında daha fazla bilgi için [bkz.](../data/data-binding-overview.md)

### <a name="styles"></a>Stiller
Stiller ve şablonlar, bağımlılık özelliklerini kullanmak için başlıca motive edici senaryolardan ikisidir. Stiller özellikle uygulamayı [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]tanımlayan özellikleri ayarlamak için yararlıdır. Stiller genellikle XAML'de kaynak olarak tanımlanır. Stiller, genellikle belirli özellikler için "ayarlayıcılar" ve başka bir özelliğin gerçek zamanlı değerine dayalı bir özellik değerini değiştiren "tetikleyiciler" içerdiğinden özellik sistemiyle etkileşime geçer.

Aşağıdaki örnek çok basit bir stil oluşturur (hangi <xref:System.Windows.FrameworkElement.Resources%2A> bir sözlük içinde tanımlanır, gösterilmez), <xref:System.Windows.FrameworkElement.Style%2A> sonra <xref:System.Windows.Controls.Button>doğrudan bir . Stil içindeki ayarlayıcı, <xref:System.Windows.Controls.Control.Background%2A> özelliği yeşile <xref:System.Windows.Controls.Button> doğru şekillendiren bir özellik olarak ayarlar.

[!code-xaml[PropertiesOvwSupport#SimpleStyleDef](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#simplestyledef)]

[!code-xaml[PropertiesOvwSupport#SimpleStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#simplestyle)]

Daha fazla bilgi için [Stil ve Templating'e](../controls/styling-and-templating.md)bakın.

### <a name="animations"></a>Animasyonlar
Bağımlılık özellikleri animasyonlu olabilir. Animasyon uygulandığında ve çalışırken, animasyondeğeri özelliğin sahip olduğu herhangi bir değerden (yerel değer gibi) daha yüksek bir önceliğe göre çalışır.

Aşağıdaki örnek, <xref:System.Windows.Controls.Control.Background%2A> bir <xref:System.Windows.Controls.Button> özellik üzerinde animasyonlar (teknik olarak, <xref:System.Windows.Controls.Control.Background%2A> özellik öğesi sözdizimi <xref:System.Windows.Media.SolidColorBrush> kullanarak <xref:System.Windows.Controls.Control.Background%2A>boş <xref:System.Windows.Media.SolidColorBrush.Color%2A> belirtmek için <xref:System.Windows.Media.SolidColorBrush> animasyonlu , sonra bunun özelliği doğrudan animasyonlu özelliğidir).

[!code-xaml[PropertiesOvwSupport#MiniAnimate](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#minianimate)]

Animasyon özellikleri hakkında daha fazla bilgi için [Animasyona Genel Bakış](../graphics-multimedia/animation-overview.md) ve [Storyboards Genel Bakış'a](../graphics-multimedia/storyboards-overview.md)bakın.

### <a name="metadata-overrides"></a>Meta veri geçersiz kılar
Bağımlılık özelliğini özgün olarak kaydeden sınıftan türettiğinizde, bu özellik için meta verileri geçersiz kılarak bir bağımlılık özelliğinin belirli davranışlarını değiştirebilirsiniz. Meta verileri geçersiz kılmak <xref:System.Windows.DependencyProperty> tanımlayıcıya dayanır. Meta verilerin geçersiz kılınması özelliğin yeniden uygulanmasını gerektirmez. Meta veri değişikliği, özellik sistemi tarafından doğal olarak işlenir; her sınıf, her tür bazında temel sınıflardan devralınan tüm özellikler için ayrı meta verileri barındırabilir.

Aşağıdaki örnek, bağımlılık özelliği <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>için meta verileri geçersiz kılar. Bu özel bağımlılık özelliği meta verileri geçersiz kılmak, temalardan varsayılan stilleri kullanabilen denetimler oluşturan bir uygulama deseninin parçasıdır.

[!code-csharp[PropertiesOvwSupport#OverrideMetadata](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml.cs#overridemetadata)]
[!code-vb[PropertiesOvwSupport#OverrideMetadata](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page3.xaml.vb#overridemetadata)]

Özellik meta verilerini geçersiz kılma veya alma hakkında daha fazla bilgi için Bkz. [Bağımlılık Özelliği Meta verileri.](dependency-property-metadata.md)

### <a name="property-value-inheritance"></a>Özellik değeri devralma
Bir öğe, bir bağımlılık özelliğinin değerini nesne ağacındaki üst öğesinden devralabilir.

> [!NOTE]
> Devralma için hesaplama zamanı bazı performans etkisi olduğundan, tüm bağımlılık özellikleri için genel olarak etkin leştirilmiş değer devralma davranışı. Özellik değeri devralma genellikle belirli bir senaryo özellik değeri devralma uygun olduğunu düşündürmektedir özellikleri için etkinleştirilir. SDK başvurusunda bu bağımlılık özelliği için **Bağımlılık Özelliği Bilgileri** bölümüne bakarak bir bağımlılık özelliğinin devralınıp devralmayacağını belirleyebilirsiniz.

Aşağıdaki örnek, bir bağlama gösterir <xref:System.Windows.FrameworkElement.DataContext%2A> ve önceki bağlama örneğinde gösterilmemiş bağlama nın kaynağını belirten özelliği ayarlar. Alt nesnelerde sonraki bağlamalar kaynak belirtmek gerekmez, onlar üst <xref:System.Windows.FrameworkElement.DataContext%2A> <xref:System.Windows.Controls.StackPanel> nesneden devralınan değeri kullanabilirsiniz. (Alternatif olarak, bir alt nesne bunun yerine <xref:System.Windows.FrameworkElement.DataContext%2A> doğrudan <xref:System.Windows.Data.Binding.Source%2A> kendi <xref:System.Windows.Data.Binding>veya bir belirtmek için seçebilirsiniz , ve kasıtlı olarak kendi bağlayıcıları veri bağlamı için devralınan değeri kullanmayın.)

[!code-xaml[PropertiesOvwSupport#InheritanceContext](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#inheritancecontext)]

Daha fazla bilgi için [Bkz. Özellik Değeri Devralma.](property-value-inheritance.md)

### <a name="wpf-designer-integration"></a>WPF tasarımcı entegrasyonu
Bağımlılık özellikleri olarak uygulanan özelliklere sahip özel bir denetim, Visual Studio desteği için uygun WPF Tasarımcısı'nı alır. Özellikler **penceresi** ile doğrudan ve bağlı bağımlılık özelliklerini yeniden yapılandırabilme özelliği bir örnektir. Daha fazla bilgi için [bkz.](../controls/control-authoring-overview.md)

## <a name="dependency-property-value-precedence"></a>Bağımlılık özelliği değeri önceliği
Bir bağımlılık özelliğinin değerini aldığınızda, wpf özellik sistemine katılan diğer özellik tabanlı girişlerden herhangi biri aracılığıyla bu özellik üzerinde ayarlanmış bir değer elde etme potansiyeline sahip olursunuz. Bağımlılık özelliği değeri önceliği, özelliklerin değerlerini nasıl elde ettiğine dair çeşitli senaryoların öngörülebilir bir şekilde etkileşime girebilmesi için vardır.

Aşağıdaki örneği inceleyin. Örnek, tüm düğmeler ve özellikleri <xref:System.Windows.Controls.Control.Background%2A> için geçerli olan bir stil içerir, ancak daha <xref:System.Windows.Controls.Control.Background%2A> sonra yerel olarak ayarlanmış bir değere sahip bir düğme de belirtir.

> [!NOTE]
> SDK belgeleri bağımlılık özelliklerini tartışırken ara sıra "yerel değer" veya "yerel olarak ayarlanmış değer" terimlerini kullanır. Yerel olarak ayarlanmış değer, doğrudan koddaki bir nesne örneğinde veya XAML'deki bir öğenin özniteliği olarak ayarlanan bir özellik değeridir.  
  
Prensipte, ilk düğme için özellik iki kez ayarlanır, ancak yalnızca bir değer uygulanır: en yüksek önceliğe sahip değer. Yerel olarak ayarlanmış bir değer en yüksek önceliğe sahiptir (çalışan animasyon hariç, ancak bu örnekte animasyon uygulanmaz) ve böylece ilk düğmedeki arka plan için stil ayarlayıcı değeri yerine yerel olarak ayarlanmış değer kullanılır. İkinci düğmenin yerel değeri yoktur (ve stil ayarlayıcısından daha yüksek önceliğe sahip başka bir değer yoktur) ve böylece bu düğmedeki arka plan stil ayarlayıcısından gelir.

[!code-xaml[PropertiesOvwSupport#MiniPrecedence](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#miniprecedence)]  

### <a name="why-does-dependency-property-precedence-exist"></a>Bağımlılık özelliği önceliği neden var?
Tipik olarak, stillerin her zaman uygulanmasını ve tek bir öğenin yerel olarak ayarlanmış değerini bile gizlemesini istemezsiniz (aksi takdirde, stilleri veya öğeleri genel olarak kullanmak çok zor olur). Bu nedenle, stiller gelen değerler yerel olarak ayarlanmış bir değerden daha düşük bir emsalde çalışır. Bağımlılık özelliklerinin daha ayrıntılı bir listesi ve bağımlılık özelliğinin etkin değerinin nereden gelebileceği [için](dependency-property-value-precedence.md)bkz.

> [!NOTE]
> WPF öğelerinde tanımlı bağımlılık özellikleri olmayan birkaç özellik vardır. Ve büyük ölçüde, özellikler yalnızca özellik sisteminin etkinleştirdığı senaryolardan en az birini desteklemesi gerektiğinde bağımlılık özellikleri olarak uygulanmıştır: veri bağlama, şekillendirme, animasyon, varsayılan değer desteği, devralma, ekli özellikler veya geçersiz leştirme.

## <a name="learning-more-about-dependency-properties"></a>Bağımlılık özellikleri hakkında daha fazla bilgi edinme  

- Ekli özellik, XAML'de özelleştirilmiş bir sözdizimini destekleyen bir özellik türüdür. Ekli bir özellik genellikle ortak bir dil çalışma zamanı (CLR) özelliği ile 1:1 yazışmaları yoktur ve mutlaka bir bağımlılık özelliği değildir. Ekli bir özelliğin tipik amacı, üst öğe ve alt öğe sınıf üyeleri listelerinin bir parçası olarak bu özelliğe sahip olmasa bile, alt öğelerin özellik değerlerini bir üst öğeye bildirmesine izin vermektir. Birincil senaryolardan biri, alt öğelerin ebeveyne nasıl [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]sunulması gerektiğini bildirmesini sağlamaktır; örneğin, bkz. <xref:System.Windows.Controls.DockPanel.Dock%2A> <xref:System.Windows.Controls.Canvas.Left%2A> Ayrıntılar için bkz: [Ekteki Özellikler Genel Bakış.](attached-properties-overview.md)

- Bileşen geliştiricileri veya uygulama geliştiricileri, veri bağlama veya stil desteği gibi yetenekleri etkinleştirmek veya geçersizleştirme ve değer zorlama desteği için kendi bağımlılık özelliklerini oluşturmak isteyebilir. Ayrıntılar için Bkz. [Özel Bağımlılık Özellikleri.](custom-dependency-properties.md)

- Bağımlılık özellikleri genellikle ortak özellikler olarak kabul edilmelidir, erişilebilir veya en azından bir örnek erişimi olan herhangi bir arayan tarafından bulunabilir. Daha fazla bilgi için Bkz. [Bağımlılık Özelliği Güvenliği.](dependency-property-security.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Bağımlılık Özellikleri](custom-dependency-properties.md)
- [Salt Okunur Bağımlılık Özellikleri](read-only-dependency-properties.md)
- [XAML'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [WPF Mimarisi](wpf-architecture.md)
