---
title: "Yapı üyeleri olarak bildirilen diziler için başlangıç boyutu bildirilemez"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31043
- bc31043
helpviewer_keywords:
- BC31043
ms.assetid: 5bd90c71-1b78-444b-91e1-4789451ef085
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 983154a144a79991c86db5056ad0e0e563a3ba73
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="arrays-declared-as-structure-members-cannot-be-declared-with-an-initial-size"></a><span data-ttu-id="7a031-102">Yapı üyeleri olarak bildirilen diziler için başlangıç boyutu bildirilemez</span><span class="sxs-lookup"><span data-stu-id="7a031-102">Arrays declared as structure members cannot be declared with an initial size</span></span>
<span data-ttu-id="7a031-103">Yapı bir dizi başlangıç boyutuyla bildirildi.</span><span class="sxs-lookup"><span data-stu-id="7a031-103">An array in a structure is declared with an initial size.</span></span> <span data-ttu-id="7a031-104">Herhangi bir yapı öğesi başlatılamıyor ve bir dizi boyutu bildirme bir başlatma biçimidir.</span><span class="sxs-lookup"><span data-stu-id="7a031-104">You cannot initialize any structure element, and declaring an array size is one form of initialization.</span></span>  
  
 <span data-ttu-id="7a031-105">**Hata Kimliği:** BC31043</span><span class="sxs-lookup"><span data-stu-id="7a031-105">**Error ID:** BC31043</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7a031-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="7a031-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="7a031-107">Dizi, yapısında (ilk büyüklük) dinamik tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="7a031-107">Define the array in your structure as dynamic (no initial size).</span></span>  
  
2.  <span data-ttu-id="7a031-108">Belirli bir boyuta dizinin gerektiriyorsa, dinamik bir dizinin redimension bir [ReDim deyimi](../../../visual-basic/language-reference/statements/redim-statement.md) kodunuzu çalışmadığı zaman.</span><span class="sxs-lookup"><span data-stu-id="7a031-108">If you require a certain size of array, you can redimension a dynamic array with a [ReDim Statement](../../../visual-basic/language-reference/statements/redim-statement.md) when your code is running.</span></span> <span data-ttu-id="7a031-109">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="7a031-109">The following example illustrates this.</span></span>  
  
    ```  
    Structure demoStruct  
        Public demoArray() As Integer  
    End Structure  
    Sub useStruct()  
        Dim struct As demoStruct  
        ReDim struct.demoArray(9)  
        Struct.demoArray(2) = 777  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="7a031-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7a031-110">See Also</span></span>  
 [<span data-ttu-id="7a031-111">Diziler</span><span class="sxs-lookup"><span data-stu-id="7a031-111">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="7a031-112">Nasıl yapılır: bir yapıyı bildirme</span><span class="sxs-lookup"><span data-stu-id="7a031-112">How to: Declare a Structure</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
