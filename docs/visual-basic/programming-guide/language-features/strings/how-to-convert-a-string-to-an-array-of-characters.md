---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: bir dizeyi Visual Basic bir karakter dizisine dönüştürme'
title: 'Nasıl yapılır: Bir Dizeyi Karakter Dizilerine Dönüştürme'
ms.date: 07/20/2015
helpviewer_keywords:
- character arrays [Visual Basic], converting strings
- arrays [Visual Basic], converting strings to
- examples [Visual Basic], string conversion
- strings [Visual Basic], converting to arrays
- string conversion [Visual Basic], arrays
ms.assetid: 1b54b686-ab29-413b-adce-6bd5422376eb
ms.openlocfilehash: f85b0801cf013e207eacd70a256a3ed0a8dc7887
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100476156"
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a><span data-ttu-id="1ad98-103">Nasıl yapılır: Visual Basic'te Bir Dizeyi Karakter Dizilerine Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="1ad98-103">How to: Convert a String to an Array of Characters in Visual Basic</span></span>

<span data-ttu-id="1ad98-104">Bazen dizinizdeki karakterlerle ilgili verilerin ve dizinizdeki karakterlerin (örneğin, bir dizeyi ayrıştırırken) bulunduğu konumlarda olması yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="1ad98-104">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string, such as when you are parsing a string.</span></span> <span data-ttu-id="1ad98-105">Bu örnek, dizenin metodunu çağırarak bir dizedeki karakterlerin bir dizisini nasıl kullanabileceğinizi gösterir <xref:System.String.ToCharArray%2A> .</span><span class="sxs-lookup"><span data-stu-id="1ad98-105">This example shows how you can get an array of the characters in a string by calling the string's <xref:System.String.ToCharArray%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ad98-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="1ad98-106">Example</span></span>  

 <span data-ttu-id="1ad98-107">Bu örnekte bir dizenin bir diziye nasıl bölüneceği `Char` ve bir dizenin `String` Unicode metin karakterlerinin dizisine bölünmesi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1ad98-107">This example demonstrates how to split a string into a `Char` array, and how to split a string into a `String` array of its Unicode text characters.</span></span> <span data-ttu-id="1ad98-108">Bu farkın nedeni, Unicode metin karakterlerinin iki veya daha fazla `Char` karakterden (örneğin, bir vekil çifti veya Birleşik karakter dizisi) oluşmasının nedenidir.</span><span class="sxs-lookup"><span data-stu-id="1ad98-108">The reason for this distinction is that Unicode text characters can be composed of two or more `Char` characters (such as a surrogate pair or a combining character sequence).</span></span> <span data-ttu-id="1ad98-109">Daha fazla bilgi için bkz <xref:System.Globalization.TextElementEnumerator> . ve [Unicode standart](https://www.unicode.org/standard/standard.html).</span><span class="sxs-lookup"><span data-stu-id="1ad98-109">For more information, see <xref:System.Globalization.TextElementEnumerator> and [The Unicode Standard](https://www.unicode.org/standard/standard.html).</span></span>  
  
 [!code-vb[VbVbalrStrings#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#75)]  
  
## <a name="example"></a><span data-ttu-id="1ad98-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="1ad98-110">Example</span></span>  

 <span data-ttu-id="1ad98-111">Bir dizeyi Unicode metin karakterlerine bölmek daha zordur, ancak bir dizenin görsel temsili hakkında bilgi gerekirse bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1ad98-111">It is more difficult to split a string into its Unicode text characters, but this is necessary if you need information about the visual representation of a string.</span></span> <span data-ttu-id="1ad98-112">Bu örnek, <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> bir dizeyi oluşturan Unicode metin karakterleri hakkında bilgi almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="1ad98-112">This example uses the <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> method to get information about the Unicode text characters that make up a string.</span></span>  
  
 [!code-vb[VbVbalrStrings#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#76)]  
  
## <a name="see-also"></a><span data-ttu-id="1ad98-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ad98-113">See also</span></span>

- <xref:System.String.Chars%2A>
- <xref:System.Globalization.StringInfo?displayProperty=nameWithType>
- [<span data-ttu-id="1ad98-114">Nasıl Yapılır: Dizelerdeki Karakterlere Erişme</span><span class="sxs-lookup"><span data-stu-id="1ad98-114">How to: Access Characters in Strings</span></span>](how-to-access-characters-in-strings.md)
- [<span data-ttu-id="1ad98-115">Visual Basic'de Dizeler ve Diğer Veri Türleri Arasında Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="1ad98-115">Converting Between Strings and Other Data Types in Visual Basic</span></span>](converting-between-strings-and-other-data-types.md)
- [<span data-ttu-id="1ad98-116">Dizeler</span><span class="sxs-lookup"><span data-stu-id="1ad98-116">Strings</span></span>](index.md)
