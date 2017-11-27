---
title: "Nasıl yapılır: Visual Basic'de Numaralandırma Yoluyla Yineleme Yapma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 439e6eae7d475316625a2cc1d3a70a9e7181f68a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a>Nasıl yapılır: Visual Basic'de Numaralandırma Yoluyla Yineleme Yapma
Numaralandırmalar ilgili sabitleri kümeleriyle çalışmak ve sabit değerleri adlarıyla ilişkilendirmek için kolay bir yol sağlamak. Bir numaralandırma yineleme yapmak için bir dizi kullanarak taşıyabilirsiniz <xref:System.Enum.GetValues%2A> yöntemi. Bir numaralandırma kullanarak aracılığıyla da yinelemek bir `For...Each` deyimi kullanarak <xref:System.Enum.GetNames%2A> veya <xref:System.Enum.GetValues%2A> yöntemi dizeyi veya sayı değerini ayıklayın.  
  
### <a name="to-iterate-through-an-enumeration"></a>Bir numaralandırma yineleme  
  
-   Bir dizi bildirme ve onunla numaralandırması dönüştürmek <xref:System.Enum.GetValues%2A> yöntemi, dizi geçirmeden önce başka bir değişken gerekir. Aşağıdaki örnek her bir numaralandırma üyesi görüntüler <xref:Microsoft.VisualBasic.FirstDayOfWeek> numaralandırma yineleme olarak.  
  
     [!code-vb[VbEnumsTask#7](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-iterate-through-an-enumeration_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Numaralandırmalara genel bakış](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)  
 [Nasıl yapılır: bir numaralandırma bildirme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [Bir numaralandırmanın ne zaman kullanılacağı](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [Nasıl yapılır: bir numaralandırma değeriyle ilişkili dizeyi belirleme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [Nasıl yapılır: bir numaralandırma üyesine başvurma](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [Numaralandırmalar ve ad niteliği](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [Diziler](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
