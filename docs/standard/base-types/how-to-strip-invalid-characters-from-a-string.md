---
title: "Nasıl yapılır: Dizeden Geçersiz Karakterleri Çıkartma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 030fc003c54e122362d7ecc71675a8b197b68e48
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-strip-invalid-characters-from-a-string"></a><span data-ttu-id="e43a1-102">Nasıl yapılır: Dizeden Geçersiz Karakterleri Çıkartma</span><span class="sxs-lookup"><span data-stu-id="e43a1-102">How to: Strip Invalid Characters from a String</span></span>
<span data-ttu-id="e43a1-103">Aşağıdaki örnek, statik kullanır <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> bir dizeden geçersiz karakterleri Şerit yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e43a1-103">The following example uses the static <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> method to strip invalid characters from a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e43a1-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="e43a1-104">Example</span></span>  
 <span data-ttu-id="e43a1-105">Kullanabileceğiniz `CleanInput` Bu örnekte, kullanıcı girişi kabul eden bir metin alanına girilen zararlı olabilecek karakterleri Şerit tanımlanmış yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e43a1-105">You can use the `CleanInput` method defined in this example to strip potentially harmful characters that have been entered into a text field that accepts user input.</span></span> <span data-ttu-id="e43a1-106">Bu durumda, `CleanInput` nokta (.) dışındaki tüm alfasayısal olmayan karakterler çıkışı konumundaki simgeleri kaldırır (@), tire (-) ve kalan dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="e43a1-106">In this case, `CleanInput` strips out all nonalphanumeric characters except periods (.), at symbols (@), and hyphens (-), and returns the remaining string.</span></span> <span data-ttu-id="e43a1-107">Ancak, böylece bir giriş dizesi içinde dahil edilmemesi gereken herhangi bir karakteri çıkışı şeritler normal ifade deseni değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e43a1-107">However, you can modify the regular expression pattern so that it strips out any characters that should not be included in an input string.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/vb/Example.vb#1)]  
  
 <span data-ttu-id="e43a1-108">Normal ifade deseni `[^\w\.@-]` bir sözcük karakteriyle değil herhangi bir karakterle eşleşir bir nokta, bir simge veya tire @.</span><span class="sxs-lookup"><span data-stu-id="e43a1-108">The regular expression pattern `[^\w\.@-]` matches any character that is not a word character, a period, an @ symbol, or a hyphen.</span></span> <span data-ttu-id="e43a1-109">Bir word herhangi harf, ondalık sayı veya alt çizgi gibi noktalama bağlayıcı karakterdir.</span><span class="sxs-lookup"><span data-stu-id="e43a1-109">A word character is any letter, decimal digit, or punctuation connector such as an underscore.</span></span> <span data-ttu-id="e43a1-110">Bu desenle eşleşen herhangi bir karakter ile değiştirilir <xref:System.String.Empty?displayProperty=nameWithType>, değiştirme düzeni tarafından tanımlanan bir dize değil.</span><span class="sxs-lookup"><span data-stu-id="e43a1-110">Any character that matches this pattern is replaced by <xref:System.String.Empty?displayProperty=nameWithType>, which is the string defined by the replacement pattern.</span></span> <span data-ttu-id="e43a1-111">Uygulamasında kullanıcı girdisi ek karakterlerine izin vermek için bu karakterleri normal ifade deseni karakter sınıfında ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e43a1-111">To allow additional characters in user input, add those characters to the character class in the regular expression pattern.</span></span> <span data-ttu-id="e43a1-112">Örneğin, normal ifade deseni `[^\w\.@-\\%]` yüzdesi simge ve bir ters eğik çizgi bir giriş dizesi içinde de sağlar.</span><span class="sxs-lookup"><span data-stu-id="e43a1-112">For example, the regular expression pattern `[^\w\.@-\\%]` also allows a percentage symbol and a backslash in an input string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e43a1-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e43a1-113">See Also</span></span>  
 [<span data-ttu-id="e43a1-114">.NET normal ifadeler</span><span class="sxs-lookup"><span data-stu-id="e43a1-114">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
