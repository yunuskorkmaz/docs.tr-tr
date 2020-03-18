---
title: parametre değiştirici - C# Reference
ms.date: 03/26/2019
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.openlocfilehash: f963188d77685bb81f7dc9fb3794e343114fe3c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173568"
---
# <a name="out-parameter-modifier-c-reference"></a>out parametresi değiştiricisi (C# Başvurusu)
Anahtar `out` kelime bağımsız değişkenlerin başvuruyla geçirilmesine neden olur. Bu, resmi parametreyi bağımsız değişken için bir diğer ad yapar, bu da bir değişken olmalıdır. Başka bir deyişle, parametre üzerinde herhangi bir işlem bağımsız değişken üzerinde yapılır. Bu [ref](ref.md) anahtar kelime gibi, `ref` ancak bu değişken geçirilmeden önce başlatılmasını gerektirir. Ayrıca anahtar kelime [gibi,](in-parameter-modifier.md) ancak `in` bu çağrılan yöntem bağımsız değişken değerini değiştirmek için izin vermez. Bir `out` parametre kullanmak için hem yöntem tanımı hem de `out` arama yönteminin anahtar sözcüğü açıkça kullanması gerekir. Örnek:  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE]
> `out` Anahtar kelime, tür parametresinin ortak olduğunu belirtmek için genel bir tür parametresi ile de kullanılabilir. Bu bağlamda `out` anahtar kelimenin kullanımı hakkında daha fazla bilgi için bkz. [out (Generic Modifier)](out-generic-modifier.md)
  
Bağımsız değişkenler `out` olarak geçirilen değişkenlerin bir yöntem çağrısında geçirilmeden önce başlatılması gerekmez. Ancak, yöntem dönmeden önce bir değer atamak için çağrılan yöntem gereklidir.  
  
, `in` `ref`ve `out` anahtar kelimeler aşırı yük çözümlemesi amacıyla yöntem imzasının bir parçası olarak kabul edilmez. Bu nedenle, tek fark bir yöntemin bir `ref` bağımsız `in` değişken ilerlerken `out` diğerinin bir bağımsız değişken almasıysa, yöntemler aşırı yüklenemez. Örneğin, aşağıdaki kod derlenilmeyecektir:  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
Aşırı yükleme yasal, ancak, bir `ref`yöntem `in`alır `out` , , veya argüman ve diğer bu gibi bu değiştiriciler hiçbiri vardır:  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

Derleyici, çağrı yerindeki parametre değiştiricilerini yöntem çağrısında kullanılan parametre değiştiricileriyle eşleştirerek en iyi aşırı yüklemeyi seçer.

Özellikler değişken değildir ve bu nedenle `out` parametre olarak geçirilemez.
  
Aşağıdaki yöntem türleri `in`için `ref`, `out` ve anahtar kelimeleri kullanamazsınız:  
  
- Async değiştirici kullanarak tanımladığınız [async](./async.md) yöntemleri.  
  
- [Verim getirisi](./yield.md) veya `yield break` deyimi içeren yineleyici yöntemleri.  

## <a name="declaring-out-parameters"></a>Parametreleri `out` bildirme

Bağımsız değişkenlerle `out` bir yöntem bildirmek, birden çok değer döndürmek için klasik bir geçici çözümdür. C# 7.0 ile başlayarak, benzer senaryolar için [tuples](../../tuples.md) düşünün. Aşağıdaki örnekte, `out` tek bir yöntem çağrısıyla üç değişken i Üçüncü bağımsız değişkenin null olarak atandığını unutmayın. Bu, yöntemlerin değerleri isteğe bağlı olarak döndürmesini sağlar.  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

## <a name="calling-a-method-with-an-out-argument"></a>Bir yöntemi `out` bağımsız değişkenle çağırma

C# 6 ve daha önce, bir değişkeni bağımsız değişken olarak `out` geçirmeden önce ayrı bir ifadede bildirmeniz gerekir. Aşağıdaki örnek, bir dizeyi bir sayıya dönüştürmeyi amaçlayan `number` [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) yöntemine geçirilmeden önce adlı bir değişkeni bildirir.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

C# 7.0 ile başlayarak, `out` değişkeni ayrı bir değişken bildirimi yerine yöntem çağrısının bağımsız değişken listesinde bildirebilirsiniz. Bu, daha kompakt, okunabilir kod üretir ve yöntem çağrısından önce değişkene yanlışlıkla bir değer atamanızı engeller. Aşağıdaki örnek, [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) `number` yöntemine yapılan çağrıdaki değişkeni tanımlaması dışında önceki örnekteki gibidir.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  

Önceki örnekte, `number` değişken güçlü bir şekilde `int`. Aşağıdaki örnekte olduğu gibi, örtülü olarak yazılan yerel değişkeni de bildirebilirsiniz.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  

## <a name="c-language-specification"></a>C# Dil Belirtimi  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Kelimeler](./index.md)
- [Yöntem Parametreleri](./method-parameters.md)
