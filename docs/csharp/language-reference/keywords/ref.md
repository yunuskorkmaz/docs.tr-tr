---
title: ref anahtar sözcüğü C# başvurusu
ms.custom: seodec18
ms.date: 03/26/2019
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: f11137b3c13bb9e8670c4df25fedf3251724a088
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566891"
---
# <a name="ref-c-reference"></a>ref (C# Başvurusu)

Anahtar `ref` sözcüğü, başvuruya göre geçirilen bir değeri gösterir. Dört farklı bağlamda kullanılır:

- Bir yöntem imzasında ve bir yöntem çağrısında, bir bağımsız değişkeni başvuruya göre bir yönteme geçirmek için. Daha fazla bilgi için bkz. [bir bağımsız değişkeni başvuruya göre geçirme](#passing-an-argument-by-reference).
- Bir yöntem imzasında, çağıran öğesine başvuruya göre bir değer döndürün. Daha fazla bilgi için bkz. [Başvuru dönüş değerleri](#reference-return-values).
- Bir üye gövdesinde, bir başvuru dönüş değerinin, çağıranın değiştirme amaçladığı bir başvuru olarak yerel olarak depolandığını belirtmek için, yerel bir değişken başvuruya göre başka bir değere erişir. Daha fazla bilgi için bkz. [ref Yereller](#ref-locals).
- Bir veya ' i `struct` `ref struct` bildirmek için bir bildirimde. `readonly ref struct` Daha fazla bilgi için bkz. [ref struct Types](#ref-struct-types).

## <a name="passing-an-argument-by-reference"></a>Bir bağımsız değişkeni başvuruya göre geçirme

Bir yöntemin parametre listesinde kullanıldığında, `ref` anahtar sözcüğü bir bağımsız değişkenin değere göre değil başvuruya göre geçtiğini gösterir. `ref` Anahtar sözcüğü, bir değişken olması gereken bağımsız değişken için biçimsel parametreye bir diğer ad getirir. Diğer bir deyişle, parametresindeki tüm işlemler bağımsız değişkende yapılır. Örneğin, çağıran bir yerel değişken ifadesi veya bir dizi öğesi erişim ifadesi geçirirse ve çağrılan yöntem Ref parametresinin başvurduğu nesnenin yerini alırsa, bu durumda çağıranın yerel değişkeni veya Array öğesi artık yeni nesnesine başvurur Yöntemi döndürür.

> [!NOTE]
> Başvuru türü kavramıyla başvuruya göre geçirme kavramını karıştırmayın. İki kavram aynı değildir. Bir yöntem parametresi, bir değer türü `ref` veya bir başvuru türü olmasına bakılmaksızın değiştirilebilir. Başvuru ile geçirildiğinde bir değer türünün kutulenmesi yoktur.  

Bir `ref` parametre kullanmak için, aşağıdaki örnekte gösterildiği gibi yöntem tanımı ve çağırma yöntemi `ref` anahtar sözcüğünü açıkça kullanmalıdır.  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

Bir `ref` veya`in` parametresine geçirilen bir bağımsız değişken geçirilmeden önce başlatılmalıdır. Bu, bağımsız değişkenlerin geçirilmeden önce açıkça başlatılmış olması gereken [Out](out-parameter-modifier.md) parametrelerinden farklıdır.

Bir sınıfın üyelerinin yalnızca, `ref` `in`, veya `out`ile farklı imzaları olamaz. Bir türün `ref` iki üyesi arasındaki tek fark, bir parametre içeriyorsa ve diğeri `out`veya `in` parametresi varsa bir derleyici hatası oluşur. Aşağıdaki kod, örneğin derlenmiyor.  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```

Ancak, bir yöntem bir `ref`, `in`veya `out` parametresi olduğunda ve diğeri bir değer parametresine sahip olduğunda, aşağıdaki örnekte gösterildiği gibi yöntemler aşırı yüklenebilir.
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 İmza eşleştirmesi gerektiren diğer durumlarda,,, ve,, ve ' ı `in`gizleme `ref`veya geçersiz `out` kılma,,, ve birbirini eşleştirmeyin.  
  
 Özellikler değişken değildir. Bunlar yöntemlerdir ve `ref` parametrelere geçirilemez.  
  
 Aşağıdaki tür yöntemler için `ref`, `in`ve `out` anahtar sözcüklerini kullanamazsınız:  
  
- Zaman [uyumsuz](async.md) değiştirici kullanarak tanımladığınız zaman uyumsuz yöntemler.  
- Bir [yield return](yield.md) veya `yield break` bildiri içeren Yineleyici yöntemleri.  

## <a name="passing-an-argument-by-reference-an-example"></a>Bir bağımsız değişkeni başvuruya göre geçirme: Örnek

Önceki örneklerde değer türleri başvuruya göre geçer. Başvuru türlerini başvuruya göre geçirmek `ref` için anahtar sözcüğünü de kullanabilirsiniz. Başvuru türü başvuruya göre geçirilme yöntemi, çağrılan yöntemin, başvuru parametresinin çağırıcının başvurduğu nesneyi değiştirmesini sağlar. Nesnenin depolama konumu, başvuru parametresi değeri olarak yöntemine geçirilir. Parametresinin depolama konumundaki değeri değiştirirseniz (yeni bir nesneyi işaret etmek için), çağıranın başvurduğu depolama konumunu da değiştirirsiniz. Aşağıdaki örnek, bir başvuru türünün örneğini bir `ref` parametre olarak geçirir.
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

Başvuru türlerini değere ve başvuruya göre geçirme hakkında daha fazla bilgi için bkz. [başvuru türü parametrelerini geçirme](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).
  
## <a name="reference-return-values"></a>Başvuru dönüş değerleri

Başvuru dönüş değerleri (veya ref dönüşler), bir yöntemin çağırana başvuruya göre döndürdüğü değerlerdir. Diğer bir deyişle, çağıran bir yöntem tarafından döndürülen değeri değiştirebilir ve bu değişiklik yöntemi içeren nesnenin durumunda yansıtılır.

Bir başvuru dönüş değeri `ref` anahtar sözcüğü kullanılarak tanımlanır:

- Metot imzasında. Örneğin, aşağıdaki yöntem imzası, `GetCurrentPrice` yöntemin başvuruya göre bir <xref:System.Decimal> değer döndürdüğünü gösterir.

```csharp
public ref decimal GetCurrentPrice()
```

- Belirteç ve yöntemin içindeki bir `return` ifadede döndürülen değişken. `return` Örneğin:

```csharp
return ref DecimalArray[0];
```

Çağıranın nesnenin durumunu değiştirmesi için, başvuru dönüş değeri açıkça bir [ref yerel](#ref-locals)olarak tanımlanmış bir değişkene depolanmalıdır.

Çağrılan yöntem, değeri başvuruya göre döndürmek `ref readonly` için dönüş değerini de bildirebilir ve çağıran kodun döndürülen değeri değiştiremeyeceğini zorunlu kılabilir. Çağırma yöntemi, değeri yerel bir [ref salt okunur](#ref-readonly-locals) değişkeninde depolayarak döndürülen değerli değeri kopyalamayı önleyebilir.

Bir örnek için, bkz. [bir başvuru dönüşleri ve ref Yereller örneği](#a-ref-returns-and-ref-locals-example).

## <a name="ref-locals"></a>Başvuru yerelleri

Kullanılarak `return ref`döndürülen değerlere başvurmak için bir başvuru yerel değişkeni kullanılır. Bir ref yerel değişkeni, ref olmayan bir dönüş değeri olarak başlatılamaz. Diğer bir deyişle, başlatmanın sağ tarafı bir başvuru olmalıdır. Ref Local değerindeki tüm değişiklikler, metodu, yöntemi başvuruya göre döndürülen nesnenin durumuna yansıtılır.

Değişken bildiriminden önce `ref` anahtar sözcüğünü kullanarak bir ref yerel tanımlayın ve değeri başvuruya göre döndüren yönteme çağrıdan hemen önce.

Örneğin, aşağıdaki ifade adlı `GetEstimatedValue`bir yöntem tarafından döndürülen bir başvuru yerel değeri tanımlar:

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

Başvuruya göre bir değere aynı şekilde erişebilirsiniz. Bazı durumlarda, başvuruya göre değere erişmek, potansiyel olarak pahalı bir kopyalama işlemini önleyerek performansı artırır. Örneğin, aşağıdaki ifade bir değere başvurmak için kullanılan bir başvuru yerel değerini nasıl tanımlayacağınızı gösterir.

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

Her iki örnekte `ref` anahtar sözcüğünün her iki yerde de kullanılması gerektiğini veya derleyicinin hata CS8172 hata yaratmadığını, "bir değere sahip bir başvuru değişkeni başlatamıyor."

7,3 ile C# başlayarak, `foreach` deyimin yineleme değişkeni ref yerel veya ref ReadOnly yerel değişken olabilir. Daha fazla bilgi için [foreach ifadesi](foreach-in.md) makalesine bakın.

## <a name="ref-readonly-locals"></a>Ref ReadOnly Yereller

Ref salt okunur yerel değeri, imzası ve kullanımları `ref readonly` `return ref`olan yöntem veya özellik tarafından döndürülen değerleri ifade etmek için kullanılır. Değişken, `ref` yerel bir değişkenin özelliklerini bir `readonly` değişkenle birleştirir: Bu, atandığı depolamanın diğer adıdır ve değiştirilemez. `ref readonly` 

## <a name="a-ref-returns-and-ref-locals-example"></a>Bir ref, ve ref Yereller örneği döndürür

Aşağıdaki `Book` örnek, <xref:System.String> `Title` ve ikialanıolanbirsınıfıtanımlar.`Author` Ayrıca, `BookCollection` `Book` özel nesne dizisi içeren bir sınıfı tanımlar. Bağımsız kitap nesneleri, `GetBookByTitle` yöntemi çağırarak başvuruya göre döndürülür.

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

Çağıran, `GetBookByTitle` yöntem tarafından döndürülen değeri bir ref yerel olarak depoladığında, çağıranın dönüş değeri için yaptığı değişiklikler, aşağıdaki örnekte gösterildiği gibi `BookCollection` nesnesine yansıtılır.

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="ref-struct-types"></a>Ref struct türleri

`ref` Bir`struct` bildirime değiştiricisini eklemek, bu türdeki örneklerin yığın olarak ayrılmış olması gerektiğini tanımlar. Diğer bir deyişle, bu türlerin örnekleri başka bir sınıfın üyesi olarak yığın üzerinde hiçbir şekilde oluşturulamaz. Bu özellik <xref:System.Span%601> için birincil mosyon ve ilgili yapılar.

Bir `ref struct` türü yığın olarak ayrılmış bir değişken olarak tutmanın hedefi, derleyicinin tüm `ref struct` türler için uyguladığı çeşitli kurallar sunar.

- Bir `ref struct`kutusu ekleyemezsiniz. Türü `ref struct` `object`, veya`dynamic`herhangi bir arabirim türü değişkenine bir tür atayamazsınız.
- `ref struct`türler arabirimleri uygulayamaz.
- Bir `ref struct` sınıfın alan üyesi olarak veya normal bir yapının bildirimini yapamazsınız. Bu, bir derleyici tarafından oluşturulan bir yedekleme alanı oluşturan otomatik uygulanan bir özellik bildirimi içerir. 
- Zaman uyumsuz metotlarda `ref struct` türler olan yerel değişkenler bildiremezsiniz. Bunları, <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> veya benzeritürlerdöndürenzamanuyumluyöntemlerlebildirebilirsiniz.`Task`
- Yineleyiciler içinde `ref struct` yerel değişkenler bildiremezsiniz.
- Lambda ifadelerinde veya `ref struct` yerel işlevlerde değişkenleri yakalayamazsınız.

Bu kısıtlamalar, yanlışlıkla bir `ref struct` ' i yönetilen yığına yükseltebilen bir şekilde kullanmamasını sağlar.

Bir yapıyı olarak `readonly ref`tanımlamak için değiştiriciler birleştirebilirsiniz. , `readonly ref struct` `ref struct` Ve bildirimlerinin`readonly struct` avantajlarını ve kısıtlamalarını birleştirir.

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli verimli kod yazma](../../write-safe-efficient-code.md)
- [Ref dönüşler ve ref yerel ayarlar](../../programming-guide/classes-and-structs/ref-returns.md)
- [Koşullu başvuru ifadesi](../operators/conditional-operator.md#conditional-ref-expression)
- [ref atama işleci](../operators/assignment-operator.md#ref-assignment-operator)
- [Parametreleri Geçirme](../../programming-guide/classes-and-structs/passing-parameters.md)
- [Yöntem Parametreleri](method-parameters.md)
- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
