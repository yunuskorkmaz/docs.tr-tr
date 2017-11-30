---
title: "Nasıl yapılır: Visual Basic'de Dizeleri Bir Bayt Dizisine Dönüştürme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- arrays [Visual Basic], converting strings to
- byte arrays
- examples [Visual Basic], string conversion
- arrays [Visual Basic], byte arrays
ms.assetid: f477d35c-a3fc-4a30-b1d4-cd0d353aae1d
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6d527434dc0a61c9c771b42d05c1ee316094e7fd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-strings-into-an-array-of-bytes-in-visual-basic"></a>Nasıl yapılır: Visual Basic'de Dizeleri Bir Bayt Dizisine Dönüştürme
Bu konuda, bir dizeyi bir bayt dizisine dönüştürme gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Text.Encoding.GetBytes%2A> yöntemi <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> bir dizeyi bir bayt dizisine dönüştürme için sınıf kodlama.  
  
 [!code-vb[VbVbalrStrings#74](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-strings-into-an-array-of-bytes_1.vb)]  
  
 Bir dizeyi bir bayt dizisine dönüştürme için kodlama çeşitli seçenekler arasından seçim yapabilirsiniz:  
  
-   <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Alır ASCII (7 bit) karakter kodlama ayarlayın.  
  
-   <xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Bir kodlama big endian bayt sırasını kullanarak UTF-16 biçimini alır.  
  
-   <xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Bir sistemin geçerli ANSI kod sayfası için kodlama alır.  
  
-   <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Bir kodlama little endian bayt sırası kullanarak UTF-16 biçimini alır.  
  
-   <xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Bir kodlama little endian bayt sırası kullanarak UTF-32 biçimini alır.  
  
-   <xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Bir kodlama UTF-7 biçimini alır.  
  
-   <xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Bir kodlama için UTF-8 biçiminde alır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Text.Encoding?displayProperty=nameWithType>  
 <xref:System.Text.Encoding.GetBytes%2A>  
 [Nasıl yapılır: Visual Basic'te bir dizeyi bir bayt dizisi dönüştürün](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-an-array-of-bytes-into-a-string.md)
