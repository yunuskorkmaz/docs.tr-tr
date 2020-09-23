---
title: 'Nasıl yapılır: Karakter Değerleri Dizisinden Bir Dize Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: 08ad2f1c9455853e92533a7f00726c73b6adb87e
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071163"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a><span data-ttu-id="02a9f-102">Nasıl yapılır: Karakter Değerleri Dizisinden Bir Dize Oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="02a9f-102">How to: Create a String from An Array of Char Values (Visual Basic)</span></span>

<span data-ttu-id="02a9f-103">Bu örnek, bağımsız karakterlerden "abcd" dizesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="02a9f-103">This example creates the string "abcd" from individual characters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02a9f-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="02a9f-104">Example</span></span>  

 [!code-vb[VbVbalrStrings#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#61)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="02a9f-105">Kodu derle</span><span class="sxs-lookup"><span data-stu-id="02a9f-105">Compile the code</span></span>  

 <span data-ttu-id="02a9f-106">Bu yöntemin özel gereksinimleri yoktur.</span><span class="sxs-lookup"><span data-stu-id="02a9f-106">This method has no special requirements.</span></span>  
  
 <span data-ttu-id="02a9f-107">Tek bir `"a"c` `c` karakteri tırnak işareti içinde izleyen sözdizimi, bir karakter sabit değeri oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="02a9f-107">The syntax `"a"c`, where a single `c` follows a single character in quotation marks, is used to create a character literal.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="02a9f-108">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="02a9f-108">Robust Programming</span></span>  

 <span data-ttu-id="02a9f-109">Dizedeki null karakterler (eşdeğer `Chr(0)` ), dize kullanılırken beklenmeyen sonuçlara neden olur.</span><span class="sxs-lookup"><span data-stu-id="02a9f-109">Null characters (equivalent to `Chr(0)`) in the string lead to unexpected results when using the string.</span></span> <span data-ttu-id="02a9f-110">Dize ile null karakter dahil edilecek, ancak null karakteri izleyen karakterler bazı durumlarda görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="02a9f-110">The null character will be included with the string, but characters following the null character will not be displayed in some situations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02a9f-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="02a9f-111">See also</span></span>

- <xref:System.String>
- [<span data-ttu-id="02a9f-112">Char Veri Türü</span><span class="sxs-lookup"><span data-stu-id="02a9f-112">Char Data Type</span></span>](../../../language-reference/data-types/char-data-type.md)
- [<span data-ttu-id="02a9f-113">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="02a9f-113">Data Types</span></span>](../data-types/index.md)
