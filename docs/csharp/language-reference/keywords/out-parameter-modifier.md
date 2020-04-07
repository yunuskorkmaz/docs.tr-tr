---
title: parametre değiştirici - C# Reference
ms.date: 03/19/2020
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.openlocfilehash: 57308992268e1285cfeb82b28e2abf213e7a831b
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805863"
---
# <a name="out-parameter-modifier-c-reference"></a>out parametresi değiştiricisi (C# Başvurusu)

Anahtar `out` kelime bağımsız değişkenlerin başvuruyla geçirilmesine neden olur. Bu, resmi parametreyi bağımsız değişken için bir diğer ad yapar, bu da bir değişken olmalıdır. Başka bir deyişle, parametre üzerinde herhangi bir işlem bağımsız değişken üzerinde yapılır. Bu [ref](ref.md) anahtar kelime gibi, `ref` ancak bu değişken geçirilmeden önce başlatılmasını gerektirir. Ayrıca anahtar kelime [gibi,](in-parameter-modifier.md) ancak `in` bu çağrılan yöntem bağımsız değişken değerini değiştirmek için izin vermez. Bir `out` parametre kullanmak için hem yöntem tanımı hem de `out` arama yönteminin anahtar sözcüğü açıkça kullanması gerekir. Örneğin:  
  
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

Buna ek olarak, [uzantı yöntemleri](../../programming-guide/classes-and-structs/extension-methods.md) aşağıdaki kısıtlamalara sahiptir:

- Anahtar `out` kelime, bir uzantı yönteminin ilk bağımsız değişkeninde kullanılamaz.
- Anahtar `ref` kelime, bağımsız değişken bir yapı olmadığında veya yapı olarak sınırlandırılmamış genel bir tür olduğunda, uzantı yönteminin ilk bağımsız değişkeninde kullanılamaz.
- İlk `in` bağımsız değişken bir yapı olmadığı sürece anahtar sözcük kullanılamaz. Anahtar `in` kelime, yapı olarak sınırlandırılsa bile, herhangi bir genel türde kullanılamaz.

## <a name="declaring-out-parameters"></a>Parametreleri `out` bildirme

Bağımsız değişkenlerle `out` bir yöntem bildirmek, birden çok değer döndürmek için klasik bir geçici çözümdür. C# 7.0 ile başlayarak, benzer senaryolar için [tuples](../../tuples.md) düşünün. Aşağıdaki örnekte, `out` tek bir yöntem çağrısıyla üç değişken i Üçüncü bağımsız değişken null atanır. Bu, yöntemlerin değerleri isteğe bağlı olarak döndürmesini sağlar.  
  
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
