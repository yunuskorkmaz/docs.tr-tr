---
title: parametresi değiştiricisi (C# Başvurusu)
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
ms.openlocfilehash: 9b8b21e2bdc95829c831ee71f24b47986321b7d0
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2018
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

Genellikle bildirmelidir `in` bağımsız değişkenleri değere göre geçirme gerekli kopyalama işlemleri önlemek için bağımsız değişkenler. Bağımsız değişkenler kopyalama işlemleri daha başvuruya göre geçirme daha pahalı olduğu değer türleri yapıları gibi olduğunda bu kullanışlıdır.

> [!WARNING]
>  `in` parametreler yanlış olmadığını daha pahalı olabilir. Derleyici üye yöntemleri yapısı durumunu değiştirirseniz bilemeyebilirsiniz. Derleyici nesne değiştirilmeyen garanti edemez her biçimde geliştirmelisiniz bir kopyasını oluşturur ve bu kopyayı kullanarak başvurular üye çağırır. Olası değişiklikler savunma bu kopyaya ' dir. Geçirmek için bu kopyaları önlemek için iki yol olan `in` parametre olarak `in` bağımsız değişken veya yapıları olarak tanımlamak için `readonly struct`.

## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Yöntem Parametreleri](../../../csharp/language-reference/keywords/method-parameters.md)  
 [Başvuru semantiği ile değer türleri](../../../csharp/reference-semantics-with-value-types.md)
