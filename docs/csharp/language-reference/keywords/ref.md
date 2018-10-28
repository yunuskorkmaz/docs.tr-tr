---
title: ref anahtar sözcüğü (C# Başvurusu)
ms.date: 10/24/2018
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: 9165a388122eeda5ca0499c6d75c2266780a6004
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50195976"
---
# <a name="ref-c-reference"></a>ref (C# Başvurusu)

`ref` Anahtar sözcüğü, başvuru tarafından geçirilmediğine bir değer belirtir. Bu dört farklı bağlamda kullanılır:

- Bir yöntem imzası ve bağımsız değişken başvuru ile bir yönteme geçirmek için bir yöntem çağrısı. Daha fazla bilgi için [başvuruya göre bağımsız değişken geçirme](#passing-an-argument-by-reference).
- Başvuruya göre çağırana bir değer döndürmek için bir yöntem imzasında. Daha fazla bilgi için [başvuru dönüş değerleri](#reference-return-values).
- Bir üye gövdesinde çağıran değiştirme amaçlayan bir başvuru olarak yerel veya genel olarak, bir başvuru dönüş değeri depolanır belirtmek için bir yerel değişkeni başka bir değer başvuruya göre erişir. Daha fazla bilgi için [Ref yerel ayarlar](#ref-locals).
- İçinde bir `struct` bildirmek için bildirimi bir `ref struct` veya `ref readonly struct`. Daha fazla bilgi için [ref struct türlerini](#ref-struct-types).


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

Çağrılan yöntemin dönüş değeri olarak da bildirebilir `ref readonly` başvuruya göre dönüş değeri ve zorunlu çağıran kod döndürülen değeri değiştirilemez. Döndürülen değer yerel depolayarak değerli kopyalama yöntemi çağrılırken kaçınabilirsiniz [ref salt okunur](#ref-readonly-locals) değişkeni.

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

## <a name="ref-readonly-locals"></a>ref salt okunur yerel öğeler

Yerel başvuru salt okunur olan özelliği ve yöntemi tarafından döndürülen değerler başvurmak için kullanılan `ref readonly` kullanır ve imza `return ref`. A `ref readonly` değişkeni özelliklerini birleştiren bir `ref` yerel bir değişken bir `readonly` değişkeni: bir diğer addır depolama alanına atanır ve değiştirilemez. 

## <a name="a-ref-returns-and-ref-locals-example"></a>Bir ref dönüşler ve ref yerel örneği

Aşağıdaki örnekte tanımlayan bir `Book` iki sınıf <xref:System.String> alanları `Title` ve `Author`. Ayrıca tanımlar bir `BookCollection` özel bir dizi içeren sınıf `Book` nesneleri. Tek tek kitap nesneleri çağırarak başvuru ile döndürülür kendi `GetBookByTitle` yöntemi.

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

Çağıran tarafından döndürülen değeri, zaman depolar `GetBookByTitle` yöntemi bir ref yerel olarak çağırana döndürülen değeri yaptığı değişiklikler yansıtılır `BookCollection` aşağıdaki örnekte gösterildiği gibi bir nesne.

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="ref-struct-types"></a>Ref struct türleri

Ekleme `ref` değiştiriciyi bir `struct` bildirimi tanımlar, türün örneklerinin yığını ayrılan olmalıdır. Diğer bir deyişle, bu tür örnekleri hiçbir zaman yığın üzerinde başka bir sınıf üyesi olarak oluşturulabilir. Bu özellik için birincil motivasyon olan <xref:System.Span%601> ve ilişkili yapıları.

Amacı tutarken, bir `ref struct` yazın, tüm derleyici zorlayan çeşitli kurallar bir yığın ayırma değişken tanıtan `ref struct` türleri.

- Kutusunda edilemez bir `ref struct`. Atama yapılamaz bir `ref struct` türünde bir değişkene `object`, `dynamic`, veya herhangi bir arabirim türü.
- `ref struct` türleri, arabirimleri uygulayamaz.
- Bildirip bir `ref struct` bir sınıf veya normal yapı üyesi olarak.
- Yerel değişkenler bildiremezsiniz `ref struct` zaman uyumsuz yöntemlerde türleri. Döndüren zaman uyumlu yöntemleri bildirebilirsiniz <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601> veya `Task`-türleri ister.
- Bildirip `ref struct` yineleyiciler yerel değişkenler.
- Yakalama gerçekleştiremez `ref struct` değişkenleri lambda ifadeleri veya yerel işlevler.

Bu kısıtlamalar yanlışlıkla kullanmayın emin olun. bir `ref struct` bir şekilde yönetilen yığınla Yükselt.

Bir yapı olarak bildirmek için değiştiriciler birleştirebilirsiniz `readonly ref`. A `readonly ref struct` avantajları ve kısıtlamaları birleştirir `ref struct` ve `readonly struct` bildirimleri.

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli verimli kod yazma](../../write-safe-efficient-code.md)  
- [Parametreleri Geçirme](../../programming-guide/classes-and-structs/passing-parameters.md)  
- [Yöntem Parametreleri](method-parameters.md)  
- [C# başvurusu](../index.md)  
- [C# Programlama Kılavuzu](../../programming-guide/index.md)  
- [C# Anahtar Sözcükleri](index.md)
