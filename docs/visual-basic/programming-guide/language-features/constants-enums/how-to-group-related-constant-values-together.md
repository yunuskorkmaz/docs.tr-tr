---
title: 'Nasıl yapılır: İlgili Sabit Değerleri Birlikte Gruplandırma'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
ms.openlocfilehash: 151eefee4f69e1db8ba40f91334da8a051b95732
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354038"
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a>Nasıl yapılır: İlgili Sabit Değerleri Birlikte Gruplandırma (Visual Basic)
Listeleme, ilgili sabitleri birlikte gruplandırmak için en iyi yoldur. Bir sınıfın veya modülün Bildirimler bölümünde `Enum` ifadesiyle bir numaralandırma oluşturursunuz. Daha fazla bilgi için bkz. [nasıl yapılır: numaralandırma bildirme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).  
  
### <a name="to-group-related-constant-values"></a>İlgili sabit değerleri gruplandırmak için  
  
1. Kod erişim düzeyini, `Enum` anahtar sözcüğünü ve geçerli bir adı içeren bir bildirim yazın. Bu örnekte, `temperatureValues``Private` numaralandırması oluşturulur.  
  
     [!code-vb[VbEnumsTask#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#21)]  
  
2. Sabit Listesi içindeki sabitleri tanımlayın. Bu örnek `Public` numaralandırma `temperatureValues` oluşturur ve değerlerini atar.  
  
     [!code-vb[VbEnumsTask#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sabit Listeleri ve Ad Niteliği](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Nasıl yapılır: Bir Sabit Listesi Üyesine Başvurma](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Sabit Listesi Ne Zaman Kullanılır?](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [Sabitlere Genel Bakış](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [Sabit ve Değişmez Değerli Veri Türleri](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [Sabitler ve Sabit Listeleri](../../../../visual-basic/language-reference/constants-and-enumerations.md)
