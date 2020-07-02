---
title: Dizelerin geçerli e-posta biçiminde olduğunu doğrulama
description: Normal bir ifadenin, dizelerin .NET 'teki geçerli bir e-posta biçiminde olduğunu nasıl doğrulayadığına ilişkin bir örnek okuyun.
ms.date: 06/30/2020
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
ms.openlocfilehash: d303c13dead6b4ba29cb7476c2a9b382a9395aff
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803202"
---
# <a name="how-to-verify-that-strings-are-in-valid-email-format"></a>Dizelerin geçerli e-posta biçiminde olduğunu doğrulama

Aşağıdaki örnek bir dizenin geçerli e-posta biçiminde olduğunu doğrulamak için normal bir ifade kullanır.

[!INCLUDE [regex](../../../includes/regex.md)]

## <a name="example"></a>Örnek

Örnek, `IsValidEmail` `true` dize geçerli bir e-posta adresi içeriyorsa ve yoksa ancak başka bir eylem içermiyorsa döndüren bir yöntemi tanımlar `false` .

E-posta adresinin geçerli olduğunu doğrulamak için yöntemi, `IsValidEmail` <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> `(@)(.+)$` etki alanı adını e-posta adresinden ayırmak üzere normal ifade düzeniyle yöntemi çağırır. Üçüncü parametre, <xref:System.Text.RegularExpressions.MatchEvaluator> eşleşen metni işleyen ve değiştiren yöntemi temsil eden bir temsilcisidir. Normal ifade deseninin aşağıdaki şekilde yorumlanması.

|Desen|Açıklama|
|-------------|-----------------|
|`(@)`|@ Karakteriyle eşleştirin. Bu ilk yakalama grubudur.|
|`(.+)`|Herhangi bir karakterin bir veya daha fazla tekrarı ile eşleştirin. Bu ikinci yakalama grubudur.|
|`$`|Dizenin sonundaki eşleşmeyi sonlandırın.|

@ Karakteriyle birlikte etki alanı adı yöntemine geçirilir ve bu, `DomainMapper` <xref:System.Globalization.IdnMapping> US-ASCII karakter aralığının dışındaki Unicode karakterleri, Punyıcode 'a dönüştürmek için sınıfını kullanır. Yöntemi, `invalid` `True` <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> yöntemi etki alanı adında geçersiz karakterler algılarsa, bayrağını da ayarlar. Yöntemi, önüne @ simgesinden önce gelen Punyıcode etki alanı adını döndürür `IsValidEmail` .

`IsValidEmail`Yöntemi daha sonra, <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> adresin bir normal ifade düzenine uygun olduğunu doğrulamak için yöntemini çağırır.

`IsValidEmail`Yönteminin, e-posta adresini doğrulamak için kimlik doğrulaması gerçekleştirmediğini unutmayın. Yalnızca biçiminin bir e-posta adresi için geçerli olup olmadığını belirler. Ayrıca `IsValidEmail` Yöntem, üst düzey etki alanı adının, [IANA kök bölgesi veritabanında](https://www.iana.org/domains/root/db)listelenen geçerli bir etki alanı adı olduğunu doğrulamaz, bu da bir arama işlemi gerektirir. Bunun yerine, normal ifade yalnızca en üst düzey etki alanı adının, alfasayısal ve son karakterlerden oluşan iki ve Yirmi dört ASCII karakterden oluştuğunu doğrular ve geri kalan karakterlerin alfasayısal ya da kısa çizgi (-) olacağını doğrular.

[!code-csharp[RegularExpressions.Examples.Email#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#7)]
[!code-vb[RegularExpressions.Examples.Email#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#7)]

Bu örnekte, normal ifade deseninin ``^(?(")(".+?(?<!\\)"@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*)(?<=[0-9a-z])@))(?(\[)(\[(\d{1,3}\.){3}\d{1,3}\])|(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))$`` aşağıdaki göstergede gösterildiği gibi yorumlanacaktır. Normal ifade, bayrağı kullanılarak derlenir <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> .

Model `^` : dizenin başlangıcında eşleşmeyi Başlat.

Model `(?(")` : ilk karakterin bir tırnak işareti olup olmadığını belirleme. `(?(")`, değişim yapısının başlangıcıdır.

Model `(?(")(".+?(?<!\\)"@)` : ilk karakter bir tırnak işareti ise, bir başlangıç tırnak işaretiyle, ardından herhangi bir karakterin en az bir örneğinden ve ardından bir bitiş tırnak işaretiyle eşleştirin. Bitiş tırnak işareti önünde ters eğik çizgi karakteri ( \\ ) olmamalıdır. `(?<!`Sıfır Genişlik negatif geriye yönelik bir onaylama işlemi başlangıcının başlangıcıdır. Dize bir at işareti (@) ile sona ermelidir.

Model `|(([0-9a-z]` : ilk karakter bir tırnak işareti değilse, a 'dan z 'ye veya a 'Dan z 'ye (karşılaştırma büyük/küçük harfe duyarsız) veya 0 ile 9 arasında bir sayısal karakter eşleştirin.

Model `(\.(?!\.))` : sonraki karakter bir nokta ise, bunu eşleştirin. Bir nokta değilse, sonraki karaktere bakın ve eşleştirmeye devam edin. `(?!\.)`, iki ardışık dönemin bir e-posta adresinin yerel bölümünde görünmesini engelleyen sıfır Genişlik negatif ileriye yönelik bir onaylama işlemi.

Model ``|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w]`` : sonraki karakter bir nokta değilse, herhangi bir sözcük karakteri veya şu karakterlerden birini eşleştirin:-! # $% & ' \* +/=? ^ \` {} | ~

Model ``((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*`` : değişim düzeniyle (bir dönem, dönem olmayan bir nokta veya bir dizi karakterden biri) sıfır veya daha fazla kez eşleştirin.

Model `@` : @ karakteriyle eşleştirin.

Model `(?<=[0-9a-z])` : @ karakterinden önce gelen karakter bir-z, a-z veya 0 ile 9 arasında bir karakter olduğunda eşleştirmeye devam edin. Bu model sıfır Genişlik pozitif geriye yönelik bir onaylama işlemi tanımlar.

Model `(?(\[)` : @ sözcüğünden sonra gelen karakterin bir açılış ayracı olup olmadığını kontrol edin.

Model `(\[(\d{1,3}\.){3}\d{1,3}\])` : bir açma köşeli ayracı ise, açma köşeli ayracından sonra BIR IP adresi (her bir noktayla ayırarak dört adet bir ve üç basamaklı dört küme) ve bir kapanış ayracı eşleştirin.

Model `|(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+` : @ ' i izleyen karakter bir açılış ayracı değilse, bir alfasayısal karakteri a-z, a-z veya 0-9 ile eşleştirin, ardından sıfır veya daha fazla tire, a-z, a-z veya 0-9 değerli bir alfasayısal karakter ve ardından bir nokta gelir. Bu kalıp bir veya daha fazla kez tekrarlanabilir ve ardından üst düzey etki alanı adı gelmelidir.

Model `[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))` : en üst düzey etki alanı adı alfasayısal bir karakterle başlamalı ve bitmelidir (a-z, a-z ve 0-9). Ayrıca, alfasayısal veya kısa çizgi olan sıfır ile 22 ASCII karakter arasında da olabilir.

Model `$` : dizenin sonundaki eşleşmeyi sonlandırın.

## <a name="compile-the-code"></a>Kodu derle

`IsValidEmail`Ve `DomainMapper` yöntemleri bir normal ifade yardımcı programı yöntemlerine dahil edilebilir veya uygulama sınıfına özel statik veya örnek yöntemleri olarak dahil edilebilir.

<xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType>Bu normal ifade bir normal ifade kitaplığına dahil etmek için yöntemini de kullanabilirsiniz.

Bunlar bir normal ifade kitaplığında kullanılıyorsa, bunları aşağıdaki gibi bir kod kullanarak çağırabilirsiniz:

[!code-csharp[RegularExpressions.Examples.Email#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#8)]
[!code-vb[RegularExpressions.Examples.Email#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#8)]

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework Normal İfadeleri](regular-expressions.md)
