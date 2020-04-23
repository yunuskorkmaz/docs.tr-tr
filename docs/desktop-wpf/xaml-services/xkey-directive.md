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
ms.openlocfilehash: c05f98932ceceeb1530b34a09b1923f2af1378b5
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071502"
---
# <a name="xkey-directive"></a>x:Key Yönergesi
XAML tanımlı sözlükte oluşturulan ve başvurulan öğeleri benzersiz olarak tanımlar. XAML nesne öğesine `x:Key` değer eklemek, kaynak sözlüğündeki bir kaynağı tanımlamanın en yaygın <xref:System.Windows.ResourceDictionary>yoludur, örneğin WPF'de.  
  
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
|`stringKeyValue`|Anahtar olarak kullanılacak metin dizesi. Metin dizesi [XamlName Dilbilgisine](xamlname-grammar.md)uygun olmalıdır.|  
|`markupExtensionUsage`|Biçimlendirme uzantısı sınırlayıcılar {}içinde, anahtar olarak kullanılacak bir nesne sağlayan bir biçimlendirme uzantısı kullanımı. Bkz. Açıklamalar.|  
  
## <a name="remarks"></a>Açıklamalar  
 `x:Key`XAML kaynak sözlüğü kavramını destekler. Bir dil olarak XAML, belirli UI çerçevelerine bırakılan bir kaynak sözlüğü uygulamasını tanımlamaz. XAML kaynak sözlüklerinin WPF'de nasıl uygulandığı hakkında daha fazla bilgi edinmek için Bkz. [XAML Kaynakları.](../fundamentals/xaml-resources-define.md)  
  
 XAML 2006 ve WPF'de öznitelik `x:Key` olarak sağlanmalıdır. Hala nonstring tuşları kullanabilirsiniz, ancak bu öznitelik formunda nonstring değeri sağlamak için bir biçimlendirme uzantısı kullanımı gerektirir. XAML 2009 kullanıyorsanız, `x:Key` bir biçimlendirme uzantısı ara gerek kalmadan dizeleri dışındaki nesne türleri tarafından anahtarlanmış sözlükleri açıkça desteklemek için bir öğe olarak belirtilebilir. Bu konudaki "XAML 2009" bölümüne bakın. Açıklamalar bölümünün geri kalanı özellikle XAML 2006 uygulaması için geçerlidir.  
  
 Öznitelik değeri `x:Key` [XamlName Grammar](xamlname-grammar.md) tanımlanan herhangi bir dize olabilir veya bir biçimlendirme uzantısı ile değerlendirilen bir nesne olabilir. WPF'den bir örnek için "WPF Kullanım Notları"na bakın.  
  
 <xref:System.Collections.IDictionary> Bir uygulama olan bir üst öğenin alt `x:Key` öğeleri genellikle bu sözlük içinde benzersiz bir anahtar değeri belirten bir öznitelik içermelidir. Çerçeveler, belirli `x:Key` türlerde yerine geçecek diğer adla temel özellikleri uygulayabilir; bu tür özellikleri tanımlayan türleri <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>ile atfedilen olmalıdır.  
  
 Belirtmenin kod eşdeğeri, temel `x:Key` <xref:System.Collections.IDictionary>altında yatan anahtardır. Örneğin, WPF'deki bir kaynak için biçimlendirmede uygulanan `x:Key` bir değer, kaynağı koddaki bir WPF'ye `key` <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> <xref:System.Windows.ResourceDictionary> eklediğinizde parametrenin değerine eşittir.  
  
## <a name="wpf-usage-notes"></a>WPF Kullanım Notları  
 WPF <xref:System.Collections.IDictionary> <xref:System.Windows.ResourceDictionary>gibi bir uygulama olan bir üst nesnenin alt nesneleri genellikle `x:Key` bir öznitelik içermelidir ve anahtar değeri bu sözlük içinde benzersiz olmalıdır. İki önemli istisna vardır:  
  
- Bazı WPF türleri sözlük kullanımı için örtük bir anahtar bildirir. Örneğin, bir <xref:System.Windows.Style> <xref:System.Windows.Style.TargetType%2A>, veya <xref:System.Windows.DataTemplate> a <xref:System.Windows.DataTemplate.DataType%2A>ile , bir <xref:System.Windows.ResourceDictionary> olabilir bir ve örtülü anahtarı kullanın.  
  
- WPF birleştirilmiş kaynak sözlüğü kavramını destekler. Anahtarlar birleştirilmiş sözlükler arasında paylaşılabilir ve paylaşılan anahtar davranışına <xref:System.Windows.FrameworkContentElement.FindResource%2A>.. Daha fazla bilgi [için, Birleştirilmiş Kaynak Sözlükleri'ne](../../framework/wpf/advanced/merged-resource-dictionaries.md)bakın.  
  
 Genel WPF XAML uygulama ve uygulama modelinde, anahtar benzersizliği XAML biçimlendirme derleyicisi tarafından denetlenmez. Bunun yerine, eksik `x:Key` veya benzersiz olmayan değerler yükleme süresi XAML ayrıştırıcı hatalarına neden olur. Ancak, WPF için sözlüklerin Visual Studio işleme genellikle tasarım aşamasında bu tür hataları fark edebilirsiniz.  
  
 Gösterilen sözdiziminde nesnenin, <xref:System.Windows.ResourceDictionary> WPF XAML işlemcisinin bir <xref:System.Windows.FrameworkElement.Resources%2A> koleksiyonu doldurmak için bir koleksiyon nasıl ürettiğine dolaylı olarak geldiğini unutmayın. A <xref:System.Windows.ResourceDictionary> genellikle biçimlendirmede bir öğe olarak açıkça sağlanmaz, ancak bazı durumlarda netlik için istenirse <xref:System.Windows.FrameworkElement.Resources%2A> (özellik öğesi ile sözlüğü dolduran öğeler arasında bir koleksiyon nesnesi öğesi olacaktır) olabilir. Bir koleksiyon nesnesi hemen hemen her zaman biçimlendirme de örtülü bir öğe neden hakkında bilgi için Ayrıntılı [Olarak XAML Sözdizimi](../../framework/wpf/advanced/xaml-syntax-in-detail.md)bakın.  
  
 WPF XAML uygulamasında, kaynak sözlük anahtarlarıiçin işleme <xref:System.Windows.ResourceKey> soyut sınıf tarafından tanımlanır. Ancak WPF XAML işlemci, kullanımlarına göre tuşlar için farklı temel uzantı türleri üretir. Örneğin, türetilmiş <xref:System.Windows.DataTemplate> bir sınıfın anahtarı ayrı ayrı işlenir <xref:System.Windows.DataTemplateKey> ve farklı bir nesne üretir.  
  
 Anahtarlar ve adlar temel XAML tanımında farklı yönergeler ve dil öğeleri (karşı)`x:Key` `x:Name`kullanır. Anahtarlar ve adlar da wpf tanımı ve bu kavramların uygulanması tarafından farklı durumlarda kullanılır. Ayrıntılar için [WPF XAML İsimSkopları'na](../../framework/wpf/advanced/wpf-xaml-namescopes.md)bakın.  
  
 Daha önce belirtildiği gibi, bir anahtarın değeri bir biçimlendirme uzantısı aracılığıyla sağlanabilir ve bir dize değeri dışında olabilir. Bir örnek WPF senaryo değeri `x:Key` bir [ComponentResourceKey](../../framework/wpf/advanced/componentresourcekey-markup-extension.md)olabilir. Belirli denetimler, stilin tamamen değiştirilmeden görünüm ve davranışının bir kısmını etkileyen özel bir stil kaynağı için bu tür bir stil anahtarını ortaya çıkarır. Böyle bir anahtar bir <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>örnek .  
  
 WPF birleştirilmiş sözlük özelliği, anahtar benzersizliği ve anahtar arama davranışı için ek hususlar sunar. Daha fazla bilgi [için, Birleştirilmiş Kaynak Sözlükleri'ne](../../framework/wpf/advanced/merged-resource-dictionaries.md)bakın.  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009 `x:Key` her zaman öznitelik formunda sağlanacak kısıtlamayı rahatlatır.  
  
 WPF'de XAML 2009 özelliklerini kullanabilirsiniz, ancak yalnızca biçimlendirmeyle derlenen XAML için. WPF için biçimlendirmeyle derlenen XAML ve XAML'nin BAML formu şu anda XAML 2009 anahtar kelimelerini ve özelliklerini desteklemez.  
  
 XAML 2009 altında, `x:Key` aşağıdaki kullanım yoluyla öğeleri belirtebilirsiniz:  
  
### <a name="xaml-element-usage-xaml-2009-only"></a>XAML Eleman Kullanımı (yalnızca XAML 2009)  
  
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
|`keyObject`|Özel bir sözlükte verilen `object` bir anahtar olarak kullanılan nesne öğesi.|  
  
- Bu tür kullanımiçin kapsayıcı/üst öğe burada gösterilmez. `object`özel sözlük uygulamasını temsil eden bir nesne öğesinin alt öğesi olması beklenir. `keyObject`belirli özel sözlük uygulaması için anahtar olarak uygun bir nesne örneği (veya bir değer türünün değeri) olması beklenir.  
  
- WPF bu kullanımı gerektiren sözlükler uygulamaz. Nesne anahtarları daha çok XAML dilinin genel bir özelliğidir ve büyük olasılıkla XAML'de sözlük oluşturmanın arzu edildiği belirli özel sözlük senaryoları için yararlıdır. Kaynaklar için dize olmayan anahtarları kullanan örtük stiller gibi WPF özellikleri için, anahtarları oluşturmak veya belirtmek için diğer teknikler vardır, bu nedenle nesne anahtarı kullanmak gerekli değildir.  
  
- `keyObject`doğrudan nesne örneği yerine nesne öğesi formunda biçimlendirme uzantısı kullanımı da olabilir.  
  
## <a name="silverlight-usage-notes"></a>Silverlight Kullanım Notları  
 `x:Key`Silverlight için ayrı ayrı belgelenmiştir. Daha fazla bilgi için [Bkz. XAML Namespace (x:) Dil Özellikleri (Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95)).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XAML Kaynakları](../fundamentals/xaml-resources-define.md)
- [Kaynaklar ve Kod](../../framework/wpf/advanced/resources-and-code.md)
- [StaticResource Biçimlendirme Uzantısı](../../framework/wpf/advanced/staticresource-markup-extension.md)
