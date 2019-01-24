---
title: 'Nasıl yapılır: Grup ilgili sabit değerleri birlikte (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
ms.openlocfilehash: 04697092534daa6f83a29e69dcdc509644fa6147
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558689"
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a>Nasıl yapılır: Grup ilgili sabit değerleri birlikte (Visual Basic)
Bir sabit listesi, ilgili sabit değerleri birlikte gruplamak için en iyi bir yoludur. Numaralandırma ile oluşturma `Enum` bir sınıf veya modül bildirimleri bölümünde bildirimi. Daha fazla bilgi için [nasıl yapılır: Bir numaralandırma bildirme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).  
  
### <a name="to-group-related-constant-values"></a>Gruba ilgili sabit değerleri  
  
1.  Kod erişim düzeyi içeren bir bildirimi yazma `Enum` anahtar sözcük ve geçerli bir ad. Bu örnekte `Private` numaralandırma `temperatureValues`.  
  
     [!code-vb[VbEnumsTask#21](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-group-related-constant-values-together_1.vb)]  
  
2.  Sabitleri sabit listesi tanımlayın. Bu örnekte `Public` numaralandırma `temperatureValues` ve değerleri atar.  
  
     [!code-vb[VbEnumsTask#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-group-related-constant-values-together_2.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Sabit Listeleri ve Ad Niteliği](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Nasıl yapılır: Bir numaralandırma üyesine başvurma](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Sabit Listesi Ne Zaman Kullanılır?](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [Sabitlere Genel Bakış](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [Sabit ve Değişmez Değerli Veri Türleri](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [Sabitler ve Sabit Listeleri](../../../../visual-basic/language-reference/constants-and-enumerations.md)
