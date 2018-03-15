---
title: "ref (C# Başvurusu)"
ms.date: 03/06/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 427045317e9d7d0fe3435a486b9f761908ab5e78
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2018
---
# <a name="ref-c-reference"></a>ref (C# Başvurusu)

`ref` Anahtar sözcüğü başvuruya göre geçirilen bir değer belirtir. Üç farklı bağlamlarda kullanılır: 

- Bir yöntem imzası ve bir yönteme başvuruya göre bağımsız değişken geçirmek için bir yöntem çağrısı. Bkz: [başvuruya göre bağımsız değişken geçirme](#passing-an-argument-by-reference) daha fazla bilgi için.

- Başvuruya göre çağırana bir değer döndürmek için bir yöntem imza ile. Bkz: [başvuru dönüş değerleri](#reference-return-values) daha fazla bilgi için.

- Bir başvuru dönüş değeri çağıran değiştirme amaçlayan bir başvuru olarak yerel olarak depolanan belirtmek için bir üye gövdesine. Bkz: [Ref Yereller](#ref-locals) daha fazla bilgi için.

## <a name="passing-an-argument-by-reference"></a>Başvuruya göre bağımsız değişken geçirme

Bir yöntemin parametre listesinde kullanıldığında `ref` anahtar sözcüğü gösterir bağımsız değişken değeri tarafından başvuruya göre geçirilir. Başvuruya göre geçirme çağrılan yöntemin değişkeninde herhangi bir değişiklik arama yönteminde yansıtılır etkisidir. Örneğin, yerel bir değişken ifadesi veya bir dizi öğesi erişim ifadesi çağıran geçerse ve çağrılan yöntemin hangi ref parametresi gösterir, ardından çağıran yerel nesnenin yerini değişken veya dizi öğesi artık yeni bir nesneye başvuruyor olduğunda yöntemi döndürür.

> [!NOTE]
>  Başvuru türleri kavramı ile başvuruya göre geçirme kavramı karıştırmayın. İki kavramları aynı değildir. Yöntem parametresi tarafından değiştirilebilir `ref` bir değer türü veya bir başvuru türü olmasından bağımsız olarak. Başvuruya göre geçirildiğinde hiçbir kutulama değer türü yok.  

Kullanılacak bir `ref` parametresi, yöntem tanımı ve arama yöntemi açıkça kullanmalıdır `ref` aşağıdaki örnekte gösterildiği gibi anahtar.  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

Geçirilen bağımsız değişken bir `ref` veya `in` parametresi, geçirilmeden önce başlatılmalıdır. Bu farklıdır [çıkışı](out-parameter-modifier.md) parametreleri olan bağımsız değişkenler bunlar geçirilmeden önce açıkça başlatılması gerekmez.

Sınıf üyeleri yalnızca farklı imzalar olamaz `ref`, `in`, veya `out`. Bir türün iki üyeleri arasındaki tek fark, biri olduğunda bunları sahip bir derleyici hatası oluşursa bir `ref` parametre ve diğer sahip bir `out`, veya `in` parametresi. Aşağıdaki kod, örneğin, derleme değil.  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
Bir yöntemi varsa ancak yöntemlerini aşırı yüklenebilir bir `ref`, `in`, veya `out` parametre ve diğer aşağıdaki örnekte gösterildiği gibi bir değer parametresine sahip.
  
[!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 İmza eşleştirme gizleme veya geçersiz kılma, gibi gerektiren diğer durumlarda `in`, `ref`, ve `out` imza parçası olan ve birbirlerine eşleşmiyor.  
  
 Özellikler değişkenleri değildir. Bunlar yöntemleri ve için geçirilemez `ref` parametreleri.  
  
 Diziler geçirmek hakkında daha fazla bilgi için bkz: [kullanarak dizileri geçirme ref ve çıkış](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).  
  
 Kullanamazsınız `ref`, `in`, ve `out` yöntemleri şu tür için anahtar sözcükleri:  
  
- Kullanarak tanımladığınız zaman uyumsuz yöntemleri [zaman uyumsuz](../../../csharp/language-reference/keywords/async.md) değiştiricisi.  
- Dahil yineleyici metotları bir [verim return](../../../csharp/language-reference/keywords/yield.md) veya `yield break` deyimi.  

## <a name="passing-an-argument-by-reference-an-example"></a>Başvuruya göre bağımsız değişken geçirme: örneği

Önceki örneklerde değer türleri başvuruya göre geçirin. Aynı zamanda `ref` başvuru geçirmek için anahtar sözcüğü türleri başvuruya göre. Bir başvuru türü başvuruya göre geçirme başvuru parametresi çağrı yapan başvurduğu nesneyi değiştirmek çağrılan yöntem sağlar. Nesne depolama konumunu yönteme başvurusu parametre değeri olarak geçirilir. Depolama konumu (yeni bir nesneye işaret edecek şekilde) parametresinin değeri değiştirirseniz, aynı zamanda çağıran başvurduğu depolama konumunu değiştirebilirsiniz. Aşağıdaki örnek başvuru türünde bir örneğini geçirmeden bir `ref` parametresi.   
  
[!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

Başvuru türleri değere ve başvuruya göre geçirme hakkında daha fazla bilgi için bkz: [başvuru türü parametreleri geçirme](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md).
  
## <a name="reference-return-values"></a>Başvuru dönüş değerleri

Başvuru dönüş değerleri (veya ref döndürür) çağırana başvuruya göre bir yöntem döndüren değerlerdir. Diğer bir deyişle, arayan bir yöntemi tarafından döndürülen değer değiştirebilirsiniz ve bu değişikliği yöntemi içeren nesneyi durumda yansıtılır. 

Bir başvuru dönüş değeri kullanılarak tanımlanmış `ref` anahtar sözcüğü:

- Yöntem imzası. Örneğin, aşağıdaki yöntemi imza inidicates, `GetCurrentPrice` yöntemi döndürür bir <xref:System.Decimal> başvuruya değeri.

   ```csharp
   public ref decimal GetCurrentValue()
   ``` 
- Arasında `return` belirteci ve döndürülen değişken bir `return` yöntemi deyiminde. Örneğin:
 
   ```csharp
   return ref DecimalArray[0];
   ``` 

Nesnenin durumu değiştirmek çağıran için sırayla başvuru dönüş değeri depolanan, olarak açıkça tanımlanmış bir değişken için bir [ref yerel](#ref-locals). 

Bir örnek için bkz: [bir başvuru döndürür ve ref Yereller örneği](#a-ref-returns-and-ref-locals-example)

## <a name="ref-locals"></a>Ref Yereller

Ref yerel değişken değerleri kullanarak döndürülen başvurmak için kullanılan `return ref`.  Ref yerel değişken başlatılmalı ve ref dönüş değerine atanmış. Değer yapılan tüm değişiklikler yerel ref, değeri olan yöntemi döndürülen nesnenin durumda başvuruya göre yansıtılır.

Kullanarak yerel bir ref tanımlayın `ref` değişken bildirimi önce yanı sıra hemen başvuruya göre değeri döndüren yöntemi çağırmadan önce anahtar sözcüğü. 

Örneğin, aşağıdaki deyim adlı bir yöntemi tarafından döndürülen ref yerel değerin tanımlar `GetEstimatedValue`:

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

Unutmayın `ref` anahtar sözcüğü her iki yerde de kullanılmalıdır ya da derleyici hatası "değerine sahip bir başvuru tarafından değişken başlatılamıyor." CS8172 oluşturur 
 
## <a name="a-ref-returns-and-ref-locals-example"></a>Bir başvuru döndürür ve ref Yereller örneği

Aşağıdaki örnek tanımlayan bir `Book` iki olan sınıfı <xref:System.String> alanları `Title` ve `Author`. Ayrıca tanımlayan bir `BookCollection` özel bir dizi içeren sınıf `Book` nesneleri. Tek tek defteri nesneleri çağırarak başvuruya göre döndürülür, `GetBookByTitle` yöntemi.

[!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

Ne zaman çağıran depolar tarafından döndürülen değer `GetBookByTitle` yöntemi ref yerel olarak çağıran dönüş değerini yaptığı değişiklikler yansıtılır `BookCollection` aşağıdaki örnekte gösterildiği gibi bir nesne.

[!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Parametreleri Geçirme](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)  
 [Yöntem Parametreleri](../../../csharp/language-reference/keywords/method-parameters.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)
