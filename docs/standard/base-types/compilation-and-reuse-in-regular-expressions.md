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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2166412269a84329d42f58c7e3423229be4327b8
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43877782"
---
# <a name="compilation-and-reuse-in-regular-expressions"></a>Normal İfadelerde Derleme ve Yeniden Kullanma
Normal ifadelerin kapsamlı kullanımını nasıl ifadeler normal ifade altyapısı derler anlama ve nasıl normal ifadeler önbelleğe anlama olun uygulamaların performansını iyileştirebilir. Bu konuda, hem derleme hem de önbelleğe alma anlatılmaktadır.  
  
## <a name="compiled-regular-expressions"></a>Derlenmiş normal ifadeler  
 Varsayılan olarak, normal ifade altyapısının bir dizi için normal bir ifade iç yönergeleri (Microsoft Ara dili veya MSIL farklı olan üst düzey kodları bunlar) derler. Bir normal ifade altyapısı yürütüldüğünde, iç kodları yorumlar.  
  
 Varsa bir <xref:System.Text.RegularExpressions.Regex> nesnesi ile oluşturulduğunda <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> seçeneği, normal ifade için üst düzey bir normal ifade iç yönergeler yerine açık MSIL kodu derler. Bu izin verir. İfade, daha yüksek performans için yerel makine koda dönüştürmek için NET just-in-time (JIT) derleyicisi.  
  
Ancak, oluşturulan MSIL kaldırılamıyor. Tüm uygulama etki alanını kaldırmak için kodun kaldırılmasını tek yolu olduğundan (diğer bir deyişle, tüm uygulamanızın kaldırmak için kullanıcının kodu.). Etkili bir şekilde, normal bir ifade ile derlenen sonra <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> seçeneği, hiçbir zaman bile normal ifade tarafından oluşturulan derlenmiş ifade tarafından kullanılan kaynakları serbest bırakır bir <xref:System.Text.RegularExpressions.Regex> kendisini çöp toplama için yayımlanmış olan nesne.  
  
 Derleme farklı normal ifadeler sayısını sınırlamak dikkatli olmanız gerekir <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> çok fazla kaynak tüketmeye önlemek için seçeneği. Uygulamanın normal ifadelerin büyük ya da sınırlandırılmamış bir sayı kullanmanız gerekiyorsa, derlenmemiş her ifade yorumlanıp. Normal ifadeleri çok az sayıda art arda kullanılması durumunda, ancak bunlar ile derlenmelidir <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> daha iyi performans için. Önceden derlenmiş normal ifadeler kullanmaya alternatiftir. Tüm yeniden kullanılabilir bir DLL, ifadelere kullanarak derleme <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A> yöntemi. Bu, çalışma zamanında derlenmiş normal ifadeler hızından hala yararlanmaya sırasında derleme gereksinimini ortadan kaldırır.  
  
## <a name="the-regular-expressions-cache"></a>Normal ifadeler önbellek  
 Performansı artırmak için bir uygulama önbellek derlenmiş normal ifadeler, normal ifade altyapısı tutar. Önbellek, yalnızca statik yöntem çağrılarında kullanılan normal ifade desenleri depolar. (Örnek yöntemleri için sağlanan normal ifade deseni önbelleğe alınmaz.) Bu, bir ifade kullanıldığı her zaman üst düzey bayt koda yeniden ayrıştırma gereksinimini ortadan kaldırır.  
  
 Önbelleğe alınan normal ifadelerin sayısı değeri tarafından belirlenir `static` (`Shared` Visual Basic'te) <xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=nameWithType> özelliği. Varsayılan olarak, en fazla 15 derlenmiş normal ifadeler normal ifade altyapısının önbelleğe alır. Derlenmiş normal ifadeler önbellek boyutunu aşıyor, yakın zamanda kullanılmamış normal ifade atılır ve yeni bir normal ifade önbelleğe alınır.  
  
 Uygulamanızın önceden derlenmiş normal ifadelerin aşağıdaki iki yoldan birini yararlanabilirsiniz:  
  
-   Statik bir yöntemi kullanarak <xref:System.Text.RegularExpressions.Regex> normal ifade tanımlamak için nesne. Başka bir statik yöntem çağrısında zaten tanımlanmış bir normal ifade deseni kullanıyorsanız, normal ifade altyapısı önbellekten alır. Aksi halde altyapısı normal ifadeyi derlemek ve önbelleğe ekleyin.  
  
-   Mevcut bir yeniden tarafından <xref:System.Text.RegularExpressions.Regex> normal ifade desenine gerekli olduğu sürece nesne.  
  
 Nesne örneklemesini ve normal ifade derleme, oluşturma ve hızlı bir şekilde çok sayıda yok etme yükü nedeniyle <xref:System.Text.RegularExpressions.Regex> nesneleri çok pahalı bir işlemdir. Çok sayıda farklı normal ifadeler kullanan uygulamalar için statik çağrıları kullanarak performans iyileştirebilirsiniz `Regex` yöntemleri ve büyük olasılıkla normal ifade önbellek boyutuna göre artırma.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET normal ifadeler](../../../docs/standard/base-types/regular-expressions.md)
