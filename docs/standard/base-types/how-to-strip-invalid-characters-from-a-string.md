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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a3bbd25e40607bd316f1bbab974174fe5433770f
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46537910"
---
# <a name="how-to-strip-invalid-characters-from-a-string"></a><span data-ttu-id="8dd59-102">Nasıl yapılır: Dizeden Geçersiz Karakterleri Çıkartma</span><span class="sxs-lookup"><span data-stu-id="8dd59-102">How to: Strip Invalid Characters from a String</span></span>
<span data-ttu-id="8dd59-103">Aşağıdaki örnek, statik kullanır <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> yöntemi bir dizeden geçersiz karakterleri kaldırın.</span><span class="sxs-lookup"><span data-stu-id="8dd59-103">The following example uses the static <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> method to strip invalid characters from a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8dd59-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="8dd59-104">Example</span></span>  
 <span data-ttu-id="8dd59-105">Kullanabileceğiniz `CleanInput` kullanıcı girişi kabul eden bir metin alanına girilen zararlı karakter Kendiyle Bu örnekte tanımlanan yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8dd59-105">You can use the `CleanInput` method defined in this example to strip potentially harmful characters that have been entered into a text field that accepts user input.</span></span> <span data-ttu-id="8dd59-106">Bu durumda, `CleanInput` nokta (.) dışındaki tüm alfasayısal olmayan karakterleri çıkış sembol kaldırır. (@), tire (-) ve kalan dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="8dd59-106">In this case, `CleanInput` strips out all nonalphanumeric characters except periods (.), at symbols (@), and hyphens (-), and returns the remaining string.</span></span> <span data-ttu-id="8dd59-107">Ancak, bir giriş dizesinde dahil edilmemesi gereken herhangi bir karakter çıkış kaldırır, böylece normal ifade deseni değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8dd59-107">However, you can modify the regular expression pattern so that it strips out any characters that should not be included in an input string.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/vb/Example.vb#1)]  
  
 <span data-ttu-id="8dd59-108">Normal ifade deseni `[^\w\.@-]` bir sözcük karakteri olmayan herhangi bir karakterle eşleşen bir süresi, bir sembol veya tire @.</span><span class="sxs-lookup"><span data-stu-id="8dd59-108">The regular expression pattern `[^\w\.@-]` matches any character that is not a word character, a period, an @ symbol, or a hyphen.</span></span> <span data-ttu-id="8dd59-109">Bir sözcük karakteri, herhangi bir harf, ondalık basamak veya alt çizgi gibi noktalama Bağlayıcısı ' dir.</span><span class="sxs-lookup"><span data-stu-id="8dd59-109">A word character is any letter, decimal digit, or punctuation connector such as an underscore.</span></span> <span data-ttu-id="8dd59-110">Bu desenle eşleşen herhangi bir karakterle değiştirilir <xref:System.String.Empty?displayProperty=nameWithType>, değiştirme deseni tarafından tanımlanan bir dize olduğu.</span><span class="sxs-lookup"><span data-stu-id="8dd59-110">Any character that matches this pattern is replaced by <xref:System.String.Empty?displayProperty=nameWithType>, which is the string defined by the replacement pattern.</span></span> <span data-ttu-id="8dd59-111">Uygulamasında kullanıcı girdisi ek karakterler izin vermek için bu karakterler normal ifade deseninde karakter sınıfı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8dd59-111">To allow additional characters in user input, add those characters to the character class in the regular expression pattern.</span></span> <span data-ttu-id="8dd59-112">Örneğin, normal ifade deseni `[^\w\.@-\\%]` bir giriş dizesindeki bir yüzde sembolü ve ters eğik çizgi de sağlar.</span><span class="sxs-lookup"><span data-stu-id="8dd59-112">For example, the regular expression pattern `[^\w\.@-\\%]` also allows a percentage symbol and a backslash in an input string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dd59-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8dd59-113">See also</span></span>

- [<span data-ttu-id="8dd59-114">.NET normal ifadeler</span><span class="sxs-lookup"><span data-stu-id="8dd59-114">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
