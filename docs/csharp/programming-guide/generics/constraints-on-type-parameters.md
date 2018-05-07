---
title: Tür Parametrelerindeki Kısıtlamalar (C# Programlama Kılavuzu)
ms.date: 04/12/2018
helpviewer_keywords:
- generics [C#], type constraints
- type constraints [C#]
- type parameters [C#], constraints
- unbound type parameter [C#]
ms.openlocfilehash: 1d6487f4136b5a3f8bfc2e1721ae268e06f5ba98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="constraints-on-type-parameters-c-programming-guide"></a>Tür parametreleri (C# programlama Kılavuzu) kısıtlamaları

Kısıtlamaları derleyici tür bağımsız değişkeni olmalıdır özellikleri hakkında bildirin. Tüm kısıtlamaları, tür bağımsız değişkeni herhangi bir türü olabilir. Derleyici üyeleri yalnızca kabul edilebilir <xref:System.Object?displayPropety=nameWithType>, herhangi bir .NET türü için ultimate temel sınıfı olan. Daha fazla bilgi için bkz: [neden kısıtlamaları kullanmak](#why-use-constraints). İstemci kodu kısıtlaması tarafından izin verilmeyen bir türünü kullanarak, sınıfının örneği çalışırsa, bir derleme zamanı hatası sonucudur. Kısıtlamaları belirtilen kullanarak `where` bağlamsal anahtar sözcüğü. Aşağıdaki tabloda kısıtlamaları yedi türlerini listeler:

|Kısıtlama|Açıklama|
|----------------|-----------------|
|`where T: struct`|Tür bağımsız değişkeni bir değer türü olmalıdır. Herhangi bir değer türü dışında <xref:System.Nullable> belirtilebilir. Daha fazla bilgi için bkz: [kullanarak boş değer atanabilir türler](../nullable-types/using-nullable-types.md).|
|`where T : class`|Tür bağımsız değişkeni bir başvuru türü olmalıdır. Bu sınırlama herhangi sınıfı, arabirim, temsilci veya dizi türü için de geçerlidir.|
|`where T : unmanaged`|Tür bağımsız değişkeni bir başvuru türü olmalıdır ve iç içe geçme herhangi bir düzeyde herhangi bir başvuru türü üye içermemelidir.|
|`where T : new()`|Tür bağımsız değişkeni genel bir parametresiz oluşturucuya sahip olmalıdır. Diğer kısıtlamalar ile birlikte kullanıldığında `new()` kısıtlaması son belirtilmelidir.|
|`where T :` *\<taban sınıf adı >*|Tür bağımsız değişkeni, olabilir veya belirtilen temel sınıfından türetilir.|
|`where T :` *\<Arabirim adı >*|Tür bağımsız değişkeni olabilir veya belirtilen arabirimini uygulaması gerekir. Birden çok arabirim kısıtlamaları belirtilebilir. Kısıtlayan arabirimi genel olabilir.|
|`where T : U`|T olması veya u için sağlanan bağımsız değişken öğesinden türetilen için sağlanan tür bağımsız değişkeni|

Bazı kısıtlamalar karşılıklı olarak birbirini dışlar. Tüm değer türleri erişilebilir bir parametresiz oluşturucuya sahip olmalıdır. `struct` Kısıtlaması gelir `new()` kısıtlama ve `new()` kısıtlaması ile ilişkilendirilemez `struct` kısıtlaması. `unmanaged` Kısıtlaması gelir `struct` kısıtlaması. `unmanaged` Kısıtlaması ile ya da ilişkilendirilemez `struct` veya `new()` kısıtlamaları.

## <a name="why-use-constraints"></a>Kısıtlamaları neden kullanılır?

Tür parametresi kısıtlayarak, izin verilen işlemler ve kısıtlama türü ve devralma hiyerarşisi içindeki tüm türler tarafından desteklenen yöntem çağrılarını sayısını artırın. Tasarlarken genel sınıfları veya yöntemleri, basit atama ötesinde Genel üyeler üzerinde herhangi bir işlemi gerçekleştirme veya kaldırılacak tarafından desteklenmeyen herhangi bir yöntem çağırma varsa <xref:System.Object?displayProperty=nameWithType>, tür parametresi kısıtlamaları uygulamak gerekir. Örneğin, taban sınıf kısıtlaması bu tür nesneler yalnızca derleyici söyler veya öğesinden türetilmiş türü tür bağımsız değişkenleri kullanılır. Derleyici bu garantisi sonra genel sınıfında çağrılacak türü yöntemleri izin verebilirsiniz. Aşağıdaki kod örneği için ekleme işlevini gösterir `GenericList<T>` sınıfı (içinde [genel türlere giriş](introduction-to-generics.md)) bir taban sınıf kısıtlaması uygulayarak.

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#9)]

Kullanmak genel bir sınıf kısıtlaması etkinleştirir `Employee.Name` özelliği. Kısıtlama belirleyen türündeki tüm öğeleri `T` ya da olması garanti bir `Employee` veya öğesinden devralınan bir nesneyi `Employee`.

Aynı tür parametresi birden çok kısıtlama uygulanabilir ve kısıtlamaları kendilerini genel türleri, aşağıdaki gibi olabilir:

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#10)]

Uygularken `where T : class` kısıtlaması, kaçının `==` ve `!=` tür parametresi işleçlerini çünkü bu işleçlere yalnızca başvuru kimliği olmayan değer eşitlik için test. Bağımsız değişken olarak kullanılan bir türdeki Bu işleçleri aşırı yüklenmiş olsa bile bu davranış oluşur. Aşağıdaki kod bu noktayı gösterir; Çıktı halde false şeklindedir <xref:System.String> sınıf aşırı `==` işleci.

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#11)]

Derleyici yalnızca T derleme zamanında bir başvuru türüdür ve tüm başvuru türleri için geçerli varsayılan işleçleri kullanmalıdır bilir. Değer eşitlik için test etmeniz gerekir, önerilen yöntem de uygulamak için ise `where T : IEquatable<T>` veya `where T : IComparable<T>` kısıtlaması ve genel bir sınıf oluşturmak için kullanılan herhangi bir sınıf arabiriminde uygulayın.

## <a name="constraining-multiple-parameters"></a>Birden çok parametre sınırlama

Aşağıdaki örnekte gösterildiği gibi birden çok parametre ve tek bir parametre için birden çok kısıtlama kısıtlamaları uygulayabilirsiniz:

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#12)]

## <a name="unbounded-type-parameters"></a>Sınırsız tür parametreleri

 Tür ortak sınıfı T gibi herhangi bir kısıtlama söz konusu parametrelerindeki `SampleClass<T>{}`, sınırsız tür parametreleri olarak adlandırılır. Sınırsız tür parametreleri aşağıdaki kurallar vardır:

- `!=` Ve `==` somut tür bağımsız değişkeni bu işleçlere destekleyecek garanti olduğundan işleçleri kullanılamaz.
- Ve ondan dönüştürülebilir `System.Object` veya herhangi bir arabirim türü açıkça dönüştürülebilir.
- Bunları karşılaştırabilirsiniz [null](../../language-reference/keywords/null.md). Sınırsız bir parametre karşılaştırılır varsa `null`, karşılaştırma her zaman tür bağımsız değişkeni bir değer türü ise false döndürür.

## <a name="type-parameters-as-constraints"></a>Tür parametreleri kısıtlamaları olarak

Bir kısıtlama yararlı üye işlevi kendi tür parametresi ile olduğu gibi aşağıdaki örnekte gösterildiği gibi kapsayan tür tür parametresi bu parametreye sınırlamak bir genel tür parametresi kullanımını sahiptir:

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#13)]

Önceki örnekte, `T` türü kısıtlaması bağlamında `Add` yöntemi ve sınırsız tür parametresi bağlamında `List` sınıfı.

Tür parametreleri, genel bir sınıf tanımları kısıtlamalar olarak da kullanılabilir. Tür parametresi herhangi bir tür parametre birlikte köşeli ayraç içinde bildirilmesi gerekir:

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#14)]

Tür parametreleri yararlılığını Genel sınıflar kısıtlamalarıyla olarak den türemesi dışında derleyici tür parametresi hakkında hiçbir şey kabul edilebilir olduğundan sınırlıdır `System.Object`. Genel sınıflar, iki tür parametreleri arasında bir devralma ilişkisi uygulamak istediğiniz senaryolarda kısıtlamalar olarak tür parametreleri kullanın.

## <a name="unmanaged-constraint"></a>Yönetilmeyen kısıtlaması

C# 7.3 ile başlayarak, kullanabilirsiniz `unmanaged` tür parametresi gerektiğini belirtmek için kısıtlama bir **yönetilmeyen türü**. Bir **yönetilmeyen türü** bir başvuru türü olmayan ve tüm iç içe geçme düzeyini başvuru türü alanlarını içermiyor. bir tür. `unmanaged` Kısıtlaması, aşağıdaki örnekte gösterildiği gibi bellek bloğu yönetilebilir türleriyle çalışmak için yeniden kullanılabilir yordamları yazmanıza olanak sağlar:

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#15)]

Yukarıdaki yöntem içinde derlenmelidir bir `unsafe` bağlamı kullandığından `sizeof` işlecinin yerleşik bir tür olarak bilinmeyen bir tür. Olmadan `unmanaged` kısıtlamayı `sizeof` işleci kullanılamaz.

## <a name="delegate-constraints"></a>Temsilci kısıtlamaları

Ayrıca C# 7.3 ile başlayarak, kullanabilirsiniz <xref:System.Delegate?displayProperty=nameWithType> veya <xref:System.MulticastDelegate?displayProperty=nameWithType> bir temel sınıf kısıtlaması olarak. CLR her zaman bu kısıtlamayı izin ancak C# dili izin verilmiyor. `System.Delegate` Kısıtlaması temsilciler ile bir tür kullanımı uyumlu şekilde çalışan kod yazmanıza olanak sağlar. Aşağıdaki kod, aynı türde olması koşuluyla, iki temsilciler birleştiren bir genişletme yöntemi tanımlar:

[!code-csharp[using the delegate constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#16)]

Aynı türde olan temsilcileri birleştirme için yukarıdaki yöntemi kullanabilirsiniz:

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#17)]

Son satırı açıklamadan çıkarın, derleme olmaz. Her ikisi de `first` ve `test` temsilci türleri, ancak bunlar farklı temsilci türleri.

## <a name="enum-constraints"></a>Enum kısıtlamaları

C# 7.3 içinde başlayarak, ayrıca belirtebilirsiniz <xref:System.Enum?displayProperty=nameWithType> bir temel sınıf kısıtlaması türü. CLR her zaman bu kısıtlamayı izin ancak C# dili izin verilmiyor. Genel türler kullanma `System.Enum` statik yöntemleri kullanarak sonuçlarını önbelleğe alma tür kullanımı uyumlu programlama sağlamak `System.Enum`. Aşağıdaki örnek, bir numaralandırma türü için geçerli tüm değerlerin bulur ve bu değerleri, dize gösterimi eşleyen bir sözlük oluşturur.

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#18)]

Kullanılan yöntemleri olun performans etkileri olduğu yansıma kullanın. Önbelleğe alınan ve yeniden bir koleksiyon oluşturmak için bu yöntemi çağırın yansıma gerektiren çağrıları yinelenen yerine.

Bunu aşağıdaki örnekte gösterildiği gibi bir numaralandırma ve adları ve değerleri sözlüğü oluşturmak için kullanabilirsiniz:

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#19)]

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#20)]

## <a name="see-also"></a>Ayrıca bkz.

 <xref:System.Collections.Generic> [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Genel Türlere Giriş](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [Genel Sınıflar](../../../csharp/programming-guide/generics/generic-classes.md)  
 [new Kısıtlaması](../../../csharp/language-reference/keywords/new-constraint.md)  
