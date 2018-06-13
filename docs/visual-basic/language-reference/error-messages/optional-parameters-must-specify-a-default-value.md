---
title: İsteğe bağlı parametreler varsayılan bir değer belirtmelidir
ms.date: 07/20/2015
f1_keywords:
- vbc30812
- bc30812
helpviewer_keywords:
- BC30812
ms.assetid: 5091a250-be66-413b-98a3-2a9974c4d600
ms.openlocfilehash: 6788a7908489591e266af6d141006f2aa2d0e6f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593922"
---
# <a name="optional-parameters-must-specify-a-default-value"></a><span data-ttu-id="a5094-102">İsteğe bağlı parametreler varsayılan bir değer belirtmelidir</span><span class="sxs-lookup"><span data-stu-id="a5094-102">Optional parameters must specify a default value</span></span>
<span data-ttu-id="a5094-103">İsteğe bağlı parametreler arama yordamı tarafından hiçbir parametre belirtilirse, kullanılabilen varsayılan değerler sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a5094-103">Optional parameters must provide default values that can be used if no parameter is supplied by a calling procedure.</span></span>  
  
 <span data-ttu-id="a5094-104">**Hata Kimliği:** BC30812</span><span class="sxs-lookup"><span data-stu-id="a5094-104">**Error ID:** BC30812</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a5094-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="a5094-105">To correct this error</span></span>  
  
-   <span data-ttu-id="a5094-106">İsteğe bağlı parametreler için varsayılan değerleri belirtin; Örneğin:</span><span class="sxs-lookup"><span data-stu-id="a5094-106">Specify default values for optional parameters; for example:</span></span>  
  
    ```  
    Sub Proc1(ByVal X As Integer,   
          Optional ByVal Y As String = "Default Value")  
       MsgBox("Default argument is: " & Y)  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a5094-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a5094-107">See Also</span></span>  
 [<span data-ttu-id="a5094-108">Optional</span><span class="sxs-lookup"><span data-stu-id="a5094-108">Optional</span></span>](../../../visual-basic/language-reference/modifiers/optional.md)
