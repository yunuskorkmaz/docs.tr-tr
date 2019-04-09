---
title: out parametresi değiştiricisi - C# başvurusu
ms.custom: seodec18
ms.date: 03/26/2019
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.openlocfilehash: 769d1ac0b6266c87e99605c76a25e016f15eb11c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125761"
---
# <a name="out-parameter-modifier-c-reference"></a>out parametresi değiştiricisi (C# Başvurusu)
`out` Anahtar sözcüğü, başvuruya göre geçirilecek bağımsız değişkenleri neden olur. Bir değişken olmalıdır bağımsız değişkeni için bir diğer ad biçimsel parametre kolaylaştırır. Diğer bir deyişle, herhangi bir işlem parametresinde bağımsız değişken üzerinde yapılır. Nasıl olduğunu [ref](ref.md) hariç anahtar sözcüğü `ref` kendisine geçirilen önce değişkenin başlatılması gerekir. Aynı zamanda gibi olan [içinde](in-parameter-modifier.md) hariç anahtar sözcüğü `in` çağrılan yöntem bağımsız değişken değerini değiştirmek izin vermez. Kullanılacak bir `out` parametresi, yöntem tanımının hem yöntemi çağrılırken açıkça kullanmalıdır `out` anahtar sözcüğü. Örneğin:  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE] 
> `out` Anahtar sözcüğü de kullanılabilir bir genel tür parametresi tür parametresi birlikte değişken olduğunu belirtmek için. Kullanımı hakkında daha fazla bilgi için `out` anahtar sözcüğü bu bağlamda bkz [out (genel değiştirici)](out-generic-modifier.md).
  
Değişkenleri olarak geçirildi `out` bağımsız değişken bir yöntem çağrısında iletilmeden önce başlatılmış gerekmez. Ancak, çağrılan yöntem yöntemi döndürmeden önce bir değer atamak için gereklidir.  
  
`in`, `ref`, Ve `out` anahtar sözcükleri aşırı yükleme çözünürlüğü amacıyla yöntem imzasının parçası dikkate alınmaz. Tek fark, bir yöntem aldığını ise, bu nedenle, yöntemler aşırı yüklenemez bir `ref` veya `in` bağımsız değişkeni ve diğer alır bir `out` bağımsız değişken. Örneğin, aşağıdaki kod derlemeyecektir:  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
Aşırı yükleme yasal, ancak bir yöntem uzun sürerse bir `ref`, `in`, veya `out` bağımsız değişken ve diğer sahip böyle bu değiştiricileri hiçbiri:  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

Derleyici, yöntem çağrısında kullanılan parametre değiştiriciler çağrı sitesinde parametre değiştiriciler eşleştirerek en iyi aşırı yüklemede seçer.
 
Özellikler değişkenleri değildir ve olarak gönderilemez `out` parametreleri.
  
Kullanamazsınız `in`, `ref`, ve `out` yöntemleri aşağıdaki türde için anahtar sözcükler:  
  
-   Kullanarak tanımladığınız zaman uyumsuz yöntemlerde [zaman uyumsuz](../../../csharp/language-reference/keywords/async.md) değiştiricisi.  
  
-   Yineleyici yöntemleri dahil bir [yield return](../../../csharp/language-reference/keywords/yield.md) veya `yield break` deyimi.  

## <a name="declaring-out-parameters"></a>Bildirme `out` parametreleri   

Bir yöntemi bildirmek `out` bağımsız değişkenleri olan birden çok değer döndürmek için Klasik bir geçici çözüm. İle başlayarak C# 7.0 göz önünde bulundurun [diziler](../../tuples.md) benzer senaryolar için. Aşağıdaki örnekte `out` üç değişkenin tek bir yöntem çağrısı ile döndürülecek. Üçüncü bağımsız değişken null olarak atandığını dikkat edin. Bu isteğe bağlı olarak dönüş değerleri için yöntemler sağlar.  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

## <a name="calling-a-method-with-an-out-argument"></a>Bir yöntemi çağırmak bir `out` bağımsız değişken

Olarak geçirmeden önce C# 6 ve önceki sürümlerinde, ayrı bir deyimde değişken bildirmelidir bir `out` bağımsız değişken. Aşağıdaki örnek adlı bir değişken bildirir `number` için geçirilmeden önce [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) yöntemi bir dizeyi sayıya dönüştürmek için çalışır.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

C# 7.0 ile başlayarak, bildirebilirsiniz `out` değişkeni yöntem çağrısında bağımsız değişken listesi yerine ayrı bir değişken bildirimi. Bu daha kompakt ve okunabilir bir kod üretir ve ayrıca yöntem çağrısından önce değişkenine yanlışlıkla bir değer atamadan önler. Tanımladığı dışında önceki örnekteki gibi aşağıdaki örnek, `number` çağrısında değişken [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) yöntemi.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  
   
Önceki örnekte, `number` değişkeni türü kesin olarak belirtilmiş bir `int`. Aşağıdaki örnekte olduğu gibi bir türü örtük olarak belirlenmiş yerel değişken de bildirebilirsiniz.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  
   
## <a name="c-language-specification"></a>C# Dil Belirtimi  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Başvurusu](../../../csharp/language-reference/index.md)
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)
- [Yöntem Parametreleri](../../../csharp/language-reference/keywords/method-parameters.md)
