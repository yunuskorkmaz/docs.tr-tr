---
title: "Nasıl yapılır: Karakter Değerleri Dizisinden Bir Dize Oluşturma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 06e5c6923c26f3cb84b38475d6680523853d727d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a>Nasıl yapılır: Karakter Değerleri Dizisinden Bir Dize Oluşturma (Visual Basic)
Bu örnek, tek tek karakteri "abcd" dize oluşturur.  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbVbalrStrings#61](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-a-string-from-an-array-of-char-values_1.vb)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu yöntem, özel bir gereksinimi yoktur.  
  
 Sözdizimi `"a"c`, tek bir yerde `c` tırnak işaretleri içindeki tek bir karakter izler, bir karakter değişmez değer oluşturmak için kullanılır.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Boş karakterler (eşdeğer `Chr(0)`) dizesinde dize kullanırken beklenmeyen sonuçlara neden. Null karakter dizesiyle dahil edilir, ancak bazı durumlarda null karakterden sonraki karakterler görüntülenmez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.String>  
 [Char veri türü](../../../../visual-basic/language-reference/data-types/char-data-type.md)  
 [Veri türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
