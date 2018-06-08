---
title: Bağımlılık özelliklerine genel bakış
description: WPF özellik sistemi tarafından yedeklenen bir özellik bağımlılık özelliği olarak bilinir. Bu genel bakışta, WPF özellik sistemi ve bağımlılık özelliği özelliklerini açıklar.
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
ms.openlocfilehash: 36370eb54e75df9bf2bf8eb9e073bbbee995e287
ms.sourcegitcommit: d955cb4c681d68cf301d410925d83f25172ece86
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34827013"
---
# <a name="dependency-properties-overview"></a>Bağımlılık özelliklerine genel bakış

Windows Presentation Foundation (WPF) sağlayan bir tür işlevselliğini genişletmek için kullanılan hizmetleri kümesi [özelliği](../../../standard/base-types/common-type-system.md#Properties). Topluca, bu hizmetleri genellikle WPF özellik sistemi olarak adlandırılır. WPF özellik sistemi tarafından yedeklenen bir özellik bağımlılık özelliği olarak bilinir. Bu genel bakışta, WPF özellik sistemi ve bağımlılık özelliği özelliklerini açıklar. XAML ve kod varolan bağımlılık özellikleri kullanmayı içerir. Bu genel bakışta, aynı zamanda özelleştirilmiş yönlerini bağımlılık özelliği meta verileri ve özel bir sınıf içinde kendi bağımlılık özelliği yaratmayı gibi bağımlılık özellikleri sunar.

## <a name="prerequisites"></a>Önkoşullar
Bu konu, .NET tür sistemi ve nesne odaklı programlama bazı temel bilgiye sahip olduğunu varsayar. Bu konudaki örnekleri takip etmek için ayrıca XAML anlamak ve WPF uygulamaların nasıl yazılacağını bilmeniz gerekir. Daha fazla bilgi için bkz: [gözden geçirme: ilk WPF Masaüstü Uygulamam](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
## <a name="dependency-properties-and-clr-properties"></a>Bağımlılık özellikleri ve CLR Özellikleri
 WPF içinde özellikleri genellikle standart .NET sunulan [özellikleri](../../../standard/base-types/common-type-system.md#Properties). Temel düzeyde, bu özellikleri ile doğrudan etkileşim ve hiçbir zaman bir bağımlılık özelliği olarak uygulanan biliyorsanız. Bu özelliklerden yararlanabilmeniz ancak, bazı veya tüm WPF özellik sistemi özelliklerini tanıdık olmanız gerekir.

Bağımlılık özellikleri amacı, diğer girişlerini değere göre bir özelliğin değerini hesaplamak için bir yol sağlamaktır. Bu diğer girişler içerebilir temalar ve kullanıcı tercihi gibi sistem özellikleri, veri bağlama ve animasyonları/film şeritleri, kaynakları ve stiller ya da bilinen değerleri gibi çoklu kullanım şablonları gibi tam zamanında özellik belirleme mekanizması öğe ağacındaki diğer öğelerle üst-alt ilişkisi. Ayrıca, bir bağımlılık özelliği, kendi içinde yer alan doğrulama, varsayılan değerler, diğer özellikleri değişiklikleri izlemek geri aramalar ve olası çalışma zamanı bilgilere dayanarak özellik değerlerini coerce bir sistem sağlamak üzere uygulanabilir. Türetilen sınıflar, ayrıca bağımlılık özelliği meta verileri geçersiz kılma yerine tarafından özellikleri varolan veya yeni özellikleri oluşturma gerçek uygulamayı geçersiz kılma mevcut bir özellik belirli bazı özelliklerini değiştirebilirsiniz.

SDK Başvurusu'nda, bağımlılık özelliği bu özellik için yönetilen başvuru sayfasındaki bağımlılık özelliği bilgileri bölümünden varlığını tarafından hangi özelliktir tanımlayabilirsiniz. Bağımlılık özelliği bilgileri bölümüne bir bağlantı içerir <xref:System.Windows.DependencyProperty> tanımlayıcı alan bu bağımlılık özelliği için ve ayrıca bu özellik, sınıf başına geçersiz kılma bilgilerini ve diğer ayrıntılar için ayarlanan meta verileri seçeneklerinin bir listesini içerir.

## <a name="dependency-properties-back-clr-properties"></a>Bağımlılık özellikleri, CLR özelliklerini yedekler.
Bağımlılık özellikleri ve WPF özellik sistemi özellik işlevselliğini özel alan özelliğiyle yedekleme standart deseni için alternatif bir uygulama olarak bir özellik yedekleyen bir tür sağlayarak genişletir. Bu tür adı <xref:System.Windows.DependencyProperty>. WPF özellik sistemi tanımlar bir önemli tür <xref:System.Windows.DependencyObject>. <xref:System.Windows.DependencyObject> kaydeden ve bir bağımlılık özelliği kendi temel sınıf tanımlar.

Bağımlılık özellikleri ile kullanılan terimleri listelenmektedir:

- **Bağımlılık özelliği:** tarafından yedeklenen bir özelliği bir <xref:System.Windows.DependencyProperty>.

- **Bağımlılık özelliği tanımlayıcı:** A <xref:System.Windows.DependencyProperty> dönüş değeri olarak bir bağımlılık özelliği kaydederken elde ve statik sınıf üyesi olarak depolanan örneği. Bu tanımlayıcı, WPF özellik sistemi ile etkileşim API'leri birçoğu için parametre olarak kullanılır.

- **CLR "sarmalayıcı":** gerçek alma ve ayarlama özelliği için uygulamaları. Bu uygulamalar içindeki kullanarak bağımlılık özelliği tanımlayıcı dahil <xref:System.Windows.DependencyObject.GetValue%2A> ve <xref:System.Windows.DependencyObject.SetValue%2A> çağrıları, böylece WPF özellik sistemi kullanan özellik için destek sağlama.

Aşağıdaki örnek tanımlar `IsSpinning` bağımlılık özelliği ve ilişkisi gösterilmektedir <xref:System.Windows.DependencyProperty> tanımlayıcısı ile onu yedekleyen özellik.

[!code-csharp[PropertiesOvwSupport#DPFormBasic](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#dpformbasic)]
[!code-vb[PropertiesOvwSupport#DPFormBasic](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#dpformbasic)]  
  
Özellik ve yedekleme adlandırma kuralı <xref:System.Windows.DependencyProperty> alan önemlidir. Alanın adını her zaman soneki özelliği adıdır `Property` eklenir. Bu kural ve nedenleri hakkında daha fazla bilgi için bkz: [özel bağımlılık özellikleri](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).  

## <a name="setting-property-values"></a>Özellik değerlerini ayarlama
Kod veya XAML özellikleri ayarlayabilirsiniz.

### <a name="setting-property-values-in-xaml"></a>XAML'de özellik değerlerini ayarlama 
Aşağıdaki XAML örnek kırmızı düğme arka plan rengini belirtir. Bu örnek bir XAML özniteliği için basit bir dize değeri olduğu bir WPF türü WPF XAML çözümleyiciye tarafından türe dönüştürülüp bir durumu gösterir (bir <xref:System.Windows.Media.Color>, tarafından yolu, bir <xref:System.Windows.Media.SolidColorBrush>) oluşturulan kod.

[!code-xaml[PropertiesOvwSupport#MostBasicProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml#mostbasicproperty)]

XAML özelliklerini ayarlamak için çeşitli sözdizimi formlarını destekler. Belirli bir özellik için kullanılacak hangi sözdizimini tür dönüştürücüsünü varlığını gibi diğer faktörlere yanı sıra bir özelliği kullanan değer türüne bağlıdır. Özellik ayarı için XAML sözdizimi hakkında daha fazla bilgi için bkz: [XAML genel bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) ve [içinde XAML sözdizimi ayrıntı](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).

Öznitelik olmayan sözdiziminin bir örnek, aşağıdaki XAML örnek başka bir düğme arka planını gösterir. Bu süre basit bir düz renk ayarlamak yerine, arka plan, görüntü ve iç içe geçmiş öğe bir özniteliği olarak belirtilmiş, görüntü kaynağını temsil eden bir öğesiyle bir görüntüye ayarlanır. Bu özellik öğe sözdizimini örneğidir.

[!code-xaml[PropertiesOvwSupport#PESyntaxProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml#pesyntaxproperty)]

### <a name="setting-properties-in-code"></a>Kodda özelliklerini ayarlama
 Bağımlılık özellik değerleri kodda ayarlamak, genellikle yalnızca bir çağrı tarafından sunulan kümesi uygulamasına [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] "sarmalayıcı".

[!code-csharp[PropertiesOvwSupport#ProceduralPropertySet](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml.cs#proceduralpropertyset)]
[!code-vb[PropertiesOvwSupport#ProceduralPropertySet](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page1.xaml.vb#proceduralpropertyset)]

Bir özellik değeri alınırken bir çağrı get "sarmalayıcı" uygulamasına şöyledir:

[!code-csharp[PropertiesOvwSupport#ProceduralPropertyGet](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml.cs#proceduralpropertyget)]
 [!code-vb[PropertiesOvwSupport#ProceduralPropertyGet](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page1.xaml.vb#proceduralpropertyget)]

Ayrıca, özellik sistemi çağırabilirsiniz [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] <xref:System.Windows.DependencyObject.GetValue%2A> ve <xref:System.Windows.DependencyObject.SetValue%2A> doğrudan. (Sarmalayıcılar daha kullanışlı ve geliştirici araçları için daha iyi riskini özelliği sağlar) mevcut özellikleri kullanılarak ancak çağırma bu genellikle gerekli değilse [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] doğrudan belirli senaryolar uygundur.

Özellikler de XAML'de ayarlayın ve daha sonra kod, arka plan kodu üzerinden erişilebilir. Ayrıntılar için bkz [arka plan kod ve WPF XAML](../../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md).

## <a name="property-functionality-provided-by-a-dependency-property"></a>Bağımlılık özelliği tarafından sağlanan özellik işlevselliği
Bir özelliğe karşı işlevselliğini genişleten işlevselliği bir alan tarafından yedeklenen bir bağımlılık özelliği sağlar. Genellikle, bu tür işlevselliği temsil eder veya aşağıdaki belirli özellikler destekler:

- [Kaynaklar](#resources)

- [Veri bağlama](#data-binding)

- [Stiller](#styles)

- [Animasyonlar](#animations)

- [Meta verileri geçersiz kılar](#metadata-overrides)

- [Özellik değeri devralma](#property-value-inheritance)

- [WPF Tasarımcısı tümleştirmesi](#wpf-designer-integration)

### <a name="resources"></a>Kaynaklar
Bağımlılık özelliği değeri, bir kaynak başvurarak ayarlayabilirsiniz. Kaynaklar olarak belirtilen genellikle `Resources` sayfa kök öğesinin ya da (Bu konumları etkinleştirme kaynak için en uygun erişim) uygulamasının özellik değeri. Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.Media.SolidColorBrush> kaynak.

[!code-xaml[PropertiesOvwSupport#ResourcesResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page2.xaml#resourcesresource)]

Kaynak tanımlandıktan sonra referans ve bir özellik değeri sağlamak için kullanın:

[!code-xaml[PropertiesOvwSupport#ResourcesReference](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page2.xaml#resourcesreference)]

Bu belirli kaynak olarak başvurulan bir [DynamicResource Biçimlendirme Uzantısı](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) (WPF XAML içinde statik veya dinamik kaynak başvurusu kullanabilirsiniz). WPF özelliği sistem tarafından etkinleştirilen özellikle dinamik kaynak başvurusu kullanımı olacak şekilde dinamik kaynak başvurusu kullanmak için bir bağımlılık özelliği için ayarlamanız gerekir. Daha fazla bilgi için bkz: [XAML kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md).

> [!NOTE]
> Kaynak başka bir yerel değer ayarlarsanız, kaynak başvurusu giderilecektir yani bir yerel değer olarak kabul edilir. Daha fazla bilgi için bkz: [bağımlılık özelliği değeri önceliği](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).

### <a name="data-binding"></a>Veri bağlama
Bağımlılık özelliği değeri veri bağlama aracılığıyla başvuruda bulunabilir. Veri belirli biçimlendirme uzantısı sözdizimi çalışır XAML'de bağlama veya <xref:System.Windows.Data.Binding> kodu nesnesi. Veri bağlama ile son özellik değeri belirleme çalışma zamanı, aynı zamanda bir veri kaynağından değeri elde kadar ertelenir.

Aşağıdaki örnek kümeleri <xref:System.Windows.Controls.ContentControl.Content%2A> özelliği için bir <xref:System.Windows.Controls.Button>, bildirilen XAML'de kullanarak bir bağlama. Bağlama devralınan veri bağlamını kullanır ve bir <xref:System.Windows.Data.XmlDataProvider> veri kaynağı (gösterilmez). Bağlama tarafından istenen kaynak özelliğini belirtir <xref:System.Windows.Data.Binding.XPath%2A> veri kaynağı içinde.

[!code-xaml[PropertiesOvwSupport#BasicInlineBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#basicinlinebinding)]

> [!NOTE]
> Bağlama başka bir yerel değer ayarlarsanız, bağlama giderilecektir yani bir yerel değer olarak kabul edilir. Ayrıntılar için bkz [bağımlılık özelliği değeri önceliği](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).

Bağımlılık özellikleri veya <xref:System.Windows.DependencyObject> sınıfı, özgün olarak desteklemez <xref:System.ComponentModel.INotifyPropertyChanged> içindeki değişikliklerin bildirimleri üretme amaçları için <xref:System.Windows.DependencyObject> kaynak veri bağlama işlemleri için özellik değeri. Veri bağlama kullanımda veri bağlama hedefine değişiklikleri rapor için özelliklerin nasıl oluşturulacağı hakkında daha fazla bilgi için bkz: [veri bağlama genel bakış](../../../../docs/framework/wpf/data/data-binding-overview.md).

### <a name="styles"></a>Stilleri
Stilleri ve şablonları bağımlılık özellikleri kullanmak için baş seçimini artıran senaryoları ikisidir. Stilleri uygulama tanımlayan özellikleri ayarlamak için özellikle yararlı [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Stilleri genellikle XAML içindeki kaynaklar olarak tanımlanır. Genellikle "başka bir özellik için gerçek zamanlı değere göre bir özellik değeri değiştirme Tetikleyicileri" yanı sıra belirli özellikler için "ayarlayıcılar" içerdiğinden stiller özellik sistemi ile etkileşim.

Aşağıdaki örnek çok basit bir stil oluşturur (hangi tanımlanması içinde bir <xref:System.Windows.FrameworkElement.Resources%2A> gösterilmez sözlük), o stili doğrudan uygular <xref:System.Windows.FrameworkElement.Style%2A> özelliği için bir <xref:System.Windows.Controls.Button>. Stil kümelerinin ayarlandığı <xref:System.Windows.Controls.Control.Background%2A> özelliği için bir stilde <xref:System.Windows.Controls.Button> yeşil.

[!code-xaml[PropertiesOvwSupport#SimpleStyleDef](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#simplestyledef)]

[!code-xaml[PropertiesOvwSupport#SimpleStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#simplestyle)]

Daha fazla bilgi için bkz: [stil ve şablon](../../../../docs/framework/wpf/controls/styling-and-templating.md).

### <a name="animations"></a>Animasyonlar
Bağımlılık özellikleri animasyon uygulanabilir. Animasyonun uygulanır ve çalışır durumda olduğunda, aksi takdirde özelliğine sahip herhangi bir değer (örneğin, yerel bir değeri) daha yüksek öncelikle animasyonlu değer çalışır.

Aşağıdaki örnek canlandırır <xref:System.Windows.Controls.Control.Background%2A> üzerinde bir <xref:System.Windows.Controls.Button> özelliği (teknik olarak <xref:System.Windows.Controls.Control.Background%2A> boş belirtmek için özellik öğesi sözdizimini kullanarak animasyonlu <xref:System.Windows.Media.SolidColorBrush> olarak <xref:System.Windows.Controls.Control.Background%2A>, sonra <xref:System.Windows.Media.SolidColorBrush.Color%2A> , özelliği <xref:System.Windows.Media.SolidColorBrush> doğrudan animasyonlu özelliktir).

[!code-xaml[PropertiesOvwSupport#MiniAnimate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#minianimate)]

Özellikleri hakkında daha fazla bilgi için bkz: [animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) ve [film şeritleri genel bakış](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).

### <a name="metadata-overrides"></a>Meta verileri geçersiz kılar
Bağımlılık özelliği ilk olarak kaydeder sınıfından türetilen olduğunda bu özellik için meta verileri geçersiz kılarak, bir bağımlılık özelliğinin belirli davranışlarını değiştirebilirsiniz. Meta verileri geçersiz kılma kullanır <xref:System.Windows.DependencyProperty> tanımlayıcısı. Meta verileri geçersiz kılma özelliği yeniden uygulamayı gerektirmez. Meta veri değişikliği yerel özellik sistemi tarafından işlenir; her sınıf, büyük olasılıkla türü başına temelinde temel sınıflardan devralınır tüm özellikler için tek tek meta verileri içerir.

Aşağıdaki örnek bir bağımlılık özelliği için meta verileri geçersiz kılar <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>. Bu belirli bağımlılık özelliği meta verileri geçersiz kılma temalardan varsayılan stilleri kullanabileceğiniz denetimleri oluşturan bir uygulama deseninin bir parçasıdır.

[!code-csharp[PropertiesOvwSupport#OverrideMetadata](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml.cs#overridemetadata)]
[!code-vb[PropertiesOvwSupport#OverrideMetadata](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page3.xaml.vb#overridemetadata)]

Geçersiz kılma veya özellik meta verileri alma hakkında daha fazla bilgi için bkz: [bağımlılık özelliği meta verileri](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md).

### <a name="property-value-inheritance"></a>Özellik değeri devralma
Bir öğenin üst nesne ağacındaki bir bağımlılık özelliğinin değeri devralınmalıdır.

> [!NOTE]
> Devralma için gerekli hesaplama süresi bazı performans etkisi sahip olmadığından özellik değeri devralma davranışı genel olarak tüm bağımlılık özellikleri için etkin değil. Özellik değeri devralma genellikle yalnızca belirli bir senaryo özellik değeri devralma uygundur burada önerdiği özellikler için etkinleştirilir. Bağımlılık özelliği bakarak devralıp almadığını belirler **bağımlılık özelliği bilgileri** SDK başvurusu bu bağımlılık özelliği için bölüm.

Aşağıdaki örnek bir bağlama gösterir ve ayarlar <xref:System.Windows.FrameworkElement.DataContext%2A> önceki bağlama örneğinde gösterilmeyen bağlama kaynağını belirten özellik. Sonraki tüm alt nesneleri bağlama kaynak belirtmek gerekmez, devralınan değerden kullanabileceklerini <xref:System.Windows.FrameworkElement.DataContext%2A> üst <xref:System.Windows.Controls.StackPanel> nesnesi. (Alternatif olarak, bir alt nesne yerine doğrudan kendi belirtmek seçebilir <xref:System.Windows.FrameworkElement.DataContext%2A> veya <xref:System.Windows.Data.Binding.Source%2A> içinde <xref:System.Windows.Data.Binding>ve kendi bağlamalarının veri bağlamı için devralınan değeri kasten kullanmamayı.)

[!code-xaml[PropertiesOvwSupport#InheritanceContext](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#inheritancecontext)]

Daha fazla bilgi için bkz: [özellik değeri devralma](../../../../docs/framework/wpf/advanced/property-value-inheritance.md).

### <a name="wpf-designer-integration"></a>WPF Tasarımcı tümleştirme
Bağımlılık özellikleri uygun alacak şekilde uygulanan özelliklere sahip özel bir denetim [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] destekler. Bir örnektir ile doğrudan ve iliştirilmiş bağımlılık özelliklerini düzenleme yeteneğini **özellikleri** penceresi. Daha fazla bilgi için bkz: [denetimine genel bakış yazma](../../../../docs/framework/wpf/controls/control-authoring-overview.md).

## <a name="dependency-property-value-precedence"></a>Bağımlılık özelliği değeri önceliği
Bir bağımlılık özelliğinin değeri aldığınızda, büyük olasılıkla bu özellik, WPF özelliği sisteme katılan diğer özelliği tabanlı girişleri herhangi biri üzerinden ayarlanan bir değeri elde. Böylece çeşitli senaryolarda nasıl özelliklerini değerleri almak için tahmin edilebilir bir yolla etkileşebilir bağımlılık özelliği değeri önceliği bulunmaktadır.

Aşağıdaki örnek göz önünde bulundurun. Örnek, tüm düğmelere uygulanan stil içerir ve bunların <xref:System.Windows.Controls.Control.Background%2A> özellikleri, ancak daha sonra da bir düğme yerel olarak ayarlanmış belirtir <xref:System.Windows.Controls.Control.Background%2A> değeri.

> [!NOTE]
> SDK Belgeleri kullanan koşulları "yerel değerin" veya "yerel olarak ayarlanmış. değer" bazen bağımlılık özellikleri ele alırken. Yerel olarak ayarlanmış doğrudan bir nesne örneği kodda ya da XAML içinde bir öğe üzerinde bir öznitelik olarak ayarlanan bir özellik değeri bir değerdir.  
  
İlk düğme ilkesine özelliği iki kez ayarlanır, ancak tek bir değer geçerlidir: önceliği en yüksek değer. Yerel olarak ayarlanmış değeri en yüksek önceliğe sahiptir (dışında çalışan bir animasyon, ancak hiçbir animasyon uygular Bu örnekte) ve bu nedenle yerel olarak ayarlanmış değer arka planı için ilk düğmesine stili ayarlayıcısı değeri yerine kullanılır. Yerel değer (ve stil ayarlayıcı daha yüksek önceliğe sahip başka bir değer) ikinci düğme vardır ve böylece bu düğmenin arka planı stili ayarlayıcı gelir.

[!code-xaml[PropertiesOvwSupport#MiniPrecedence](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#miniprecedence)]  

### <a name="why-does-dependency-property-precedence-exist"></a>Bağımlılık özelliği önceliği neden yok?
Genellikle, her zaman uygulamak ve hatta yerel olarak ayarlanmış saklamasını stilleri istemezsiniz tek bir öğe değerini (Aksi halde, bu stilleri veya öğeleri genel olarak kullanmak oldukça zor olacaktır). Bu nedenle, yerel olarak ayarlanmış'den daha düşük öncelikte stilleri değerlerini çalışması değeri. Bağımlılık özellikleri ve bağımlılık özelliği etkin bir değerin alınacağı yeri daha kapsamlı bir listesi için bkz: [bağımlılık özelliği değeri önceliği](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).

> [!NOTE]
> Bağımlılık özellikleri olmayan WPF öğelerinde tanımlanan özellikler mevcuttur. Yalnızca en az bir özellik sistemi tarafından etkinleştirilen senaryolar desteklemesi zamanki göre ve large özellikleri bağımlılık özellikleri olarak uygulanan: veri bağlama, stil, animasyon, varsayılan değer desteği, devralma, ekli özellikler veya geçersiz kılma.

## <a name="learning-more-about-dependency-properties"></a>Bağımlılık özellikleri hakkında daha fazla bilgi  

- Ekli özellik, özel bir söz dizimi XAML'de destekler özellik türüdür. Ekli özellik ile 1:1 yazışmaları genellikle yok bir [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] özelliği ve mutlaka bir bağımlılık özelliği değil. Üst öğe ve alt öğesi hem sınıfı üyeleri listelerini bir parçası olarak bu özelliğe sahip olsa bile ekli özellik tipik amacı alt öğelerin bir üst öğeye özellik değerlerini raporlamasına izin vermektir. Bir birincil senaryodur nasıl bunlar içinde sunulması gereken üst bildirmek alt öğeler etkinleştirmek için [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]; bir örnek için bkz: <xref:System.Windows.Controls.DockPanel.Dock%2A> veya <xref:System.Windows.Controls.Canvas.Left%2A>. Ayrıntılar için bkz [bağlı özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).

- Bileşen geliştiriciler veya uygulama geliştiriciler, veri bağlama veya stiller desteği gibi özellikleri etkinleştirmek ya da geçersiz kılma ve değer baskı desteği için kendi bağımlılık özelliği oluşturmak isteyebilirsiniz. Ayrıntılar için bkz [özel bağımlılık özellikleri](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).

- Bağımlılık özellikleri genellikle ortak özellikler, erişilebilir olarak düşünülmelidir veya bir örneğine erişimi olan herhangi bir çağırıcı tarafından en az bulunabilir. Daha fazla bilgi için bkz: [bağımlılık özelliği güvenlik](../../../../docs/framework/wpf/advanced/dependency-property-security.md).

## <a name="see-also"></a>Ayrıca bkz.
 [Özel Bağımlılık Özellikleri](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [Salt Okunur Bağımlılık Özellikleri](../../../../docs/framework/wpf/advanced/read-only-dependency-properties.md)  
 [XAML'ye Genel Bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [WPF Mimarisi](../../../../docs/framework/wpf/advanced/wpf-architecture.md)
