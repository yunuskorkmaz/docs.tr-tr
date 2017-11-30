---
title: "Handles Tümcesi (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- Handles
- vb.Handles
helpviewer_keywords: Handles keyword [Visual Basic]
ms.assetid: 1b051c0e-f499-42f6-acb5-6f4f27824b40
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a23b3d96052ad179ea25150bb570461a9e764977
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="handles-clause-visual-basic"></a>Handles Tümcesi (Visual Basic)
Bir yordam belirtilen bir olay işleme bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
proceduredeclaration Handles eventlist  
```  
  
## <a name="parts"></a>Bölümler  
 `proceduredeclaration`  
 `Sub` Yordamı bildirimi olayı işleyecek bir yordam.  
  
 `eventlist`  
 Olayları listesi `proceduredeclaration` işlemek için virgülle ayrılmış. Olayları ya da taban sınıfı için geçerli sınıf veya kullanılarak bildirilen bir nesne tarafından oluşturulması `WithEvents` anahtar sözcüğü.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım `Handles` anahtar sözcüğü bir nesne değişkeni tarafından başlatılan olayları işlemek için neden bir yordam bildiriminin sonundaki kullanarak bildirilen `WithEvents` anahtar sözcüğü. `Handles` Anahtar sözcüğü de türetilen bir sınıfta bir temel sınıf olayları işlemek için kullanılabilir.  
  
 `Handles` Anahtar sözcüğü ve `AddHandler` deyimi hem belirli yordamları belirli olayları işleme, ancak bazı farklılıklar vardır belirtmenize olanak tanır. Kullanım `Handles` , belirli bir olay işleme belirtmek için bir yordam tanımlarken anahtar sözcüğü. `AddHandler` Deyimi olaylarına yordamlar çalışma zamanında bağlanır. Daha fazla bilgi için bkz: [AddHandler deyimi](../../../visual-basic/language-reference/statements/addhandler-statement.md).  
  
 Özel olaylar için uygulama olay çağırır `AddHandler` olay işleyici yordamı eklediğinde erişimcisi. Özel olaylar hakkında daha fazla bilgi için bkz: [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbVbalrEvents#2](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_1.vb)]  
  
 Aşağıdaki örnek, türetilmiş bir sınıf nasıl kullanabileceğinizi gösterir `Handles` temel sınıfından bir olayını işlemek için deyimi.  
  
 [!code-vb[VbVbalrEvents#3](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_2.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte iki düğmesi olay işleyicilerini içeren bir **WPF uygulaması** projesi.  
  
 [!code-vb[VbVbalrEvents#41](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_3.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek önceki örneğe eşdeğerdir. `eventlist` İçinde `Handles` yan tümcesi hem düğmelerinin olaylarını içerir.  
  
 [!code-vb[VbVbalrEvents#42](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_4.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)  
 [AddHandler deyimi](../../../visual-basic/language-reference/statements/addhandler-statement.md)  
 [RemoveHandler deyimi](../../../visual-basic/language-reference/statements/removehandler-statement.md)  
 [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md)  
 [RaiseEvent deyimi](../../../visual-basic/language-reference/statements/raiseevent-statement.md)  
 [Olayları](../../../visual-basic/programming-guide/language-features/events/index.md)
