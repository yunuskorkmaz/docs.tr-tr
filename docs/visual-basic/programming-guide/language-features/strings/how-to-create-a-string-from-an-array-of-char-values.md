---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Char değerleri dizisinden dize oluşturma (Visual Basic)'
title: 'Nasıl yapılır: Karakter Değerleri Dizisinden Bir Dize Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: 67b675f5f02c92b785e374b99f49248d43d12fb4
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100429838"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a><span data-ttu-id="3f701-103">Nasıl yapılır: Karakter Değerleri Dizisinden Bir Dize Oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3f701-103">How to: Create a String from An Array of Char Values (Visual Basic)</span></span>

<span data-ttu-id="3f701-104">Bu örnek, bağımsız karakterlerden "abcd" dizesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3f701-104">This example creates the string "abcd" from individual characters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f701-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="3f701-105">Example</span></span>  

 [!code-vb[VbVbalrStrings#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#61)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="3f701-106">Kodu derle</span><span class="sxs-lookup"><span data-stu-id="3f701-106">Compile the code</span></span>  

 <span data-ttu-id="3f701-107">Bu yöntemin özel gereksinimleri yoktur.</span><span class="sxs-lookup"><span data-stu-id="3f701-107">This method has no special requirements.</span></span>  
  
 <span data-ttu-id="3f701-108">Tek bir `"a"c` `c` karakteri tırnak işareti içinde izleyen sözdizimi, bir karakter sabit değeri oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3f701-108">The syntax `"a"c`, where a single `c` follows a single character in quotation marks, is used to create a character literal.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="3f701-109">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="3f701-109">Robust Programming</span></span>  

 <span data-ttu-id="3f701-110">Dizedeki null karakterler (eşdeğer `Chr(0)` ), dize kullanılırken beklenmeyen sonuçlara neden olur.</span><span class="sxs-lookup"><span data-stu-id="3f701-110">Null characters (equivalent to `Chr(0)`) in the string lead to unexpected results when using the string.</span></span> <span data-ttu-id="3f701-111">Dize ile null karakter dahil edilecek, ancak null karakteri izleyen karakterler bazı durumlarda görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="3f701-111">The null character will be included with the string, but characters following the null character will not be displayed in some situations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f701-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f701-112">See also</span></span>

- <xref:System.String>
- [<span data-ttu-id="3f701-113">Char Veri Türü</span><span class="sxs-lookup"><span data-stu-id="3f701-113">Char Data Type</span></span>](../../../language-reference/data-types/char-data-type.md)
- [<span data-ttu-id="3f701-114">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="3f701-114">Data Types</span></span>](../data-types/index.md)
