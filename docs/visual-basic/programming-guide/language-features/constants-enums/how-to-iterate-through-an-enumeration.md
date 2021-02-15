---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Visual Basic bir numaralandırma aracılığıyla yineleme'
title: 'Nasıl yapılır: Sabit Listesi Yoluyla Yineleme'
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
ms.openlocfilehash: a14d65a33e8a2f7872203a6a332dec1e753704f8
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100471571"
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a>Nasıl yapılır: Visual Basic'de Numaralandırma Yoluyla Yineleme Yapma

Numaralandırmalar ilgili sabitler kümesiyle çalışmanın kolay bir yolunu sağlar ve sabit değerleri adlarla ilişkilendirir. Bir numaralandırma boyunca yinelemek için yöntemini kullanarak bir diziye taşıyabilirsiniz <xref:System.Enum.GetValues%2A> . Ayrıca, `For...Each` <xref:System.Enum.GetNames%2A> <xref:System.Enum.GetValues%2A> dize veya sayısal değeri ayıklamak için veya yöntemini kullanarak bir sıralama kullanarak bir numaralandırma aracılığıyla yineleyebilirsiniz.  
  
### <a name="to-iterate-through-an-enumeration"></a>Bir sabit listesi üzerinden yinelemek için  
  
- Diziyi <xref:System.Enum.GetValues%2A> başka herhangi bir değişken gibi geçirmeden önce bir diziyi bildirin ve bu öğeyi bu yönteme dönüştürün. Aşağıdaki örnek, sabit listesinin her bir üyesini <xref:Microsoft.VisualBasic.FirstDayOfWeek> numaralandırma boyunca yineleme yaparken görüntüler.  
  
     [!code-vb[VbEnumsTask#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#7)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sabit Listelerine Genel Bakış](enumerations-overview.md)
- [Nasıl yapılır: numaralandırma bildirme](how-to-declare-enumerations.md)
- [Sabit Listesi Ne Zaman Kullanılır?](when-to-use-an-enumeration.md)
- [Nasıl yapılır: Bir Numaralandırma Değeriyle İlişkili Dizeyi Belirleme](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Nasıl yapılır: Bir Sabit Listesi Üyesine Başvurma](how-to-refer-to-an-enumeration-member.md)
- [Sabit Listeleri ve Ad Niteliği](enumerations-and-name-qualification.md)
- [Diziler](../arrays/index.md)
