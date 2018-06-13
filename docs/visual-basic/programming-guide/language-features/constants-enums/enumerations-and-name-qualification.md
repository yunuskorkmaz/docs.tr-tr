---
title: Numaralandırmalar ve Ad Niteliği (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- Imports statement [Visual Basic], namespace declarations
- declaring namespaces [Visual Basic], enumerations
- name collisions
- ambiguous names [Visual Basic], enumerations
- enumerations [Visual Basic], name qualification
- names [Visual Basic], avoiding conflicts
- namespaces [Visual Basic], declaring
- naming conflicts, enumerations
- naming conflicts, qualifying names
- declaring enumerations
- references [Visual Basic], enumeration members
- naming conventions [Visual Basic], naming conflicts
- declarations [Visual Basic], namespaces
ms.assetid: 08ba2738-df52-4140-bc55-f57c871c9b73
ms.openlocfilehash: eb1f5653d968e81168833cd57813219e8f049b70
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648586"
---
# <a name="enumerations-and-name-qualification-visual-basic"></a>Numaralandırmalar ve Ad Niteliği (Visual Basic)
Normalde, bir numaralandırma üyesi için söz konusu olduğunda numaralandırması adıyla üye nitelemeniz gerekir. Örneğin, başvurmak için `Sunday` üyesi, `Days` numaralandırma, aşağıdaki sözdizimini kullanın:  
  
 [!code-vb[VbEnumsTask#18](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_1.vb)]  
  
## <a name="using-the-imports-statement"></a>Imports deyimi kullanarak  
 Ekleyerek tam olarak nitelenmiş adlar kullanmaktan kaçınabilirsiniz bir `Imports` ad alanı bildirimleri bölümüne aşağıdaki örnekte olduğu gibi kodunuzu deyimi:  
  
 [!code-vb[VbEnumsTask#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_2.vb)]  
  
 Bir `Imports` başvurulan projeleri ve derlemeler ve içinden ad alanı adları Imports deyimi aynı projesi deyim göründüğü modülü olarak. Bu bildirimi eklendikten sonra aşağıdaki örnekte olduğu gibi nitelik olmadan numaralandırma üyeleri başvurabilir:  
  
 [!code-vb[VbEnumsTask#24](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_3.vb)]  
  
 Numaralandırmalar ilgili sabitler kümesi düzenleyerek farklı bağlamlarda aynı sabit adlarını kullanabilirsiniz. Örneğin, haftanın günü sabitler için aynı adlarını kullanabilirsiniz `Days` ve `WorkDays` numaralandırmalar. Kullanırsanız `Imports` deyimi, numaralandırmalar sahip olmanız gerekir belirsiz başvuruları kaçınmak için dikkatli. Aşağıdaki örnek göz önünde bulundurun:  
  
 [!code-vb[VbEnumsTask#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_2.vb)]  
  
 [!code-vb[VbEnumsTask#25](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_4.vb)]  
  
 Varsayılarak `Monday` her ikisi de üyesi `Days` numaralandırma ve `Workdays` numaralandırma, bu kod bir derleyici hatası oluşturur. Tek bir sabite başvururken belirsiz başvuruları önlemek için kendi numaralandırma sabit adıyla nitelemek. Aşağıdaki kod başvurduğu `Saturday` sabitler `Days` ve `WorkDays` numaralandırmalar.  
  
 [!code-vb[VbEnumsTask#32](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_5.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sabitler ve Sabit Listeleri](../../../../visual-basic/language-reference/constants-and-enumerations.md)  
 [Nasıl yapılır: bir numaralandırma bildirme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [Nasıl yapılır: Bir Sabit Listesi Üyesine Başvurma](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [Nasıl yapılır: Visual Basic'de numaralandırma yoluyla yineleme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [Nasıl yapılır: Bir Sabit Listesi Değeriyle İlişkili Dizeyi Belirleme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [Sabit Listesi Ne Zaman Kullanılır?](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [Sabit ve Değişmez Değerli Veri Türleri](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [Enum Deyimi](../../../../visual-basic/language-reference/statements/enum-statement.md)  
 [Imports Deyimi (.NET Ad Alanı ve Türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [Veri Türleri](../../../../visual-basic/language-reference/data-types/data-type-summary.md)
