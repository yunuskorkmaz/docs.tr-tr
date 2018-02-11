---
title: Visual Basic'de diziler
ms.custom: 
ms.date: 04/23/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- tuples [Visual Basic]
ms.assetid: 3e66cd1b-3432-4e1d-8c37-5ebacae8f53f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2653b9dc8a6ecbcb718c20be8bd6275edf4cfb6e
ms.sourcegitcommit: be1fb5d9447ad459bef22b91a91c72e3e0b2d916
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2018
---
# <a name="tuples-visual-basic"></a>Diziler (Visual Basic)

Visual Basic 2017 ile başlayarak, Visual Basic Dil yapar diziler için yerleşik destek sunar tanımlama grupları oluşturma ve diziler daha kolay öğelerini erişme. Bir tanımlama grubu belirli sayıda ve değerleri dizisi olan bir hafif veri yapısıdır. Tuple örneği olduğunda sayısını ve her değeri (veya bir öğenin) veri türünü tanımlayın. Örneğin, bir 2 bölütlü (veya çifti) iki öğe sahiptir. İlk olabilir bir `Boolean` değer ikinci olsa da bir `String`. Tanımlama grupları birden çok değeri tek bir nesnede depolama kolaylaştırmak için bunlar genellikle birden çok değer döndürme için basit bir yol olarak kullanılır.

> [!IMPORTANT]
> Tuple destek gerektiren <xref:System.ValueTuple> türü. .NET Framework 4.7 yüklü değilse, NuGet paketini eklemeniz gerekir `System.ValueTuple`, hangi kullanılabilir NuGet galerisinde. Bu paketi bir derleme hatası benzer şekilde, "'ValueTuple(Of,,,)' tanımlı veya alınmamış önceden tanımlanmış türü." alabilirsiniz

## <a name="instantiating-and-using-a-tuple"></a>Örnek oluşturma ve bir tanımlama grubu kullanma

Bir tanımlama grubu, virgülle ayrılmış değerler IM parantez kapsayan tarafından örneği oluşturur. Bu değerlerin her birini daha sonra kayıt bir alan olur. Örneğin, aşağıdaki kodu Üçlü (veya 3-tanımlama grubu) ile tanımlayan bir `Date` ilk değeri olarak bir `String` , ikinci olarak ve bir `Boolean` kendi üçüncü olarak.

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#1)]

Varsayılan olarak, bir tanımlama grubu içindeki her alan adını dizesi oluşur `Item` birlikte alanın tabanlı konumda yer alan tanımlama grubu. Bu 3-başlığı için `Date` alandır `Item1`, `String` alandır `Item2`ve `Boolean` alanı `Item3`. Aşağıdaki örnek kod önceki satırında örneği kayıt alanların değerlerini görüntüler.

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#2)]

Visual Basic tanımlama grubu okuma-yazma alanlardır; bir tanımlama grubu örneği sonra değerlerini değiştirebilirsiniz. Aşağıdaki örnek önceki örnekte oluşturulan tanımlama grubu üç alanlarını ikilisi değiştirir ve sonucu görüntüler.

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#3)]

## <a name="instantiating-and-using-a-named-tuple"></a>Örnek oluşturma ve adlandırılmış bir tanımlama grubu kullanma

Demete ait alanları için varsayılan adlar kullanmak yerine, bir örneğini oluşturabilirsiniz bir *tanımlama grubu adlı* demete ait öğelerine kendi adlarınızı atayarak. Demete ait alanlara sonra atanan adlarıyla erişilebilir *veya* varsayılan adlarına göre. Açıkça ilk alan adları dışında aynı 3-tanımlama grubu olarak daha önce aşağıdaki örnek başlatır `EventDate`, ikinci `Name`ve üçüncü `IsHoliday`. Bunu ardından alan değerlerini, bunları değiştirir ve alan değerlerini yeniden görüntüler.

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#4)]

## <a name="inferred-tuple-element-names"></a>Çıkarsanan tanımlama grubu öğe adları

Visual Basic, Visual Basic 15.3 ile başlayarak, başlığın öğeleri adlarının çıkarımını; açıkça atamak gerekmez. Çıkarsanan tanımlama grubu adları değişkenleri kümesinden bir tanımlama grubu başlatmak ve tanımlama grubu öğe adı değişken adı ile aynı olacak şekilde istediğinizde faydalıdır. 

Aşağıdaki örnekte bir `stateInfo` üç açıkça içeren tanımlama grubu adlı öğeleri `state`, `stateName`, ve `capital`. Öğeleri adlandırmada tanımlama grubu başlatma deyimi yalnızca adlandırılmış öğeleri aynı adlı değişkenlerin değerleri atar, unutmayın.

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#1)]
 
Visual Basic derleyici öğeleri ve değişkenleri aynı ada sahip olduğundan, aşağıdaki örnekte gösterildiği gibi alanların adlarını çıkarımını.

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#2)]

İnterred tanımlama grubu öğe adları etkinleştirmek için Visual Basic projesinde kullanmak için Visual Basic derleyici sürümünü tanımlama (\*.vbproj) dosyası: 

```xml 
<PropertyGroup> 
  <LangVersion>15.3</LangVersion> 
</PropertyGroup> 

The version number can be any version of the Visual Basic compiler starting with 15.3. Rather than hard-coding a specific compiler version, you can also specify "Latest" as the value of `LangVersion` to compile with the most recent version of the Visual Basic compiler installed on your system.

In some cases, the Visual Basic compiler cannot infer the tuple element name from the candidate name, and the tuple field can only be referenced using its default name, such as `Item1`, `Item2`, etc. These include:

- The candidate name is the same as the name of a tuple member, such as `Item3`, `Rest`, or `ToString`.

- The candidate name is duplicated in the tuple.
 
When field name inference fails, Visual Basic does not generate a compiler error, nor is an exception thrown at runtime. Instead, tuple fields must be referenced by their predefined names, such as `Item1` and `Item2`. 
  
## Tuples versus structures

A Visual Basic tuple is a value type that is an instance of one of the a **System.ValueTuple** generic types. For example, the `holiday` tuple defined in the previous example is an instance of the <xref:System.ValueTuple%603> structure. It is designed to be a lightweight container for data. Since the tuple aims to make it easy to create an object with multiple data items, it lacks some of the features that a custom structure might have. These include:

- Customer members. You cannot define your own properties, methods, or events for a tuple.

- Validation. You cannot validate the data assigned to fields.

- Immutability. Visual Basic tuples are mutable. In contrast, a custom structure allows you to control whether an instance is mutable or immutable.

If custom members, property and field validation, or immutability are important, you should use the Visual Basic [Structure](../../../language-reference/statements/structure-statement.md) statement to define a custom value type.

A Visual Basic tuple does inherit the members of its **ValueTuple** type. In addition to its fields, these include the following methods:

| Member | Description |
| ---|---|
| CompareTo | Compares the current tuple to another tuple with the same number of elements. |
| Equals | Determines whether the current tuple is equal to another tuple or object. |
| GetHashCode | Calculates the hash code for the current instance. |
| ToString | Returns the string representation of this tuple, which takes the form `(Item1, Item2...)`, where `Item1` and `Item2` represent the values of the tuple's fields. |

In addition, the **ValueTuple** types implement <xref:System.Collections.IStructuralComparable> and <xref:System.Collections.IStructuralEquatable> interfaces, which allow you to define customer comparers.

## Assignment and tuples

Visual Basic supports assignment between tuple types that have the same number of fields. The field types can be converted if one of the following is true:

- The source and target field are of the same type.

- A widening (or implicit) conversion of the source type to the target type is defined. 

- `Option Strict` is `On`, and a narrowing (or explicit) conversion of the source type to the target type is defined. This conversion can throw an exception if the source value is outside the range of the target type.

Other conversions are not considered for assignments. Let's look at the kinds of assignments that are allowed between tuple types.

Consider these variables used in the following examples:

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#1)]

The first two variables, `unnamed` and `anonymous`, do not have semantic names provided for the fields. Their field names are the default `Item1` and `Item2`. The last two variables, `named` and `differentName` have semantic field names. Note that these two tuples have different names for the fields.

All four of these tuples have the same number of fields (referred to as 'arity'), and the types of those fields are identical. Therefore, all of these assignments work:

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#2)]

Notice that the names of the tuples are not assigned. The values of the fields are assigned following the order of the fields in the tuple.

Finally, notice that we can assign the `named` tuple to the `conversion` tuple, even though the first field of `named` is an `Integer`, and the first field of `conversion` is a `Long`. This assignment succeeds because converting an `Integer` to a `Long` is a widening conversion.

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#3)]

Tuples with different numbers of fields are not assignable:

```vb
' Does not compile.
' VB30311: Value of type '(Integer, Integer, Integer)' cannot be converted
'          to '(Answer As Integer, Message As String)'
var differentShape = (1, 2, 3)
named = differentShape
```

## <a name="tuples-as-method-return-values"></a>Diziler yöntemi olarak dönüş değerleri

Bir yöntem yalnızca tek bir değer döndürebilir. Sık sık rağmen birden çok değer döndürmek için bir yöntem çağrısı istersiniz. Bu sınırlamaya geçici bir çözüm için birkaç yol vardır:

- Özel sınıf veya yapı özellikleri oluşturabilir veya alanlar yöntemi tarafından döndürülen değerleri temsil eder. Bu nedenle bir ağır çözümdür; Bu yöntem çağrısından değerleri almak için tek amacı olan bir özel tür tanımlamanızı gerektirir.

- Tek bir değer döndürme ve yöntemine başvuruya geçirerek kalan değerler döndürür. Bu değişken ve başvuruya göre geçirme değişkenin değerini yanlışlıkla üzerine riskleri başlatmasını yükünü içerir.

- Birden çok dönüş değerleri alma için basit bir çözüm sağlar bir tanımlama grubu kullanabilirsiniz.

Örneğin, **TryParseyöntemini** .NET return yöntemleri bir `Boolean` ayrıştırma işlemi başarılı olup olmadığını belirten değer. Ayrıştırma işleminin sonucu başvuruya yöntemine geçirilen bir değişken döndürülür. Normal olarak yapılan bir çağrı gibi ayrıştırma yönteminin <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> aşağıdaki gibi görünür:

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#1)]

Biz çağrısı sarmalama, biz bir tanımlama grubu ayrıştırma işlemi döndürebilir <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> kendi yöntemi yöntemi. Aşağıdaki örnekte, `NumericLibrary.ParseInteger` çağrıları <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> yöntemi ve iki öğe ile adlandırılmış bir tanımlama grubu döndürür. 

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

Ardından aşağıdaki gibi kod ile yöntemi çağırabilirsiniz:

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)]

## <a name="visual-basic-tuples-and-tuples-in-the-net-framework"></a>Visual Basic başlıkları ve .NET Framework diziler

Visual Basic tanımlama grubu birinin örneğidir **System.ValueTuple** .NET Framework 4.7 içinde sunulan genel türler. .NET Framework genel bir dizi de içerir **System.Tuple** sınıfları. Bu sınıfları, ancak Visual Basic diziler farklı ve **System.ValueTuple** çeşitli yollarla genel türleri:

- Öğelerini **tanımlama grubu** sınıflardır adlı özellikleri `Item1`, `Item2`ve benzeri. Visual Basic dizilerde ve **ValueTuple** türleri, başlığın öğeleri alanlardır.

- Anlamlı adlar öğelerine atayamazsınız bir **tanımlama grubu** örneği veya bir **ValueTuple** örneği. Visual Basic, alanları anlamını iletişim adları atamanıza olanak sağlar.

- Özelliklerini bir **tanımlama grubu** örnek salt okunur; başlıklar değişmez. Visual Basic dizilerde ve **ValueTuple** türleri tanımlama grubu alanlardır okuma-yazma; başlıklar değişebilir.

- Genel **tanımlama grubu** türleri başvuru türleridir. Bunlar kullanarak **tanımlama grubu** türleri nesneleri ayırma anlamına gelir. Sık kullanılan yollarına göre bu, uygulamanızın performans üzerinde ölçülebilir bir etkisi olabilir. Visual Basic başlıkları ve **ValueTuple** değer türleri türleridir.

Genişletme yöntemleri <xref:System.TupleExtensions> sınıfı kolaylaştırır Visual Basic başlıkları ve .NET arasında dönüştürme **tanımlama grubu** nesneleri. **ToTuple** yöntemi dönüştürür Visual Basic tanımlama grubu için bir .NET **tanımlama grubu** nesnesi ve **ToValueTuple** yöntemi bir .NET dönüştürür **tanımlama grubu** Visual Basic tanımlama grubu nesne.

Aşağıdaki örnek bir tanımlama grubu oluşturur, bir .NET dönüştürür **tanımlama grubu** nesne ve bir Visual Basic tanımlama grubu geri dönüştürür. Örnek daha sonra bu tanımlama grubu eşit olduğundan emin olmak için özgün bir karşılaştırır.

[!code-vb[Convert](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple2.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

[Visual Basic Dil Başvurusu](index.md)  
