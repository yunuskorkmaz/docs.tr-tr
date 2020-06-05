---
title: 'Nasıl yapılır: Bir Numaralandırma Üyesine Başvurma'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], referring to
- values [Visual Basic], associating constant values with names
- enumeration members
- constants [Visual Basic], enumerated
ms.assetid: bbb5c3cc-7cdb-4814-8d6a-a6d91546ed1e
ms.openlocfilehash: 66c527bd4ba4721065de8fca8534fe652d0139be
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414420"
---
# <a name="how-to-refer-to-an-enumeration-member-visual-basic"></a>Nasıl yapılır: Bir Numaralandırma Üyesine Başvurma (Visual Basic)
Numaralandırmalar ilgili sabitler kümesiyle çalışmak ve sabit değerleri adlarla ilişkilendirmek için kullanışlı bir yol sağlar. Örneğin, haftanın günleriyle ilişkili bir tamsayı sabitleri kümesi için bir sabit listesi belirtebilir ve ardından kodunuzda tamsayı değerleri yerine günlerin adlarını kullanabilirsiniz.  
  
 İfadesiyle tam nitelikli adlar kullanmaktan kaçınabilirsiniz `Imports` . Daha fazla bilgi için bkz. [numaralandırmalar ve ad niteliği](enumerations-and-name-qualification.md).  
  
### <a name="to-refer-to-an-enumeration-member"></a>Bir numaralandırma üyesine başvurmak için  
  
- Üye adını listeleme ile niteleyin. Örneğin, aşağıdaki örnek, `Saturday` `FirstDayOfWeek` numaralandırmanın üyesini değişkenine atar `DayValue` .  
  
     [!code-vb[VbEnumsTask#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#19)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: numaralandırma bildirme](how-to-declare-enumerations.md)
- [Sabit Listeleri ve Ad Niteliği](enumerations-and-name-qualification.md)
- [Nasıl yapılır: Visual Basic'de Numaralandırma Yoluyla Yineleme Yapma](how-to-iterate-through-an-enumeration.md)
- [Nasıl yapılır: Bir Numaralandırma Değeriyle İlişkili Dizeyi Belirleme](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Sabit Listesi Ne Zaman Kullanılır?](when-to-use-an-enumeration.md)
