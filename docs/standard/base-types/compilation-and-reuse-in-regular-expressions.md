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
ms.openlocfilehash: 3e1dfe8373145286b03e503f038e267ff0d4c4f3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091738"
---
# <a name="compilation-and-reuse-in-regular-expressions"></a>Normal İfadelerde Derleme ve Yeniden Kullanma
Normal ifade altyapısının ifadeleri nasıl derlediğini ve normal ifadelerin nasıl önbelleğe alınacağını anlamak için düzenli ifadeleri yoğun şekilde kullanan uygulamaların performansını en iyi hale getirebilirsiniz. Bu konuda hem derleme hem de önbelleğe alma açıklanmaktadır.  
  
## <a name="compiled-regular-expressions"></a>Derlenmiş normal Ifadeler  
 Varsayılan olarak, normal ifade altyapısı bir normal ifadeyi iç yönergeler dizisine derler (Bunlar, Microsoft ara dili veya MSIL 'den farklı olan üst düzey kodlardır). Motor bir normal ifadeyi yürüttüğünde, iç kodları yorumlar.  
  
 <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> seçeneği ile bir <xref:System.Text.RegularExpressions.Regex> nesnesi oluşturulursa, normal ifadeyi üst düzey normal ifade iç yönergeleri yerine açık MSIL koduna derler. Bu izin verir. Daha yüksek performans için ifadeyi yerel makine koduna dönüştürmek üzere NET-Time (JıT) derleyicisi.  
  
Ancak, oluşturulan MSIL kaldırılamıyor. Kodu kaldırmak için tek yol, tüm uygulama etki alanını (yani, uygulamanızın kodunu) kaldırmak içindir. Etkin bir şekilde, bir normal ifade <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> seçeneği ile derlendikten sonra, normal ifade çöp toplama tarafından yayınlanan bir <xref:System.Text.RegularExpressions.Regex> nesnesi tarafından oluşturulmuş olsa bile, derlenmiş ifade tarafından kullanılan kaynakları hiçbir şekilde serbest bırakmayın.  
  
 Çok fazla kaynak tüketmemek için <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> seçeneğiyle derleyebileceğiniz farklı normal ifade sayısını sınırlandırmaya dikkat etmeniz gerekir. Bir uygulamanın büyük veya sınırsız sayıda normal ifade kullanması gerekiyorsa, her ifadenin derlenmemelidir, yorumlanmalıdır. Ancak, az sayıda normal ifade tekrar tekrar kullanılırsa, daha iyi performans için <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> ile derlenmesi gerekir. Alternatif olarak, önceden derlenmiş normal ifadelerin kullanılması. <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A> yöntemini kullanarak ifadelerinizin tamamını yeniden kullanılabilir bir DLL olarak derleyebilirsiniz. Bu, derlenmiş normal ifadelerin hızından yararlanırken devam ederken çalışma zamanında derleme ihtiyacını önler.  
  
## <a name="the-regular-expressions-cache"></a>Normal Ifadeler önbelleği  
 Normal ifade altyapısı, performansı artırmak için derlenmiş normal ifadelerin uygulama genelinde bir önbelleğini korur. Önbellek, yalnızca statik yöntem çağrılarında kullanılan normal ifade desenlerini depolar. (Örnek yöntemlerine sağlanan normal ifade desenleri önbelleğe alınmaz.) Bu, her kullanıldığı sırada bir ifadeyi üst düzey bayt koduna yeniden ayrıştırma gereksinimini ortadan kaldırır.  
  
 Önbelleğe alınan en fazla normal ifade sayısı, `static` (`Shared` Visual Basic) <xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=nameWithType> özelliğindeki değere göre belirlenir. Varsayılan olarak, normal ifade altyapısı, en fazla 15 derlenmiş normal ifadeyi önbelleğe alır. Derlenmiş normal ifadelerin sayısı önbellek boyutunu aşarsa, en az kullanılan normal ifade atılır ve yeni normal ifade önbelleğe alınır.  
  
 Uygulamanız aşağıdaki iki şekilde önceden derlenmiş normal ifadelerden faydalanabilir:  
  
- Normal ifadeyi tanımlamak için <xref:System.Text.RegularExpressions.Regex> nesnesinin statik bir yöntemini kullanarak. Zaten başka bir statik yöntem çağrısında tanımlanmış olan bir normal ifade deseninin kullanılması durumunda, normal ifade altyapısı onu önbellekten alır. Aksi takdirde, altyapı normal ifadeyi derler ve önbelleğe ekler.  
  
- Var olan bir <xref:System.Text.RegularExpressions.Regex> nesnesini, normal ifade deseninin gerektiği sürece yeniden kullanma.  
  
 Nesne örnekleme ve normal ifade derlemesinin ek yükü nedeniyle, çok sayıda <xref:System.Text.RegularExpressions.Regex> nesnesini oluşturmak ve hızlıca yok etmek çok pahalı bir işlemdir. Çok sayıda farklı normal ifade kullanan uygulamalar için, statik `Regex` yöntemlerine yapılan çağrıları kullanarak ve muhtemelen normal ifade önbelleğinin boyutunu artırarak performansı iyileştirebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET normal Ifadeleri](../../../docs/standard/base-types/regular-expressions.md)
