---
title: Visual Basic'de Dize Düzenleme Yöntemlerinin Türleri
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
ms.openlocfilehash: 11903e067c064f129ecd2df80244edb6741c73be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648700"
---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a>Visual Basic'de Dize Düzenleme Yöntemlerinin Türleri
Analiz etmek ve dizelerinizi işlemek için birkaç farklı yolu vardır. Yöntemlerin bazıları Visual Basic Dil parçası olan ve diğerleri de devralınan `String` sınıfı.  
  
## <a name="visual-basic-language-and-the-net-framework"></a>Visual Basic dili ve .NET Framework  
 Visual Basic yöntemleri dil devralınmış işlevler kullanılır. Kodunuzu nitelikte olmadan kullanılabilir. Aşağıdaki örnek, bir Visual Basic dize düzenlemesi komutu tipik kullanımını göstermektedir:  
  
 [!code-vb[VbVbalrStrings#44](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_1.vb)]  
  
 Bu örnekte, `Mid` işlevi gerçekleştirir doğrudan işlemi `aString` ve değeri atar `bString`.  
  
 Visual Basic dize düzenleme yöntemlerinin listesi için bkz [dize düzenleme özeti](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).  
  
### <a name="shared-methods-and-instance-methods"></a>Paylaşılan ve örnek yöntemleri  
 Dize yöntemleri ile işleyebileceğiniz `String` sınıfı. İki tür yöntemleri vardır `String`: *paylaşılan* yöntemleri ve *örneği* yöntemleri.  
  
#### <a name="shared-methods"></a>Paylaşılan yöntemleri  
 Bir paylaşılan yöntemi gelen kaynaklandığını yöntemdir `String` sınıfının kendisini ve çalışmak için bu sınıfının bir örneği gerektirmez. Bu yöntemlerden sınıfın adını nitelenmiş olmalıdır (`String`) yerine bir örneğiyle `String` sınıfı. Örneğin:  
  
 [!code-vb[VbVbalrStrings#45](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_2.vb)]  
  
 Önceki örnekte <xref:System.String.Copy%2A?displayProperty=nameWithType> yöntemdir bir ifade üzerinde çalışan verilir ve çıkan değeri atar bir statik yöntem `bString`.  
  
#### <a name="instance-methods"></a>Örnek yöntemleri  
 Örnek yöntemleri, bunun aksine, belirli bir örneği gövdesi `String` ve örnek adıyla nitelendirilmelidir. Örneğin:  
  
 [!code-vb[VbVbalrStrings#46](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_3.vb)]  
  
 Bu örnekte, <xref:System.String.Substring%2A?displayProperty=nameWithType> yöntemi örneğinin bir yöntemdir `String` (diğer bir deyişle, `aString`). Üzerinde bir işlemi gerçekleştiren `aString` ve bu değeri atar `bString`.  
  
 Daha fazla bilgi için belgelerine bakın <xref:System.String> sınıfı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de dizelere giriş](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
