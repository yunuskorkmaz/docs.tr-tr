---
title: Normal İfadelerde Derleme ve Yeniden Kullanma
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- parsing text with regular expressions, compilation
- searching with regular expressions, compilation
- .NET Framework regular expressions, engines
- .NET Framework regular expressions, compilation
- regular expressions, compilation
- compilation, regular expressions
- pattern-matching with regular expressions, compilation
- regular expressions, engines
ms.assetid: 182ec76d-5a01-4d73-996c-0b0d14fcea18
ms.openlocfilehash: b89f7f88233ecdab25ba2a74647aafeb4d8b74af
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344186"
---
# <a name="compilation-and-reuse-in-regular-expressions"></a>Normal İfadelerde Derleme ve Yeniden Kullanma
Normal ifade altyapısının ifadeleri nasıl derlediğini anlayarak ve normal ifadelerin önbelleğe nasıl kullanıldığını anlayarak normal ifadeleri yaygın olarak kullanan uygulamaların performansını en iyi duruma getirebilirsiniz. Bu konu hem derleme hem de önbelleğe alma konur.  
  
## <a name="compiled-regular-expressions"></a>Derlenmiş Düzenli İfadeler  
 Varsayılan olarak, normal ifade altyapısı bir iç yönerge dizisine normal bir ifade derler (bunlar Microsoft ara dilinden veya MSIL'den farklı olan üst düzey kodlardır). Motor düzenli bir ifade yürütürken, iç kodları yorumlar.  
  
 Bir <xref:System.Text.RegularExpressions.Regex> nesne <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> seçeneğiyle oluşturulmuşsa, üst düzey normal ifade iç yönergeleri yerine normal ifadeyi açık MSIL koduna derler. Bu sağlar. NET'in tam zamanında (JIT) derleyicisi daha yüksek performans için ifadeyi yerel makine koduna dönüştürür.  Nesneyi <xref:System.Text.RegularExpressions.Regex> oluşturmanın maliyeti daha yüksek olabilir, ancak onunla eşleşen performans maliyeti çok daha küçük olması muhtemeldir.

 Bir alternatif önceden derlenmiş düzenli ifadeler kullanmaktır. Tüm ifadelerinizi <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A> yöntemi kullanarak yeniden kullanılabilir bir DLL'ye kopyalayabilirsiniz. Bu, derlenmiş düzenli ifadelerin hızından yararlanırken çalışma zamanında derleme gereksinimini önler.  
  
## <a name="the-regular-expressions-cache"></a>Normal İfadeler Önbelleği  
 Performansı artırmak için, normal ifade altyapısı derlenmiş düzenli ifadelerin uygulama çapında önbelleğini tutar. Önbellek, yalnızca statik yöntem çağrılarında kullanılan düzenli ifade desenleri depolar. (Örnek yöntemlerine verilen normal ifade desenleri önbelleğe alınmaz.) Bu, bir ifadenin her kullanıldığında üst düzey bayt koduna reparse gereksinimini önler.  
  
 Önbelleğe alınan en fazla normal ifade sayısı `static` (`Shared` Visual Basic'teki) <xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=nameWithType> özelliğinin değerine göre belirlenir. Varsayılan olarak, normal ifade altyapısı 15'e kadar derlenmiş normal ifadeleri önbelleğe alır. Derlenen normal ifadelerin sayısı önbellek boyutunu aşıyorsa, en son kullanılan normal ifade atılır ve yeni normal ifade önbelleğe çıkar.  
  
 Uygulamanız normal ifadeleri aşağıdaki iki şekilde yeniden kullanabilir:  
  
- Normal ifadeyi tanımlamak <xref:System.Text.RegularExpressions.Regex> için nesnenin statik bir yöntem kullanarak. Başka bir statik yöntem çağrısı yla zaten tanımlanmış olan normal bir ifade deseni kullanıyorsanız, normal ifade altyapısı önbellekten almaya çalışır. Önbellekte kullanılamıyorsa, motor normal ifadeyi derler ve önbelleğe ekler.
  
- Varolan <xref:System.Text.RegularExpressions.Regex> bir nesneyi normal ifade deseni gerekli olduğu sürece yeniden kullanarak.  
  
 Çünkü nesne anlık ve düzenli ifade derleme yükü, oluşturma ve hızla <xref:System.Text.RegularExpressions.Regex> çok sayıda nesne yok çok pahalı bir süreçtir. Çok sayıda farklı normal ifade kullanan uygulamalar da, statik `Regex` yöntemlere yapılan çağrıları kullanarak ve büyük olasılıkla normal ifade önbelleğinin boyutunu artırarak performansı en iyi duruma getirebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET Düzenli İfadeler](../../../docs/standard/base-types/regular-expressions.md)
