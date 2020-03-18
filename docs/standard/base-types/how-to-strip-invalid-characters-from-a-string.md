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
ms.openlocfilehash: cc90e6609f9335b7e2f08271e5540b182901e8c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73127646"
---
# <a name="how-to-strip-invalid-characters-from-a-string"></a><span data-ttu-id="f3f94-102">Nasıl yapılır: Dizeden Geçersiz Karakterleri Çıkartma</span><span class="sxs-lookup"><span data-stu-id="f3f94-102">How to: Strip Invalid Characters from a String</span></span>
<span data-ttu-id="f3f94-103">Aşağıdaki örnek, geçersiz <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> karakterleri bir dizeden sökmek için statik yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="f3f94-103">The following example uses the static <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> method to strip invalid characters from a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3f94-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="f3f94-104">Example</span></span>  
 <span data-ttu-id="f3f94-105">Bu örnekte `CleanInput` tanımlanan yöntemi, kullanıcı girişini kabul eden bir metin alanına girilmiş zararlı olabilecek karakterleri şeritlemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3f94-105">You can use the `CleanInput` method defined in this example to strip potentially harmful characters that have been entered into a text field that accepts user input.</span></span> <span data-ttu-id="f3f94-106">Bu durumda, `CleanInput` dönemler (.), semboller (@) ve tireler (-) dışındaki tüm alfasayısal olmayan karakterleri şeritler ve kalan dizeyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="f3f94-106">In this case, `CleanInput` strips out all nonalphanumeric characters except periods (.), at symbols (@), and hyphens (-), and returns the remaining string.</span></span> <span data-ttu-id="f3f94-107">Ancak, giriş dizesinde yer almaması gereken karakterleri silecek şekilde normal ifade deseni değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3f94-107">However, you can modify the regular expression pattern so that it strips out any characters that should not be included in an input string.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/vb/Example.vb#1)]  
  
 <span data-ttu-id="f3f94-108">Normal ifade `[^\w\.@-]` deseni, sözcük karakteri, dönem, bir @ sembolü veya tire olmayan herhangi bir karakterle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="f3f94-108">The regular expression pattern `[^\w\.@-]` matches any character that is not a word character, a period, an @ symbol, or a hyphen.</span></span> <span data-ttu-id="f3f94-109">Sözcük karakteri, alt puan gibi herhangi bir harf, ondalık basamak veya noktalama bağlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="f3f94-109">A word character is any letter, decimal digit, or punctuation connector such as an underscore.</span></span> <span data-ttu-id="f3f94-110">Bu deseneşleşen herhangi bir karakter, değiştirme deseni tarafından tanımlanan dize ile değiştirilir. <xref:System.String.Empty?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f3f94-110">Any character that matches this pattern is replaced by <xref:System.String.Empty?displayProperty=nameWithType>, which is the string defined by the replacement pattern.</span></span> <span data-ttu-id="f3f94-111">Kullanıcı girişindeki ek karakterlere izin vermek için, bu karakterleri normal ifade desenindeki karakter sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f3f94-111">To allow additional characters in user input, add those characters to the character class in the regular expression pattern.</span></span> <span data-ttu-id="f3f94-112">Örneğin, normal ifade `[^\w\.@-\\%]` deseni de bir yüzde sembolü ve bir giriş dizesi bir ters çizgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f3f94-112">For example, the regular expression pattern `[^\w\.@-\\%]` also allows a percentage symbol and a backslash in an input string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3f94-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f3f94-113">See also</span></span>

- [<span data-ttu-id="f3f94-114">.NET Düzenli İfadeler</span><span class="sxs-lookup"><span data-stu-id="f3f94-114">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
