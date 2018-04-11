---
title: Tür belirleyicilerde dizi sınırları bulunamaz
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30638
- bc30638
helpviewer_keywords:
- BC30638
ms.assetid: 93b654f4-70fa-4a48-baed-ffae42075550
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 770f86ca960110965b6917a22d284678ff8b6f8c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="array-bounds-cannot-appear-in-type-specifiers"></a>Tür belirleyicilerde dizi sınırları bulunamaz
Dizi boyutları bir veri türü belirleyici bir parçası olarak bildirilemez.  
  
 **Hata Kimliği:** BC30638  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Aşağıdaki örnekte gösterildiği gibi türü dizi boyutu yerleştirme yerine değişken adı hemen ardından dizinin boyutu belirtin.  
  
    ```  
    Dim Array(8) As Integer   
    ```  
  
-   Aşağıdaki örnekte gösterildiği gibi öğeleri, istenen sayısı ile başlatın ve bir dizi tanımlayın.  
  
    ```  
    Dim Array2() As Integer = New Integer(8) {}  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md)
