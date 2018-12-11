---
title: out parametresi değiştiricisi - C# başvurusu
ms.custom: seodec18
ms.date: 03/06/2018
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.openlocfilehash: f50490195344c488d264735f89e0107caba888c2
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53242067"
---
# <a name="out-parameter-modifier-c-reference"></a>out parametresi değiştiricisi (C# Başvurusu)
`out` Anahtar sözcüğü, başvuruya göre geçirilecek bağımsız değişkenleri neden olur. Nasıl olduğunu [ref](ref.md) hariç anahtar sözcüğü `ref` kendisine geçirilen önce değişkenin başlatılması gerekir. Aynı zamanda gibi olan [içinde](in-parameter-modifier.md) hariç anahtar sözcüğü `in` çağrılan yöntem bağımsız değişken değerini değiştirmek izin vermez. Kullanılacak bir `out` parametresi, yöntem tanımının hem yöntemi çağrılırken açıkça kullanmalıdır `out` anahtar sözcüğü. Örneğin:  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE] 
> `out` Anahtar sözcüğü de kullanılabilir bir genel tür parametresi tür parametresi birlikte değişken olduğunu belirtmek için. Kullanımı hakkında daha fazla bilgi için `out` anahtar sözcüğü bu bağlamda bkz [out (genel değiştirici)](out-generic-modifier.md).
  
Değişkenleri olarak geçirildi `out` bağımsız değişken bir yöntem çağrısında iletilmeden önce başlatılmış gerekmez. Ancak, çağrılan yöntem yöntemi döndürmeden önce bir değer atamak için gereklidir.  
  
Ancak `in`, `ref`, ve `out` anahtar sözcükleri neden farklı çalışma zamanı davranışı, derleme zamanında yöntem imzasının parçası değerlendirilmez. Tek fark, bir yöntem aldığını ise, bu nedenle, yöntemler aşırı yüklenemez bir `ref` veya `in` bağımsız değişkeni ve diğer alır bir `out` bağımsız değişken. Örneğin, aşağıdaki kod derlemeyecektir:  
  
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

## <a name="declaring-out-arguments"></a>Bildirme `out` bağımsız değişkenleri   

 Bir yöntemi bildirmek `out` bağımsız değişkenleri, birden çok değer döndürmek için bir yöntem istediğinizde yararlıdır. Aşağıdaki örnekte `out` üç değişkenin tek bir yöntem çağrısı ile döndürülecek. Üçüncü bağımsız değişken null olarak atandığını dikkat edin. Bu isteğe bağlı olarak dönüş değerleri için yöntemler sağlar.  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

 [Deneyin deseni](/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods) döndüren içerir bir `bool` bir işlemi başarılı veya başarısız, hem değer döndürüyor üretilen işlemde tarafından belirtmenize olanak bir `out` bağımsız değişken. Bir sayı gibi yöntemleri ayrıştırma [DateTime.TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) yöntemi, bu düzeni kullanın.
   
## <a name="calling-a-method-with-an-out-argument"></a>Bir yöntemi çağırmak bir `out` bağımsız değişken

Olarak geçirmeden önce C# 6 ve önceki sürümlerinde, ayrı bir deyimde değişken bildirmelidir bir `out` bağımsız değişken. Aşağıdaki örnek adlı bir değişken bildirir `number` için geçirilmeden önce [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) yöntemi bir dizeyi sayıya dönüştürmek için çalışır.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

C# 7.0 ile başlayarak, bildirebilirsiniz `out` değişkeni yöntem çağrısında bağımsız değişken listesi yerine ayrı bir değişken bildirimi. Bu daha kompakt ve okunabilir bir kod üretir ve ayrıca yöntem çağrısından önce değişkenine yanlışlıkla bir değer atamadan önler. Tanımladığı dışında önceki örnekteki gibi aşağıdaki örnek, `number` çağrısında değişken [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) yöntemi.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  
   
Önceki örnekte, `number` değişkeni türü kesin olarak belirtilmiş bir `int`. Aşağıdaki örnekte olduğu gibi bir türü örtük olarak belirlenmiş yerel değişken de bildirebilirsiniz.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  
   
## <a name="c-language-specification"></a>C# Dil Belirtimi  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
- [Yöntem Parametreleri](../../../csharp/language-reference/keywords/method-parameters.md)
