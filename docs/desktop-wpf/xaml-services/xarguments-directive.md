---
title: x:Arguments Yönergesi
ms.date: 03/30/2017
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
ms.openlocfilehash: 5ec6e192688e1065ea847db6c175ad9da0e743fe
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071593"
---
# <a name="xarguments-directive"></a>x:Arguments Yönergesi

XAML'de parametresiz olmayan bir yapı oluşturucu nesne öğesi bildirimi veya fabrika yöntemi nesne bildirimi için yapı bağımsız değişkenlerini paketler.

## <a name="xaml-element-usage-nonparameterless-constructor"></a>XAML Eleman Kullanımı (Parametresiz yapıcı)

```xaml
<object ...>
  <x:Arguments>
    oneOrMoreObjectElements
  </x:Arguments>
</object>
```

## <a name="xaml-element-usage-factory-method"></a>XAML Eleman Kullanımı (fabrika yöntemi)

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
|`oneOrMoreObjectElements`|Parametresiz olmayan kurucu veya fabrika yöntemine geçirilecek bağımsız değişkenleri belirten bir veya daha fazla nesne öğesi.<br /><br /> Tipik kullanım, nesne öğeleri içindeki başlatma metnini kullanarak gerçek bağımsız değişken değerlerini belirtmektir. Örnekler bölümüne bakınız.<br /><br /> Elementlerin sırası önemlidir. Sırayla XAML türleri, destek oluşturucu veya fabrika yöntemi aşırı yüklemesinin türleri ve türü sırasına uygun olmalıdır.|
|`methodName`|Herhangi bir `x:Arguments` bağımsız değişkeni işlemesi gereken fabrika yönteminin adı.|

## <a name="dependencies"></a>Bağımlılıklar

`x:FactoryMethod`uygulandığı durumlarda `x:Arguments` kapsamı ve davranışı değiştirebilir.

Hiçbir `x:FactoryMethod` şey belirtilmemişse, `x:Arguments` destek oluşturucuların alternatif (varsayılan olmayan) imzaları için geçerlidir.

`x:FactoryMethod` Belirtilirse, `x:Arguments` adlandırılmış yöntemin aşırı yüklenmesi için geçerlidir.

## <a name="remarks"></a>Açıklamalar

XAML 2006, başlatma metni aracılığıyla varsayılan olmayan başlatmayı destekleyebilir. Ancak, bir başlatma metin yapım tekniğinin pratik uygulama sınırlıdır. Başlatma metni tek bir metin dizesi olarak kabul edilir; bu nedenle, özel bilgi öğelerini ve özel sınır aşanları dizeden ayrıştırabilen yapı davranışı için bir tür dönüştürücü tanımlanmadıkça, yalnızca tek bir parametre başlatma özelliği ekler. Ayrıca, nesne mantığımetin dize potansiyel olarak gerçek bir dize dışında ilkel işlemek için verilen bir XAML parleyici yerel varsayılan türü dönüştürücüdür.

`x:Arguments` XAML kullanımı, yönerge biçimlendirmesi içeren nesne öğe öğesinin türüne başvurmadığından, tipik anlamda özellik öğesi kullanımı değildir. Bu, öğenin biçimlendirmenin `x:Code` alt içerikler için varsayılan dan başka bir aralık olarak yorumlanması gereken bir aralığı işaretlediği yer gibi diğer yönergelere daha çok benzer. Bu durumda, her nesne öğesinin XAML türü, xaml parsers tarafından hangi belirli kurucu fabrika yöntemi imzasını `x:Arguments` belirlemek için kullanılan bağımsız değişken türleri hakkında bilgi iletir.

`x:Arguments`yapılandırılan bir nesne öğesi için nesne öğesinin diğer özellik öğelerinden, içeriğinden, iç metinden veya başlatma dizelerinden önce olmalıdır. İçerdeki `x:Arguments` nesne öğeleri, xaml türü ve onun destek oluşturucusu veya fabrika yönteminin izin verdiği gibi öznitelikleri ve başlatma dizeleri içerebilir. Nesne veya bağımsız değişkenler için, yerleşik önek eşlemelerine başvurarak varsayılan XAML ad alanının dışında olan özel XAML türleri veya XAML türleri belirtebilirsiniz.

XAML işlemciler, bir nesne oluşturmak için `x:Arguments` belirtilen bağımsız değişkenlerin nasıl kullanılması gerektiğini belirlemek için aşağıdaki yönergeleri kullanır. `x:FactoryMethod` Belirtilirse, bilgiler belirtilenle `x:FactoryMethod` karşılaştırılır (değerin `x:FactoryMethod` yöntem adı olduğunu ve adlandırılmış yöntemin aşırı yüklendiğini unutmayın. `x:FactoryMethod` Belirtilmemişse, bilgiler nesnenin tüm ortak yapı oluşturma kümesiyle karşılaştırılır. XAML işleme mantığı daha sonra parametrelerin sayısını karşılaştırır ve aşırı yükü eşleşen arite ile seçer. Birden fazla eşleşme varsa, XAML işlemci sağlanan nesne elemanlarının XAML türlerine dayalı parametre türlerini karşılaştırmalıdır. Hala birden fazla eşleşme varsa, XAML işlemci davranışı tanımsızdır. A `x:FactoryMethod` belirtilmişse ancak yöntem çözülemiyorsa, Bir XAML işlemci bir özel durum atmalıdır.

XAML öznitelik `<x:Arguments>string</x:Arguments>` kullanımı teknik olarak mümkündür. Ancak, bu, başlatma metni ve tür dönüştürücüler aracılığıyla başka türlü yapılabileceklerin ötesinde hiçbir yetenek sağlamaz ve bu sözdizimini kullanmak XAML 2009 fabrika yöntemi özelliklerinin tasarım amacı değildir.

## <a name="examples"></a>Örnekler

Aşağıdaki örnek, parametresiz olmayan bir yapıcı imzasını, daha `x:Arguments` sonra bu imzaya erişen XAML kullanımını gösterir.

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

Aşağıdaki örnek, bir hedef fabrika yöntemi imzasını gösterir, ardından bu imzaya erişen in XAML `x:Arguments` kullanımı.

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

- [.NET XAML Hizmetlerinde Kullanılacak Özel Türleri Tanımlama](define-custom-types.md)
- [XAML'ye Genel Bakış (WPF)](../fundamentals/xaml.md)
