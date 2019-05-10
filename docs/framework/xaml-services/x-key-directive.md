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
ms.openlocfilehash: 5c18bbcc25ca0c1bab9d649552774b761635adf9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64659612"
---
# <a name="xkey-directive"></a>x:Key Yönergesi
Oluşturulan ve XAML tanımlı bir sözlükte başvurulan öğeleri benzersiz olarak tanımlar. Ekleme bir `x:Key` değerdir XAML nesnesi öğesine örneğin WPF içindeki bir kaynak sözlüğünde bir kaynağı tanımlamak için en yaygın yolu <xref:System.Windows.ResourceDictionary>.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```  
<object x:Key="stringKeyValue".../>  
-or-  
<object x:Key="{markupExtensionUsage}".../>  
```  
  
## <a name="xaml-attribute-usage-wpf-specific"></a>XAML öznitelik kullanımı (WPF'ye özgü)  
  
```  
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
|`stringKeyValue`|Bir anahtar olarak kullanmak için bir metin dizesi. Metin dizesi uymalıdır [XamlName Dilbilgisi](xamlname-grammar.md).|  
|`markupExtensionUsage`|Biçimlendirme uzantısı sınırlayıcıları içinde {}, bir anahtar olarak kullanılacak bir nesne sağlayan biçimlendirme uzantısı kullanımı. Açıklamalara bakın.|  
  
## <a name="remarks"></a>Açıklamalar  
 `x:Key` XAML kaynak sözlüğü kavramını destekler. XAML dil olarak belirli bir UI çerçeveleri için kalan kaynak sözlük uygulamasını tanımlamıyor. XAML kaynak sözlükleri WPF'de nasıl uygulandığı hakkında daha fazla bilgi için bkz: [XAML kaynakları](../wpf/advanced/xaml-resources.md).  
  
 XAML 2006 ve WPF'de içinde `x:Key` öznitelik olarak sağlanması gerekir. Dize olmayan anahtarlar kullanmaya devam edebilirsiniz, ancak bu öznitelik formunda dize olmayan değer sağlamak için bir biçimlendirme uzantısı kullanımı gerektirir. XAML 2009 kullanıyorsanız `x:Key` belirtilebilir bir öğe olarak nesne türleri tarafından Anahtarlanan sözlükleri açıkça desteklemek için dizeleri bir işaretleme uzantısı Ara gerek kalmadan. Bu konudaki "XAML 2009" bölümüne bakın. Açıklamalar bölümüne geri kalanı özellikle XAML 2006 uygulaması için geçerlidir.  
  
 Öznitelik değeri `x:Key` herhangi bir dize içinde tanımlanmış [XamlName Dilbilgisi](xamlname-grammar.md) veya bir işaretleme uzantısı aracılığıyla Değerlendirilmiş bir nesne olabilir. "WPF kullanım notları" wpf'den bir örnek için bkz.  
  
 Alt öğeleri olan bir üst öğenin bir <xref:System.Collections.IDictionary> uygulaması genellikle içermelidir bir `x:Key` Bu sözlük dahilinde benzersiz anahtar değer belirten özniteliği. Çerçeveler için yedek olarak takma adlı anahtar özellikleri uygulayabilir `x:Key` özel türlerde; gibi özellikleri tanımlayan türler ile oluşturulmalıdır <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>.  
  
 Belirten kod eşdeğeri `x:Key` arka plandaki için kullanılan anahtardır <xref:System.Collections.IDictionary>. Örneğin, bir `x:Key` , işaretlemede uygulanan bir kaynak WPF değerine eşdeğerdir için `key` parametresinin <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> WPF kaynak eklediğinizde, <xref:System.Windows.ResourceDictionary> kod.  
  
## <a name="wpf-usage-notes"></a>WPF kullanım notları  
 Üst alt nesnelerin nesnesini bir <xref:System.Collections.IDictionary> WPF gibi bir uygulama <xref:System.Windows.ResourceDictionary>, genellikle içermelidir bir `x:Key` özniteliği ve anahtar değer bu sözlük dahilinde benzersiz olmalıdır. İki önemli özel durum vardır:  
  
- Bazı WPF türleri sözlük kullanımı için bir örtülü anahtar bildirir. Örneğin, bir <xref:System.Windows.Style> ile bir <xref:System.Windows.Style.TargetType%2A>, veya bir <xref:System.Windows.DataTemplate> ile bir <xref:System.Windows.DataTemplate.DataType%2A>, kullanılabilir bir <xref:System.Windows.ResourceDictionary> ve örtük anahtarı kullanabilir.  
  
- WPF birleştirilmiş bir kaynak sözcük kavramını destekler. Anahtarlar birleştirilmiş sözlükler arasında paylaşılabilir ve paylaşılan anahtar davranışına kullanılarak erişilebilir <xref:System.Windows.FrameworkContentElement.FindResource%2A>. Daha fazla bilgi için [birleştirilmiş kaynak sözlükleri](../wpf/advanced/merged-resource-dictionaries.md).  
  
 Genel WPF XAML uygulama ve uygulama modelinde, anahtar benzersizlik XAML biçimlendirme derleyici tarafından denetlenmez. Bunun yerine, eksik veya benzersiz olmayan `x:Key` değerleri yükleme zamanı XAML ayrıştırıcı hatalarına neden olur. Ancak WPF için sözlüklerin Visual Studio işleme gibi hataları tasarım aşamasında unutmayın genellikle.  
  
 Gösterilen sözdiziminde unutmayın <xref:System.Windows.ResourceDictionary> nesnedir ve WPF XAML işlemcisinin doldurmak için bir koleksiyonu nasıl ürettiğinin örtülü bir <xref:System.Windows.FrameworkElement.Resources%2A> koleksiyonu. A <xref:System.Windows.ResourceDictionary> bazı durumlarda açıklık için istenirse olabilir ancak genellikle açıkça bir öğe olarak işaretleme, sağlanmamış (arasında koleksiyon nesne öğesi olabilir <xref:System.Windows.FrameworkElement.Resources%2A> özellik öğesi ve oluşturan öğeler Doldur Sözlük). Bir koleksiyon nesnesi işaretlemede örtülü bir öğe neredeyse her zaman neden olduğu hakkında daha fazla bilgi için bkz: [içinde XAML söz dizimi ayrıntı](../wpf/advanced/xaml-syntax-in-detail.md).  
  
 WPF XAML uygulamasında kaynak sözlük anahtarlarını işleme anahtarları tarafından tanımlanan <xref:System.Windows.ResourceKey> soyut sınıf. Ancak WPF XAML işlemcisi anahtarları kendi kullanımları temelinde altta farklı uzantı türleri üretir. Örneğin, anahtar için bir <xref:System.Windows.DataTemplate> veya türetilmiş bir sınıf ayrı olarak yönetilir ve farklı üretir <xref:System.Windows.DataTemplateKey> nesne.  
  
 Anahtarlar ve adlar kullanmak, farklı yönergeler ve Dil öğelerini (`x:Key` karşı `x:Name`) temel XAML tanımında. Ayrıca anahtarlar ve adlar farklı durumlarda bu kavramların uygulama ve WPF tanımı kullanılır. Ayrıntılar için bkz [WPF XAML ad kapsamları](../wpf/advanced/wpf-xaml-namescopes.md).  
  
 Daha önce belirtildiği gibi bir anahtarın değerini biçimlendirme uzantısı ile sağlanabilir ve dize değerinden farklı olabilir. Örnek bir WPF senaryosu, değeri `x:Key` olabilir bir [ComponentResourceKey](../wpf/advanced/componentresourcekey-markup-extension.md). Belirli denetimler, tamamen stili değiştirmeden görünümünün ve denetimin davranışını etkileyen özel stil kaynağı için bir stil anahtar türü ortaya çıkarır. Böyle bir anahtarın örneğidir <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>.  
  
 WPF birleştirilmiş sözlük özelliği, anahtar benzersizlik ve anahtar arama çalışma ilişkin ek konuları tanıtır. Daha fazla bilgi için [birleştirilmiş kaynak sözlükleri](../wpf/advanced/merged-resource-dictionaries.md).  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009 kısıtlamayı rahatlatır; `x:Key` öznitelik formunda her zaman sağlanmalıdır.  
  
 WPF içinde ancak yalnızca işaretleme yapılmayan XAML için XAML 2009 özelliklerini kullanabilirsiniz. WPF ve XAML, BAML formu için biçimlendirme derlenmiş XAML şu anda desteklemediğinden XAML 2009 anahtar sözcükleri ve özellikleri.  
  
 XAML 2009 altında belirttiğiniz `x:Key` öğelerini aşağıdaki kullanım aracılığıyla:  
  
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
|`keyObject`|Object öğesi için anahtar olarak kullanılan nesne için bir verilen `object` bir özel sözlükte.|  
  
- Bu tür bir kullanım için kapsayıcı/üst burada gösterilmez. `object` Özel sözlük uygulamasını temsil eden bir nesne öğesinin alt olması beklenir. `keyObject` bir nesne örneği (veya bir değer türünün bir değerinin) olması bekleniyor, belirli özel sözlük uygulaması için anahtar olarak uygun.  
  
- WPF bu kullanımı gerektiren sözlükler uygulamaz. Nesne anahtarları olan XAML içinde sözlük oluşturma arzu olduğu bazı özel sözlük senaryoları için belki yararlı XAML dilinin daha genel bir özelliğidir. Bu nedenle bir nesne anahtarı kullanılması gerekli değildir, dize olmayan kaynaklar için kullanan örtük stilleri gibi WFP özellikleri, oluşturma veya anahtarlarının belirterek için diğer teknikler vardır.  
  
- *keyObject* doğrudan nesne örneği yerine nesne öğesi biçiminde biçimlendirme uzantısı kullanımı da olabilir.  
  
## <a name="silverlight-usage-notes"></a>Silverlight kullanım notları  
 `x:Key` Silverlight için ayrı olarak belgelenmiştir. Daha fazla bilgi için [XAML Namespace (x:) Dil özellikleri (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=199081).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XAML Kaynakları](../wpf/advanced/xaml-resources.md)
- [Kaynaklar ve Kod](../wpf/advanced/resources-and-code.md)
- [StaticResource İşaretleme Uzantısı](../wpf/advanced/staticresource-markup-extension.md)
