---
title: x:Arguments Yönergesi
ms.date: 03/30/2017
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
ms.openlocfilehash: 338286b417c78b7cceeb30188e888928a15607cd
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458660"
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
|`methodName`|`x:Arguments` bağımsız değişkenlerini işlemek zorunda olan Factory yönteminin adı.|  
  
## <a name="dependencies"></a>Bağımlılıklar  
 `x:FactoryMethod`, `x:Arguments` uygulandığı kapsam ve davranışı değiştirebilir.  
  
 `x:FactoryMethod` belirtilmemişse `x:Arguments`, yedekleme oluşturucuların alternatif (varsayılan olmayan) imzaları için geçerlidir.  
  
 `x:FactoryMethod` belirtilirse, `x:Arguments` adlandırılmış yöntemin aşırı yüklemesi için geçerlidir.  
  
## <a name="remarks"></a>Açıklamalar  
 XAML 2006, başlatma metni aracılığıyla varsayılan olmayan başlatmayı destekleyebilir. Ancak, bir başlatma metni oluşturma tekniğinin pratik uygulaması sınırlıdır. Başlatma metni tek bir metin dizesi olarak değerlendirilir; Bu nedenle, özel bilgi öğelerini ve dizeden özel sınırlayıcıları ayrıştırabilen oluşturma davranışı için bir tür dönüştürücüsü tanımlanmadığı müddetçe yalnızca tek bir parametre başlatması için yetenek ekler. Ayrıca, nesne mantığından metin dizesi büyük olasılıkla belirli bir XAML ayrıştırıcısının, doğru bir dize dışındaki temelleri işlemek için yerel varsayılan tür dönüştürücütür.  
  
 `x:Arguments` XAML kullanımı, yönerge işaretlemesi kapsayan nesne öğesinin türüne başvurmadığından tipik anlamda Özellik öğesi kullanımı değildir. `x:Code` gibi diğer yönergelere daha fazla oturum vardır; burada öğe, biçimlendirmenin alt içerik için varsayılan değer olarak yorumlanacağı bir aralığı işaretler. Bu durumda, her bir nesne öğesinin XAML türü, `x:Arguments` kullanımı için hangi belirli Oluşturucu fabrikası yönteminin başvurulmaya çalışacağını belirleyen XAML Çözümleyicileri tarafından kullanılan bağımsız değişken türleriyle ilgili bilgileri iletişim kurar.  
  
 oluşturulan nesne öğesi için `x:Arguments`, nesne öğesinin diğer özellik öğelerinden, içerikten, iç metinden veya başlatma dizelerinden önce gelmelidir. `x:Arguments` içindeki nesne öğeleri, bu XAML türü ve onun yedekleme Oluşturucusu ya da fabrika yöntemi tarafından izin verilen öznitelikleri ve başlatma dizelerini içerebilir. Nesne veya bağımsız değişkenler için, oluşturulan önek eşlemelerine başvurarak varsayılan XAML ad alanı dışındaki özel XAML türlerini veya XAML türlerini belirtebilirsiniz.  
  
 XAML işlemcileri, `x:Arguments` ' de belirtilen bağımsız değişkenlerin bir nesne oluşturmak için nasıl kullanılacağını belirlemede aşağıdaki yönergeleri kullanır. `x:FactoryMethod` belirtilirse, bilgiler belirtilen `x:FactoryMethod` karşılaştırılır (`x:FactoryMethod` değerinin Yöntem adı olduğunu ve adlandırılmış yöntemin aşırı yüklemeleri olabileceğini unutmayın. `x:FactoryMethod` belirtilmemişse, bilgiler nesnenin tüm genel Oluşturucu aşırı yüklerini kümesiyle karşılaştırılır. XAML işleme mantığı, parametre sayısını karşılaştırır ve eşleşen parametre sayısına sahip aşırı yüklemeyi seçer. Birden fazla eşleşme varsa, XAML işlemcisi parametrelerin türlerini, belirtilen nesne öğelerinin XAML türlerine göre karşılaştırmalıdır. Hala birden fazla eşleşme varsa XAML işlemci davranışı tanımsızdır. Bir `x:FactoryMethod` belirtilirse, ancak yöntem çözümlenemiyorsa, bir XAML işlemcisi bir özel durum oluşturur.  
  
 XAML öznitelik kullanımı `<x:Arguments>string</x:Arguments>` teknik açıdan mümkündür. Bununla birlikte, bu, başlatma metni ve tür dönüştürücüler aracılığıyla ne yapabileceğinize ilişkin hiçbir özellik sağlamaz ve bu sözdiziminin kullanılması XAML 2009 fabrika yöntemi özelliklerinin tasarım amacı değildir.  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki örnek, parametresiz bir Oluşturucu imzasını, ardından bu imzaya erişen `x:Arguments` XAML kullanımını gösterir.  
  
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
  
 Aşağıdaki örnek, bir hedef fabrika yöntemi imzasını, ardından bu imzaya erişen `x:Arguments` XAML kullanımını gösterir.  
  
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
- [XAML'ye Genel Bakış (WPF)](../../desktop-wpf/fundamentals/xaml.md)
