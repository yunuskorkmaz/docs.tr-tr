---
title: "'<membername>', devralınmış '<interfacename1>' ve '<interfacename2>' arabirimleri arasında belirsiz"
ms.date: 07/20/2015
f1_keywords:
- vbc30685
- bc30685
helpviewer_keywords:
- BC30685
ms.assetid: 756add7a-23d5-4b4f-a48d-8297d6459c73
ms.openlocfilehash: 1548c9894d476cc4b92d6581362d309e7b4d00d4
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55265005"
---
# <a name="membername-is-ambiguous-across-the-inherited-interfaces-interfacename1-and-interfacename2"></a><span data-ttu-id="54c5e-102">'\<membername >' devralınan arabirimleri arasında belirsiz\<interfacename1 >' ve '\<interfacename2 >'</span><span class="sxs-lookup"><span data-stu-id="54c5e-102">'\<membername>' is ambiguous across the inherited interfaces '\<interfacename1>' and '\<interfacename2>'</span></span>
<span data-ttu-id="54c5e-103">Arabirimi aynı ada sahip iki veya daha fazla üyesi birden çok arabirimlerinden devralır.</span><span class="sxs-lookup"><span data-stu-id="54c5e-103">The interface inherits two or more members with the same name from multiple interfaces.</span></span>  
  
 <span data-ttu-id="54c5e-104">**Hata Kimliği:** BC30685</span><span class="sxs-lookup"><span data-stu-id="54c5e-104">**Error ID:** BC30685</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="54c5e-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="54c5e-105">To correct this error</span></span>  
  
-   <span data-ttu-id="54c5e-106">Kullanmak istediğiniz temel arabirim değerine dönüştürme; Örneğin:</span><span class="sxs-lookup"><span data-stu-id="54c5e-106">Cast the value to the base interface that you want to use; for example:</span></span>  
  
    ```  
    Interface Left  
        Sub MySub()  
    End Interface  
  
    Interface Right  
        Sub MySub()  
    End Interface  
  
    Interface LeftRight  
        Inherits Left, Right  
    End Interface  
  
    Module test  
        Sub Main()  
            Dim x As LeftRight  
            ' x.MySub()  'x is ambiguous.  
            CType(x, Left).MySub() ' Cast to base type.  
            CType(x, Right).MySub() ' Call the other base type.  
        End Sub  
    End Module  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="54c5e-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54c5e-107">See also</span></span>
- [<span data-ttu-id="54c5e-108">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="54c5e-108">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
