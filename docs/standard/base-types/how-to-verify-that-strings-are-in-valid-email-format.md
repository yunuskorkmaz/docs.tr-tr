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
ms.openlocfilehash: 1812235da6e6d02a97fe994568c5c26a3c7cde33
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126407"
---
# <a name="how-to-verify-that-strings-are-in-valid-email-format"></a>Nasıl yapılır: dizelerin geçerli e-posta biçiminde olduğunu doğrulama

Aşağıdaki örnek bir dizenin geçerli e-posta biçiminde olduğunu doğrulamak için normal bir ifade kullanır.

## <a name="example"></a>Örnek

Örnek, dize geçerli bir e-posta adresi içeriyorsa ve `false` yoksa ancak başka bir eylem yoksa, `true` döndüren `IsValidEmail` yöntemini tanımlar.

E-posta adresinin geçerli olduğunu doğrulamak için `IsValidEmail` yöntemi, etki alanı adını e-posta adresinden ayırmak için `(@)(.+)$` normal ifade düzeniyle <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> yöntemini çağırır. Üçüncü parametre, eşleşen metni işleyen ve değiştiren yöntemi temsil eden bir <xref:System.Text.RegularExpressions.MatchEvaluator> temsilcisidir. Normal ifade deseninin aşağıdaki şekilde yorumlanması.

|Desen|Açıklama|
|-------------|-----------------|
|`(@)`|@ Karakteriyle eşleştirin. Bu ilk yakalama grubudur.|
|`(.+)`|Herhangi bir karakterin bir veya daha fazla tekrarı ile eşleştirin. Bu ikinci yakalama grubudur.|
|`$`|Dizenin sonundaki eşleşmeyi sonlandırın.|

Etki alanı adı @ karakteriyle birlikte `DomainMapper` yöntemine geçirilir ve bu, US-ASCII karakter aralığının dışındaki Unicode karakterleri, Punyıcode 'a dönüştürmek için <xref:System.Globalization.IdnMapping> sınıfını kullanır. Ayrıca, <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> yöntemi etki alanı adında geçersiz karakterler algılarsa, yöntem `invalid` bayrağını `True` olarak ayarlar. Yöntemi, `IsValidEmail` metoduna önüne @ symbol olan Punyıcode etki alanı adını döndürür.

`IsValidEmail` yöntemi, adresin bir normal ifade düzenine uygun olduğunu doğrulamak için <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> yöntemini çağırır.

`IsValidEmail` yönteminin, e-posta adresini doğrulamak için kimlik doğrulaması gerçekleştirmediğini unutmayın. Yalnızca biçiminin bir e-posta adresi için geçerli olup olmadığını belirler. Ayrıca `IsValidEmail` yöntemi, üst düzey etki alanı adının, [IANA kök bölgesi veritabanında](https://www.iana.org/domains/root/db)listelenen geçerli bir etki alanı adı olduğunu doğrulamaz, bu da bir arama işlemi gerektirir. Bunun yerine, normal ifade yalnızca en üst düzey etki alanı adının, alfasayısal ve son karakterlerden oluşan iki ve Yirmi dört ASCII karakterden oluştuğunu doğrular ve geri kalan karakterlerin alfasayısal ya da kısa çizgi (-) olacağını doğrular.

[!code-csharp[RegularExpressions.Examples.Email#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#7)]
[!code-vb[RegularExpressions.Examples.Email#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#7)]

Bu örnekte, normal ifade deseninin ``^(?(")(".+?(?<!\\)"@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*)(?<=[0-9a-z])@))(?([)([(\d{1,3}.){3}\d{1,3}])|(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+[a-z0-9][-a-z0-9]{0,22}[a-z0-9]))$`` aşağıdaki göstergede gösterildiği gibi yorumlanır. Normal ifade <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> bayrağı kullanılarak derlenir.

`^`model: dizenin başlangıcında eşleşmeyi Başlat.

Model `(?(")`: ilk karakterin bir tırnak işareti olup olmadığını belirleme. `(?(")`, değişim yapısının başlangıcıdır.

Model `(?(")(".+?(?<!\\)"@)`: ilk karakter bir tırnak işareti ise, bir başlangıç tırnak işaretiyle, ardından herhangi bir karakterin en az bir örneğinden ve ardından bir bitiş tırnak işaretiyle eşleştirin. Bitiş tırnak işareti önünde ters eğik çizgi karakteri (\\) olmamalıdır. `(?<!` sıfır Genişlik negatif geriye yönelik onay başlangıcının başlangıcıdır. Dize bir at işareti (@) ile sona ermelidir.

Model `|(([0-9a-z]`: ilk karakter bir tırnak işareti değilse, a 'dan z 'ye veya A 'dan Z 'ye (karşılaştırma büyük/küçük harfe duyarsız) veya 0 ile 9 arasında bir sayısal karakter eşleştirin.

Model `(\.(?!\.))`: sonraki karakter bir nokta ise, bunu eşleştirin. Bir nokta değilse, sonraki karaktere bakın ve eşleştirmeye devam edin. `(?!\.)`, iki ardışık dönemin bir e-posta adresinin yerel bölümünde görünmesini engelleyen sıfır Genişlik negatif ileriye yönelik bir onaylama işlemi.

Model ``|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w]``: sonraki karakter bir nokta değilse, herhangi bir sözcük karakteri veya şu karakterlerden birini eşleştirin:-! # $% & ' * +/=? ^ '{}| ~

``((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*``model: değişim düzeniyle (bir dönem, süresi olmayan bir nokta veya karakter sayısından biri) sıfır veya daha fazla kez eşleştirin.

`@`stili: @ karakteriyle eşleştirin.

`(?<=[0-9a-z])`model: @ karakterinden önce gelen karakter bir-Z, a-z veya 0 ile 9 arasında bir karakter olduğunda eşleştirmeye devam edin. Bu model sıfır Genişlik pozitif geriye yönelik bir onaylama işlemi tanımlar.

`(?(\[)`desenli desenler: @ sözcüğünden sonra gelen karakterin bir açılış ayracı olup olmadığını denetleyin.

Model `(\[(\d{1,3}\.){3}\d{1,3}\])`: bir açma köşeli ayracı ise, açma köşeli ayracını takip eden bir IP adresi (her bir noktayla ayırarak dört adet bir ve üç basamaklı dört küme) ve bir kapanış ayracı ile eşleştirin.

Model `|(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+`: @ ' i izleyen karakter bir açılış ayracı değilse, bir alfasayısal karakteri A-Z, a-z veya 0-9 ile eşleştirin, ardından sıfır veya daha fazla tire ile, ardından sıfır veya A-Z değeri olan bir alfasayısal karakter ile eşleşir , a-z veya 0-9, sonrasında bir nokta. Bu kalıp bir veya daha fazla kez tekrarlanabilir ve ardından üst düzey etki alanı adı gelmelidir.

`[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))`model: en üst düzey etki alanı adı alfasayısal bir karakterle başlamalı ve bitmelidir (a-z, A-Z ve 0-9). Ayrıca, alfasayısal veya kısa çizgi olan sıfır ile 22 ASCII karakter arasında da olabilir.

`$`desenli desenler: dizenin sonundaki eşleşmeyi sonlandırın.

## <a name="compile-the-code"></a>Kodu derle

`IsValidEmail` ve `DomainMapper` yöntemleri bir normal ifade yardımcı programı yöntemlerine dahil edilebilir veya uygulama sınıfına özel statik veya örnek yöntemleri olarak eklenebilir.

Bu normal ifadeyi normal ifade kitaplığına dahil etmek için <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> yöntemini de kullanabilirsiniz.

Bunlar bir normal ifade kitaplığında kullanılıyorsa, bunları aşağıdaki gibi bir kod kullanarak çağırabilirsiniz:

[!code-csharp[RegularExpressions.Examples.Email#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#8)]
[!code-vb[RegularExpressions.Examples.Email#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#8)]

## <a name="see-also"></a>Ayrıca bkz.

- [Normal Ifadeleri .NET Framework](../../../docs/standard/base-types/regular-expressions.md)
