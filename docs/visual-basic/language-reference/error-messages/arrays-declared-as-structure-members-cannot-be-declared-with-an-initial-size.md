---
title: Yapı üyeleri olarak bildirilen diziler için başlangıç boyutu bildirilemez
ms.date: 07/20/2015
f1_keywords:
- vbc31043
- bc31043
helpviewer_keywords:
- BC31043
ms.assetid: 5bd90c71-1b78-444b-91e1-4789451ef085
ms.openlocfilehash: de9d77aa9ea853b6f044e91878044115588ca77c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701248"
---
# <a name="arrays-declared-as-structure-members-cannot-be-declared-with-an-initial-size"></a><span data-ttu-id="13d1c-102">Yapı üyeleri olarak bildirilen diziler için başlangıç boyutu bildirilemez</span><span class="sxs-lookup"><span data-stu-id="13d1c-102">Arrays declared as structure members cannot be declared with an initial size</span></span>
<span data-ttu-id="13d1c-103">Yapıdaki bir dizi, başlangıç boyutuyla birlikte bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="13d1c-103">An array in a structure is declared with an initial size.</span></span> <span data-ttu-id="13d1c-104">Herhangi bir yapı öğesini başlatamıyor ve bir dizi boyutunun bildirilmesi, tek bir başlatma biçimidir.</span><span class="sxs-lookup"><span data-stu-id="13d1c-104">You cannot initialize any structure element, and declaring an array size is one form of initialization.</span></span>  
  
 <span data-ttu-id="13d1c-105">**Hata kimliği:** BC31043</span><span class="sxs-lookup"><span data-stu-id="13d1c-105">**Error ID:** BC31043</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="13d1c-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="13d1c-106">To correct this error</span></span>  
  
1. <span data-ttu-id="13d1c-107">Yapıdaki diziyi dinamik (başlangıç boyutu olmadan) olarak tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="13d1c-107">Define the array in your structure as dynamic (no initial size).</span></span>  
  
2. <span data-ttu-id="13d1c-108">Belirli bir dizi boyutuna ihtiyacınız varsa, kodunuz çalışırken bir [ReDim ifadesiyle](../../../visual-basic/language-reference/statements/redim-statement.md) dinamik bir diziyi yeniden Dimension uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13d1c-108">If you require a certain size of array, you can redimension a dynamic array with a [ReDim Statement](../../../visual-basic/language-reference/statements/redim-statement.md) when your code is running.</span></span> <span data-ttu-id="13d1c-109">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="13d1c-109">The following example illustrates this.</span></span>  
  
    ```vb  
    Structure demoStruct  
        Public demoArray() As Integer  
    End Structure  
    Sub useStruct()  
        Dim struct As demoStruct  
        ReDim struct.demoArray(9)  
        Struct.demoArray(2) = 777  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="13d1c-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13d1c-110">See also</span></span>

- [<span data-ttu-id="13d1c-111">Diziler</span><span class="sxs-lookup"><span data-stu-id="13d1c-111">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="13d1c-112">Nasıl yapılır: Bir Yapıyı Bildirme</span><span class="sxs-lookup"><span data-stu-id="13d1c-112">How to: Declare a Structure</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
