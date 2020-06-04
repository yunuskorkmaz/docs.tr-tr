---
title: Handles Yan Tümcesi
ms.date: 07/20/2015
f1_keywords:
- Handles
- vb.Handles
helpviewer_keywords:
- Handles keyword [Visual Basic]
ms.assetid: 1b051c0e-f499-42f6-acb5-6f4f27824b40
ms.openlocfilehash: df786e4b0f0ab3795592ea57f7af17695b086cfa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404582"
---
# <a name="handles-clause-visual-basic"></a>Handles Tümcesi (Visual Basic)
Bir yordamın belirtilen bir olayı işlediğini bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
proceduredeclaration Handles eventlist  
```  
  
## <a name="parts"></a>Bölümler  
 `proceduredeclaration`  
 `Sub`Olayı işleyecek yordamın yordam bildirimi.  
  
 `eventlist`  
 İşlenecek olayların listesi `proceduredeclaration` , virgülle ayrılmış. Olaylar, geçerli sınıfın temel sınıfı ya da anahtar sözcüğü kullanılarak belirtilen bir nesne tarafından oluşturulmalıdır `WithEvents` .  
  
## <a name="remarks"></a>Açıklamalar  
 `Handles`Anahtar sözcüğü kullanılarak belirtilen bir nesne değişkeni tarafından oluşturulan olayları işlemesini sağlamak için yordam bildiriminin sonundaki anahtar sözcüğünü kullanın `WithEvents` . `Handles`Anahtar sözcüğü, bir temel sınıftan olayları işlemek için türetilmiş bir sınıfta de kullanılabilir.  
  
 `Handles`Anahtar sözcüğü ve `AddHandler` deyimleri her ikisi de belirli olayları işleyen belirli yordamları belirtmenizi sağlar, ancak farklılık vardır. `Handles`Belirli bir olayı işlediğini belirtmek için bir yordam tanımlarken anahtar sözcüğünü kullanın. `AddHandler`İfade, çalışma zamanında yordamları olaylara bağlar. Daha fazla bilgi için bkz. [AddHandler bildirisi](addhandler-statement.md).  
  
 Özel olaylar için uygulama, `AddHandler` yordamı bir olay işleyicisi olarak eklediğinde olayın erişimcisini çağırır. Özel olaylar hakkında daha fazla bilgi için bkz. [Event deyimi](event-statement.md).  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbVbalrEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#2)]  
  
 Aşağıdaki örnek, bir türetilen sınıfın bir `Handles` temel sınıftan bir olayı işlemek için nasıl kullanılacağını gösterir.  
  
 [!code-vb[VbVbalrEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#3)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir **WPF uygulama** projesi için iki düğme olay işleyicisi içerir.  
  
 [!code-vb[VbVbalrEvents#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#41)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, önceki örneğe eşdeğerdir. `eventlist`İçindeki `Handles` yan tümce her iki düğme için de olayları içerir.  
  
 [!code-vb[VbVbalrEvents#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#42)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WithEvents](../modifiers/withevents.md)
- [AddHandler Deyimi](addhandler-statement.md)
- [RemoveHandler Deyimi](removehandler-statement.md)
- [Event Deyimi](event-statement.md)
- [RaiseEvent Deyimi](raiseevent-statement.md)
- [Olaylar](../../programming-guide/language-features/events/index.md)
