---
title: "Nasıl yapılır: Visual Basic'te Bir Dizeyi Karakter Dizilerine Dönüştürme"
ms.date: 07/20/2015
helpviewer_keywords:
- character arrays [Visual Basic], converting strings
- arrays [Visual Basic], converting strings to
- examples [Visual Basic], string conversion
- strings [Visual Basic], converting to arrays
- string conversion [Visual Basic], arrays
ms.assetid: 1b54b686-ab29-413b-adce-6bd5422376eb
ms.openlocfilehash: cc12b70cddcb93a72b4421a8ddd93542ef84f55b
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/26/2018
ms.locfileid: "50041160"
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a><span data-ttu-id="21a89-102">Nasıl yapılır: Visual Basic'te Bir Dizeyi Karakter Dizilerine Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="21a89-102">How to: Convert a String to an Array of Characters in Visual Basic</span></span>
<span data-ttu-id="21a89-103">Bazen, dize ve bu karakterleri ne zaman bir dizeyi ayrıştırma, dizesindeki konumlarını karakterler hakkında veriler kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="21a89-103">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string, such as when you are parsing a string.</span></span> <span data-ttu-id="21a89-104">Bu örnek, bir dizedeki dizenin çağırarak karakter nasıl alabileceğiniz gösterir <xref:System.String.ToCharArray%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="21a89-104">This example shows how you can get an array of the characters in a string by calling the string's <xref:System.String.ToCharArray%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21a89-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="21a89-105">Example</span></span>  
 <span data-ttu-id="21a89-106">Bu örnek, bir dizeye bölme gösterir. bir `Char` dizi ve bir dizeye bölme bir `String` , Unicode karakterler dizisi.</span><span class="sxs-lookup"><span data-stu-id="21a89-106">This example demonstrates how to split a string into a `Char` array, and how to split a string into a `String` array of its Unicode text characters.</span></span> <span data-ttu-id="21a89-107">İki veya daha fazla Unicode metin karakterleri oluşturulabildikleri Bu ayrım sebebi `Char` karakter (bir yedek çifti ya da bir birleştirme gibi karakter dizisi).</span><span class="sxs-lookup"><span data-stu-id="21a89-107">The reason for this distinction is that Unicode text characters can be composed of two or more `Char` characters (such as a surrogate pair or a combining character sequence).</span></span> <span data-ttu-id="21a89-108">Daha fazla bilgi için <xref:System.Globalization.TextElementEnumerator> ve [Unicode standart](https://www.unicode.org/standard/standard.html).</span><span class="sxs-lookup"><span data-stu-id="21a89-108">For more information, see <xref:System.Globalization.TextElementEnumerator> and [The Unicode Standard](https://www.unicode.org/standard/standard.html).</span></span>  
  
 [!code-vb[VbVbalrStrings#75](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="21a89-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="21a89-109">Example</span></span>  
 <span data-ttu-id="21a89-110">Bir dize, Unicode metin karakterlere bölmek daha zordur, ancak bu görsel bir dize temsilini hakkında bilgi almanız gerekiyorsa şarttır.</span><span class="sxs-lookup"><span data-stu-id="21a89-110">It is more difficult to split a string into its Unicode text characters, but this is necessary if you need information about the visual representation of a string.</span></span> <span data-ttu-id="21a89-111">Bu örnekte <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> dizesini oluşturan Unicode karakterler hakkında bilgi almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="21a89-111">This example uses the <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> method to get information about the Unicode text characters that make up a string.</span></span>  
  
 [!code-vb[VbVbalrStrings#76](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="21a89-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="21a89-112">See Also</span></span>  
 <xref:System.String.Chars%2A>  
 <xref:System.Globalization.StringInfo?displayProperty=nameWithType>  
 [<span data-ttu-id="21a89-113">Nasıl Yapılır: Dizelerdeki Karakterlere Erişme</span><span class="sxs-lookup"><span data-stu-id="21a89-113">How to: Access Characters in Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-access-characters-in-strings.md)  
 [<span data-ttu-id="21a89-114">Dizeler ve Visual Basic'te diğer veri türleri arasında dönüştürme</span><span class="sxs-lookup"><span data-stu-id="21a89-114">Converting Between Strings and Other Data Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)  
 [<span data-ttu-id="21a89-115">Dizeler</span><span class="sxs-lookup"><span data-stu-id="21a89-115">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
