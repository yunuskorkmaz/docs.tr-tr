---
title: x:Arguments Yönergesi
ms.date: 03/30/2017
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
ms.openlocfilehash: a87542513ffeeec7efc526d4218f921d1b7579a1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61953965"
---
# <a name="xarguments-directive"></a>x:Arguments Yönergesi
Paketleri yapım bağımsız XAML varsayılan olmayan bir oluşturucu nesne öğe bildiriminde ya da bir fabrika yöntemi nesne bildirimi.  
  
## <a name="xaml-element-usage-nondefault-constructor"></a>XAML öğesi kullanımı (varsayılan oluşturucu)  
  
```  
<object ...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-element-usage-factory-method"></a>XAML öğesi kullanımı (Üreteç yöntemi)  
  
```  
<object x:FactoryMethod="methodName"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`oneOrMoreObjectElements`|Yedekleme varsayılan olmayan oluşturucu veya Fabrika yöntemine geçirilecek bağımsız değişkenleri belirten bir veya daha fazla nesne öğeler.<br /><br /> Tipik kullanım gerçek bağımsız değişken değerlerini belirtmek için nesne öğelerini başlatma metinde kullanmaktır. Örnekler bölümüne bakın.<br /><br /> Öğelerin sırasını büyük/küçük harf önemlidir. XAML türleri sırayla, türlerinin eşleşmesi ve yedekleme Oluşturucusu veya Fabrika yöntemi aşırı yüklemesini sırasını yazın.|  
|`methodName`|Tüm işlemelisiniz Üreteç yöntemi adını `x:Arguments` bağımsız değişkenler.|  
  
## <a name="dependencies"></a>Bağımlılıklar  
 `x:FactoryMethod` kapsam ve davranışını değiştirebilirsiniz burada `x:Arguments` uygular.  
  
 Hayır ise `x:FactoryMethod` belirtilen `x:Arguments` yedekleme oluşturucular alternatif (varsayılan olmayan) imzalar için geçerlidir.  
  
 Varsa `x:FactoryMethod` belirtilen `x:Arguments` adlandırılmış yöntemi aşırı yüklemesi için geçerlidir.  
  
## <a name="remarks"></a>Açıklamalar  
 XAML 2006 başlatma metnin varsayılan olmayan başlatma destekleyebilir. Ancak, bir başlatma metin oluşturma teknik uygulaması pratik sınırlıdır. Başlatma metin tek metin dizesi olarak kabul edilir; Bu nedenle, bir tür dönüştürücüsü özel bilgi öğeleri ve özel sınırlayıcıları dizesinden ayrıştırabilen oluşturma davranışı için tanımlı olmadığı sürece yalnızca tek bir parametre başlatma özelliği ekler. Ayrıca, nesne mantığı potansiyel olarak doğru bir dize dışında temelleri işlemek için bir verilen XAML ayrıştırıcı ait yerel varsayılan tür dönüştürücüsü metindir.  
  
 `x:Arguments` XAML kullanım değil özellik öğesi kullanımı tipik anlamında yönerge biçimlendirme içeren nesne öğe türünün başvurmadığından. Gibi diğer yönergeleri yakındır daha fazla `x:Code` burada öğe demarks içine işaretleme yorumlanabilir alt içeriğini için varsayılan olarak dışındaki bir aralık. Bu durumda, her nesne öğesi XAML türü XAML ayrıştırıcıları tarafından hangi belirli Oluşturucusu Fabrika yöntem imzası belirlemek için kullanılan bağımsız değişken türleri hakkında bilgi iletişim kuran bir `x:Arguments` kullanım başvurmak çalışıyor.  
  
 `x:Arguments` bir nesne öğesi için yapılandırılan herhangi diğer özellik öğeleri, içerik, iç metni veya nesne öğesi başlatma dizeleri gelmelidir. Nesne öğeleri içinde `x:Arguments` öznitelikleri ve başlatma dizeleri, XAML türü ve yedekleme Oluşturucusu veya Fabrika yöntemi tarafından izin verildiğinde içerebilir. Nesne veya bağımsız değişkenleri için özel bir XAML türleri ya da aksi takdirde varsayılan XAML ad alanı dışında belirlenen önek eşletirmeleri başvurarak XAML türlerini belirtebilirsiniz.  
  
 XAML işlemci bağımsız değişkenlerin nasıl belirtilen belirlemek için aşağıdaki yönergeleri kullanın `x:Arguments` bir nesne oluşturmak için kullanılmalıdır. Varsa `x:FactoryMethod` belirtilirse, bilgi karşılaştırılır belirtilen `x:FactoryMethod` (unutmayın değerini `x:FactoryMethod` yöntem adı ve aşırı yüklemeleri adlandırılmış yöntemi olabilir. Varsa `x:FactoryMethod` belirtilmezse, bilgi, nesnenin tüm ortak oluşturucu aşırı yüklemeleri kümesine karşılaştırılır. XAML işleme mantığı, parametrelerin sayısıyla karşılaştırır ve aşırı yükleme ile eşleşen kutup seçer. Birden fazla eşleşme varsa, XAML işlemci sağlanan nesne öğeleri XAML türlerine bağlı parametre türleri karşılaştırmanız gerekir. Yine de birden çok eşleşme varsa, XAML işlemci davranışı tanımsızdır. Varsa bir `x:FactoryMethod` belirtildi ancak metodu nelze rozpoznat, XAML işlemci özel bir durum oluşturmamalıdır.  
  
 XAML öznitelik kullanımı `<x:Arguments>string</x:Arguments>` teknik olarak mümkündür. Ancak, bu ne aksi başlatma metin ve tür dönüştürücüleri yapılabilir dışında hiçbir özellikleri sağlar ve bu sözdizimi kullanarak XAML 2009 fabrika yöntemi özelliklerini tasarım amacınıza değil.  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki örnek, varsayılan olmayan bir oluşturucu imzası ve XAML kullanımını gösterir `x:Arguments` , bu imza erişir.  
  
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
  
 Aşağıdaki örnek, bir hedef Fabrika yöntem imzası ve XAML kullanımını gösterir. `x:Arguments` , bu imza erişir.  
  
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
