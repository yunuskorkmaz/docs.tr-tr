---
title: "ref (C# Başvurusu)"
ms.date: 05/30/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.assetid: b8a5e59c-907d-4065-b41d-95bf4273c0bd
caps.latest.revision: "32"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0be0eee67b507e2a209c9caaa3eb14cc60e8a763
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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

[!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-1.cs)]

Geçirilen bağımsız değişken bir `ref` parametresi, geçirilmeden önce başlatılmalıdır. Bu farklıdır [çıkışı](out.md) parametreleri olan bağımsız değişkenler bunlar geçirilmeden önce açıkça başlatılması gerekmez.

Sınıf üyeleri yalnızca farklı imzalar olamaz `ref` ve `out`. Bir türün iki üyeleri arasındaki tek fark, biri olduğunda bunları sahip bir derleyici hatası oluşursa bir `ref` parametre ve diğer sahip bir `out` parametresi. Aşağıdaki kod, örneğin, derleme değil.  
  
 [!code-csharp[csrefKeywordsMethodParams#2](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-2.cs)]
  
 Bir yöntemi varsa ancak yöntemlerini aşırı yüklenebilir bir `ref` veya `out` parametre ve diğer aşağıdaki örnekte gösterildiği gibi bir değer parametresine sahip.
  
 [!code-csharp[ref-and-overloads](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-3.cs)]
  
 İmza eşleştirme gizleme veya geçersiz kılma, gibi gerektiren diğer durumlarda `ref` ve `out` imza parçası olan ve birbirlerine eşleşmiyor.  
  
 Özellikler değişkenleri değildir. Bunlar yöntemleri ve için geçirilemez `ref` parametreleri.  
  
 Diziler geçirmek hakkında daha fazla bilgi için bkz: [kullanarak dizileri geçirme ref ve çıkış](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).  
  
 Kullanamazsınız `ref` ve `out` yöntemleri şu tür için anahtar sözcükleri:  
  
-   Kullanarak tanımladığınız zaman uyumsuz yöntemleri [zaman uyumsuz](../../../csharp/language-reference/keywords/async.md) değiştiricisi.  
  
-   Dahil yineleyici metotları bir [verim return](../../../csharp/language-reference/keywords/yield.md) veya `yield break` deyimi.  
  
## <a name="passing-an-argument-by-reference-an-example"></a>Başvuruya göre bağımsız değişken geçirme: örneği

Önceki örneklerde değer türleri başvuruya göre geçirin. Aynı zamanda `ref` başvuru geçirmek için anahtar sözcüğü türleri başvuruya göre. Bir başvuru türü başvuruya göre geçirme başvuru parametresi çağrı yapan başvurduğu nesneyi değiştirmek çağrılan yöntem sağlar. Nesne depolama konumunu yönteme başvurusu parametre değeri olarak geçirilir. Depolama konumu (yeni bir nesneye işaret edecek şekilde) parametresinin değeri değiştirirseniz, aynı zamanda çağıran başvurduğu depolama konumunu değiştirebilirsiniz. Aşağıdaki örnek başvuru türünde bir örneğini geçirmeden bir `ref` parametresi.   
  
 [!code-csharp[ReferencesByRef](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-4.cs)]  

Başvuru türleri değere ve başvuruya göre geçirme hakkında daha fazla bilgi için bkz: [başvuru türü parametreleri geçirme](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md).
  
## <a name="reference-return-values"></a>Başvuru dönüş değerleri

Başvuru dönüş değerleri (veya ref döndürür) çağırana başvuruya göre bir yöntem döndüren değerlerdir. Diğer bir deyişle, arayan bir yöntemi tarafından döndürülen değer değiştirebilirsiniz ve bu değişikliği yöntemi içeren nesneyi durumda yansıtılır. 

Bir başvuru dönüş değeri kullanılarak tanımlanmış `ref` anahtar sözcüğü:

- Yöntem imzası. Örneğin, aşağıdaki yöntemi imza inidicates, `GetCurrentPrice` yöntemi döndürür bir <xref:System.Decimal> başvuruya değeri.

   ```csharp
   public ref decimal GetCurrentValue()
   ``` 
- Her önce `return` yöntemi deyiminde. Örneğin:
 
   ```csharp
   ref return Decimal.Zero;
   ``` 

Nesnenin durumu değiştirmek çağıran için sırayla başvuru dönüş değeri depolanan, olarak açıkça tanımlanmış bir değişken için bir [ref yerel](#ref-locals). 

Bir örnek için bkz: [bir başvuru döndürür ve ref Yereller örneği](#a-ref-returns-and-ref-locals-example)

## <a name="ref-locals"></a>Ref Yereller

Ref yerel değişken değerleri kullanarak döndürülen başvurmak için kullanılan `ref return`.  Ref yerel değişken başlatılmalı ve ref dönüş değerine atanmış. Değer yapılan tüm değişiklikler yerel ref, değeri olan yöntemi döndürülen nesnenin durumda başvuruya göre yansıtılır.

Kullanarak yerel bir ref tanımlayın `ref` değişken bildirimi önce yanı sıra hemen başvuruya göre değeri döndüren yöntemi çağırmadan önce anahtar sözcüğü. 

Örneğin, aşağıdaki deyim adlı bir yöntemi tarafından döndürülen ref yerel değerin tanımlar `GetEstimatedValue`:

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

Unutmayın `ref` anahtar sözcüğü her iki yerde de kullanılmalıdır ya da derleyici hatası "değerine sahip bir başvuru tarafından değişken başlatılamıyor." CS8172 oluşturur 
 
## <a name="a-ref-returns-and-ref-locals-example"></a>Bir başvuru döndürür ve ref Yereller örneği

Aşağıdaki örnek tanımlayan bir `Book` iki olan sınıfı <xref:System.String> alanları `Title` ve `Author`. Ayrıca tanımlayan bir `BookCollection` özel bir dizi içeren sınıf `Book` nesneleri. Tek tek defteri nesneleri çağırarak başvuruya göre döndürülür, `GetBookByTitle` yöntemi.

[!code-csharp[csrefreturns](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-5.cs#1)]  

Ne zaman çağıran depolar tarafından döndürülen değer `GetBookByTitle` yöntemi ref yerel olarak çağıran dönüş değerini yaptığı değişiklikler yansıtılır `BookCollection` aşağıdaki örnekte gösterildiği gibi bir nesne.

[!code-csharp[csrefreturns](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-5.cs#2)]  

## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Parametreleri geçirme](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)  
 [Yöntem parametreleri](../../../csharp/language-reference/keywords/method-parameters.md)  
 [C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md)
