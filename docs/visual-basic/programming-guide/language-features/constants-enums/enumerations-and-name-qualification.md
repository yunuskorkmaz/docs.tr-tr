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
ms.openlocfilehash: 9edb809624727aba5c40b410d0356804257bf516
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56964664"
---
# <a name="enumerations-and-name-qualification-visual-basic"></a>Numaralandırmalar ve Ad Niteliği (Visual Basic)
Normalde, bir sabit listesi üyesi için söz konusu olduğunda, üye adını sabit listesi adıyla nitelemeniz gerekir. Örneğin, başvurmak için `Sunday` üyesi, `Days` numaralandırma, aşağıdaki sözdizimini kullanın:  
  
 [!code-vb[VbEnumsTask#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#18)]  
  
## <a name="using-the-imports-statement"></a>Imports deyimi kullanarak  
 Ekleyerek tam olarak nitelenmiş adlar kullanmaktan kaçınabilirsiniz bir `Imports` ad alanı bildirimleri bölümüne aşağıdaki örnekte olduğu gibi kodunuzun deyimi:  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 Bir `Imports` başvurulan projeleri ve derlemeleri ve içinden ad alanı adları Imports deyimi deyim göründüğü modül olarak aynı proje. Bu bildirimi eklendikten sonra aşağıdaki örnekte olduğu gibi bir nitelik olmadan numaralandırma üyeleri başvurabilir:  
  
 [!code-vb[VbEnumsTask#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#24)]  
  
 İlişkili numaralandırmalar sabitlerle kümesi düzenleyerek, farklı bağlamlardaki aynı sabit adları kullanabilirsiniz. Örneğin, hafta içi sabitlerle için aynı adları kullanabilirsiniz `Days` ve `WorkDays` numaralandırma. Kullanırsanız `Imports` ifadesi, sabit listeleri ile olmalısınız belirsiz başvuru kaçınmak dikkatli. Aşağıdaki örnek göz önünde bulundurun:  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 [!code-vb[VbEnumsTask#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#25)]  
  
 Varsayarak `Monday` hem de bir üyesi `Days` numaralandırma ve `Workdays` sabit listesi, bu kod bir derleyici hatası oluşturur. Tek bir sabite söz konusu olduğunda belirsiz başvuru kaçınmak için sabit, sabit listesi adıyla niteleyin. Aşağıdaki kod başvurduğu `Saturday` sabitlerle `Days` ve `WorkDays` numaralandırma.  
  
 [!code-vb[VbEnumsTask#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#32)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Sabitler ve Sabit Listeleri](../../../../visual-basic/language-reference/constants-and-enumerations.md)
- [Nasıl yapılır: Bir numaralandırma bildirme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Nasıl yapılır: Bir numaralandırma üyesine başvurma](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Nasıl yapılır: Visual Basic'de numaralandırma yoluyla yineleme yapma](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [Nasıl yapılır: Bir numaralandırma değeriyle ilişkili dizeyi belirleme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Sabit Listesi Ne Zaman Kullanılır?](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [Sabit ve Değişmez Değerli Veri Türleri](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [Enum Deyimi](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [Imports Deyimi (.NET Ad Alanı ve Türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Veri Türleri](../../../../visual-basic/language-reference/data-types/index.md)
