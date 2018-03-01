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
# <a name="optional-parameters-must-specify-a-default-value"></a>İsteğe bağlı parametreler varsayılan bir değer belirtmelidir
İsteğe bağlı parametreler arama yordamı tarafından hiçbir parametre belirtilirse, kullanılabilen varsayılan değerler sağlamanız gerekir.  
  
 **Hata Kimliği:** BC30812  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   İsteğe bağlı parametreler için varsayılan değerleri belirtin; Örneğin:  
  
    ```  
    Sub Proc1(ByVal X As Integer,   
          Optional ByVal Y As String = "Default Value")  
       MsgBox("Default argument is: " & Y)  
    End Sub  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İsteğe bağlı](../../../visual-basic/language-reference/modifiers/optional.md)
