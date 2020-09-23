---
title: 'Nasıl yapılır: Bir Numaralandırma Değeriyle İlişkili Dizeyi Belirleme'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- strings [Visual Basic], enumeration values
- values [Visual Basic], enumeration members
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
ms.openlocfilehash: 4138759bfbb049b77406fc536219b40d3ed9e2a5
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058775"
---
# <a name="how-to-determine-the-string-associated-with-an-enumeration-value-visual-basic"></a>Nasıl yapılır: Bir Numaralandırma Değeriyle İlişkili Dizeyi Belirleme (Visual Basic)

<xref:System.Enum.GetValues%2A>Ve <xref:System.Enum.GetNames%2A> yöntemleri, numaralandırma üyeleriyle ilişkili dizeleri ve değerleri belirlemenizi sağlar.  
  
### <a name="to-determine-the-string-associated-with-an-enumeration"></a>Bir sabit listesi ile ilişkili dizeyi belirleme  
  
- <xref:System.Enum.GetNames%2A>Numaralandırma üyeleriyle ilişkili dizeleri almak için yöntemini kullanın. Bu örnek bir sabit listesi bildirir, `flavorEnum` sonra <xref:System.Enum.GetNames%2A> her üyeyle ilişkili dizeleri göstermek için yöntemini kullanır.  
  
     [!code-vb[VbEnumsTask#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Enum.GetValues%2A>
- <xref:System.Enum.GetNames%2A>
- <xref:System.Enum>
- [Nasıl yapılır: numaralandırma bildirme](how-to-declare-enumerations.md)
- [Nasıl yapılır: Bir Sabit Listesi Üyesine Başvurma](how-to-refer-to-an-enumeration-member.md)
- [Sabit Listeleri ve Ad Niteliği](enumerations-and-name-qualification.md)
- [Nasıl yapılır: Visual Basic'de Numaralandırma Yoluyla Yineleme Yapma](how-to-iterate-through-an-enumeration.md)
- [Sabit Listesi Ne Zaman Kullanılır?](when-to-use-an-enumeration.md)
- [Enum Deyimi](../../../language-reference/statements/enum-statement.md)
