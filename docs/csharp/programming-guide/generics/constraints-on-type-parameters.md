---
title: Tür Parametrelerindeki Kısıtlamalar (C# Programlama Kılavuzu)
ms.date: 04/12/2018
helpviewer_keywords:
- generics [C#], type constraints
- type constraints [C#]
- type parameters [C#], constraints
- unbound type parameter [C#]
ms.openlocfilehash: df5a509296f3fb9e8e77a273a0636c74a6f86da3
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46516606"
---
# <a name="constraints-on-type-parameters-c-programming-guide"></a>(C# programlama Kılavuzu) tür parametrelerindeki kısıtlamalar

Kısıtlamaları, derleyici bir tür bağımsız değişkeni olmalıdır özellikleri hakkında bilgilendirin. Herhangi bir kısıtlama tür bağımsız değişkeni, herhangi bir tür olabilir. Derleyici, yalnızca üyelerinin varsayabilirsiniz <xref:System.Object?displayPropety=nameWithType>, üstün temel sınıf için herhangi bir .NET türü. Daha fazla bilgi için [kısıtlamaları neden kullanılmalı](#why-use-constraints). İstemci kodu, sınıf kısıtlaması tarafından izin verilmeyen bir türü kullanarak örneği oluşturmak çalışırsa, sonucu bir derleme zamanı hatasıdır. Kısıtlamaları kullanılarak belirtilir `where` bağlamsal anahtar sözcük. Aşağıdaki tabloda, yedi kısıtlamalar türleri listelenmektedir:

|Kısıtlama|Açıklama|
|----------------|-----------------|
|`where T : struct`|Tür bağımsız değişkeni bir değer türü olması gerekir. Herhangi bir değer türü hariç <xref:System.Nullable%601> belirtilebilir. Boş değer atanabilir türler hakkında daha fazla bilgi için bkz: [boş değer atanabilir türler](../nullable-types/index.md).|
|`where T : class`|Tür bağımsız değişkeninin bir başvuru türü olması gerekir. Bu kısıtlama, tüm sınıf, arabirim, temsilci ya da dizi türü için de geçerlidir.|
|`where T : unmanaged`|Tür bağımsız değişkeninin bir başvuru türü olmalıdır ve iç içe geçme herhangi bir düzeyde herhangi bir başvuru türü üye içermemelidir.|
|`where T : new()`|Tür bağımsız değişkeni genel bir parametresiz oluşturucusu olmalıdır. Diğer kısıtlamalarla birlikte kullanıldığında `new()` kısıtlaması en son belirtilmelidir.|
|`where T :` *\<temel sınıf adı >*|Tür bağımsız değişkeni, olabilir veya belirtilen temel sınıfından türetilir.|
|`where T :` *\<Arabirim adı >*|Tür bağımsız değişkeni, olabilir veya belirtilen arabirim uygular. Birden çok arabirim kısıtlamasını belirtilebilir. Kısıtlama arabirimi genel olabilir.|
|`where T : U`|T olabilir veya u için sağlanan bağımsız değişken türetmek için sağlanan tür bağımsız değişkeni|

Bazı kısıtlamalar birbirini dışlar. Tüm değer türleri, erişilebilir bir parametresiz oluşturucuya sahip olmalıdır. `struct` Kısıtlaması gelir `new()` kısıtlaması ve `new()` kısıtlaması ile birleştirilemez `struct` kısıtlaması. `unmanaged` Kısıtlaması gelir `struct` kısıtlaması. `unmanaged` Kısıtlaması ile birleştirilemez `struct` veya `new()` kısıtlamaları.

## <a name="why-use-constraints"></a>Kısıtlamaları neden kullanılır?

Tür parametresi kısıtlayarak, izin verilen işlemler ve kısıtlama türü ve devralma hiyerarşisindeki tüm türleri tarafından desteklenen yöntem çağrılarını sayısını artırın. Tasarlarken genel sınıfları veya yöntemleri, basit atamasını ötesindeki genel üyeleri üzerinde herhangi bir işlemi gerçekleştirme veya kaldırılacak desteklenmeyen herhangi bir yöntem çağırma varsa <xref:System.Object?displayProperty=nameWithType>, tür parametresi kısıtlamaları uygulamak gerekir. Örneğin, temel sınıf kısıtlaması, yalnızca bu tür nesnelerin derleyiciye veya bundan türetilmiş türü, tür bağımsız değişkeni olarak kullanılır. Derleyici bu garanti olduğunda, bu türdeki genel sınıfta çağrılacak yöntem izin verebilirsiniz. Aşağıdaki kod örneği ekleyebilirsiniz işlevselliğini gösterir `GenericList<T>` sınıfı (içinde [genel türlere giriş](introduction-to-generics.md)) uygulayarak bir temel sınıf kısıtlaması.

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#9)]

Kullanılacak genel sınıf kısıtlaması sağlayan `Employee.Name` özelliği. Kısıtlama belirten türündeki tüm öğeleri `T` aşağıdakilerden biri olması garanti bir `Employee` veya devralınan bir nesneyi `Employee`.

Birden çok kısıtlaması aynı tür parametresi için uygulanabilir ve sınırlamalar genel türler, aşağıdaki gibi olabilir:

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#10)]

Uygularken `where T : class` kısıtlaması, kaçının `==` ve `!=` işleçlerini tür parametresi olduğundan, bu işleçler yalnızca başvuru kimliği değil değeri eşitlik için test eder. Bağımsız değişken olarak kullanılan bir tür içinde bu işleçler aşırı yüklenmiş olsa bile bu davranış oluşur. Aşağıdaki kod bu noktayı gösterir; Çıkış olsa bile yanlış <xref:System.String> sınıfı aşırı `==` işleci.

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#11)]

Derleyici, yalnızca T derleme zamanında bir başvuru türüdür ve tüm başvuru türleri için geçerli varsayılan işleçlerini kullanmalısınız bilir. İçin değer eşitliği test etmeniz gerekir, ayrıca uygulamak için önerilen yöntem olduğu `where T : IEquatable<T>` veya `where T : IComparable<T>` kısıtlaması ve genel bir sınıf oluşturmak için kullanılan herhangi bir sınıf içinde arabirim uygular.

## <a name="constraining-multiple-parameters"></a>Birden çok parametre sınırlama

Aşağıdaki örnekte gösterildiği gibi birden çok parametre ve birden çok kısıtlaması tek bir parametre için kısıtlamalar uygulayabilirsiniz:

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#12)]

## <a name="unbounded-type-parameters"></a>Sınırsız tür parametreleri

 Tür T genel sınıfında gibi herhangi bir kısıtlama söz konusu parametrelerindeki `SampleClass<T>{}`, sınırsız tür parametreleri olarak adlandırılır. Sınırsız tür parametreleri, aşağıdaki kurallar vardır:

- `!=` Ve `==` işleçleri somut tür bağımsız değişkeni, bu işleçler destekleyecek garanti olduğundan kullanılamaz.
- Ve ondan dönüştürülebilir `System.Object` veya herhangi bir arabirim türüne açıkça dönüştürülebilir.
- Bunları karşılaştıran [null](../../language-reference/keywords/null.md). Sınırsız bir parametre karşılaştırılır, `null`, karşılaştırma her zaman tür bağımsız değişkeni bir değer türü ise false döndürür.

## <a name="type-parameters-as-constraints"></a>Kısıtlama olarak tür parametreleri

Kısıtlama yararlı bir üye işlevi çalıştırıldığında, kendi tür parametresi olduğundan aşağıdaki örnekte gösterildiği gibi kapsanan türün tür parametresi, parametre sınırlamak bir genel tür parametresi kullanımı vardır:

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#13)]

Önceki örnekte, `T` bağlamında bir tür kısıtlaması `Add` yöntemi ve bir sınırsız tür parametre bağlamında `List` sınıfı.

Tür parametreleri, genel sınıf tanımlarındaki kısıtlama olarak da kullanılabilir. Tür parametresi, diğer tür parametrelerinin birlikte açılı ayraçlar içinde bildirilmesi gerekir:

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#14)]

Öğesinden türetilen dışında derleyicinin tür parametresi hakkında hiçbir şey kabul edilebilir olduğundan, tür parametreleri ile genel sınıflar kısıtlama olarak kullanışlılığını sınırlıdır `System.Object`. Tür parametreleri, iki tür parametreleri arasında bir devralma ilişkisi uygulamak istediğiniz senaryolarda Genel sınıflar üzerinde kısıtlama olarak kullanın.

## <a name="unmanaged-constraint"></a>Yönetilmeyen kısıtlaması

Kullanabileceğiniz C# 7.3 ile başlayarak, `unmanaged` kısıtlaması, tür parametresi olması gerektiğini belirtmek için bir **yönetilmeyen tür**. Bir **yönetilmeyen tür** , bir başvuru türü değil ve başvuru türü alanları iç içe geçme herhangi bir düzeyde içermeyen bir türdür. `unmanaged` Kısıtlaması, aşağıdaki örnekte gösterildiği gibi bellek bloklarını yönetilebilir türleriyle çalışmak için yeniden kullanılabilir rutinleri yazmanıza olanak sağlar:

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#15)]

Önceki yöntem derlenmesi gereken bir `unsafe` bağlam kullandığından `sizeof` işleci yerleşik bir tür olarak bilinmeyen bir türde. Olmadan `unmanaged` kısıtlaması `sizeof` işleci kullanılamaz.

## <a name="delegate-constraints"></a>Temsilci kısıtlamaları

Kullanabileceğiniz ayrıca C# 7.3 ile başlayarak, <xref:System.Delegate?displayProperty=nameWithType> veya <xref:System.MulticastDelegate?displayProperty=nameWithType> bir temel sınıf kısıtlama olarak. CLR, bu kısıtlama her zaman izin verilir, ancak C# dili izin verilmiyor. `System.Delegate` Kısıtlaması ile temsilciler bir tür kullanımı uyumlu şekilde çalışan kod yazmanıza olanak sağlar. Aşağıdaki kod, aynı türde oldukları sağlanan iki temsilcilerin birleştiren bir genişletme yöntemi tanımlar:

[!code-csharp[using the delegate constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#16)]

Aynı türdeyse temsilcileri birleştirme için yukarıdaki yöntemi kullanabilirsiniz:

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#17)]

Son satırı açıklamadan çıkarın, derlenemeyecektir. Her ikisi de `first` ve `test` temsilci türleri, ancak bunlar farklı temsilci türleri.

## <a name="enum-constraints"></a>Enum kısıtlamaları

C# 7.3 başlayarak, ayrıca belirtebileceğiniz <xref:System.Enum?displayProperty=nameWithType> bir temel sınıf kısıtlaması türü. CLR, bu kısıtlama her zaman izin verilir, ancak C# dili izin verilmiyor. Genel türler kullanarak `System.Enum` tür kullanımı uyumlu programlama sonuçlarını önbelleğe alma statik yöntemleri kullanmasını sağlamak `System.Enum`. Aşağıdaki örnek, bir sabit listesi türü için geçerli tüm değerlerin bulur ve sonra bu değerleri dize gösterimine eşleyen sözlük oluşturur.

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#18)]

Kullanılan yöntemleri olun performans şifrelemelerini yansıma kullanın. Önbelleğe alınan ve yeniden bir koleksiyon oluşturmak için bu yöntem çağırabilirsiniz yansıma gerektiren çağrıları yinelenen yerine.

Bunu aşağıdaki örnekte gösterildiği gibi bir sabit listesi ve adları ve değerleri sözlüğü oluşturmak için kullanabilirsiniz:

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#19)]

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#20)]

## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.Collections.Generic>
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Genel Türlere Giriş](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
- [Genel Sınıflar](../../../csharp/programming-guide/generics/generic-classes.md)  
- [new Kısıtlaması](../../../csharp/language-reference/keywords/new-constraint.md)  
