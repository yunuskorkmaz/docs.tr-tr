---
title: ref anahtar sözcüğü C# başvurusu
ms.date: 03/26/2019
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: 25c74317ce9033ef10735ee0087f275632b6bd17
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715180"
---
# <a name="ref-c-reference"></a>ref (C# Başvurusu)

`ref` anahtar sözcüğü, başvuruya göre geçirilen bir değeri gösterir. Dört farklı bağlamda kullanılır:

- Bir yöntem imzasında ve bir yöntem çağrısında, bir bağımsız değişkeni başvuruya göre bir yönteme geçirmek için. Daha fazla bilgi için bkz. [bir bağımsız değişkeni başvuruya göre geçirme](#passing-an-argument-by-reference).
- Bir yöntem imzasında, çağıran öğesine başvuruya göre bir değer döndürün. Daha fazla bilgi için bkz. [Başvuru dönüş değerleri](#reference-return-values).
- Bir üye gövdesinde, bir başvuru dönüş değerinin, çağıranın değiştirme amaçladığı bir başvuru olarak yerel olarak depolandığını belirtmek için, yerel bir değişken başvuruya göre başka bir değere erişir. Daha fazla bilgi için bkz. [ref Yereller](#ref-locals).
- Bir `struct` bildiriminde `ref struct` veya `readonly ref struct`bildirme. Daha fazla bilgi için bkz. [ref struct Types](#ref-struct-types).

## <a name="passing-an-argument-by-reference"></a>Bir bağımsız değişkeni başvuruya göre geçirme

Yöntemin parametre listesinde kullanıldığında, `ref` anahtar sözcüğü bir bağımsız değişkenin değere göre değil başvuruya göre geçtiğini gösterir. `ref` anahtar sözcüğü, bir değişken olması gereken bağımsız değişken için biçimsel parametreye bir diğer ad sağlar. Diğer bir deyişle, parametresindeki tüm işlemler bağımsız değişkende yapılır. Örneğin, çağıran bir yerel değişken ifadesi veya bir dizi öğesi erişim ifadesi geçirirse ve çağrılan yöntem Ref parametresinin başvurduğu nesnenin yerini alırsa, bu durumda çağıranın yerel değişkeni veya Array öğesi artık yeni nesnesine başvurur Yöntemi döndürür.

> [!NOTE]
> Başvuru türü kavramıyla başvuruya göre geçirme kavramını karıştırmayın. İki kavram aynı değildir. Bir yöntem parametresi, bir değer türü veya bir başvuru türü olmasına bakılmaksızın `ref` değiştirilebilir. Başvuru ile geçirildiğinde bir değer türünün kutulenmesi yoktur.  

Bir `ref` parametresi kullanmak için, aşağıdaki örnekte gösterildiği gibi yöntem tanımı ve çağırma yöntemi açık olarak `ref` anahtar sözcüğünü kullanmalıdır.  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

Bir `ref` veya `in` parametresine geçirilen bir bağımsız değişken geçirilmeden önce başlatılmalıdır. Bu, bağımsız değişkenlerin geçirilmeden önce açıkça başlatılmış olması gereken [Out](out-parameter-modifier.md) parametrelerinden farklıdır.

Bir sınıfın üyelerinin yalnızca `ref`, `in`veya `out`farklı imzaları olamaz. Bir türün iki üyesi arasındaki tek fark, bir `ref` parametresi ve diğeri ise `out`veya `in` parametresine sahipse bir derleyici hatası oluşur. Aşağıdaki kod, örneğin derlenmiyor.  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```

Ancak, bir yöntemin `ref`, `in`veya `out` parametresine sahip olduğu ve diğeri bir değer parametresi varsa, aşağıdaki örnekte gösterildiği gibi yöntemler aşırı yüklenebilir.
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 `in`, `ref`ve `out` gibi imza eşleştirmesi gerektiren diğer durumlarda, imzanın bir parçasıdır ve birbirleriyle eşleşmez.  
  
 Özellikler değişken değildir. Bunlar yöntemlerdir ve `ref` parametrelere geçirilemez.  
  
 Aşağıdaki tür yöntemler için `ref`, `in`ve `out` anahtar sözcüklerini kullanamazsınız:  
  
- Zaman [uyumsuz](async.md) değiştirici kullanarak tanımladığınız zaman uyumsuz yöntemler.  
- Bir [yield return](yield.md) veya `yield break` ifadesini içeren Yineleyici yöntemleri.  

## <a name="passing-an-argument-by-reference-an-example"></a>Bir bağımsız değişkeni başvuruya göre geçirme: bir örnek

Önceki örneklerde değer türleri başvuruya göre geçer. Başvuru türlerini başvuruya göre geçirmek için `ref` anahtar sözcüğünü de kullanabilirsiniz. Başvuru türü başvuruya göre geçirilme yöntemi, çağrılan yöntemin, başvuru parametresinin çağırıcının başvurduğu nesneyi değiştirmesini sağlar. Nesnenin depolama konumu, başvuru parametresi değeri olarak yöntemine geçirilir. Parametresinin depolama konumundaki değeri değiştirirseniz (yeni bir nesneyi işaret etmek için), çağıranın başvurduğu depolama konumunu da değiştirirsiniz. Aşağıdaki örnek, bir başvuru türünün örneğini `ref` parametresi olarak geçirir.
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

Başvuru türlerini değere ve başvuruya göre geçirme hakkında daha fazla bilgi için bkz. [başvuru türü parametrelerini geçirme](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).
  
## <a name="reference-return-values"></a>Başvuru dönüş değerleri

Başvuru dönüş değerleri (veya ref dönüşler), bir yöntemin çağırana başvuruya göre döndürdüğü değerlerdir. Diğer bir deyişle, çağıran bir yöntem tarafından döndürülen değeri değiştirebilir ve bu değişiklik yöntemi içeren nesnenin durumunda yansıtılır.

Başvuru dönüş değeri `ref` anahtar sözcüğü kullanılarak tanımlanır:

- Metot imzasında. Örneğin, aşağıdaki yöntem imzası `GetCurrentPrice` yönteminin başvuruya göre <xref:System.Decimal> değer döndürdüğünü gösterir.

```csharp
public ref decimal GetCurrentPrice()
```

- `return` belirteci ve yöntemi içindeki bir `return` ifadesinde döndürülen değişken arasında. Örneğin:

```csharp
return ref DecimalArray[0];
```

Çağıranın nesnenin durumunu değiştirmesi için, başvuru dönüş değeri açıkça bir [ref yerel](#ref-locals)olarak tanımlanmış bir değişkene depolanmalıdır.

Çağrılan yöntem aynı zamanda değeri başvuruya göre döndürmek için `ref readonly` olarak döndürülen değeri bildirebilir ve çağıran kodun döndürülen değeri değiştiremeyeceğini zorunlu kılabilir. Çağırma yöntemi, değeri yerel bir [ref salt okunur](#ref-readonly-locals) değişkeninde depolayarak döndürülen değerli değeri kopyalamayı önleyebilir.

Bir örnek için, bkz. [bir başvuru dönüşleri ve ref Yereller örneği](#a-ref-returns-and-ref-locals-example).

## <a name="ref-locals"></a>Başvuru yerelleri

`return ref`kullanılarak döndürülen değerlere başvurmak için bir ref yerel değişkeni kullanılır. Bir ref yerel değişkeni, ref olmayan bir dönüş değeri olarak başlatılamaz. Diğer bir deyişle, başlatmanın sağ tarafı bir başvuru olmalıdır. Ref Local değerindeki tüm değişiklikler, metodu, yöntemi başvuruya göre döndürülen nesnenin durumuna yansıtılır.

Değişken bildiriminden önce `ref` anahtar sözcüğünü kullanarak, ve değeri başvuruya göre döndüren yönteme çağrıdan hemen önce, bir ref yerel tanımlayın.

Örneğin, aşağıdaki ifade `GetEstimatedValue`adlı bir yöntem tarafından döndürülen bir ref yerel değeri tanımlar:

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

Başvuruya göre bir değere aynı şekilde erişebilirsiniz. Bazı durumlarda, başvuruya göre değere erişmek, potansiyel olarak pahalı bir kopyalama işlemini önleyerek performansı artırır. Örneğin, aşağıdaki ifade bir değere başvurmak için kullanılan bir başvuru yerel değerini nasıl tanımlayacağınızı gösterir.

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

Her iki örnekte de `ref` anahtar sözcüğünün her iki yerde de kullanılması gerektiğini veya derleyicinin hata CS8172, "bir değere sahip bir başvuruya göre değişkeni başlatamıyor" şeklinde olduğunu unutmayın.

7,3 ile C# başlayarak, `foreach` deyimin yineleme değişkeni ref yerel veya ref ReadOnly yerel değişken olabilir. Daha fazla bilgi için [foreach ifadesi](foreach-in.md) makalesine bakın.

## <a name="ref-readonly-locals"></a>Ref ReadOnly Yereller

Ref salt okunur yerel, yöntemi veya özelliği tarafından döndürülen değerlere, imzasında `ref readonly` olan ve `return ref`kullanan değerleri ifade etmek için kullanılır. `ref readonly` değişkeni, bir `ref` yerel değişkeninin özelliklerini `readonly` değişkeniyle birleştirir: Bu, atandığı depolamanın diğer adıdır ve değiştirilemez. 

## <a name="a-ref-returns-and-ref-locals-example"></a>Bir ref, ve ref Yereller örneği döndürür

Aşağıdaki örnek, `Title` ve `Author`iki <xref:System.String> alanı olan bir `Book` sınıfını tanımlar. Ayrıca, özel bir `Book` nesneleri dizisi içeren bir `BookCollection` sınıfını tanımlar. Tek kitap nesneleri, `GetBookByTitle` metodu çağırarak başvuruya göre döndürülür.

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

Çağıran `GetBookByTitle` yöntemi tarafından döndürülen değeri bir ref yerel olarak depoladığında, çağıranın dönüş değeri için yaptığı değişiklikler, aşağıdaki örnekte gösterildiği gibi `BookCollection` nesnesine yansıtılır.

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="ref-struct-types"></a>Ref struct türleri

`struct` bildirimine `ref` değiştiricisini eklemek, bu türdeki örneklerin yığın olarak ayrılmış olması gerektiğini tanımlar. Diğer bir deyişle, bu türlerin örnekleri başka bir sınıfın üyesi olarak yığın üzerinde hiçbir şekilde oluşturulamaz. Bu özellik için birincil mosyon <xref:System.Span%601> ve ilgili yapılarıdır.

Bir `ref struct` türünü yığın olarak ayrılmış bir değişken olarak tutmanın amacı, derleyicinin tüm `ref struct` türleri için uyguladığı çeşitli kuralları tanıtır.

- `ref struct`. `ref struct` türü `object`, `dynamic`veya herhangi bir arabirim türü değişkenine atayamazsınız.
- `ref struct` türleri arabirimler uygulayamaz.
- Bir `ref struct` bir sınıfın alan üyesi veya normal bir yapı olarak bildiremezsiniz. Bu, bir derleyici tarafından oluşturulan bir yedekleme alanı oluşturan otomatik uygulanan bir özellik bildirimi içerir. 
- Zaman uyumsuz yöntemlerde `ref struct` türler olan yerel değişkenler bildiremezsiniz. <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601> veya `Task`benzeri türler döndüren zaman uyumlu yöntemlerde bildirebilirsiniz.
- Yineleyiciler içinde `ref struct` yerel değişken bildiremezsiniz.
- Lambda ifadelerinde veya yerel işlevlerde `ref struct` değişkenlerini yakalayamazsınız.

Bu kısıtlamalar, yanlışlıkla `ref struct` yönetilen yığına yükseltebilen bir şekilde kullanmamasını sağlar.

Bir yapıyı `readonly ref`olarak bildirmek için değiştiriciler birleştirebilirsiniz. `readonly ref struct`, `ref struct` ve `readonly struct` bildirimlerinin avantajlarını ve kısıtlamalarını birleştirir.

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
