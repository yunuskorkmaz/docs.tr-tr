---
title: 'Nasıl yapılır: Bir sabit listesi değeri (Visual Basic) ile ilişkili dizeyi belirleme'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- strings [Visual Basic], enumeration values
- values [Visual Basic], enumeration members
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
ms.openlocfilehash: 74dff310ccba0bebcf96576d769bf50420ca7397
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971695"
---
# <a name="how-to-determine-the-string-associated-with-an-enumeration-value-visual-basic"></a>Nasıl yapılır: Bir sabit listesi değeri (Visual Basic) ile ilişkili dizeyi belirleme
<xref:System.Enum.GetValues%2A> Ve <xref:System.Enum.GetNames%2A> yöntemler dizeleri ve numaralandırma üyeleri ile ilişkilendirilmiş değerlerini belirlemenize olanak sağlar.  
  
### <a name="to-determine-the-string-associated-with-an-enumeration"></a>Bir numaralandırma ile ilişkili dizeyi belirleme  
  
-   Kullanım <xref:System.Enum.GetNames%2A> numaralandırma üyeleri ile ilişkilendirilmiş dizeler almak için yöntemi. Bu örnek, bir sabit listesi bildirir `flavorEnum`, ardından <xref:System.Enum.GetNames%2A> her üye ile ilişkili dizelerin görüntülemek için yöntemi.  
  
     [!code-vb[VbEnumsTask#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Enum.GetValues%2A>
- <xref:System.Enum.GetNames%2A>
- <xref:System.Enum>
- [Nasıl yapılır: Bir numaralandırma bildirme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Nasıl yapılır: Bir numaralandırma üyesine başvurma](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Sabit Listeleri ve Ad Niteliği](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Nasıl yapılır: Visual Basic'de numaralandırma yoluyla yineleme yapma](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [Sabit Listesi Ne Zaman Kullanılır?](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [Enum Deyimi](../../../../visual-basic/language-reference/statements/enum-statement.md)
