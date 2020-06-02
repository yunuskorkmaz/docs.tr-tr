---
title: 'Nasıl yapılır: Dizeden Geçersiz Karakterleri Çıkartma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, examples
- cleaning input
- user input, examples
- .NET Framework regular expressions, examples
- regular expressions [.NET Framework], examples
- Regex.Replace method
- stripping invalid characters
- Replace method
- validating user input
ms.assetid: b4319c8a-9032-4129-a9d5-6f6fc28e7f32
ms.openlocfilehash: 5f2a1e7a3202b14d32ed02c6808fe2411465d9b5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290441"
---
# <a name="how-to-strip-invalid-characters-from-a-string"></a><span data-ttu-id="8254e-102">Nasıl yapılır: Dizeden Geçersiz Karakterleri Çıkartma</span><span class="sxs-lookup"><span data-stu-id="8254e-102">How to: Strip Invalid Characters from a String</span></span>
<span data-ttu-id="8254e-103">Aşağıdaki örnek, <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> bir dizeden geçersiz karakterleri atmak için statik yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="8254e-103">The following example uses the static <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> method to strip invalid characters from a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8254e-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="8254e-104">Example</span></span>  
 <span data-ttu-id="8254e-105">`CleanInput`Kullanıcı girişini kabul eden bir metin alanına girilmiş olabilecek zararlı karakterleri birleştirmek için bu örnekte tanımlanan yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8254e-105">You can use the `CleanInput` method defined in this example to strip potentially harmful characters that have been entered into a text field that accepts user input.</span></span> <span data-ttu-id="8254e-106">Bu durumda, `CleanInput` noktalar (.), semboller (@) ve tire (-) dışındaki tüm alfasayısal olmayan karakterleri kaldırır ve kalan dizeyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="8254e-106">In this case, `CleanInput` strips out all nonalphanumeric characters except periods (.), at symbols (@), and hyphens (-), and returns the remaining string.</span></span> <span data-ttu-id="8254e-107">Ancak, normal ifade deseninin bir giriş dizesine dahil olmaması gereken herhangi bir karakteri şeritleri için değişiklik yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8254e-107">However, you can modify the regular expression pattern so that it strips out any characters that should not be included in an input string.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/vb/Example.vb#1)]  
  
 <span data-ttu-id="8254e-108">Normal ifade stili, bir `[^\w\.@-]` sözcük karakteri, nokta, @ simge veya kısa çizgi olmayan herhangi bir karakterle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="8254e-108">The regular expression pattern `[^\w\.@-]` matches any character that is not a word character, a period, an @ symbol, or a hyphen.</span></span> <span data-ttu-id="8254e-109">Bir sözcük karakteri, alt çizgi gibi herhangi bir harf, ondalık basamak veya noktalama bağlayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="8254e-109">A word character is any letter, decimal digit, or punctuation connector such as an underscore.</span></span> <span data-ttu-id="8254e-110">Bu düzenle eşleşen herhangi bir karakter <xref:System.String.Empty?displayProperty=nameWithType> , değiştirme düzeniyle tanımlanan dize olan ile değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8254e-110">Any character that matches this pattern is replaced by <xref:System.String.Empty?displayProperty=nameWithType>, which is the string defined by the replacement pattern.</span></span> <span data-ttu-id="8254e-111">Kullanıcı girişinde ek karakterlere izin vermek için, bu karakterleri normal ifade deseninin karakter sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8254e-111">To allow additional characters in user input, add those characters to the character class in the regular expression pattern.</span></span> <span data-ttu-id="8254e-112">Örneğin, normal ifade deseninin de bir `[^\w\.@-\\%]` yüzde simgesine ve bir giriş dizesinde ters eğik çizgiye izin verir.</span><span class="sxs-lookup"><span data-stu-id="8254e-112">For example, the regular expression pattern `[^\w\.@-\\%]` also allows a percentage symbol and a backslash in an input string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8254e-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8254e-113">See also</span></span>

- [<span data-ttu-id="8254e-114">.NET normal Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="8254e-114">.NET Regular Expressions</span></span>](regular-expressions.md)
