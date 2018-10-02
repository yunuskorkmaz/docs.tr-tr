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
ms.openlocfilehash: 08594d9757596eed470ffba8b5b63a01c493c358
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48035064"
---
# <a name="xname-directive"></a>x:Name Yönergesi
XAML namescope XAML tanımlı öğeleri benzersiz olarak tanımlar. XAML ad kapsamları ve benzersizlik modellerini çerçeveleri, API'leri sağlar veya çalışma zamanında XAML oluşturulan nesne grafiğine erişerek davranışları uygulayın örneklenmiş nesnelere uygulanabilir.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xaml  
<object x:Name="XAMLNameValue".../>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`XAMLNameValue`|Kısıtlamalar, uygun bir dize [XamlName Dilbilgisi](../../../docs/framework/xaml-services/xamlname-grammar.md).|  
  
## <a name="remarks"></a>Açıklamalar  
 Sonra `x:Name` uygulanan bir framework programlama modeli yedekleme, adı, bir nesne başvurusu ya da Oluşturucu tarafından döndürülen bir örneğini tutan değişken eşdeğerdir.  
  
 Değerini bir `x:Name` yönerge kullanım bir XAML namescope içinde benzersiz olmalıdır. Birincil XAML namescope .NET Framework XAML Hizmetleri API'si tarafından kullanıldığında varsayılan olarak tek bir XAML üretim XAML kök öğe tanımlanır ve bu XAML üretimde bulunan öğeleri kapsar. İçinde tek bir XAML üretim oluşabilecek ek ayrık XAML ad kapsamları belirli senaryolara çerçevelerine tanımlanabilir. Örneğin, WPF içinde yeni XAML ad kapsamları tanımlanır ve bu XAML üretimde tanımlanmış herhangi bir şablon tarafından oluşturuldu. XAML ad kapsamları (WPF için birçok XAML namescope kavramları ilgili ancak yazılan) hakkında daha fazla bilgi için bkz: [WPF XAML ad kapsamları](../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md).  
  
 Genel olarak, `x:Name` de durumlarda uygulanmamalıdır `x:Key`. XAML uygulamaları belirli mevcut altyapılarınız tarafından sunulan arasında değiştirme kavramları `x:Key` ve `x:Name`, ancak bu önerilen bir yöntem değildir. .NET framework XAML hizmetlerinde ad/anahtarı bilgileri gibi ele alırken bu tür değiştirme kavramları desteklemiyor <xref:System.Windows.Markup.INameScope> veya <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>.  
  
 Kuralları permittance `x:Name` yanı sıra ad benzersizliğini zorlama olabilecek belirli uygulama çerçeveleri tarafından tanımlanır. Ancak, .NET Framework XAML hizmetlerinde ile kullanılabilmesi için XAML namescope benzersizlik framework tanımlarını tanımı ile tutarlı olmalıdır <xref:System.Windows.Markup.INameScope> bu belgedeki bilgiler ve aynı kuralları ile ilgili nereden kullanmalıdır bilgi uygulanır. Örneğin, [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] uygulaması ayrı çeşitli biçimlendirme öğelerini böler <xref:System.Windows.NameScope> aralıkları, kaynak sözlükleri gibi sayfa düzeyi XAML, şablonları ve diğer ertelenmiş içerik, oluşturduğunuz mantıksal ağaç ve ardından XAML uygular ad benzersizliğini her birinde bu XAML ad kapsamları.  
  
 .NET Framework XAML Hizmetleri XAML nesne yazıcılar kullanan özel türleri için bir özellik eşlenen `x:Name` üzerinde bir tür kurulamadı veya değiştirildi. İle eşlemek için özellik adını başvurarak bu davranışı tanımladığınız <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> türü tanımı kod.  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> bir tür düzeyi özniteliğidir.  
  
 Using.NET Framework XAML hizmetlerinde, XAML namescope destek yedekleme mantığını tanımlanabilir bir framework bağımsız şekilde uygulayarak <xref:System.Windows.Markup.INameScope> arabirimi.  
  
## <a name="wpf-usage-notes"></a>WPF kullanım notları  
 Standart yapı yapılandırması altında bir [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] XAML, kısmi sınıflar ve arka plan kod, belirtilen kullanan uygulama `x:Name` temel oluşturulan bir alanın adı haline gelen ne zaman kod [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme tarafından işlenen derleme derleme görevi ve bu alan nesnesine bir başvuru tutar. Varsayılan olarak oluşturulan alan gerçekleştirilir. Alan erişimini belirterek değiştirebileceğiniz [x: FieldModifier özniteliği](../../../docs/framework/xaml-services/x-fieldmodifier-directive.md). WPF ve Silverlight, biçimlendirme derleme tanımlar ve kısmi bir sınıf, ancak değeri alan adları başlangıçta boş olan sırasıdır. Ardından, adlı oluşturulan bir yöntem `InitializeComponent` içinde sınıf oluşturucu çağrılır. `InitializeComponent` oluşan `FindName` çağrılarını her birini kullanarak `x:Name` XAML tanımlı bir parçası kısmi sınıf mevcut değerleri dizeleri girin. Dönüş değerleri ayrıştırma alan değerlerini XAML oluşturulan nesnelerle doldurmak için benzer adlı bir alan başvuru sonra atanır. Yürütülmesini `InitializeComponent` çalışma süresi Nesne grafiğini kullanarak başvuru mümkün kılar `x:Name` / alan adı doğrudan çağırmak zorunda yerine `FindName` açıkça dilediğiniz zaman XAML tanımlı bir nesneye başvuru gerekir.  
  
 WPF için Microsoft Visual Basic kullanan uygulama hedefler ve XAML dosyaları içerir `Page` yapı eylemi, ayrı başvuru özelliği ekleyen derleme sırasında oluşturulan `WithEvents` anahtar sözcüğü bir olantümöğeleriçin`x:Name`desteklemek için `Handles` olay işleyicisi temsilcileri için söz dizimi. Bu özellik her zaman büyük/küçük harf geneldir. Daha fazla bilgi için [Visual Basic ve WPF olay işleme](../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md).  
  
 `x:Name` WPF XAML işlemcisi tarafından bir ad, sayfa biçimlendirme derlenmiş derleme Eylemler (örneğin, gevşek XAML kaynak sözlüğü) tarafından olduğu durumlarda bile yükleme zamanında bir XAML namescope kaydetmek için kullanılır. Bu davranış bir nedeni olduğundan `x:Name` için büyük olasılıkla gerekli <xref:System.Windows.Data.Binding.ElementName%2A> bağlama. Ayrıntılar için bkz [Data Binding Overview](../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 Daha önce de belirtildiği `x:Name` (veya `Name`) de durumlarda uygulanmamalıdır `x:Key`. [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.ResourceDictionary> Kendisi bir XAML namescope tanımlama ancak uygulanmadı veya null değerler için özel bir davranışı <xref:System.Windows.Markup.INameScope> API bu davranışı uygulanmasına yönelik bir yöntem olarak. WPF XAML ayrıştırıcı karşılaşırsa `Name` veya `x:Name` XAML tanımlı içinde <xref:System.Windows.ResourceDictionary>, adı için herhangi bir XAML namescope eklenmez. Tüm XAML namescope bu adından bulmaya çalışırken ve `FindName` yöntemleri değil geçerli sonuçlar döndürür.  
  
### <a name="xname-and-name"></a>x: Name ve adı  
 Birçok WPF uygulama senaryoları kullanımı kaçınabilirsiniz `x:Name` olduğundan, öznitelik `Name` bağımlılık özelliği olarak belirtilen varsayılan XAML ad alanı birkaç önemli temel sınıflar gibi <xref:System.Windows.FrameworkElement> ve <xref:System.Windows.FrameworkContentElement> aynı amaçla karşılar. XAML ve WPF bazı yaygın senaryolar hala var. burada erişim olmadan bir öğe için kod `Name` framework düzeyinde özelliğin önemlidir. Örneğin, bazı animasyon ve görsel taslak desteği sınıfları desteklemeyen bir `Name` özelliği, ancak bunlar genellikle gerekir animasyon denetlemek için kod içinde başvurulamaz. Belirtmeniz gerekir `x:Name` zaman çizelgeleri ve daha sonra koddan başvurmak istiyorsanız, XAML içinde oluşturulan dönüşümler özniteliği olarak.  
  
 Varsa <xref:System.Windows.FrameworkElement.Name%2A> sınıfta bir özellik olarak kullanılabilir <xref:System.Windows.FrameworkElement.Name%2A> ve `x:Name` öznitelikler birbirlerinin yerine kullanılabilir, ancak her ikisi de aynı öğede belirtilirse ayrıştırma özel durumu neden olur. XAML biçimlendirme ise özel durum aksi yüklendiğinde meydana gelir biçimlendirmesi derleme üzerinde ortaya çıkar.  
  
 <xref:System.Windows.FrameworkElement.Name%2A> XAML öznitelik sözdizimi kullanılarak ayarlanabilir ve kod kullanarak <xref:System.Windows.DependencyObject.SetValue%2A>; ancak Not söz konusu ayarın <xref:System.Windows.FrameworkElement.Name%2A> kod özelliğinde XAML nerede olduğunu zaten çoğu durumda XAML namescope içinde temsili alan başvurusu oluşturmaz yüklendi. Ayarlama girişimi yerine <xref:System.Windows.FrameworkElement.Name%2A> , kodunuzda kullanabileceğiniz <xref:System.Windows.NameScope> uygun namescope karşı koddan yöntemleri.  
  
 <xref:System.Windows.FrameworkElement.Name%2A> özellik öğesi sözdizimini iç metin ile kullanma da ayarlanabilir ancak seyrek olmasıdır. Buna karşılık, `x:Name` XAML özellik öğesi sözdizimine veya kod kullanarak ayarlanamaz <xref:System.Windows.DependencyObject.SetValue%2A>; çünkü bu bir yönerge nesneler üzerinde öznitelik sözdizimi kullanılarak yalnızca ayarlanabilir.  
  
## <a name="silverlight-usage-notes"></a>Silverlight kullanım notları  
 `x:Name` Silverlight için ayrı olarak belgelenmiştir. Daha fazla bilgi için [XAML Namespace (x:) Dil özellikleri (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=199081).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>  
 <xref:System.Windows.FrameworkContentElement.Name%2A?displayProperty=nameWithType>  
 [WPF İçinde Ağaçlar](../../../docs/framework/wpf/advanced/trees-in-wpf.md)
