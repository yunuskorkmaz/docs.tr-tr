---
title: "Normal İfadelerde Derleme ve Yeniden Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 230a1b8b083362c149b5b7e64f708bd09ab21788
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="compilation-and-reuse-in-regular-expressions"></a>Normal İfadelerde Derleme ve Yeniden Kullanma
Normal ifadeler kapsamlı kullanımını nasıl normal ifade altyapı ifadeleri derler anlama ve nasıl normal ifadeler önbelleğe alınan anlama olun uygulamaların performansını en iyi duruma getirebilirsiniz. Bu konuda, hem derleme hem de önbelleğe alma anlatılmaktadır.  
  
## <a name="compiled-regular-expressions"></a>Derlenmiş normal ifadeler  
 Varsayılan olarak, normal ifade altyapısı bir dizisine normal bir ifade iç yönergeleri (Microsoft Ara dili veya MSIL farklı üst düzey kodları bunlar) derler. Altyapı normal bir ifade yürütüldüğünde, iç kodları yorumlar.  
  
 Varsa bir <xref:System.Text.RegularExpressions.Regex> nesnesi ile yapılandırılmıştır <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> seçeneği, üst düzey normal ifade iç yönergeler yerine açık MSIL kod normal ifadeye derler. Bu izin verir. Daha yüksek performans için yerel makine kod ifadeyi dönüştürmek için tam zamanında (JIT) derleyici NET'in.  
  
Ancak, oluşturulan MSIL kaldırılamıyor. Tüm uygulama etki alanını kaldırmak için kod kaldırmak için tek yolu olduğundan (diğer bir deyişle, tüm uygulamanızın kaldırmak için kullanıcının kodu.). Etkili bir şekilde bir normal ifade ile derlenen bir kez <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> seçeneği, normal ifade tarafından oluşturulan olsa bile hiçbir zaman derlenmiş ifade tarafından kullanılan kaynakları serbest bir <xref:System.Text.RegularExpressions.Regex> kendisi çöp toplama yayımlanan nesnesi.  
  
 Derleme ile farklı normal ifadeler sayısını sınırlamak dikkatli olmanız gerekir <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> çok fazla kaynak tüketen önlemek için seçeneği. Uygulamanın normal ifadeler büyük ya da sınırsız sayısı kullanmanız gerekiyorsa, her bir ifadenin, derlenmemiş yorumlanması gerektiğini. Normal ifadeler az sayıda sürekli olarak kullanılıyorsa, ancak bunlar ile derlenip <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> daha iyi performans için. Önceden derlenmiş normal ifadeler kullanmaya alternatiftir. Yeniden kullanılabilir DLL, ifadelere tümünün kullanarak derleme <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A> yöntemi. Bu, çalışma zamanında derlenen normal ifadeler hızından hala benefiting sırasında derlemek için gereken önler.  
  
## <a name="the-regular-expressions-cache"></a>Normal ifadeler önbelleği  
 Performansı artırmak için normal ifade altyapısı derlenmiş normal ifadeler, bir uygulama çapında önbelleğini korur. Önbelleği yalnızca statik yöntem çağrılarında kullanılan normal ifade desenleri depolar. (Örnek yöntemleri için sağlanan normal ifade desenleri önbelleğe alınmaz.) Bir ifadeyi üst düzey bayt kodu her kullanılışında yeniden ayrıştırma gerek önler.  
  
 Önbelleğe alınan normal ifadeler maksimum sayısı değeri tarafından belirlenir `static` (`Shared` Visual Basic'te) <xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=nameWithType> özelliği. Varsayılan olarak, normal ifade altyapısı en fazla 15 derlenmiş normal ifadeler önbelleğe alır. Derlenmiş normal ifadeler sayısı önbellek boyutunu aşarsa, yakın zamanda kullanılmamış normal ifade atılır ve yeni normal ifade önbelleğe alınır.  
  
 Uygulamanızı önceden derlenmiş normal ifadeler aşağıdaki iki yoldan biriyle yararlanabilirsiniz:  
  
-   Statik bir yöntemi kullanarak <xref:System.Text.RegularExpressions.Regex> normal ifade tanımlamak için nesne. Normal ifade altyapısı başka bir statik yöntem çağrısında zaten tanımlanmış bir normal ifade deseni kullanıyorsanız, önbellekten alır. Aksi durumda, altyapı normal ifade derlemek ve önbelleğe ekleyin.  
  
-   Var olan yeniden tarafından <xref:System.Text.RegularExpressions.Regex> , normal ifade deseni gerekli olduğu sürece nesne.  
  
 Nesne Örneğini Oluşturmada ve oluşturma ve hızla çok sayıda yok etme normal ifade derleme yükünden nedeniyle <xref:System.Text.RegularExpressions.Regex> nesnedir çok pahalı bir işlem. Çok sayıda farklı normal ifadeler kullanan uygulamalar için statik çağrıları kullanarak performansını iyileştirebilirsiniz `Regex` yöntemleri ve büyük olasılıkla göre normal ifade önbellek boyutunu artırma.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [.NET normal ifadeler](../../../docs/standard/base-types/regular-expressions.md)
