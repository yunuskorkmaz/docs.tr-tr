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
ms.openlocfilehash: 9f812a49a3217a563be1bd7f1d999b641c28463d
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071453"
---
# <a name="xname-directive"></a>x:Name Yönergesi

XAML adskopundaki XAML tanımlı öğeleri benzersiz olarak tanımlar. XAML adskopları ve bunların benzersizlik modelleri, çerçeveler API'ler sağladığında veya xaml tarafından oluşturulan nesne grafiğine çalışma zamanında erişen davranışları uyguladığında, anında oluşturulan nesnelere uygulanabilir.

## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı

```xaml
<object x:Name="XAMLNameValue".../>
```

## <a name="xaml-values"></a>XAML Değerleri

|||
|-|-|
|`XAMLNameValue`|[XamlName Dilbilgisi](xamlname-grammar.md)kısıtlamalarına uygun bir dize.|

## <a name="remarks"></a>Açıklamalar

Bir `x:Name` çerçevenin destek programlama modeline uygulandıktan sonra, ad nesne başvuruyu veya bir oluşturucu tarafından döndürülen bir örneği tutan değişkene eşdeğerdir.

Bir `x:Name` yönerge kullanımının değeri bir XAML adalanında benzersiz olmalıdır. .NET XAML Services API tarafından kullanıldığında varsayılan olarak, birincil XAML adscope tek bir XAML üretiminin XAML kök elemanı tanımlanır ve bu XAML üretiminde bulunan öğeleri kapsar. Tek bir XAML üretimi içinde oluşabilecek ek ayrık XAML adskopları, belirli senaryoları ele alacak çerçevelerle tanımlanabilir. Örneğin, WPF'de yeni XAML adskopları, xaml üretiminde de tanımlanan herhangi bir şablon tarafından tanımlanır ve oluşturulur. XAML adscopes hakkında daha fazla bilgi için (WPF için yazılmış ancak birçok XAML ad-kapsam kavramları için alakalı), [WPF XAML Namescopes](../../framework/wpf/advanced/wpf-xaml-namescopes.md)bakın.

Genel olarak, `x:Name` aynı zamanda kullanan `x:Key`durumlarda uygulanmamalıdır. Belirli varolan çerçeveler tarafından XAML uygulamaları arasında `x:Key` ikame `x:Name`kavramları getirmiştir ve , ancak bu önerilen bir uygulama değildir. .NET XAML Hizmetleri, ad/anahtar bilgilerini işlerken bu tür <xref:System.Windows.Markup.INameScope> ikame kavramlarını desteklemez. <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>

İzin kurallarının `x:Name` yanı sıra benzersizlik zorlama adı potansiyel olarak belirli uygulama çerçeveleri tarafından tanımlanır. Ancak, .NET XAML Hizmetleri ile kullanılabilir olması için, XAML namescope benzersizliğinin çerçeve <xref:System.Windows.Markup.INameScope> tanımları bu belgelerdeki bilgilerin tanımıyla tutarlı olmalı ve bilgilerin uygulandığı yerle ilgili aynı kuralları kullanmalıdır. Örneğin, [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] uygulama çeşitli biçimlendirme öğelerini <xref:System.Windows.NameScope> kaynak sözlükleri, sayfa düzeyi XAML, şablonlar ve diğer ertelenmiş içerik tarafından oluşturulan mantıksal ağaç gibi ayrı aralıklara böler ve ardından bu XAML ad ayırım scopelarının her birinde XAML ad benzersizliğini zorlar.

.NET XAML Services XAML nesne yazarlarını kullanan özel `x:Name` türler için, bir türle eşlenen bir özellik kurulabilir veya değiştirilebilir. Bu davranışı, özellik adını tür tanımı <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> koduyla eşleştirmek için başvurarak tanımlarsınız.  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>tür düzeyinde bir özniteliktir.

XAML Hizmetleri Using.NET, XAML ad-scope desteği için destek mantığı <xref:System.Windows.Markup.INameScope> arabirimi uygulayarak çerçeve-nötr bir şekilde tanımlanabilir.

## <a name="wpf-usage-notes"></a>WPF Kullanım Notları

XAML, kısmi [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] sınıflar ve kod arkası kullanan bir uygulama için standart `x:Name` yapı yapılandırması altında, belirtilen bir biçimlendirme derleme oluşturma görevi tarafından işlendiğinde temel kodda [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] oluşturulan bir alanın adı olur ve bu alan nesneye bir başvuru tutar. Varsayılan olarak, oluşturulan alan iç. [X:FieldModifier özniteliğini](xfieldmodifier-directive.md)belirterek alan erişimini değiştirebilirsiniz. WPF ve Silverlight'ta, sıra, biçimlendirme derlemesinin alanı kısmi bir sınıfta tanımladığı ve adlandırır, ancak değer başlangıçta boştur. Daha sonra, oluşturulan `InitializeComponent` bir yöntem adlı sınıf oluşturucu içinden çağrılır. `InitializeComponent`giriş `FindName` dizeleri olarak `x:Name` kısmi sınıfın XAML tanımlı bölümünde var olan değerlerin her birini kullanan çağrılardan oluşur. İade değerleri daha sonra alan değerlerini XAML ayrıştırma oluşturulan nesnelerle doldurmak için benzer adlandırılmış alan başvurusuna atanır. Yürütme, `InitializeComponent` XAML tanımlı bir nesneye `x:Name` bir başvuru yapmanız gerektiğinde açıkça `FindName` aramak zorunda kalmak yerine, / alan adını kullanarak doğrudan çalışma zamanı nesnesi grafiğine başvuru yapmak mümkün kılar.

Microsoft Visual Basic hedeflerini kullanan ve yapı eylemi `Page` içeren XAML dosyalarını içeren bir WPF uygulaması `WithEvents` için, derleme sırasında olay `x:Name`işleyicisi temsilcileri için sözdizimini desteklemek `Handles` için anahtar kelimeyi içeren ayrı bir başvuru özelliği oluşturulur. Bu mülk her zaman halka açıktır. Daha fazla bilgi için [Visual Basic ve WPF Olay Yönetimi'ne](../../framework/wpf/advanced/visual-basic-and-wpf-event-handling.md)bakın.

`x:Name`WPF XAML işlemcisi tarafından, sayfanın yapı eylemleri (örneğin, kaynak sözlüğünün gevşek XAML'si) tarafından biçimlendirilmeyen durumlarda bile, yükleme zamanında bir XAML adskobuna bir ad kaydetmek için kullanılır. Bu davranışın bir nedeni, bağlama `x:Name` için <xref:System.Windows.Data.Binding.ElementName%2A> potansiyel olarak gerekli olmasıdır. Ayrıntılar için [veri bağlama genel bakış](../data/data-binding-overview.md)bakın.

Daha önce de `x:Name` belirtildiği `Name`gibi, (veya) de kullanan `x:Key`durumlarda uygulanmamalıdır. Bu [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.ResourceDictionary> davranışı uygulamak için bir yol olarak, kendisini XAML adskopu <xref:System.Windows.Markup.INameScope> olarak tanımlayan ancak UYGULANMAYan veya API'ler için null değerleri döndürme özel bir davranışı vardır. WPF XAML arayıcısı `Name` karşılaşırsa veya `x:Name` XAML tanımlı <xref:System.Windows.ResourceDictionary>bir durumda, ad herhangi bir XAML adskopuna eklenmez. Herhangi bir XAML adskopve `FindName` yöntemleri bu adı bulmaya çalışırken geçerli sonuçlar döndürmez.

### <a name="xname-and-name"></a>x:Adı ve Adı

Birçok WPF uygulama senaryosu öznitelik `x:Name` herhangi bir kullanımını `Name` önleyebilirsiniz, çünkü bağımlılık özelliği gibi önemli temel sınıfların birkaç <xref:System.Windows.FrameworkElement> için <xref:System.Windows.FrameworkContentElement> varsayılan XAML ad alanında belirtildiği gibi ve bu aynı amacı tatmin eder. Çerçeve düzeyinde özelliği olmayan `Name` bir öğeye kod erişiminin önemli olduğu bazı yaygın XAML ve WPF senaryoları hala vardır. Örneğin, belirli animasyon ve film şeridi destek `Name` sınıfları bir özelliği desteklemez, ancak animasyonu denetlemek için genellikle kodla başvurmaları gerekir. Daha sonra `x:Name` koddan başvurmak istiyorsanız, XAML'de oluşturulan zaman çizelgeleri ve dönüşümler üzerinde bir öznitelik olarak belirtmeniz gerekir.

Sınıfta <xref:System.Windows.FrameworkElement.Name%2A> bir özellik olarak kullanılabilir <xref:System.Windows.FrameworkElement.Name%2A> ve `x:Name` öznitelik olarak birbirinin yerine kullanılabilir, ancak her ikisi de aynı öğe üzerinde belirtilirse ayrıştırıkla özel durum ortaya çıkar. XAML biçimlendirme derlenmişse, özel durum biçimlendirme derlemesi üzerinde oluşur, aksi takdirde yükte oluşur.

<xref:System.Windows.FrameworkElement.Name%2A>XAML öznitelik sözdizimi kullanılarak ayarlanabilir ve <xref:System.Windows.DependencyObject.SetValue%2A>kod kullanılarak; ancak, özelliği <xref:System.Windows.FrameworkElement.Name%2A> kodolarak ayarlamanın, XAML'nin zaten yüklendiği çoğu durumda XAML adskopu içinde temsili alan başvurusu oluşturmadığını unutmayın. Kod ayarlamaya <xref:System.Windows.FrameworkElement.Name%2A> çalışmak yerine, <xref:System.Windows.NameScope> uygun ad skobuna karşı koddan yöntemler kullanın.

<xref:System.Windows.FrameworkElement.Name%2A>ayrıca iç metin ile özellik öğesi sözdizimi kullanılarak ayarlanabilir, ancak bu nadirdir. Buna karşılık, `x:Name` XAML özellik öğesi sözdizimi veya <xref:System.Windows.DependencyObject.SetValue%2A>kod kullanılarak ayarlanamaz; yalnızca bir yönerge olduğu için nesnelerüzerinde öznitelik sözdizimi kullanılarak ayarlanabilir.

## <a name="silverlight-usage-notes"></a>Silverlight Kullanım Notları

`x:Name`Silverlight için ayrı ayrı belgelenmiştir. Daha fazla bilgi için [Bkz. XAML Namespace (x:) Dil Özellikleri (Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95)).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>
- <xref:System.Windows.FrameworkContentElement.Name%2A?displayProperty=nameWithType>
- [WPF İçinde Ağaçlar](../../framework/wpf/advanced/trees-in-wpf.md)
