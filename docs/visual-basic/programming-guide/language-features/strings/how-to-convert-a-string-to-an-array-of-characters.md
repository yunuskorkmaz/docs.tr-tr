---
title: 'Nasıl yapılır: Bir Dizeyi Karakter Dizilerine Dönüştürme'
ms.date: 07/20/2015
helpviewer_keywords:
- character arrays [Visual Basic], converting strings
- arrays [Visual Basic], converting strings to
- examples [Visual Basic], string conversion
- strings [Visual Basic], converting to arrays
- string conversion [Visual Basic], arrays
ms.assetid: 1b54b686-ab29-413b-adce-6bd5422376eb
ms.openlocfilehash: d2f7128f97e576d37216d3aa9736921f13f77004
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352455"
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a><span data-ttu-id="d67bd-102">Nasıl yapılır: Visual Basic'te Bir Dizeyi Karakter Dizilerine Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="d67bd-102">How to: Convert a String to an Array of Characters in Visual Basic</span></span>
<span data-ttu-id="d67bd-103">Bazen dizinizdeki karakterlerle ilgili verilerin ve dizinizdeki karakterlerin (örneğin, bir dizeyi ayrıştırırken) bulunduğu konumlarda olması yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="d67bd-103">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string, such as when you are parsing a string.</span></span> <span data-ttu-id="d67bd-104">Bu örnekte, dizenin <xref:System.String.ToCharArray%2A> yöntemini çağırarak bir dizedeki karakterlerin dizisini nasıl alabileceğiniz gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d67bd-104">This example shows how you can get an array of the characters in a string by calling the string's <xref:System.String.ToCharArray%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d67bd-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="d67bd-105">Example</span></span>  
 <span data-ttu-id="d67bd-106">Bu örnek, bir dizenin bir `Char` dizisine nasıl bölüneceği ve bir dizenin Unicode metin karakterlerinin `String` dizisine nasıl bölüneceği gösterir.</span><span class="sxs-lookup"><span data-stu-id="d67bd-106">This example demonstrates how to split a string into a `Char` array, and how to split a string into a `String` array of its Unicode text characters.</span></span> <span data-ttu-id="d67bd-107">Bu farkın nedeni, Unicode metin karakterlerinin iki veya daha fazla `Char` karakterden (bir vekil çifti veya Birleşik karakter dizisi gibi) oluşmasının nedenidir.</span><span class="sxs-lookup"><span data-stu-id="d67bd-107">The reason for this distinction is that Unicode text characters can be composed of two or more `Char` characters (such as a surrogate pair or a combining character sequence).</span></span> <span data-ttu-id="d67bd-108">Daha fazla bilgi için bkz. <xref:System.Globalization.TextElementEnumerator> ve [Unicode standart](https://www.unicode.org/standard/standard.html).</span><span class="sxs-lookup"><span data-stu-id="d67bd-108">For more information, see <xref:System.Globalization.TextElementEnumerator> and [The Unicode Standard](https://www.unicode.org/standard/standard.html).</span></span>  
  
 [!code-vb[VbVbalrStrings#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#75)]  
  
## <a name="example"></a><span data-ttu-id="d67bd-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="d67bd-109">Example</span></span>  
 <span data-ttu-id="d67bd-110">Bir dizeyi Unicode metin karakterlerine bölmek daha zordur, ancak bir dizenin görsel temsili hakkında bilgi gerekirse bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d67bd-110">It is more difficult to split a string into its Unicode text characters, but this is necessary if you need information about the visual representation of a string.</span></span> <span data-ttu-id="d67bd-111">Bu örnek, bir dizeyi oluşturan Unicode metin karakterleri hakkında bilgi almak için <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d67bd-111">This example uses the <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> method to get information about the Unicode text characters that make up a string.</span></span>  
  
 [!code-vb[VbVbalrStrings#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#76)]  
  
## <a name="see-also"></a><span data-ttu-id="d67bd-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d67bd-112">See also</span></span>

- <xref:System.String.Chars%2A>
- <xref:System.Globalization.StringInfo?displayProperty=nameWithType>
- [<span data-ttu-id="d67bd-113">Nasıl Yapılır: Dizelerdeki Karakterlere Erişme</span><span class="sxs-lookup"><span data-stu-id="d67bd-113">How to: Access Characters in Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-access-characters-in-strings.md)
- [<span data-ttu-id="d67bd-114">Visual Basic dizeler ve diğer veri türleri arasında dönüştürme</span><span class="sxs-lookup"><span data-stu-id="d67bd-114">Converting Between Strings and Other Data Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)
- [<span data-ttu-id="d67bd-115">Dizeler</span><span class="sxs-lookup"><span data-stu-id="d67bd-115">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
