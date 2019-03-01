---
title: "Nasıl yapılır: Visual Basic'de numaralandırma yoluyla yineleme yapma"
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
ms.openlocfilehash: dd7a540839fd833d3a316506e433c576edae5384
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979092"
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a>Nasıl yapılır: Visual Basic'de numaralandırma yoluyla yineleme yapma
Numaralandırmalar ilgili sabitlerinin kümeleri ile birlikte çalışır ve adları ile sabit değerleri ilişkilendirmek için kullanışlı bir yol sağlar. Sabit listesi yoluyla yineleme yapmak için bir dizi kullanarak taşıyabilirsiniz <xref:System.Enum.GetValues%2A> yöntemi. Bir listeleme kullanarak aracılığıyla da yineleme bir `For...Each` deyimini kullanarak <xref:System.Enum.GetNames%2A> veya <xref:System.Enum.GetValues%2A> dize veya sayısal değeri ayıklamak için yöntemi.  
  
### <a name="to-iterate-through-an-enumeration"></a>Sabit listesi yoluyla yineleme yapmak için  
  
-   Bir diziyi bildirmek ve onunla numaralandırma dönüştürmek <xref:System.Enum.GetValues%2A> yöntemi, dizi geçirmeden önce başka bir değişken gerekir. Aşağıdaki örnek, her bir numaralandırma üyesi görüntüler <xref:Microsoft.VisualBasic.FirstDayOfWeek> olarak sabit listesi yinelenir.  
  
     [!code-vb[VbEnumsTask#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#7)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Sabit Listelerine Genel Bakış](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [Nasıl yapılır: Bir numaralandırma bildirme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Sabit Listesi Ne Zaman Kullanılır?](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [Nasıl yapılır: Bir numaralandırma değeriyle ilişkili dizeyi belirleme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Nasıl yapılır: Bir numaralandırma üyesine başvurma](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Sabit Listeleri ve Ad Niteliği](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Diziler](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
