---
title: out parametre değiştiricisi- C# başvuru
ms.date: 03/26/2019
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.openlocfilehash: bc3814b91ed4327f4af1a4a1bfbda632b0393bb8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713278"
---
# <a name="out-parameter-modifier-c-reference"></a>out parametresi değiştiricisi (C# Başvurusu)
`out` anahtar sözcüğü, bağımsız değişkenlerin başvuruya göre geçirilmesine neden olur. Bir değişken olması gereken, biçimsel parametreye bağımsız değişken için bir diğer ad oluşturur. Diğer bir deyişle, parametresindeki tüm işlemler bağımsız değişkende yapılır. [Ref](ref.md) anahtar sözcüğüne benzer, çünkü `ref`, değişkeninin geçirilmeden önce başlatılmasını gerektirir. Aynı zamanda [ın](in-parameter-modifier.md) anahtar sözcüğü de gibidir, çünkü `in` bağımsız değişken değerini değiştirmek için çağrılan yönteme izin vermez. Bir `out` parametresi kullanmak için, hem yöntem tanımı hem de çağıran yöntem, `out` anahtar sözcüğünü açıkça kullanmalıdır. Örneğin:  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE] 
> `out` anahtar sözcüğü, tür parametresinin covaryant olduğunu belirtmek için genel bir tür parametresiyle de kullanılabilir. `out` anahtar sözcüğünün bu bağlamda kullanımı hakkında daha fazla bilgi için bkz. [Out (genel değiştirici)](out-generic-modifier.md).
  
`out` bağımsız değişken olarak geçirilen değişkenlerin, yöntem çağrısında geçirilmeden önce başlatılması gerekmez. Ancak, yöntemi döndürmadan önce bir değer atamak için çağrılan yöntem gereklidir.  
  
`in`, `ref`ve `out` anahtar sözcükleri, aşırı yükleme çözümlemesi amacıyla yöntem imzasının bir parçası olarak kabul edilmez. Bu nedenle, tek fark bir yöntem `ref` veya `in` bağımsız değişken alırsa ve diğeri bir `out` bağımsız değişkeni alırsa Yöntemler aşırı yüklenemez. Aşağıdaki kod, örneğin derlenmeyecektir:  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
Ancak, bir yöntem `ref`, `in`veya `out` bağımsız değişkeni alırsa ve diğeri bunun gibi bu değiştiricilerin hiçbirini içeriyorsa, aşırı yükleme geçerlidir:  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

Derleyici, çağrı sitesindeki parametre değiştiricilerini Yöntem çağrısında kullanılan parametre değiştiricilerine eşleyerek en iyi aşırı yüklemeyi seçer.
 
Özellikler değişken değildir ve bu nedenle `out` parametresi olarak geçirilemez.
  
Aşağıdaki tür yöntemler için `in`, `ref`ve `out` anahtar sözcüklerini kullanamazsınız:  
  
- Zaman [uyumsuz](./async.md) değiştirici kullanarak tanımladığınız zaman uyumsuz yöntemler.  
  
- Bir [yield return](./yield.md) veya `yield break` ifadesini içeren Yineleyici yöntemleri.  

## <a name="declaring-out-parameters"></a>`out` parametrelerini bildirme   

`out` bağımsız değişkenlerle bir yöntemi bildirmek, birden çok değer döndürmek için klasik bir geçici çözümdür. 7,0 ' C# den başlayarak, benzer senaryolar için [başlıkları](../../tuples.md) göz önünde bulundurun. Aşağıdaki örnek, tek bir yöntem çağrısıyla üç değişken döndürmek için `out` kullanır. Üçüncü bağımsız değişkenin null 'a atandığını unutmayın. Bu, yöntemlerin değerleri isteğe bağlı olarak döndürmesini sağlar.  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

## <a name="calling-a-method-with-an-out-argument"></a>Bir yöntemi `out` bağımsız değişkenle çağırma

C# 6 ve önceki sürümlerde, bir değişkeni `out` bağımsız değişken olarak geçirmeden önce ayrı bir ifadede bildirmeniz gerekir. Aşağıdaki örnek, bir dizeyi bir sayıya dönüştürmeyi deneyen [Int32. TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) yöntemine geçirilmeden önce `number` adlı bir değişken bildirir.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

C# 7,0 ' den başlayarak, `out` değişkenini ayrı bir değişken bildiriminde değil yöntem çağrısının bağımsız değişken listesinde bildirebilirsiniz. Bu daha kompakt, okunabilir kod üretir ve ayrıca yöntem çağrısından önce değişkene yanlışlıkla bir değer atamaktan de engel olur. Aşağıdaki örnek, [Int32. TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) yöntemine yapılan çağrıda `number` değişkenini tanımladığından, önceki örneğe benzer.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  
   
Önceki örnekte `number` değişkeni kesin olarak bir `int`olarak yazılır. Ayrıca, aşağıdaki örnekte olduğu gibi örtük olarak yazılmış bir yerel değişken de bildirebilirsiniz.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  
   
## <a name="c-language-specification"></a>C# Dil Belirtimi  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](./index.md)
- [Yöntem Parametreleri](./method-parameters.md)
