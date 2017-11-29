---
title: "Nasıl yapılır: Dize İçinde Arama (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2c828d0b32fdf90e121e9d5da0bb60ab11c212f4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-search-within-a-string-visual-basic"></a>Nasıl yapılır: Dize İçinde Arama (Visual Basic)
Bu örnek çağırır <xref:System.String.IndexOf%2A> yöntemi bir <xref:System.String> bir alt dizenin ilk örneğinin dizinini bildirmek için nesne.  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbVbalrStrings#71](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-search-within-a-string_1.vb)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Bir `Imports` deyimi belirtme <xref:System> ad alanı. Daha fazla bilgi için bkz: [Imports deyimi (.NET Namespace ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 <xref:System.String.IndexOf%2A> Yöntemi raporları alt dizenin ilk örneğinin ilk karakterin konumu. Bir dizenin ilk karakter 0 dizini sahip olduğu anlamına 0 tabanlı dizinidir.  
  
 Varsa <xref:System.String.IndexOf%2A> alt dizeyi bulur değil -1 döndürür.  
  
 <xref:System.String.IndexOf%2A> Yöntemi küçük harfe duyarlıdır ve geçerli kültürü kullanır.  
  
 En iyi hata denetimi için dize aramada içine isteyebilirsiniz `Try` , engelleme bir [deneyin... Catch... Finally ifadesi](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) oluşturma.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.String.IndexOf%2A>  
 [Try... Catch... Finally ifadesi](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Visual Basic'de dizelere giriş](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)  
 [Dizeleri](../../../../visual-basic/programming-guide/language-features/strings/index.md)
