---
title: ref anahtar sözcüğü (C# Başvurusu)
ms.date: 03/06/2018
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: e0b82de125246e95d8dce2a7afc20119a8a1fe4f
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48583119"
---
# <a name="ref-c-reference"></a>ref (C# Başvurusu)

`ref` Anahtar sözcüğü, başvuru tarafından geçirilmediğine bir değer belirtir. Bu dört farklı bağlamda kullanılır:

- Bir yöntem imzası ve bağımsız değişken başvuru ile bir yönteme geçirmek için bir yöntem çağrısı. Bkz: [başvuruya göre bağımsız değişken geçirme](#passing-an-argument-by-reference) daha fazla bilgi için.
- Başvuruya göre çağırana bir değer döndürmek için bir yöntem imzasında. Bkz: [başvuru dönüş değerleri](#reference-return-values) daha fazla bilgi için.
- Bir üye gövdesinde çağıran değiştirme amaçlayan bir başvuru olarak yerel veya genel olarak, bir başvuru dönüş değeri depolanır belirtmek için bir yerel değişkeni başka bir değer başvuruya göre erişir. Bkz: [Ref yerel ayarlar](#ref-locals) daha fazla bilgi için.
- İçinde bir `struct` bildirmek için bildirimi bir `ref struct` veya `ref readonly struct`. Daha fazla bilgi için [başvuru semantiği ile değer türleri](../../reference-semantics-with-value-types.md).

## <a name="passing-an-argument-by-reference"></a>Başvuruya göre bağımsız değişken geçirme

Bir yöntemin parametre listesinde kullanıldığında `ref` anahtar sözcüğü gösterir bir bağımsız değişken başvuruya göre değil değere göre geçirilir. Başvuruya göre geçirme çağrılan yöntem değişkeninde herhangi bir değişiklik çağıran yöntemin yansıtılır etkisidir. Örneğin, çağıran bir yerel değişken ifade veya bir dizi öğe erişimi ifadesi geçerse ve çağrılan yöntemin hangi ref parametresi başvuruyor, sonra çağıran yerel nesne değiştirir değişkeni ya da dizi öğesini şimdi yeni nesneye başvuran olduğunda yöntemi döndürür.

> [!NOTE]
> Başvuru türlerinin kavramıyla başvuruya göre geçirme kavramını karıştırmayın. İki konsepti aynı değildir. Bir yöntem parametresi tarafından değiştirilebilir `ref` bir değer türü veya bir başvuru türü olmasına bakılmaksızın. Başvuruya göre geçildiğinde bir değer türünün hiçbir kutulama yoktur.  

Kullanılacak bir `ref` parametresi, yöntem tanımının hem yöntemi çağrılırken açıkça kullanmalıdır `ref` anahtar sözcüğü, aşağıdaki örnekte gösterildiği gibi.  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

Geçirilen bir bağımsız değişken bir `ref` veya `in` bunu geçirilmeden önce parametresi'nin başlatılması gerekir. Bu farklıdır [kullanıma](out-parameter-modifier.md) parametreleri, bağımsız değişkenleri geçirilen önce açıkça başlatılması gerekmez.

Bir sınıfın üyelerinin, yalnızca farklı imzaları olamaz `ref`, `in`, veya `out`. İki bir türün üyeleri arasındaki tek fark, birinin ise bunları sahip bir derleyici hatası oluşur. bir `ref` parametresi ve diğer bir `out`, veya `in` parametresi. Örneğin, aşağıdaki kod, derleme değil.  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```

Bir yöntem olduğunda ancak yöntemler aşırı yüklenebilir bir `ref`, `in`, veya `out` parametresi ve diğer aşağıdaki örnekte gösterildiği gibi bir değer parametresi vardır.
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 Gizleme veya geçersiz kılma, gibi imza eşleştirme gerektiren diğer durumlarda `in`, `ref`, ve `out` imzasının bir parçası olan ve birbiriyle uyuşmuyor.  
  
 Özellikler değişkenleri değildir. Yöntemler ve için geçirilemez `ref` parametreleri.  
  
 Kullanamazsınız `ref`, `in`, ve `out` yöntemleri aşağıdaki türde için anahtar sözcükler:  
  
- Kullanarak tanımladığınız zaman uyumsuz yöntemlerde [zaman uyumsuz](async.md) değiştiricisi.  
- Yineleyici yöntemleri dahil bir [yield return](yield.md) veya `yield break` deyimi.  

## <a name="passing-an-argument-by-reference-an-example"></a>Başvuruya göre bağımsız değişken geçirme: örneği

Önceki örneklerde, değer türleri başvuruya göre geçirin. Ayrıca `ref` başvuru geçirilecek anahtar sözcüğü türleri başvuruya göre. Bir başvuru türü başvuruya göre geçirme başvuru parametresi arayanda başvurduğu nesneyi değiştirmek çağrılan yöntem sağlar. Nesne depolama konumu yönteme başvuru parametresi değeri olarak geçirilir. Depolama konumu (yeni bir nesneye işaret edecek şekilde) parametresinin değeri değiştirirseniz, ayrıca çağıran başvurduğu depolama konumunu değiştirin. Aşağıdaki örnek bir başvuru türünün örneğini geçirir bir `ref` parametresi.
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

Başvuru türleri değere ve başvuruya göre geçirme hakkında daha fazla bilgi için bkz: [başvuru türü parametreleri geçirme](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).
  
## <a name="reference-return-values"></a>Başvuru dönüş değerleri

Başvuru dönüş değerleri (veya ref döndürür) başvuru arayana döner değerlerdir. Diğer bir deyişle, arayan bir yöntemi tarafından döndürülen değer değiştirebilirsiniz ve bu değişiklik yöntemi içeren nesneyi durumda yansıtılır.

Başvuru dönüş değeri kullanılarak tanımlanmış `ref` anahtar sözcüğü:

- Yöntem imzasında. Örneğin, aşağıdaki yöntem imzasını belirten `GetCurrentPrice` yöntemi döndürür bir <xref:System.Decimal> başvuruya göre değeri.

```csharp
public ref decimal GetCurrentPrice()
```

- Arasında `return` belirtecini ve döndürülen değişkeni bir `return` deyiminde yöntemi. Örneğin:

```csharp
return ref DecimalArray[0];
```

Nesnenin durumunu değiştirmek arayan için sırada başvuru dönüş değeri depolanan, olarak açıkça tanımlanmış bir değişkene bir [ref yerel](#ref-locals).

Bir örnek için bkz [A ref dönüşler ve ref yerel örneği](#a-ref-returns-and-ref-locals-example)

## <a name="ref-locals"></a>Ref yerel ayarlar

Bir ref yerel değişken başvuru ile döndürülen değerleri için kullanılan `return ref`. Bir ref yerel değişken başvuru olmayan dönüş değeri için başlatılamıyor. Diğer bir deyişle, sağ taraftaki başlatma bir başvuru olmalıdır. Yerel başvurunun değeri herhangi bir değişiklik durumunda, yöntem döndürülen değer nesnesinin başvuruya göre yansıtılır.

Bir ref yerel kullanarak tanımladığınız `ref` anahtar sözcüğü Değişken bildiriminde önce yanı sıra hemen önce başvuruya göre değeri döndüren yöntem çağrısı.

Örneğin, aşağıdaki deyim adlı bir yöntem tarafından döndürülen bir ref yerel değer tanımlar `GetEstimatedValue`:

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

Başvuruya göre bir değer aynı şekilde erişebilirsiniz. Bazı durumlarda, bir değere Başvuruya göre erişmeden performansı büyük olasılıkla pahalı kopyalama işlemi tarafından artırır. Örneğin, aşağıdaki ifade bir değer başvurmak için kullanılan bir ref yerel değer nasıl tanımlayabilirsiniz gösterir.

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

Her iki örneklerde unutmayın `ref` anahtar sözcüğü her iki yerde de kullanılması gerekir ya da derleyici hata CS8172, "bir başvuruya göre değişken bir değer ile başlatılamaz." oluşturur

## <a name="a-ref-returns-and-ref-locals-example"></a>Bir ref dönüşler ve ref yerel örneği

Aşağıdaki örnekte tanımlayan bir `Book` iki sınıf <xref:System.String> alanları `Title` ve `Author`. Ayrıca tanımlar bir `BookCollection` özel bir dizi içeren sınıf `Book` nesneleri. Tek tek kitap nesneleri çağırarak başvuru ile döndürülür kendi `GetBookByTitle` yöntemi.

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

Çağıran tarafından döndürülen değeri, zaman depolar `GetBookByTitle` yöntemi bir ref yerel olarak çağırana döndürülen değeri yaptığı değişiklikler yansıtılır `BookCollection` aşağıdaki örnekte gösterildiği gibi bir nesne.

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Değer türleri ile başvuru semantiği](../../reference-semantics-with-value-types.md)  
- [Parametreleri Geçirme](../../programming-guide/classes-and-structs/passing-parameters.md)  
- [Yöntem Parametreleri](method-parameters.md)  
- [C# başvurusu](../index.md)  
- [C# Programlama Kılavuzu](../../programming-guide/index.md)  
- [C# Anahtar Sözcükleri](index.md)