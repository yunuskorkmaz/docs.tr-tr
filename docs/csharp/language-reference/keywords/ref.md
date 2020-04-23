---
title: ref anahtar kelime - C# Referans
ms.date: 04/21/2020
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: 07e1b49605c83908f7b9af25e0cb2599a97257c5
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102079"
---
# <a name="ref-c-reference"></a>ref (C# Başvurusu)

Anahtar `ref` kelime, başvuru yla geçirilen bir değeri gösterir. Dört farklı bağlamda kullanılır:

- Bir yöntem imza ve bir yöntem arama, başvuru ile bir yönteme bir argüman geçmek için. Daha fazla bilgi için [bkz.](#passing-an-argument-by-reference)
- Bir yöntem imzasında, başvuru ile arayana bir değer döndürmek için. Daha fazla bilgi için [Bkz. Başvuru iade değerleri.](#reference-return-values)
- Bir üye gövdesinde, bir referans dönüş değerinin, arayanın değiştirmek istediği bir başvuru olarak yerel olarak depolandığını veya genel olarak yerel bir değişkenin başvuru yla başka bir değere eriştiğini belirtmek için. Daha fazla bilgi için Ref [yerel bilgilerine](#ref-locals)bakın.
- Bir `struct` veya bir `ref struct` `readonly ref struct`beyanda . Daha fazla bilgi [ `ref` ](../builtin-types/struct.md#ref-struct) için Yapı [türleri](../builtin-types/struct.md) makalesinin yapı bölümüne bakın.

## <a name="passing-an-argument-by-reference"></a>Bir bağımsız değişkeni başvuruyla geçirme

Bir yöntemin `ref` parametre listesinde kullanıldığında, anahtar kelime bir bağımsız değişkenin değere göre değil, başvuru yla geçirildiğini gösterir. Anahtar `ref` kelime, resmi parametreyi bağımsız değişken için bir diğer ad yapar ve bu da değişken olmalıdır. Başka bir deyişle, parametre üzerinde herhangi bir işlem bağımsız değişken üzerinde yapılır. Örneğin, arayan yerel bir değişken ifadesini veya dizi öğesi erişim ifadesini geçerse ve çağrılan yöntem ref parametrenin başvurulduğu nesnenin yerini alırsa, arayanın yerel değişkeni veya dizi öğesi yöntem döndüğünde şimdi yeni nesneye başvurur.

> [!NOTE]
> Referans la geçme kavramını başvuru türleri kavramıyla karıştırmayın. İki kavram aynı değildir. Yöntem parametresi, değer `ref` türü veya başvuru türü olup olmadığına bakılmaksızın değiştirilebilir. Başvuru yla geçirildiğinde değer türünün kutulamayoktur.  

Bir `ref` parametre kullanmak için, hem yöntem tanımı hem de `ref` arama yöntemi, aşağıdaki örnekte gösterildiği gibi anahtar kelimeyi açıkça kullanmalıdır.  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

Bir `ref` veya `in` parametreye geçirilen bir bağımsız değişken geçirilmeden önce başharfe atılmalıdır. Bu, bağımsız değişkenleri geçirilmeden önce açıkça başlatılması gerekmeyen [dış](out-parameter-modifier.md) parametrelerden farklıdır.

Bir sınıfın üyeleri yalnızca `ref`, `in`veya `out`. Bir türiki üye arasındaki tek fark, birinin `ref` parametresi, diğerinin ise bir `out`parametresi `in` veya parametresi olması ysa derleyici hatası oluşur. Örneğin, aşağıdaki kod derlenmiyor.  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```

Ancak, yöntemlerden biri `ref`, , `in`parametresi `out` ve diğer bir değer parametresi varsa, aşağıdaki örnekte gösterildiği gibi aşırı yüklenebilir.
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 Gizleme veya geçersiz kılma `in` `ref`gibi imza eşleştirmegerektiren ve imzanın bir parçası olan ve `out` birbiriyle eşleşmeyen diğer durumlarda.  
  
 Özellikler değişken değildir. Bunlar yöntemdir ve parametrelere `ref` geçirilemez.  
  
 Aşağıdaki yöntem türleri `ref`için `in`, `out` ve anahtar kelimeleri kullanamazsınız:  
  
- Async değiştirici kullanarak tanımladığınız [async](async.md) yöntemleri.  
- [Verim getirisi](yield.md) veya `yield break` deyimi içeren yineleyici yöntemleri.

Buna ek olarak, [uzantı yöntemleri](../../programming-guide/classes-and-structs/extension-methods.md) aşağıdaki kısıtlamalara sahiptir:

- Anahtar `out` kelime, bir uzantı yönteminin ilk bağımsız değişkeninde kullanılamaz.
- Anahtar `ref` kelime, bağımsız değişken bir yapı olmadığında veya yapı olarak sınırlandırılmamış genel bir tür olduğunda, uzantı yönteminin ilk bağımsız değişkeninde kullanılamaz.
- İlk `in` bağımsız değişken bir yapı olmadığı sürece anahtar sözcük kullanılamaz. Anahtar `in` kelime, yapı olarak sınırlandırılsa bile, herhangi bir genel türde kullanılamaz.

## <a name="passing-an-argument-by-reference-an-example"></a>Bir bağımsız değişkeni başvuruyla geçirme: Bir örnek

Önceki örnekler referansa göre değer türlerini geçer. Referans türlerini `ref` başvuruya göre geçirmek için anahtar sözcüğü de kullanabilirsiniz. Başvuru türünü referansla geçmek, başvuru parametresinin arayanda başvururolduğu nesneyi değiştirmek için çağrılan yöntemin değiştirilmesine olanak tanır. Nesnenin depolama konumu, başvuru parametresi değeri olarak yönteme geçirilir. Parametrenin depolama konumundaki değeri değiştirirseniz (yeni bir nesneye işaret etmek için), arayanın başvurulması gereken depolama konumunu da değiştirirsiniz. Aşağıdaki örnek, `ref` parametre olarak bir başvuru türü örneğini geçer.
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

Referans türlerinin değere ve başvuruya göre nasıl geçirilen hakkında daha fazla bilgi için [Bkz.](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md)
  
## <a name="reference-return-values"></a>Başvuru dönüş değerleri

Başvuru iade değerleri (veya ref returns) bir yöntemin arayana başvuruyla döndürdettiği değerlerdir. Diğer bir deyişle, arayan bir yöntem tarafından döndürülen değeri değiştirebilir ve bu değişiklik arama yönteminde nesnenin durumuna yansıtılır.

Bir referans iade değeri anahtar `ref` sözcüğü kullanılarak tanımlanır:

- Yöntem imzasında. Örneğin, aşağıdaki yöntem imzası yöntemin `GetCurrentPrice` başvuru <xref:System.Decimal> tarafından bir değer döndürür gösterir.

```csharp
public ref decimal GetCurrentPrice()
```

- Belirteç `return` ve değişken arasında `return` yöntemde bir ifade döndürülür. Örneğin:

```csharp
return ref DecimalArray[0];
```

Arayanın nesnenin durumunu değiştirebilmesi için, başvuru iade değerinin ref [yerel](#ref-locals)olarak açıkça tanımlanan bir değişkene depolanmış olması gerekir.

Burada yöntem imza ve yöntem gövdesi hem gösteren daha eksiksiz bir ref dönüş örneğidir.

[!code-csharp[FindReturningRef](~/samples/snippets/csharp/new-in-7/MatrixSearch.cs#FindReturningRef "Find returning by reference")]

Çağrılan yöntem, iade değerini başvuru `ref readonly` yla değeri döndürecek şekilde bildirebilir ve arama kodunun döndürülen değeri değiştiremeyeceğini zorlayabilir. Arama yöntemi, değeri yerel bir [ref readonly](#ref-readonly-locals) değişkeninde depolayarak döndürülen değeri kopyalamaktan kaçınabilir.

Örneğin, [bkz.](#a-ref-returns-and-ref-locals-example)

## <a name="ref-locals"></a>Ref yerlileri

Ref yerel değişkeni kullanılarak `return ref`döndürülen değerlere başvurmak için kullanılır. Bir ref yerel değişkeni, ref olmayan bir geri dönüş değerine başolarak başlılamaz. Başka bir deyişle, başlaştırmanın sağ tarafı bir başvuru olmalıdır. Ref yerel değeri herhangi bir değişiklik yöntemi referans tarafından değeri döndürülen nesnenin durumuna yansıtılır.

Değişken bildiriminden `ref` önce anahtar sözcüğü kullanarak ve başvuru değeri döndüren yönteme çağrıdan hemen önce bir ref yerel tanımlarsınız.

Örneğin, aşağıdaki deyim, adlı `GetEstimatedValue`bir yöntemle döndürülen bir ref yerel değerini tanımlar:

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

Bir değere aynı şekilde başvuru yla erişebilirsiniz. Bazı durumlarda, bir değere referans la erişmek, pahalı olabilecek bir kopyalama işleminden kaçınarak performansı artırır. Örneğin, aşağıdaki deyim, bir değere başvurmak için kullanılan bir ref yerel değerini nasıl tanımlayabileceğini gösterir.

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

Her iki `ref` örnekte de anahtar kelime her iki yerde de kullanılmalıdır veya derleyici CS8172 hatası oluşturur, "Bir değerle bir referans değişkeni başharflenemez."

C# 7.3 ile başlayarak, ifadenin `foreach` yineleme değişkeni ref lokal veya ref readonlyonly local değişken olabilir. Daha fazla bilgi için [foreach deyimi](foreach-in.md) makalesine bakın.

Ayrıca C# 7.3 ile başlayarak, [ref atama işleci](../operators/assignment-operator.md#ref-assignment-operator)ile bir ref yerel veya ref readonlyonly local değişken yeniden atayabilirsiniz.

## <a name="ref-readonly-locals"></a>Ref sadece yerlileri okuyor

Bir ref readonly yerel imzası ve kullandığı `ref readonly` `return ref`yöntem veya özellik tarafından döndürülen değerleri başvurmak için kullanılır. Bir `ref readonly` değişken yerel değişkenin `ref` özelliklerini bir `readonly` değişkenle birleştirir: atandığı depolamanın diğer adıdır ve değiştirilemez.

## <a name="a-ref-returns-and-ref-locals-example"></a>Bir ref döner ve ref locals örneği

Aşağıdaki örnekte iki `Book` <xref:System.String> alanı olan bir `Title` `Author`sınıf tanımlanır ve . Ayrıca, özel `BookCollection` bir `Book` nesne dizisi içeren bir sınıf tanımlar. Tek tek kitap nesneleri, `GetBookByTitle` yöntemini çağırarak referans la döndürülür.

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

Arayan `GetBookByTitle` yöntem tarafından döndürülen değeri bir ref yerel olarak depoladığında, aşağıdaki örnekte görüldüğü `BookCollection` gibi, arayanın return value'a yaptığı değişiklikler nesneye yansıtılır.

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli verimli kod yazın](../../write-safe-efficient-code.md)
- [Ref dönüşler ve ref yerel ayarlar](../../programming-guide/classes-and-structs/ref-returns.md)
- [Koşullu ref ekspresyonu](../operators/conditional-operator.md#conditional-ref-expression)
- [Geçme Parametreleri](../../programming-guide/classes-and-structs/passing-parameters.md)
- [Yöntem Parametreleri](method-parameters.md)
- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Kelimeler](index.md)
