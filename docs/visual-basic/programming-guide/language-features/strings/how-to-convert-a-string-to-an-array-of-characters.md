---
title: "Nasıl yapılır: Visual Basic'te Bir Dizeyi Karakter Dizilerine Dönüştürme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- character arrays [Visual Basic], converting strings
- arrays [Visual Basic], converting strings to
- examples [Visual Basic], string conversion
- strings [Visual Basic], converting to arrays
- string conversion [Visual Basic], arrays
ms.assetid: 1b54b686-ab29-413b-adce-6bd5422376eb
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 59d0da52c8f78b93c76325e6242156c106deeaf1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te Bir Dizeyi Karakter Dizilerine Dönüştürme
Bazen dizenizi ve bu karakterleri ne zaman bir dizesini ayrıştırma, dizesindeki konumlarını karakterler hakkında veriler kullanışlıdır. Bu örnek, bir dize dizesinin çağırarak karakter nasıl erişebileceğini gösterir <xref:System.String.ToCharArray%2A> yöntemi.  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir dizeye bölüneceği gösterilmiştir bir `Char` dizi ve nasıl bir dizeye bölüneceği bir `String` kendi Unicode metin karakter dizisi. Bu ayrım iki veya daha fazla Unicode metin karakterlerinin birleştirilebilen nedeni `Char` karakterleri (bir yedek çifti ya da bir birleştirme gibi karakter dizisi). Daha fazla bilgi için bkz: <xref:System.Globalization.TextElementEnumerator> ve "Unicode standart" http://www.unicode.org adresindeki.  
  
 [!code-vb[VbVbalrStrings#75](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_1.vb)]  
  
## <a name="example"></a>Örnek  
 Bir dize, Unicode metin karakterlere bölmek daha da zor olan, ancak bu görsel bir dize gösterimini hakkında bilgi istiyorsanız gereklidir. Bu örnekte <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> bir dize olun Unicode metin karakterler hakkında bilgi almak için yöntemi.  
  
 [!code-vb[VbVbalrStrings#76](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_2.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.String.Chars%2A>  
 <xref:System.Globalization.StringInfo?displayProperty=nameWithType>  
 [Nasıl yapılır: dizelerdeki karakterlere erişme](../../../../visual-basic/programming-guide/language-features/strings/how-to-access-characters-in-strings.md)  
 [Dizeler ve diğer Visual Basic veri türleri arasında dönüştürme](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)  
 [Dizeleri](../../../../visual-basic/programming-guide/language-features/strings/index.md)
