---
title: 'Nasıl yapılır: (Visual Basic) karakter değerleri dizisinden bir dize oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: 0d3a4caf0967ab77de7d91470e43e52521dbd2da
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975517"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a><span data-ttu-id="0cdac-102">Nasıl yapılır: (Visual Basic) karakter değerleri dizisinden bir dize oluşturma</span><span class="sxs-lookup"><span data-stu-id="0cdac-102">How to: Create a String from An Array of Char Values (Visual Basic)</span></span>
<span data-ttu-id="0cdac-103">Bu örnek, tek tek karakteri "abcd" dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0cdac-103">This example creates the string "abcd" from individual characters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0cdac-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="0cdac-104">Example</span></span>  
 [!code-vb[VbVbalrStrings#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#61)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0cdac-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="0cdac-105">Compiling the Code</span></span>  
 <span data-ttu-id="0cdac-106">Bu yöntem, hiçbir özel gereksinimleri vardır.</span><span class="sxs-lookup"><span data-stu-id="0cdac-106">This method has no special requirements.</span></span>  
  
 <span data-ttu-id="0cdac-107">Söz dizimi `"a"c`, tek bir yerde `c` izleyen tırnak işaretleri içindeki tek bir karakter, karakter değişmez değeri oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0cdac-107">The syntax `"a"c`, where a single `c` follows a single character in quotation marks, is used to create a character literal.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="0cdac-108">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="0cdac-108">Robust Programming</span></span>  
 <span data-ttu-id="0cdac-109">Boş karakterler (eşdeğer `Chr(0)`) dize, dize kullanılırken beklenmeyen sonuçlara neden.</span><span class="sxs-lookup"><span data-stu-id="0cdac-109">Null characters (equivalent to `Chr(0)`) in the string lead to unexpected results when using the string.</span></span> <span data-ttu-id="0cdac-110">Null karakteri ile dizeyi dahil edilir, ancak bazı durumlarda null karakterden sonraki karakterler görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="0cdac-110">The null character will be included with the string, but characters following the null character will not be displayed in some situations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cdac-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0cdac-111">See also</span></span>
- <xref:System.String>
- [<span data-ttu-id="0cdac-112">Char Veri Türü</span><span class="sxs-lookup"><span data-stu-id="0cdac-112">Char Data Type</span></span>](../../../../visual-basic/language-reference/data-types/char-data-type.md)
- [<span data-ttu-id="0cdac-113">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="0cdac-113">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
