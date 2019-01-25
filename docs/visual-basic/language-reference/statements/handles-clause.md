---
title: Handles Tümcesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Handles
- vb.Handles
helpviewer_keywords:
- Handles keyword [Visual Basic]
ms.assetid: 1b051c0e-f499-42f6-acb5-6f4f27824b40
ms.openlocfilehash: 45fa54d7f7a3e167ffe0545cc3edf6a24900b2b3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492968"
---
# <a name="handles-clause-visual-basic"></a>Handles Tümcesi (Visual Basic)
Bir yordamın belirtilmiş bir olayı işlediğini bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
proceduredeclaration Handles eventlist  
```  
  
## <a name="parts"></a>Bölümler  
 `proceduredeclaration`  
 `Sub` Olayı işleyecek yordam için yordam bildirimi.  
  
 `eventlist`  
 Olayları listesi `proceduredeclaration` işlemek için virgülle ayrılmış. Olayları için geçerli sınıfın ya da temel sınıf veya kullanılarak bildirilen bir nesne oluşturulması `WithEvents` anahtar sözcüğü.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım `Handles` sonunda bir nesne değişkeni tarafından başlatılan olayları işlemek için neden bir yordam bildirimi, anahtar sözcüğü kullanılarak bildirilen `WithEvents` anahtar sözcüğü. `Handles` Anahtar sözcüğü de türetilen bir sınıfta bir temel sınıf olayları işlemek için kullanılabilir.  
  
 `Handles` Anahtar sözcüğü ve `AddHandler` iki deyimi belirli bir yordam belirli olayları işleme, ancak bazı farklılıklar vardır belirtmenize olanak tanır. Kullanım `Handles` , belirli bir olay işleme belirtmek için bir yordam tanımlarken anahtar sözcüğü. `AddHandler` Deyimi olayları yordamları çalışma zamanında bağlanır. Daha fazla bilgi için [AddHandler deyimi](../../../visual-basic/language-reference/statements/addhandler-statement.md).  
  
 Özel olaylar için uygulama olay çağırır `AddHandler` yordamı bir olay işleyicisi eklediğinde erişimcisi. Özel olaylar hakkında daha fazla bilgi için bkz. [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbVbalrEvents#2](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_1.vb)]  
  
 Aşağıdaki örnek, türetilmiş bir sınıf nasıl kullanabileceğinizi gösterir. `Handles` deyimi bir temel sınıftan bir olayı işlemek için.  
  
 [!code-vb[VbVbalrEvents#3](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_2.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek iki düğme olay işleyicilerini içeren bir **WPF uygulaması** proje.  
  
 [!code-vb[VbVbalrEvents#41](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_3.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek önceki örneğe eşdeğerdir. `eventlist` İçinde `Handles` yan tümcesi, iki düğme için olayları içerir.  
  
 [!code-vb[VbVbalrEvents#42](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_4.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)
- [AddHandler Deyimi](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [RemoveHandler Deyimi](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [Event Deyimi](../../../visual-basic/language-reference/statements/event-statement.md)
- [RaiseEvent Deyimi](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
- [Olaylar](../../../visual-basic/programming-guide/language-features/events/index.md)
