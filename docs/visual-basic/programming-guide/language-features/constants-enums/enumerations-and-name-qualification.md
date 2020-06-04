---
title: Sabit Listeleri ve Ad Niteliği
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
ms.openlocfilehash: 4b09284b8282c481e406050d37cbdb2f3c8686bc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414511"
---
# <a name="enumerations-and-name-qualification-visual-basic"></a>Numaralandırmalar ve Ad Niteliği (Visual Basic)
Normalde, bir numaralandırma üyesine başvuru yaparken, üye adını numaralandırma adıyla nitelemeniz gerekir. Örneğin, `Sunday` numaralandırmanın üyesine başvurmak için `Days` aşağıdaki sözdizimini kullanın:  
  
 [!code-vb[VbEnumsTask#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#18)]  
  
## <a name="using-the-imports-statement"></a>Imports Ifadesini kullanma  
 `Imports`Aşağıdaki örnekte olduğu gibi, kodunuzun ad alanı bildirimleri bölümüne bir ifade ekleyerek tam nitelikli adlar kullanmaktan kaçınabilirsiniz:  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 Bir `Imports` ifade, Başvurulmuş projelerden ve derlemelerden ve aynı proje içinden, deyimin göründüğü modülle ad alanı adlarını içeri aktarır. Bu ifade eklendikten sonra, aşağıdaki örnekte olduğu gibi, nitelik olmadan sabit listesi üyelerinize başvurabilirsiniz:  
  
 [!code-vb[VbEnumsTask#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#24)]  
  
 Numaralandırmalar içindeki ilgili sabitlerin kümelerini düzenleyerek, farklı bağlamlarda aynı sabit adları kullanabilirsiniz. Örneğin, `Days` ve numaralandırmalar içindeki hafta içi sabitler için aynı adları kullanabilirsiniz `WorkDays` . `Imports`İfadesini Numaralandırmalarla birlikte kullanıyorsanız, belirsiz başvuruların önüne geçmek için dikkatli olmanız gerekir. Aşağıdaki örneği inceleyin:  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 [!code-vb[VbEnumsTask#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#25)]  
  
 `Monday`Hem numaralandırmanın hem de numaralandırmanın üyesi olduğu varsayılarak `Days` `Workdays` , bu kod bir derleyici hatası oluşturur. Tek bir Sabitte başvuru yaparken belirsiz başvuruların önüne geçmek için sabit adı kendi numaralandırmasına uygun hale getirebilirsiniz. Aşağıdaki kod `Saturday` , `Days` ve numaralandırmalar içindeki sabitleri ifade eder `WorkDays` .  
  
 [!code-vb[VbEnumsTask#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#32)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sabitler ve numaralandırmalar](../../../language-reference/constants-and-enumerations.md)
- [Nasıl yapılır: numaralandırma bildirme](how-to-declare-enumerations.md)
- [Nasıl yapılır: Bir Sabit Listesi Üyesine Başvurma](how-to-refer-to-an-enumeration-member.md)
- [Nasıl yapılır: Visual Basic'de Numaralandırma Yoluyla Yineleme Yapma](how-to-iterate-through-an-enumeration.md)
- [Nasıl yapılır: Bir Numaralandırma Değeriyle İlişkili Dizeyi Belirleme](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Sabit Listesi Ne Zaman Kullanılır?](when-to-use-an-enumeration.md)
- [Sabit ve Değişmez Değerli Veri Türleri](constant-and-literal-data-types.md)
- [Enum Deyimi](../../../language-reference/statements/enum-statement.md)
- [Imports Deyimi (.NET Ad Alanı ve Türü)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Veri türleri](../../../language-reference/data-types/index.md)
