---
title: Dizelerin geçerli e-posta biçiminde olduğunu doğrulama
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
ms.openlocfilehash: c02fc215fa66951ae3333175191ab96a226a2afe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73197587"
---
# <a name="how-to-verify-that-strings-are-in-valid-email-format"></a>Dizelerin geçerli e-posta biçiminde olduğunu doğrulama

Aşağıdaki örnek, bir dize geçerli e-posta biçiminde olduğunu doğrulamak için normal bir ifade kullanır.

## <a name="example"></a>Örnek

Örnek, dize `IsValidEmail` geçerli bir `true` e-posta adresi içeriyorsa ve `false` yoksa döndüren, ancak başka bir işlem yapamayan bir yöntem tanımlar.

E-posta adresinin geçerli olduğunu `IsValidEmail` doğrulamak <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> için yöntem, etki alanı adını e-posta adresinden ayırmak için `(@)(.+)$` normal ifade deseniyle yöntemi çağırır. Üçüncü parametre, <xref:System.Text.RegularExpressions.MatchEvaluator> eşleşen metni işleyen ve değiştiren yöntemi temsil eden bir temsilcidir. Normal ifade deseni aşağıdaki gibi yorumlanır.

|Desen|Açıklama|
|-------------|-----------------|
|`(@)`|@ karakterini eşleştirin. Bu ilk yakalama grubudur.|
|`(.+)`|Herhangi bir karakterin bir veya daha fazla olayını eşleştirin. Bu ikinci yakalama grubudur.|
|`$`|Dize sonunda maç sona erdirin.|

@ karakteri ile birlikte etki alanı `DomainMapper` adı Punycode <xref:System.Globalization.IdnMapping> IÇIN ABD-ASCII karakter aralığı dışında Unicode karakterleri çevirmek için sınıf kullanan yönteme geçirilir. Yöntem, etki `invalid` alanı `True` adında <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> geçersiz karakterler algılarsa bayrağı da ayarlar. Yöntem, @ sembolünden önceki Punycode etki alanı `IsValidEmail` adını yönteme döndürür.

Yöntem `IsValidEmail` daha sonra, adresin <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> normal bir ifade desenine uydurluğunu doğrulamak için yöntemi çağırır.

Yöntemin `IsValidEmail` e-posta adresini doğrulamak için kimlik doğrulaması gerçekleştirmediğini unutmayın. Yalnızca biçiminin bir e-posta adresi için geçerli olup olmadığını belirler. Buna ek `IsValidEmail` olarak, yöntem üst düzey etki alanı adının [IANA Kök Bölgesi Veritabanı'nda](https://www.iana.org/domains/root/db)listelenen geçerli bir etki alanı adı olduğunu doğrulamaz, bu da bir arama işlemi gerektirir. Bunun yerine, normal ifade yalnızca üst düzey etki alanı adının alfasayısal birinci ve son karakterler ve kalan karakterler alfasayısal veya tire (-) olmak üzere iki ila yirmi dört ASCII karakterden oluştuğunu doğrular.

[!code-csharp[RegularExpressions.Examples.Email#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#7)]
[!code-vb[RegularExpressions.Examples.Email#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#7)]

Bu örnekte, normal ``^(?(")(".+?(?<!\\)"@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*)(?<=[0-9a-z])@))(?(\[)(\[(\d{1,3}\.){3}\d{1,3}\])|(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))$`` ifade deseni aşağıdaki göstergede gösterildiği gibi yorumlanır. Normal ifade <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> bayrak kullanılarak derlenir.

Desen `^`: Dize başında maç başlar.

Desen `(?(")`: İlk karakterin tırnak işareti olup olmadığını belirleyin. `(?(")`bir değişim yapısının başlangıcıdır.

Desen `(?(")(".+?(?<!\\)"@)`: İlk karakter bir tırnak işaretiyse, bir başlangıç tırnak işaretini eşleştirin ve ardından herhangi bir karakterin en az bir oluşumunu ve ardından bitiş tırnak işaretini eşleştirin. Bitiş tırnak işareti bir ters eğik çizgi karakteri\\( ) önce olmamalıdır. `(?<!`sıfır genişlikteki negatif bir bakış iddiasının başlangıcıdır. Dize bir at işareti (@) ile sonuçlandırılmalıdır.

Desen `|(([0-9a-z]`: İlk karakter bir tırnak işareti değilse, a'dan z'ye veya A'dan Z'ye herhangi bir alfabetik karakteri (karşılaştırma duyarsız dır) veya 0'dan 9'a kadar sayısal bir karakterle eşleştirin.

Desen `(\.(?!\.))`: Bir sonraki karakter bir dönemse, eşleştirin. Bu bir dönem değilse, bir sonraki karaktere bakın ve maça devam edin. `(?!\.)`bir e-posta adresinin yerel bölümünde görünmesini iki ardışık dönem engelleyen sıfır genişliknegatif ileriye dönük bir iddiadır.

Desen ``|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w]``: Bir sonraki karakter bir nokta değilse, herhangi bir sözcük karakteri yle veya\*aşağıdaki karakterlerden\`{}biriyle eşleşin: -!#$%&' +/=?^ |~

Desen ``((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*``: Sıfır veya daha fazla kez değiştirme desenini (bir dönem, bir dönem veya bir karakter sayısından biri) eşleştirin.

Desen `@`: @ karakteri eşleştirin.

Desen `(?<=[0-9a-z])`: @ karakterinden önce gelen karakter A'dan Z'ye, a'dan z'ye veya 0'dan 9'a kadar ise maça devam edin. Bu desen, sıfır genişlikpozitif görünüm iddiasını tanımlar.

Desen `(?(\[)`: @'yi izleyen karakterin bir açılım ayraç olup olmadığını kontrol edin.

Desen `(\[(\d{1,3}\.){3}\d{1,3}\])`: Bir açılım ayraç ise, bir IP adresi (her bir set bir döneme ayrılmış dört set) ve bir kapanış ayraç ardından açılış braketi eşleştirin.

Desen `|(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+`: @'ı izleyen karakter bir açılış parantezi değilse, bir alfanümerik karakteri A-Z, a-z veya 0-9 değeriyle eşleştirin, ardından bir tirenin sıfır veya daha fazla oluşumunu, ardından a-Z, a-z veya 0-9 değerine sahip sıfır veya bir alfasayısal karakter, ardından bir dönem gelir. Bu desen bir veya daha fazla kez yinelenebilir ve üst düzey etki alanı adı tarafından izlenmelidir.

Desen `[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))`: Üst düzey etki alanı adı alfasayısal bir karakter (a-z, A-Z ve 0-9) ile başlamalı ve bitmelidir. Ayrıca alfasayısal veya tire olan sıfırdan 22 ASCII karakter içerebilir.

Desen `$`: Eşleşmeyi dize sonunda bitirin.

## <a name="compile-the-code"></a>Kodu derleme

Ve `IsValidEmail` `DomainMapper` yöntemleri düzenli ifade yardımcı yöntemleri bir kitaplık dahil edilebilir, ya da uygulama sınıfında özel statik veya örnek yöntemleri olarak dahil edilebilir.

Bu normal ifadeyi normal bir ifade kitaplığına eklemek için <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> yöntemi de kullanabilirsiniz.

Normal bir ifade kitaplığında kullanılırsa, aşağıdaki gibi bir kod kullanarak onları arayabilirsiniz:

[!code-csharp[RegularExpressions.Examples.Email#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#8)]
[!code-vb[RegularExpressions.Examples.Email#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#8)]

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework Normal İfadeleri](../../../docs/standard/base-types/regular-expressions.md)
