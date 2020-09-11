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
ms.openlocfilehash: 90e79af649727330c2afa1ccb8c64ffe34733f92
ms.sourcegitcommit: 6d4ee46871deb9ea1e45bb5f3784474e240bbc26
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90022954"
---
# <a name="how-to-verify-that-strings-are-in-valid-email-format"></a>Dizelerin geçerli e-posta biçiminde olduğunu doğrulama

Aşağıdaki örnek bir dizenin geçerli e-posta biçiminde olduğunu doğrulamak için normal bir ifade kullanır.

Bu normal ifade, gerçekte e-posta olarak kullanılabilecek şekilde daha basit bir şekilde karşılaştırmalıdır. E-posta yapısının doğru olduğundan emin olmak için bir e-postayı doğrulamak üzere normal bir ifade kullanmak faydalıdır, ancak e-postanın gerçekten var olduğunu doğrulamak için bir değiştirme işlemi değildir.

✔️ bir e-postanın geçerli yapısını denetlemek için küçük bir normal ifade kullanın.

✔️, uygulamanızın bir kullanıcısı tarafından belirtilen adrese bir sınama e-postası gönderir.

❌ Bir e-postayı doğrulamakta olan tek yönlü bir normal ifade kullanmayın.

Bir e-postanın yapısının doğru olduğunu doğrulamak için _kusursuz_ bir normal ifade oluşturmaya çalışırsanız, ifade, hata ayıklama veya geliştirme inanılmaz zor hale gelir. Normal ifadeler, doğru şekilde yapılandırılmış olsa bile, bir e-posta olduğunu doğrulayamaz. E-postayı doğrulamak için en iyi yol, adrese bir sınama e-postası göndermektir.

[!INCLUDE [regex](../../../includes/regex.md)]

## <a name="example"></a>Örnek

Örnek, `IsValidEmail` `true` dize geçerli bir e-posta adresi içeriyorsa ve yoksa ancak başka bir işlem gerçekleştirmezse, döndüren bir yöntemini tanımlar `false` .

E-posta adresinin geçerli olduğunu doğrulamak için yöntemi, `IsValidEmail` <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> `(@)(.+)$` etki alanı adını e-posta adresinden ayırmak üzere normal ifade düzeniyle yöntemi çağırır. Üçüncü parametre, <xref:System.Text.RegularExpressions.MatchEvaluator> eşleşen metni işleyen ve değiştiren yöntemi temsil eden bir temsilcisidir. Normal ifade deseninin aşağıdaki şekilde yorumlanması.

| Desen | Description                                                                         |
|---------|-------------------------------------------------------------------------------------|
| `(@)`   | @ Karakteriyle eşleştirin. Bu bölüm ilk yakalama grubudur.                           |
| `(.+)`  | Herhangi bir karakterin bir veya daha fazla tekrarı ile eşleştirin. Bu bölüm, ikinci yakalama grubudur. |
| `$`     | Dizenin sonundaki eşleşmeyi sonlandırın.                                             |

@ Karakteriyle birlikte etki alanı adı yöntemine geçirilir ve bu, `DomainMapper` <xref:System.Globalization.IdnMapping> US-ASCII karakter aralığının dışındaki Unicode karakterleri, Punyıcode 'a dönüştürmek için sınıfını kullanır. Yöntemi, `invalid` `True` <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> yöntemi etki alanı adında geçersiz karakterler algılarsa, bayrağını da ayarlar. Yöntemi, önüne @ simgesinden önce gelen Punyıcode etki alanı adını döndürür `IsValidEmail` .

> [!TIP]
> `(@)(.+)$`Etki alanını normalleştirmek için basit normal ifade deseninin kullanılması önerilir ve sonra geçtiğini veya başarısız olduğunu gösteren bir değer döndürür. Ancak, bu makaledeki örnekte e-postayı doğrulamak için normal bir ifadenin nasıl kullanılacağı açıklanmaktadır. Bir e-postayı nasıl doğruladığınızdan bağımsız olarak, mevcut olduğundan emin olmak için adrese her zaman bir sınama e-postası göndermeniz gerekir.

`IsValidEmail`Yöntemi daha sonra, <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> adresin bir normal ifade düzenine uygun olduğunu doğrulamak için yöntemini çağırır.

Yöntemi yalnızca e-posta `IsValidEmail` biçiminin bir e-posta adresi için geçerli olup olmadığını belirler, e-postanın mevcut olduğunu doğrulamaz. Ayrıca, `IsValidEmail` yöntemi en üst düzey etki alanı adının, [IANA kök bölgesi veritabanında](https://www.iana.org/domains/root/db)listelenen geçerli bir etki alanı adı olduğunu doğrulamaz, bu da bir arama işlemi gerektirir.

:::code language="csharp" source="snippets/how-to-verify-that-strings-are-in-valid-email-format/csharp/RegexUtilities.cs":::

:::code language="vb" source="snippets/how-to-verify-that-strings-are-in-valid-email-format/vb/RegexUtilities.vb":::

Bu örnekte, normal ifade deseninin `^[^@\s]+@[^@\s]+\.[^@\s]+$` Aşağıdaki tabloda gösterildiği gibi yorumlanır. Normal ifade, bayrağı kullanılarak derlenir <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> .

| Desen   | Description                                                                              |
|-----------|------------------------------------------------------------------------------------------|
| `^`       | Dizenin başlangıcında eşleşmeyi başlatın.                                              |
| `[^@\s]+` | @ Character veya boşluk dışında herhangi bir karakterin bir veya daha fazla tekrarı ile eşleştirin. |
| `@`       | @ Karakteriyle eşleştirin.                                                                   |
| `[^@\s]+` | @ Character veya boşluk dışında herhangi bir karakterin bir veya daha fazla tekrarı ile eşleştirin. |
| `\.`      | Tek bir nokta karakteriyle eşleşir.                                                         |
| `[^@\s]+` | @ Character veya boşluk dışında herhangi bir karakterin bir veya daha fazla tekrarı ile eşleştirin. |
| `$`       | Dizenin sonundaki eşleşmeyi sonlandırın.                                                  |

> [!IMPORTANT]
> Bu normal ifade, geçerli bir e-posta adresinin her yönünü kapsayacak şekilde tasarlanmamıştır. Gerektiğinde genişletmenize örnek olarak sunulmaktadır.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework Normal İfadeleri](regular-expressions.md)
- [Tek bir e-posta adresi doğrulaması ne kadar sürer?](https://softwareengineering.stackexchange.com/questions/78353/how-far-should-one-take-e-mail-address-validation#78363)
