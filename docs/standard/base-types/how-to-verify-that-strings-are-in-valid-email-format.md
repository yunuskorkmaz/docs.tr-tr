---
title: 'Nasıl yapılır: Dizelerin Geçerli E-Posta Biçiminde Olduğunu Doğrulama'
ms.date: 12/10/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, examples
- user input, examples
- Regex.IsMatch method
- regular expressions [.NET Framework], examples
- examples [Visual Basic], strings
- IsValidEmail
- validation, email strings
- input, checking
- strings [.NET Framework], examples [Visual Basic]
- email [.NET Framework], validating
- IsMatch method
ms.assetid: 7536af08-4e86-4953-98a1-a8298623df92
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f6381747bc998f73b374442fcb15e025ca15795d
ms.sourcegitcommit: 46c68557bf6395f0ab9915f7558f2faae0097695
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2019
ms.locfileid: "65589530"
---
# <a name="how-to-verify-that-strings-are-in-valid-email-format"></a>Nasıl yapılır: Dizelerin Geçerli E-Posta Biçiminde Olduğunu Doğrulama
Aşağıdaki örnek bir dizenin geçerli e-posta biçiminde olduğunu doğrulamak için normal bir ifade kullanır.  

## <a name="example"></a>Örnek  
 Örnek, dize geçerli `IsValidEmail` bir e-posta `true` adresi içeriyorsa ve `false` yoksa ancak başka bir eylem içermiyorsa döndüren bir yöntemi tanımlar.  
  
 E-posta adresinin geçerli `IsValidEmail` olduğunu doğrulamak için yöntemi, etki alanı adını e-posta adresinden ayırmak üzere `(@)(.+)$` normal ifade düzeniyle <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> yöntemi çağırır. Üçüncü parametre, eşleşen metni <xref:System.Text.RegularExpressions.MatchEvaluator> işleyen ve değiştiren yöntemi temsil eden bir temsilcisidir. Normal ifade deseninin aşağıdaki şekilde yorumlanması.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`(@)`|@ Karakteriyle eşleştirin. Bu ilk yakalama grubudur.|  
|`(.+)`|Herhangi bir karakterin bir veya daha fazla tekrarı ile eşleştirin. Bu ikinci yakalama grubudur.|  
|`$`|Dizenin sonundaki eşleşmeyi sonlandırın.|  
  
 @ Karakteriyle birlikte etki alanı adı `DomainMapper` yöntemine geçirilir ve bu, US-ASCII karakter aralığının dışındaki Unicode karakterleri, punyıcode 'a dönüştürmek için <xref:System.Globalization.IdnMapping> sınıfını kullanır. Yöntemi, <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> yöntemi etki alanı `invalid` adında geçersiz `True` karakterler algılarsa, bayrağını da ayarlar. Yöntemi, önüne @ simgesinden `IsValidEmail` önce gelen punyıcode etki alanı adını döndürür.  
  
 Yöntemi daha sonra, adresin <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> bir normal ifade düzenine uygun olduğunu doğrulamak için yöntemini çağırır. `IsValidEmail`  
  
 `IsValidEmail` Yönteminin, e-posta adresini doğrulamak için kimlik doğrulaması gerçekleştirmediğini unutmayın. Yalnızca biçiminin bir e-posta adresi için geçerli olup olmadığını belirler. Ayrıca `IsValidEmail` Yöntem, üst düzey etki alanı adının, [IANA kök bölgesi veritabanında](https://www.iana.org/domains/root/db)listelenen geçerli bir etki alanı adı olduğunu doğrulamaz, bu da bir arama işlemi gerektirir. Bunun yerine, normal ifade yalnızca en üst düzey etki alanı adının, alfasayısal ve son karakterlerden oluşan iki ve Yirmi dört ASCII karakterden oluştuğunu doğrular ve geri kalan karakterlerin alfasayısal ya da kısa çizgi (-) olacağını doğrular.  
  
 [!code-csharp[RegularExpressions.Examples.Email#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#7)]
 [!code-vb[RegularExpressions.Examples.Email#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#7)]  
  
 Bu örnekte, normal ifade deseninin ``^(?(")(".+?(?<!\\)"@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`{}|~\w])*)(?<=[0-9a-z])@))(?([)([(\d{1,3}.){3}\d{1,3}])|(([0-9a-z][-0-9a-z]*[0-9a-z]*.)+[a-z0-9][-a-z0-9]{0,22}[a-z0-9]))$`` aşağıdaki tabloda gösterildiği gibi yorumlanır. Normal ifadenin <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> bayrak kullanılarak derlendiğini unutmayın.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`^`|Dizenin başlangıcında eşleşmeyi başlatın.|  
|`(?(")`|İlk karakterin bir tırnak işareti olup olmadığını belirleme. `(?(")`, değişim yapısının başlangıcıdır.|  
|`(?("")("".+?(?<!\\)""@)`|İlk karakter bir tırnak işareti ise, bir başlangıç tırnak işaretiyle, ardından herhangi bir karakterin en az bir örneğinden ve ardından bir bitiş tırnak işaretiyle eşleştirin. Bitiş tırnak işareti önünde ters eğik çizgi karakteri (\\) olmamalıdır. `(?<!`Sıfır Genişlik negatif geriye yönelik bir onaylama işlemi başlangıcının başlangıcıdır. Dize bir at işareti (@) ile sona ermelidir.|  
|<code>&#124;(([0-9a-z]</code>|İlk karakter bir tırnak işareti değilse, a 'dan z 'ye veya A 'dan Z 'ye (karşılaştırma büyük/küçük harfe duyarsız) veya 0 ile 9 arasında bir sayısal karakter eşleştirin.|  
|`(\.(?!\.))`|Sonraki karakter bir nokta ise, bunu eşleştirin. Bir nokta değilse, sonraki karaktere bakın ve eşleştirmeye devam edin. `(?!\.)`, iki ardışık dönemin bir e-posta adresinin yerel bölümünde görünmesini engelleyen sıfır Genişlik negatif ileriye yönelik bir onaylama işlemi.|  
|<code>&#124;[-!#\$%&'\*\+/=\?\^\`{}&#124;~\w]</code>|Sonraki karakter bir nokta değilse, herhangi bir sözcük karakteri veya şu karakterlerden birini eşleştirin:-! # $% ' * + =? ^\`{}&#124;~.|  
|<code>((\.(?!\.))&#124;[-!#\$%'\*\+/=\?\^\`{}&#124;~\w])*</code>|Değişim düzeniyle (bir dönem ve sonra dönem olmayan bir nokta veya karakter sayısından biri) sıfır veya daha fazla kez eşleştirin.|  
|`@`|@ Karakteriyle eşleştirin.|  
|`(?<=[0-9a-z])`|@ Karakterinden önce gelen karakter bir-Z, a-z veya 0 ile 9 arasında bir karakter ise eşleştirmeye devam edin. `(?<=[0-9a-z])` Yapı sıfır genişlikli pozitif geriye yönelik bir onaylama işlemi tanımlar.|  
|`(?(\[)`|@ Sözcüğünden sonraki karakterin bir açılış ayracı olup olmadığını denetleyin.|  
|`(\[(\d{1,3}\.){3}\d{1,3}\])`|Bir açma köşeli ayracı ise, açma köşeli ayracından sonra bir IP adresi (her bir noktayla ayırarak dört adet, üç basamaklı dört küme kümesi) ve bir kapanış ayracı eşleştirin.|  
|<code>&#124;(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+</code>|@ ' İ izleyen karakter bir açma köşeli ayracı değilse, bir alfasayısal karakteri A-Z, a-z veya 0-9 ile eşleştirin, ardından sıfır veya daha fazla tire ile, sıfırdan sonra sıfır veya bir alfasayısal karakter ile-Z, a-z veya 0-9 değerli , ardından bir nokta gelir. Bu kalıp bir veya daha fazla kez tekrarlanabilir ve ardından üst düzey etki alanı adı gelmelidir.|  
|`[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))`|En üst düzey etki alanı adı alfasayısal bir karakterle başlamalı ve bitmelidir (a-z, A-Z ve 0-9). Ayrıca, alfasayısal veya kısa çizgi olan sıfır ile 22 ASCII karakter arasında da olabilir.|  
|`$`|Dizenin sonundaki eşleşmeyi sonlandırın.|  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 `IsValidEmail` Ve`DomainMapper` yöntemleri bir normal ifade yardımcı programı yöntemlerine dahil edilebilir veya uygulama sınıfına özel statik veya örnek yöntemleri olarak dahil edilebilir.  
  
 Bu normal ifade bir normal <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> ifade kitaplığına dahil etmek için yöntemini de kullanabilirsiniz.  
  
 Bunlar bir normal ifade kitaplığında kullanılıyorsa, bunları aşağıdaki gibi bir kod kullanarak çağırabilirsiniz:  
  
 [!code-csharp[RegularExpressions.Examples.Email#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#8)]
 [!code-vb[RegularExpressions.Examples.Email#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#8)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Normal Ifadeleri .NET Framework](../../../docs/standard/base-types/regular-expressions.md)
