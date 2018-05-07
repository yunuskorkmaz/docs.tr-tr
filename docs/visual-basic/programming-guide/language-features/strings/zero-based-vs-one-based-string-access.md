---
title: Sıfır tabanlı vs. Visual Basic'de dize tabanlı erişim
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
ms.openlocfilehash: a0a42f72d94adf1c10865374017fa61e833df40f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a>Sıfır tabanlı vs. Visual Basic'de dize tabanlı erişim
Bu konuda nasıl Visual Basic karşılaştırır ve [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] bir dizedeki karakter erişim sağlar. [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Visual Basic işlevi bağlı olarak sıfır tabanlı ve tabanlı erişim sağlar ancak her zaman bir dizedeki karakter sıfır tabanlı erişim sağlar.  
  
## <a name="one-based"></a>Tabanlı  
 Örneği tabanlı Visual Basic işlevi için göz önünde bulundurun `Mid` işlevi. Alt dizeyi, 1 konumundan başlayarak başlayacağı karakterin gösteren bağımsız değişken alır. [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Substring%2A?displayProperty=nameWithType> Yöntemi alır karakter dizinini alt dizeyi olduğu başlatmak için dizesinde başlama konumu 0 ile. "ABCDE" dize varsa, bu nedenle, tek tek karakterleri 1,2,3,4,5 ile kullanmak için numaralandırılmış `Mid` işlevi ancak ile kullanılmak üzere 0,1,2,3,4 <xref:System.String.Substring%2A?displayProperty=nameWithType> yöntemi.  
  
## <a name="zero-based"></a>Sıfır tabanlı  
 Örneği sıfır tabanlı bir Visual Basic işlevi için göz önünde bulundurun `Split` işlevi. Bir dize böler ve alt dize içeren bir dizi döndürür. [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Split%2A?displayProperty=nameWithType> Yöntemi de bir dize böler ve alt dize içeren bir dizi döndürür. Çünkü `Split` işlevi ve <xref:System.String.Split%2A> yöntemi dönüş [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] dizileri, bunlar olmalıdır sıfır tabanlı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A>  
 <xref:Microsoft.VisualBasic.Strings.Split%2A>  
 <xref:System.String.Substring%2A>  
 <xref:System.String.Split%2A>  
 [Visual Basic'de dizelere giriş](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
