---
title: out parametre değiştiricisi-C# başvurusu
ms.date: 03/19/2020
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.openlocfilehash: 30946c85d2b64ead3f42e03da61108fa5b367779
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174815"
---
# <a name="out-parameter-modifier-c-reference"></a>out parametresi değiştiricisi (C# Başvurusu)

`out`Anahtar sözcüğü, bağımsız değişkenlerin başvuruya göre geçirilmesine neden olur. Bir değişken olması gereken, biçimsel parametreye bağımsız değişken için bir diğer ad oluşturur. Diğer bir deyişle, parametresindeki tüm işlemler bağımsız değişkende yapılır. [Ref](ref.md) anahtar sözcüğüne benzer, ancak bu, `ref` değişkeninin geçirilmeden önce başlatılması gerekir. Aynı zamanda [ın](in-parameter-modifier.md) anahtar sözcüğüne benzer, ancak `in` çağrılan yöntemin bağımsız değişken değerini değiştirmesine izin vermez. Bir parametre kullanmak için `out` , hem yöntem tanımı hem de çağıran yöntemi, anahtar sözcüğünü açıkça kullanmalıdır `out` . Örnek:  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE]
> `out`Anahtar sözcüğü, tür parametresinin covaryant olduğunu belirtmek için genel bir tür parametresiyle de kullanılabilir. Anahtar sözcüğünün bu bağlamda kullanımı hakkında daha fazla bilgi için `out` bkz. [Out (genel değiştirici)](out-generic-modifier.md).
  
Bağımsız değişken olarak geçirilen değişkenlerin `out` , yöntem çağrısında geçirilmeden önce başlatılması gerekmez. Ancak, yöntemi döndürmadan önce bir değer atamak için çağrılan yöntem gereklidir.  
  
`in`, `ref` Ve `out` anahtar kelimeleri, aşırı yükleme çözümlemesi amacıyla yöntem imzasının bir parçası olarak kabul edilmez. Bu nedenle, tek fark bir yöntemin bir `ref` veya bağımsız değişken alırsa `in` ve diğeri bir bağımsız değişken alırsa Yöntemler aşırı yüklenemez `out` . Aşağıdaki kod, örneğin derlenmeyecektir:  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
Ancak, bir yöntem bir `ref` , `in` veya `out` bağımsız değişkeni alırsa ve diğeri bu değiştiricilerin hiçbirini içeriyorsa, bunun gibi aşırı yükleme geçerlidir:  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

Derleyici, çağrı sitesindeki parametre değiştiricilerini Yöntem çağrısında kullanılan parametre değiştiricilerine eşleyerek en iyi aşırı yüklemeyi seçer.

Özellikler değişken değildir ve bu nedenle parametre olarak geçirilemez `out` .
  
`in` `ref` `out` Aşağıdaki tür yöntemler için, ve anahtar sözcüklerini kullanamazsınız:  
  
- Zaman [uyumsuz](./async.md) değiştirici kullanarak tanımladığınız zaman uyumsuz yöntemler.  
  
- Bir [yield return](./yield.md) veya bildiri içeren Yineleyici yöntemleri `yield break` .  

Ayrıca, [genişletme yöntemleri](../../programming-guide/classes-and-structs/extension-methods.md) aşağıdaki kısıtlamalara sahiptir:

- `out`Anahtar sözcüğü, bir genişletme yönteminin ilk bağımsız değişkeninde kullanılamaz.
- `ref`Anahtar sözcüğü, bağımsız değişken bir struct olmadığında ya da genel bir tür struct olarak kısıtlanmamışsa Genişletme yönteminin ilk bağımsız değişkeninde kullanılamaz.
- `in`İlk bağımsız değişken bir struct olmadığı müddetçe anahtar sözcüğü kullanılamaz. `in`Anahtar sözcüğü, bir struct gibi sınırlandırsalar bile herhangi bir genel tür üzerinde kullanılamaz.

## <a name="declaring-out-parameters"></a>`out`Parametreleri bildirme

Bağımsız değişkenlerle bir yöntemi bildirmek `out` , birden çok değer döndürmek için klasik bir geçici çözümdür. C# 7,0 ' den başlayarak benzer senaryolar için [değer tanımlama gruplarını](../builtin-types/value-tuples.md) göz önünde bulundurun. Aşağıdaki örnek, `out` tek bir yöntem çağrısıyla üç değişken döndürmek için kullanır. Üçüncü bağımsız değişken null öğesine atandı. Bu, yöntemlerin değerleri isteğe bağlı olarak döndürmesini sağlar.  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

## <a name="calling-a-method-with-an-out-argument"></a>Bağımsız değişkenle bir yöntemi çağırma `out`

C# 6 ve önceki sürümlerde, bağımsız değişken olarak geçirmeden önce bir değişkeni ayrı bir ifadede bildirmeniz gerekir `out` . Aşağıdaki örnek, `number` bir dizeyi bir sayıya dönüştürmeyi deneyen [Int32. TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) yöntemine geçirilmeden önce adlı bir değişken bildirir.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

C# 7,0 ' den başlayarak `out` değişkeni ayrı bir değişken bildiriminde değil, yöntem çağrısının bağımsız değişken listesinde bildirebilirsiniz. Bu daha kompakt, okunabilir kod üretir ve ayrıca yöntem çağrısından önce değişkene yanlışlıkla bir değer atamaktan de engel olur. Aşağıdaki örnek, `number` [Int32. TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) yöntemine yapılan çağrıda değişkeni tanımladığından, önceki örneğe benzer.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  

Önceki örnekte, `number` değişken kesin olarak bir olarak yazılır `int` . Ayrıca, aşağıdaki örnekte olduğu gibi örtük olarak yazılmış bir yerel değişken de bildirebilirsiniz.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  

## <a name="c-language-specification"></a>C# Dil Belirtimi  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# anahtar sözcükleri](./index.md)
- [Yöntem Parametreleri](./method-parameters.md)
