---
title: out parametresi değiştiricisi (C# Başvurusu)
ms.date: 03/06/2018
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.openlocfilehash: 76c2c27d4575918bb2ed4209a7ff7d2b0517b6f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="out-parameter-modifier-c-reference"></a>out parametresi değiştiricisi (C# Başvurusu)
`out` Anahtar sözcüğü başvuruya göre geçirilecek bağımsız değişkenler neden olur. Benzer; [ref](ref.md) hariç anahtar sözcüğü `ref` değişkenin kendisine geçirilen önce başlatılması gerekir. Aynı zamanda gibi olan [içinde](in-parameter-modifier.md) hariç anahtar sözcüğü `in` bağımsız değişken değeri değiştirmek çağrılan yöntemine izin vermiyor. Kullanılacak bir `out` parametresi, yöntem tanımı ve arama yöntemi açıkça kullanmalıdır `out` anahtar sözcüğü. Örneğin:  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE] 
> `out` Anahtar sözcüğü de genel tür parametresi ile tür parametresi birlikte değişkendir olduğunu belirtmek için kullanılabilir. Kullanımı hakkında daha fazla bilgi için `out` anahtar sözcüğü bu bağlamda bkz [out (genel değiştirici)](out-generic-modifier.md).
  
Değişkenler geçildi olarak `out` bağımsız bir yöntem çağrısı iletilmeden önce başlatılmış gerekmez. Ancak, çağrılan yöntemin yöntemi döndürmeden önce bir değer atamak için gereklidir.  
  
Ancak `in`, `ref`, ve `out` anahtar sözcükleri neden farklı bir çalışma zamanı davranışı, derleme zamanında yöntem imzası parçası değerlendirilmez. Bir yöntem aldığını tek fark ise, bu nedenle, yöntem aşırı yüklenemez bir `ref` veya `in` bağımsız değişkeni ve diğer alır bir `out` bağımsız değişkeni. Aşağıdaki kod, örneğin, derlenmez:  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
Aşırı yükleme yasal, ancak bir yöntem uzun sürerse bir `ref`, `in`, veya `out` bağımsız değişkeni ve diğer şöyle bu değiştiricileri hiçbiri sahiptir:  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

Derleyici, yöntem çağrısında kullanılan parametre değiştiricileri çağrısı sitesinde parametre değiştiricileri eşleştirerek en iyi aşırı seçer.
 
Özellikleri değişkenleri değildir ve bu nedenle olarak gönderilemez `out` parametreleri.
  
 Dizileri geçirme hakkında daha fazla bilgi için bkz: [kullanarak dizileri geçirme ref ve çıkış](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).  
  
 Kullanamazsınız `in`, `ref`, ve `out` yöntemleri şu tür için anahtar sözcükleri:  
  
-   Kullanarak tanımladığınız zaman uyumsuz yöntemleri [zaman uyumsuz](../../../csharp/language-reference/keywords/async.md) değiştiricisi.  
  
-   Dahil yineleyici metotları bir [verim return](../../../csharp/language-reference/keywords/yield.md) veya `yield break` deyimi.  

## <a name="declaring-out-arguments"></a>Bildirme `out` bağımsız değişkenleri   

 Bir yöntemle bildirme `out` bağımsız değişkenleri, birden çok değer döndürmek için bir yöntem istediğinizde yararlıdır. Aşağıdaki örnek kullanır `out` tek yöntem çağrısı üç değişkenlerle dönün. Üçüncü bağımsız değişkeni null atandığını dikkat edin. Bu değer isteğe bağlı olarak döndürmek yöntemleri sağlar.  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

 [Deneyin düzeni](/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods.md) döndürme içerir bir `bool` bir işlem başarılı ve başarısız oldu ve değer döndürme üretilen işlemi tarafından olup olmadığını belirtmek için bir `out` bağımsız değişkeni. Yöntemleri gibi ayrıştırma sayısı [DateTime.TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) yöntemi, bu deseni kullanır.
   
## <a name="calling-a-method-with-an-out-argument"></a>Bir yöntemi çağırma bir `out` bağımsız değişken

Olarak geçirmeden önce C# 6 ve önceki sürümlerinde, ayrı bir deyimi bir değişkene bildirmelidir bir `out` bağımsız değişkeni. Aşağıdaki örnek adlı bir değişken bildiren `number` için geçmeden önce [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) bir dizeyi sayıya dönüştürme girişiminde yöntemi.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

C# 7. 0'dan başlayarak, bildirebilirsiniz `out` değişkeni yöntem çağrısı bağımsız değişken listesi yerine ayrı bir değişken bildirimi. Bu daha küçük, okunabilir kodunu üretir ve ayrıca yanlışlıkla bir değer değişken yöntemi çağırmadan önce atanmasını engeller. Tanımladığı aşağıdaki örnek önceki örnek gibi olmasıdır `number` çağrısında değişken [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) yöntemi.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  
   
Önceki örnekte, `number` değişken olarak belirtilmiş kesinlikle bir `int`. Aşağıdaki örnekte olduğu gibi bir türü örtük olarak belirlenmiş yerel değişkeni de bildirebilirsiniz.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  
   
## <a name="c-language-specification"></a>C# Dil Belirtimi  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Yöntem Parametreleri](../../../csharp/language-reference/keywords/method-parameters.md)
