---
title: "parametresi değiştiricisi (C# Başvurusu)"
ms.date: 03/06/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- parameters [C#], in
- in parameters [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 035aac3e6b902f607e533b709713eb1d07c9774a
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2018
---
# <a name="in-parameter-modifier-c-reference"></a>parametresi değiştiricisi (C# Başvurusu)

`in` Anahtar sözcüğü başvuruya göre geçirilecek bağımsız değişkenler neden olur. Benzer; [ref](ref.md) veya [çıkışı](out-parameter-modifier.md) anahtar sözcüklerini dışındaki `in` bağımsız değişkenleri ancak çağrılan yöntemi tarafından değiştirilemez `ref` bağımsız değişkenleri değiştirilmiş, `out` bağımsız değişkenleri çağıran tarafından değiştirilmesi gerekir ve bu değişiklik observable arama bağlamında.

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

Önceki örnekte gösteren `in` değiştiricisi gereksiz çağrı sitede. Yalnızca yöntemi bildiriminde de gereklidir.

> [!NOTE] 
> `in` Anahtar sözcüğü de kullanılabilir bir genel tür parametresi tür parametresi, bir parçası olarak karşıtıdır olduğunu belirtmek için bir `foreach` deyimi, veya bir parçası olarak bir `join` yan tümcesinde bir LINQ Sorgu. Kullanımı hakkında daha fazla bilgi için `in` anahtar sözcüğü bu bağlamlarında bkz [içinde](in.md) Bu kullanımlar için bağlantılar sağlar.
  
 Değişkenler geçildi olarak `in` bağımsız değişkenleri, bir yöntem çağrısı iletilmeden önce başlatılmalıdır. Ancak, çağrılan yöntemin düzgün bir değer atamak veya bağımsız değişkeni değiştirin.  
  
 Ancak `in`, `ref`, ve `out` anahtar sözcükleri neden farklı bir çalışma zamanı davranışı, derleme zamanında yöntem imzası parçası değerlendirilmez. Bir yöntem aldığını tek fark ise, bu nedenle, yöntem aşırı yüklenemez bir `ref` veya `in` bağımsız değişkeni ve diğer alır bir `out` bağımsız değişkeni. Aşağıdaki kod, örneğin, derlenmez:  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on in, ref and out".
    public void SampleMethod(in int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
Aşırı yükleme varlığını temel `in` izin verilir, ancak derleyici uyarısı oluşturur:  
  
```csharp
class InOverloads
{
    // Discouraged. Calling SampleMethod(value) is ambiguous.
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

Özellikleri veya sabitleri bayraklarıdır olarak `in` parametreleri, çünkü arama yöntemi değerlerine değişiklik yapamazsınız.
  
Kullanamazsınız `in`, `ref`, ve `out` yöntemleri şu tür için anahtar sözcükleri:  
  
- Kullanarak tanımladığınız zaman uyumsuz yöntemleri [zaman uyumsuz](../../../csharp/language-reference/keywords/async.md) değiştiricisi.  
  
- Dahil yineleyici metotları bir [verim return](../../../csharp/language-reference/keywords/yield.md) veya `yield break` deyimi.  

Genellikle bildirmelidir `in` bağımsız değişkenleri değere göre geçirme gerekli kopyalama işlemleri önlemek için bağımsız değişkenler. Bağımsız değişkenler yapıları veya yapıları dizileri olduğunda bu kullanışlıdır.

## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Yöntem Parametreleri](../../../csharp/language-reference/keywords/method-parameters.md)
