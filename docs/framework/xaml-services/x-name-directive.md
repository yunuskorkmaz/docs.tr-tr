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
ms.openlocfilehash: 7fcb7fe767e892109e48c5e56db26b5943b6ef13
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565856"
---
# <a name="xname-directive"></a>x:Name Yönergesi
XAML isim alanı XAML tanımlanan öğelerinde benzersiz olarak tanımlar. Çerçeveler API'leri sağlayın ya da XAML oluşturulan nesne grafiği çalışma zamanında erişme davranışlarını uygulamak XAML ad kapsamları ve kendi benzersizlik modelleri örneklenen nesnelere uygulanabilir.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xaml  
<object x:Name="XAMLNameValue".../>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`XAMLNameValue`|Kısıtlamaları için uygun bir dize [XamlName Dilbilgisi](../../../docs/framework/xaml-services/xamlname-grammar.md).|  
  
## <a name="remarks"></a>Açıklamalar  
 Sonra `x:Name` uygulanan bir çerçeve programlama modeli yedekleme, bir nesne başvurusu ya da bir Oluşturucu tarafından döndürülen bir örneğini tutan değişken adı eşdeğerdir.  
  
 Değeri bir `x:Name` yönerge kullanım XAML isim alanı içinde benzersiz olmalıdır. Birincil XAML isim alanı .NET Framework XAML Hizmetleri API tarafından kullanıldığında varsayılan olarak tek bir XAML üretim XAML Kök öğede tanımlanır ve bu XAML üretimde bulunan öğeleri kapsar. İçinde tek bir XAML üretim oluşabilecek ek ayrık XAML ad kapsamları belirli senaryolar için çerçeveleri tarafından tanımlanabilir. Örneğin, WPF içinde yeni XAML ad kapsamları tanımlanır ve bu XAML üretimde tanımlanmış herhangi bir şablonu tarafından oluşturulmuş. XAML ad kapsamları (birçok XAML isim alanı kavramları için ilgili ancak WPF için yazılmış) hakkında daha fazla bilgi için bkz: [WPF XAML ad kapsamları](../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md).  
  
 Genel olarak, `x:Name` de durumlarda uygulanmamalıdır `x:Key`. XAML uygulamaları belirli varolan çerçeveleri tarafından değiştirme kavramları arasında sunulan `x:Key` ve `x:Name`, ancak bu önerilen bir yöntem değildir. .NET framework XAML hizmetlerinde ad/anahtarı bilgileri gibi işlerken böyle değiştirme kavramları desteklemiyor <xref:System.Windows.Markup.INameScope> veya <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>.  
  
 Kurallar permittance için `x:Name` yanı sıra adı benzersizlik zorlama olası belirli uygulama çerçeveleri tarafından tanımlanır. Ancak, .NET Framework XAML Hizmetleri ile kullanılabilmesi için XAML isim alanı benzersizlik framework tanımlarını tanımı ile tutarlı olmalıdır <xref:System.Windows.Markup.INameScope> bu belgedeki bilgiler ve aynı kuralları ile ilgili where kullanmanız gerekir bilgileri uygulanır. Örneğin, [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] uygulama ayrı çeşitli biçimlendirme öğelerini böler <xref:System.Windows.NameScope> aralıkları, kaynak sözlüklerindeki gibi sayfa düzeyinde XAML, şablonları ve diğer ertelenmiş tarafından içerik, oluşturduğunuz mantıksal ağacının ve XAML uygular Bu XAML ad kapsamları her benzersiz adı olmasını sağlar.  
  
 .NET Framework XAML Hizmetleri XAML nesne yazıcılarının kullanan özel türler için bir özellik eşlenen `x:Name` üzerinde bir türü kurulan veya değiştirildi. İle eşlemek için özelliğinin adı başvurarak Bu davranış tanımladığınız <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> türü tanımı kod.  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> tür düzeyinde bir öznitelik değil.  
  
 Using.NET Framework XAML hizmetlerinde, XAML isim alanı desteği için yedekleme mantığı tanımlanabilir framework bağımsız şekilde uygulayarak <xref:System.Windows.Markup.INameScope> arabirimi.  
  
## <a name="wpf-usage-notes"></a>WPF kullanım notları  
 Standart yapı yapılandırması altında bir [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] XAML, kısmi sınıflar ve arka plan kodu, belirtilen kullanan uygulama `x:Name` temel oluşturulan bir alanın adı olur ne zaman kod [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme tarafından işlenir derleme derleme görevi oluşturup bu alan, bir nesneye başvuru tutar. Varsayılan olarak, oluşturulan iç alandır. Alan erişimi belirterek değiştirebileceğiniz [x: FieldModifier özniteliği](../../../docs/framework/xaml-services/x-fieldmodifier-directive.md). WPF ve Silverlight biçimlendirmesi derleme tanımlar ve adları bir parçalı sınıf ancak değeri alanında başlangıçta boş olan sırasıdır. Ardından, adlandırılmış bir oluşturulan yöntemi `InitializeComponent` içinde sınıf oluşturucu çağrılır. `InitializeComponent` oluşan `FindName` çağrılarını her birini kullanarak `x:Name` XAML tanımlanan kısmi sınıfının parçası bulunan değerleri Giriş dizeleri. Dönüş değerleri ayrıştırma XAML oluşturulan nesneleri alan değerlerle doldurmak için benzer adlı alanı referansı sonra atanır. Yürütülmesi `InitializeComponent` çalışma zamanında nesne grafiğini kullanarak referansı mümkün kılar `x:Name` / alan adı doğrudan çağırmak sahip olmak yerine `FindName` açıkça dilediğiniz zaman XAML tanımlı bir nesneye başvuru gerekir.  
  
 Bir WPF için Microsoft Visual Basic kullanan uygulamayı hedefler ve XAML dosyaları içerir `Page` yapı eylemi, ayrı başvuru özelliği ekler derleme sırasında oluşturulan `WithEvents` anahtar sözcüğü bir sahiptümöğeleri`x:Name`desteklemek için `Handles` olay işleyici temsilcileri sözdizimi. Bu özellik her zaman herkes tarafından kullanılabilir. Daha fazla bilgi için bkz: [Visual Basic ve WPF olay işleme](../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md).  
  
 `x:Name` WPF XAML işlemcisi tarafından bir ad sayfası biçimlendirme derlenmiş yapı eylemleri (örneğin, bir kaynak sözlüğü, gevşek XAML) tarafından olduğu durumlarda bile yükleme zamanında XAML isim alanı kaydetmek için kullanılır. Bu davranış nedenlerinden biri olduğundan `x:Name` için büyük olasılıkla gerekli <xref:System.Windows.Data.Binding.ElementName%2A> bağlama. Ayrıntılar için bkz [veri bağlama genel bakış](../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 Daha önce belirtildiği gibi `x:Name` (veya `Name`) de durumlarda uygulanmamalıdır `x:Key`. [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.ResourceDictionary> Kendisini XAML isim alanı tanımlama ancak uygulanmadı veya null değerler için özel bir davranışı vardır <xref:System.Windows.Markup.INameScope> Bu davranış uygulanmasına yönelik bir yöntem olarak API'leri. WPF XAML ayrıştırıcısı karşılaşırsa `Name` veya `x:Name` XAML tanımlı içinde <xref:System.Windows.ResourceDictionary>, adı herhangi XAML isim alanı eklenmez. Bu herhangi XAML isim alanı adından bulmaya çalışırken ve `FindName` yöntemleri değil geçerli sonuçları döndürür.  
  
### <a name="xname-and-name"></a>x: Name ve adı  
 Birçok WPF uygulama senaryoları herhangi bir kullanımından önleyebilirsiniz `x:Name` olduğundan, öznitelik `Name` bağımlılık özelliği olarak belirtilen varsayılan XAML ad uzayı birkaç önemli temel sınıflar gibi <xref:System.Windows.FrameworkElement> ve <xref:System.Windows.FrameworkContentElement> Bu aynı amaçla karşılar. Hala bazı ortak XAML ve WPF senaryolar vardır burada erişim bir öğeye sahip code `Name` framework düzeyinde özelliğin önemlidir. Örneğin, belirli animasyon ve film şeridi destek sınıfları desteklemeyen bir `Name` özelliği, ancak bunlar çoğunlukla gerekir animasyonun denetlemek için kod başvurulacak. Belirtmeniz gerekir `x:Name` zaman çizelgelerini ve bunları koddan daha sonra başvurmak istiyorsanız, XAML içinde oluşturulan dönüşümler özniteliği olarak.  
  
 Varsa <xref:System.Windows.FrameworkElement.Name%2A> sınıfı bir özellik olarak kullanılabilir <xref:System.Windows.FrameworkElement.Name%2A> ve `x:Name` niteliklerini birbirinin yerine kullanılabilir, ancak her ikisi de aynı öğede belirtilen bir ayrıştırma özel neden olur. XAML biçimlendirme derlenirken biçimlendirme ise, özel durum Aksi halde üzerindeki yükü oluşur biçimlendirmesi derleme üzerinde meydana gelir.  
  
 <xref:System.Windows.FrameworkElement.Name%2A> XAML öznitelik sözdizimi kullanılarak ayarlanabilir ve kod kullanarak <xref:System.Windows.DependencyObject.SetValue%2A>; ancak unutmayın, ayar <xref:System.Windows.FrameworkElement.Name%2A> özelliğinin kodda XAML olduğu zaten çoğu durumda XAML isim alanı içinde temsilcisi alan başvurusu oluşturmaz yüklendi. Ayarlama girişimi yerine <xref:System.Windows.FrameworkElement.Name%2A> kod içinde kullanma <xref:System.Windows.NameScope> uygun isim alanı karşı kodundan yöntemleri.  
  
 <xref:System.Windows.FrameworkElement.Name%2A> İç metinle özellik öğesi sözdizimini kullanarak da ayarlanabilir, ancak genel olarak görülmez. Buna karşılık, `x:Name` XAML özellik öğesi sözdizimini veya kod kullanarak ayarlanamaz <xref:System.Windows.DependencyObject.SetValue%2A>; bir yönerge olduğundan nesnelerde öznitelik sözdizimini kullanarak yalnızca ayarlanabilir.  
  
## <a name="silverlight-usage-notes"></a>Silverlight kullanım notları  
 `x:Name` Silverlight için ayrı olarak belgelenmiştir. Daha fazla bilgi için bkz: [XAML Namespace (x:) Dil özellikleri (Silverlight)](http://go.microsoft.com/fwlink/?LinkId=199081).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>  
 <xref:System.Windows.FrameworkContentElement.Name%2A?displayProperty=nameWithType>  
 [WPF İçinde Ağaçlar](../../../docs/framework/wpf/advanced/trees-in-wpf.md)
