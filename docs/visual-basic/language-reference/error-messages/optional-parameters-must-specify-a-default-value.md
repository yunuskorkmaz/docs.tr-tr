---
title: İsteğe bağlı parametreler varsayılan bir değer belirtmelidir
ms.date: 07/20/2015
f1_keywords:
- vbc30812
- bc30812
helpviewer_keywords:
- BC30812
ms.assetid: 5091a250-be66-413b-98a3-2a9974c4d600
ms.openlocfilehash: 01c0abb366e8605a9b153333e645fc3276b6bd16
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772599"
---
# <a name="optional-parameters-must-specify-a-default-value"></a><span data-ttu-id="61fb2-102">İsteğe bağlı parametreler varsayılan bir değer belirtmelidir</span><span class="sxs-lookup"><span data-stu-id="61fb2-102">Optional parameters must specify a default value</span></span>
<span data-ttu-id="61fb2-103">İsteğe bağlı parametreler tarafından çağıran bir yordam parametre sağlanmazsa, kullanılabilen varsayılan değerler sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="61fb2-103">Optional parameters must provide default values that can be used if no parameter is supplied by a calling procedure.</span></span>  
  
 <span data-ttu-id="61fb2-104">**Hata Kimliği:** BC30812</span><span class="sxs-lookup"><span data-stu-id="61fb2-104">**Error ID:** BC30812</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="61fb2-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="61fb2-105">To correct this error</span></span>  
  
- <span data-ttu-id="61fb2-106">İsteğe bağlı parametrelerinin varsayılan değerleri; belirtin. Örneğin:</span><span class="sxs-lookup"><span data-stu-id="61fb2-106">Specify default values for optional parameters; for example:</span></span>  
  
    ```  
    Sub Proc1(ByVal X As Integer,   
          Optional ByVal Y As String = "Default Value")  
       MsgBox("Default argument is: " & Y)  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="61fb2-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="61fb2-107">See also</span></span>

- [<span data-ttu-id="61fb2-108">Optional</span><span class="sxs-lookup"><span data-stu-id="61fb2-108">Optional</span></span>](../../../visual-basic/language-reference/modifiers/optional.md)
