---
title: 'Nasıl Yapılır: Dizelerdeki Karakterlere Erişme'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
ms.openlocfilehash: 44a021ed3ce1d10613cf6ab7c959c62feec6046c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352457"
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a><span data-ttu-id="c6178-102">Nasıl Yapılır: Visual Basic'de Dizelerdeki Karakterlere Erişme</span><span class="sxs-lookup"><span data-stu-id="c6178-102">How to: Access Characters in Strings in Visual Basic</span></span>
<span data-ttu-id="c6178-103">Bu örnek, bir dizedeki belirtilen konumdaki karaktere erişmek için <xref:System.String.Chars%2A> özelliğinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c6178-103">This example demonstrates how to use the <xref:System.String.Chars%2A> property to access the character at the specified location in a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6178-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="c6178-104">Example</span></span>  
 <span data-ttu-id="c6178-105">Bazen dizinizdeki karakterler ve dizeniz içindeki bu karakterlerin konumları hakkında veri olması yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="c6178-105">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string.</span></span> <span data-ttu-id="c6178-106">Dizeyi bir karakter dizisi (`Char` örnekleri) olarak düşünebilirsiniz; Bu karakterin dizinine <xref:System.String.Chars%2A> özelliği aracılığıyla başvurarak belirli bir karakteri alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6178-106">You can think of a string as an array of characters (`Char` instances); you can retrieve a particular character by referencing the index of that character through the <xref:System.String.Chars%2A> property.</span></span>  
  
 [!code-vb[VbVbalrStrings#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#49)]  
  
 <span data-ttu-id="c6178-107"><xref:System.String.Chars%2A> özelliğinin `index` parametresi sıfır tabanlıdır.</span><span class="sxs-lookup"><span data-stu-id="c6178-107">The `index` parameter of the <xref:System.String.Chars%2A> property is zero-based.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="c6178-108">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="c6178-108">Robust Programming</span></span>  
 <span data-ttu-id="c6178-109"><xref:System.String.Chars%2A> özelliği, belirtilen konumdaki karakteri döndürür.</span><span class="sxs-lookup"><span data-stu-id="c6178-109">The <xref:System.String.Chars%2A> property returns the character at the specified position.</span></span> <span data-ttu-id="c6178-110">Ancak bazı Unicode karakterler birden fazla karakterle temsil edilebilir.</span><span class="sxs-lookup"><span data-stu-id="c6178-110">However, some Unicode characters can be represented by more than one character.</span></span> <span data-ttu-id="c6178-111">Unicode karakterlerle çalışma hakkında daha fazla bilgi için bkz. [nasıl yapılır: dizeyi bir karakter dizisine dönüştürme](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).</span><span class="sxs-lookup"><span data-stu-id="c6178-111">For more information on how to work with Unicode characters, see [How to: Convert a String to an Array of Characters](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).</span></span>  
  
 <span data-ttu-id="c6178-112"><xref:System.String.Chars%2A> özelliği, `index` parametresi dizenin uzunluğuna eşit veya daha büyükse veya sıfırdan küçükse bir <xref:System.IndexOutOfRangeException> özel durum oluşturur</span><span class="sxs-lookup"><span data-stu-id="c6178-112">The <xref:System.String.Chars%2A> property throws an <xref:System.IndexOutOfRangeException> exception if the `index` parameter is greater than or equal to the length of the string, or if it is less than zero</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6178-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6178-113">See also</span></span>

- <xref:System.String.Chars%2A>
- [<span data-ttu-id="c6178-114">Nasıl yapılır: Bir Dizeyi Karakter Dizilerine Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="c6178-114">How to: Convert a String to an Array of Characters</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)
- [<span data-ttu-id="c6178-115">Visual Basic dizeler ve diğer veri türleri arasında dönüştürme</span><span class="sxs-lookup"><span data-stu-id="c6178-115">Converting Between Strings and Other Data Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)
- [<span data-ttu-id="c6178-116">Dizeler</span><span class="sxs-lookup"><span data-stu-id="c6178-116">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
