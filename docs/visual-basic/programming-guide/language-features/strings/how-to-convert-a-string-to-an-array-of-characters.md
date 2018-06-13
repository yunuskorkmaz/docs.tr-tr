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
ms.openlocfilehash: c109143601e304b1ec15a60c71d65fe6bd15aae8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648625"
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a><span data-ttu-id="dbee4-102">Nasıl yapılır: Visual Basic'te Bir Dizeyi Karakter Dizilerine Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="dbee4-102">How to: Convert a String to an Array of Characters in Visual Basic</span></span>
<span data-ttu-id="dbee4-103">Bazen dizenizi ve bu karakterleri ne zaman bir dizesini ayrıştırma, dizesindeki konumlarını karakterler hakkında veriler kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="dbee4-103">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string, such as when you are parsing a string.</span></span> <span data-ttu-id="dbee4-104">Bu örnek, bir dize dizesinin çağırarak karakter nasıl erişebileceğini gösterir <xref:System.String.ToCharArray%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="dbee4-104">This example shows how you can get an array of the characters in a string by calling the string's <xref:System.String.ToCharArray%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dbee4-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="dbee4-105">Example</span></span>  
 <span data-ttu-id="dbee4-106">Bu örnek, bir dizeye bölüneceği gösterilmiştir bir `Char` dizi ve nasıl bir dizeye bölüneceği bir `String` kendi Unicode metin karakter dizisi.</span><span class="sxs-lookup"><span data-stu-id="dbee4-106">This example demonstrates how to split a string into a `Char` array, and how to split a string into a `String` array of its Unicode text characters.</span></span> <span data-ttu-id="dbee4-107">Bu ayrım iki veya daha fazla Unicode metin karakterlerinin birleştirilebilen nedeni `Char` karakterleri (bir yedek çifti ya da bir birleştirme gibi karakter dizisi).</span><span class="sxs-lookup"><span data-stu-id="dbee4-107">The reason for this distinction is that Unicode text characters can be composed of two or more `Char` characters (such as a surrogate pair or a combining character sequence).</span></span> <span data-ttu-id="dbee4-108">Daha fazla bilgi için bkz: <xref:System.Globalization.TextElementEnumerator> ve "Unicode standart" konumundaki http://www.unicode.org.</span><span class="sxs-lookup"><span data-stu-id="dbee4-108">For more information, see <xref:System.Globalization.TextElementEnumerator> and "The Unicode Standard" at http://www.unicode.org.</span></span>  
  
 [!code-vb[VbVbalrStrings#75](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="dbee4-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="dbee4-109">Example</span></span>  
 <span data-ttu-id="dbee4-110">Bir dize, Unicode metin karakterlere bölmek daha da zor olan, ancak bu görsel bir dize gösterimini hakkında bilgi istiyorsanız gereklidir.</span><span class="sxs-lookup"><span data-stu-id="dbee4-110">It is more difficult to split a string into its Unicode text characters, but this is necessary if you need information about the visual representation of a string.</span></span> <span data-ttu-id="dbee4-111">Bu örnekte <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> bir dize olun Unicode metin karakterler hakkında bilgi almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="dbee4-111">This example uses the <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> method to get information about the Unicode text characters that make up a string.</span></span>  
  
 [!code-vb[VbVbalrStrings#76](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="dbee4-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dbee4-112">See Also</span></span>  
 <xref:System.String.Chars%2A>  
 <xref:System.Globalization.StringInfo?displayProperty=nameWithType>  
 [<span data-ttu-id="dbee4-113">Nasıl Yapılır: Dizelerdeki Karakterlere Erişme</span><span class="sxs-lookup"><span data-stu-id="dbee4-113">How to: Access Characters in Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-access-characters-in-strings.md)  
 [<span data-ttu-id="dbee4-114">Dizeler ve diğer Visual Basic veri türleri arasında dönüştürme</span><span class="sxs-lookup"><span data-stu-id="dbee4-114">Converting Between Strings and Other Data Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)  
 [<span data-ttu-id="dbee4-115">Dizeler</span><span class="sxs-lookup"><span data-stu-id="dbee4-115">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
