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
ms.openlocfilehash: eb9f9cc1dfdb802e340123d0d39e9c9ebaa457f0
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053758"
---
# <a name="xkey-directive"></a>x:Key Yönergesi
, XAML tanımlı bir sözlükte oluşturulan ve başvurulan öğeleri benzersiz şekilde tanımlar. Bir xaml nesne öğesine <xref:System.Windows.ResourceDictionary> değereklemek,kaynaksözlüğündebirkaynağı(örneğin,WPF)belirlemeninenyaygınyoludur.`x:Key`  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xaml  
<object x:Key="stringKeyValue".../>  
-or-  
<object x:Key="{markupExtensionUsage}".../>  
```  
  
## <a name="xaml-attribute-usage-wpf-specific"></a>XAML öznitelik kullanımı (WPF 'e özgü)  
  
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
|`stringKeyValue`|Anahtar olarak kullanılacak bir metin dizesi. Metin dizesi [XamlName dilbilgisinde](xamlname-grammar.md)uyumlu olmalıdır.|  
|`markupExtensionUsage`|Biçimlendirme Uzantısı sınırlayıcıları {}içinde, anahtar olarak kullanılacak bir nesne sağlayan bir biçimlendirme uzantısı kullanımı. Bkz. açıklamalar.|  
  
## <a name="remarks"></a>Açıklamalar  
 `x:Key`XAML kaynak sözlüğü kavramını destekler. Dil olarak XAML, belirli kullanıcı arabirimi çerçevelerine kalan bir kaynak sözlüğü uygulamasını tanımlamaz. XAML kaynak sözlüklerinin WPF 'de nasıl uygulandığı hakkında daha fazla bilgi edinmek için bkz. [xaml kaynakları](../wpf/advanced/xaml-resources.md).  
  
 XAML 2006 ve WPF `x:Key` 'de bir öznitelik olarak sağlanmalıdır. Dize olmayan anahtarlar kullanmaya devam edebilirsiniz, ancak öznitelik biçiminde dize olmayan değer sağlamak için bu bir biçimlendirme uzantısı kullanımı gerektirir. XAML 2009 kullanıyorsanız, `x:Key` bir işaretleme uzantısı ara alanı gerektirmeden dizeler dışındaki nesne türlerine göre anahtarlı sözlükleri açıkça desteklemek için bir öğe olarak belirtilebilir. Bu konudaki "XAML 2009" bölümüne bakın. Açıklamalar bölümünün geri kalanı XAML 2006 uygulamasına özel olarak uygulanır.  
  
 Öznitelik değeri `x:Key` [XamlName dilbilgisinde](xamlname-grammar.md) tanımlanmış herhangi bir dize olabilir veya bir işaretleme uzantısı aracılığıyla değerlendirilen bir nesne olabilir. WPF örneği için bkz. "WPF kullanım notları".  
  
 Bir <xref:System.Collections.IDictionary> uygulama olan üst öğenin alt öğeleri genellikle bu sözlük içinde benzersiz bir anahtar `x:Key` değeri belirten bir özniteliği içermelidir. Çerçeveler, belirli türlerin yerini alacak `x:Key` diğer ad anahtar özelliklerini uygulayabilir; bu tür özellikleri tanımlayan türler ile <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>ilişkilendirilebilmelidir.  
  
 Öğesinin `x:Key` kod eşdeğeri, temeldeki <xref:System.Collections.IDictionary>için kullanılan anahtardır. Örneğin, WPF içindeki `x:Key` bir kaynak için biçimlendirmede uygulanan bir kaynak, kodda bir WPF <xref:System.Windows.ResourceDictionary> 'e eklediğinizde `key` parametresinin <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> değerine eşdeğerdir.  
  
## <a name="wpf-usage-notes"></a>WPF kullanım notları  
 WPF <xref:System.Collections.IDictionary> `x:Key` gibi bir uygulama olan üst nesnenin alt nesneleri, genellikle bir özniteliği içermeli ve anahtar değeri bu sözlük içinde benzersiz olmalıdır. <xref:System.Windows.ResourceDictionary> İki önemli özel durumu vardır:  
  
- Bazı WPF türleri sözlük kullanımı için örtük bir anahtar bildirir. Örneğin <xref:System.Windows.Style> <xref:System.Windows.DataTemplate> <xref:System.Windows.DataTemplate.DataType%2A>,birile, veya ile, bir içinde <xref:System.Windows.ResourceDictionary> olabilir ve örtük anahtarı kullanabilir. <xref:System.Windows.Style.TargetType%2A>  
  
- WPF, birleştirilmiş bir kaynak sözlüğü kavramını destekler. Anahtarlar birleştirilmiş sözlükler arasında paylaşılabilir ve paylaşılan anahtar davranışına kullanılarak <xref:System.Windows.FrameworkContentElement.FindResource%2A>erişilebilir. Daha fazla bilgi için bkz. [birleştirilmiş kaynak sözlükleri](../wpf/advanced/merged-resource-dictionaries.md).  
  
 Genel WPF XAML uygulamasında ve uygulama modelinde, anahtar benzersizliği XAML biçimlendirme derleyicisi tarafından denetlenmez. Bunun yerine, eksik veya benzersiz `x:Key` olmayan değerler yükleme zamanı xaml Ayrıştırıcı hatalarına neden olur. Bununla birlikte, WPF sözlüklerinin Visual Studio tarafından işlenmesi genellikle tasarım aşamasında bu tür hataları da belirtebilir.  
  
 Gösterilen sözdiziminde, <xref:System.Windows.ResourceDictionary> nesnenin WPF XAML işlemcisinin bir <xref:System.Windows.FrameworkElement.Resources%2A> koleksiyonu doldurmak için bir koleksiyon üretmesinin örtük olduğunu unutmayın. Genellikle, biçimlendirme içinde bir öğe olarak açıkça sağlanmaz, ancak bazı durumlarda (örneğin, <xref:System.Windows.FrameworkElement.Resources%2A> Özellik öğesi ve içindeki öğeler arasında bir koleksiyon nesnesi öğesi olur) <xref:System.Windows.ResourceDictionary> sözlük). Bir koleksiyon nesnesinin biçimlendirme sırasında neredeyse her zaman örtük bir öğe olduğu hakkında bilgi için bkz. [XAML sözdizimi ayrıntılı](../wpf/advanced/xaml-syntax-in-detail.md).  
  
 WPF xaml uygulamasında kaynak sözlüğü anahtarları için işleme <xref:System.Windows.ResourceKey> soyut sınıf tarafından tanımlanır. Ancak WPF XAML işlemcisi, kullanımlarına göre anahtarlar için farklı temel uzantı türleri üretir. Örneğin, ya da türetilmiş bir <xref:System.Windows.DataTemplate> sınıfın anahtarı ayrı olarak işlenir ve ayrı <xref:System.Windows.DataTemplateKey> bir nesne oluşturur.  
  
 Anahtarlar ve adlar, temel xaml tanımında farklı yönergeler ve`x:Key` dil `x:Name`öğeleri (karşılık gelen) kullanır. Anahtarlar ve adlar Ayrıca, WPF tanımına ve bu kavramların uygulamasına göre farklı durumlarda kullanılır. Ayrıntılar için bkz. [WPF xaml namescopes](../wpf/advanced/wpf-xaml-namescopes.md).  
  
 Daha önce belirtildiği gibi, bir anahtarın değeri bir işaretleme uzantısı aracılığıyla sağlanabilir ve bir dize değerinden başka olabilir. Örnek WPF senaryosu, değerinin `x:Key` bir [ComponentResourceKey](../wpf/advanced/componentresourcekey-markup-extension.md)olması olabilir. Belirli denetimler, stili tamamen değiştirmeden bu denetimin görünümünü ve davranışını etkileyen özel bir stil kaynağı için bu türün bir stil anahtarını kullanıma sunar. Bu tür bir anahtara örnek olarak yer <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>verilir.  
  
 WPF birleştirilmiş sözlük özelliği, anahtar benzersizliği ve anahtar arama davranışına ilişkin ek konular sunar. Daha fazla bilgi için bkz. [birleştirilmiş kaynak sözlükleri](../wpf/advanced/merged-resource-dictionaries.md).  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009, öznitelik biçiminde `x:Key` her zaman sağlanacak kısıtlamayı gevyordu.  
  
 WPF 'de XAML 2009 özelliklerini kullanabilirsiniz, ancak yalnızca biçimlendirme ile derlenen XAML için. WPF için biçimlendirme derlenmiş XAML ve XAML 'nin BAML formu şu anda XAML 2009 anahtar sözcüklerini ve özelliklerini desteklememektedir.  
  
 XAML 2009 altında, aşağıdaki kullanım aracılığıyla `x:Key` öğeleri belirtebilirsiniz:  
  
### <a name="xaml-element-usage-xaml-2009-only"></a>XAML öğesi kullanımı (yalnızca XAML 2009)  
  
```  
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
|`keyObject`|Özel bir sözlükte verilen `object` için anahtar olarak kullanılan nesnenin nesne öğesi.|  
  
- Bu tür kullanım için kapsayıcı/üst öğe burada gösterilmez. `object`özel bir sözlük uygulamasını temsil eden bir nesne öğesinin alt öğesi olması beklenir. `keyObject`söz konusu özel sözlük uygulamasının anahtarı olarak uygun bir nesne örneği (veya bir değer türünün değeri) olması beklenir.  
  
- WPF bu kullanımı gerektiren sözlükler uygulamaz. Nesne anahtarları XAML dilinin genel bir özelliğidir, ancak XAML 'de sözlük oluşturmanın tercih edildiği belirli özel sözlük senaryoları için faydalı olabilir. Kaynaklar için dize olmayan anahtarlar kullanan örtük stiller gibi WPF özellikleri için, anahtarları oluşturmaya veya belirtmeye yönelik diğer teknikler mevcut değildir, bu nedenle bir nesne anahtarı kullanılması gerekli değildir.  
  
- *keyObject* , doğrudan nesne örneği yerine nesne öğesi formunda biçimlendirme uzantısı kullanımı da olabilir.  
  
## <a name="silverlight-usage-notes"></a>Silverlight kullanım notları  
 `x:Key`Silverlight için ayrı olarak belgelenmiştir. Daha fazla bilgi için bkz [. xaml ad alanı (x:) Dil özellikleri (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=199081).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XAML Kaynakları](../wpf/advanced/xaml-resources.md)
- [Kaynaklar ve Kod](../wpf/advanced/resources-and-code.md)
- [StaticResource İşaretleme Uzantısı](../wpf/advanced/staticresource-markup-extension.md)
