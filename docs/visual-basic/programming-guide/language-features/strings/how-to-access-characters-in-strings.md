---
title: "Nasıl yapılır: Visual Basic'de Dizelerdeki karakterlere erişim"
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
ms.openlocfilehash: 840a769b0bb322ef7b878a312437c5ec200ab074
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834497"
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a><span data-ttu-id="a054a-102">Nasıl yapılır: Visual Basic'de Dizelerdeki karakterlere erişim</span><span class="sxs-lookup"><span data-stu-id="a054a-102">How to: Access Characters in Strings in Visual Basic</span></span>
<span data-ttu-id="a054a-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.String.Chars%2A> belirtilen konumda bir dizedeki karakter erişmek için özelliği.</span><span class="sxs-lookup"><span data-stu-id="a054a-103">This example demonstrates how to use the <xref:System.String.Chars%2A> property to access the character at the specified location in a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a054a-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="a054a-104">Example</span></span>  
 <span data-ttu-id="a054a-105">Bazen, dize ve bu karakterleri, dize içindeki konumunu karakterler hakkında veriler kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="a054a-105">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string.</span></span> <span data-ttu-id="a054a-106">Bir dizenin karakter dizisi olarak düşünebilirsiniz (`Char` örnekleri); belirli bir karakterin bu karakter dizinini başvurarak alabilirsiniz <xref:System.String.Chars%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="a054a-106">You can think of a string as an array of characters (`Char` instances); you can retrieve a particular character by referencing the index of that character through the <xref:System.String.Chars%2A> property.</span></span>  
  
 [!code-vb[VbVbalrStrings#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#49)]  
  
 <span data-ttu-id="a054a-107">`index` Parametresinin <xref:System.String.Chars%2A> özelliği sıfır tabanlı.</span><span class="sxs-lookup"><span data-stu-id="a054a-107">The `index` parameter of the <xref:System.String.Chars%2A> property is zero-based.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="a054a-108">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="a054a-108">Robust Programming</span></span>  
 <span data-ttu-id="a054a-109"><xref:System.String.Chars%2A> Özelliği belirtilen konumdaki karakteri döndürür.</span><span class="sxs-lookup"><span data-stu-id="a054a-109">The <xref:System.String.Chars%2A> property returns the character at the specified position.</span></span> <span data-ttu-id="a054a-110">Ancak, bazı Unicode karakterler birden fazla karakter gösterilebilir.</span><span class="sxs-lookup"><span data-stu-id="a054a-110">However, some Unicode characters can be represented by more than one character.</span></span> <span data-ttu-id="a054a-111">Unicode karakter ile çalışma konusunda daha fazla bilgi için bkz. [nasıl yapılır: Bir dizeyi karakter dizilerine dönüştürme](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).</span><span class="sxs-lookup"><span data-stu-id="a054a-111">For more information on how to work with Unicode characters, see [How to: Convert a String to an Array of Characters](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).</span></span>  
  
 <span data-ttu-id="a054a-112"><xref:System.String.Chars%2A> Özelliği oluşturur bir <xref:System.IndexOutOfRangeException> özel durum, `index` parametresi değerinden büyük veya eşit bir dizenin uzunluğunu veya onu küçükse sıfırdan</span><span class="sxs-lookup"><span data-stu-id="a054a-112">The <xref:System.String.Chars%2A> property throws an <xref:System.IndexOutOfRangeException> exception if the `index` parameter is greater than or equal to the length of the string, or if it is less than zero</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a054a-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a054a-113">See also</span></span>

- <xref:System.String.Chars%2A>
- [<span data-ttu-id="a054a-114">Nasıl yapılır: Bir dizeyi karakter dizilerine dönüştürme</span><span class="sxs-lookup"><span data-stu-id="a054a-114">How to: Convert a String to an Array of Characters</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)
- [<span data-ttu-id="a054a-115">Dizeler ve Visual Basic'te diğer veri türleri arasında dönüştürme</span><span class="sxs-lookup"><span data-stu-id="a054a-115">Converting Between Strings and Other Data Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)
- [<span data-ttu-id="a054a-116">Dizeler</span><span class="sxs-lookup"><span data-stu-id="a054a-116">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
