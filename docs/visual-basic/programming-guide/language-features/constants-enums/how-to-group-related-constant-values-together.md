---
title: 'Nasıl yapılır: İlgili Sabit Değerleri Birlikte Gruplandırma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
ms.openlocfilehash: 320373116ad4d61293690353fce6b7b152e79a4f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646410"
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a>Nasıl yapılır: İlgili Sabit Değerleri Birlikte Gruplandırma (Visual Basic)
Numaralandırma, ilgili sabitleri gruplamak için en iyi yoludur. Bir numaralandırma ile oluşturduğunuz `Enum` deyiminin bildirimleri bölümünde bir sınıf veya bir modül. Daha fazla bilgi için bkz: [nasıl yapılır: bir numaralandırma bildirme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).  
  
### <a name="to-group-related-constant-values"></a>Grup için ilgili sabit değerleri  
  
1.  Kod erişim düzeyi içeren bir bildirim yazma `Enum` anahtar sözcük ve geçerli bir ad. Bu örnekte `Private` numaralandırma, `temperatureValues`.  
  
     [!code-vb[VbEnumsTask#21](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-group-related-constant-values-together_1.vb)]  
  
2.  Sabitler numaralandırmada tanımlayın. Bu örnekte `Public` numaralandırma `temperatureValues` ve değerlerini atar.  
  
     [!code-vb[VbEnumsTask#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-group-related-constant-values-together_2.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sabit Listeleri ve Ad Niteliği](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [Nasıl yapılır: Bir Sabit Listesi Üyesine Başvurma](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [Sabit Listesi Ne Zaman Kullanılır?](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [Sabitlere Genel Bakış](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [Sabit ve Değişmez Değerli Veri Türleri](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [Sabitler ve Sabit Listeleri](../../../../visual-basic/language-reference/constants-and-enumerations.md)
