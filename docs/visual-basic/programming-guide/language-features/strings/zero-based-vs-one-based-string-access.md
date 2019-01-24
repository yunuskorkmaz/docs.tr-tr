---
title: Sıfır tabanlı vs. Visual Basic'te bir tabanlı dize erişimi
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
ms.openlocfilehash: d4b2f73f8955b103e70e240e714e2b31d6198438
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54535547"
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a>Sıfır tabanlı vs. Visual Basic'te bir tabanlı dize erişimi
Bu konu Visual Basic karşılaştırır ve [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] bir dizedeki karakter erişim sağlar. [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Visual Basic işlevi bağlı olarak, sıfır tabanlı ve bir tabanlı erişim sağlar ancak her zaman bir dizedeki karakter sıfır tabanlı erişim sağlar.  
  
## <a name="one-based"></a>Bir tabanlı  
 Visual Basic bir tabanlı işlevi örneği için göz önünde bulundurun `Mid` işlevi. İşlem alt dizeyi, konum 1 ile başlayan başlayacağı karakter konumunu belirten bir bağımsız değişken alır. [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Substring%2A?displayProperty=nameWithType> Yöntemi alır karakter dizinini alt dizeyi olduğu başlatmak için dizedeki başlangıç konumu 0 ile. Bu nedenle, bir dize "ABCDE" varsa, karakterlerin tek tek ile kullanılmak üzere 1,2,3,4,5 numaralandırılır `Mid` işlevi, ancak ile kullanılmak üzere 0,1,2,3,4 <xref:System.String.Substring%2A?displayProperty=nameWithType> yöntemi.  
  
## <a name="zero-based"></a>Sıfır tabanlı  
 Sıfır tabanlı bir Visual Basic işlev örneği için göz önünde bulundurun `Split` işlevi. Bir dizeyi böler ve alt dizeler içeren bir dizi döndürür. [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Split%2A?displayProperty=nameWithType> Yöntemi ayrıca bir dizeyi böler ve alt dizeler içeren bir dizi döndürür. Çünkü `Split` işlevi ve <xref:System.String.Split%2A> yöntemi dönüş [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] diziler, bunlar olmalıdır sıfır tabanlı.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:System.String.Substring%2A>
- <xref:System.String.Split%2A>
- [Visual Basic'de dizelere giriş](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
