---
title: 'Nasıl yapılır: Dize İçinde Arama (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
ms.openlocfilehash: 08a005f2927a76c9b29c1ff0092ea8282188b2b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647689"
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
 [Try...Catch...Finally Deyimi](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Visual Basic'de dizelere giriş](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)  
 [Dizeler](../../../../visual-basic/programming-guide/language-features/strings/index.md)
