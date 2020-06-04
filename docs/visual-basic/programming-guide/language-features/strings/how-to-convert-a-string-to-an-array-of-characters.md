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
ms.openlocfilehash: eca8cd7be8da1f6149dadf1e9edeab5e5225ab9f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360676"
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a><span data-ttu-id="df843-102">Nasıl yapılır: Visual Basic'te Bir Dizeyi Karakter Dizilerine Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="df843-102">How to: Convert a String to an Array of Characters in Visual Basic</span></span>
<span data-ttu-id="df843-103">Bazen dizinizdeki karakterlerle ilgili verilerin ve dizinizdeki karakterlerin (örneğin, bir dizeyi ayrıştırırken) bulunduğu konumlarda olması yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="df843-103">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string, such as when you are parsing a string.</span></span> <span data-ttu-id="df843-104">Bu örnek, dizenin metodunu çağırarak bir dizedeki karakterlerin bir dizisini nasıl kullanabileceğinizi gösterir <xref:System.String.ToCharArray%2A> .</span><span class="sxs-lookup"><span data-stu-id="df843-104">This example shows how you can get an array of the characters in a string by calling the string's <xref:System.String.ToCharArray%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df843-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="df843-105">Example</span></span>  
 <span data-ttu-id="df843-106">Bu örnekte bir dizenin bir diziye nasıl bölüneceği `Char` ve bir dizenin `String` Unicode metin karakterlerinin dizisine bölünmesi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="df843-106">This example demonstrates how to split a string into a `Char` array, and how to split a string into a `String` array of its Unicode text characters.</span></span> <span data-ttu-id="df843-107">Bu farkın nedeni, Unicode metin karakterlerinin iki veya daha fazla `Char` karakterden (örneğin, bir vekil çifti veya Birleşik karakter dizisi) oluşmasının nedenidir.</span><span class="sxs-lookup"><span data-stu-id="df843-107">The reason for this distinction is that Unicode text characters can be composed of two or more `Char` characters (such as a surrogate pair or a combining character sequence).</span></span> <span data-ttu-id="df843-108">Daha fazla bilgi için bkz <xref:System.Globalization.TextElementEnumerator> . ve [Unicode standart](https://www.unicode.org/standard/standard.html).</span><span class="sxs-lookup"><span data-stu-id="df843-108">For more information, see <xref:System.Globalization.TextElementEnumerator> and [The Unicode Standard](https://www.unicode.org/standard/standard.html).</span></span>  
  
 [!code-vb[VbVbalrStrings#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#75)]  
  
## <a name="example"></a><span data-ttu-id="df843-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="df843-109">Example</span></span>  
 <span data-ttu-id="df843-110">Bir dizeyi Unicode metin karakterlerine bölmek daha zordur, ancak bir dizenin görsel temsili hakkında bilgi gerekirse bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="df843-110">It is more difficult to split a string into its Unicode text characters, but this is necessary if you need information about the visual representation of a string.</span></span> <span data-ttu-id="df843-111">Bu örnek, <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> bir dizeyi oluşturan Unicode metin karakterleri hakkında bilgi almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="df843-111">This example uses the <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> method to get information about the Unicode text characters that make up a string.</span></span>  
  
 [!code-vb[VbVbalrStrings#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#76)]  
  
## <a name="see-also"></a><span data-ttu-id="df843-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="df843-112">See also</span></span>

- <xref:System.String.Chars%2A>
- <xref:System.Globalization.StringInfo?displayProperty=nameWithType>
- [<span data-ttu-id="df843-113">Nasıl Yapılır: Dizelerdeki Karakterlere Erişme</span><span class="sxs-lookup"><span data-stu-id="df843-113">How to: Access Characters in Strings</span></span>](how-to-access-characters-in-strings.md)
- [<span data-ttu-id="df843-114">Visual Basic'de Dizeler ve Diğer Veri Türleri Arasında Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="df843-114">Converting Between Strings and Other Data Types in Visual Basic</span></span>](converting-between-strings-and-other-data-types.md)
- [<span data-ttu-id="df843-115">Dizeler</span><span class="sxs-lookup"><span data-stu-id="df843-115">Strings</span></span>](index.md)
