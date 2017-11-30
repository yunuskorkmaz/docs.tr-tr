---
title: "Nasıl yapılır: Visual Basic'de Bir Nesne Değişkeni Bildirme ve bir Nesne Atama"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f4a682c7ae32ace0b1f859d52963342546a83f29
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a>Nasıl yapılır: Visual Basic'de Bir Nesne Değişkeni Bildirme ve bir Nesne Atama
Bir değişken bildirme [nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md) belirterek `As Object` içinde bir [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md). Nesne sonra eşittir işareti koyarak bir nesne gibi bir değişkene atayın (`=`) atama deyimi veya başlatma yan tümcesinde.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bildiren bir `Object` değişkeni ve geçerli örnek için atar.  
  
```  
      Dim thisObject As Object  
thisObject = "This is an Object"  
```  
  
 Değişkeni bildiriminden bir parçası olarak başlatarak ataması ve bildirimi birleştirebilirsiniz. Aşağıdaki örnek önceki örneğe eşdeğerdir.  
  
```  
Dim thisObject As Object= "This is an Object"  
```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Bir başvuru <xref:System> ad alanı.  
  
-   Sınıf, yapı veya modülü yerleştirileceği `Dim` deyimi.  
  
-   Atama deyimi yerleştirileceği bir yordamdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Değişken bildirimi](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Nesne değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Nesne değişken bildirimi](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [Nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Yerel tür çıkarımı](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
