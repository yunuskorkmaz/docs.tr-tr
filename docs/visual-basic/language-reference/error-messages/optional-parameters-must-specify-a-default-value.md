---
title: "İsteğe bağlı parametreler varsayılan bir değer belirtmelidir"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30812
- bc30812
helpviewer_keywords:
- BC30812
ms.assetid: 5091a250-be66-413b-98a3-2a9974c4d600
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e9ec6d044ba0a1bb904030ddbb4c4fa406c3ba63
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="optional-parameters-must-specify-a-default-value"></a><span data-ttu-id="7d6bc-102">İsteğe bağlı parametreler varsayılan bir değer belirtmelidir</span><span class="sxs-lookup"><span data-stu-id="7d6bc-102">Optional parameters must specify a default value</span></span>
<span data-ttu-id="7d6bc-103">İsteğe bağlı parametreler arama yordamı tarafından hiçbir parametre belirtilirse, kullanılabilen varsayılan değerler sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7d6bc-103">Optional parameters must provide default values that can be used if no parameter is supplied by a calling procedure.</span></span>  
  
 <span data-ttu-id="7d6bc-104">**Hata Kimliği:** BC30812</span><span class="sxs-lookup"><span data-stu-id="7d6bc-104">**Error ID:** BC30812</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7d6bc-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="7d6bc-105">To correct this error</span></span>  
  
-   <span data-ttu-id="7d6bc-106">İsteğe bağlı parametreler için varsayılan değerleri belirtin; Örneğin:</span><span class="sxs-lookup"><span data-stu-id="7d6bc-106">Specify default values for optional parameters; for example:</span></span>  
  
    ```  
    Sub Proc1(ByVal X As Integer,   
          Optional ByVal Y As String = "Default Value")  
       MsgBox("Default argument is: " & Y)  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="7d6bc-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7d6bc-107">See Also</span></span>  
 [<span data-ttu-id="7d6bc-108">İsteğe bağlı</span><span class="sxs-lookup"><span data-stu-id="7d6bc-108">Optional</span></span>](../../../visual-basic/language-reference/modifiers/optional.md)
