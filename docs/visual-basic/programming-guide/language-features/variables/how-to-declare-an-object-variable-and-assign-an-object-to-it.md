---
title: "Nasıl yapılır: Visual Basic'de Bir Nesne Değişkeni Bildirme ve bir Nesne Atama"
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: 1f38c90f0571b3fc73c4c89812092cdada936d84
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
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
 [Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Nesne Değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Nesne Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [Object Veri Türü](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [Dim Deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Yerel Çıkarım](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Option Strict Deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
