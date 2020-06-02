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
ms.openlocfilehash: 54f14a4f31bef00dd222686cc523935b2d9dd5fa
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279044"
---
# <a name="compilation-and-reuse-in-regular-expressions"></a>Normal İfadelerde Derleme ve Yeniden Kullanma
Normal ifade altyapısının ifadeleri nasıl derlediğini ve normal ifadelerin nasıl önbelleğe alınacağını anlamak için düzenli ifadeleri yoğun şekilde kullanan uygulamaların performansını en iyi hale getirebilirsiniz. Bu konuda hem derleme hem de önbelleğe alma açıklanmaktadır.  
  
## <a name="compiled-regular-expressions"></a>Derlenmiş normal Ifadeler  
 Varsayılan olarak, normal ifade altyapısı bir normal ifadeyi iç yönergeler dizisine derler (Bunlar, Microsoft ara dili veya MSIL 'den farklı olan üst düzey kodlardır). Motor bir normal ifadeyi yürüttüğünde, iç kodları yorumlar.  
  
 Seçeneğiyle bir <xref:System.Text.RegularExpressions.Regex> nesne oluşturulursa <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> , normal ifadeyi üst düzey normal ifade iç yönergeleri yerıne açık MSIL koduna derler. Bu izin verir. Daha yüksek performans için ifadeyi yerel makine koduna dönüştürmek üzere NET-Time (JıT) derleyicisi.  <xref:System.Text.RegularExpressions.Regex>Nesnenin oluşturulması maliyeti daha yüksek olabilir, ancak ile eşleşme gerçekleştirme maliyeti büyük olasılıkla çok daha küçüktür.

 Alternatif olarak, önceden derlenmiş normal ifadelerin kullanılması. Yöntemini kullanarak tüm ifadelerinizi yeniden kullanılabilir bir DLL olarak derleyebilirsiniz <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A> . Bu, derlenmiş normal ifadelerin hızından hala yararlanırken, çalışma zamanında derleme ihtiyacını önler.  
  
## <a name="the-regular-expressions-cache"></a>Normal Ifadeler önbelleği  
 Normal ifade altyapısı, performansı artırmak için derlenmiş normal ifadelerin uygulama genelinde bir önbelleğini korur. Önbellek, yalnızca statik yöntem çağrılarında kullanılan normal ifade desenlerini depolar. (Örnek yöntemlerine sağlanan normal ifade desenleri önbelleğe alınmaz.) Bu, her kullanıldığı sırada bir ifadeyi üst düzey bayt koduna yeniden ayrıştırma gereksinimini ortadan kaldırır.  
  
 Önbelleğe alınan en fazla normal ifade sayısı, `static` ( `Shared` Visual Basic) özelliğinin değerine göre belirlenir <xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=nameWithType> . Varsayılan olarak, normal ifade altyapısı, en fazla 15 derlenmiş normal ifadeyi önbelleğe alır. Derlenmiş normal ifadelerin sayısı önbellek boyutunu aşarsa, en az kullanılan normal ifade atılır ve yeni normal ifade önbelleğe alınır.  
  
 Uygulamanız, normal ifadeleri aşağıdaki iki şekilde kullanabilir:  
  
- <xref:System.Text.RegularExpressions.Regex>Normal ifadeyi tanımlamak için nesnesinin statik bir yöntemini kullanarak. Zaten başka bir statik yöntem çağrısıyla tanımlanmış bir normal ifade deseninin kullanılması durumunda, normal ifade altyapısı onu önbellekten almaya çalışır. Önbellekte yoksa, altyapı normal ifadeyi derler ve önbelleğe ekler.
  
- Varolan bir <xref:System.Text.RegularExpressions.Regex> nesneyi normal ifade deseninin gerektiği sürece yeniden kullanma.  
  
 Nesne örneği oluşturma ve normal ifade derleme ek yükü nedeniyle çok sayıda nesne oluşturmak ve hızlıca yok etmek <xref:System.Text.RegularExpressions.Regex> çok pahalı bir işlemdir. Çok sayıda farklı normal ifade kullanan uygulamalar için, statik yöntemlere yapılan çağrıları kullanarak `Regex` ve muhtemelen normal ifade önbelleğinin boyutunu artırarak performansı iyileştirebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET normal Ifadeleri](regular-expressions.md)
