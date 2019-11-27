---
title: 'Nasıl yapılır: sabit listesi üzerinden yineleme yapma'
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
ms.openlocfilehash: 6e8fd6760565a73d9d3b3d1d02fc872992eea354
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354018"
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a>Nasıl yapılır: Visual Basic'de Numaralandırma Yoluyla Yineleme Yapma
Numaralandırmalar ilgili sabitler kümesiyle çalışmanın kolay bir yolunu sağlar ve sabit değerleri adlarla ilişkilendirir. Bir sabit listesi üzerinden yinelemek için <xref:System.Enum.GetValues%2A> yöntemini kullanarak onu bir diziye taşıyabilirsiniz. Ayrıca, dize veya sayısal değeri ayıklamak için <xref:System.Enum.GetNames%2A> veya <xref:System.Enum.GetValues%2A> metodunu kullanarak `For...Each` bir sıralama kullanarak bir sabit listesi üzerinden de yineleyebilirsiniz.  
  
### <a name="to-iterate-through-an-enumeration"></a>Bir sabit listesi üzerinden yinelemek için  
  
- Diziyi başka herhangi bir değişken gibi geçirmeden önce bir diziyi bildirin ve <xref:System.Enum.GetValues%2A> yöntemi ile numaralandırmayı buna dönüştürün. Aşağıdaki örnek, sabit listesinin her bir üyesini numaralandırma boyunca yineleme <xref:Microsoft.VisualBasic.FirstDayOfWeek> görüntüler.  
  
     [!code-vb[VbEnumsTask#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#7)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sabit Listelerine Genel Bakış](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [Nasıl yapılır: numaralandırma bildirme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Sabit Listesi Ne Zaman Kullanılır?](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [Nasıl yapılır: Bir Sabit Listesi Değeriyle İlişkili Dizeyi Belirleme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Nasıl yapılır: Bir Sabit Listesi Üyesine Başvurma](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Sabit Listeleri ve Ad Niteliği](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Diziler](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
