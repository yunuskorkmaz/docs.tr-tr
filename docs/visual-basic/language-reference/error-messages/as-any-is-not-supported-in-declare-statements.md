---
title: '&#39;Tüm&#39; desteklenmeyen &#39;Declare&#39; deyimleri'
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30828
- vbc30828
helpviewer_keywords:
- BC30828
ms.assetid: 7e5cf519-8b64-4ac5-8116-705fe26c846d
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d8146e339ac5cb005b99c9a1e02f1cd248c4558b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="39as-any39-is-not-supported-in-39declare39-statements"></a>&#39;Tüm&#39; desteklenmeyen &#39;Declare&#39; deyimleri
`Any` Veri türü ile kullanıldı `Declare` deyimleri Visual Basic 6.0 ve önceki sürümlerde herhangi bir türde veri içeren bağımsız değişkenler kullanımına izin vermek için. Bunu yapar ve Visual Basic destekler, ancak aşırı `Any` veri türü geçersiz.  
  
 **Hata Kimliği:** BC30828  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Kullanmak istediğiniz belirli türdeki parametreleri bildirin; Örneğin.  
  
     [!code-vb[VbVbalrStatements#95](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_1.vb)]  
  
2.  Kullanım <xref:System.Runtime.InteropServices.MarshalAsAttribute> belirtmek için özniteliği `As Any` zaman `Void*` çağrılan yordamı tarafından beklenir.  
  
     [!code-vb[VbVbalrStatements#96](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_2.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [İzlenecek yol: Windows API'lerini Çağırma](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 [Declare Deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [Yönetilen Kodda Prototipler Oluşturma](../../../framework/interop/creating-prototypes-in-managed-code.md)
