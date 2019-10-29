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
ms.openlocfilehash: 352808e561a0f59d41f092eb7c70c40a591da5b6
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846775"
---
# <a name="how-to-verify-that-strings-are-in-valid-email-format"></a><span data-ttu-id="64eda-102">Nasıl yapılır: dizelerin geçerli e-posta biçiminde olduğunu doğrulama</span><span class="sxs-lookup"><span data-stu-id="64eda-102">How to: Verify that strings are in valid email format</span></span>

<span data-ttu-id="64eda-103">Aşağıdaki örnek bir dizenin geçerli e-posta biçiminde olduğunu doğrulamak için normal bir ifade kullanır.</span><span class="sxs-lookup"><span data-stu-id="64eda-103">The following example uses a regular expression to verify that a string is in valid email format.</span></span>

## <a name="example"></a><span data-ttu-id="64eda-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="64eda-104">Example</span></span>

<span data-ttu-id="64eda-105">Örnek, dize geçerli bir e-posta adresi içeriyorsa ve `false` yoksa ancak başka bir eylem yoksa, `true` döndüren `IsValidEmail` yöntemini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="64eda-105">The example defines an `IsValidEmail` method, which returns `true` if the string contains a valid email address and `false` if it does not, but takes no other action.</span></span>

<span data-ttu-id="64eda-106">E-posta adresinin geçerli olduğunu doğrulamak için `IsValidEmail` yöntemi, etki alanı adını e-posta adresinden ayırmak için `(@)(.+)$` normal ifade düzeniyle <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="64eda-106">To verify that the email address is valid, the `IsValidEmail` method calls the <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> method with the `(@)(.+)$` regular expression pattern to separate the domain name from the email address.</span></span> <span data-ttu-id="64eda-107">Üçüncü parametre, eşleşen metni işleyen ve değiştiren yöntemi temsil eden bir <xref:System.Text.RegularExpressions.MatchEvaluator> temsilcisidir.</span><span class="sxs-lookup"><span data-stu-id="64eda-107">The third parameter is a <xref:System.Text.RegularExpressions.MatchEvaluator> delegate that represents the method that processes and replaces the matched text.</span></span> <span data-ttu-id="64eda-108">Normal ifade deseninin aşağıdaki şekilde yorumlanması.</span><span class="sxs-lookup"><span data-stu-id="64eda-108">The regular expression pattern is interpreted as follows.</span></span>

|<span data-ttu-id="64eda-109">Desen</span><span class="sxs-lookup"><span data-stu-id="64eda-109">Pattern</span></span>|<span data-ttu-id="64eda-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="64eda-110">Description</span></span>|
|-------------|-----------------|
|`(@)`|<span data-ttu-id="64eda-111">@ Karakteriyle eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="64eda-111">Match the @ character.</span></span> <span data-ttu-id="64eda-112">Bu ilk yakalama grubudur.</span><span class="sxs-lookup"><span data-stu-id="64eda-112">This is the first capturing group.</span></span>|
|`(.+)`|<span data-ttu-id="64eda-113">Herhangi bir karakterin bir veya daha fazla tekrarı ile eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="64eda-113">Match one or more occurrences of any character.</span></span> <span data-ttu-id="64eda-114">Bu ikinci yakalama grubudur.</span><span class="sxs-lookup"><span data-stu-id="64eda-114">This is the second capturing group.</span></span>|
|`$`|<span data-ttu-id="64eda-115">Dizenin sonundaki eşleşmeyi sonlandırın.</span><span class="sxs-lookup"><span data-stu-id="64eda-115">End the match at the end of the string.</span></span>|

<span data-ttu-id="64eda-116">Etki alanı adı @ karakteriyle birlikte `DomainMapper` yöntemine geçirilir ve bu, US-ASCII karakter aralığının dışındaki Unicode karakterleri, Punyıcode 'a dönüştürmek için <xref:System.Globalization.IdnMapping> sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="64eda-116">The domain name along with the @ character is passed to the `DomainMapper` method, which uses the <xref:System.Globalization.IdnMapping> class to translate Unicode characters that are outside the US-ASCII character range to Punycode.</span></span> <span data-ttu-id="64eda-117">Ayrıca, <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> yöntemi etki alanı adında geçersiz karakterler algılarsa, yöntem `invalid` bayrağını `True` olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="64eda-117">The method also sets the `invalid` flag to `True` if the <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> method detects any invalid characters in the domain name.</span></span> <span data-ttu-id="64eda-118">Yöntemi, `IsValidEmail` metoduna önüne @ symbol olan Punyıcode etki alanı adını döndürür.</span><span class="sxs-lookup"><span data-stu-id="64eda-118">The method returns the Punycode domain name preceded by the @ symbol to the `IsValidEmail` method.</span></span>

<span data-ttu-id="64eda-119">`IsValidEmail` yöntemi, adresin bir normal ifade düzenine uygun olduğunu doğrulamak için <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="64eda-119">The `IsValidEmail` method then calls the <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> method to verify that the address conforms to a regular expression pattern.</span></span>

<span data-ttu-id="64eda-120">`IsValidEmail` yönteminin, e-posta adresini doğrulamak için kimlik doğrulaması gerçekleştirmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="64eda-120">Note that the `IsValidEmail` method does not perform authentication to validate the email address.</span></span> <span data-ttu-id="64eda-121">Yalnızca biçiminin bir e-posta adresi için geçerli olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="64eda-121">It merely determines whether its format is valid for an email address.</span></span> <span data-ttu-id="64eda-122">Ayrıca `IsValidEmail` yöntemi, üst düzey etki alanı adının, [IANA kök bölgesi veritabanında](https://www.iana.org/domains/root/db)listelenen geçerli bir etki alanı adı olduğunu doğrulamaz, bu da bir arama işlemi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="64eda-122">In addition, the `IsValidEmail` method does not verify that the top-level domain name is a valid domain name listed at the [IANA Root Zone Database](https://www.iana.org/domains/root/db), which would require a look-up operation.</span></span> <span data-ttu-id="64eda-123">Bunun yerine, normal ifade yalnızca en üst düzey etki alanı adının, alfasayısal ve son karakterlerden oluşan iki ve Yirmi dört ASCII karakterden oluştuğunu doğrular ve geri kalan karakterlerin alfasayısal ya da kısa çizgi (-) olacağını doğrular.</span><span class="sxs-lookup"><span data-stu-id="64eda-123">Instead, the regular expression merely verifies that the top-level domain name consists of between two and twenty-four ASCII characters, with alphanumeric first and last characters and the remaining characters being either alphanumeric or a hyphen (-).</span></span>

[!code-csharp[RegularExpressions.Examples.Email#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#7)]
[!code-vb[RegularExpressions.Examples.Email#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#7)]

<span data-ttu-id="64eda-124">Bu örnekte, normal ifade deseninin ``^(?(")(".+?(?<!\\)"@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*)(?<=[0-9a-z])@))(?([)([(\d{1,3}.){3}\d{1,3}])|(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+[a-z0-9][-a-z0-9]{0,22}[a-z0-9]))$`` aşağıdaki göstergede gösterildiği gibi yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="64eda-124">In this example, the regular expression pattern ``^(?(")(".+?(?<!\\)"@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*)(?<=[0-9a-z])@))(?([)([(\d{1,3}.){3}\d{1,3}])|(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+[a-z0-9][-a-z0-9]{0,22}[a-z0-9]))$`` is interpreted as shown in the following legend.</span></span> <span data-ttu-id="64eda-125">Normal ifade <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> bayrağı kullanılarak derlenir.</span><span class="sxs-lookup"><span data-stu-id="64eda-125">The regular expression is compiled using the <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> flag.</span></span>

<span data-ttu-id="64eda-126">`^`model: dizenin başlangıcında eşleşmeyi Başlat.</span><span class="sxs-lookup"><span data-stu-id="64eda-126">Pattern `^`: Begin the match at the start of the string.</span></span>

<span data-ttu-id="64eda-127">Model `(?(")`: ilk karakterin bir tırnak işareti olup olmadığını belirleme.</span><span class="sxs-lookup"><span data-stu-id="64eda-127">Pattern `(?(")`: Determine whether the first character is a quotation mark.</span></span> <span data-ttu-id="64eda-128">`(?(")`, değişim yapısının başlangıcıdır.</span><span class="sxs-lookup"><span data-stu-id="64eda-128">`(?(")` is the beginning of an alternation construct.</span></span>

<span data-ttu-id="64eda-129">Model `(?(")(".+?(?<!\\)"@)`: ilk karakter bir tırnak işareti ise, bir başlangıç tırnak işaretiyle, ardından herhangi bir karakterin en az bir örneğinden ve ardından bir bitiş tırnak işaretiyle eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="64eda-129">Pattern `(?(")(".+?(?<!\\)"@)`: If the first character is a quotation mark, match a beginning quotation mark followed by at least one occurrence of any character, followed by an ending quotation mark.</span></span> <span data-ttu-id="64eda-130">Bitiş tırnak işareti önünde ters eğik çizgi karakteri (\\) olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="64eda-130">The ending quotation mark must not be preceded by a backslash character (\\).</span></span> <span data-ttu-id="64eda-131">`(?<!` sıfır Genişlik negatif geriye yönelik onay başlangıcının başlangıcıdır.</span><span class="sxs-lookup"><span data-stu-id="64eda-131">`(?<!` is the beginning of a zero-width negative lookbehind assertion.</span></span> <span data-ttu-id="64eda-132">Dize bir at işareti (@) ile sona ermelidir.</span><span class="sxs-lookup"><span data-stu-id="64eda-132">The string should conclude with an at sign (@).</span></span>

<span data-ttu-id="64eda-133">Model `|(([0-9a-z]`: ilk karakter bir tırnak işareti değilse, a 'dan z 'ye veya A 'dan Z 'ye (karşılaştırma büyük/küçük harfe duyarsız) veya 0 ile 9 arasında bir sayısal karakter eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="64eda-133">Pattern `|(([0-9a-z]`: If the first character is not a quotation mark, match any alphabetic character from a to z or A to Z (the comparison is case insensitive), or any numeric character from 0 to 9.</span></span>

<span data-ttu-id="64eda-134">Model `(\.(?!\.))`: sonraki karakter bir nokta ise, bunu eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="64eda-134">Pattern `(\.(?!\.))`: If the next character is a period, match it.</span></span> <span data-ttu-id="64eda-135">Bir nokta değilse, sonraki karaktere bakın ve eşleştirmeye devam edin.</span><span class="sxs-lookup"><span data-stu-id="64eda-135">If it is not a period, look ahead to the next character and continue the match.</span></span> <span data-ttu-id="64eda-136">`(?!\.)`, iki ardışık dönemin bir e-posta adresinin yerel bölümünde görünmesini engelleyen sıfır Genişlik negatif ileriye yönelik bir onaylama işlemi.</span><span class="sxs-lookup"><span data-stu-id="64eda-136">`(?!\.)` is a zero-width negative lookahead assertion that prevents two consecutive periods from appearing in the local part of an email address.</span></span>

<span data-ttu-id="64eda-137">Model ``|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w]``: sonraki karakter bir nokta değilse, herhangi bir sözcük karakteri veya şu karakterlerden birini eşleştirin:-! # $% & ' \* +/=? ^ '{}| ~</span><span class="sxs-lookup"><span data-stu-id="64eda-137">Pattern ``|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w]``: If the next character is not a period, match any word character or one of the following characters: -!#$%&'\*+/=?^\`{}|~</span></span>

<span data-ttu-id="64eda-138">``((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*``model: değişim düzeniyle (bir dönem, süresi olmayan bir nokta veya karakter sayısından biri) sıfır veya daha fazla kez eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="64eda-138">Pattern ``((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*``: Match the alternation pattern (a period followed by a non-period, or one of a number of characters) zero or more times.</span></span>

<span data-ttu-id="64eda-139">`@`stili: @ karakteriyle eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="64eda-139">Pattern `@`: Match the @ character.</span></span>

<span data-ttu-id="64eda-140">`(?<=[0-9a-z])`model: @ karakterinden önce gelen karakter bir-Z, a-z veya 0 ile 9 arasında bir karakter olduğunda eşleştirmeye devam edin.</span><span class="sxs-lookup"><span data-stu-id="64eda-140">Pattern `(?<=[0-9a-z])`: Continue the match if the character that precedes the @ character is A through Z, a through z, or 0 through 9.</span></span> <span data-ttu-id="64eda-141">Bu model sıfır Genişlik pozitif geriye yönelik bir onaylama işlemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="64eda-141">This pattern defines a zero-width positive lookbehind assertion.</span></span>

<span data-ttu-id="64eda-142">`(?(\[)`desenli desenler: @ sözcüğünden sonra gelen karakterin bir açılış ayracı olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="64eda-142">Pattern `(?(\[)`: Check whether the character that follows @ is an opening bracket.</span></span>

<span data-ttu-id="64eda-143">Model `(\[(\d{1,3}\.){3}\d{1,3}\])`: bir açma köşeli ayracı ise, açma köşeli ayracını takip eden bir IP adresi (her bir noktayla ayırarak dört adet bir ve üç basamaklı dört küme) ve bir kapanış ayracı ile eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="64eda-143">Pattern `(\[(\d{1,3}\.){3}\d{1,3}\])`: If it is an opening bracket, match the opening bracket followed by an IP address (four sets of one to three digits, with each set separated by a period) and a closing bracket.</span></span>

<span data-ttu-id="64eda-144">Model `|(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+`: @ ' i izleyen karakter bir açılış ayracı değilse, bir alfasayısal karakteri A-Z, a-z veya 0-9 ile eşleştirin, ardından sıfır veya daha fazla tire ile, ardından sıfır veya A-Z değeri olan bir alfasayısal karakter ile eşleşir , a-z veya 0-9, sonrasında bir nokta.</span><span class="sxs-lookup"><span data-stu-id="64eda-144">Pattern `|(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+`: If the character that follows @ is not an opening bracket, match one alphanumeric character with a value of A-Z, a-z, or 0-9, followed by zero or more occurrences of a hyphen, followed by zero or one alphanumeric character with a value of A-Z, a-z, or 0-9, followed by a period.</span></span> <span data-ttu-id="64eda-145">Bu kalıp bir veya daha fazla kez tekrarlanabilir ve ardından üst düzey etki alanı adı gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="64eda-145">This pattern can be repeated one or more times, and must be followed by the top-level domain name.</span></span>

<span data-ttu-id="64eda-146">`[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))`model: en üst düzey etki alanı adı alfasayısal bir karakterle başlamalı ve bitmelidir (a-z, A-Z ve 0-9).</span><span class="sxs-lookup"><span data-stu-id="64eda-146">Pattern `[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))`: The top-level domain name must begin and end with an alphanumeric character (a-z, A-Z, and 0-9).</span></span> <span data-ttu-id="64eda-147">Ayrıca, alfasayısal veya kısa çizgi olan sıfır ile 22 ASCII karakter arasında da olabilir.</span><span class="sxs-lookup"><span data-stu-id="64eda-147">It can also include from zero to 22 ASCII characters that are either alphanumeric or hyphens.</span></span>

<span data-ttu-id="64eda-148">`$`desenli desenler: dizenin sonundaki eşleşmeyi sonlandırın.</span><span class="sxs-lookup"><span data-stu-id="64eda-148">Pattern `$`: End the match at the end of the string.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="64eda-149">Kodu derle</span><span class="sxs-lookup"><span data-stu-id="64eda-149">Compile the code</span></span>

<span data-ttu-id="64eda-150">`IsValidEmail` ve `DomainMapper` yöntemleri bir normal ifade yardımcı programı yöntemlerine dahil edilebilir veya uygulama sınıfına özel statik veya örnek yöntemleri olarak eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="64eda-150">The `IsValidEmail` and `DomainMapper` methods can be included in a library of regular expression utility methods, or they can be included as private static or instance methods in the application class.</span></span>

<span data-ttu-id="64eda-151">Bu normal ifadeyi normal ifade kitaplığına dahil etmek için <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> yöntemini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="64eda-151">You can also use the <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> method to include this regular expression in a regular expression library.</span></span>

<span data-ttu-id="64eda-152">Bunlar bir normal ifade kitaplığında kullanılıyorsa, bunları aşağıdaki gibi bir kod kullanarak çağırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="64eda-152">If they are used in a regular expression library, you can call them by using code such as the following:</span></span>

[!code-csharp[RegularExpressions.Examples.Email#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#8)]
[!code-vb[RegularExpressions.Examples.Email#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#8)]

## <a name="see-also"></a><span data-ttu-id="64eda-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64eda-153">See also</span></span>

- [<span data-ttu-id="64eda-154">Normal Ifadeleri .NET Framework</span><span class="sxs-lookup"><span data-stu-id="64eda-154">.NET Framework Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
