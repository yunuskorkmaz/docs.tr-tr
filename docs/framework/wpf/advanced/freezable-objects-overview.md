---
title: Freezable Nesnelerine Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], description
- unfreezing Freezable objects [WPF]
- classes [WPF], Freezable
ms.assetid: 89c71692-4f43-4057-b611-67c6a8a863a2
ms.openlocfilehash: b1887afd19407898d8de1d92252e29778899fb89
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095196"
---
# <a name="freezable-objects-overview"></a>Freezable Nesnelerine Genel Bakış

Bu konuda, uygulama performansının artırılmasına yardımcı olabilecek özel özellikler sağlayan <xref:System.Windows.Freezable> nesnelerinin etkin bir şekilde kullanılması ve oluşturulması açıklanmaktadır. Freezable nesne örnekleri, fırçalar, kalemler, dönüşümler, geometriler ve animasyonları içerir.

<a name="whatisafreezable"></a>

## <a name="what-is-a-freezable"></a>Freezable nedir?

<xref:System.Windows.Freezable>, iki durumu olan özel bir nesne türüdür: dondurulmamış ve dondurulmuş. Dondurulmamış olduğunda, <xref:System.Windows.Freezable> diğer herhangi bir nesne gibi davranır. Dondurulduktan sonra, <xref:System.Windows.Freezable> artık değiştirilemez.

<xref:System.Windows.Freezable>, nesne üzerinde yapılan herhangi bir değişiklik için gözlemcilerin 'a bildirimde bulunan <xref:System.Windows.Freezable.Changed> bir olay sağlar. Bir <xref:System.Windows.Freezable> dondurmak, artık kaynakları değişiklik bildirimleri üzerinde harcaması gerekmediği için performansını iyileştirebilir. Dondurulmuş bir <xref:System.Windows.Freezable> iş parçacıkları arasında da paylaşılabilir, ancak dondurulmamış bir <xref:System.Windows.Freezable> olamaz.

<xref:System.Windows.Freezable> sınıfında birçok uygulama olsa da, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] içindeki çoğu <xref:System.Windows.Freezable> nesne grafik alt sistemiyle ilgilidir.

<xref:System.Windows.Freezable> sınıfı, belirli grafik sistem nesnelerinin kullanılmasını kolaylaştırır ve uygulama performansının artırılmasına yardımcı olabilir. <xref:System.Windows.Freezable> 'ten devraldığı türlerin örnekleri <xref:System.Windows.Media.Brush>, <xref:System.Windows.Media.Transform>ve <xref:System.Windows.Media.Geometry> sınıflarını içerir. Yönetilmeyen kaynaklar içerdiğinden, sistemin bu nesneleri değişikliklere karşı izlemesi gerekir ve özgün nesnede bir değişiklik olduğunda ilgili yönetilmeyen kaynaklarını güncelleştirmelidir. Bir grafik sistemi nesnesini gerçekten değiştirmese de, sistemin değişiklik yapması durumunda nesneyi izleyen bazı kaynakları harcaması gerekir.

Örneğin, bir <xref:System.Windows.Media.SolidColorBrush> fırçası oluşturduğunuzu ve düğmenin arka planını boyamak için kullandığınızı varsayalım.

[!code-csharp[freezablesample_procedural#FrozenExamplePart1](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart1)]
[!code-vb[freezablesample_procedural#FrozenExamplePart1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart1)]

Düğme işlendiğinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] grafik alt sistemi, bir düğmenin görünümünü oluşturmak için bir piksel grubunu boyamak üzere verdiğiniz bilgileri kullanır. Düğmenin nasıl boyanması gerektiğini betimleyen bir düz renk fırçası kullansanız da, düz renk fırçanızı gerçekten boyama yapmaz. Grafik sistemi, düğme ve fırça için hızlı, alt düzey nesneler oluşturur ve aslında ekranda görünen nesnelerdir.

Fırçayı değiştirmek istiyorsanız, bu alt düzey nesnelerin yeniden oluşturulması gerekir. Freezable sınıfı, bir fırçaya karşılık gelen oluşturulan, alt düzey nesneleri bulma ve değişiklik yaparken bunları güncelleştirme olanağı sunar. Bu özellik etkinleştirildiğinde, fırça "dondurulmamış" olarak kabul edilir.

Freezable 'ın <xref:System.Windows.Freezable.Freeze%2A> yöntemi, bu kendi kendini güncelleştirme yeteneğini devre dışı bırakmanızı sağlar. Fırçayı "dondurulmuş" veya değiştirilemez hale getirmek için bu yöntemi kullanabilirsiniz.

> [!NOTE]
> Her Freezable nesnesi dondurulamıyor. Bir <xref:System.InvalidOperationException>oluşturmamaya kaçınmak için, dondurmadan önce dondurulmuş olup olmadığını öğrenmek üzere Freezable nesnesinin <xref:System.Windows.Freezable.CanFreeze%2A> özelliğinin değerini denetleyin.

[!code-csharp[freezablesample_procedural#FrozenExamplePart2](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart2)]
[!code-vb[freezablesample_procedural#FrozenExamplePart2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart2)]

Freezable 'ı değiştirmenize gerek kalmadığında performans avantajları sağlar. Bu örnekteki fırçayı dondurursanız, grafik sisteminin artık değişiklikleri izlemek zorunda kalmaz. Fırçanın değişmediği bildiğinden, grafik sistemi başka iyileştirmeler de yapabilir.

> [!NOTE]
> Daha kolay bir şekilde dondurmadığınız takdirde, Freezable nesneler dondurulmamış olarak kalır.

<a name="frozenfreezables"></a>

## <a name="using-freezables"></a>Freezable nesneleri kullanma

Dondurulmamış bir Freezable kullanmak, herhangi bir nesne türünü kullanmak gibidir. Aşağıdaki örnekte, bir düğmenin arka planını boyamak için kullanıldıktan sonra bir <xref:System.Windows.Media.SolidColorBrush> rengi sarıya kırmızıya dönüştürülür. Grafik sistemi, ekranın arkasında bir sonraki sefer yenilendiğinde düğme sarıdan kırmızıya otomatik olarak değiştirilmesini sağlar.

[!code-csharp[freezablesample_procedural#UnFrozenExampleShort](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#unfrozenexampleshort)]
[!code-vb[freezablesample_procedural#UnFrozenExampleShort](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#unfrozenexampleshort)]

### <a name="freezing-a-freezable"></a>Freezable 'ı dondurma

<xref:System.Windows.Freezable> değiştirilemez yapmak için, <xref:System.Windows.Freezable.Freeze%2A> yöntemini çağırın. Freezable nesneleri içeren bir nesneyi dondurursanız, bu nesneler de dondurulur. Örneğin, bir <xref:System.Windows.Media.PathGeometry>dondurursanız, içerdiği şekiller ve segmentler de dondurulur.

Aşağıdakilerden biri **doğruysa Freezable dondurulamıyor:**

- Animasyonlu veya veri bağlantılı özelliklere sahiptir.

- Dinamik bir kaynak tarafından ayarlanan özelliklere sahiptir. (Dinamik kaynaklar hakkında daha fazla bilgi için bkz. [xaml kaynakları](../../../desktop-wpf/fundamentals/xaml-resources-define.md) .)

- Dondurulamayan <xref:System.Windows.Freezable> alt nesneler içerir.

Bu koşullar yanlışsa ve <xref:System.Windows.Freezable>değiştirmeyi düşünmüyorsanız, daha önce açıklanan performans avantajlarını kazanmak için bu koşulları dondurmanız gerekir.

Freezable 'ın <xref:System.Windows.Freezable.Freeze%2A> yöntemini çağırdığınızda, artık değiştirilemez. Dondurulmuş bir nesneyi değiştirme girişimi bir <xref:System.InvalidOperationException> oluşturulmasına neden olur. Aşağıdaki kod bir özel durum oluşturur, çünkü bir fırçayı dondurulmuş olduktan sonra değiştirmeyi deneiyoruz.

[!code-csharp[freezablesample_procedural#ExceptionExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#exceptionexample)]
[!code-vb[freezablesample_procedural#ExceptionExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#exceptionexample)]

Bu özel durumun üretilmesini önlemek için, bir <xref:System.Windows.Freezable> dondurulmuş olup olmadığını anlamak üzere <xref:System.Windows.Freezable.IsFrozen%2A> yöntemini kullanabilirsiniz.

[!code-csharp[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
[!code-vb[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]

Yukarıdaki kod örneğinde, dondurulmuş bir nesneden <xref:System.Windows.Freezable.Clone%2A> yöntemi kullanılarak değiştirilebilir bir kopya yapılmıştır. Sonraki bölümde kopyalamayı daha ayrıntılı olarak ele alınmaktadır.

> [!NOTE]
> Dondurulmuş bir Freezable animasyon uygulanamadığından, bir <xref:System.Windows.Media.Animation.Storyboard>hareketlendirmek istediğinizde animasyon sistemi otomatik olarak dondurulmuş <xref:System.Windows.Freezable> nesnelerinin değiştirilebilir klonlarını oluşturur. Kopyalamanın neden olduğu performans yükünü ortadan kaldırmak için, hareketlendirmek istiyorsanız nesne dondurulmamış olarak bırakın. Görsel taslaklara animasyon ekleme hakkında daha fazla bilgi için bkz. görsel taslaklara [genel bakış](../graphics-multimedia/storyboards-overview.md)

### <a name="freezing-from-markup"></a>Biçimlendirmeden dondurma

Biçimlendirme içinde belirtilen bir <xref:System.Windows.Freezable> nesnesini dondurmak için `PresentationOptions:Freeze` özniteliğini kullanırsınız. Aşağıdaki örnekte, bir <xref:System.Windows.Media.SolidColorBrush> sayfa kaynağı olarak bildirildiği ve dondurulmuş. Daha sonra bir düğmenin arka planını ayarlamak için kullanılır.

[!code-xaml[FreezableSample#FreezeFromMarkupWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FreezableSample/CS/FreezeFromMarkupExample.xaml#freezefrommarkupwholepage)]

`Freeze` özniteliğini kullanmak için, sunu seçenekleri ad alanına eşlemeniz gerekir: `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options`. `PresentationOptions`, bu ad alanını eşlemek için önerilen önekidir:

```xaml
xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"
```

Tüm XAML okuyucuları bu özniteliği tanımadığı için, `Presentation:Freeze` özniteliğini yoksayılabilir olarak işaretlemek için [mc: Ignorable özniteliğini](mc-ignorable-attribute.md) kullanmanız önerilir:

```xaml
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
mc:Ignorable="PresentationOptions"
```

Daha fazla bilgi için bkz. [mc: Ignorable özniteliği](mc-ignorable-attribute.md) sayfası.

### <a name="unfreezing-a-freezable"></a>Freezable "dondurmayı kaldırma"

Dondurulduktan sonra, <xref:System.Windows.Freezable> hiçbir şekilde değiştirilemez veya çözülemez; Ancak, <xref:System.Windows.Freezable.Clone%2A> veya <xref:System.Windows.Freezable.CloneCurrentValue%2A> yöntemini kullanarak dondurulmamış bir kopya oluşturabilirsiniz.

Aşağıdaki örnekte, düğmenin arka planı fırçayla ayarlanır ve bu fırça daha sonra dondurulur. <xref:System.Windows.Freezable.Clone%2A> yöntemi kullanılarak fırçayla dondurulmamış bir kopya yapılır. Kopya değiştirilir ve düğmenin arka planını sarıdan kırmızıya değiştirmek için kullanılır.

[!code-csharp[freezablesample_procedural#CloneExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
[!code-vb[freezablesample_procedural#CloneExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]

> [!NOTE]
> Kullandığınız kopya yönteminden bağımsız olarak, animasyonlar hiçbir şekilde yeni <xref:System.Windows.Freezable>kopyalanmaz.

<xref:System.Windows.Freezable.Clone%2A> ve <xref:System.Windows.Freezable.CloneCurrentValue%2A> yöntemleri, Freezable 'ın derin kopyalarını oluşturur. Freezable diğer dondurulmuş Freezable nesnelerini içeriyorsa, bunlar da klonlanır ve değiştirilebilir hale getirilir. Örneğin, değiştirilebilir yapmak için dondurulmuş bir <xref:System.Windows.Media.PathGeometry> klonladığınızda, içerdiği şekiller ve segmentler de kopyalanır ve değiştirilebilir hale getirilir.

<a name="createyourownfreezableclass"></a>

## <a name="creating-your-own-freezable-class"></a>Kendi Freezable sınıfınızı oluşturma

<xref:System.Windows.Freezable> türetilen bir sınıf aşağıdaki özellikleri kazanır.

- Özel durumlar: salt okunurdur (dondurulmuş) ve yazılabilir bir durumdur.

- İş parçacığı güvenliği: dondurulmuş bir <xref:System.Windows.Freezable>, iş parçacıkları arasında paylaşılabilir.

- Ayrıntılı değişiklik bildirimi: diğer <xref:System.Windows.DependencyObject>öğelerinden farklı olarak, Freezable nesneleri, alt özellik değerleri değiştiğinde değişiklik bildirimleri sağlar.

- Kolay kopyalama: Freezable sınıfı derin kopyalar üreten birkaç yöntemi zaten uygulamıştır.

<xref:System.Windows.Freezable> bir <xref:System.Windows.DependencyObject>türüdür ve bu nedenle bağımlılık özellik sistemini kullanır. Sınıf özelliklerindeki bağımlılık özellikleri olması gerekmez, ancak bağımlılık özelliklerinin kullanılması, <xref:System.Windows.Freezable> sınıfı bağımlılık özellikleriyle birlikte tasarlandığından, yazmanız gereken kod miktarını azaltır. Bağımlılık özelliği sistemi hakkında daha fazla bilgi için bkz. [bağımlılık özelliklerine genel bakış](dependency-properties-overview.md).

Her <xref:System.Windows.Freezable> alt sınıfı <xref:System.Windows.Freezable.CreateInstanceCore%2A> yöntemi geçersiz kılmalıdır. Sınıfınız tüm verileri için bağımlılık özelliklerini kullanıyorsa işiniz tamamlanmıştır.

Sınıfınız bağımlılık olmayan özellik verisi üyeleri içeriyorsa, aşağıdaki yöntemleri de geçersiz kılmanız gerekir:

- <xref:System.Windows.Freezable.CloneCore%2A>

- <xref:System.Windows.Freezable.CloneCurrentValueCore%2A>

- <xref:System.Windows.Freezable.GetAsFrozenCore%2A>

- <xref:System.Windows.Freezable.GetCurrentValueAsFrozenCore%2A>

- <xref:System.Windows.Freezable.FreezeCore%2A>

Bağımlılık özellikleri olmayan veri üyelerine erişmek ve bunlara yazmak için aşağıdaki kuralları da gözlemleyebilirsiniz:

- Bağımlılık olmayan özellik veri üyelerini okuyan herhangi bir API 'nin başlangıcında <xref:System.Windows.Freezable.ReadPreamble%2A> yöntemini çağırın.

- Bağımlılık olmayan özellik veri üyelerini yazan herhangi bir API 'nin başlangıcında <xref:System.Windows.Freezable.WritePreamble%2A> yöntemini çağırın. (Bir API 'de <xref:System.Windows.Freezable.WritePreamble%2A> çağrıldıktan sonra, bağımlılık olmayan özellik veri üyelerini de okuduğunuzda <xref:System.Windows.Freezable.ReadPreamble%2A> için ek bir çağrı yapmanız gerekmez.)

- Bağımlılık olmayan özellik veri üyelerine yazılan yöntemlerden çıkmadan önce <xref:System.Windows.Freezable.WritePostscript%2A> yöntemini çağırın.

Sınıfınız <xref:System.Windows.DependencyObject> nesneler olan bağımlılık dışı özellik veri üyelerini içeriyorsa, üyeyi `null`olarak ayarlasanız bile, değerlerinden birini her değiştirişinizde <xref:System.Windows.Freezable.OnFreezablePropertyChanged%2A> yöntemini de çağırmanız gerekir.

> [!NOTE]
> Geçersiz kıldığınız her bir <xref:System.Windows.Freezable> yöntemi temel uygulamaya yapılan bir çağrı ile başlamanız çok önemlidir.

Özel bir <xref:System.Windows.Freezable> sınıfına bir örnek için bkz. [özel animasyon örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/CustomAnimation).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Freezable>
- [Özel animasyon örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/CustomAnimation)
- [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md)
- [Özel Bağımlılık Özellikleri](custom-dependency-properties.md)
