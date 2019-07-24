---
title: Bağımlılık özelliklerine genel bakış
description: WPF özellik sistemi tarafından desteklenen bir özellik, bağımlılık özelliği olarak bilinir. Bu genel bakışta WPF özellik sistemi ve bağımlılık özelliğinin özellikleri açıklanmaktadır.
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
ms.openlocfilehash: b7401cd3e9551b378983193f4c5e8e4107954b74
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401420"
---
# <a name="dependency-properties-overview"></a>Bağımlılık özelliklerine genel bakış

Windows Presentation Foundation (WPF), bir türün [özelliğinin](../../../standard/base-types/common-type-system.md#Properties)işlevlerini genişletmek için kullanılabilen bir dizi hizmet sağlar. Toplu olarak, bu hizmetler genellikle WPF özellik sistemi olarak adlandırılır. WPF özellik sistemi tarafından desteklenen bir özellik, bağımlılık özelliği olarak bilinir. Bu genel bakışta WPF özellik sistemi ve bağımlılık özelliğinin özellikleri açıklanmaktadır. Bu, XAML 'de ve kodda var olan bağımlılık özelliklerinin nasıl kullanılacağını içerir. Bu genel bakış, bağımlılık özelliği meta verileri gibi bağımlılık özelliklerinin özelleşmiş yönlerini ve özel bir sınıfta kendi bağımlılık özelliklerinizi oluşturmayı da açıklar.

## <a name="prerequisites"></a>Önkoşullar
Bu konu başlığı altında, .NET türünde sistem ve nesne odaklı programlama hakkında bazı temel bilgilere sahip olduğunuz varsayılmaktadır. Bu konudaki örnekleri izlemek için XAML 'yi de anlamanız ve WPF uygulamalarının nasıl yazılacağını bilmeniz gerekir. Daha fazla bilgi için bkz [. İzlenecek yol: İlk WPF Masaüstü](../getting-started/walkthrough-my-first-wpf-desktop-application.md)Uygulamam.  
  
## <a name="dependency-properties-and-clr-properties"></a>Bağımlılık özellikleri ve CLR özellikleri
 WPF 'de, özellikler genellikle standart .NET [özellikleri](../../../standard/base-types/common-type-system.md#Properties)olarak sunulur. Temel düzeyde, bu özelliklerle doğrudan etkileşim kurabilir ve bağımlılık özelliği olarak uygulandığını hiçbir zaman bilemezsiniz. Ancak, bu özelliklerden faydalanmak için WPF özellik sisteminin bazı veya tüm özelliklerini tanımanız gerekir.

Bağımlılık özelliklerinin amacı, diğer girdilerin değerine göre bir özelliğin değerini hesaplamak için bir yol sağlamaktır. Bu diğer girişler, Temalar ve Kullanıcı tercihi gibi sistem özelliklerinin yanı sıra veri bağlama ve animasyonlar/film şeridi gibi tam zamanında özellik belirleme mekanizmaları, kaynak ve stil gibi çoklu kullanım şablonları veya bilinen değerler içerebilir öğe ağacındaki diğer öğelerle üst-alt ilişkileri aracılığıyla. Buna ek olarak, kendi kendine içerilen doğrulama, varsayılan değerler, diğer özelliklerde yapılan değişiklikleri izleyen geri çağrılar ve olası çalışma zamanı bilgilerine göre özellik değerlerini karşılayan bir sistem sağlamak için bir bağımlılık özelliği uygulanabilir. Türetilmiş sınıflar, mevcut özelliklerin gerçek uygulamasını geçersiz kılmak veya yeni özellikler oluşturmak yerine bağımlılık özelliği meta verilerini geçersiz kılarak, varolan bir özelliğin bazı belirli özelliklerini de değiştirebilir.

SDK başvurusu ' nda, bu özellik için yönetilen başvuru sayfasındaki bağımlılık özelliği bilgileri bölümünde bulunan bir bağımlılık özelliği olan özelliği belirleyebilirsiniz. Bağımlılık özelliği bilgileri bölümü, bu bağımlılık özelliğine ilişkin <xref:System.Windows.DependencyProperty> tanımlayıcı alanına bir bağlantı içerir ve ayrıca bu özellik için ayarlanan meta veri seçeneklerinin bir listesini, sınıf başına geçersiz kılma bilgilerini ve diğer ayrıntıları içerir.

## <a name="dependency-properties-back-clr-properties"></a>Bağımlılık özellikleri arka CLR özellikleri
Bağımlılık özellikleri ve WPF özellik sistemi, özelliği bir özel alanla birlikte yedeklemenin standart düzenine alternatif bir uygulama olarak bir özelliği yedekleyen bir tür sağlayarak özellik işlevselliğini genişletir. Bu türün <xref:System.Windows.DependencyProperty>adı. WPF özellik sistemini <xref:System.Windows.DependencyObject>tanımlayan diğer önemli tür. <xref:System.Windows.DependencyObject>bir bağımlılık özelliğine kaydolabileceğini ve sahip olan temel sınıfı tanımlar.

Bağımlılık özellikleriyle kullanılan terminoloji aşağıda listelenmiştir:

- **Bağımlılık özelliği:** Tarafından desteklenen bir özellik <xref:System.Windows.DependencyProperty>.

- **Bağımlılık özelliği tanımlayıcısı:** Bir bağımlılık özelliği kaydedilirken dönüş değeri olarak elde edilen ve sonra bir sınıfın statik üyesi olarak depolanan örnek.<xref:System.Windows.DependencyProperty> Bu tanımlayıcı, WPF özellik sistemiyle etkileşimde bulunan birçok API için parametre olarak kullanılır.

- **CLR "sarmalayıcı":** Özelliği için gerçek get ve set uygulamaları. Bu uygulamalar, <xref:System.Windows.DependencyObject.GetValue%2A> ve çağrılarında kullanarak bağımlılık özellik tanımlayıcısını ve <xref:System.Windows.DependencyObject.SetValue%2A> bu sayede WPF özellik sistemini kullanarak özelliğin yedeklenmesini sağlar.

Aşağıdaki örnek, `IsSpinning` bağımlılık özelliğini tanımlar ve <xref:System.Windows.DependencyProperty> tanımlayıcı tarafından geri yüklenen özelliğin ilişkisini gösterir.

[!code-csharp[PropertiesOvwSupport#DPFormBasic](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#dpformbasic)]
[!code-vb[PropertiesOvwSupport#DPFormBasic](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#dpformbasic)]  
  
Özelliğin adlandırma kuralı ve Destek <xref:System.Windows.DependencyProperty> alanı önemlidir. Alanın adı her zaman özelliğin adı, son ek `Property` eklenmiş olur. Bu kural ve bunun nedenleri hakkında daha fazla bilgi için bkz. [Özel bağımlılık özellikleri](custom-dependency-properties.md).  

## <a name="setting-property-values"></a>Özellik değerlerini ayarlama
Özellikleri kodda ya da XAML içinde ayarlayabilirsiniz.

### <a name="setting-property-values-in-xaml"></a>XAML 'de özellik değerlerini ayarlama 
Aşağıdaki XAML örneği, bir düğmenin arka plan rengini kırmızı olarak belirtir. Bu örnek, bir xaml özniteliği için basit dize değerinin, oluşturulan kodda bir WPF türüne ( <xref:System.Windows.Media.Color>a 'ya göre <xref:System.Windows.Media.SolidColorBrush>) WPF XAML ayrıştırıcısı tarafından tür dönüştürdüğüne ilişkin bir durumu gösterir.

[!code-xaml[PropertiesOvwSupport#MostBasicProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml#mostbasicproperty)]

XAML, özellikleri ayarlamak için çeşitli sözdizimi formlarını destekler. Belirli bir özellik için kullanılacak sözdizimi, bir özelliğin kullandığı değer türüne ve bir tür dönüştürücünün varlığı gibi diğer faktörlere bağlı olacaktır. Özellik ayarı için XAML sözdizimi hakkında daha fazla bilgi için bkz. [xaml genel bakış (WPF)](xaml-overview-wpf.md) ve [XAML sözdizimi ayrıntılı](xaml-syntax-in-detail.md).

Öznitelik olmayan sözdiziminin bir örneği olarak, aşağıdaki XAML örneği başka bir düğme arkaplanını gösterir. Bu kez basit bir düz renk ayarlamak yerine, arka plan bir görüntüye ayarlanır, bu da söz konusu görüntüyü temsil eden öğe ve iç içe geçmiş öğenin bir özniteliği olarak belirtilen görüntünün kaynağı. Bu bir özellik öğesi söz dizimi örneğidir.

[!code-xaml[PropertiesOvwSupport#PESyntaxProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml#pesyntaxproperty)]

### <a name="setting-properties-in-code"></a>Koddaki özellikleri ayarlama
 Kodda bağımlılık özelliği değerlerini ayarlamak genellikle CLR "sarmalayıcı" tarafından kullanıma sunulan küme uygulamasına yapılan bir çağrıdır.

[!code-csharp[PropertiesOvwSupport#ProceduralPropertySet](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml.cs#proceduralpropertyset)]
[!code-vb[PropertiesOvwSupport#ProceduralPropertySet](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page1.xaml.vb#proceduralpropertyset)]

Özellik değeri alma, Ayrıca, Get "sarmalayıcı" uygulamasına yapılan bir çağrıdır:

[!code-csharp[PropertiesOvwSupport#ProceduralPropertyGet](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml.cs#proceduralpropertyget)]
 [!code-vb[PropertiesOvwSupport#ProceduralPropertyGet](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page1.xaml.vb#proceduralpropertyget)]

Ayrıca, özellik sistemi API 'lerini <xref:System.Windows.DependencyObject.GetValue%2A> ve <xref:System.Windows.DependencyObject.SetValue%2A> doğrudan çağırabilirsiniz. Mevcut özellikleri kullanıyorsanız bu genellikle gerekli değildir (sarmalayıcılar daha uygundur ve geliştirici araçları için özelliğin daha iyi pozlamasını sağlar), ancak API 'Lerin doğrudan çağrılması belirli senaryolar için uygundur.

Özellikler XAML 'de de ayarlanabilir ve daha sonra kod içinde daha sonra kod arkasında erişilebilir. Ayrıntılar için bkz. [WPF Içinde arka plan kodu ve xaml](code-behind-and-xaml-in-wpf.md).

## <a name="property-functionality-provided-by-a-dependency-property"></a>Bağımlılık özelliği tarafından sunulan özellik işlevselliği
Dependency özelliği bir özelliğin işlevselliğini bir alan tarafından desteklenen bir özelliğin aksine genişleten işlevselliği sağlar. Genellikle, bu tür işlevler aşağıdaki özel özelliklerden birini temsil eder veya destekler:

- [Kaynaklar](#resources)

- [Veri bağlama](#data-binding)

- [Stiller](#styles)

- [Animasyonlar](#animations)

- [Meta veri geçersiz kılmaları](#metadata-overrides)

- [Özellik değeri devralma](#property-value-inheritance)

- [WPF Tasarımcısı tümleştirmesi](#wpf-designer-integration)

### <a name="resources"></a>Kaynaklar
Bir bağımlılık özelliği değeri, bir kaynağa başvurarak ayarlanabilir. Kaynaklar, genellikle bir sayfa kök `Resources` öğesinin ya da uygulamanın özellik değeri olarak belirtilir (Bu konumlar kaynağa en kolay erişimi etkinleştirir). Aşağıdaki örnekte, bir <xref:System.Windows.Media.SolidColorBrush> kaynağın nasıl tanımlanacağı gösterilmektedir.

[!code-xaml[PropertiesOvwSupport#ResourcesResource](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page2.xaml#resourcesresource)]

Kaynak tanımlandıktan sonra, kaynağa başvurabilir ve bunu bir özellik değeri sağlamak için kullanabilirsiniz:

[!code-xaml[PropertiesOvwSupport#ResourcesReference](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page2.xaml#resourcesreference)]

Bu kaynağa bir [DynamicResource Işaretleme uzantısı](dynamicresource-markup-extension.md) olarak başvurulur (WPF XAML 'de, statik veya dinamik kaynak başvurusu kullanabilirsiniz). Dinamik bir kaynak başvurusu kullanmak için, bir bağımlılık özelliği olarak ayarlanması gerekir, bu nedenle WPF özellik sistemi tarafından etkinleştirilen dinamik kaynak başvuru kullanımıdır. Daha fazla bilgi için bkz. [xaml kaynakları](xaml-resources.md).

> [!NOTE]
> Kaynaklar yerel bir değer olarak değerlendirilir, yani başka bir yerel değer ayarlarsanız kaynak başvurusunu ortadan kaldıracaksınız. Daha fazla bilgi için bkz. [bağımlılık özelliği değer önceliği](dependency-property-value-precedence.md).

### <a name="data-binding"></a>Veri bağlama
Bağımlılık özelliği, veri bağlama yoluyla bir değere başvurabilir. Veri bağlama xaml 'deki belirli bir işaretleme uzantısı sözdizimi veya <xref:System.Windows.Data.Binding> koddaki nesne aracılığıyla işe yarar. Veri bağlama ile son özellik değeri belirleme işlemi çalışma zamanına kadar ertelenir ve bu süre, değer bir veri kaynağından alınır.

Aşağıdaki örnek, XAML 'de <xref:System.Windows.Controls.ContentControl.Content%2A> bildirildiği bir bağlamayı <xref:System.Windows.Controls.Button>kullanarak bir için özelliğini ayarlar. Bağlama devralınan bir veri bağlamını ve bir <xref:System.Windows.Data.XmlDataProvider> veri kaynağını (gösterilmez) kullanır. Bağlama, veri kaynağı <xref:System.Windows.Data.Binding.XPath%2A> dahilinde istenen kaynak özelliğini belirtir.

[!code-xaml[PropertiesOvwSupport#BasicInlineBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#basicinlinebinding)]

> [!NOTE]
> Bağlamalar yerel bir değer olarak değerlendirilir, yani başka bir yerel değer ayarlarsanız bağlamayı ortadan kaldıracaksınız. Ayrıntılar için bkz. [bağımlılık özelliği değer önceliği](dependency-property-value-precedence.md).

Bağımlılık özellikleri veya <xref:System.Windows.DependencyObject> sınıfı, veri bağlama işlemleri için <xref:System.Windows.DependencyObject> kaynak özellik <xref:System.ComponentModel.INotifyPropertyChanged> değerindeki değişikliklere ilişkin bildirim üretme amacıyla yerel olarak desteklenmez. Veri bağlama hedefinde değişiklik bildiremeyen veri bağlamasında kullanılmak üzere özellikler oluşturma hakkında daha fazla bilgi için bkz. [veri bağlamaya genel bakış](../data/data-binding-overview.md).

### <a name="styles"></a>Stiller
Stiller ve şablonlar, bağımlılık özelliklerini kullanmak için, bir veya daha fazla mücadele senaryolarından ikdir. Stiller, uygulamayı [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]tanımlayan özellikleri ayarlamak için özellikle faydalıdır. Stiller genellikle XAML 'de kaynak olarak tanımlanır. Stiller, genellikle belirli özellikler için "ayarlayıcılar" ve diğer bir özellik için gerçek zamanlı değere göre bir özellik değeri değiştiren "Tetikleyiciler" içerdiğinden, özellik sistemiyle etkileşime geçer.

Aşağıdaki örnek, çok basit bir stil (bir <xref:System.Windows.FrameworkElement.Resources%2A> Sözlük içinde tanımlanacak, gösterilmez) oluşturur, ardından bu stili doğrudan bir <xref:System.Windows.FrameworkElement.Style%2A> <xref:System.Windows.Controls.Button>özelliği için uygular. Stili içindeki ayarlayıcı, stillendirilmiş <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button> bir için özelliğini yeşil olarak ayarlar.

[!code-xaml[PropertiesOvwSupport#SimpleStyleDef](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#simplestyledef)]

[!code-xaml[PropertiesOvwSupport#SimpleStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#simplestyle)]

Daha fazla bilgi için bkz. [Stil oluşturma ve şablon](../controls/styling-and-templating.md)oluşturma.

### <a name="animations"></a>Animasyonlar
Bağımlılık özellikleri canlandırılabilirler. Bir animasyon uygulandığında ve çalışırken, animasyon değeri, özelliğin başka türlü herhangi bir değerden (yerel bir değer gibi) daha yüksek bir önceliğe göre çalışır.

Aşağıdaki örnek <xref:System.Windows.Controls.Control.Background%2A> , bir <xref:System.Windows.Media.SolidColorBrush> <xref:System.Windows.Controls.Control.Background%2A>özelliğini bir <xref:System.Windows.Controls.Button> özelliği üzerinde hareketlendirir (Teknik olarak, özelliği olarak <xref:System.Windows.Media.SolidColorBrush.Color%2A> boş bir değerbelirtmekiçinözelliköğesisözdizimikullanılarakcanlandırılır.<xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Media.SolidColorBrush> , doğrudan canlandırılmış olan özelliktir).

[!code-xaml[PropertiesOvwSupport#MiniAnimate](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#minianimate)]

Hareketlendirilen özellikler hakkında daha fazla bilgi için bkz. [animasyon genel bakış](../graphics-multimedia/animation-overview.md) ve [görsel taslakları genel bakış](../graphics-multimedia/storyboards-overview.md).

### <a name="metadata-overrides"></a>Meta veri geçersiz kılmaları
Bağımlılık özelliğini ilk kaydeden sınıftan türettiğinizde, bir bağımlılık özelliğinin belirli davranışlarını, bu özellik için meta verileri geçersiz kılarak değiştirebilirsiniz. Meta verileri geçersiz kılma <xref:System.Windows.DependencyProperty> tanımlayıcı kullanır. Meta verilerin geçersiz kılınması, özelliğin yeniden uygulanması gerektirmez. Meta veri değişikliği, özellik sistemi tarafından yerel olarak işlenir; Her bir sınıf potansiyel olarak temel sınıflardan devralınan tüm özellikler için bağımsız meta verileri bir tür temelinde barındırır.

Aşağıdaki örnek, bir bağımlılık özelliği <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>için meta verileri geçersiz kılar. Bu belirli bağımlılık özelliği meta verilerinin geçersiz kılınması, temalardan varsayılan stilleri kullanan denetimler oluşturan bir uygulama deseninin parçasıdır.

[!code-csharp[PropertiesOvwSupport#OverrideMetadata](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml.cs#overridemetadata)]
[!code-vb[PropertiesOvwSupport#OverrideMetadata](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page3.xaml.vb#overridemetadata)]

Özellik meta verilerini geçersiz kılma veya alma hakkında daha fazla bilgi için bkz. [bağımlılık özelliği meta verileri](dependency-property-metadata.md).

### <a name="property-value-inheritance"></a>Özellik değeri devralma
Bir öğesi, nesne ağacındaki üst öğesinden bir bağımlılık özelliğinin değerini alabilir.

> [!NOTE]
> Devralma için hesaplama süresi bazı performans etkilerine sahip olduğundan, özellik değeri devralma davranışı tüm bağımlılık özellikleri için genel olarak etkin değildir. Özellik değeri kalıtımı genellikle yalnızca belirli bir senaryonun Özellik değeri devralmayı uygun şekilde önerdiği özellikler için etkinleştirilir. SDK başvurusunda ilgili bağımlılık özelliği için **bağımlılık özelliği bilgileri** bölümüne bakarak bir bağımlılık özelliğinin devralıp devralınmayacağını belirleyebilirsiniz.

Aşağıdaki örnek bir bağlamayı gösterir ve önceki bağlama örneğinde görünmeyen <xref:System.Windows.FrameworkElement.DataContext%2A> bağlamanın kaynağını belirten özelliği ayarlar. Alt nesnelerdeki sonraki tüm bağlamaların kaynağı belirtmesi gerekmez, devralınan değeri <xref:System.Windows.FrameworkElement.DataContext%2A> üst <xref:System.Windows.Controls.StackPanel> nesne içinden kullanabilirler. (Alternatif olarak, bir alt nesne bunun yerine kendi <xref:System.Windows.FrameworkElement.DataContext%2A> <xref:System.Windows.Data.Binding.Source%2A> içinde <xref:System.Windows.Data.Binding>kendi veya ' nin doğrudan belirtmeyi ve bağlamaların veri bağlamı için devralınan değeri kasıtlı olarak kullanmamaktır.)

[!code-xaml[PropertiesOvwSupport#InheritanceContext](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#inheritancecontext)]

Daha fazla bilgi için bkz. [özellik değeri devralma](property-value-inheritance.md).

### <a name="wpf-designer-integration"></a>WPF Tasarımcısı tümleştirmesi
Bağımlılık özellikleri olarak uygulanan özelliklere sahip özel bir denetim uygun [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] desteği alacaktır. Bir örnek, doğrudan ve iliştirilmiş bağımlılık özelliklerini **Özellikler** penceresiyle düzenleme olanağıdır. Daha fazla bilgi için bkz. [Denetim yazma genel bakış](../controls/control-authoring-overview.md).

## <a name="dependency-property-value-precedence"></a>Bağımlılık özelliği değer önceliği
Bir bağımlılık özelliğinin değerini aldığınızda, büyük olasılıkla WPF özellik sistemine katılan diğer özellik tabanlı girdilerden herhangi biri aracılığıyla o özellikte ayarlanmış bir değer elde edersiniz. Bağımlılık özelliği değer önceliği bulunur, böylece özelliklerin değerlerini elde etmek için çeşitli senaryolar öngörülebilir bir şekilde etkileşim kurabilir.

Aşağıdaki örneği göz önünde bulundurun. Örnek, tüm düğmelere ve <xref:System.Windows.Controls.Control.Background%2A> özelliklerine uygulanan bir stil içerir, ancak aynı zamanda yerel olarak ayarlanmış <xref:System.Windows.Controls.Control.Background%2A> bir değeri olan bir düğmeyi belirtir.

> [!NOTE]
> SDK belgeleri, bağımlılık özellikleri tartışırken bazen "yerel değer" veya "yerel olarak ayarlanmış değer" terimlerini kullanır. Yerel olarak ayarlanan değer, doğrudan kodda bir nesne örneğinde veya XAML içindeki bir öğe üzerinde bir öznitelik olarak ayarlanan bir özellik değeridir.  
  
İlke ' de, ilk düğme için özellik iki kez ayarlanır, ancak yalnızca bir değer geçerlidir: en yüksek önceliğe sahip değer. Yerel olarak ayarlanmış bir değer en yüksek önceliğe sahiptir (çalışan bir animasyon hariç, ancak bu örnekte herhangi bir animasyon uygulanmaz) ve bu nedenle, ilk düğmedeki arka plan için stil ayarlayıcısı değeri yerine yerel olarak ayarlanan değer kullanılır. İkinci düğme yerel bir değere sahip değildir (ve bir stil ayarlayıcısından daha yüksek önceliğe sahip başka bir değer yoktur) ve bu nedenle söz konusu düğmedeki arka plan stil ayarlayıcısından gelir.

[!code-xaml[PropertiesOvwSupport#MiniPrecedence](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#miniprecedence)]  

### <a name="why-does-dependency-property-precedence-exist"></a>Bağımlılık özelliği önceliği neden var?
Genellikle, stillerin her zaman ve tek bir öğe için yerel olarak ayarlanmış bir değere sahip olmasını istemezsiniz (Aksi takdirde, genel olarak stili veya öğeleri kullanmak çok zor olur). Bu nedenle, stillerden gelen değerler yerel olarak ayarlanmış bir değere göre daha düşük bir şekilde çalışır. Bağımlılık özelliklerinin ve bağımlılık özelliği etkin bir değerin nereden gelebileceği hakkında daha kapsamlı bir liste için bkz. [bağımlılık özelliği değer önceliği](dependency-property-value-precedence.md).

> [!NOTE]
> Bağımlılık özellikleri olmayan WPF öğelerinde tanımlanmış birçok özellik vardır. Ve büyük, özellikler yalnızca özellik sistemi tarafından etkinleştirilen senaryolardan en az birini desteklemesi gerektiğinde bağımlılık özellikleri olarak uygulandı: veri bağlama, stil oluşturma, animasyon, varsayılan değer desteği, devralma, ekli özellikler veya geçersiz kılma.

## <a name="learning-more-about-dependency-properties"></a>Bağımlılık özellikleri hakkında daha fazla bilgi  

- İliştirilmiş özellik XAML 'de özelleştirilmiş bir söz dizimini destekleyen bir özellik türüdür. İliştirilmiş bir özelliğin genellikle ortak dil çalışma zamanı (CLR) özelliğine sahip 1:1 yazışmaları yoktur ve bir bağımlılık özelliği olması gerekmez. İliştirilmiş bir özelliğin tipik amacı, üst öğe ve alt öğe her ikisi de sınıf üye listelerinin parçası olarak bu özelliğe sahip olmasa bile, alt öğelerin özellik değerlerini bir üst öğeye rapor vermesine izin versağlamaktır. Tek bir birincil senaryo, alt öğelerin ' de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]nasıl sunulmaları gerektiğini bilgilendirmek üzere etkinleştirilmesidir; Örneğin, bkz <xref:System.Windows.Controls.DockPanel.Dock%2A> . veya <xref:System.Windows.Controls.Canvas.Left%2A>. Ayrıntılar için bkz. [ekli özelliklere genel bakış](attached-properties-overview.md).

- Bileşen geliştiricileri veya uygulama geliştiricileri, veri bağlama veya stiller desteği veya geçersiz doğrulama ve değer zorlaması desteği gibi özellikleri etkinleştirmek için kendi bağımlılık özelliğini oluşturmak isteyebilir. Ayrıntılar için bkz. [Özel bağımlılık özellikleri](custom-dependency-properties.md).

- Bağımlılık özellikleri genellikle genel özellikler, erişilebilir veya en az bir örneğe erişimi olan herhangi bir çağıran tarafından bulunabilir olarak düşünülmelidir. Daha fazla bilgi için bkz. [bağımlılık özelliği güvenliği](dependency-property-security.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Bağımlılık Özellikleri](custom-dependency-properties.md)
- [Salt Okunur Bağımlılık Özellikleri](read-only-dependency-properties.md)
- [XAML'ye Genel Bakış (WPF)](xaml-overview-wpf.md)
- [WPF Mimarisi](wpf-architecture.md)
