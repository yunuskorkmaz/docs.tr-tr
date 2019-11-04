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
ms.openlocfilehash: 8a790ea964ffe399136a82ea298e1c7600f48366
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459970"
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
 `x:Name` bir Framework 'ün destek programlama modeline uygulandıktan sonra, ad bir nesne başvurusunu tutan değişkene veya bir Oluşturucu tarafından döndürülen örneğe eşdeğerdir.  
  
 Bir `x:Name` yönergesi kullanımının değeri bir XAML namescope içinde benzersiz olmalıdır. Varsayılan olarak, .NET Framework XAML Hizmetleri API 'SI tarafından kullanıldığında, birincil XAML namescope tek XAML üretiminin XAML kök öğesinde tanımlanır ve bu XAML üretiminde bulunan öğeleri kapsar. Tek bir xaml üretimi içinde gerçekleşebilecek ek ayrık xaml ad kapsamları, belirli senaryolara yönelik olarak çerçeveler tarafından tanımlanabilir. Örneğin, WPF 'de yeni xaml ad kapsamları, bu xaml üretiminde de tanımlanan herhangi bir şablon tarafından tanımlanır ve oluşturulur. Xaml ad kapsamları hakkında daha fazla bilgi için (WPF için yazılmıştır ancak birçok xaml namescope kavramlarıyla ilgilidir), bkz. [WPF XAML ad kapsamları](../wpf/advanced/wpf-xaml-namescopes.md).  
  
 Genel olarak, `x:Name` `x:Key`da kullanan durumlara uygulanmamalıdır. Mevcut çerçevelere göre XAML uygulamaları `x:Key` ve `x:Name`arasında değiştirme kavramları sunmuştur, ancak bu önerilen bir uygulamadır. .NET Framework XAML Hizmetleri, <xref:System.Windows.Markup.INameScope> veya <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>gibi ad/anahtar bilgilerini işlerken böyle bir değiştirme kavramlarını desteklemez.  
  
 Ad benzersizlik zorlamasının, büyük olasılıkla belirli uygulama çerçeveleri tarafından tanımlanan `x:Name` permittans kuralları. Ancak, .NET Framework XAML hizmetleriyle kullanılabilir olması için XAML namescope benzersizlerinin çerçeve tanımları bu belgelerde <xref:System.Windows.Markup.INameScope> bilgilerinin tanımıyla tutarlı olmalıdır ve bilgilerin nerede olduğu ile ilgili kuralların kullanılması gerekir uygulandı. Örneğin [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] uygulama, çeşitli biçimlendirme öğelerini kaynak sözlükleri, sayfa düzeyi XAML tarafından oluşturulan mantıksal ağaç, şablonlar ve diğer ertelenmiş içerik gibi ayrı <xref:System.Windows.NameScope> aralıklarına böler ve ardından XAML adını uygular Bu XAML ad copes değerlerinin her biri içinde benzersizlik.  
  
 .NET Framework XAML Hizmetleri XAML nesne yazıcılarını kullanan özel türler için, bir tür üzerinde `x:Name` eşleyen bir özellik oluşturulabilir veya değiştirilebilir. Bu davranışı, tür tanımı kodundaki <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> eşlenecek özelliğin adına başvurarak tanımlarsınız.  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>, tür düzeyi bir özniteliktir.  
  
 Using.NET Framework XAML Hizmetleri, XAML namescope desteği için yedekleme mantığı, <xref:System.Windows.Markup.INameScope> arabirimini uygulayarak çerçeve nötr bir şekilde tanımlanabilir.  
  
## <a name="wpf-usage-notes"></a>WPF kullanım notları  
 XAML, kısmi sınıflar ve arka plan kod kullanan bir [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] uygulaması için standart derleme yapılandırması altında, belirtilen `x:Name`, [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] bir işaretleme derleme derlemesi tarafından işlendiğinde temeldeki kodda oluşturulan alanın adı olur görev ve bu alan, nesnesine bir başvuru içerir. Varsayılan olarak, oluşturulan alan dahili olur. [X:FieldModifier özniteliğini](x-fieldmodifier-directive.md)belirterek alan erişimini değiştirebilirsiniz. WPF ve Silverlight 'ta sıra, biçimlendirme derlemesi tarafından tanımlanmakta ve kısmi bir sınıfta alanı isimlemedir, ancak değer başlangıçta boştur. Daha sonra, `InitializeComponent` adlı üretilmiş bir yöntem sınıf oluşturucusunun içinden çağırılır. `InitializeComponent`, giriş dizeleri olarak kısmi sınıfın XAML tarafından tanımlanan bölümünde bulunan `x:Name` değerlerinin her birini kullanarak `FindName` çağrılarından oluşur. Dönüş değerleri, alan değerlerini XAML ayrıştırmasından oluşturulan nesnelerle birlikte dolduracak şekilde, benzer adlı alan başvurusuna atanır. `InitializeComponent` yürütülmesi, XAML tanımlı bir nesneye başvurmanız gerektiğinde `FindName` açıkça çağırmak zorunda kalmadan, `x:Name`/alan adını kullanarak çalışma zamanı nesne grafiğine başvuruda bulunmak mümkün hale getirir.  
  
 Microsoft Visual Basic hedeflerini kullanan ve `Page` derleme eylemiyle XAML dosyaları içeren bir WPF uygulaması için, `WithEvents` anahtar sözcüğünü bir `x:Name`olan tüm öğelere ekleyen derleme sırasında ayrı bir başvuru özelliği oluşturulur @no olay işleyicisi temsilcileri için __t_3_ sözdizimi. Bu özellik her zaman geneldir. Daha fazla bilgi için bkz. [Visual Basic ve WPF olay işleme](../wpf/advanced/visual-basic-and-wpf-event-handling.md).  
  
 `x:Name`, WPF XAML işlemcisi tarafından, sayfanın derleme eylemleri (örneğin, bir kaynak sözlüğünün gevşek XAML gibi) ile derlenmediği durumlarda bile, yükleme zamanında XAML namescope 'a bir ad kaydetmek için kullanılır. Bu davranışın bir nedeni, `x:Name` <xref:System.Windows.Data.Binding.ElementName%2A> bağlama için gerekli olma nedenidir. Ayrıntılar için bkz. [veri bağlamaya genel bakış](../../desktop-wpf/data/data-binding-overview.md).  
  
 Daha önce de belirtildiği gibi, `x:Key`kullanan durumlarda `x:Name` (veya `Name`) uygulanmamalıdır. [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.ResourceDictionary>, kendisini XAML namescope olarak tanımlamayı, ancak uygulanmamış veya null değerleri <xref:System.Windows.Markup.INameScope> API 'Leri için bu davranışı zorlayabilmenin bir yöntemi olan özel bir davranış içerir. WPF XAML ayrıştırıcısı `Name` veya `x:Name` XAML tanımlı bir <xref:System.Windows.ResourceDictionary>karşılaşırsa, ad herhangi bir XAML namescope 'a eklenmez. Herhangi bir XAML namescope 'dan bu adı bulmaya çalışmak ve `FindName` yöntemleri geçerli sonuçları döndürmeyecektir.  
  
### <a name="xname-and-name"></a>x:Name ve Name  
 Birçok WPF uygulama senaryosu, <xref:System.Windows.FrameworkElement> ve <xref:System.Windows.FrameworkContentElement> gibi önemli temel sınıfların bazıları için varsayılan XAML ad alanında belirtilen `Name` bağımlılık özelliği `x:Name` özniteliğin herhangi bir kullanımını önleyebilir. Çerçeve düzeyinde `Name` özelliği olmayan bir öğeye kod erişiminin önemli olduğu bazı yaygın XAML ve WPF senaryoları vardır. Örneğin, belirli animasyon ve film şeridi destek sınıfları bir `Name` özelliğini desteklemez, ancak animasyonun denetlenmesi için genellikle kodda başvurulmaları gerekir. Daha sonra koddan daha sonra başvuruda bulunmak istiyorsanız, XAML 'de oluşturulan zaman çizelgelerinde ve dönüşümlerde bir öznitelik olarak `x:Name` belirtmelisiniz.  
  
 <xref:System.Windows.FrameworkElement.Name%2A> sınıf üzerinde bir özellik olarak kullanılabiliyorsa, <xref:System.Windows.FrameworkElement.Name%2A> ve `x:Name` öznitelikler olarak birbirinin yerine kullanılabilir, ancak aynı öğede her ikisi de belirtilmişse bir ayrıştırma özel durumu ortaya kalır. XAML biçimlendirme derlenmişse, özel durum biçimlendirme derlenmesi üzerinde gerçekleşir, aksi takdirde yük üzerinde oluşur.  
  
 <xref:System.Windows.FrameworkElement.Name%2A> XAML öznitelik sözdizimi kullanılarak ve kodda <xref:System.Windows.DependencyObject.SetValue%2A>kullanılarak ayarlanabilir. Ancak, koddaki <xref:System.Windows.FrameworkElement.Name%2A> özelliğini ayarlamanın, XAML 'in zaten yüklendiği çoğu durumda XAML namescope içinde temsilci alan başvurusunu oluşturmadığını unutmayın. Kodda <xref:System.Windows.FrameworkElement.Name%2A> ayarlamayı denemek yerine, uygun namescope 'da koddan <xref:System.Windows.NameScope> yöntemler kullanın.  
  
 <xref:System.Windows.FrameworkElement.Name%2A> Ayrıca, iç metinle birlikte Özellik öğesi söz dizimi kullanılarak ayarlanabilir, ancak bu sık görülen bir durumdur. Buna karşılık `x:Name` XAML özellik öğesi sözdiziminde veya <xref:System.Windows.DependencyObject.SetValue%2A>kullanılarak kodda ayarlanamaz; yalnızca bir yönerge olduğu için nesneler üzerinde öznitelik söz dizimi kullanılarak ayarlanabilir.  
  
## <a name="silverlight-usage-notes"></a>Silverlight kullanım notları  
 Silverlight için `x:Name` ayrı olarak belgelenmiştir. Daha fazla bilgi için bkz. [xaml ad alanı (x:) Dil özellikleri (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=199081).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>
- <xref:System.Windows.FrameworkContentElement.Name%2A?displayProperty=nameWithType>
- [WPF İçinde Ağaçlar](../wpf/advanced/trees-in-wpf.md)
