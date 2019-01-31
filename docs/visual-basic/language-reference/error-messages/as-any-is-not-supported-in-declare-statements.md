---
title: "'Declare' deyimlerinde 'As Any' desteklenmiyor"
ms.date: 07/20/2015
f1_keywords:
- bc30828
- vbc30828
helpviewer_keywords:
- BC30828
ms.assetid: 7e5cf519-8b64-4ac5-8116-705fe26c846d
ms.openlocfilehash: bdf339e0d91106a6d6527e085608a06b0439951c
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55274098"
---
# <a name="as-any-is-not-supported-in-declare-statements"></a>'Declare' deyimlerinde 'As Any' desteklenmiyor
`Any` Veri türü ile kullanıldığında `Declare` deyimleri Visual Basic 6.0 ve önceki sürümlerinde her türden veriyi içerebilir bağımsız değişkenleri kullanımına izin vermek için. Bunu yapar ve Visual Basic destekler, ancak aşırı `Any` veri türü geçersiz.  
  
 **Hata Kimliği:** BC30828  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Kullanmak istediğiniz belirli türdeki parametreleri bildirme; Örneğin.  
  
     [!code-vb[VbVbalrStatements#95](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_1.vb)]  
  
2.  Kullanım <xref:System.Runtime.InteropServices.MarshalAsAttribute> belirtmek için özniteliği `As Any` olduğunda `Void*` çağrılan yordam tarafından beklenir.  
  
     [!code-vb[VbVbalrStatements#96](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_2.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [İzlenecek yol: Windows API'lerini Çağırma](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
- [Declare Deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Yönetilen Kodda Prototipler Oluşturma](../../../framework/interop/creating-prototypes-in-managed-code.md)
