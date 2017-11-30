---
title: "Nasıl yapılır: İlgili Sabit Değerleri Birlikte Gruplandırma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: be57b56047654d6eb3536bb0b8f63eca27decdb7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a>Nasıl yapılır: İlgili Sabit Değerleri Birlikte Gruplandırma (Visual Basic)
Numaralandırma, ilgili sabitleri gruplamak için en iyi yoludur. Bir numaralandırma ile oluşturduğunuz `Enum` deyiminin bildirimleri bölümünde bir sınıf veya bir modül. Daha fazla bilgi için bkz: [nasıl yapılır: bir numaralandırma bildirme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).  
  
### <a name="to-group-related-constant-values"></a>Grup için ilgili sabit değerleri  
  
1.  Kod erişim düzeyi içeren bir bildirim yazma `Enum` anahtar sözcük ve geçerli bir ad. Bu örnekte `Private` numaralandırma, `temperatureValues`.  
  
     [!code-vb[VbEnumsTask#21](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-group-related-constant-values-together_1.vb)]  
  
2.  Sabitler numaralandırmada tanımlayın. Bu örnekte `Public` numaralandırma `temperatureValues` ve değerlerini atar.  
  
     [!code-vb[VbEnumsTask#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-group-related-constant-values-together_2.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Numaralandırmalar ve ad niteliği](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [Nasıl yapılır: bir numaralandırma üyesine başvurma](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [Bir numaralandırmanın ne zaman kullanılacağı](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [Sabitlere genel bakış](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [Sabit ve değişmez değerli veri türleri](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [Sabitler ve numaralandırmalar](../../../../visual-basic/language-reference/constants-and-enumerations.md)
