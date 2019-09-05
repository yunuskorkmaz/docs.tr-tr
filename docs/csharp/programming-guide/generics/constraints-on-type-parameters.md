---
title: Tür parametrelerine yönelik kısıtlamalar- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 04/12/2018
helpviewer_keywords:
- generics [C#], type constraints
- type constraints [C#]
- type parameters [C#], constraints
- unbound type parameter [C#]
ms.openlocfilehash: bb545d9da73154c237f55809a3a72ff0f121ce1a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253015"
---
# <a name="constraints-on-type-parameters-c-programming-guide"></a>Tür Parametrelerindeki Kısıtlamalar (C# Programlama Kılavuzu)

Kısıtlamalar, derleyicisini bir tür bağımsız değişkeni olması gereken yetenekler hakkında bilgilendirir. Herhangi bir kısıtlama olmadan tür bağımsız değişkeni herhangi bir tür olabilir. Derleyici yalnızca <xref:System.Object?displayProperty=nameWithType>, tüm .net türleri için en son temel sınıf olan üyelerini kabul edebilir. Daha fazla bilgi için bkz. [kısıtlamaların neden kullanılması](#why-use-constraints). İstemci kodu bir kısıtlama tarafından izin verilmeyen bir tür kullanarak sınıfınızın örneğini oluşturmaya çalışırsa, sonuç derleme zamanı hatasıdır. Kısıtlamalar, `where` bağlamsal anahtar sözcüğü kullanılarak belirtilir. Aşağıdaki tabloda yedi tür kısıtlama listelenmektedir:

|Kısıtlaması|Açıklama|
|----------------|-----------------|
|`where T : struct`|Tür bağımsız değişkeni bir değer türü olmalıdır. Dışında <xref:System.Nullable%601> herhangi bir değer türü belirtilebilir. Null yapılabilir türler hakkında daha fazla bilgi için bkz. [Nullable türler](../nullable-types/index.md).|
|`where T : class`|Tür bağımsız değişkeni bir başvuru türü olmalıdır. Bu kısıtlama, her sınıf, arabirim, temsilci veya dizi türü için de geçerlidir.|
|`where T : notnull`|Tür bağımsız değişkeni null yapılamayan bir tür olmalıdır. Bağımsız değişken, C# 8,0 veya sonraki bir sürümde null atanamaz bir başvuru türü veya null yapılamayan bir değer türü olabilir. Bu kısıtlama, her sınıf, arabirim, temsilci veya dizi türü için de geçerlidir.|
|`where T : unmanaged`|Tür bağımsız değişkeni [yönetilmeyen bir tür](../../language-reference/builtin-types/unmanaged-types.md)olmalıdır.|
|`where T : new()`|Tür bağımsız değişkeni Ortak parametresiz bir oluşturucuya sahip olmalıdır. Diğer kısıtlamalarla birlikte kullanıldığında, `new()` kısıtlama en son belirtilmelidir.|
|`where T :`temel sınıf adı >  *\<*|Tür bağımsız değişkeni belirtilen temel sınıftan olmalıdır veya türetilmelidir.|
|`where T :` *arabirimadı\<>*|Tür bağımsız değişkeni belirtilen arabirimi içermelidir veya uygulamalıdır. Birden çok arabirim kısıtlaması belirlenebilir. Kısıtlama arabirimi de genel olabilir.|
|`where T : U`|T için sağlanan tür bağımsız değişkeni U için sağlanan bağımsız değişkenden türetilmiş veya türemelidir.|

Bazı kısıtlamalar birbirini dışlıyor. Tüm değer türlerinin erişilebilir bir parametresiz oluşturucusu olmalıdır. Kısıtlama kısıtlamayı belirtir ve`new()` kısıtlama `struct` kısıtlama ile birleştirilemez. `new()` `struct` `unmanaged` Kısıtlama kısıtlamayı`struct` gösterir. Kısıtlama, `struct` ya`new()` da kısıtlamalarıyla birleştirilemez. `unmanaged`

## <a name="why-use-constraints"></a>Neden kısıtlama kullanılmalıdır

Tür parametresini kısıtlayan, izin verilen işlem ve metot çağrılarının sayısını kısıtlayan türü tarafından desteklenenlere ve devralma hiyerarşisindeki tüm türlere göre artırırsınız. Genel sınıfları veya yöntemleri tasarlarken, Genel Üyeler üzerinde basit atamanın ötesinde herhangi bir işlem gerçekleştiriyor veya tarafından <xref:System.Object?displayProperty=nameWithType>desteklenmeyen herhangi bir yöntemi çağırdıktan sonra, tür parametresine kısıtlamalar uygulamanız gerekir. Örneğin, temel sınıf kısıtlaması derleyiciye yalnızca bu türden veya bu türden türetilmiş nesnelerin tür bağımsız değişkenleri olarak kullanılacağını söyler. Derleyiciye bu garanti verildikten sonra, genel sınıfta bu tür yöntemlerin çağrılmasına izin verebilir. Aşağıdaki kod örneği, bir temel sınıf kısıtlaması uygulayarak `GenericList<T>` sınıfına ekleyebileceğiniz işlevselliği gösterir (Genel türlere [giriş](introduction-to-generics.md)olarak).

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#9)]

Kısıtlama, genel sınıfın `Employee.Name` özelliğini kullanmasını sağlar. Kısıtlama, türündeki `T` tüm öğelerin bir `Employee` nesne ya da öğesinden `Employee`devralan nesne olduğunu belirtir.

Aynı tür parametresine birden çok kısıtlama uygulanabilir ve kısıtlamalar aşağıdaki gibi genel türler olabilir:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#10)]

`where T : class` Kısıtlama uygulanırken tür parametresindeki `==` ve `!=` işleçlerden kaçının, çünkü bu işleçler yalnızca başvuru kimliğini test edecek, değer eşitlik için değil. Bu davranış, bu işleçler bağımsız değişken olarak kullanılan bir türde aşırı yüklense bile oluşur. Aşağıdaki kod bu noktayı gösterir; <xref:System.String> sınıf işleci`==` aşırı yüklese de çıkış yanlış olur.

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#11)]

Derleyici yalnızca derleme zamanında bir `T` başvuru türü olduğunu ve tüm başvuru türleri için geçerli olan varsayılan işleçleri kullanması gerektiğini bilir. Değer eşitlik için test etmeniz gerekiyorsa, önerilen yol, `where T : IEquatable<T>` veya `where T : IComparable<T>` kısıtlamasını uygulamak ve genel sınıfı oluşturmak için kullanılacak herhangi bir sınıfta arabirimini uygulamaktır.

## <a name="constraining-multiple-parameters"></a>Birden çok parametreyi kısıtlama

Aşağıdaki örnekte gösterildiği gibi birden çok parametreye kısıtlama uygulayabilir ve tek bir parametreye birden çok kısıtlama uygulayabilirsiniz:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#12)]

## <a name="unbounded-type-parameters"></a>Sınırlandırılmamış tür parametreleri

 Public sınıfında `SampleClass<T>{}`T gibi hiçbir kısıtlaması olmayan tür parametrelerine, sınırlandırılmamış tür parametreleri denir. Sınırlandırılmamış tür parametreleri aşağıdaki kurallara sahiptir:

- `!=` Ve`==` işleçleri, somut tür bağımsız değişkeninin bu işleçleri destekleyeceği garantisi olmadığından kullanılamaz.
- Bunlar, herhangi bir arabirim türüne dönüştürülebilir `System.Object` veya buradan dönüştürülebilir ya da açıkça dönüştürülebilir.
- Bunları [null](../../language-reference/keywords/null.md)ile karşılaştırabilirsiniz. Sınırlandırılmamış bir parametre ile `null`karşılaştırılabiliyorsanız, tür bağımsız değişkeni bir değer türündeyse karşılaştırma her zaman yanlış olarak döndürülür.

## <a name="type-parameters-as-constraints"></a>Parametreleri kısıtlamalar olarak yazın

Genel tür parametresinin bir kısıtlama olarak kullanılması, aşağıdaki örnekte gösterildiği gibi, kendi tür parametresine sahip bir üye işlevi bu parametreyi kapsayan türün tür parametresiyle kısıtlamak için yararlıdır:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#13)]

Önceki örnekte, `T` `Add` yönteminin bağlamındaki bir tür kısıtlamasıdır ve `List` sınıfı bağlamında sınırsız bir tür parametresi olur.

Tür parametreleri, genel sınıf tanımlarında kısıtlama olarak da kullanılabilir. Tür parametresi, diğer tür parametreleriyle birlikte açılı ayraç içinde bildirilmelidir:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#14)]

Tür parametrelerinin genel sınıflarla kısıtlamalar olarak yararlılığı sınırlıdır, çünkü derleyici tür parametresi hakkında türetilmediği `System.Object`hariç hiçbir şey kabul edebilir. Tür parametrelerini, iki tür parametresi arasında bir devralma ilişkisi uygulamak istediğiniz senaryolarda genel sınıflarda kısıtlamalar olarak kullanın.

## <a name="notnull-constraint"></a>NotNull kısıtlaması

8,0 ile C# başlayarak, tür bağımsız değişkeninin null `notnull` yapılamayan bir değer türü veya null yapılamayan bir başvuru türü olması gerektiğini belirtmek için kısıtlamasını kullanabilirsiniz. Kısıtlama yalnızca bir `nullable enable` bağlamda kullanılabilir. `notnull` Kısıtlama, `notnull` null yapılabilir bir zorunluluvou bağlamına eklerseniz bir uyarı oluşturur. 

Diğer kısıtlamaların aksine, bir tür bağımsız değişkeni `notnull` kısıtlamayı ihlal ettiğinde, derleyici bu kod bir `nullable enable` bağlamda derlenirse bir uyarı oluşturur. Kod, null yapılabilir bir zorunluluvou bağlamında derlenmişse, derleyici hiçbir uyarı veya hata oluşturmaz.

## <a name="unmanaged-constraint"></a>Yönetilmeyen kısıtlama

7,3 ile C# başlayarak, tür parametresinin yönetilmeyen bir `unmanaged` [tür](../../language-reference/builtin-types/unmanaged-types.md)olması gerektiğini belirtmek için kısıtlamasını kullanabilirsiniz. `unmanaged` Kısıtlama, aşağıdaki örnekte gösterildiği gibi, bellek blokları olarak işlenebilen türlerle çalışmak için yeniden kullanılabilir yordamlar yazmanızı sağlar:

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#15)]

Önceki yöntem, yerleşik bir tür olarak bilinen `unsafe` bir tür üzerinde `sizeof` işleç kullandığından bir bağlamda derlenmelidir. `unmanaged` Kısıtlama`sizeof` olmadan işleç kullanılamaz.

## <a name="delegate-constraints"></a>Temsilci kısıtlamaları

Ayrıca, 7,3 C# ' den itibaren, veya <xref:System.Delegate?displayProperty=nameWithType> <xref:System.MulticastDelegate?displayProperty=nameWithType> temel sınıf kısıtlaması olarak kullanabilirsiniz. CLR bu kısıtlamaya her zaman izin verilir, ancak C# dil izin vermez. Kısıtlama `System.Delegate` , temsilcilerle birlikte, tür açısından güvenli bir şekilde kod yazmanıza olanak sağlar. Aşağıdaki kod, iki temsilciyi aynı tür olduklarından birleştiren bir genişletme yöntemi tanımlar:

[!code-csharp[using the delegate constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#16)]

Aynı türdeki temsilcileri birleştirmek için yukarıdaki yöntemi kullanabilirsiniz:

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#17)]

Son satırın açıklamasını kaldırırsanız, derlenmez. Hem hem de `first` temsilci türlerdir,ancakfarklıtemsilcitürleridir.`test`

## <a name="enum-constraints"></a>Sabit listesi kısıtlamaları

C# 7,3 ' den başlayarak, <xref:System.Enum?displayProperty=nameWithType> türü temel sınıf kısıtlaması olarak da belirtebilirsiniz. CLR bu kısıtlamaya her zaman izin verilir, ancak C# dil izin vermez. Kullanan `System.Enum` genel türler, içindeki `System.Enum`statik yöntemleri kullanarak sonuçları önbelleğe almak için tür kullanımı uyumlu programlama sağlar. Aşağıdaki örnek, bir sabit listesi türü için geçerli tüm değerleri bulur ve sonra bu değerleri dize gösterimiyle eşleyen bir sözlük oluşturur.

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#18)]

Kullanılan yöntemler, performans etkilerine sahip olan yansıma kullanımını kullanır. Bu yöntemi, yansıma gerektiren çağrıları yinelemek yerine önbelleğe alınmış ve yeniden kullanılan bir koleksiyon oluşturmak için çağırabilirsiniz.

Aşağıdaki örnekte gösterildiği gibi, bir sabit listesi oluşturmak ve değerlerini ve adlarını bir sözlüğü oluşturmak için kullanabilirsiniz:

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#19)]

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#20)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic>
- [C# Programlama Kılavuzu](../index.md)
- [Genel Türlere Giriş](./index.md)
- [Genel Sınıflar](./generic-classes.md)
- [new Kısıtlaması](../../language-reference/keywords/new-constraint.md)
