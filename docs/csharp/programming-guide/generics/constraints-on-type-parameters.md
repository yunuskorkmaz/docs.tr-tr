---
title: Tür parametrelerine yönelik kısıtlamalar-C# Programlama Kılavuzu
description: Tür parametrelerinin kısıtlamaları hakkında bilgi edinin. Kısıtlamalar derleyiciye bir tür bağımsız değişkeninin sahip olması gereken özellikleri söyler.
ms.date: 04/12/2018
helpviewer_keywords:
- generics [C#], type constraints
- type constraints [C#]
- type parameters [C#], constraints
- unbound type parameter [C#]
ms.openlocfilehash: 91807fa05ce49b8507ee6913ff2620452fcbfab5
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301950"
---
# <a name="constraints-on-type-parameters-c-programming-guide"></a>Tür Parametrelerindeki Kısıtlamalar (C# Programlama Kılavuzu)

Kısıtlamalar, derleyicisini bir tür bağımsız değişkeni olması gereken yetenekler hakkında bilgilendirir. Herhangi bir kısıtlama olmadan tür bağımsız değişkeni herhangi bir tür olabilir. Derleyici yalnızca <xref:System.Object?displayProperty=nameWithType> , tüm .net türleri için en son temel sınıf olan üyelerini kabul edebilir. Daha fazla bilgi için bkz. [kısıtlamaların neden kullanılması](#why-use-constraints). İstemci kodu bir kısıtlamayı karşılamayan bir tür kullanıyorsa, derleyici bir hata verir. Kısıtlamalar, `where` bağlamsal anahtar sözcüğü kullanılarak belirtilir. Aşağıdaki tabloda yedi tür kısıtlama listelenmektedir:

|Kısıtlaması|Description|
|----------------|-----------------|
|`where T : struct`|Tür bağımsız değişkeni null yapılamayan bir değer türü olmalıdır. Nullable değer türleri hakkında daha fazla bilgi için bkz. [Nullable değer türleri](../../language-reference/builtin-types/nullable-value-types.md). Tüm değer türlerinde erişilebilir parametresiz bir Oluşturucu olduğundan, kısıtlama `struct` `new()` kısıtlamayı gösterir ve `new()` kısıtlamayla birleştirilemez. Kısıtlamayı `struct` `unmanaged` kısıtlamasıyla birleştiremezsiniz.|
|`where T : class`|Tür bağımsız değişkeni bir başvuru türü olmalıdır. Bu kısıtlama, her sınıf, arabirim, temsilci veya dizi türü için de geçerlidir. C# 8,0 veya sonraki bir sürümde null yapılabilir bir bağlamda, `T` null atanamaz bir başvuru türü olmalıdır. |
|`where T : class?`|Tür bağımsız değişkeni, null yapılabilir veya null yapılamayan bir başvuru türü olmalıdır. Bu kısıtlama, her sınıf, arabirim, temsilci veya dizi türü için de geçerlidir.|
|`where T : notnull`|Tür bağımsız değişkeni null yapılamayan bir tür olmalıdır. Bağımsız değişken, C# 8,0 veya sonraki bir sürümde null atanamaz bir başvuru türü veya null yapılamayan bir değer türü olabilir. |
|`where T : unmanaged`|Tür bağımsız değişkeni null atanamaz bir [yönetilmeyen tür](../../language-reference/builtin-types/unmanaged-types.md)olmalıdır. `unmanaged`Kısıtlama `struct` kısıtlamayı gösterir ve ya da kısıtlamalarıyla birleştirilemez `struct` `new()` .|
|`where T : new()`|Tür bağımsız değişkeni Ortak parametresiz bir oluşturucuya sahip olmalıdır. Diğer kısıtlamalarla birlikte kullanıldığında, `new()` kısıtlama en son belirtilmelidir. `new()`Kısıtlama `struct` ve `unmanaged` kısıtlamalarıyla birleştirilemez.|
|`where T :` *\<base class name>*|Tür bağımsız değişkeni belirtilen temel sınıftan olmalıdır veya türetilmelidir. C# 8,0 ve üzeri bir null yapılabilir bağlamda, `T` belirtilen temel sınıftan türetilmiş null atanamaz bir başvuru türü olmalıdır. |
|`where T :` *\<base class name>?*|Tür bağımsız değişkeni belirtilen temel sınıftan olmalıdır veya türetilmelidir. C# 8,0 ve üzeri bir null yapılabilir bağlamda, `T` belirtilen temel sınıftan türetilmiş null yapılabilen veya null yapılamayan bir tür olabilir. |
|`where T :` *\<interface name>*|Tür bağımsız değişkeni belirtilen arabirimi içermelidir veya uygulamalıdır. Birden çok arabirim kısıtlaması belirlenebilir. Kısıtlama arabirimi de genel olabilir. C# 8,0 ve üzeri bir null yapılabilir bağlamda, `T` belirtilen arabirimi uygulayan null yapılamayan bir tür olmalıdır.|
|`where T :` *\<interface name>?*|Tür bağımsız değişkeni belirtilen arabirimi içermelidir veya uygulamalıdır. Birden çok arabirim kısıtlaması belirlenebilir. Kısıtlama arabirimi de genel olabilir. C# 8,0 ' de null yapılabilir bir bağlamda, `T` null yapılabilir bir başvuru türü, null olamayan bir başvuru türü veya değer türü olabilir. `T`null yapılabilen bir değer türü olmayabilir.|
|`where T : U`|İçin sağlanan tür bağımsız değişkeni, `T` için sağlanan bağımsız değişkenden türetilmiş veya türetilmiş olmalıdır `U` . Null yapılabilir bir bağlamda, `U` null atanamaz bir başvuru türü ise, `T` null olamayan bir başvuru türü olmalıdır. `U`Null yapılabilir bir başvuru türü ise, `T` null yapılabilir veya null atanamaz olabilir. |

## <a name="why-use-constraints"></a>Neden kısıtlama kullanılmalıdır

Kısıtlamalar, bir tür parametresinin yeteneklerini ve beklentilerini belirtir. Bu kısıtlamaları bildirmek, kısıtlama türünün işlemlerini ve Yöntem çağrılarını kullanabileceğiniz anlamına gelir. Genel bir sınıf veya yönteminiz, Genel Üyeler üzerinde basit atamanın ötesinde veya tarafından desteklenmeyen herhangi bir yöntemi çağıran herhangi bir işlem kullanıyorsa <xref:System.Object?displayProperty=nameWithType> , tür parametresine kısıtlamalar uygulamanız gerekir. Örneğin, temel sınıf kısıtlaması derleyiciye yalnızca bu türden veya bu türden türetilmiş nesnelerin tür bağımsız değişkenleri olarak kullanılacağını söyler. Derleyiciye bu garanti verildikten sonra, genel sınıfta bu tür yöntemlerin çağrılmasına izin verebilir. Aşağıdaki kod örneği, `GenericList<T>` bir temel sınıf kısıtlaması uygulayarak sınıfına ekleyebileceğiniz işlevselliği gösterir ( [Genel türlere giriş](../../../standard/generics/index.md)olarak).

[!code-csharp[using the class and struct constraints](snippets/GenericWhereConstraints.cs#9)]

Kısıtlama, genel sınıfın özelliğini kullanmasını sağlar `Employee.Name` . Kısıtlama, türündeki tüm öğelerin `T` bir `Employee` nesne ya da öğesinden devralan nesne olduğunu belirtir `Employee` .

Aynı tür parametresine birden çok kısıtlama uygulanabilir ve kısıtlamalar aşağıdaki gibi genel türler olabilir:

[!code-csharp[using the class and struct constraints](snippets/GenericWhereConstraints.cs#10)]

`where T : class`Kısıtlama uygulanırken `==` `!=` tür parametresindeki ve işleçlerden kaçının, çünkü bu işleçler yalnızca başvuru kimliğini test edecek, değer eşitlik için değil. Bu davranış, bu işleçler bağımsız değişken olarak kullanılan bir türde aşırı yüklense bile oluşur. Aşağıdaki kod bu noktayı gösterir; sınıf işleci aşırı yüklese de çıkış yanlış olur <xref:System.String> `==` .

[!code-csharp[using the class and struct constraints](snippets/GenericWhereConstraints.cs#11)]

Derleyici yalnızca `T` derleme zamanında bir başvuru türü olduğunu ve tüm başvuru türleri için geçerli olan varsayılan işleçleri kullanması gerektiğini bilir. Değer eşitlik için test etmeniz gerekiyorsa, önerilen yol, `where T : IEquatable<T>` veya `where T : IComparable<T>` kısıtlamasını uygulamak ve genel sınıfı oluşturmak için kullanılacak herhangi bir sınıfta arabirimini uygulamaktır.

## <a name="constraining-multiple-parameters"></a>Birden çok parametreyi kısıtlama

Aşağıdaki örnekte gösterildiği gibi birden çok parametreye kısıtlama uygulayabilir ve tek bir parametreye birden çok kısıtlama uygulayabilirsiniz:

[!code-csharp[using the class and struct constraints](snippets/GenericWhereConstraints.cs#12)]

## <a name="unbounded-type-parameters"></a>Sınırlandırılmamış tür parametreleri

 Public sınıfında T gibi hiçbir kısıtlaması olmayan tür parametrelerine, `SampleClass<T>{}` sınırlandırılmamış tür parametreleri denir. Sınırlandırılmamış tür parametreleri aşağıdaki kurallara sahiptir:

- `!=`Ve `==` işleçleri, somut tür bağımsız değişkeninin bu işleçleri destekleyeceği garantisi olmadığından kullanılamaz.
- Bunlar, `System.Object` herhangi bir arabirim türüne dönüştürülebilir veya buradan dönüştürülebilir ya da açıkça dönüştürülebilir.
- Bunları [null](../../language-reference/keywords/null.md)ile karşılaştırabilirsiniz. Sınırlandırılmamış bir parametre ile karşılaştırılabiliyorsanız `null` , tür bağımsız değişkeni bir değer türündeyse karşılaştırma her zaman yanlış olarak döndürülür.

## <a name="type-parameters-as-constraints"></a>Parametreleri kısıtlamalar olarak yazın

Genel tür parametresinin bir kısıtlama olarak kullanılması, aşağıdaki örnekte gösterildiği gibi, kendi tür parametresine sahip bir üye işlevi bu parametreyi kapsayan türün tür parametresiyle kısıtlamak için yararlıdır:

[!code-csharp[using the class and struct constraints](snippets/GenericWhereConstraints.cs#13)]

Önceki örnekte, `T` yönteminin bağlamındaki bir tür kısıtlamasıdır `Add` ve sınıfı bağlamında sınırsız bir tür parametresi olur `List` .

Tür parametreleri, genel sınıf tanımlarında kısıtlama olarak da kullanılabilir. Tür parametresi, diğer tür parametreleriyle birlikte açılı ayraç içinde bildirilmelidir:

[!code-csharp[using the class and struct constraints](snippets/GenericWhereConstraints.cs#14)]

Tür parametrelerinin genel sınıflarla kısıtlamalar olarak yararlılığı sınırlıdır, çünkü derleyici tür parametresi hakkında türetilmediği hariç hiçbir şey kabul edebilir `System.Object` . Tür parametrelerini, iki tür parametresi arasında bir devralma ilişkisi uygulamak istediğiniz senaryolarda genel sınıflarda kısıtlamalar olarak kullanın.

## <a name="notnull-constraint"></a>NotNull kısıtlaması

Bağımsız değişken olmayan bir bağlamda C# 8,0 ile başlayarak, `notnull` tür bağımsız değişkeninin null yapılamayan bir değer türü veya null yapılamayan bir başvuru türü olması gerektiğini belirtmek için kısıtlamasını kullanabilirsiniz. `notnull`Kısıtlama yalnızca bir `nullable enable` bağlamda kullanılabilir. `notnull`Kısıtlama, null yapılabilir bir zorunluluvou bağlamına eklerseniz bir uyarı oluşturur.

Diğer kısıtlamaların aksine, bir tür bağımsız değişkeni kısıtlamayı ihlal ettiğinde `notnull` , derleyici bu kod bir bağlamda derlenirse bir uyarı oluşturur `nullable enable` . Kod, null yapılabilir bir zorunluluvou bağlamında derlenmişse, derleyici hiçbir uyarı veya hata oluşturmaz.

Null olabilen bir bağlamda C# 8,0 ' den başlayarak `class` kısıtlama, tür bağımsız değişkeninin null yapılamayan bir başvuru türü olması gerektiğini belirtir. Null yapılabilir bir bağlamda, bir tür parametresi null olabilen bir başvuru türü olduğunda, derleyici bir uyarı oluşturur.

## <a name="unmanaged-constraint"></a>Yönetilmeyen kısıtlama

C# 7,3 ' den başlayarak, `unmanaged` tür parametresinin null atanamaz [yönetilmeyen bir tür](../../language-reference/builtin-types/unmanaged-types.md)olması gerektiğini belirtmek için kısıtlamasını kullanabilirsiniz. `unmanaged`Kısıtlama, aşağıdaki örnekte gösterildiği gibi, bellek blokları olarak işlenebilen türlerle çalışmak için yeniden kullanılabilir yordamlar yazmanızı sağlar:

[!code-csharp[using the unmanaged constraint](snippets/GenericWhereConstraints.cs#15)]

Önceki yöntem, `unsafe` `sizeof` yerleşik bir tür olarak bilinen bir tür üzerinde işleç kullandığından bir bağlamda derlenmelidir. Kısıtlama olmadan `unmanaged` `sizeof` işleç kullanılamaz.

`unmanaged`Kısıtlama `struct` kısıtlamayı belirtir ve onunla birleştirilemez. Kısıtlama `struct` kısıtlamayı gösterdiği için kısıtlama `new()` `unmanaged` kısıtlama ile birleştirilemez `new()` .

## <a name="delegate-constraints"></a>Temsilci kısıtlamaları

C# 7,3 ' den itibaren, <xref:System.Delegate?displayProperty=nameWithType> ya da <xref:System.MulticastDelegate?displayProperty=nameWithType> temel sınıf kısıtlaması olarak kullanabilirsiniz. CLR bu kısıtlamaya her zaman izin verilir, ancak C# dili izin vermez. `System.Delegate`Kısıtlama, temsilcilerle birlikte, tür açısından güvenli bir şekilde kod yazmanıza olanak sağlar. Aşağıdaki kod, iki temsilciyi aynı tür olduklarından birleştiren bir genişletme yöntemi tanımlar:

[!code-csharp[using the delegate constraint](snippets/GenericWhereConstraints.cs#16)]

Aynı türdeki temsilcileri birleştirmek için yukarıdaki yöntemi kullanabilirsiniz:

[!code-csharp[using the unmanaged constraint](snippets/GenericWhereConstraints.cs#17)]

Son satırın açıklamasını kaldırırsanız, derlenmez. Hem hem de `first` `test` temsilci türlerdir, ancak farklı temsilci türleridir.

## <a name="enum-constraints"></a>Sabit listesi kısıtlamaları

C# 7,3 ' den başlayarak, <xref:System.Enum?displayProperty=nameWithType> türü temel sınıf kısıtlaması olarak da belirtebilirsiniz. CLR bu kısıtlamaya her zaman izin verilir, ancak C# dili izin vermez. Kullanan genel türler `System.Enum` , içindeki statik yöntemleri kullanarak sonuçları önbelleğe almak için tür kullanımı uyumlu programlama sağlar `System.Enum` . Aşağıdaki örnek, bir sabit listesi türü için geçerli tüm değerleri bulur ve sonra bu değerleri dize gösterimiyle eşleyen bir sözlük oluşturur.

[!code-csharp[using the enum constraint](snippets/GenericWhereConstraints.cs#18)]

`Enum.GetValues`ve `Enum.GetName` performans etkilerine sahip olan yansıma kullanın. `EnumNamedValues`Yansıma gerektiren çağrıları yinelemek yerine önbelleğe alınmış ve yeniden kullanılan bir koleksiyon oluşturmak için öğesini çağırabilirsiniz.

Aşağıdaki örnekte gösterildiği gibi, bir sabit listesi oluşturmak ve değerlerini ve adlarını bir sözlüğü oluşturmak için kullanabilirsiniz:

[!code-csharp[enum definition](snippets/GenericWhereConstraints.cs#19)]

[!code-csharp[using the enum constrained method](snippets/GenericWhereConstraints.cs#20)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic>
- [C# Programlama Kılavuzu](../index.md)
- [Genel Türlere Giriş](./index.md)
- [Genel Sınıflar](./generic-classes.md)
- [Yeni kısıtlama](../../language-reference/keywords/new-constraint.md)
