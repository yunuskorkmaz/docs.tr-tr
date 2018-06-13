---
title: 'Nasıl yapılır: Karakter Değerleri Dizisinden Bir Dize Oluşturma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: 104b329011d69e10a2926f31ce5d296759a3cce8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647188"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a><span data-ttu-id="464c0-102">Nasıl yapılır: Karakter Değerleri Dizisinden Bir Dize Oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="464c0-102">How to: Create a String from An Array of Char Values (Visual Basic)</span></span>
<span data-ttu-id="464c0-103">Bu örnek, tek tek karakteri "abcd" dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="464c0-103">This example creates the string "abcd" from individual characters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="464c0-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="464c0-104">Example</span></span>  
 [!code-vb[VbVbalrStrings#61](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-a-string-from-an-array-of-char-values_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="464c0-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="464c0-105">Compiling the Code</span></span>  
 <span data-ttu-id="464c0-106">Bu yöntem, özel bir gereksinimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="464c0-106">This method has no special requirements.</span></span>  
  
 <span data-ttu-id="464c0-107">Sözdizimi `"a"c`, tek bir yerde `c` tırnak işaretleri içindeki tek bir karakter izler, bir karakter değişmez değer oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="464c0-107">The syntax `"a"c`, where a single `c` follows a single character in quotation marks, is used to create a character literal.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="464c0-108">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="464c0-108">Robust Programming</span></span>  
 <span data-ttu-id="464c0-109">Boş karakterler (eşdeğer `Chr(0)`) dizesinde dize kullanırken beklenmeyen sonuçlara neden.</span><span class="sxs-lookup"><span data-stu-id="464c0-109">Null characters (equivalent to `Chr(0)`) in the string lead to unexpected results when using the string.</span></span> <span data-ttu-id="464c0-110">Null karakter dizesiyle dahil edilir, ancak bazı durumlarda null karakterden sonraki karakterler görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="464c0-110">The null character will be included with the string, but characters following the null character will not be displayed in some situations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="464c0-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="464c0-111">See Also</span></span>  
 <xref:System.String>  
 [<span data-ttu-id="464c0-112">Char Veri Türü</span><span class="sxs-lookup"><span data-stu-id="464c0-112">Char Data Type</span></span>](../../../../visual-basic/language-reference/data-types/char-data-type.md)  
 [<span data-ttu-id="464c0-113">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="464c0-113">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
