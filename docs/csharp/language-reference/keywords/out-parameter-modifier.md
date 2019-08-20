---
title: out parametre değiştiricisi- C# başvuru
ms.custom: seodec18
ms.date: 03/26/2019
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.openlocfilehash: 81d60782cf8e16d55889fb3c7c05858070a97741
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602068"
---
# <a name="out-parameter-modifier-c-reference"></a>out parametresi değiştiricisi (C# Başvurusu)
Anahtar `out` sözcüğü, bağımsız değişkenlerin başvuruya göre geçirilmesine neden olur. Bir değişken olması gereken, biçimsel parametreye bağımsız değişken için bir diğer ad oluşturur. Diğer bir deyişle, parametresindeki tüm işlemler bağımsız değişkende yapılır. [Ref](ref.md) anahtar sözcüğüne benzer, ancak bu `ref` , değişkeninin geçirilmeden önce başlatılması gerekir. Aynı zamanda [ın](in-parameter-modifier.md) anahtar sözcüğüne benzer, ancak `in` çağrılan yöntemin bağımsız değişken değerini değiştirmesine izin vermez. Bir `out` parametre kullanmak için, hem yöntem tanımı hem de çağıran yöntemi, `out` anahtar sözcüğünü açıkça kullanmalıdır. Örneğin:  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE] 
> `out` Anahtar sözcüğü, tür parametresinin covaryant olduğunu belirtmek için genel bir tür parametresiyle de kullanılabilir. `out` Anahtar sözcüğünün bu bağlamda kullanımı hakkında daha fazla bilgi için bkz. [Out (genel değiştirici)](out-generic-modifier.md).
  
Bağımsız değişken olarak `out` geçirilen değişkenlerin, yöntem çağrısında geçirilmeden önce başlatılması gerekmez. Ancak, yöntemi döndürmadan önce bir değer atamak için çağrılan yöntem gereklidir.  
  
`in`, `ref`Ve anahtar`out` kelimeleri, aşırı yükleme çözümlemesi amacıyla yöntem imzasının bir parçası olarak kabul edilmez. Bu nedenle, tek fark bir yöntemin bir `ref` veya `in` bağımsız değişken alırsa ve diğeri bir `out` bağımsız değişken alırsa Yöntemler aşırı yüklenemez. Aşağıdaki kod, örneğin derlenmeyecektir:  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
Ancak, bir yöntem bir `ref`, `in`veya `out` bağımsız değişkeni alırsa ve diğeri bu değiştiricilerin hiçbirini içeriyorsa, bunun gibi aşırı yükleme geçerlidir:  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

Derleyici, çağrı sitesindeki parametre değiştiricilerini Yöntem çağrısında kullanılan parametre değiştiricilerine eşleyerek en iyi aşırı yüklemeyi seçer.
 
Özellikler değişken değildir ve bu nedenle parametre olarak `out` geçirilemez.
  
Aşağıdaki tür yöntemler için `in`, `ref`ve `out` anahtar sözcüklerini kullanamazsınız:  
  
- Zaman [uyumsuz](./async.md) değiştirici kullanarak tanımladığınız zaman uyumsuz yöntemler.  
  
- Bir [yield return](./yield.md) veya `yield break` bildiri içeren Yineleyici yöntemleri.  

## <a name="declaring-out-parameters"></a>Parametreleri `out` bildirme   

`out` Bağımsız değişkenlerle bir yöntemi bildirmek, birden çok değer döndürmek için klasik bir geçici çözümdür. 7,0 ' C# den başlayarak, benzer senaryolar için [başlıkları](../../tuples.md) göz önünde bulundurun. Aşağıdaki örnek, tek `out` bir yöntem çağrısıyla üç değişken döndürmek için kullanır. Üçüncü bağımsız değişkenin null 'a atandığını unutmayın. Bu, yöntemlerin değerleri isteğe bağlı olarak döndürmesini sağlar.  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

## <a name="calling-a-method-with-an-out-argument"></a>`out` Bağımsız değişkenle bir yöntemi çağırma

C# 6 ve önceki sürümlerde, `out` bağımsız değişken olarak geçirmeden önce bir değişkeni ayrı bir ifadede bildirmeniz gerekir. Aşağıdaki örnek, bir dizeyi bir sayıya `number` dönüştürmeyi deneyen [Int32. TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) yöntemine geçirilmeden önce adlı bir değişken bildirir.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

C# 7,0 ' den başlayarak `out` değişkeni ayrı bir değişken bildiriminde değil, yöntem çağrısının bağımsız değişken listesinde bildirebilirsiniz. Bu daha kompakt, okunabilir kod üretir ve ayrıca yöntem çağrısından önce değişkene yanlışlıkla bir değer atamaktan de engel olur. Aşağıdaki örnek, `number` [Int32. TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) yöntemine yapılan çağrıda değişkeni tanımladığından, önceki örneğe benzer.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  
   
Önceki örnekte, `number` değişken kesin olarak bir `int`olarak yazılır. Ayrıca, aşağıdaki örnekte olduğu gibi örtük olarak yazılmış bir yerel değişken de bildirebilirsiniz.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  
   
## <a name="c-language-specification"></a>C# Dil Belirtimi  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](./index.md)
- [Yöntem Parametreleri](./method-parameters.md)
