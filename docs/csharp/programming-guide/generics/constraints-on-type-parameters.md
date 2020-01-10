---
title: Tür parametrelerine yönelik kısıtlamalar- C# Programlama Kılavuzu
ms.date: 04/12/2018
helpviewer_keywords:
- generics [C#], type constraints
- type constraints [C#]
- type parameters [C#], constraints
- unbound type parameter [C#]
ms.openlocfilehash: 3ce68ecc1f0740fdb43ccf22b636dcd4bc05ea0a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712240"
---
# <a name="constraints-on-type-parameters-c-programming-guide"></a>Tür Parametrelerindeki Kısıtlamalar (C# Programlama Kılavuzu)

Kısıtlamalar, derleyicisini bir tür bağımsız değişkeni olması gereken yetenekler hakkında bilgilendirir. Herhangi bir kısıtlama olmadan tür bağımsız değişkeni herhangi bir tür olabilir. Derleyici yalnızca, tüm .NET türleri için en son temel sınıf olan <xref:System.Object?displayProperty=nameWithType>üyelerini kabul edebilir. Daha fazla bilgi için bkz. [kısıtlamaların neden kullanılması](#why-use-constraints). İstemci kodu bir kısıtlama tarafından izin verilmeyen bir tür kullanarak sınıfınızın örneğini oluşturmaya çalışırsa, sonuç derleme zamanı hatasıdır. Kısıtlamalar `where` bağlamsal anahtar sözcüğü kullanılarak belirtilir. Aşağıdaki tabloda yedi tür kısıtlama listelenmektedir:

|Kısıtlaması|Açıklama|
|----------------|-----------------|
|`where T : struct`|Tür bağımsız değişkeni null yapılamayan bir değer türü olmalıdır. Nullable değer türleri hakkında daha fazla bilgi için bkz. [Nullable değer türleri](../../language-reference/builtin-types/nullable-value-types.md). Tüm değer türlerinde erişilebilir parametresiz bir Oluşturucu olduğundan, `struct` kısıtlaması `new()` kısıtlamasını gösterir ve `new()` kısıtlaması ile birleştirilemez. Ayrıca `struct` kısıtlamasını `unmanaged` kısıtlamasıyla birleştiremezsiniz.|
|`where T : class`|Tür bağımsız değişkeni bir başvuru türü olmalıdır. Bu kısıtlama, her sınıf, arabirim, temsilci veya dizi türü için de geçerlidir.|
|`where T : notnull`|Tür bağımsız değişkeni null yapılamayan bir tür olmalıdır. Bağımsız değişken, C# 8,0 veya sonraki bir sürümde null atanamaz bir başvuru türü veya null yapılamayan bir değer türü olabilir. Bu kısıtlama, her sınıf, arabirim, temsilci veya dizi türü için de geçerlidir.|
|`where T : unmanaged`|Tür bağımsız değişkeni null atanamaz bir [yönetilmeyen tür](../../language-reference/builtin-types/unmanaged-types.md)olmalıdır. `unmanaged` kısıtlaması `struct` kısıtlamasını gösterir ve `struct` ya da `new()` kısıtlamalarıyla birleştirilemez.|
|`where T : new()`|Tür bağımsız değişkeni Ortak parametresiz bir oluşturucuya sahip olmalıdır. Diğer kısıtlamalarla birlikte kullanıldığında, `new()` kısıtlamasının en son belirtilmesi gerekir. `new()` kısıtlaması `struct` ve `unmanaged` kısıtlamalarıyla birleştirilemez.|
|`where T :` *\<temel sınıf adı >*|Tür bağımsız değişkeni belirtilen temel sınıftan olmalıdır veya türetilmelidir.|
|`where T :` *\<arabirimi adı >*|Tür bağımsız değişkeni belirtilen arabirimi içermelidir veya uygulamalıdır. Birden çok arabirim kısıtlaması belirlenebilir. Kısıtlama arabirimi de genel olabilir.|
|`where T : U`|T için sağlanan tür bağımsız değişkeni U için sağlanan bağımsız değişkenden türetilmiş veya türemelidir.|

## <a name="why-use-constraints"></a>Neden kısıtlama kullanılmalıdır

Tür parametresini kısıtlayan, izin verilen işlem ve metot çağrılarının sayısını kısıtlayan türü tarafından desteklenenlere ve devralma hiyerarşisindeki tüm türlere göre artırırsınız. Genel sınıfları veya yöntemleri tasarlarken, Genel Üyeler üzerinde basit atama veya <xref:System.Object?displayProperty=nameWithType>tarafından desteklenmeyen yöntemler çağırma durumunda herhangi bir işlem gerçekleştiriyorsunuz, tür parametresine kısıtlamalar uygulamanız gerekir. Örneğin, temel sınıf kısıtlaması derleyiciye yalnızca bu türden veya bu türden türetilmiş nesnelerin tür bağımsız değişkenleri olarak kullanılacağını söyler. Derleyiciye bu garanti verildikten sonra, genel sınıfta bu tür yöntemlerin çağrılmasına izin verebilir. Aşağıdaki kod örneği, bir temel sınıf kısıtlaması uygulayarak `GenericList<T>` sınıfına ekleyebileceğiniz işlevselliği gösterir ( [Genel türlere giriş](../../../standard/generics/index.md)olarak).

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#9)]

Kısıtlama, genel sınıfın `Employee.Name` özelliğini kullanmasını sağlar. Kısıtlama, `T` türündeki tüm öğelerin `Employee` bir nesne veya `Employee`devralan bir nesne olduğunu belirtir.

Aynı tür parametresine birden çok kısıtlama uygulanabilir ve kısıtlamalar aşağıdaki gibi genel türler olabilir:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#10)]

`where T : class` kısıtlaması uygulanırken, tür parametresindeki `==` ve `!=` işleçlerden kaçının, çünkü bu işleçler yalnızca başvuru kimliğini test edecek, değer eşitlik için değil. Bu davranış, bu işleçler bağımsız değişken olarak kullanılan bir türde aşırı yüklense bile oluşur. Aşağıdaki kod bu noktayı gösterir; <xref:System.String> sınıfı `==` işlecini aşırı yüklese de çıkış yanlış olur.

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#11)]

Derleyici, derleme zamanında `T` bir başvuru türü olduğunu ve tüm başvuru türleri için geçerli olan varsayılan işleçleri kullanması gerektiğini bilir. Değer eşitlik için test etmeniz gerekiyorsa, önerilen yol `where T : IEquatable<T>` veya `where T : IComparable<T>` kısıtlamasını de uygulamak ve arayüzü genel sınıfı oluşturmak için kullanılacak herhangi bir sınıfa uygulamaktır.

## <a name="constraining-multiple-parameters"></a>Birden çok parametreyi kısıtlama

Aşağıdaki örnekte gösterildiği gibi birden çok parametreye kısıtlama uygulayabilir ve tek bir parametreye birden çok kısıtlama uygulayabilirsiniz:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#12)]

## <a name="unbounded-type-parameters"></a>Sınırlandırılmamış tür parametreleri

 Ortak sınıf `SampleClass<T>{}`gibi hiçbir kısıtlaması olmayan tür parametrelerine, sınırlandırılmamış tür parametreleri denir. Sınırlandırılmamış tür parametreleri aşağıdaki kurallara sahiptir:

- Somut tür bağımsız değişkeninin bu işleçleri destekleyeceği garantisi olmadığından `!=` ve `==` işleçleri kullanılamıyor.
- Bunlara veya `System.Object` dönüştürülebilir ya da açıkça herhangi bir arabirim türüne dönüştürülebilir.
- Bunları [null](../../language-reference/keywords/null.md)ile karşılaştırabilirsiniz. Sınırlandırılmamış bir parametre `null`ile karşılaştırıldığında, tür bağımsız değişkeni bir değer türündeyse karşılaştırma her zaman false döndürür.

## <a name="type-parameters-as-constraints"></a>Parametreleri kısıtlamalar olarak yazın

Genel tür parametresinin bir kısıtlama olarak kullanılması, aşağıdaki örnekte gösterildiği gibi, kendi tür parametresine sahip bir üye işlevi bu parametreyi kapsayan türün tür parametresiyle kısıtlamak için yararlıdır:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#13)]

Önceki örnekte `T`, `Add` yönteminin bağlamındaki bir tür kısıtlamasıdır ve `List` sınıfının bağlamında sınırsız bir tür parametresi olur.

Tür parametreleri, genel sınıf tanımlarında kısıtlama olarak da kullanılabilir. Tür parametresi, diğer tür parametreleriyle birlikte açılı ayraç içinde bildirilmelidir:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#14)]

Derleyici tür parametresi hakkında hiçbir şey `System.Object`türetilmediği hariç, genel sınıflarla kısıtlamalar olarak tür parametrelerinin kullanışlılığı sınırlıdır. Tür parametrelerini, iki tür parametresi arasında bir devralma ilişkisi uygulamak istediğiniz senaryolarda genel sınıflarda kısıtlamalar olarak kullanın.

## <a name="notnull-constraint"></a>NotNull kısıtlaması

8,0 ile C# başlayarak, tür bağımsız değişkeninin null yapılamayan bir değer türü veya null yapılamayan bir başvuru türü olması gerektiğini belirtmek için `notnull` kısıtlamasını kullanabilirsiniz. `notnull` kısıtlaması yalnızca bir `nullable enable` bağlamında kullanılabilir. `notnull` kısıtlamasını null yapılabilir bir zorunluluvou bağlamına eklerseniz derleyici bir uyarı oluşturur. 

Diğer kısıtlamaların aksine, bir tür bağımsız değişkeni `notnull` kısıtlamasını ihlal ettiğinde, bu kod bir `nullable enable` bağlamında derlenirse derleyici bir uyarı oluşturur. Kod, null yapılabilir bir zorunluluvou bağlamında derlenmişse, derleyici hiçbir uyarı veya hata oluşturmaz.

## <a name="unmanaged-constraint"></a>Yönetilmeyen kısıtlama

7,3 ile C# başlayarak, tür parametresinin null atanamaz [yönetilmeyen bir tür](../../language-reference/builtin-types/unmanaged-types.md)olması gerektiğini belirtmek için `unmanaged` kısıtlamasını kullanabilirsiniz. `unmanaged` kısıtlaması, aşağıdaki örnekte gösterildiği gibi, bellek blokları olarak işlenebilen türlerle çalışmak için yeniden kullanılabilir yordamlar yazmanızı sağlar:

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#15)]

Yukarıdaki yöntemin, yerleşik tür olarak bilinen bir tür üzerinde `sizeof` işlecini kullandığından `unsafe` bağlamda derlenmesi gerekir. `unmanaged` kısıtlaması olmadan `sizeof` işleci kullanılamaz.

`unmanaged` kısıtlaması `struct` kısıtlamasını gösterir ve onunla birleştirilemez. `struct` kısıtlaması `new()` kısıtlamasını gösterdiği için `unmanaged` kısıtlaması de `new()` kısıtlaması ile birleştirilemez.

## <a name="delegate-constraints"></a>Temsilci kısıtlamaları

Ayrıca, 7,3 C# ile başlayarak temel sınıf kısıtlaması olarak <xref:System.Delegate?displayProperty=nameWithType> veya <xref:System.MulticastDelegate?displayProperty=nameWithType> kullanabilirsiniz. CLR bu kısıtlamaya her zaman izin verilir, ancak C# dil izin vermez. `System.Delegate` kısıtlaması, temsilcilerle birlikte, tür açısından güvenli bir şekilde sorunsuz kod yazmanıza olanak sağlar. Aşağıdaki kod, iki temsilciyi aynı tür olduklarından birleştiren bir genişletme yöntemi tanımlar:

[!code-csharp[using the delegate constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#16)]

Aynı türdeki temsilcileri birleştirmek için yukarıdaki yöntemi kullanabilirsiniz:

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#17)]

Son satırın açıklamasını kaldırırsanız, derlenmez. Hem `first` hem de `test` temsilci türleridir, ancak farklı temsilci türleridir.

## <a name="enum-constraints"></a>Sabit listesi kısıtlamaları

C# 7,3 ' den başlayarak, <xref:System.Enum?displayProperty=nameWithType> türünü temel sınıf kısıtlaması olarak da belirtebilirsiniz. CLR bu kısıtlamaya her zaman izin verilir, ancak C# dil izin vermez. `System.Enum` kullanan genel türler, `System.Enum`statik yöntemlerin kullanılmasıyla sonuçları önbelleğe almak için tür kullanımı uyumlu programlama sağlar. Aşağıdaki örnek, bir sabit listesi türü için geçerli tüm değerleri bulur ve sonra bu değerleri dize gösterimiyle eşleyen bir sözlük oluşturur.

[!code-csharp[using the enum constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#18)]

Performans etkilerine sahip olan yansıma kullanımını sağlamak için kullanılan yöntemler. Bu yöntemi, yansıma gerektiren çağrıları yinelemek yerine önbelleğe alınmış ve yeniden kullanılan bir koleksiyon oluşturmak için çağırabilirsiniz.

Aşağıdaki örnekte gösterildiği gibi, bir sabit listesi oluşturmak ve değerlerini ve adlarını bir sözlüğü oluşturmak için kullanabilirsiniz:

[!code-csharp[enum definition](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#19)]

[!code-csharp[using the enum constrained method](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#20)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic>
- [C# Programlama Kılavuzu](../index.md)
- [Genel Türlere Giriş](./index.md)
- [Genel Sınıflar](./generic-classes.md)
- [new Kısıtlaması](../../language-reference/keywords/new-constraint.md)
