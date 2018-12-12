---
title: 'Nasıl Yapılır: Dizelerin geçerli e-posta biçiminde olduğunu doğrulama'
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
ms.openlocfilehash: 9ed0721f2bfa8e272822740cf26173c1592de428
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236654"
---
# <a name="how-to-verify-that-strings-are-in-valid-email-format"></a>Nasıl Yapılır: Dizelerin geçerli e-posta biçiminde olduğunu doğrulama
Aşağıdaki örnek, bir dize geçerli bir e-posta biçiminde olduğunu doğrulamak için normal bir ifade kullanır.  

## <a name="example"></a>Örnek  
 Örnek tanımlayan bir `IsValidEmail` döndüren yöntemi `true` dize geçerli bir eposta adresi içeriyorsa ve `false` desteklemez ancak başka işlem yapmaz.  
  
 E-posta adresinin geçerli olduğunu doğrulamak için `IsValidEmail` yöntem çağrılarını <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> yöntemiyle `(@)(.+)$` etki alanı adı e-posta adresinden ayırmak için normal ifade deseni. Üçüncü parametre bir <xref:System.Text.RegularExpressions.MatchEvaluator> işler ve eşleştirilen metni değiştiren yöntemi temsil eden bir temsilci. Normal ifade deseni aşağıdaki gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`(@)`|Eşleşme @ karakteri. Bu ilk yakalama grubudur.|  
|`(.+)`|Herhangi bir karakteri bir veya daha fazla oluşumunu eşleyin. Bu ikinci yakalama grubudur.|  
|`$`|Dizenin sonunda eşleştirmeyi sonlandır.|  
  
 Etki alanı adı ile birlikte @ karakteri geçirilir `DomainMapper` kullanan yöntemi <xref:System.Globalization.IdnMapping> punycode'a US-ASCII karakter aralığı dışındaki Unicode karakterleri çevirmek için sınıf. Yöntemi ayrıca ayarlar `invalid` bayrak `True` varsa <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> yöntemi, etki alanı adında geçersiz karakterler algılarsa. Punycode etki alanı adı öncesinde yöntem döndürür @ simgesiyle `IsValidEmail` yöntemi.  
  
 `IsValidEmail` Sonra yöntemi çağırır <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> adresi bir normal ifade desenine uyduğunu doğrulamak için yöntem.  
  
 Unutmayın `IsValidEmail` yöntemi, e-posta adresinizi doğrulamak için kimlik doğrulaması gerçekleştirmez. Yalnızca kendi biçiminde bir e-posta adresi için geçerli olup olmadığını belirler. Ayrıca, `IsValidEmail` yöntemi üst düzey etki alanı adının listelenmiş geçerli etki alanı adı olduğunu doğrulamaz [IANA Root Zone Database](https://www.iana.org/domains/root/db), bir arama işlemi gerektirir. Bunun yerine, normal ifade yalnızca en üst düzey etki alanı adı, iki ve yirmi dört ASCII karakter uzunluğunda ilk ve son karakter alfasayısal ve alfasayısal veya tire kalan karakter bulundurduğunu doğrular (-).  
  
 [!code-csharp[RegularExpressions.Examples.Email#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#7)]
 [!code-vb[RegularExpressions.Examples.Email#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#7)]  
  
 Bu örnekte, normal ifade deseni ``^(?(")(".+?(?<!\\)"@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`{}|~\w])*)(?<=[0-9a-z])@))(?([)([(\d{1,3}.){3}\d{1,3}])|(([0-9a-z][-0-9a-z]*[0-9a-z]*.)+[a-z0-9][-a-z0-9]{0,22}[a-z0-9]))$`` aşağıdaki tabloda gösterildiği gibi yorumlanır. Normal ifade kullanılarak derlenmiş olduğuna dikkat edin <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> bayrağı.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`^`|Dizesinin başında eşleşmeye başla.|  
|`(?(")`|İlk karakter bir tırnak işareti olup olmadığını belirler. `(?(")` Değişim yapısının başlangıcıdır.|  
|`(?("")("".+?(?<!\\)""@)`|İlk karakter bir tırnak işareti ise, en az bir bitiş tırnak işaretinden sonra herhangi bir karakter, oluşumunu ardından bir başlangıç tırnağından eşleştirin. Bir ters eğik çizgi karakteriyle bitiş tırnak işareti gelmemelidir (\\). `(?<!` bir sıfır Genişlik negatif geriye yönelik onaydır başlangıcıdır. Dizenin sonunda bir at işareti (@).|  
|<code>&#124;(([0-9a-z]</code>|İlk karakter bir tırnak işareti değil ise, gelen alfabetik bir karakterle eşleşen bir-z veya A (karşılaştırma büyük/küçük harfe duyarsız) Z ya da herhangi bir sayısal karakter 0-9.|  
|`(\.(?!\.))`|Sonraki karakteri bir nokta ise, eşleştirin. Bir nokta değil ise, önceden sonraki karaktere bakın ve eşleştirmeyi devam ettirin. `(?!\.)` Art arda iki bir e-posta adresinin yerel kısmında görünmesini engelleyen bir sıfır Genişlik negatif ileriye yönelik olaydır.|  
|<code>&#124;[-!#\$%&'\*\+/=\?\^\`{}\&#124;~\w]</code>|Sonraki karakteri bir nokta değil ise, herhangi bir sözcük karakteri veya şu karakterlerden birini eşleşen:-! #$% ' * +=? ^\`{}&#124;~.|  
|<code>((\.(?!\.))&#124;[-!#\$%'\*\+/=\?\^\`{}\&#124;~\w])*</code>|Değişim deseni (süre olmayan veya karakter sayısını biri tarafından izlenen bir nokta) sıfır veya daha fazla kez eşleştirin.|  
|`@`|Eşleşme @ karakteri.|  
|`(?<=[0-9a-z])`|Karakter önceyse eşleştirmeyi devam ettirin. A-Z, A'dan Z'ye veya 0-9 @ karakterdir. `(?<=[0-9a-z])` Yapısı, sıfır genişlik pozitif geriye yönelik onayı tanımlar.|  
|`(?(\[)`|@ İzleyen karakterin açılış ayracı olup olmadığını denetleyin.|  
|`(\[(\d{1,3}\.){3}\d{1,3}\])`|Açılış ayracı olup, ardından bir IP adresi (en fazla üç basamaklı, birbirinden noktayla ayrılmış her bir kümesi oluşan dört küme) ve köşeli sağ ayraç ayraç eşleştirin.|  
|<code>&#124;(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+</code>|Aşağıdaki @ karakteri bir alfasayısal karakter değeri A-Z, eşleşen bir açma ayracı değilse, a-z veya 0-9, tire, sıfır veya daha çok tekrarı tarafından izlenen arkasından sıfır veya bir alfasayısal karakter değeri A-z, a-z veya 0-9 , bir nokta. Bu düzen, bir veya daha fazla kez yinelenen ve üst düzey etki alanı adından önce gelen gerekir.|  
|`[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))`|Üst düzey etki alanı adı başlamalı ve bitmelidir alfasayısal bir karakterle (a-z, A-Z ve 0-9). Ayrıca sıfır olan 22 ASCII karakter içerebilir alfasayısal veya kısa çizgi.|  
|`$`|Dizenin sonunda eşleştirmeyi sonlandır.|  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 `IsValidEmail` Ve `DomainMapper` yöntemleri bir normal ifade yardımcı program yöntemleri kitaplıkta dahil edilebilir ya da bunlar özel statik veya uygulama sınıfında örnek yöntemler olarak eklenebilir.  
  
 Bir normal ifade kitaplığında eklemek için ya da kopyalayın kodu bir Visual Studio sınıf kitaplığı projesine yapıştırın veya kopyalayın ve bir metin dosyasına yapıştırın ve aşağıdakine benzer bir komut ile komut satırından derleme (varsayarak kaynak kodunun adı  RegexUtilities.cs veya RegexUtilities.vb dosyasıdır:  
  
```csharp  
csc /t:library RegexUtilities.cs  
```  
  
```vb  
vbc /t:library RegexUtilities.vb  
```  
  
 Ayrıca <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> bu normal ifade bir normal ifade kitaplığında dahil etmek için yöntemi.  
  
 Bir normal ifade kitaplığında kullanılıyorsa aşağıdaki gibi kod kullanarak bunları çağırabilirsiniz:  
  
 [!code-csharp[RegularExpressions.Examples.Email#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#8)]
 [!code-vb[RegularExpressions.Examples.Email#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#8)]  
  
 E-posta doğrulama normal ifade içeren RegexUtilities.dll adlı bir sınıf kitaplığı oluşturduğunuz varsayıldığında, bu örnekte, aşağıdaki yollardan biriyle derleyebilirsiniz:  
  
-   Görsel bir konsol uygulaması oluşturma ve projenize bir başvuru RegexUtilities.dll ekleyerek Studio'da.  
  
-   Kopyalama ve kaynak kodu bir metin dosyasına kopyalayıp yapıştırarak aşağıdakine benzer bir komut ile derleme komut satırından (kaynak kodu dosyasının adını Example.cs veya Example.vb olduğunu varsayarak:  
  
    ```csharp  
    csc Example.cs /r:RegexUtilities.dll  
    ```  
  
    ```vb  
    vbc Example.vb /r:RegexUtilities.dll  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET framework normal ifadeleri](../../../docs/standard/base-types/regular-expressions.md)
