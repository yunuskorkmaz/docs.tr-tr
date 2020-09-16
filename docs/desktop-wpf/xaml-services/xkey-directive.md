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
ms.openlocfilehash: 7e4e9cbded01297818f9f01df01e95e94d7dc4af
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548279"
---
# <a name="xkey-directive"></a>x:Key Yönergesi
, XAML tanımlı bir sözlükte oluşturulan ve başvurulan öğeleri benzersiz şekilde tanımlar. Bir `x:Key` xaml nesne öğesine değer eklemek, kaynak sözlüğünde bir kaynağı (örneğin, WPF) belirlemenin en yaygın yoludur <xref:System.Windows.ResourceDictionary> .  
  
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
|`markupExtensionUsage`|Biçimlendirme Uzantısı sınırlayıcıları içinde {} , anahtar olarak kullanılacak bir nesne sağlayan bir biçimlendirme uzantısı kullanımı. Bkz. açıklamalar.|  
  
## <a name="remarks"></a>Açıklamalar  
 `x:Key` XAML kaynak sözlüğü kavramını destekler. Dil olarak XAML, belirli kullanıcı arabirimi çerçevelerine kalan bir kaynak sözlüğü uygulamasını tanımlamaz. XAML kaynak sözlüklerinin WPF 'de nasıl uygulandığı hakkında daha fazla bilgi edinmek için bkz. [xaml kaynakları](../fundamentals/xaml-resources-define.md).  
  
 XAML 2006 ve WPF 'de `x:Key` bir öznitelik olarak sağlanmalıdır. Dize olmayan anahtarlar kullanmaya devam edebilirsiniz, ancak öznitelik biçiminde dize olmayan değer sağlamak için bu bir biçimlendirme uzantısı kullanımı gerektirir. XAML 2009 kullanıyorsanız, `x:Key` bir işaretleme uzantısı ara alanı gerektirmeden dizeler dışındaki nesne türlerine göre anahtarlı sözlükleri açıkça desteklemek için bir öğe olarak belirtilebilir. Bu konudaki "XAML 2009" bölümüne bakın. Açıklamalar bölümünün geri kalanı XAML 2006 uygulamasına özel olarak uygulanır.  
  
 Öznitelik değeri `x:Key` [XamlName dilbilgisinde](xamlname-grammar.md) tanımlanmış herhangi bir dize olabilir veya bir işaretleme uzantısı aracılığıyla değerlendirilen bir nesne olabilir. WPF örneği için bkz. "WPF kullanım notları".  
  
 Bir uygulama olan üst öğenin alt öğeleri <xref:System.Collections.IDictionary> genellikle `x:Key` Bu sözlük içinde benzersiz bir anahtar değeri belirten bir özniteliği içermelidir. Çerçeveler, belirli türlerin yerini alacak diğer ad anahtar özelliklerini uygulayabilir `x:Key` ; Bu tür özellikleri tanımlayan türler ile ilişkilendirilebilmelidir <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute> .  
  
 Öğesinin kod eşdeğeri, `x:Key` temeldeki için kullanılan anahtardır <xref:System.Collections.IDictionary> . Örneğin, `x:Key` WPF içindeki bir kaynak için biçimlendirmede uygulanan bir kaynak, `key` <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> kodda bir WPF 'e eklediğinizde parametresinin değerine eşdeğerdir <xref:System.Windows.ResourceDictionary> .  
  
## <a name="wpf-usage-notes"></a>WPF kullanım notları  
 WPF gibi bir uygulama olan üst nesnenin alt nesneleri, <xref:System.Collections.IDictionary> <xref:System.Windows.ResourceDictionary> genellikle bir `x:Key` özniteliği içermeli ve anahtar değeri bu sözlük içinde benzersiz olmalıdır. İki önemli özel durumu vardır:  
  
- Bazı WPF türleri sözlük kullanımı için örtük bir anahtar bildirir. Örneğin, bir ile, <xref:System.Windows.Style> <xref:System.Windows.Style.TargetType%2A> veya ile, bir <xref:System.Windows.DataTemplate> <xref:System.Windows.DataTemplate.DataType%2A> içinde olabilir <xref:System.Windows.ResourceDictionary> ve örtük anahtarı kullanabilir.  
  
- WPF, birleştirilmiş bir kaynak sözlüğü kavramını destekler. Anahtarlar birleştirilmiş sözlükler arasında paylaşılabilir ve paylaşılan anahtar davranışına kullanılarak erişilebilir <xref:System.Windows.FrameworkContentElement.FindResource%2A> . Daha fazla bilgi için bkz. [birleştirilmiş kaynak sözlükleri](/dotnet/desktop/wpf/advanced/merged-resource-dictionaries).  
  
 Genel WPF XAML uygulamasında ve uygulama modelinde, anahtar benzersizliği XAML biçimlendirme derleyicisi tarafından denetlenmez. Bunun yerine, eksik veya benzersiz olmayan `x:Key` değerler yükleme zamanı xaml Ayrıştırıcı hatalarına neden olur. Bununla birlikte, WPF sözlüklerinin Visual Studio tarafından işlenmesi genellikle tasarım aşamasında bu tür hataları da belirtebilir.  
  
 Gösterilen sözdiziminde, <xref:System.Windows.ResourceDictionary> NESNENIN WPF XAML işlemcisinin bir koleksiyonu doldurmak için bir koleksiyon üretmesinin örtük olduğunu unutmayın <xref:System.Windows.FrameworkElement.Resources%2A> . <xref:System.Windows.ResourceDictionary>Genellikle, biçimlendirme içinde bir öğe olarak açıkça sağlanmaz, ancak bazı durumlarda (örneğin, <xref:System.Windows.FrameworkElement.Resources%2A> özellik öğesi ve sözlüğün dolduruldığı öğeler arasında bir koleksiyon nesnesi öğesi olur) olabilir. Bir koleksiyon nesnesinin biçimlendirme sırasında neredeyse her zaman örtük bir öğe olduğu hakkında bilgi için bkz. [XAML sözdizimi ayrıntılı](/dotnet/desktop/wpf/advanced/xaml-syntax-in-detail).  
  
 WPF XAML uygulamasında kaynak sözlüğü anahtarları için işleme <xref:System.Windows.ResourceKey> soyut sınıf tarafından tanımlanır. Ancak WPF XAML işlemcisi, kullanımlarına göre anahtarlar için farklı temel uzantı türleri üretir. Örneğin, <xref:System.Windows.DataTemplate> ya da türetilmiş bir sınıfın anahtarı ayrı olarak işlenir ve ayrı bir nesne oluşturur <xref:System.Windows.DataTemplateKey> .  
  
 Anahtarlar ve adlar, temel XAML tanımında farklı yönergeler ve dil öğeleri ( `x:Key` karşılık `x:Name` gelen) kullanır. Anahtarlar ve adlar Ayrıca, WPF tanımına ve bu kavramların uygulamasına göre farklı durumlarda kullanılır. Ayrıntılar için bkz. [WPF xaml namescopes](/dotnet/desktop/wpf/advanced/wpf-xaml-namescopes).  
  
 Daha önce belirtildiği gibi, bir anahtarın değeri bir işaretleme uzantısı aracılığıyla sağlanabilir ve bir dize değerinden başka olabilir. Örnek WPF senaryosu, değerinin `x:Key` bir [ComponentResourceKey](/dotnet/desktop/wpf/advanced/componentresourcekey-markup-extension)olması olabilir. Belirli denetimler, stili tamamen değiştirmeden bu denetimin görünümünü ve davranışını etkileyen özel bir stil kaynağı için bu türün bir stil anahtarını kullanıma sunar. Bu tür bir anahtara örnek olarak yer verilir <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A> .  
  
 WPF birleştirilmiş sözlük özelliği, anahtar benzersizliği ve anahtar arama davranışına ilişkin ek konular sunar. Daha fazla bilgi için bkz. [birleştirilmiş kaynak sözlükleri](/dotnet/desktop/wpf/advanced/merged-resource-dictionaries).  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009, `x:Key` öznitelik biçiminde her zaman sağlanacak kısıtlamayı gevyordu.  
  
 WPF 'de XAML 2009 özelliklerini kullanabilirsiniz, ancak yalnızca biçimlendirme ile derlenen XAML için. WPF için biçimlendirme derlenmiş XAML ve XAML 'nin BAML formu şu anda XAML 2009 anahtar sözcüklerini ve özelliklerini desteklememektedir.  
  
 XAML 2009 altında, `x:Key` aşağıdaki kullanım aracılığıyla öğeleri belirtebilirsiniz:  
  
### <a name="xaml-element-usage-xaml-2009-only"></a>XAML öğesi kullanımı (yalnızca XAML 2009)  
  
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
|`keyObject`|Özel bir sözlükte verilen için anahtar olarak kullanılan nesnenin nesne öğesi `object` .|  
  
- Bu tür kullanım için kapsayıcı/üst öğe burada gösterilmez. `object` özel bir sözlük uygulamasını temsil eden bir nesne öğesinin alt öğesi olması beklenir. `keyObject` söz konusu özel sözlük uygulamasının anahtarı olarak uygun bir nesne örneği (veya bir değer türünün değeri) olması beklenir.  
  
- WPF bu kullanımı gerektiren sözlükler uygulamaz. Nesne anahtarları XAML dilinin genel bir özelliğidir, ancak XAML 'de sözlük oluşturmanın tercih edildiği belirli özel sözlük senaryoları için faydalı olabilir. Kaynaklar için dize olmayan anahtarlar kullanan örtük stiller gibi WPF özellikleri için, anahtarları oluşturmaya veya belirtmeye yönelik diğer teknikler mevcut değildir, bu nedenle bir nesne anahtarı kullanılması gerekli değildir.  
  
- `keyObject` , doğrudan nesne örneği yerine nesne öğesi formunda biçimlendirme uzantısı kullanımı da olabilir.  
  
## <a name="silverlight-usage-notes"></a>Silverlight kullanım notları  
 `x:Key` Silverlight için ayrı olarak belgelenmiştir. Daha fazla bilgi için bkz. [xaml ad alanı (x:) Dil özellikleri (Silverlight)](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95)).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XAML Kaynakları](../fundamentals/xaml-resources-define.md)
- [Kaynaklar ve Kod](/dotnet/desktop/wpf/advanced/resources-and-code)
- [StaticResource Biçimlendirme Uzantısı](/dotnet/desktop/wpf/advanced/staticresource-markup-extension)
