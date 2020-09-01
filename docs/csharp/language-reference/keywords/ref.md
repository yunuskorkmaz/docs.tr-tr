---
description: ref anahtar sözcüğü-C# başvurusu
title: ref anahtar sözcüğü-C# başvurusu
ms.date: 04/21/2020
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: 58a4ce30e11ca023b50e5e53b1f1554a30d44390
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137090"
---
# <a name="ref-c-reference"></a>ref (C# Başvurusu)

`ref`Anahtar sözcüğü, başvuruya göre geçirilen bir değeri gösterir. Dört farklı bağlamda kullanılır:

- Bir yöntem imzasında ve bir yöntem çağrısında, bir bağımsız değişkeni başvuruya göre bir yönteme geçirmek için. Daha fazla bilgi için bkz. [bir bağımsız değişkeni başvuruya göre geçirme](#passing-an-argument-by-reference).
- Bir yöntem imzasında, çağıran öğesine başvuruya göre bir değer döndürün. Daha fazla bilgi için bkz. [Başvuru dönüş değerleri](#reference-return-values).
- Bir üye gövdesinde, bir başvuru dönüş değerinin, çağıranın değiştirme amaçladığı bir başvuru olarak yerel olarak depolandığını belirtmek için, yerel bir değişken başvuruya göre başka bir değere erişir. Daha fazla bilgi için bkz. [ref Yereller](#ref-locals).
- Bir veya ' i `struct` bildirmek için bir bildirimde `ref struct` `readonly ref struct` . Daha fazla bilgi için [yapı türleri](../builtin-types/struct.md) makalesinin [ `ref` struct](../builtin-types/struct.md#ref-struct) bölümüne bakın.

## <a name="passing-an-argument-by-reference"></a>Bir bağımsız değişkeni başvuruya göre geçirme

Bir yöntemin parametre listesinde kullanıldığında, `ref` anahtar sözcüğü bir bağımsız değişkenin değere göre değil başvuruya göre geçtiğini gösterir. `ref`Anahtar sözcüğü, bir değişken olması gereken bağımsız değişken için biçimsel parametreye bir diğer ad getirir. Diğer bir deyişle, parametresindeki tüm işlemler bağımsız değişkende yapılır. Örneğin, çağıran bir yerel değişken ifadesi veya bir dizi öğesi erişim ifadesi geçirirse ve çağrılan yöntem Ref parametresinin başvurduğu nesnenin yerini alıyorsa, çağıran yerel değişkeni veya Array öğesi artık yöntem döndürüldüğünde yeni nesneye başvurur.

> [!NOTE]
> Başvuru türü kavramıyla başvuruya göre geçirme kavramını karıştırmayın. İki kavram aynı değildir. Bir yöntem parametresi `ref` , bir değer türü veya bir başvuru türü olmasına bakılmaksızın değiştirilebilir. Başvuru ile geçirildiğinde bir değer türünün kutulenmesi yoktur.  

Bir parametre kullanmak için `ref` , `ref` Aşağıdaki örnekte gösterildiği gibi yöntem tanımı ve çağırma yöntemi anahtar sözcüğünü açıkça kullanmalıdır.  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

Bir veya parametresine geçirilen bir bağımsız değişken `ref` `in` geçirilmeden önce başlatılmalıdır. Bu, bağımsız değişkenlerin geçirilmeden önce açıkça başlatılmış olması gereken [Out](out-parameter-modifier.md) parametrelerinden farklıdır.

Bir sınıfın üyelerinin yalnızca `ref` ,, veya ile farklı imzaları olamaz `in` `out` . Bir türün iki üyesi arasındaki tek fark, bir `ref` parametre içeriyorsa ve diğeri `out` veya parametresi varsa bir derleyici hatası oluşur `in` . Aşağıdaki kod, örneğin derlenmiyor.  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```

Ancak, bir yöntem bir `ref` , `in` veya `out` parametresi olduğunda ve diğeri bir değer parametresine sahip olduğunda, aşağıdaki örnekte gösterildiği gibi yöntemler aşırı yüklenebilir.
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 İmza eşleştirmesi gerektiren diğer durumlarda,,, ve,, ve ' ı gizleme veya geçersiz kılma,,, `in` `ref` ve birbirini `out` eşleştirmeyin.  
  
 Özellikler değişken değildir. Bunlar yöntemlerdir ve `ref` parametrelere geçirilemez.  
  
 `ref` `in` `out` Aşağıdaki tür yöntemler için, ve anahtar sözcüklerini kullanamazsınız:  
  
- Zaman [uyumsuz](async.md) değiştirici kullanarak tanımladığınız zaman uyumsuz yöntemler.  
- Bir [yield return](yield.md) veya bildiri içeren Yineleyici yöntemleri `yield break` .

Ayrıca, [genişletme yöntemleri](../../programming-guide/classes-and-structs/extension-methods.md) aşağıdaki kısıtlamalara sahiptir:

- `out`Anahtar sözcüğü, bir genişletme yönteminin ilk bağımsız değişkeninde kullanılamaz.
- `ref`Anahtar sözcüğü, bağımsız değişken bir struct olmadığında ya da genel bir tür struct olarak kısıtlanmamışsa Genişletme yönteminin ilk bağımsız değişkeninde kullanılamaz.
- `in`İlk bağımsız değişken bir struct olmadığı müddetçe anahtar sözcüğü kullanılamaz. `in`Anahtar sözcüğü, bir struct gibi sınırlandırsalar bile herhangi bir genel tür üzerinde kullanılamaz.

## <a name="passing-an-argument-by-reference-an-example"></a>Bir bağımsız değişkeni başvuruya göre geçirme: bir örnek

Önceki örneklerde değer türleri başvuruya göre geçer. Başvuru `ref` türlerini başvuruya göre geçirmek için anahtar sözcüğünü de kullanabilirsiniz. Başvuru türü başvuruya göre geçirilme yöntemi, çağrılan yöntemin, başvuru parametresinin çağırıcının başvurduğu nesneyi değiştirmesini sağlar. Nesnenin depolama konumu, başvuru parametresi değeri olarak yöntemine geçirilir. Parametresinin depolama konumundaki değeri değiştirirseniz (yeni bir nesneyi işaret etmek için), çağıranın başvurduğu depolama konumunu da değiştirirsiniz. Aşağıdaki örnek, bir başvuru türünün örneğini bir parametre olarak geçirir `ref` .
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

Başvuru türlerini değere ve başvuruya göre geçirme hakkında daha fazla bilgi için bkz. [başvuru türü parametrelerini geçirme](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).
  
## <a name="reference-return-values"></a>Başvuru dönüş değerleri

Başvuru dönüş değerleri (veya ref dönüşler), bir yöntemin çağırana başvuruya göre döndürdüğü değerlerdir. Diğer bir deyişle, çağıran bir yöntem tarafından döndürülen değeri değiştirebilir ve bu değişiklik çağırma yöntemindeki nesnenin durumunda yansıtılır.

Bir başvuru dönüş değeri `ref` anahtar sözcüğü kullanılarak tanımlanır:

- Metot imzasında. Örneğin, aşağıdaki yöntem imzası, `GetCurrentPrice` yöntemin başvuruya göre bir değer döndürdüğünü gösterir <xref:System.Decimal> .

```csharp
public ref decimal GetCurrentPrice()
```

- `return`Belirteç ve `return` yöntemin içindeki bir ifadede döndürülen değişken. Örneğin:

```csharp
return ref DecimalArray[0];
```

Çağıranın nesnenin durumunu değiştirmesi için, başvuru dönüş değeri açıkça bir [ref yerel](#ref-locals)olarak tanımlanmış bir değişkene depolanmalıdır.

Burada hem yöntem imzasını hem de Yöntem gövdesini gösteren daha kapsamlı bir başvuru dönüş örneği verilmiştir.

[!code-csharp[FindReturningRef](~/samples/snippets/csharp/new-in-7/MatrixSearch.cs#FindReturningRef "Find returning by reference")]

Çağrılan yöntem, `ref readonly` değeri başvuruya göre döndürmek için dönüş değerini de bildirebilir ve çağıran kodun döndürülen değeri değiştiremeyeceğini zorunlu kılabilir. Çağırma yöntemi, değeri yerel bir [ref salt okunur](#ref-readonly-locals) değişkeninde depolayarak döndürülen değerli değeri kopyalamayı önleyebilir.

Bir örnek için, bkz. [bir başvuru dönüşleri ve ref Yereller örneği](#a-ref-returns-and-ref-locals-example).

## <a name="ref-locals"></a>Başvuru yerelleri

Kullanılarak döndürülen değerlere başvurmak için bir başvuru yerel değişkeni kullanılır `return ref` . Bir ref yerel değişkeni, ref olmayan bir dönüş değeri olarak başlatılamaz. Diğer bir deyişle, başlatmanın sağ tarafı bir başvuru olmalıdır. Ref Local değerindeki tüm değişiklikler, metodu, yöntemi başvuruya göre döndürülen nesnenin durumuna yansıtılır.

`ref`Değişken bildiriminden önce anahtar sözcüğünü kullanarak bir ref yerel tanımlayın ve değeri başvuruya göre döndüren yönteme çağrıdan hemen önce.

Örneğin, aşağıdaki ifade adlı bir yöntem tarafından döndürülen bir başvuru yerel değeri tanımlar `GetEstimatedValue` :

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

Başvuruya göre bir değere aynı şekilde erişebilirsiniz. Bazı durumlarda, başvuruya göre değere erişmek, potansiyel olarak pahalı bir kopyalama işlemini önleyerek performansı artırır. Örneğin, aşağıdaki ifade bir değere başvurmak için kullanılan bir başvuru yerel değerini nasıl tanımlayacağınızı gösterir.

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

Her iki örnekte, `ref` anahtar sözcüğü her iki yerde de kullanılmalıdır veya derleyici hata CS8172 oluşturuyor, "bir değere sahip bir başvuru değişkeni başlatılamaz."

C# 7,3 ' den başlayarak, deyimin yineleme değişkeni `foreach` ref yerel veya ref ReadOnly yerel değişken olabilir. Daha fazla bilgi için [foreach ifadesi](foreach-in.md) makalesine bakın.

Ayrıca C# 7,3 ' den itibaren, ref [atama işleciyle](../operators/assignment-operator.md#ref-assignment-operator)bir ref yerel veya ref ReadOnly yerel değişkenini yeniden atayabilirsiniz.

## <a name="ref-readonly-locals"></a>Ref ReadOnly Yereller

Ref salt okunur yerel değeri, imzası ve kullanımları olan yöntem veya özellik tarafından döndürülen değerleri ifade etmek için kullanılır `ref readonly` `return ref` . `ref readonly`Değişken, yerel bir `ref` değişkenin özelliklerini bir değişkenle birleştirir `readonly` : Bu, atandığı depolamanın diğer adıdır ve değiştirilemez.

## <a name="a-ref-returns-and-ref-locals-example"></a>Bir ref, ve ref Yereller örneği döndürür

Aşağıdaki örnek `Book` , ve iki alanı olan bir sınıfı tanımlar <xref:System.String> `Title` `Author` . Ayrıca `BookCollection` , özel nesne dizisi içeren bir sınıfı tanımlar `Book` . Bağımsız kitap nesneleri, yöntemi çağırarak başvuruya göre döndürülür `GetBookByTitle` .

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

Çağıran, yöntem tarafından döndürülen değeri `GetBookByTitle` bir ref yerel olarak depoladığında, çağıranın dönüş değeri için yaptığı değişiklikler, `BookCollection` Aşağıdaki örnekte gösterildiği gibi nesnesine yansıtılır.

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli verimli kod yazma](../../write-safe-efficient-code.md)
- [Ref dönüşler ve ref yerel ayarlar](../../programming-guide/classes-and-structs/ref-returns.md)
- [Koşullu başvuru ifadesi](../operators/conditional-operator.md#conditional-ref-expression)
- [Parametreleri Geçirme](../../programming-guide/classes-and-structs/passing-parameters.md)
- [Yöntem Parametreleri](method-parameters.md)
- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# anahtar sözcükleri](index.md)
