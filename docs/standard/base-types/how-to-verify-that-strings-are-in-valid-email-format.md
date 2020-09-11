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
# <a name="how-to-verify-that-strings-are-in-valid-email-format"></a><span data-ttu-id="f6002-103">Dizelerin geçerli e-posta biçiminde olduğunu doğrulama</span><span class="sxs-lookup"><span data-stu-id="f6002-103">How to verify that strings are in valid email format</span></span>

<span data-ttu-id="f6002-104">Aşağıdaki örnek bir dizenin geçerli e-posta biçiminde olduğunu doğrulamak için normal bir ifade kullanır.</span><span class="sxs-lookup"><span data-stu-id="f6002-104">The following example uses a regular expression to verify that a string is in valid email format.</span></span>

<span data-ttu-id="f6002-105">Bu normal ifade, gerçekte e-posta olarak kullanılabilecek şekilde daha basit bir şekilde karşılaştırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f6002-105">This regular expression is comparatively simple to what can actually be used as an email.</span></span> <span data-ttu-id="f6002-106">E-posta yapısının doğru olduğundan emin olmak için bir e-postayı doğrulamak üzere normal bir ifade kullanmak faydalıdır, ancak e-postanın gerçekten var olduğunu doğrulamak için bir değiştirme işlemi değildir.</span><span class="sxs-lookup"><span data-stu-id="f6002-106">Using a regular expression to validate an email is useful to make sure the structure of an email is correct, but it isn't a substitution for verifying the email actually exists.</span></span>

<span data-ttu-id="f6002-107">✔️ bir e-postanın geçerli yapısını denetlemek için küçük bir normal ifade kullanın.</span><span class="sxs-lookup"><span data-stu-id="f6002-107">✔️ DO use a small regular expression to check for the valid structure of an email.</span></span>

<span data-ttu-id="f6002-108">✔️, uygulamanızın bir kullanıcısı tarafından belirtilen adrese bir sınama e-postası gönderir.</span><span class="sxs-lookup"><span data-stu-id="f6002-108">✔️ DO send a test email to the address provided by a user of your app.</span></span>

<span data-ttu-id="f6002-109">❌ Bir e-postayı doğrulamakta olan tek yönlü bir normal ifade kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="f6002-109">❌ DON'T use a regular expression as the only way you validate an email.</span></span>

<span data-ttu-id="f6002-110">Bir e-postanın yapısının doğru olduğunu doğrulamak için _kusursuz_ bir normal ifade oluşturmaya çalışırsanız, ifade, hata ayıklama veya geliştirme inanılmaz zor hale gelir.</span><span class="sxs-lookup"><span data-stu-id="f6002-110">If you try to create the _perfect_ regular expression to validate that the structure of an email is correct, the expression becomes so complex that it's incredibly difficult to debug or improve.</span></span> <span data-ttu-id="f6002-111">Normal ifadeler, doğru şekilde yapılandırılmış olsa bile, bir e-posta olduğunu doğrulayamaz.</span><span class="sxs-lookup"><span data-stu-id="f6002-111">Regular expressions can't validate an email exists, even if it's structured correctly.</span></span> <span data-ttu-id="f6002-112">E-postayı doğrulamak için en iyi yol, adrese bir sınama e-postası göndermektir.</span><span class="sxs-lookup"><span data-stu-id="f6002-112">The best way to validate an email is to send a test email to the address.</span></span>

[!INCLUDE [regex](../../../includes/regex.md)]

## <a name="example"></a><span data-ttu-id="f6002-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="f6002-113">Example</span></span>

<span data-ttu-id="f6002-114">Örnek, `IsValidEmail` `true` dize geçerli bir e-posta adresi içeriyorsa ve yoksa ancak başka bir işlem gerçekleştirmezse, döndüren bir yöntemini tanımlar `false` .</span><span class="sxs-lookup"><span data-stu-id="f6002-114">The example defines an `IsValidEmail` method, which returns `true` if the string contains a valid email address and `false` if it doesn't, but takes no other action.</span></span>

<span data-ttu-id="f6002-115">E-posta adresinin geçerli olduğunu doğrulamak için yöntemi, `IsValidEmail` <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> `(@)(.+)$` etki alanı adını e-posta adresinden ayırmak üzere normal ifade düzeniyle yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="f6002-115">To verify that the email address is valid, the `IsValidEmail` method calls the <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> method with the `(@)(.+)$` regular expression pattern to separate the domain name from the email address.</span></span> <span data-ttu-id="f6002-116">Üçüncü parametre, <xref:System.Text.RegularExpressions.MatchEvaluator> eşleşen metni işleyen ve değiştiren yöntemi temsil eden bir temsilcisidir.</span><span class="sxs-lookup"><span data-stu-id="f6002-116">The third parameter is a <xref:System.Text.RegularExpressions.MatchEvaluator> delegate that represents the method that processes and replaces the matched text.</span></span> <span data-ttu-id="f6002-117">Normal ifade deseninin aşağıdaki şekilde yorumlanması.</span><span class="sxs-lookup"><span data-stu-id="f6002-117">The regular expression pattern is interpreted as follows.</span></span>

| <span data-ttu-id="f6002-118">Desen</span><span class="sxs-lookup"><span data-stu-id="f6002-118">Pattern</span></span> | <span data-ttu-id="f6002-119">Description</span><span class="sxs-lookup"><span data-stu-id="f6002-119">Description</span></span>                                                                         |
|---------|-------------------------------------------------------------------------------------|
| `(@)`   | <span data-ttu-id="f6002-120">@ Karakteriyle eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="f6002-120">Match the @ character.</span></span> <span data-ttu-id="f6002-121">Bu bölüm ilk yakalama grubudur.</span><span class="sxs-lookup"><span data-stu-id="f6002-121">This part is the first capturing group.</span></span>                           |
| `(.+)`  | <span data-ttu-id="f6002-122">Herhangi bir karakterin bir veya daha fazla tekrarı ile eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="f6002-122">Match one or more occurrences of any character.</span></span> <span data-ttu-id="f6002-123">Bu bölüm, ikinci yakalama grubudur.</span><span class="sxs-lookup"><span data-stu-id="f6002-123">This part is the second capturing group.</span></span> |
| `$`     | <span data-ttu-id="f6002-124">Dizenin sonundaki eşleşmeyi sonlandırın.</span><span class="sxs-lookup"><span data-stu-id="f6002-124">End the match at the end of the string.</span></span>                                             |

<span data-ttu-id="f6002-125">@ Karakteriyle birlikte etki alanı adı yöntemine geçirilir ve bu, `DomainMapper` <xref:System.Globalization.IdnMapping> US-ASCII karakter aralığının dışındaki Unicode karakterleri, Punyıcode 'a dönüştürmek için sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="f6002-125">The domain name along with the @ character is passed to the `DomainMapper` method, which uses the <xref:System.Globalization.IdnMapping> class to translate Unicode characters that are outside the US-ASCII character range to Punycode.</span></span> <span data-ttu-id="f6002-126">Yöntemi, `invalid` `True` <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> yöntemi etki alanı adında geçersiz karakterler algılarsa, bayrağını da ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f6002-126">The method also sets the `invalid` flag to `True` if the <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> method detects any invalid characters in the domain name.</span></span> <span data-ttu-id="f6002-127">Yöntemi, önüne @ simgesinden önce gelen Punyıcode etki alanı adını döndürür `IsValidEmail` .</span><span class="sxs-lookup"><span data-stu-id="f6002-127">The method returns the Punycode domain name preceded by the @ symbol to the `IsValidEmail` method.</span></span>

> [!TIP]
> <span data-ttu-id="f6002-128">`(@)(.+)$`Etki alanını normalleştirmek için basit normal ifade deseninin kullanılması önerilir ve sonra geçtiğini veya başarısız olduğunu gösteren bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="f6002-128">It's recommended that you use use the simple `(@)(.+)$` regular expression pattern to normalize the domain and then return a value indicating that it passed or failed.</span></span> <span data-ttu-id="f6002-129">Ancak, bu makaledeki örnekte e-postayı doğrulamak için normal bir ifadenin nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f6002-129">However, the example in this article describes how to further use a regular expression to validate the email.</span></span> <span data-ttu-id="f6002-130">Bir e-postayı nasıl doğruladığınızdan bağımsız olarak, mevcut olduğundan emin olmak için adrese her zaman bir sınama e-postası göndermeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f6002-130">Regardless of how you validate an email, you should always send a test email to the address to make sure it exists.</span></span>

<span data-ttu-id="f6002-131">`IsValidEmail`Yöntemi daha sonra, <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> adresin bir normal ifade düzenine uygun olduğunu doğrulamak için yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="f6002-131">The `IsValidEmail` method then calls the <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> method to verify that the address conforms to a regular expression pattern.</span></span>

<span data-ttu-id="f6002-132">Yöntemi yalnızca e-posta `IsValidEmail` biçiminin bir e-posta adresi için geçerli olup olmadığını belirler, e-postanın mevcut olduğunu doğrulamaz.</span><span class="sxs-lookup"><span data-stu-id="f6002-132">The `IsValidEmail` method merely determines whether the email format is valid for an email address, it doesn't validate that the email exists.</span></span> <span data-ttu-id="f6002-133">Ayrıca, `IsValidEmail` yöntemi en üst düzey etki alanı adının, [IANA kök bölgesi veritabanında](https://www.iana.org/domains/root/db)listelenen geçerli bir etki alanı adı olduğunu doğrulamaz, bu da bir arama işlemi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f6002-133">Also, the `IsValidEmail` method doesn't verify that the top-level domain name is a valid domain name listed at the [IANA Root Zone Database](https://www.iana.org/domains/root/db), which would require a look-up operation.</span></span>

:::code language="csharp" source="snippets/how-to-verify-that-strings-are-in-valid-email-format/csharp/RegexUtilities.cs":::

:::code language="vb" source="snippets/how-to-verify-that-strings-are-in-valid-email-format/vb/RegexUtilities.vb":::

<span data-ttu-id="f6002-134">Bu örnekte, normal ifade deseninin `^[^@\s]+@[^@\s]+\.[^@\s]+$` Aşağıdaki tabloda gösterildiği gibi yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="f6002-134">In this example, the regular expression pattern `^[^@\s]+@[^@\s]+\.[^@\s]+$` is interpreted as shown in the following table.</span></span> <span data-ttu-id="f6002-135">Normal ifade, bayrağı kullanılarak derlenir <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f6002-135">The regular expression is compiled using the <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> flag.</span></span>

| <span data-ttu-id="f6002-136">Desen</span><span class="sxs-lookup"><span data-stu-id="f6002-136">Pattern</span></span>   | <span data-ttu-id="f6002-137">Description</span><span class="sxs-lookup"><span data-stu-id="f6002-137">Description</span></span>                                                                              |
|-----------|------------------------------------------------------------------------------------------|
| `^`       | <span data-ttu-id="f6002-138">Dizenin başlangıcında eşleşmeyi başlatın.</span><span class="sxs-lookup"><span data-stu-id="f6002-138">Begin the match at the start of the string.</span></span>                                              |
| `[^@\s]+` | <span data-ttu-id="f6002-139">@ Character veya boşluk dışında herhangi bir karakterin bir veya daha fazla tekrarı ile eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="f6002-139">Match one or more occurrences of any character other than the @ character or whitespace.</span></span> |
| `@`       | <span data-ttu-id="f6002-140">@ Karakteriyle eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="f6002-140">Match the @ character.</span></span>                                                                   |
| `[^@\s]+` | <span data-ttu-id="f6002-141">@ Character veya boşluk dışında herhangi bir karakterin bir veya daha fazla tekrarı ile eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="f6002-141">Match one or more occurrences of any character other than the @ character or whitespace.</span></span> |
| `\.`      | <span data-ttu-id="f6002-142">Tek bir nokta karakteriyle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="f6002-142">Match a single period character.</span></span>                                                         |
| `[^@\s]+` | <span data-ttu-id="f6002-143">@ Character veya boşluk dışında herhangi bir karakterin bir veya daha fazla tekrarı ile eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="f6002-143">Match one or more occurrences of any character other than the @ character or whitespace.</span></span> |
| `$`       | <span data-ttu-id="f6002-144">Dizenin sonundaki eşleşmeyi sonlandırın.</span><span class="sxs-lookup"><span data-stu-id="f6002-144">End the match at the end of the string.</span></span>                                                  |

> [!IMPORTANT]
> <span data-ttu-id="f6002-145">Bu normal ifade, geçerli bir e-posta adresinin her yönünü kapsayacak şekilde tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="f6002-145">This regular expression is not intended to cover every aspect of a valid email address.</span></span> <span data-ttu-id="f6002-146">Gerektiğinde genişletmenize örnek olarak sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f6002-146">It's provided as an example for you to extend as needed.</span></span>

## <a name="see-also"></a><span data-ttu-id="f6002-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f6002-147">See also</span></span>

- [<span data-ttu-id="f6002-148">.NET Framework Normal İfadeleri</span><span class="sxs-lookup"><span data-stu-id="f6002-148">.NET Framework Regular Expressions</span></span>](regular-expressions.md)
- [<span data-ttu-id="f6002-149">Tek bir e-posta adresi doğrulaması ne kadar sürer?</span><span class="sxs-lookup"><span data-stu-id="f6002-149">How far should one take e-mail address validation?</span></span>](https://softwareengineering.stackexchange.com/questions/78353/how-far-should-one-take-e-mail-address-validation#78363)
