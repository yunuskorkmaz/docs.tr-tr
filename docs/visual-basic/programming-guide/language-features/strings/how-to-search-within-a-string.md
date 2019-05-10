---
title: 'Nasıl yapılır: (Visual Basic) dize içinde arama'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
ms.openlocfilehash: 57a3d9650ad78e1c8580fd46839c9a1cbc7794c9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665336"
---
# <a name="how-to-search-within-a-string-visual-basic"></a>Nasıl yapılır: (Visual Basic) dize içinde arama
Bu örnek <xref:System.String.IndexOf%2A> metodunda bir <xref:System.String> bir alt dizenin ilk geçtiği dizini bildirmek için nesne.  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbVbalrStrings#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#71)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
- Bir `Imports` deyimi belirtme <xref:System> ad alanı. Daha fazla bilgi için [Imports deyimi (.NET Namespace ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 <xref:System.String.IndexOf%2A> Yöntemi raporları alt dizenin ilk geçtiği ilk karakterin konumu. Dizin 0 tabanlı bir dizenin ilk karakteri bir dizininin 0 olduğu anlamına gelir.  
  
 Varsa <xref:System.String.IndexOf%2A> substring bulamazsa -1 döndürür.  
  
 <xref:System.String.IndexOf%2A> Yöntemi büyük küçük harfe duyarlıdır ve geçerli kültürü kullanır.  
  
 En iyi hata denetimi için dize aramaya içine isteyebilirsiniz `Try` bloğu bir [deneyin... Catch... Finally deyimini](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) oluşturma.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.String.IndexOf%2A>
- [Try...Catch...Finally Deyimi](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Visual Basic'de dizelere giriş](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
- [Dizeler](../../../../visual-basic/programming-guide/language-features/strings/index.md)
