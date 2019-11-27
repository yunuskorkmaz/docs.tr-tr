---
title: Visual Basic'te Dize Düzenleme Yöntemlerinin Türleri
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
ms.openlocfilehash: a02278abfb71efb2f31f239a89a22ad1c8ee7a18
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346277"
---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a>Visual Basic'de Dize Düzenleme Yöntemlerinin Türleri
Dizelerinizi çözümlemek ve işlemek için çeşitli farklı yollar vardır. Yöntemlerin bazıları Visual Basic dilin bir parçasıdır ve diğerleri `String` sınıfına dahil edilir.  
  
## <a name="visual-basic-language-and-the-net-framework"></a>Visual Basic dili ve .NET Framework  
 Visual Basic Yöntemler, dilin devralınan işlevleri olarak kullanılır. Kodunuzda nitelendirme olmadan kullanılabilirler. Aşağıdaki örnek Visual Basic dize işleme komutunun tipik kullanımını gösterir:  
  
 [!code-vb[VbVbalrStrings#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#44)]  
  
 Bu örnekte, `Mid` işlevi `aString` üzerinde doğrudan işlem gerçekleştirir ve değeri `bString`atar.  
  
 Visual Basic dize düzenleme yöntemlerinin listesi için bkz. [dize düzenleme Özeti](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).  
  
### <a name="shared-methods-and-instance-methods"></a>Paylaşılan Yöntemler ve örnek yöntemleri  
 Ayrıca, `String` sınıfının yöntemleriyle dizeleri de yönetebilirsiniz. `String`iki tür yöntem vardır: *paylaşılan* Yöntemler ve *örnek* yöntemleri.  
  
#### <a name="shared-methods"></a>Paylaşılan Yöntemler  
 Paylaşılan bir yöntem, `String` sınıfından kaynaklanan ve bu sınıfın bir örneğinin çalışmasını gerektirmeyen bir yöntemdir. Bu yöntemler, `String` sınıfının bir örneği yerine, sınıfın adı (`String`) ile nitelenebilir. Örneğin:  
  
 [!code-vb[VbVbalrStrings#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#45)]  
  
 Yukarıdaki örnekte <xref:System.String.Copy%2A?displayProperty=nameWithType> yöntemi, verilen bir ifadeye davranan ve elde edilen değeri `bString`atayan statik bir yöntemdir.  
  
#### <a name="instance-methods"></a>Örnek yöntemleri  
 Örneğin, belirli bir `String` örneğinden gövdeli örnek yöntemleri, örnek adı ile nitelenmelidir. Örneğin:  
  
 [!code-vb[VbVbalrStrings#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#46)]  
  
 Bu örnekte <xref:System.String.Substring%2A?displayProperty=nameWithType> yöntemi, `String` örneğinin bir yöntemidir (yani, `aString`). `aString` bir işlem gerçekleştirir ve bu değeri `bString`atar.  
  
 Daha fazla bilgi için <xref:System.String> sınıfına yönelik belgelere bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic dizelere giriş](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
