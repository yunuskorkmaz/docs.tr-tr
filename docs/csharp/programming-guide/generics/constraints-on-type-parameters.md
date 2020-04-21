---
title: Tür parametrelerindeki kısıtlamalar - C# Programlama Kılavuzu
ms.date: 04/12/2018
helpviewer_keywords:
- generics [C#], type constraints
- type constraints [C#]
- type parameters [C#], constraints
- unbound type parameter [C#]
ms.openlocfilehash: 0035f7d8aa862b4bd1b09a6f122a89786a6e295b
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738261"
---
# <a name="constraints-on-type-parameters-c-programming-guide"></a>Tür parametreleri üzerindeki kısıtlamalar (C# Programlama Kılavuzu)

Kısıtlamalar derleyiciyi bir tür bağımsız değişkeninin sahip olması gereken özellikler hakkında bilgilendirir. Herhangi bir kısıtlama olmadan, tür bağımsız değişkeni herhangi bir tür olabilir. Derleyici yalnızca herhangi bir <xref:System.Object?displayProperty=nameWithType>.NET türü için nihai taban sınıf olan üyeleri varsayar. Daha fazla bilgi için neden [kısıtlamaları kullanın'a](#why-use-constraints)bakın. İstemci kodu kısıtlamayı karşılamayan bir tür kullanıyorsa, derleyici bir hata yayınlar. Kısıtlamalar `where` bağlamsal anahtar kelime kullanılarak belirtilir. Aşağıdaki tabloda yedi tür kısıtlama listelenebvardır:

|Kısıtlama|Açıklama|
|----------------|-----------------|
|`where T : struct`|Tür bağımsız değişkeni nullable olmayan bir değer türü olmalıdır. Nullable değer türleri hakkında bilgi için, [Nullable değer türleri](../../language-reference/builtin-types/nullable-value-types.md)bakın. Tüm değer türlerinin erişilebilir bir parametresiz `struct` oluşturucusu olduğundan, kısıtlama `new()` kısıtlamayı `new()` ima eder ve kısıtlamayla birleştirilemez. Kısıtlamaile `struct` kısıtlamayı birleştiremezsiniz. `unmanaged`|
|`where T : class`|Tür bağımsız değişkeni bir başvuru türü olmalıdır. Bu kısıtlama herhangi bir sınıf, arabirim, temsilci veya dizi türü için de geçerlidir. C# 8.0 veya sonraki bir şekilde `T` nullable bağlamında, nullable olmayan bir başvuru türü olmalıdır. |
|`where T : class?`|Tür bağımsız değişkeni, geçersiz veya nullable olmayan bir başvuru türü olmalıdır. Bu kısıtlama herhangi bir sınıf, arabirim, temsilci veya dizi türü için de geçerlidir.|
|`where T : notnull`|Tür bağımsız değişkeni nullable olmayan bir tür olmalıdır. Bağımsız değişken, C# 8.0 veya sonraki bir şekilde nullable olmayan bir başvuru türü veya nullable olmayan bir değer türü olabilir. |
|`where T : unmanaged`|Tür bağımsız değişkeni, geçersiz olmayan [yönetilmeyen](../../language-reference/builtin-types/unmanaged-types.md)bir tür olmalıdır. Kısıtlama `unmanaged` kısıtlamayı `struct` ima eder ve kısıtlamalarla `struct` `new()` birleştirilemez.|
|`where T : new()`|Tür bağımsız değişkeninin ortak parametresiz bir oluşturucusu olmalıdır. Diğer kısıtlamalarla birlikte kullanıldığında, `new()` kısıtlama nın en son belirtilmesi gerekir. Kısıtlama `new()` `struct` ve `unmanaged` kısıtlamalarla birleştirilemez.|
|`where T :`taban sınıf adı>* \<*|Tür bağımsız değişkeni, belirtilen taban sınıftan türemelidir. C# 8.0 ve sonraki nullable `T` bağlamında, belirtilen taban sınıftan türetilen bir nullable olmayan bir başvuru türü olmalıdır. |
|`where T :`taban sınıf adı>? * \<*|Tür bağımsız değişkeni, belirtilen taban sınıftan türemelidir. C# 8.0 ve sonraki bir şekilde `T` nullable bağlamında, belirtilen taban sınıftan türetilen nullable veya unnullable türü olabilir. |
|`where T :`arayüz adı>* \<*|Tür bağımsız değişkeni, belirtilen arabirimi olmalıdır veya uygulamalıdır. Birden çok arabirim kısıtlaması belirtilebilir. Kısıtlayıcı arabirim de genel olabilir. C# 8.0 ve sonraki bir nullable bağlamında, `T` belirtilen arabirimi uygulayan nullable olmayan bir tür olmalıdır.|
|`where T :`arayüz adı>? * \<*|Tür bağımsız değişkeni, belirtilen arabirimi olmalıdır veya uygulamalıdır. Birden çok arabirim kısıtlaması belirtilebilir. Kısıtlayıcı arabirim de genel olabilir. C# 8.0'daki nullable `T` bağlamında, nullable başvuru türü, nullable olmayan bir başvuru türü veya bir değer türü olabilir. `T`nullable değer türü olmayabilir.|
|`where T : U`|Için `T` verilen tür bağımsız değişkeni, '' için `U`verilen bağımsız değişkenden türemelidir. Nullable bağlamında, nullable olmayan bir başvuru türü `T` ise, `U` nullable olmayan başvuru türü olmalıdır. Nullable `U` bir başvuru türü `T` ise, nullable veya unnullable olabilir. |

## <a name="why-use-constraints"></a>Neden kısıtlamaları kullanın

Kısıtlamalar, bir tür parametresinin yeteneklerini ve beklentilerini belirtir. Bu kısıtlamaları bildirmek, kısıtlama türündeki işlemleri ve yöntem çağrılarını kullanabileceğiniz anlamına gelir. Genel sınıfınız veya yönteminiz, genel üyeler üzerinde basit atamanın ötesinde <xref:System.Object?displayProperty=nameWithType>herhangi bir işlem kullanıyorsa veya desteklenmeyen yöntemleri arıyorsa, tür parametresine kısıtlamalar uygulamanız gerekir. Örneğin, taban sınıf kısıtlaması derleyiciye yalnızca bu türdeki veya bu türden türetilen nesnelerin tür bağımsız değişkeni olarak kullanılacağını söyler. Derleyici bu garantiye sahip olduktan sonra, bu tür yöntemlerin genel sınıfta çağrılmasını sağlayabilir. Aşağıdaki kod örneği, taban sınıf kısıtlaması `GenericList<T>` uygulayarak sınıfa [(Genel Lere](../../../standard/generics/index.md)Giriş'te) ekleyebileceğiniz işlevselliği gösterir.

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#9)]

Kısıtlama, genel sınıfın `Employee.Name` özelliği kullanmasını sağlar. Kısıtlama, türdeki `T` tüm öğelerin bir `Employee` nesne veya devralan bir nesne olarak `Employee`garanti edilir olduğunu belirtir.

Aynı tür parametresine birden çok kısıtlama uygulanabilir ve kısıtlamaların kendileri aşağıdaki gibi genel türler olabilir:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#10)]

Kısıtlamayı `where T : class` uygularken, bu `==` `!=` işleçler değer eşitliği için değil, yalnızca referans kimliği için test edecek tür parametresi üzerinde ve işleçleri kaçının. Bu davranış, bu işleçler bağımsız değişken olarak kullanılan bir türde aşırı yüklenmiş olsa bile oluşur. Aşağıdaki kod bu noktayı göstermektedir; <xref:System.String> sınıf `==` işleci aşırı yüklese bile çıktı yanlıştır.

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#11)]

Derleyici yalnızca derleme `T` zamanında bir başvuru türü olduğunu bilir ve tüm başvuru türleri için geçerli olan varsayılan işleçleri kullanması gerekir. Değer eşitliği için sınamanız gerekiyorsa, önerilen yol `where T : IEquatable<T>` `where T : IComparable<T>` aynı zamanda kısıtlamayı uygulamak ve genel sınıfı oluşturmak için kullanılacak herhangi bir sınıfta arabirimi uygulamaktır.

## <a name="constraining-multiple-parameters"></a>Birden çok parametreyi zorlama

Aşağıdaki örnekte gösterildiği gibi, kısıtlamaları birden çok parametreye ve birden çok kısıtlamayı tek bir parametreye uygulayabilirsiniz:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#12)]

## <a name="unbounded-type-parameters"></a>Sınırsız tür parametreleri

 Ortak sınıfta `SampleClass<T>{}`Ki'si gibi kısıtlaması olmayan tür parametreleri, sınırsız tür parametreleri olarak adlandırılır. Sınırsız tür parametreleri aşağıdaki kurallara sahiptir:

- Somut `!=` `==` tür bağımsız değişkeninin bu işleçleri destekleyeceğinin garantisi olmadığından, ve işleçler kullanılamaz.
- Bunlar herhangi bir arabirim `System.Object` türüne dönüştürülebilir veya açıkça herhangi bir arabirim türüne dönüştürülebilir.
- Null [ile](../../language-reference/keywords/null.md)karşılaştırabilirsiniz. Sınırlanmamış bir parametre ile `null`karşılaştırıldığında, tür bağımsız değişkeni bir değer türüise karşılaştırma her zaman yanlış döndürecektir.

## <a name="type-parameters-as-constraints"></a>Parametreleri kısıtlama olarak yazın

Genel bir tür parametresinin kısıtlama olarak kullanılması, kendi türü parametresine sahip bir üye işlevin, aşağıdaki örnekte gösterildiği gibi, bu parametreyi içeren tür türü parametresiyle sınırlandırması gerektiğinde yararlıdır:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#13)]

Önceki örnekte, `T` `Add` yöntem bağlamında bir tür kısıtlaması ve `List` sınıf bağlamında sınırsız bir tür parametresi vardır.

Tür parametreleri, genel sınıf tanımlarında kısıtlama olarak da kullanılabilir. Tip parametresi, açı braketi içinde diğer tip parametrelerle birlikte bildirilmelidir:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#14)]

Derleyici, `System.Object`tür parametresi hakkında türetilmiştir dışında hiçbir şey varsayamayacağından, genel sınıflarla birlikte kısıtlama olarak tür parametrelerinin kullanışlılığı sınırlıdır. İki tür paramı arasında devralma ilişkisini zorlamak istediğiniz senaryolarda genel sınıflarda tür parametrelerini kısıtlama olarak kullanın.

## <a name="notnull-constraint"></a>NotNull kısıtlama

Nullable bağlamında C# 8.0 ile başlayarak, `notnull` tür bağımsız değişkeninin nullable olmayan bir değer türü veya nullable olmayan başvuru türü olması gerektiğini belirtmek için kısıtlamak kullanabilirsiniz. Kısıtlama `notnull` yalnızca bir `nullable enable` bağlam içinde kullanılabilir. Kısıtlamayı `notnull` boş bir içeriğe eklerseniz derleyici bir uyarı oluşturur.

Diğer kısıtlamaların aksine, bir tür `notnull` bağımsız değişkeni kısıtlamayı ihlal ettiğinde, derleyici bu `nullable enable` kod bir bağlam içinde derlendiğinde bir uyarı oluşturur. Kod boş bir şekilde derlenirse, derleyici herhangi bir uyarı veya hata oluşturmaz.

Nullable bağlamında C# 8.0 ile `class` başlayarak, kısıtlama türü bağımsız değişkeninin nullable olmayan bir başvuru türü olması gerektiğini belirtir. Nullable bağlamında, bir tür parametresi nullable başvuru türü olduğunda, derleyici bir uyarı oluşturur.

## <a name="unmanaged-constraint"></a>Yönetilmeyen kısıtlama

C# 7.3 ile başlayarak, `unmanaged` tür parametresinin geçersiz olmayan [yönetilmeyen](../../language-reference/builtin-types/unmanaged-types.md)bir tür olması gerektiğini belirtmek için kısıtlamayı kullanabilirsiniz. Kısıtlama, `unmanaged` aşağıdaki örnekte gösterildiği gibi, bellek blokları olarak değiştirilebilen türlerle çalışmak için yeniden kullanılabilir yordamlar yazmanızı sağlar:

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#15)]

İşleç, yerleşik bir tür `unsafe` olarak bilinen bir türde işleci kullandığından, önceki yöntem bir bağlamda derlenmelidir. `sizeof` Kısıtlama `unmanaged` `sizeof` olmadan, işleç kullanılamaz.

Kısıtlama `unmanaged` kısıtlamayı `struct` ima eder ve onunla birleştirilemez. `struct` Kısıtlama kısıtlamayı `new()` ima ettiği `unmanaged` için, kısıtlama `new()` kısıtlamayla da birleştirilemez.

## <a name="delegate-constraints"></a>Temsilci kısıtlamaları

Ayrıca C# 7.3 ile başlayarak, kullanabilirsiniz <xref:System.Delegate?displayProperty=nameWithType> veya <xref:System.MulticastDelegate?displayProperty=nameWithType> bir taban sınıf kısıtlaması olarak. CLR her zaman bu kısıtlamaya izin verdi, ancak C# dili buna izin vermedi. Kısıtlama, `System.Delegate` temsilcilerle tür güvenli bir şekilde çalışan kod yazmanızı sağlar. Aşağıdaki kod, aynı türde olmaları koşuluyla iki temsilciyi birleştiren bir uzantı yöntemi tanımlar:

[!code-csharp[using the delegate constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#16)]

Yukarıdaki yöntemi, aynı türdeki temsilcileri birleştirmek için kullanabilirsiniz:

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#17)]

Son satırı açıklamazsanız, derleme olmaz. Her `first` `test` ikisi de ve temsilci türleri, ancak farklı temsilci türleri.

## <a name="enum-constraints"></a>Enum kısıtlamaları

C# 7.3'ten başlayarak, <xref:System.Enum?displayProperty=nameWithType> türü taban sınıf kısıtlaması olarak da belirtebilirsiniz. CLR her zaman bu kısıtlamaya izin verdi, ancak C# dili buna izin vermedi. Genel olarak `System.Enum` kullanan genel `System.Enum`ler, statik yöntemleri kullanarak sonuçları önbelleğe almak için tür için güvenli programlama sağlar. Aşağıdaki örnek, bir enum türü için tüm geçerli değerleri bulur ve sonra bu değerleri dize gösterimi ile eşleyen bir sözlük oluşturur.

[!code-csharp[using the enum constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#18)]

Performans etkileri olan yansımakullanımı nda kullanılan yöntemler. Bu yöntemi, yansıma gerektiren çağrıları yinelemek yerine önbelleğe alınmış ve yeniden kullanılan bir koleksiyon oluşturmak için arayabilirsiniz.

Bir enum oluşturmak ve değerleri ve adlarından oluşan bir sözlük oluşturmak için aşağıdaki örnekte gösterildiği gibi kullanabilirsiniz:

[!code-csharp[enum definition](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#19)]

[!code-csharp[using the enum constrained method](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#20)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic>
- [C# Programlama Kılavuzu](../index.md)
- [Genel Türlere Giriş](./index.md)
- [Genel Sınıflar](./generic-classes.md)
- [yeni Kısıtlama](../../language-reference/keywords/new-constraint.md)
