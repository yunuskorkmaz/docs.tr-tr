---
title: 'Nasıl yapılır: Bir Numaralandırma Değeriyle İlişkili Dizeyi Belirleme'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- strings [Visual Basic], enumeration values
- values [Visual Basic], enumeration members
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
ms.openlocfilehash: c396a4e2ebe973f5be65c3fab5f22cdedb29be1a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351140"
---
# <a name="how-to-determine-the-string-associated-with-an-enumeration-value-visual-basic"></a>Nasıl yapılır: Bir Numaralandırma Değeriyle İlişkili Dizeyi Belirleme (Visual Basic)
<xref:System.Enum.GetValues%2A> ve <xref:System.Enum.GetNames%2A> yöntemleri, numaralandırma üyeleriyle ilişkili dizeleri ve değerleri belirlemenizi sağlar.  
  
### <a name="to-determine-the-string-associated-with-an-enumeration"></a>Bir sabit listesi ile ilişkili dizeyi belirleme  
  
- Numaralandırma üyeleriyle ilişkili dizeleri almak için <xref:System.Enum.GetNames%2A> yöntemini kullanın. Bu örnek, `flavorEnum`bir sabit listesi bildirir ve sonra her üyeyle ilişkili dizeleri göstermek için <xref:System.Enum.GetNames%2A> yöntemini kullanır.  
  
     [!code-vb[VbEnumsTask#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Enum.GetValues%2A>
- <xref:System.Enum.GetNames%2A>
- <xref:System.Enum>
- [Nasıl yapılır: numaralandırma bildirme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Nasıl yapılır: Bir Sabit Listesi Üyesine Başvurma](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Sabit Listeleri ve Ad Niteliği](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Nasıl yapılır: Visual Basic bir numaralandırmada yineleme yapma](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [Sabit Listesi Ne Zaman Kullanılır?](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [Enum Deyimi](../../../../visual-basic/language-reference/statements/enum-statement.md)
