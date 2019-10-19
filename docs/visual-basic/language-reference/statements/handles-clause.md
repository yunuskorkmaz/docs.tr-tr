---
title: Handles Tümcesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Handles
- vb.Handles
helpviewer_keywords:
- Handles keyword [Visual Basic]
ms.assetid: 1b051c0e-f499-42f6-acb5-6f4f27824b40
ms.openlocfilehash: ae05e77515e4e2b50cdf5f9a1908375fa311c3a3
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581806"
---
# <a name="handles-clause-visual-basic"></a>Handles Tümcesi (Visual Basic)
Bir yordamın belirtilen bir olayı işlediğini bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
proceduredeclaration Handles eventlist  
```  
  
## <a name="parts"></a>Bölümler  
 `proceduredeclaration`  
 Olayı işleyecek yordamın `Sub` yordam bildirimi.  
  
 `eventlist`  
 İşlenecek `proceduredeclaration`, virgülle ayırarak olayların listesi. Olaylar, geçerli sınıfın temel sınıfı veya `WithEvents` anahtar sözcüğü kullanılarak belirtilen bir nesne tarafından oluşturulmalıdır.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir yordam bildiriminin sonundaki `Handles` anahtar sözcüğünü kullanarak, `WithEvents` anahtar sözcüğü kullanılarak belirtilen bir nesne değişkeni tarafından oluşturulan olayların işlemesine neden olur. @No__t_0 anahtar sözcüğü, bir temel sınıftan olayları işlemek için türetilmiş bir sınıfta de kullanılabilir.  
  
 @No__t_0 anahtar sözcüğü ve `AddHandler` deyimin her ikisi de belirli olayları işleyen belirli yordamları belirtmenizi sağlar, ancak farklar vardır. Belirli bir olayı işlediğini belirtmek için bir yordam tanımlarken `Handles` anahtar sözcüğünü kullanın. @No__t_0 ifade, çalışma zamanında yordamları olaylara bağlar. Daha fazla bilgi için bkz. [AddHandler bildirisi](../../../visual-basic/language-reference/statements/addhandler-statement.md).  
  
 Özel olaylar için uygulama, yordamı bir olay işleyicisi olarak eklediğinde olayın `AddHandler` erişimcisini çağırır. Özel olaylar hakkında daha fazla bilgi için bkz. [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbVbalrEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#2)]  
  
 Aşağıdaki örnek, bir türetilen sınıfın bir temel sınıftan bir olayı işlemek için `Handles` deyiminizi nasıl kullanabileceğinizi gösterir.  
  
 [!code-vb[VbVbalrEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#3)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir **WPF uygulama** projesi için iki düğme olay işleyicisi içerir.  
  
 [!code-vb[VbVbalrEvents#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#41)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, önceki örneğe eşdeğerdir. @No__t_1 yan tümcesindeki `eventlist` her iki düğme için de olayları içerir.  
  
 [!code-vb[VbVbalrEvents#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#42)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)
- [AddHandler Deyimi](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [RemoveHandler Deyimi](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [Event Deyimi](../../../visual-basic/language-reference/statements/event-statement.md)
- [RaiseEvent Deyimi](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
- [Olaylar](../../../visual-basic/programming-guide/language-features/events/index.md)
