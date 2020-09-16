---
title: x:Name Yönergesi
ms.date: 03/30/2017
f1_keywords:
- x:Name
- xName
- Name
helpviewer_keywords:
- x:Name attribute [XAML Services]
- XAML [XAML Services], x:Name attribute
- Name attribute in XAML [XAML Services]
ms.assetid: b7e61222-e8cf-48d2-acd0-6df3b7685d48
ms.openlocfilehash: ddaa35b18d1c632fc49b18dabf0d992dc1c78fcc
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90549489"
---
# <a name="xname-directive"></a>x:Name Yönergesi

Xaml namescope 'da XAML tanımlı öğeleri benzersiz şekilde tanımlar. Çerçeveler API 'ler sağlar veya çalışma zamanında XAML tarafından oluşturulan nesne grafiğine erişen davranışlar uygularsa, xaml ad kapsamları ve bunların benzersizlik modelleri örneklenmiş nesnelere uygulanabilir.

## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı

```xaml
<object x:Name="XAMLNameValue".../>
```

## <a name="xaml-values"></a>XAML Değerleri

|||
|-|-|
|`XAMLNameValue`|[XamlName dilbilgisinde](xamlname-grammar.md)kısıtlamalara uygun bir dize.|

## <a name="remarks"></a>Açıklamalar

`x:Name`Bir Framework 'ün destek programlama modeline uygulandıktan sonra, ad bir nesne başvurusunu tutan değişkene veya bir Oluşturucu tarafından döndürülen örneğe eşdeğerdir.

Bir `x:Name` yönerge kullanımının değeri BIR xaml namescope içinde benzersiz olmalıdır. Varsayılan olarak, .NET XAML Hizmetleri API 'SI tarafından kullanıldığında, birincil XAML namescope tek XAML üretiminin XAML kök öğesinde tanımlanır ve bu XAML üretiminde bulunan öğeleri kapsar. Tek bir xaml üretimi içinde gerçekleşebilecek ek ayrık xaml ad kapsamları, belirli senaryolara yönelik olarak çerçeveler tarafından tanımlanabilir. Örneğin, WPF 'de yeni xaml ad kapsamları, bu xaml üretiminde de tanımlanan herhangi bir şablon tarafından tanımlanır ve oluşturulur. Xaml ad kapsamları hakkında daha fazla bilgi için (WPF için yazılmıştır ancak birçok xaml namescope kavramlarıyla ilgilidir), bkz. [WPF XAML ad kapsamları](/dotnet/desktop/wpf/advanced/wpf-xaml-namescopes).

Genel olarak, `x:Name` kullanılan durumlara de uygulanmamalıdır `x:Key` . Mevcut çerçevelere göre XAML uygulamaları, ve arasında değiştirme kavramları sunmuştur `x:Key` `x:Name` , ancak bu önerilen bir uygulamadır. .NET XAML Hizmetleri, veya gibi ad/anahtar bilgilerini işlerken bu tür değiştirme kavramlarını desteklemez <xref:System.Windows.Markup.INameScope> <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute> .

`x:Name`Ad benzersizlik zorlaması için, permitdiof 'ın yanı sıra, belirli uygulama çerçeveleri tarafından tanımlanmış olabilir. Ancak, .NET XAML Hizmetleri ile kullanılabilir olması için XAML namescope benzersizlerinin çerçeve tanımları <xref:System.Windows.Markup.INameScope> Bu belgelerdeki bilgilerin tanımıyla tutarlı olmalıdır ve bilgilerin uygulandığı ilgili kuralların aynısını kullanmalıdır. Örneğin, [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] uygulama çeşitli biçimlendirme öğelerini <xref:System.Windows.NameScope> kaynak sözlükleri, sayfa düzeyi XAML tarafından oluşturulan mantıksal ağaç, şablonlar ve diğer ertelenmiş içerik gibi ayrı aralıklarda böler ve ardından bu xaml nameslerinin her birinde xaml ad benzersizliği uygular.

.NET XAML Hizmetleri XAML nesne yazıcılarını kullanan özel türler için, bir tür üzerinde ile eşleşen bir özellik oluşturulabilir `x:Name` veya değiştirilebilir. Bu davranışı, tür tanımı kodundaki ile eşlenecek özelliğin adına başvurarak tanımlarsınız <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> .  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> bir tür düzeyi özniteliğidir.

Using.NET XAML Hizmetleri, XAML namescope desteği için yedekleme mantığı, arabirimi uygulayarak çerçeve nötr bir şekilde tanımlanabilir <xref:System.Windows.Markup.INameScope> .

## <a name="wpf-usage-notes"></a>WPF kullanım notları

[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]XAML, kısmi sınıflar ve arka plan kod kullanan bir uygulama için standart derleme yapılandırması altında, belirtilen, `x:Name` [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] bir işaretleme derleme oluşturma görevi tarafından işlendiğinde temel alınan kodda oluşturulan alanın adı olur ve bu alan nesneye bir başvuru içerir. Varsayılan olarak, oluşturulan alan dahili olur. [X:FieldModifier özniteliğini](xfieldmodifier-directive.md)belirterek alan erişimini değiştirebilirsiniz. WPF ve Silverlight 'ta sıra, biçimlendirme derlemesi tarafından tanımlanmakta ve kısmi bir sınıfta alanı isimlemedir, ancak değer başlangıçta boştur. Ardından, oluşturulan adlı bir yöntemi `InitializeComponent` sınıf oluşturucusunun içinden çağırılır. `InitializeComponent``FindName` `x:Name` giriş dizeleri olarak kısmı sınıfın XAML tarafından tanımlanan bölümünde bulunan her bir değeri kullanan çağrılardan oluşur. Dönüş değerleri, alan değerlerini XAML ayrıştırmasından oluşturulan nesnelerle birlikte dolduracak şekilde, benzer adlı alan başvurusuna atanır. Yürütülmesi, `InitializeComponent` `x:Name` `FindName` bir xaml tanımlı nesneye yönelik bir başvuruya ihtiyacınız olduğunda açık bir şekilde çağrı yapmak yerine, doğrudan/alan adını kullanarak çalışma zamanı nesne grafiğine başvuruda bulunmak mümkün hale getirir.

Microsoft Visual Basic hedeflerini kullanan ve derleme eylemiyle XAML dosyaları içeren bir WPF uygulaması için, `Page` `WithEvents` `x:Name` `Handles` olay işleyici temsilcileri için sözdizimini desteklemek üzere, anahtar sözcüğünü içeren tüm öğelere ekleyen derleme sırasında ayrı bir başvuru özelliği oluşturulur. Bu özellik her zaman geneldir. Daha fazla bilgi için bkz. [Visual Basic ve WPF olay işleme](/dotnet/desktop/wpf/advanced/visual-basic-and-wpf-event-handling).

`x:Name` , sayfanın (örneğin, bir kaynak sözlüğü için gevşek XAML) biçimlendirme tarafından derlenmediği durumlarda bile, yükleme zamanında XAML namescope 'a bir ad kaydetmek için WPF XAML işlemcisi tarafından kullanılır. Bu davranışın bir nedeni, `x:Name` bağlama için büyük olasılıkla gerekli olma nedenidir <xref:System.Windows.Data.Binding.ElementName%2A> . Ayrıntılar için bkz. [veri bağlamaya genel bakış](../data/data-binding-overview.md).

Daha önce belirtildiği gibi, `x:Name` (veya `Name` ) de kullanan durumlara uygulanmamalıdır `x:Key` . , [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.ResourceDictionary> Kendisini xaml namescope olarak tanımlamayı, ancak uygulanmadı veya API 'ler için null değerleri <xref:System.Windows.Markup.INameScope> Bu davranışı zorunlu kılmak için özel bir davranışa sahiptir. WPF XAML ayrıştırıcısı `Name` `x:Name` bir xaml tanımlı veya ile karşılaştığında <xref:System.Windows.ResourceDictionary> , ad herhangi bir xaml namescope 'a eklenmez. Bu adı herhangi bir XAML namescope 'dan bulmaya çalışırken `FindName` Yöntemler geçerli sonuçlar döndürmez.

### <a name="xname-and-name"></a>x:Name ve Name

Birçok WPF uygulama senaryosu, `x:Name` `Name` ve gibi önemli temel sınıfların birçoğu IÇIN varsayılan xaml ad alanında belirtildiği gibi, bağımlılık özelliği tarafından bu özniteliğin herhangi bir kullanımını önleyebilir <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement> . Çerçeve düzeyinde özelliği olmayan bir öğeye kod erişiminin önemli olduğu bazı yaygın XAML ve WPF senaryoları vardır `Name` . Örneğin, belirli animasyon ve film şeridi destek sınıfları bir `Name` özelliği desteklemez, ancak animasyonun denetlenmesi için genellikle kodda başvurulmaları gerekir. `x:Name`Daha sonra koddan daha sonra başvuruda bulunmak istiyorsanız, XAML 'de oluşturulan zaman çizelgelerinde ve dönüşümlerde bir öznitelik olarak belirtmeniz gerekir.

, <xref:System.Windows.FrameworkElement.Name%2A> Sınıfında bir özellik olarak kullanılabilir <xref:System.Windows.FrameworkElement.Name%2A> ve `x:Name` öznitelik olarak birbirinin yerine kullanılabilir, ancak aynı öğede her ikisi de belirtilmişse bir ayrıştırma özel durumu ortaya kalır. XAML biçimlendirme derlenmişse, özel durum biçimlendirme derlenmesi üzerinde gerçekleşir, aksi takdirde yük üzerinde oluşur.

<xref:System.Windows.FrameworkElement.Name%2A> XAML öznitelik sözdizimi kullanılarak ve kod kullanılarak ayarlanabilir <xref:System.Windows.DependencyObject.SetValue%2A> ; ancak, koddaki özelliği ayarlamanın, XAML <xref:System.Windows.FrameworkElement.Name%2A> 'in zaten yüklü olduğu çoğu durumda, xaml namescope içinde temsilci alan başvurusunu oluşturmadığını unutmayın. Kod içinde ayarlamayı denemek yerine, <xref:System.Windows.FrameworkElement.Name%2A> <xref:System.Windows.NameScope> uygun namescope 'da koddan yöntemler kullanın.

<xref:System.Windows.FrameworkElement.Name%2A> Ayrıca, iç metinle birlikte Özellik öğesi söz dizimi kullanılarak ayarlanabilir, ancak bu seyrek kullanılır. Buna karşılık, `x:Name` XAML özellik öğesi söz diziminde veya kullanılarak kodda ayarlanamaz <xref:System.Windows.DependencyObject.SetValue%2A> ; yalnızca bir yönergesi olduğu için nesneler üzerinde öznitelik söz dizimi kullanılarak ayarlanabilir.

## <a name="silverlight-usage-notes"></a>Silverlight kullanım notları

`x:Name` Silverlight için ayrı olarak belgelenmiştir. Daha fazla bilgi için bkz. [xaml ad alanı (x:) Dil özellikleri (Silverlight)](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95)).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>
- <xref:System.Windows.FrameworkContentElement.Name%2A?displayProperty=nameWithType>
- [WPF İçinde Ağaçlar](/dotnet/desktop/wpf/advanced/trees-in-wpf)
