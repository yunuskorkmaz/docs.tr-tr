---
title: x:Key Yönergesi
ms.date: 03/30/2017
f1_keywords:
- xKey
- Key
- x:Key
helpviewer_keywords:
- x:Key attribute [XAML Services]
- Key attribute in XAML [XAML Services]
- XAML [XAML Services], x:Key attribute
ms.assetid: 1985cd45-f197-42d5-b75e-886add64b248
ms.openlocfilehash: 4ffd7a2922c7f3ba35ccb9ac7ce29a6a00cd99af
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837213"
---
# <a name="xkey-directive"></a>x:Key Yönergesi
Oluşturulan ve XAML tanımlı bir sözlükte başvurulan öğeleri benzersiz olarak tanımlar. `x:Key` değerini XAML nesnesi öğesine eklemek kaynak sözlüğünde bir kaynağı tanımlamanın en yaygın yoludur. Örneğin, WPF <xref:System.Windows.ResourceDictionary> öğesinde.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xaml  
<object x:Key="stringKeyValue".../>  
-or-  
<object x:Key="{markupExtensionUsage}".../>  
```  
  
## <a name="xaml-attribute-usage-wpf-specific"></a>XAML Öznitelik Kullanımı (WPF'ye özgü)  
  
```xaml  
<object.Resources>  
  <object x:Key="stringKeyValue".../>  
</object.Resources>  
-or-  
<object.Resources>  
  <object x:Key="{markupExtensionUsage}".../>  
</object.Resources>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`stringKeyValue`|Anahtar olarak kullanmak için metin dizesi. Metin dizesi [XamlName dilbilgisinde](xamlname-grammar.md)uyumlu olmalıdır.|  
|`markupExtensionUsage`|Biçimlendirme Uzantısı sınırlayıcıları {}, anahtar olarak kullanılacak bir nesne sağlayan bir biçimlendirme uzantısı kullanımı. Bkz. açıklamalar.|  
  
## <a name="remarks"></a>Açıklamalar  
 `x:Key` XAML kaynak sözlüğü kavramını destekler. XAML dil olarak kaynak sözlük uygulamasını desteklemez; başka bir deyişle UI framework'lerinde kalır. XAML kaynak sözlüklerinin WPF 'de nasıl uygulandığı hakkında daha fazla bilgi edinmek için bkz. [xaml kaynakları](../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
 XAML 2006 ve WPF 'de `x:Key` bir öznitelik olarak sağlanmalıdır. Dize olmayan anahtarlar kullanmaya devam edebilirsiniz, ancak bu öznitelik formunda dize olmayan değer sağlamak için bir biçimlendirme uzantısı kullanımı gerekir. XAML 2009 kullanıyorsanız, bir işaretleme uzantısı ara alanı gerektirmeden dizeler dışındaki nesne türlerine göre anahtarlı sözlükleri açıkça desteklemek için `x:Key` bir öğe olarak belirtilebilir. Bu konudaki "XAML 2009" bölümüne bakın. Açıklamalar bölümünün geri kalanı XAML 2006 uygulamasına özel olarak uygulanır.  
  
 `x:Key` öznitelik değeri [XamlName dilbilgisinde](xamlname-grammar.md) tanımlanmış herhangi bir dize olabilir veya bir işaretleme uzantısı aracılığıyla değerlendirilen bir nesne olabilir. WPF'den bir örnek için, bkz: "WPF Kullanım Notları".  
  
 <xref:System.Collections.IDictionary> uygulaması olan üst öğenin alt öğeleri genellikle bu sözlük dahilinde benzersiz anahtar değer belirten `x:Key` özniteliği içermelidir. Çerçeveler, özel türlerde `x:Key` için yedek olarak takma adlı anahtar özellikleri uygulayabilir; bu gibi özellikleri tanımlayan türler <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute> ile oluşturulmalıdır.  
  
 `x:Key` öğesini belirten kod eşdeğeri temel <xref:System.Collections.IDictionary> için kullanılan ana unsurdur. Örneğin WPF içindeki bir kaynak için işaretlemede uygulanan bir `x:Key`, kaynağı kod içindeki ,WPF <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> öğesine eklediğinizde <xref:System.Windows.ResourceDictionary> öğesinin `key` parametresinin değerine eşittir.  
  
## <a name="wpf-usage-notes"></a>WPF kullanım notları  
 WPF <xref:System.Collections.IDictionary> gibi, <xref:System.Windows.ResourceDictionary> uygulaması olan üst nesnenin alt nesneleri genellikle `x:Key` özniteliğini içermelidir ve anahtar değer bu sözlük dahilinde benzersiz olmalıdır. Dikkat çekici iki tür özel durum vardır:  
  
- Bazı WPF türleri sözlük kullanımı için bir örtülü anahtar bildirir. Örneğin  <xref:System.Windows.Style> ile bir <xref:System.Windows.Style.TargetType%2A> ya da  <xref:System.Windows.DataTemplate> ile bir <xref:System.Windows.DataTemplate.DataType%2A>, bir <xref:System.Windows.ResourceDictionary> içinde olabilir ve örtük anahtarı kullanabilir.  
  
- WPF birleştirilmiş bir kaynak sözcük kavramını destekler. Anahtarlar birleştirilmiş sözlükler arasında paylaşılabilir ve paylaşılan anahtar davranışına <xref:System.Windows.FrameworkContentElement.FindResource%2A> kullanılarak erişilebilir. Daha fazla bilgi için bkz. [birleştirilmiş kaynak sözlükleri](../wpf/advanced/merged-resource-dictionaries.md).  
  
 Genel WPF XAML uygulama ve uygulama modelinde, anahtar benzersizlik XAML biçimlendirme derleyici tarafından denetlenmez. Bunun yerine, eksik veya benzersiz olmayan `x:Key` değerleri yükleme zamanı XAML ayrıştırıcı hatalarına neden olur. Bununla birlikte, WPF sözlüklerinin Visual Studio tarafından işlenmesi genellikle tasarım aşamasında bu tür hataları da belirtebilir.  
  
 Gösterilen sözdiziminde, <xref:System.Windows.ResourceDictionary> nesnesinin, WPF XAML işlemcisinin <xref:System.Windows.FrameworkElement.Resources%2A> koleksiyonu doldurmak için bir koleksiyonu nasıl ürettiğinin örtülü olduğunu unutmayın. Bazı durumlarda Açıklık için istenirse bile <xref:System.Windows.ResourceDictionary> öğesi genellikle biçimlendirmede açık bir öğe olarak sağlanmaz (<xref:System.Windows.FrameworkElement.Resources%2A> özellik öğesi ve sözlüğü oluşturan öğeler arasında koleksiyon nesne öğesi olabilir). Bir koleksiyon nesnesinin biçimlendirme sırasında neredeyse her zaman örtük bir öğe olduğu hakkında bilgi için bkz. [XAML sözdizimi ayrıntılı](../wpf/advanced/xaml-syntax-in-detail.md).  
  
 WPF XAML uygulamasında kaynak sözlük anahtarlarını işleme anahtarları <xref:System.Windows.ResourceKey> soyut sınıfı tarafından tanımlanır. Ancak WPF XAML işlemcisi tuşlar için kendi kullanımları temelinde altta farklı uzantı türleri üretir. Örneğin bir <xref:System.Windows.DataTemplate> ya da herhangi bir türetilmiş sınıfı anahtarı ayrı olarak yönetilir ve ayrı bir <xref:System.Windows.DataTemplateKey> nesnesi oluşturur.  
  
 Anahtarlar ve adlar, XAML tanımında farklı yönergeler ve dil öğelerini (`x:Key` ve `x:Name`) kullanır. Ayrıca anahtarlar ve adlar, farklı durumlarda bu kavramların WPF tanımı ve uygulaması tarafından kullanılır. Ayrıntılar için bkz. [WPF xaml namescopes](../wpf/advanced/wpf-xaml-namescopes.md).  
  
 Yukarıda belirtildiği gibi, bir anahtarın değeri, biçimlendirme uzantısı ile sağlanabilir ve dize değerinden farklı olabilir. Örnek WPF senaryosu, `x:Key` değerinin bir [ComponentResourceKey](../wpf/advanced/componentresourcekey-markup-extension.md)olması olabilir. Belirli denetimler, tamamen stili değiştirmeden bu kontrolün görünümünün ve davranışının bir parçasını etkileyen özel stil kaynağı için o türde stil anahtarını gösterir. Böyle bir anahtarın örneği şudur: <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>.  
  
 WPF birleştirilmiş sözlük özelliği, anahtar benzersizlik ve anahtar arama çalışma biçimine ilişkin ek konuları tanıtır. Daha fazla bilgi için bkz. [birleştirilmiş kaynak sözlükleri](../wpf/advanced/merged-resource-dictionaries.md).  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009, `x:Key` her zaman öznitelik biçiminde sağlanacak kısıtlamayı gevyordu.  
  
 WPF 'de XAML 2009 özelliklerini kullanabilirsiniz, ancak yalnızca biçimlendirme ile derlenen XAML için. WPF için biçimlendirme derlenmiş XAML ve XAML 'nin BAML formu şu anda XAML 2009 anahtar sözcüklerini ve özelliklerini desteklememektedir.  
  
 XAML 2009 altında, aşağıdaki kullanım aracılığıyla `x:Key` öğeleri belirtebilirsiniz:  
  
### <a name="xaml-element-usage-xaml-2009-only"></a>XAML Öğesi Kullanımı (yalnızca XAML 2009)  
  
```xaml  
<object>  
  <x:Key>  
keyObject  
  </x:Key>  
...  
</object>  
```  
  
### <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`keyObject`|Bir özel sözlükte verilen `object` için anahtar olarak kullanılan bir nesne için nesne öğesi.|  
  
- Bu tür bir kullanım için kapsayıcı/üst burada gösterilmez. `object` özel sözlük uygulamasını temsil eden bir nesne öğesinin alt öğesi olması beklenir. `keyObject` bir nesne örneğinin (veya değer türünün bir değerinin) belirli özel sözlük uygulaması için anahtar olarak uygun olması beklenir.  
  
- WPF bu kullanımı gerektiren sözlükler uygulamaz. Nesne anahtarları, XAML dilinin daha genel bir özelliğidir ve XAML'de sözlük oluşturmanın arzu edildiği bazı özel sözlük senaryoları için belki yararlı olur. Dize olmayan kaynaklar, anahtarları oluşturmak ve belirtmek için diğer teknikler kullanan örtük stilleri gibi WFP özellikleri vardır, bu yüzden bir nesne anahtarı kullanılması gerekli değildir.  
  
- *keyObject* , doğrudan nesne örneği yerine nesne öğesi formunda biçimlendirme uzantısı kullanımı da olabilir.  
  
## <a name="silverlight-usage-notes"></a>Silverlight Kullanım Notları  
 `x:Key` Silverlight için ayrı olarak belgelenmiştir. Daha fazla bilgi için bkz. [xaml ad alanı (x:) Dil özellikleri (Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95)).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XAML Kaynakları](../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Kaynaklar ve Kod](../wpf/advanced/resources-and-code.md)
- [StaticResource İşaretleme Uzantısı](../wpf/advanced/staticresource-markup-extension.md)
