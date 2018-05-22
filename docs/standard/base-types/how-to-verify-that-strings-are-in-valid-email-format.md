---
title: 'Nasıl yapılır: Dizelerin Geçerli E-Posta Biçiminde Olduğunu Doğrulama'
ms.date: 03/30/2017
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
ms.openlocfilehash: 02c942dea3314581ce8f758bb9ed3ce88c2fe150
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2018
---
# <a name="how-to-verify-that-strings-are-in-valid-email-format"></a>Nasıl yapılır: Dizelerin Geçerli E-Posta Biçiminde Olduğunu Doğrulama
Aşağıdaki örnek, bir dize geçerli e-posta biçiminde olduğunu doğrulamak için normal bir ifade kullanır.  

> [!NOTE]
>  Kullanmanızı öneririz <xref:System.Net.Mail.MailAddress?displayProperty=nameWithType> sınıfı bir dize geçerli e-posta adresi biçiminde olup olmadığını denetleyin. Bunu yapmak için e-posta adresi dizeye geçirmek <xref:System.Net.Mail.MailAddress.%23ctor%28System.String%29?displayProperty=nameWithType> oluşturur sınıfı oluşturucusu bir <xref:System.FormatException> tanınmayan bir biçim dizesine sahipse.  
  
## <a name="example"></a>Örnek  
 Örnek tanımlayan bir `IsValidEmail` döndürür yöntemi `true` dizesi geçerli bir eposta adresi içeriyorsa ve `false` desteklemez ancak başka bir eylemi alır.  
  
 E-posta adresi geçerli olduğunu doğrulamak için `IsValidEmail` yöntem çağrılarını <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> yöntemiyle `(@)(.+)$` etki alanı adı e-posta adresinden ayırmak için normal ifade deseni. Üçüncü parametre bir <xref:System.Text.RegularExpressions.MatchEvaluator> işler ve eşleşen metni değiştirir yöntemi temsil eden temsilci. Normal ifade deseni şu şekilde yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`(@)`|Eşleşme @ karakteri. Bu ilk yakalama grubudur.|  
|`(.+)`|Herhangi bir karakterin bir veya birden çok tekrarı eşleşir. Bu ikinci yakalama grubudur.|  
|`$`|Son dizenin sonunda eşleşmiyor.|  
  
 Etki alanı adı ile birlikte @ karakteri geçirilir `DomainMapper` kullanan yöntemi <xref:System.Globalization.IdnMapping> sınıfı Punycode US-ASCII karakter aralığı dışında olan Unicode karakterler çevir. Metodu ayrıca ayarlar `invalid` bayrağını `True` varsa <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> yöntemi, etki alanı adı geçersiz karakterler algılar. Zayıf kod etki alanı adı öncesinde tarafından yöntemi döndürür @ simgesi `IsValidEmail` yöntemi.  
  
 `IsValidEmail` Sonra yöntemi çağırır <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> adresi bir normal ifade deseni uyduğunu doğrulamak için yöntem.  
  
 Unutmayın `IsValidEmail` yöntemi e-posta adresini doğrulamak için kimlik doğrulaması gerçekleştirmez. Yalnızca kendi biçiminde bir e-posta adresi için geçerli olup olmadığını belirler. Ayrıca, `IsValidEmail` yöntemi en üst düzey etki alanı adı geçerli bir etki alanı adları adresinde listelenmiş olduğunu doğrulamaz [IANA kök bölgesi veritabanı](https://www.iana.org/domains/root/db), bir arama işlemi duyar. Bunun yerine, normal ifade yalnızca üst düzey etki alanı adı ve yirmi dört iki ASCII karakterler, alfasayısal ilk ve son karakterler ve geriye kalan karakterler alfasayısal veya tire ile arasında oluşan olduğunu doğrular (-).  
  
 [!code-csharp[RegularExpressions.Examples.Email#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#7)]
 [!code-vb[RegularExpressions.Examples.Email#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#7)]  
  
 Bu örnekte, normal ifade deseni ``^(?(")(".+?(?<!\\)"@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`{}|~\w])*)(?<=[0-9a-z])@))(?([)([(\d{1,3}.){3}\d{1,3}])|(([0-9a-z][-0-9a-z]*[0-9a-z]*.)+[a-z0-9][-a-z0-9]{0,22}[a-z0-9]))$`` aşağıdaki tabloda gösterildiği gibi yorumlanır. Normal ifade kullanarak derlenir Not <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> bayrağı.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`^`|Eşleşme dizenin başında başlar.|  
|`(?(")`|İlk karakteri bir tırnak işareti olup olmadığını belirler. `(?(")` bir değişim yapısıyla başlangıcıdır.|  
|`(?("")("".+?(?<!\\)""@)`|İlk karakteri bir tırnak işareti ise, en az bir oluşumu bir bitiş tırnak işareti herhangi bir karakterin ardından bir başlangıç tırnağından eşleşmesi. Bitiş tırnağından ters eğik çizgi karakteriyle gelmemelidir (\\). `(?<!` Sıfır Genişlik negatif geriye ilerleme onaylama başlangıcıdır. Dize duymanıza neden bir at işareti (@).|  
|<code>&#124;(([0-9a-z]</code>|İlk karakteri bir tırnak işareti yoksa, alfasayısal bir karakter gelen eşleşen bir-z veya A-Z (karşılaştırma büyük/küçük harfe duyarsız) veya sayısal bir karakterle 0 ile 9 arasında.|  
|`(\.(?!\.))`|Sonraki karakteri bir nokta ise, aynı. Bir süre değilse, devam sonraki karaktere bakın ve eşleşme devam edin. `(?!\.)` bir e-posta adresi yerel bölümünde görünmesini art arda iki nokta engelleyen bir sıfır Genişlik negatif ileri yönlü onayı ifade eder.|  
|<code>&#124;[-!#\$%&'\*\+/=\?\^\`{}\&#124;~\w]</code>|Sonraki karakteri bir süre değilse, herhangi bir sözcük karakteri veya şu karakterlerden birini eşleşen:-! #$% ' * +=? ^\`{}&#124;~.|  
|<code>((\.(?!\.))&#124;[-!#\$%'\*\+/=\?\^\`{}\&#124;~\w])*</code>|(Süre olmayan veya karakter sayısını biri tarafından izlenen bir dönemi) değişim deseni sıfır veya daha çok kez aynı.|  
|`@`|Eşleşme @ karakteri.|  
|`(?<=[0-9a-z])`|Karakter önceyse eşleşme devam A ile Z, A'dan Z'ye veya 0-9 arası karakterdir. `(?<=[0-9a-z])` Yapı Sıfır Genişlik pozitif geriye ilerleme onaylama tanımlar.|  
|`(?(\[)`|@ İzleyen karakterin ayraç olup olmadığını denetleyin.|  
|`(\[(\d{1,3}\.){3}\d{1,3}\])`|Bir açma ayracı ise, ardından bir IP adresi (virgülle ayrılmış her kümesiyle bir ile üç basamak dört ayarlar) ve bir kapanış ayracı ayraç eşleşmesi.|  
|<code>&#124;(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+</code>|@ İzleyen karakterin eşleşen bir alfasayısal karakter, A-z, bir değerle bir açılış ayracı değilse, a-z veya 0-9, bir tire sıfır veya daha çok tekrarı tarafından izlenen ve ardından sıfır veya bir alfasayısal bir karakterle değeri, A-Z, a-z veya 0-9 , ardından bir noktayla. Bu desen bir veya daha çok sayıda Tekrarlanmış ve ardından üst düzey etki alanı adı olmalıdır.|  
|`[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))`|Üst düzey etki alanı ad başlamalı ve bitmelidir alfasayısal bir karakterle (a-z, A-Z ve 0-9). Ayrıca sıfır ya da olan 22 ASCII karakterleri içerebilir alfasayısal veya kısa çizgi.|  
|`$`|Son dizenin sonunda eşleşmiyor.|  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 `IsValidEmail` Ve `DomainMapper` yöntemleri normal ifade yardımcı program yöntemleri kitaplıkta dahil edilebilir ya da bunlar özel statik veya örnek uygulama sınıfı yöntemleri olarak dahil edilebilir.  
  
 Normal ifade kitaplığa eklemek için ya da kopyalayın ve Visual Studio sınıf kitaplığı projeye kodu yapıştırın veya kopyalayıp bir metin dosyasına yapıştırın ve aşağıdaki gibi bir komutla komut satırından derleme (varsayılarak kaynak kodunun adı  RegexUtilities.cs veya RegexUtilities.vb dosyadır:  
  
```csharp  
csc /t:library RegexUtilities.cs  
```  
  
```vb  
vbc /t:library RegexUtilities.vb  
```  
  
 Aynı zamanda <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> yöntemi bir normal ifade kitaplığa normal ifade.  
  
 Bunlar bir normal ifade kitaplığında kullanılıyorsa, aşağıdaki gibi kod çağırabilirsiniz:  
  
 [!code-csharp[RegularExpressions.Examples.Email#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#8)]
 [!code-vb[RegularExpressions.Examples.Email#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#8)]  
  
 E-posta doğrulama normal ifade içeren RegexUtilities.dll adlı bir sınıf kitaplığı oluşturduğunuz varsayıldığında, bu örnekte, aşağıdaki iki yoldan biriyle hazırlayabilirsiniz:  
  
-   Görsel bir konsol uygulaması oluşturma ve projenize RegexUtilities.dll bir başvuru ekleyerek Studio'da.  
  
-   Komut satırından kopyalayarak ve kaynak kodunu metin dosyasında kopyalayıp yapıştırarak ve aşağıdaki gibi bir komutu ile derleme (kaynak kodu dosyasının adını Example.cs veya Example.vb olduğu varsayılarak:  
  
    ```csharp  
    csc Example.cs /r:RegexUtilities.dll  
    ```  
  
    ```vb  
    vbc Example.vb /r:RegexUtilities.dll  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [.NET framework normal ifadeleri](../../../docs/standard/base-types/regular-expressions.md)
