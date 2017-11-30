---
title: "Nasıl yapılır: Visual Basic'de Bir Bayt Dizisini Dizeye Dönüştürme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- byte arrays [Visual Basic], converting to strings
- examples [Visual Basic], strings
- arrays [Visual Basic], converting to strings
ms.assetid: d0dc8317-9ab3-4324-99f7-3f5788c0e72a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4133109ef334c7e87884deb7db963db3291da1d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-an-array-of-bytes-into-a-string-in-visual-basic"></a>Nasıl yapılır: Visual Basic'de Bir Bayt Dizisini Dizeye Dönüştürme
Bu konu, baytı bir bayt dizisinden bir dizeye dönüştürmek gösterilmiştir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Text.Encoding.GetString%2A> yöntemi <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> tüm baytlar bir bayt dizisinden bir dizeye dönüştürmek için sınıf kodlama.  
  
 [!code-vb[VbVbalrStrings#72](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-an-array-of-bytes-into-a-string_1.vb)]  
  
 Bir bayt dizisine bir dizeye dönüştürmek için çeşitli kodlama seçenekler arasından seçim yapabilirsiniz:  
  
-   <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Alır ASCII (7 bit) karakter kodlama ayarlayın.  
  
-   <xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Bir kodlama big endian bayt sırasını kullanarak UTF-16 biçimini alır.  
  
-   <xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Bir sistemin geçerli ANSI kod sayfası için kodlama alır.  
  
-   <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Bir kodlama little endian bayt sırası kullanarak UTF-16 biçimini alır.  
  
-   <xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Bir kodlama little endian bayt sırası kullanarak UTF-32 biçimini alır.  
  
-   <xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Bir kodlama UTF-7 biçimini alır.  
  
-   <xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Bir kodlama için UTF-8 biçiminde alır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Text.Encoding?displayProperty=nameWithType>  
 <xref:System.Text.Encoding.GetString%2A>  
 [Nasıl yapılır: Visual Basic'de bir bayt dizisi halinde dizeleri dönüştürme](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-strings-into-an-array-of-bytes.md)
