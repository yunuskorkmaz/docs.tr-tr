---
title: "out parametresi değiştiricisi (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.assetid: 3fce0dc5-03f4-4faa-bd61-36c41bc6baf1
caps.latest.revision: "9"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 68ef554f95fe71f925cfa22cc49758cec3da237e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="out-parameter-modifier-c-reference"></a>out parametresi değiştiricisi (C# Başvurusu)
`out` Anahtar sözcüğü başvuruya göre geçirilecek bağımsız değişkenler neden olur. Benzer; [ref](../../../csharp/language-reference/keywords/ref.md) hariç anahtar sözcüğü `ref` değişkenin kendisine geçirilen önce başlatılması gerekir. Kullanılacak bir `out` parametresi, yöntem tanımı ve arama yöntemi açıkça kullanmalıdır `out` anahtar sözcüğü. Örneğin:  
  
 [!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/out/out-1.cs)]  

> [!NOTE] 
> `out` Anahtar sözcüğü de genel tür parametresi ile tür parametresi birlikte değişkendir olduğunu belirtmek için kullanılabilir. Kullanımı hakkında daha fazla bilgi için `out` anahtar sözcüğü bu bağlamda bkz [out (genel değiştirici)](../../../csharp/language-reference/keywords/out-generic-modifier.md).
  
 Değişkenler geçildi olarak `out` bağımsız bir yöntem çağrısı iletilmeden önce başlatılmış gerekmez. Ancak, çağrılan yöntemin yöntemi döndürmeden önce bir değer atamak için gereklidir.  
  
 Ancak `ref` ve `out` anahtar sözcükleri neden farklı bir çalışma zamanı davranışı, derleme zamanında yöntem imzası parçası değerlendirilmez. Bir yöntem aldığını tek fark ise, bu nedenle, yöntem aşırı yüklenemez bir `ref` bağımsız değişkeni ve diğer alır bir `out` bağımsız değişkeni. Aşağıdaki kod, örneğin, derlenmez:  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
Aşırı yükleme yasal, ancak bir yöntem uzun sürerse bir `ref` veya `out` bağımsız değişkeni ve diğer şöyle hiçbiri kullanır:  
  
 [!code-csharp[csrefKeywordsMethodParams#3](../../../../samples/snippets/csharp/language-reference/keywords/out/out-3.cs)]  
  
 Özellikleri değişkenleri değildir ve bu nedenle olarak gönderilemez `out` parametreleri.  
  
 Dizileri geçirme hakkında daha fazla bilgi için bkz: [kullanarak dizileri geçirme ref ve çıkış](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).  
  
 Kullanamazsınız `ref` ve `out` yöntemleri şu tür için anahtar sözcükleri:  
  
-   Kullanarak tanımladığınız zaman uyumsuz yöntemleri [zaman uyumsuz](../../../csharp/language-reference/keywords/async.md) değiştiricisi.  
  
-   Dahil yineleyici metotları bir [verim return](../../../csharp/language-reference/keywords/yield.md) veya `yield break` deyimi.  

## <a name="declaring-out-arguments"></a>Bildirme `out` bağımsız değişkenleri   

 Bir yöntemle bildirme `out` bağımsız değişkenleri, birden çok değer döndürmek için bir yöntem istediğinizde yararlıdır. Aşağıdaki örnek kullanır `out` tek yöntem çağrısı üç değişkenlerle dönün. Üçüncü bağımsız değişkeni null atandığını dikkat edin. Bu değer isteğe bağlı olarak döndürmek yöntemleri sağlar.  
  
 [!code-csharp[csrefKeywordsMethodParams#4](../../../../samples/snippets/csharp/language-reference/keywords/out/out-4.cs)]  

 [Deneyin düzeni](/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods.md) döndürme içerir bir `bool` bir işlem başarılı ve başarısız oldu ve değer döndürme üretilen işlemi tarafından olup olmadığını belirtmek için bir `out` bağımsız değişkeni. Yöntemleri gibi ayrıştırma sayısı [DateTime.TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) yöntemi, bu deseni kullanır.
   
## <a name="calling-a-method-with-an-out-argument"></a>Bir yöntemi çağırma bir `out` bağımsız değişken

Olarak geçirmeden önce C# 6 ve önceki sürümlerinde, ayrı bir deyimi bir değişkene bildirmelidir bir `out` bağımsız değişkeni. Aşağıdaki örnek adlı bir değişken bildiren `number` için geçmeden önce [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) bir dizeyi sayıya dönüştürme girişiminde yöntemi.

 [!code-csharp[csrefKeywordsMethodParams#5](../../../../samples/snippets/csharp/language-reference/keywords/out/out-5.cs)]  

C# 7 ile başlayan, bildirebilirsiniz `out` değişkeni yöntem çağrısı bağımsız değişken listesi yerine ayrı bir değişken bildirimi. Bu daha küçük, okunabilir kodunu üretir ve ayrıca yanlışlıkla bir değer değişken yöntemi çağırmadan önce atanmasını engeller. Tanımladığı aşağıdaki örnek önceki örnek gibi olmasıdır `number` çağrısında değişken [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) yöntemi.

 [!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/out/out-6.cs)]  
   
Önceki örnekte, `number` değişken olarak belirtilmiş kesinlikle bir `int`. Aşağıdaki örnekte olduğu gibi bir türü örtük olarak belirlenmiş yerel değişkeni de bildirebilirsiniz.

 [!code-csharp[csrefKeywordsMethodParams#7](../../../../samples/snippets/csharp/language-reference/keywords/out/out-7.cs)]  
   
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Yöntem parametreleri](../../../csharp/language-reference/keywords/method-parameters.md)
