---
title: Bağımlılık özelliklerine genel bakış
description: WPF özellik sistemi tarafından desteklenen bir özellik, bir bağımlılık özelliği olarak bilinir. Bu genel bakışta, WPF özellik sistemi ve bağımlılık özelliği yeteneklerini açıklar.
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
ms.openlocfilehash: 483710281feafdf97cfef9b72a67af035dcf0efa
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67860167"
---
# <a name="dependency-properties-overview"></a>Bağımlılık özelliklerine genel bakış

Windows Presentation Foundation (WPF), türün genişletmek için kullanılan hizmetleri kümesi sağlar [özelliği](../../../standard/base-types/common-type-system.md#Properties). Toplu olarak, bu hizmetleri genellikle WPF özellik sistemi adlandırılır. WPF özellik sistemi tarafından desteklenen bir özellik, bir bağımlılık özelliği olarak bilinir. Bu genel bakışta, WPF özellik sistemi ve bağımlılık özelliği yeteneklerini açıklar. Bu, XAML ve kod mevcut bağımlılık özellikleri kullanmayı içerir. Bu genel bakışta, bağımlılık özellikleri, bağımlılık özelliği meta verisi ve kendi bağımlılık özelliği özel bir sınıf içinde oluşturma gibi özelleştirilmiş yönlerini da tanıtılmaktadır.

## <a name="prerequisites"></a>Önkoşullar
Bu konuda, nesne odaklı programlama ve .NET tür sistemi bazı temel bilgi sahibi olduğunuzu varsayar. Bu konudaki örnekleri izlemek için ayrıca XAML anlamak ve WPF uygulamalarının nasıl yazılacağı bilmeniz. Daha fazla bilgi için [izlenecek yol: İlk WPF Masaüstü Uygulamam](../getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
## <a name="dependency-properties-and-clr-properties"></a>Bağımlılık özellikleri ve CLR Özellikleri
 WPF içinde özellikleri genellikle standart .NET sunulan [özellikleri](../../../standard/base-types/common-type-system.md#Properties). Bir temel düzeyde, bu özellikleri ile doğrudan etkileşim ve bağımlılık özelliği olarak uygulanan asla bilemezsiniz. Bu özelliklerden yararlanabilmeniz ancak bazı veya tüm özelliklerini WPF özellik sistemi ile tanıdık olmanız gerekir.

Bağımlılık özellikleri amacı, diğer girişler değerine göre bir özelliğin değerini hesaplamak için bir yol sağlamaktır. Bu, diğer girişler içerebilir temalar ve kullanıcı tercihi gibi sistem özellikleri, veri bağlama ve animasyonları/film şeritleri, kaynakları ve stilleri ya da bilinen değerleri gibi çoklu kullanım şablonları gibi tam zamanında özellik belirleme mekanizması diğer öğeleri öğe ağacında üst-alt ilişkileri. Ayrıca, bir bağımlılık özelliği, kendi içinde doğrulama, varsayılan değerleri, diğer özelliklere değişikliklerini izleme geri aramaları ve büyük olasılıkla çalışma zamanı bilgilerini temel alarak özellik değerlerini zorlayacak bir sistem sağlamak için uygulanabilir. Türetilen sınıflar Ayrıca, bağımlılık özelliği meta verisi geçersiz kılmak yerine özellikleri mevcut veya yeni özellikleri oluşturma gerçek uygulama geçersiz kılma mevcut özelliğin belirli özelliklerinden bazıları değiştirebilirsiniz.

SDK Başvurusu'nda, bir bağımlılık özelliği tarafından yönetilen başvuru sayfasında bu özellik için bağımlılık özelliği bilgileri bölümü varlığını özelliği tanımlayabilirsiniz. Bağımlılık özelliği bilgileri bölümüne bir bağlantı içerir <xref:System.Windows.DependencyProperty> tanımlayıcı alan, bağımlılık özelliği için ve ayrıca bu özellik, sınıf başına geçersiz kılma bilgilerini ve diğer ayrıntılar için ayarlanmış olan meta veri seçeneklerin listesini içerir.

## <a name="dependency-properties-back-clr-properties"></a>Bağımlılık özellikleri, CLR özelliklerini yedekler.
Bağımlılık özellikleri ve WPF özellik sistemi standart deseni ile özel bir alan özelliği yedekleme için alternatif bir uygulama olarak bir özelliği yedekleyen bir türü sağlayarak özellik işlevselliğini genişletir. Bu tür adı <xref:System.Windows.DependencyProperty>. WPF özellik sistemi tanımlayan bir önemli türü <xref:System.Windows.DependencyObject>. <xref:System.Windows.DependencyObject> kaydolun ve bir bağımlılık özelliği kendi temel sınıf tanımlar.

Bağımlılık özellikleri ile kullanılan terimleri listelenmektedir:

- **Bağımlılık özelliği:** Tarafından desteklenen bir özellik bir <xref:System.Windows.DependencyProperty>.

- **Bağımlılık özelliği tanımlayıcı:** A <xref:System.Windows.DependencyProperty> dönüş değeri olarak bir bağımlılık özelliği kaydederken elde ve daha sonra bir sınıfın statik bir üye depolanan bir örneği. Bu tanımlayıcı, parametre olarak WPF özellik sistemi ile etkileşim kuran API'lerden oluşan bir çoğu için kullanılır.

- **CLR "sarmalayıcı":** Gerçek alın ve uygulamaları özelliği ayarlayın. Bu uygulamaların içindeki kullanarak bağımlılık özelliği tanımlayıcı dahil edilip derecelendirilir <xref:System.Windows.DependencyObject.GetValue%2A> ve <xref:System.Windows.DependencyObject.SetValue%2A> çağrıları, bu nedenle WPF özellik sistemi kullanarak bir özellik için destek sağlama.

Aşağıdaki örnek tanımlar `IsSpinning` bağımlılık özelliği ve arasındaki ilişkiyi gösteren <xref:System.Windows.DependencyProperty> yedekleyen bu özellik için tanımlayıcı.

[!code-csharp[PropertiesOvwSupport#DPFormBasic](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#dpformbasic)]
[!code-vb[PropertiesOvwSupport#DPFormBasic](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#dpformbasic)]  
  
Özellik ve yedekleme adlandırma kuralının <xref:System.Windows.DependencyProperty> alan önemlidir. Alanın adını her zaman soneki ile özellik adıdır `Property` eklenir. Bu kuralı ve nedenleri hakkında daha fazla bilgi için bkz: [özel bağımlılık özellikleri](custom-dependency-properties.md).  

## <a name="setting-property-values"></a>Özellik değerlerini ayarlama
Kod veya XAML özellikleri ayarlayabilirsiniz.

### <a name="setting-property-values-in-xaml"></a>XAML içinde özellik değerlerini ayarlama 
Aşağıdaki XAML örnek kırmızı bir düğme arka plan rengini belirtir. Bu örnekte, bir XAML özniteliği için basit bir dize değeri olduğu bir WPF türü WPF XAML ayrıştırıcı tarafından türe dönüştürülüp bir servis talebi gösterilmektedir (bir <xref:System.Windows.Media.Color>, sunar bir <xref:System.Windows.Media.SolidColorBrush>) oluşturulan kodda.

[!code-xaml[PropertiesOvwSupport#MostBasicProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml#mostbasicproperty)]

XAML sözdizimi çeşitli özelliklerini ayarlamak için destekler. Belirli bir özellik için kullanılmak üzere hangi söz dizimi, bir tür dönüştürücüsü varlığını gibi diğer faktörlere yanı sıra bir özelliği kullanan bir değer türü bağlıdır. XAML söz dizimi özellik ayarı hakkında daha fazla bilgi için bkz. [XAML genel bakış (WPF)](xaml-overview-wpf.md) ve [içinde XAML söz dizimi ayrıntı](xaml-syntax-in-detail.md).

Öznitelik olmayan söz dizimi bir örnek olarak, aşağıdaki XAML örnek başka bir düğme arka plan gösterir. Bu kez basit düz renk ayarlamak yerine, arka plan o yansıma ve iç içe öğe öznitelik olarak belirtilen görüntünün kaynağı temsil eden bir öğe ile bir görüntü için ayarlanır. Bu özellik öğesi sözdizimine örneğidir.

[!code-xaml[PropertiesOvwSupport#PESyntaxProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml#pesyntaxproperty)]

### <a name="setting-properties-in-code"></a>Kodda özelliklerini ayarlama
 Bağımlılık kod içinde özellik değerlerini ayarlamak, genellikle bir çağrı tarafından kullanıma sunulan kümesi uygulamaya [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] "sarmalayıcı".

[!code-csharp[PropertiesOvwSupport#ProceduralPropertySet](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml.cs#proceduralpropertyset)]
[!code-vb[PropertiesOvwSupport#ProceduralPropertySet](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page1.xaml.vb#proceduralpropertyset)]

Özellik değerini alma get "sarmalayıcı" uygulaması bir çağrı gibidir:

[!code-csharp[PropertiesOvwSupport#ProceduralPropertyGet](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml.cs#proceduralpropertyget)]
 [!code-vb[PropertiesOvwSupport#ProceduralPropertyGet](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page1.xaml.vb#proceduralpropertyget)]

Ayrıca, özellik sistemi API'leri çağırabilirsiniz <xref:System.Windows.DependencyObject.GetValue%2A> ve <xref:System.Windows.DependencyObject.SetValue%2A> doğrudan. Bu (sarmalayıcılar daha kullanışlı ve daha iyi riskini özelliği sağlamak için geliştirici araçları) mevcut özellikleri kullandığınız, ancak API'lerini doğrudan çağırmak belirli senaryolar için uygundur, genellikle gerekli değildir.

Özellikleri, ayrıca XAML içinde ayarlayın ve daha sonra kodu, arka plan kod aracılığıyla erişilebilir. Ayrıntılar için bkz [arka plan kod ve WPF XAML](code-behind-and-xaml-in-wpf.md).

## <a name="property-functionality-provided-by-a-dependency-property"></a>Bağımlılık özelliği tarafından sağlanan özellik işlevselliği
Bağımlılık özelliği, bir alan tarafından yedeklenen bir özelliğe karşı işlevselliğini genişleten işlevselliği sağlar. Genellikle, bu tür işlevleri temsil eder veya aşağıdaki belirli özellikler destekler:

- [Kaynakları](#resources)

- [Veri bağlama](#data-binding)

- [Stiller](#styles)

- [Animasyonlar](#animations)

- [Meta verileri geçersiz kılar](#metadata-overrides)

- [Özellik değeri kalıtımı](#property-value-inheritance)

- [WPF Tasarımcısı tümleştirme](#wpf-designer-integration)

### <a name="resources"></a>Kaynaklar
Bir kaynak başvurarak bir bağımlılık özelliği değer ayarlanabilir. Kaynak olarak belirtilen genellikle `Resources` sayfa kök öğesinin ya da (Bu konumlar, kaynak en kullanışlı erişimi etkinleştirme) uygulamasının özellik değeri. Aşağıdaki örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.Media.SolidColorBrush> kaynak.

[!code-xaml[PropertiesOvwSupport#ResourcesResource](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page2.xaml#resourcesresource)]

Kaynak tanımlandıktan sonra referans ve özellik değeri sağlamak için kullanın:

[!code-xaml[PropertiesOvwSupport#ResourcesReference](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page2.xaml#resourcesreference)]

Bu kaynak olarak başvurulan bir [DynamicResource işaretleme uzantısı](dynamicresource-markup-extension.md) (WPF XAML içinde bir statik veya dinamik kaynak başvurusu kullanabilirsiniz). WPF özelliği sistem tarafından etkinleştirilen özellikle dinamik kaynak başvuru kullanımı, bu nedenle dinamik kaynak başvurusu kullanmak için bir bağımlılık özelliği için ayarlamanız gerekir. Daha fazla bilgi için [XAML kaynakları](xaml-resources.md).

> [!NOTE]
> Kaynakları başka bir yerel değeri ayarlarsanız, kaynak başvurusu ortadan kaldıracak anlamına gelir. bir yerel değer olarak kabul edilir. Daha fazla bilgi için [bağımlılık özelliği değer önceliği](dependency-property-value-precedence.md).

### <a name="data-binding"></a>Veri bağlama
Bağımlılık özelliği değer veri bağlama aracılığıyla başvurabilirsiniz. Veri XAML içinde özel biçimlendirme uzantısı sözdizimi aracılığıyla bağlama veya <xref:System.Windows.Data.Binding> kod nesnesi. Veri bağlama ile son özellik değeri belirleme, çalışma zamanı, aynı zamanda bir veri kaynağından alınan değeri kadar ertelenir.

Aşağıdaki örnek kümeleri <xref:System.Windows.Controls.ContentControl.Content%2A> özelliği için bir <xref:System.Windows.Controls.Button>, XAML içinde bildirilen bir bağlama işlemini kullanma. Devralınan veri bağlamından bağlama kullanır ve bir <xref:System.Windows.Data.XmlDataProvider> veri kaynağı (gösterilmemiştir). Bağlama tarafından istenen kaynak özelliği belirtir <xref:System.Windows.Data.Binding.XPath%2A> içinde veri kaynağı.

[!code-xaml[PropertiesOvwSupport#BasicInlineBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#basicinlinebinding)]

> [!NOTE]
> Bağlamaları yerel başka bir değer ayarlarsanız, bağlama ortadan kaldıracak anlamına gelen bir yerel değer olarak kabul edilir. Ayrıntılar için bkz [bağımlılık özelliği değer önceliği](dependency-property-value-precedence.md).

Bağımlılık özellikleri veya <xref:System.Windows.DependencyObject> sınıfı, özgün olarak desteklemez <xref:System.ComponentModel.INotifyPropertyChanged> değişiklik bildirimleri üretme amacıyla <xref:System.Windows.DependencyObject> kaynak veri bağlama işlemleri için özellik değeri. Veri bağlama kullanımda değişiklikleri bir veri bağlama hedefine bildirebilirsiniz için özelliklerin nasıl oluşturulacağı hakkında daha fazla bilgi için bkz. [Data Binding Overview](../data/data-binding-overview.md).

### <a name="styles"></a>Stilleri
Stilleri ve şablonları kullanarak bağımlılık özellikleri için baş motive edici temel senaryolar ikisidir. Stiller uygulama tanımlayan özellikleri ayarlamak için özellikle yararlı [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Stilleri, genellikle XAML kaynak olarak tanımlanır. Genellikle belirli özelliklerin yanı sıra, "başka bir özellik için gerçek zamanlı değere göre bir özellik değerini değiştirmek Tetikleyicileri" için "ayarlayıcılar" içerdiğinden stilleri özellik sistemi ile etkileşim kurun.

Aşağıdaki örnekte çok basit bir stil oluşturur (hangi içinde tanımlanan bir <xref:System.Windows.FrameworkElement.Resources%2A> gösterilmez, sözlük), ardından o stilin doğrudan uygular <xref:System.Windows.FrameworkElement.Style%2A> özelliği için bir <xref:System.Windows.Controls.Button>. Stil kümelerinin ayarlandığı <xref:System.Windows.Controls.Control.Background%2A> özelliği için bir stil uygulanmış <xref:System.Windows.Controls.Button> yeşil.

[!code-xaml[PropertiesOvwSupport#SimpleStyleDef](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#simplestyledef)]

[!code-xaml[PropertiesOvwSupport#SimpleStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#simplestyle)]

Daha fazla bilgi için [stil ve şablon oluşturma](../controls/styling-and-templating.md).

### <a name="animations"></a>Animasyonlar
Bağımlılık özellikleri için hareketli. Bir animasyon uygulanan ve çalışan animasyonlu değer, aksi takdirde özelliğine sahip herhangi bir değer (örneğin, yerel bir değer) daha yüksek bir önceliğe çalışır.

Aşağıdaki örnek canlandırır <xref:System.Windows.Controls.Control.Background%2A> üzerinde bir <xref:System.Windows.Controls.Button> özelliği (teknik olarak <xref:System.Windows.Controls.Control.Background%2A> boş belirtmek için özellik öğesi sözdizimini kullanarak bir animasyon görünür <xref:System.Windows.Media.SolidColorBrush> olarak <xref:System.Windows.Controls.Control.Background%2A>, sonra <xref:System.Windows.Media.SolidColorBrush.Color%2A> , söz konusu özelliği <xref:System.Windows.Media.SolidColorBrush> doğrudan animasyonlu özelliktir).

[!code-xaml[PropertiesOvwSupport#MiniAnimate](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#minianimate)]

Özellikler animasyon ekleme ile ilgili daha fazla bilgi için bkz. [animasyona genel bakış](../graphics-multimedia/animation-overview.md) ve [görsel taslaklara genel bakış](../graphics-multimedia/storyboards-overview.md).

### <a name="metadata-overrides"></a>Meta verileri geçersiz kılar
Bağımlılık özelliği ilk olarak kaydeder sınıfından türetilen olduğunda bu özellik için meta veriler geçersiz kılarak bir bağımlılık özelliği belirli davranışları değiştirebilirsiniz. Meta verileri geçersiz kılma dayanır <xref:System.Windows.DependencyProperty> tanımlayıcısı. Meta verileri geçersiz kılma özelliği yeniden uygulama gerektirmez. Meta veri değişikliği yerel olarak özellik sistemi tarafından işlenir; her sınıf, büyük olasılıkla türü başına temelinde temel sınıflardan devralınır tüm özellikler için ayrı ayrı meta verileri içerir.

Aşağıdaki örnek, bir bağımlılık özelliği için meta verileri geçersiz kılar <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>. Bu belirli bir bağımlılık özelliği meta verileri geçersiz kılma varsayılan tema stillerinden kullanabileceğiniz denetimler oluşturan bir uygulama modeli, parçasıdır.

[!code-csharp[PropertiesOvwSupport#OverrideMetadata](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml.cs#overridemetadata)]
[!code-vb[PropertiesOvwSupport#OverrideMetadata](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page3.xaml.vb#overridemetadata)]

Geçersiz kılma veya özellik meta verileri alma hakkında daha fazla bilgi için bkz. [bağımlılık özelliği meta verisi](dependency-property-metadata.md).

### <a name="property-value-inheritance"></a>Özellik değeri kalıtımı
Bir öğe, bir bağımlılık özelliğinin değeri, nesne ağacında üst öğesinden devralabilir.

> [!NOTE]
> Özellik değeri devralma davranışı genel hesaplama zamanı devralma için bazı performans etkisi sahip olmadığından tüm bağımlılık özellikleri için etkinleştirilmedi. Özellik değeri kalıtımı genellikle yalnızca özellik değeri kalıtımı uygun olduğunu, belirli bir senaryo burada önerdiği özellikler için etkindir. Bağımlılık özelliği bakarak devralıp devralmadığını belirler **bağımlılık özelliği bilgileri** SDK başvurusu, bağımlılık özelliği için bölüm.

Aşağıdaki örnek bir bağlama gösterir ve ayarlar <xref:System.Windows.FrameworkElement.DataContext%2A> önceki bağlama örnekte gösterilmeyen bağlama kaynağını belirten özelliği. Sonraki tüm alt nesneleri bağlarında kaynağını belirtmek gerekmez, devralınan değerden kullandıkları <xref:System.Windows.FrameworkElement.DataContext%2A> üst <xref:System.Windows.Controls.StackPanel> nesne. (Alternatif olarak, bir alt nesnesi yerine doğrudan kendi seçebilir <xref:System.Windows.FrameworkElement.DataContext%2A> veya <xref:System.Windows.Data.Binding.Source%2A> içinde <xref:System.Windows.Data.Binding>ve veri bağlamalarını bağlamının devralınan değerden kasıtlı olarak kullanmamayı.)

[!code-xaml[PropertiesOvwSupport#InheritanceContext](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#inheritancecontext)]

Daha fazla bilgi için [özellik değeri kalıtımı](property-value-inheritance.md).

### <a name="wpf-designer-integration"></a>WPF Tasarımcısı tümleştirme
Bağımlılık özellikleri uygun alacak şekilde uygulanan özelliklere sahip özel bir denetim [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] destekler. Bir örnektir doğrudan ve ekli bağımlılık özellikleri ile düzenleme yeteneğini **özellikleri** penceresi. Daha fazla bilgi için [denetim yazmaya genel bakış](../controls/control-authoring-overview.md).

## <a name="dependency-property-value-precedence"></a>Bağımlılık özelliği değer önceliği
Bir bağımlılık özelliğinin değeri elde ettiğinizde, potansiyel olarak bu özellik, WPF özelliği sisteme katılan diğer özellik tabanlı girişleri herhangi biri üzerinden ayarlanmış bir değer elde etme. Bağımlılık özelliği değer önceliği, böylece çeşitli senaryoları özellikleri değerlerini nasıl elde etmek için tahmin edilebilir bir şekilde etkileşim bulunmaktadır.

Aşağıdaki örnek göz önünde bulundurun. Tüm düğmeleri uygulanan stil örnek içerir ve bunların <xref:System.Windows.Controls.Control.Background%2A> özellikleri, ardından bir düğme ile yerel olarak ayarlanmış belirten <xref:System.Windows.Controls.Control.Background%2A> değeri.

> [!NOTE]
> SDK Belgeleri kullanır "yerel value" veya "yerel olarak ayarlanmış. değer" bazen bağımlılık özellikleri tartışırken. Yerel olarak ayarlanmış doğrudan nesne örneği kodda veya XAML bir öğedeki bir öznitelik olarak ayarlanmış bir özellik değeri bir değerdir.  
  
İlk düğme için bir ilke özelliği iki kez ayarlanır, ancak yalnızca bir değer geçerlidir: önceliği en yüksek değeri. Yerel olarak ayarlanmış değeri en yüksek önceliğe sahiptir (dışında çalışan bir animasyon, ancak hiçbir animasyon Bu örnekte uygulanır) ve bu nedenle yerel olarak ayarlanmış değeri arka planının ilk düğmeye stil ayarlayıcı değer yerine kullanılır. Yerel değer (ve style setter daha yüksek bir önceliğe sahip başka bir değer) İkinci düğmeye sahip ve bu nedenle arka planda bu düğmeyi stil ayarlayıcı gelir.

[!code-xaml[PropertiesOvwSupport#MiniPrecedence](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#miniprecedence)]  

### <a name="why-does-dependency-property-precedence-exist"></a>Bağımlılık özelliği önceliği neden var mı?
Genellikle, her zaman uygulamak ve bile yerel olarak ayarlanmış saklamasını stilleri istemezsiniz tek bir öğenin değeri (Aksi takdirde, bu stilleri veya öğeleri genel kullanmak oldukça zor olurdu). Bu nedenle, yerel olarak ayarlanmış'den daha düşük öncelikte stillerden gelen değerleri çalışması değeri. Bağımlılık özellikleri ve bağımlılık özelliği etkin bir değerin nereden geldiği, daha kapsamlı bir listesi için bkz: [bağımlılık özelliği değer önceliği](dependency-property-value-precedence.md).

> [!NOTE]
> Bağımlılık özellikleri olmayan WPF öğeleri üzerinde tanımlanan özellikler vardır. Yalnızca en az bir özellik sistemi tarafından etkinleştirilen senaryoları desteklemek için ihtiyaçları zamanki özellikleri bağımlılık özellikleri büyük uygulandığına: veri bağlama, stil, animasyon, varsayılan değer desteği, devralma, iliştirilmiş özellikler, veya geçersiz kılma.

## <a name="learning-more-about-dependency-properties"></a>Bağımlılık özellikleri hakkında daha fazla bilgi  

- Ekli özelliği, XAML içinde özel bir söz dizimi destekleyen özelliği türüdür. Ekli özelliği ile 1:1 ilişkiyi sık olmayan bir [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] özelliği ve mutlaka bir bağımlılık özelliği değil. Üst öğe ve alt öğe sınıfı üyeleri listeleri bir parçası olarak bu özellik her ikisi de sahip olsa bile ekli özellik tipik amacı alt öğeleri bir üst öğesi için özellik değerlerini bildirmek için izin vermektir. Alt öğeleri nasıl bunlar içinde erişemediklerinde sunulması gereken üst bildirmek üzere etkinleştirmek için bir birincil senaryodur [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]; bir örnek için bkz: <xref:System.Windows.Controls.DockPanel.Dock%2A> veya <xref:System.Windows.Controls.Canvas.Left%2A>. Ayrıntılar için bkz [ekli özelliklere genel bakış](attached-properties-overview.md).

- Bileşen geliştiriciler veya uygulama geliştiriciler, veri bağlama veya stilleri desteği gibi özellikleri etkinleştirmek ya da geçersiz kılma ve değer baskı desteklemek için kendi bağımlılık özelliği oluşturmak isteyebilirsiniz. Ayrıntılar için bkz [özel bağımlılık özellikleri](custom-dependency-properties.md).

- Bağımlılık özellikleri genellikle ortak özellikler, erişilebilir olmasını düşünülmelidir veya bir örneğine erişimi olan en az bir çağıran tarafından bulunabilir. Daha fazla bilgi için [bağımlılık özelliği güvenliği](dependency-property-security.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Bağımlılık Özellikleri](custom-dependency-properties.md)
- [Salt Okunur Bağımlılık Özellikleri](read-only-dependency-properties.md)
- [XAML'ye Genel Bakış (WPF)](xaml-overview-wpf.md)
- [WPF Mimarisi](wpf-architecture.md)
