---
title: Visual Basic'te Dize Düzenleme Yöntemlerinin Türleri
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
ms.openlocfilehash: aba9af9c699cf8d07862c5d2967902bec1623500
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363765"
---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a>Visual Basic'de Dize Düzenleme Yöntemlerinin Türleri
Dizelerinizi çözümlemek ve işlemek için çeşitli farklı yollar vardır. Yöntemlerin bazıları Visual Basic dilin bir parçasıdır ve diğerleri sınıfına dahil edilir `String` .  
  
## <a name="visual-basic-language-and-the-net-framework"></a>Visual Basic dili ve .NET Framework  
 Visual Basic Yöntemler, dilin devralınan işlevleri olarak kullanılır. Kodunuzda nitelendirme olmadan kullanılabilirler. Aşağıdaki örnek Visual Basic dize işleme komutunun tipik kullanımını gösterir:  
  
 [!code-vb[VbVbalrStrings#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#44)]  
  
 Bu örnekte, `Mid` işlevi üzerinde doğrudan bir işlem gerçekleştirir `aString` ve değerini öğesine atar `bString` .  
  
 Visual Basic dize düzenleme yöntemlerinin listesi için bkz. [dize düzenleme Özeti](../../../language-reference/keywords/string-manipulation-summary.md).  
  
### <a name="shared-methods-and-instance-methods"></a>Paylaşılan Yöntemler ve örnek yöntemleri  
 Dizeleri sınıfının yöntemleriyle de işleyebilirsiniz `String` . İçinde iki tür yöntem vardır `String` : *paylaşılan* Yöntemler ve *örnek* yöntemleri.  
  
#### <a name="shared-methods"></a>Paylaşılan Yöntemler  
 Paylaşılan bir yöntem, `String` sınıfın kendisinden kaynaklanan ve bu sınıfın bir örneğinin çalışmasını gerektirmeyen bir yöntemdir. Bu yöntemler, `String` sınıfının bir örneğiyle değil, sınıfının () adıyla nitelenebilir `String` . Örnek:  
  
 [!code-vb[VbVbalrStrings#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#45)]  
  
 Yukarıdaki örnekte, <xref:System.String.Copy%2A?displayProperty=nameWithType> Yöntemi verilen bir ifadeye davranan ve elde edilen değeri atayan statik bir yöntemdir `bString` .  
  
#### <a name="instance-methods"></a>Örnek yöntemleri  
 Örneğin, belirli bir örneğinden gövdeli örnek yöntemleri, `String` örnek adıyla nitelenmelidir. Örnek:  
  
 [!code-vb[VbVbalrStrings#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#46)]  
  
 Bu örnekte, <xref:System.String.Substring%2A?displayProperty=nameWithType> yöntemi örneğinin `String` (yani,) bir yöntemidir `aString` . Üzerinde bir işlem gerçekleştirir `aString` ve bu değeri öğesine atar `bString` .  
  
 Daha fazla bilgi için, sınıfının belgelerine bakın <xref:System.String> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de Dizelere Giriş](introduction-to-strings.md)
