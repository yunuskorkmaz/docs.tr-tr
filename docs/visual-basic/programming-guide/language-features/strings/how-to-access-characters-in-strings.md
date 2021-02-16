---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Visual Basic dizelerdeki karakterlere erişme'
title: 'Nasıl Yapılır: Dizelerdeki Karakterlere Erişme'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
ms.openlocfilehash: 373005699483dbae92df3a6fe73cc9b6318a9c61
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100476169"
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a><span data-ttu-id="aa778-103">Nasıl Yapılır: Visual Basic'de Dizelerdeki Karakterlere Erişme</span><span class="sxs-lookup"><span data-stu-id="aa778-103">How to: Access Characters in Strings in Visual Basic</span></span>

<span data-ttu-id="aa778-104">Bu örnek, <xref:System.String.Chars%2A> bir dizedeki belirtilen konumdaki karaktere erişmek için özelliğinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="aa778-104">This example demonstrates how to use the <xref:System.String.Chars%2A> property to access the character at the specified location in a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa778-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="aa778-105">Example</span></span>  

 <span data-ttu-id="aa778-106">Bazen dizinizdeki karakterler ve dizeniz içindeki bu karakterlerin konumları hakkında veri olması yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="aa778-106">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string.</span></span> <span data-ttu-id="aa778-107">Bir dizeyi bir karakter dizisi ( `Char` örnekler) olarak düşünebilirsiniz; özelliği aracılığıyla söz konusu karakterin dizinine başvurarak belirli bir karakteri alabilirsiniz <xref:System.String.Chars%2A> .</span><span class="sxs-lookup"><span data-stu-id="aa778-107">You can think of a string as an array of characters (`Char` instances); you can retrieve a particular character by referencing the index of that character through the <xref:System.String.Chars%2A> property.</span></span>  
  
 [!code-vb[VbVbalrStrings#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#49)]  
  
 <span data-ttu-id="aa778-108">`index` <xref:System.String.Chars%2A> Özelliğin parametresi sıfır tabanlıdır.</span><span class="sxs-lookup"><span data-stu-id="aa778-108">The `index` parameter of the <xref:System.String.Chars%2A> property is zero-based.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="aa778-109">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="aa778-109">Robust Programming</span></span>  

 <span data-ttu-id="aa778-110"><xref:System.String.Chars%2A>Özelliği belirtilen konumdaki karakteri döndürür.</span><span class="sxs-lookup"><span data-stu-id="aa778-110">The <xref:System.String.Chars%2A> property returns the character at the specified position.</span></span> <span data-ttu-id="aa778-111">Ancak bazı Unicode karakterler birden fazla karakterle temsil edilebilir.</span><span class="sxs-lookup"><span data-stu-id="aa778-111">However, some Unicode characters can be represented by more than one character.</span></span> <span data-ttu-id="aa778-112">Unicode karakterlerle çalışma hakkında daha fazla bilgi için bkz. [nasıl yapılır: dizeyi bir karakter dizisine dönüştürme](how-to-convert-a-string-to-an-array-of-characters.md).</span><span class="sxs-lookup"><span data-stu-id="aa778-112">For more information on how to work with Unicode characters, see [How to: Convert a String to an Array of Characters](how-to-convert-a-string-to-an-array-of-characters.md).</span></span>  
  
 <span data-ttu-id="aa778-113"><xref:System.String.Chars%2A> <xref:System.IndexOutOfRangeException> `index` Parametresi, dizenin uzunluğuna eşit veya daha büyükse veya sıfırdan küçükse özellik bir özel durum oluşturur</span><span class="sxs-lookup"><span data-stu-id="aa778-113">The <xref:System.String.Chars%2A> property throws an <xref:System.IndexOutOfRangeException> exception if the `index` parameter is greater than or equal to the length of the string, or if it is less than zero</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa778-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aa778-114">See also</span></span>

- <xref:System.String.Chars%2A>
- [<span data-ttu-id="aa778-115">Nasıl yapılır: Bir Dizeyi Karakter Dizilerine Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="aa778-115">How to: Convert a String to an Array of Characters</span></span>](how-to-convert-a-string-to-an-array-of-characters.md)
- [<span data-ttu-id="aa778-116">Visual Basic'de Dizeler ve Diğer Veri Türleri Arasında Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="aa778-116">Converting Between Strings and Other Data Types in Visual Basic</span></span>](converting-between-strings-and-other-data-types.md)
- [<span data-ttu-id="aa778-117">Dizeler</span><span class="sxs-lookup"><span data-stu-id="aa778-117">Strings</span></span>](index.md)
