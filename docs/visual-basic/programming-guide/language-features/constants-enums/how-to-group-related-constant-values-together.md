---
description: 'Şu konuda daha fazla bilgi edinin: nasıl yapılır: Ilgili sabit değerleri birlikte gruplandırma (Visual Basic)'
title: 'Nasıl yapılır: İlgili Sabit Değerleri Birlikte Gruplandırma'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
ms.openlocfilehash: ddd60696d2c751810e49ecbcb537589bedc58abf
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100471597"
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a>Nasıl yapılır: İlgili Sabit Değerleri Birlikte Gruplandırma (Visual Basic)

Listeleme, ilgili sabitleri birlikte gruplandırmak için en iyi yoldur. `Enum`Bir sınıfın veya modülün Bildirimler bölümünde ifadesiyle bir numaralandırma oluşturursunuz. Daha fazla bilgi için bkz. [nasıl yapılır: numaralandırma bildirme](how-to-declare-enumerations.md).  
  
### <a name="to-group-related-constant-values"></a>İlgili sabit değerleri gruplandırmak için  
  
1. Kod erişim düzeyi, `Enum` anahtar sözcük ve geçerli bir ad içeren bir bildirim yazın. Bu örnek `Private` , sabit listesini oluşturur `temperatureValues` ,.  
  
     [!code-vb[VbEnumsTask#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#21)]  
  
2. Sabit Listesi içindeki sabitleri tanımlayın. Bu örnek, `Public` sabit listesini oluşturur `temperatureValues` ve değerlerini atar.  
  
     [!code-vb[VbEnumsTask#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sabit Listeleri ve Ad Niteliği](enumerations-and-name-qualification.md)
- [Nasıl yapılır: Bir Sabit Listesi Üyesine Başvurma](how-to-refer-to-an-enumeration-member.md)
- [Sabit Listesi Ne Zaman Kullanılır?](when-to-use-an-enumeration.md)
- [Sabitlere Genel Bakış](constants-overview.md)
- [Sabit ve Değişmez Değerli Veri Türleri](constant-and-literal-data-types.md)
- [Sabitler ve numaralandırmalar](../../../language-reference/constants-and-enumerations.md)
