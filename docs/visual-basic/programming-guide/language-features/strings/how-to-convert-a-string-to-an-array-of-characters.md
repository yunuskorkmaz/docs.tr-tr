---
title: "Nasıl yapılır: Visual Basic'te karakter için bir dizeye dönüştürün"
ms.date: 07/20/2015
helpviewer_keywords:
- character arrays [Visual Basic], converting strings
- arrays [Visual Basic], converting strings to
- examples [Visual Basic], string conversion
- strings [Visual Basic], converting to arrays
- string conversion [Visual Basic], arrays
ms.assetid: 1b54b686-ab29-413b-adce-6bd5422376eb
ms.openlocfilehash: 63368f41aec674922ae44a3f1c9816709b981c9b
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974412"
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a><span data-ttu-id="ae8d0-102">Nasıl yapılır: Visual Basic'te karakter için bir dizeye dönüştürün</span><span class="sxs-lookup"><span data-stu-id="ae8d0-102">How to: Convert a String to an Array of Characters in Visual Basic</span></span>
<span data-ttu-id="ae8d0-103">Bazen, dize ve bu karakterleri ne zaman bir dizeyi ayrıştırma, dizesindeki konumlarını karakterler hakkında veriler kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="ae8d0-103">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string, such as when you are parsing a string.</span></span> <span data-ttu-id="ae8d0-104">Bu örnek, bir dizedeki dizenin çağırarak karakter nasıl alabileceğiniz gösterir <xref:System.String.ToCharArray%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ae8d0-104">This example shows how you can get an array of the characters in a string by calling the string's <xref:System.String.ToCharArray%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae8d0-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="ae8d0-105">Example</span></span>  
 <span data-ttu-id="ae8d0-106">Bu örnek, bir dizeye bölme gösterir. bir `Char` dizi ve bir dizeye bölme bir `String` , Unicode karakterler dizisi.</span><span class="sxs-lookup"><span data-stu-id="ae8d0-106">This example demonstrates how to split a string into a `Char` array, and how to split a string into a `String` array of its Unicode text characters.</span></span> <span data-ttu-id="ae8d0-107">İki veya daha fazla Unicode metin karakterleri oluşturulabildikleri Bu ayrım sebebi `Char` karakter (bir yedek çifti ya da bir birleştirme gibi karakter dizisi).</span><span class="sxs-lookup"><span data-stu-id="ae8d0-107">The reason for this distinction is that Unicode text characters can be composed of two or more `Char` characters (such as a surrogate pair or a combining character sequence).</span></span> <span data-ttu-id="ae8d0-108">Daha fazla bilgi için <xref:System.Globalization.TextElementEnumerator> ve [Unicode standart](https://www.unicode.org/standard/standard.html).</span><span class="sxs-lookup"><span data-stu-id="ae8d0-108">For more information, see <xref:System.Globalization.TextElementEnumerator> and [The Unicode Standard](https://www.unicode.org/standard/standard.html).</span></span>  
  
 [!code-vb[VbVbalrStrings#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#75)]  
  
## <a name="example"></a><span data-ttu-id="ae8d0-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="ae8d0-109">Example</span></span>  
 <span data-ttu-id="ae8d0-110">Bir dize, Unicode metin karakterlere bölmek daha zordur, ancak bu görsel bir dize temsilini hakkında bilgi almanız gerekiyorsa şarttır.</span><span class="sxs-lookup"><span data-stu-id="ae8d0-110">It is more difficult to split a string into its Unicode text characters, but this is necessary if you need information about the visual representation of a string.</span></span> <span data-ttu-id="ae8d0-111">Bu örnekte <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> dizesini oluşturan Unicode karakterler hakkında bilgi almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ae8d0-111">This example uses the <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> method to get information about the Unicode text characters that make up a string.</span></span>  
  
 [!code-vb[VbVbalrStrings#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#76)]  
  
## <a name="see-also"></a><span data-ttu-id="ae8d0-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae8d0-112">See also</span></span>
- <xref:System.String.Chars%2A>
- <xref:System.Globalization.StringInfo?displayProperty=nameWithType>
- [<span data-ttu-id="ae8d0-113">Nasıl yapılır: Karakterleri dizelere erişim</span><span class="sxs-lookup"><span data-stu-id="ae8d0-113">How to: Access Characters in Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-access-characters-in-strings.md)
- [<span data-ttu-id="ae8d0-114">Dizeler ve Visual Basic'te diğer veri türleri arasında dönüştürme</span><span class="sxs-lookup"><span data-stu-id="ae8d0-114">Converting Between Strings and Other Data Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)
- [<span data-ttu-id="ae8d0-115">Dizeler</span><span class="sxs-lookup"><span data-stu-id="ae8d0-115">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
