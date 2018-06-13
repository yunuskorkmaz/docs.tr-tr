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
ms.openlocfilehash: 511721c3ffffb3b80b339c4671ad99e16bafda93
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565905"
---
# <a name="xkey-directive"></a>x:Key Yönergesi
Oluşturulan ve XAML tanımlı bir sözlükte başvurulan öğeleri benzersiz şekilde tanımlar. Ekleme bir `x:Key` değerdir XAML nesne öğesi için bir kaynak örneğin bir WPF içinde bir kaynak sözlüğü olarak tanımlamak için en yaygın yolu <xref:System.Windows.ResourceDictionary>.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```  
<object x:Key="stringKeyValue".../>  
-or-  
<object x:Key="{markupExtensionUsage}".../>  
```  
  
## <a name="xaml-attribute-usage-wpf-specific"></a>XAML öznitelik kullanımı (WPF özgü)  
  
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
|`stringKeyValue`|Bir anahtar olarak kullanılacak bir metin dizesi. Metin dizesi uygun olmalıdır [XamlName Dilbilgisi](../../../docs/framework/xaml-services/xamlname-grammar.md).|  
|`markupExtensionUsage`|Biçimlendirme uzantısı sınırlayıcıları içindeki {}, bir anahtar olarak kullanılacak bir nesne sağlayan bir biçimlendirme uzantısı kullanımı. Açıklamalar bakın.|  
  
## <a name="remarks"></a>Açıklamalar  
 `x:Key` XAML kaynağı sözlük kavramını destekler. Belirli kullanıcı Arabirimi çerçeveleri sol bir kaynak sözlüğü uygulaması, XAML dili olarak tanımlamıyor. WPF'de XAML kaynak sözlüklerindeki nasıl uygulandığı hakkında daha fazla bilgi için bkz: [XAML kaynakları](../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
 XAML 2006 ve WPF, `x:Key` bir özniteliği olarak sağlanması gerekir. Dize olmayan anahtarlarını kullanmaya devam edebilirsiniz, ancak bu öznitelik formda dize olmayan değeri sağlamak için bir biçimlendirme uzantısı kullanımı gerektirir. XAML 2009 kullanıyorsanız `x:Key` belirtilebilir bir öğe açıkça nesne türleri tarafından dışında anahtarlı sözlükler desteklemek için dizeleri Ara biçimlendirme uzantısı gerek kalmadan. Bu konudaki "XAML 2009" bölümüne bakın. Açıklamalar bölümüne geri kalanı özellikle XAML 2006 uygulaması için geçerlidir.  
  
 Öznitelik değeri `x:Key` herhangi bir dize olarak tanımlanabilir [XamlName Dilbilgisi](../../../docs/framework/xaml-services/xamlname-grammar.md) veya can biçimlendirme uzantısı aracılığıyla hesaplanan bir nesne olmalıdır. "WPF kullanım notları" WPF bir örnek için bkz.  
  
 Alt öğeleri olan bir üst öğesi bir <xref:System.Collections.IDictionary> uygulaması genellikle içermelidir bir `x:Key` Bu sözlük içinde benzersiz bir anahtar değeri belirten özniteliği. Çerçeveler yerine için anahtar özellikler diğer uygulamak `x:Key` belirli türlerinde; gibi özellikleri tanımlamak türleri ile öznitelikli <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>.  
  
 Belirtmenin kod eşdeğer `x:Key` arka plandaki için kullanılan anahtardır <xref:System.Collections.IDictionary>. Örneğin, bir `x:Key` uygulanan biçimlendirme WPF kaynak değerine denktir için `key` parametresinin <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> bir WPF kaynak eklediğinizde <xref:System.Windows.ResourceDictionary> kod.  
  
## <a name="wpf-usage-notes"></a>WPF kullanım notları  
 Bir üst alt nesnelerin nesne başka bir deyişle bir <xref:System.Collections.IDictionary> WPF gibi uygulama <xref:System.Windows.ResourceDictionary>, genellikle içermelidir bir `x:Key` özniteliği ve anahtar değeri bu sözlük içinde benzersiz olmalıdır. İki önemli özel durum vardır:  
  
-   Bazı WPF türleri sözlük kullanım için örtük bir anahtar bildirin. Örneğin, bir <xref:System.Windows.Style> ile bir <xref:System.Windows.Style.TargetType%2A>, veya bir <xref:System.Windows.DataTemplate> ile bir <xref:System.Windows.DataTemplate.DataType%2A>, kullanılabilir bir <xref:System.Windows.ResourceDictionary> ve örtülü anahtar kullanın.  
  
-   WPF birleştirilmiş kaynak sözlüğü kavramını destekler. Anahtarları birleştirilmiş sözlükler arasında paylaşılabilir ve paylaşılan anahtar davranışı kullanılarak erişilebilir <xref:System.Windows.FrameworkContentElement.FindResource%2A>. Daha fazla bilgi için bkz: [birleştirilmiş kaynak sözlükleri](../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md).  
  
 Genel WPF XAML uygulama ve uygulama modeli, anahtar benzersizlik XAML biçimlendirme derleyici tarafından kontrol edilmez. Bunun yerine, eksik veya benzer `x:Key` değerleri yükleme zamanı XAML ayrıştırıcı hatalarına neden olabilir. Ancak, sözlükler Visual Studio işleme WPF için bu tür hatalar genellikle tasarım aşamasında belirtebilirsiniz.  
  
 Gösterilen sözdiziminde unutmayın <xref:System.Windows.ResourceDictionary> nesnesidir nasıl WPF XAML işlemci üreten bir koleksiyonun doldurmak için örtük bir <xref:System.Windows.FrameworkElement.Resources%2A> koleksiyonu. A <xref:System.Windows.ResourceDictionary> bazı durumlarda daha anlaşılır olması için istediyseniz olabilir ancak genellikle açıkça biçimlendirme, bir öğe olarak sağlanmadı (bir koleksiyon nesnesi öğesi arasında olacaktır <xref:System.Windows.FrameworkElement.Resources%2A> özellik öğesi ve öğeleri içindeki doldurma Sözlük). Bir koleksiyon nesnesi örtük öğenin biçimlendirmesi içinde neredeyse her zaman neden olduğu hakkında daha fazla bilgi için bkz: [içinde XAML sözdizimi ayrıntı](../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).  
  
 WPF XAML uygulamasında kaynak sözlük anahtarları için işleme tarafından tanımlanan <xref:System.Windows.ResourceKey> soyut sınıf. Ancak WPF XAML işlemci kullanımlarının üzerinde temel anahtarları için farklı temel uzantı türleri oluşturur. Örneğin, anahtar için bir <xref:System.Windows.DataTemplate> veya türetilmiş bir sınıf ayrı ayrı işlenir ve farklı üretir <xref:System.Windows.DataTemplateKey> nesnesi.  
  
 Anahtarlar ve adları farklı yönergeleri ve dil öğeleri kullanın (`x:Key` karşı `x:Name`) temel XAML tanımı'nda. Ayrıca anahtarları ve adları farklı durumlarda WPF tanım ve bu kavramları uygulama tarafından kullanılır. Ayrıntılar için bkz [WPF XAML ad kapsamları](../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md).  
  
 Daha önce belirtildiği gibi bir anahtarın değerini biçimlendirme uzantısı aracılığıyla sağlanabilir ve dışında bir dize değeri olabilir. Örnek bir WPF senaryo, değeri `x:Key` olabilir bir[ComponentResourceKey](../../../docs/framework/wpf/advanced/componentresourcekey-markup-extension.md). Belirli denetimleri bu tür tamamen stili değiştirmeden bölümü görünümünü ve davranışını denetleyen etkilediğini özel stil kaynağı için bir stil anahtarı kullanır. Böyle bir anahtar örneğidir <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>.  
  
 WPF birleştirilmiş sözlük özelliği anahtar benzersizliği ve anahtar arama davranışı için ek hususlar sunmaktadır. Daha fazla bilgi için bkz: [birleştirilmiş kaynak sözlükleri](../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md).  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009 rahatlatır kısıtlama, `x:Key` özniteliği formunda her zaman sağlanmalıdır.  
  
 WPF'de, ancak yalnızca biçimlendirme-derlenmemiş XAML için XAML 2009 özellikleri kullanabilirsiniz. XAML biçimlendirme derlenmiş WPF ve XAML BAML form için şu anda desteklemediği XAML 2009 anahtar sözcükleri ve özellikler.  
  
 XAML 2009 altında belirttiğiniz `x:Key` aşağıdaki kullanımı aracılığıyla öğelerin:  
  
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
|`keyObject`|Object öğesi için anahtar olarak kullanılan nesne için bir verilen `object` özel sözlükteki.|  
  
-   Bu tür bir kullanım için kapsayıcı/üst burada gösterilmiyor. `object` Özel sözlük uygulamasını temsil eder bir nesne öğenin alt öğesi olması beklenir. `keyObject` bir nesne örneği (veya bir değer türünde bir değer) olması bekleniyor, belirli özel sözlük uygulaması için anahtar olarak uygun olmasıdır.  
  
-   WPF bu kullanımını gerektiren sözlükler uygulamıyor. Nesne anahtarları özelliğidir daha genel XAML'de sözlük oluşturma arzu olduğu belirli özel sözlük senaryolar için büyük olasılıkla yararlı XAML dili. Bir nesne anahtarı kullanarak gerekli değildir kaynaklar için dize olmayan tuşlarını örtülü stiller gibi WPF özellikleri için oluşturma veya anahtarları belirleme için başka teknikler, mevcut.  
  
-   *keyObject* biçimlendirme uzantısı kullanımı doğrudan nesne örneği yerine nesne öğesi formu de olabilir.  
  
## <a name="silverlight-usage-notes"></a>Silverlight kullanım notları  
 `x:Key` Silverlight için ayrı olarak belgelenmiştir. Daha fazla bilgi için bkz: [XAML Namespace (x:) Dil özellikleri (Silverlight)](http://go.microsoft.com/fwlink/?LinkId=199081).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XAML Kaynakları](../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [Kaynaklar ve Kod](../../../docs/framework/wpf/advanced/resources-and-code.md)  
 [StaticResource İşaretleme Uzantısı](../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)
