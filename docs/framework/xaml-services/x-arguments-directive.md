---
title: x:Arguments Yönergesi
ms.date: 03/30/2017
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
ms.openlocfilehash: a18de9a07839f5b01620311832b85667680c12ad
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053827"
---
# <a name="xarguments-directive"></a>x:Arguments Yönergesi
XAML içindeki parametresiz bir Oluşturucu nesne öğesi bildirimi veya bir Factory yöntemi nesne bildirimi için paket oluşturma bağımsız değişkenleri.  
  
## <a name="xaml-element-usage-nonparameterless-constructor"></a>XAML öğesi kullanımı (parametresiz Oluşturucu)  
  
```xaml  
<object ...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-element-usage-factory-method"></a>XAML öğesi kullanımı (Factory yöntemi)  
  
```xaml  
<object x:FactoryMethod="methodName"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`oneOrMoreObjectElements`|, Parametresiz oluşturucuya veya fabrika yöntemine geçirilecek bağımsız değişkenleri belirten bir veya daha fazla nesne öğesi.<br /><br /> Tipik kullanım, gerçek bağımsız değişken değerlerini belirtmek için nesne öğeleri içinde başlatma metni kullanmaktır. Örnekler bölümüne bakın.<br /><br /> Öğelerin sırası önemlidir. Sırasıyla XAML türleri, yedekleme oluşturucusunun veya fabrika yöntemi aşırı yüklemesinin türleri ve tür sırasıyla eşleşmelidir.|  
|`methodName`|Herhangi bir `x:Arguments` bağımsız değişkeni işlemesi gereken fabrika yönteminin adı.|  
  
## <a name="dependencies"></a>Bağımlılıklar  
 `x:FactoryMethod`, geçerli olduğu yerde `x:Arguments` kapsamı ve davranışı değiştirebilir.  
  
 Hayır `x:FactoryMethod` belirtilirse, `x:Arguments` yedekleme oluşturucuların alternatif (varsayılan olmayan) imzaları için geçerlidir.  
  
 `x:FactoryMethod` Belirtilmişse ,`x:Arguments` adlandırılmış yöntemin aşırı yüklemesi için geçerlidir.  
  
## <a name="remarks"></a>Açıklamalar  
 XAML 2006, başlatma metni aracılığıyla varsayılan olmayan başlatmayı destekleyebilir. Ancak, bir başlatma metni oluşturma tekniğinin pratik uygulaması sınırlıdır. Başlatma metni tek bir metin dizesi olarak değerlendirilir; Bu nedenle, özel bilgi öğelerini ve dizeden özel sınırlayıcıları ayrıştırabilen oluşturma davranışı için bir tür dönüştürücüsü tanımlanmadığı müddetçe yalnızca tek bir parametre başlatması için yetenek ekler. Ayrıca, nesne mantığından metin dizesi büyük olasılıkla belirli bir XAML ayrıştırıcısının, doğru bir dize dışındaki temelleri işlemek için yerel varsayılan tür dönüştürücütür.  
  
 `x:Arguments` XAML kullanımı tipik anlamda Özellik öğesi kullanımı değildir, çünkü yönerge biçimlendirmesi kapsayan nesne öğesinin türüne başvurmuyor. Bu, öğenin, biçimlendirmenin alt içerik için varsayılan değer `x:Code` olarak yorumlanacağı bir aralığı nerede işaretlediği gibi diğer yönergelere daha fazla oturum açabilirsiniz. Bu durumda, her bir nesne öğesinin xaml türü, bir `x:Arguments` kullanımın başvuruya hangi belirli Oluşturucu fabrikası için imza olduğunu belirleyen xaml Çözümleyicileri tarafından kullanılan bağımsız değişken türleriyle ilgili bilgileri iletişim kurar.  
  
 `x:Arguments`oluşturulmakta olan bir nesne öğesinin, nesne öğesinin diğer özellik öğelerinden, içerik, iç metin veya başlatma dizelerinin önünde olması gerekir. İçindeki `x:Arguments` nesne öğeleri, bu xaml türü ve onun yedekleme Oluşturucusu ya da fabrika yöntemi tarafından izin verilen öznitelikleri ve başlatma dizelerini içerebilir. Nesne veya bağımsız değişkenler için, oluşturulan önek eşlemelerine başvurarak varsayılan XAML ad alanı dışındaki özel XAML türlerini veya XAML türlerini belirtebilirsiniz.  
  
 XAML işlemcileri, ' de `x:Arguments` belirtilen bağımsız değişkenlerin bir nesne oluşturmak için nasıl kullanılması gerektiğini belirlemede aşağıdaki yönergeleri kullanır. Belirtilmişse, bilgiler belirtilen `x:FactoryMethod` ile karşılaştırılır (değerinin yöntemin adı `x:FactoryMethod` olduğunu ve adlandırılmış yöntemin aşırı yüklemeleri olabileceğini unutmayın. `x:FactoryMethod` `x:FactoryMethod` Belirtilmemişse, bilgiler nesnenin tüm genel Oluşturucu aşırı yüklerini kümesiyle karşılaştırılır. XAML işleme mantığı, parametre sayısını karşılaştırır ve eşleşen parametre sayısına sahip aşırı yüklemeyi seçer. Birden fazla eşleşme varsa, XAML işlemcisi parametrelerin türlerini, belirtilen nesne öğelerinin XAML türlerine göre karşılaştırmalıdır. Hala birden fazla eşleşme varsa XAML işlemci davranışı tanımsızdır. Bir `x:FactoryMethod` , belirtilmişse ancak yöntem çözümlenemiyorsa, bir XAML işlemcisi bir özel durum oluşturur.  
  
 XAML öznitelik kullanımı `<x:Arguments>string</x:Arguments>` teknik açıdan mümkündür. Bununla birlikte, bu, başlatma metni ve tür dönüştürücüler aracılığıyla ne yapabileceğinize ilişkin hiçbir özellik sağlamaz ve bu sözdiziminin kullanılması XAML 2009 fabrika yöntemi özelliklerinin tasarım amacı değildir.  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki örnek, parametresiz bir Oluşturucu imzasını, ardından bu imzaya erişen xaml kullanımını `x:Arguments` gösterir.  
  
```csharp  
public class Food {  
    private string _name;  
    private Int32 _calories;  
    public Food(string name, Int32 calories) {  
        _name=name;  
        _calories=calories;  
    }  
}  
```  
  
```xaml  
<my:Food>  
    <x:Arguments>  
        <x:String>Apple</x:String>  
        <x:Int32>150</x:Int32>  
    </x:Arguments>  
</my:Food>  
```  
  
 Aşağıdaki örnek, bir hedef fabrika yöntemi imzasını, ardından bu imzaya erişen xaml kullanımını `x:Arguments` gösterir.  
  
```csharp  
public Food TryLookupFood(string name)  
{  
  switch (name) {  
    case "Apple": return new Food("Apple",150);  
    case "Chocolate": return new Food("Chocolate",200);  
    case "Cheese": return new Food("Cheese", 450);  
    default: {return new Food(name,0);  
  }  
}  
```  
  
```xaml  
<my:Food x:FactoryMethod="TryLookupFood">  
    <x:Arguments>  
        <x:String>Apple</x:String>  
    </x:Arguments>  
</my:Food>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework XAML Hizmetlerinde Kullanılacak Özel Türleri Tanımlama](defining-custom-types-for-use-with-net-framework-xaml-services.md)
- [XAML'ye Genel Bakış (WPF)](../wpf/advanced/xaml-overview-wpf.md)
