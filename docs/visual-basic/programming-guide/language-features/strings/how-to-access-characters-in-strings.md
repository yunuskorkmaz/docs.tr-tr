---
title: "Nasıl Yapılır: Visual Basic'de Dizelerdeki Karakterlere Erişme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 54d604fc08dd97e0e31f9bcec148431374e8ef8f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a><span data-ttu-id="1db07-102">Nasıl Yapılır: Visual Basic'de Dizelerdeki Karakterlere Erişme</span><span class="sxs-lookup"><span data-stu-id="1db07-102">How to: Access Characters in Strings in Visual Basic</span></span>
<span data-ttu-id="1db07-103">Bu örnek nasıl kullanılacağı ortaya <xref:System.String.Chars%2A> belirtilen konumda bir dizedeki karakter erişmek için özellik.</span><span class="sxs-lookup"><span data-stu-id="1db07-103">This example demonstrates how to use the <xref:System.String.Chars%2A> property to access the character at the specified location in a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1db07-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="1db07-104">Example</span></span>  
 <span data-ttu-id="1db07-105">Bazen dizenizi ve bu karakterleri dizenizi içinde konumlarını karakterler hakkında veriler kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="1db07-105">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string.</span></span> <span data-ttu-id="1db07-106">Bir dize bir karakter dizisi olarak düşünebilirsiniz (`Char` örnekleri); belirli bir karakterin bu karakter dizinini başvurarak alabilirsiniz <xref:System.String.Chars%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="1db07-106">You can think of a string as an array of characters (`Char` instances); you can retrieve a particular character by referencing the index of that character through the <xref:System.String.Chars%2A> property.</span></span>  
  
 [!code-vb[VbVbalrStrings#49](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-access-characters-in-strings_1.vb)]  
  
 <span data-ttu-id="1db07-107">`index` Parametresinin <xref:System.String.Chars%2A> özelliği sıfır tabanlı.</span><span class="sxs-lookup"><span data-stu-id="1db07-107">The `index` parameter of the <xref:System.String.Chars%2A> property is zero-based.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="1db07-108">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="1db07-108">Robust Programming</span></span>  
 <span data-ttu-id="1db07-109"><xref:System.String.Chars%2A> Özelliği, belirtilen konumdaki karakteri döndürür.</span><span class="sxs-lookup"><span data-stu-id="1db07-109">The <xref:System.String.Chars%2A> property returns the character at the specified position.</span></span> <span data-ttu-id="1db07-110">Ancak, bazı Unicode karakterler birden fazla karakteri temsil edilebilir.</span><span class="sxs-lookup"><span data-stu-id="1db07-110">However, some Unicode characters can be represented by more than one character.</span></span> <span data-ttu-id="1db07-111">Unicode karakter ile çalışma konusunda daha fazla bilgi için bkz: [nasıl yapılır: bir dizeyi, bir dizi karakter dönüştürme](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).</span><span class="sxs-lookup"><span data-stu-id="1db07-111">For more information on how to work with Unicode characters, see [How to: Convert a String to an Array of Characters](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).</span></span>  
  
 <span data-ttu-id="1db07-112"><xref:System.String.Chars%2A> Özelliği atar bir <xref:System.IndexOutOfRangeException> özel durum, `index` parametredir dize uzunluğu eşit veya daha büyük veya bu küçükse sıfır</span><span class="sxs-lookup"><span data-stu-id="1db07-112">The <xref:System.String.Chars%2A> property throws an <xref:System.IndexOutOfRangeException> exception if the `index` parameter is greater than or equal to the length of the string, or if it is less than zero</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1db07-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1db07-113">See Also</span></span>  
 <xref:System.String.Chars%2A>  
 [<span data-ttu-id="1db07-114">Nasıl yapılır: bir dizeyi karakter dizisi için dönüştürme</span><span class="sxs-lookup"><span data-stu-id="1db07-114">How to: Convert a String to an Array of Characters</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)  
 [<span data-ttu-id="1db07-115">Dizeler ve diğer Visual Basic veri türleri arasında dönüştürme</span><span class="sxs-lookup"><span data-stu-id="1db07-115">Converting Between Strings and Other Data Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)  
 [<span data-ttu-id="1db07-116">Dizeleri</span><span class="sxs-lookup"><span data-stu-id="1db07-116">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
