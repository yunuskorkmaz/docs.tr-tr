---
title: "Nasıl Yapılır: Visual Basic'de Dizelerdeki Karakterlere Erişme"
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
ms.openlocfilehash: 48507cade639660e6ce36697975d09fb29206c20
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649158"
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a><span data-ttu-id="57869-102">Nasıl Yapılır: Visual Basic'de Dizelerdeki Karakterlere Erişme</span><span class="sxs-lookup"><span data-stu-id="57869-102">How to: Access Characters in Strings in Visual Basic</span></span>
<span data-ttu-id="57869-103">Bu örnek nasıl kullanılacağı ortaya <xref:System.String.Chars%2A> belirtilen konumda bir dizedeki karakter erişmek için özellik.</span><span class="sxs-lookup"><span data-stu-id="57869-103">This example demonstrates how to use the <xref:System.String.Chars%2A> property to access the character at the specified location in a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57869-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="57869-104">Example</span></span>  
 <span data-ttu-id="57869-105">Bazen dizenizi ve bu karakterleri dizenizi içinde konumlarını karakterler hakkında veriler kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="57869-105">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string.</span></span> <span data-ttu-id="57869-106">Bir dize bir karakter dizisi olarak düşünebilirsiniz (`Char` örnekleri); belirli bir karakterin bu karakter dizinini başvurarak alabilirsiniz <xref:System.String.Chars%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="57869-106">You can think of a string as an array of characters (`Char` instances); you can retrieve a particular character by referencing the index of that character through the <xref:System.String.Chars%2A> property.</span></span>  
  
 [!code-vb[VbVbalrStrings#49](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-access-characters-in-strings_1.vb)]  
  
 <span data-ttu-id="57869-107">`index` Parametresinin <xref:System.String.Chars%2A> özelliği sıfır tabanlı.</span><span class="sxs-lookup"><span data-stu-id="57869-107">The `index` parameter of the <xref:System.String.Chars%2A> property is zero-based.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="57869-108">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="57869-108">Robust Programming</span></span>  
 <span data-ttu-id="57869-109"><xref:System.String.Chars%2A> Özelliği, belirtilen konumdaki karakteri döndürür.</span><span class="sxs-lookup"><span data-stu-id="57869-109">The <xref:System.String.Chars%2A> property returns the character at the specified position.</span></span> <span data-ttu-id="57869-110">Ancak, bazı Unicode karakterler birden fazla karakteri temsil edilebilir.</span><span class="sxs-lookup"><span data-stu-id="57869-110">However, some Unicode characters can be represented by more than one character.</span></span> <span data-ttu-id="57869-111">Unicode karakter ile çalışma konusunda daha fazla bilgi için bkz: [nasıl yapılır: bir dizeyi, bir dizi karakter dönüştürme](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).</span><span class="sxs-lookup"><span data-stu-id="57869-111">For more information on how to work with Unicode characters, see [How to: Convert a String to an Array of Characters](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).</span></span>  
  
 <span data-ttu-id="57869-112"><xref:System.String.Chars%2A> Özelliği atar bir <xref:System.IndexOutOfRangeException> özel durum, `index` parametredir dize uzunluğu eşit veya daha büyük veya bu küçükse sıfır</span><span class="sxs-lookup"><span data-stu-id="57869-112">The <xref:System.String.Chars%2A> property throws an <xref:System.IndexOutOfRangeException> exception if the `index` parameter is greater than or equal to the length of the string, or if it is less than zero</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57869-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="57869-113">See Also</span></span>  
 <xref:System.String.Chars%2A>  
 [<span data-ttu-id="57869-114">Nasıl yapılır: Bir Dizeyi Karakter Dizilerine Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="57869-114">How to: Convert a String to an Array of Characters</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)  
 [<span data-ttu-id="57869-115">Dizeler ve diğer Visual Basic veri türleri arasında dönüştürme</span><span class="sxs-lookup"><span data-stu-id="57869-115">Converting Between Strings and Other Data Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)  
 [<span data-ttu-id="57869-116">Dizeler</span><span class="sxs-lookup"><span data-stu-id="57869-116">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
