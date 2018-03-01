---
title: Set Deyimi (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Set
helpviewer_keywords:
- property procedures [Visual Basic], Set statements
- Set statement [Visual Basic]
- Set statement [Visual Basic], syntax
- write-only properties
- properties [Visual Basic], write-only
ms.assetid: 9ecc27b4-df84-420d-9075-db25455fb3cd
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3b18e6c858e64e78d7ab85fdaafd70e510f7a02f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="set-statement-visual-basic"></a>Set Deyimi (Visual Basic)
Bildiren bir `Set` bir özellik için bir değer atamak için kullanılan özellik yordamı.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## <a name="parts"></a>Bölümler  
 `attributelist`  
 İsteğe bağlı. Bkz: [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md).  
  
 `accessmodifier`  
 İsteğe bağlı en `Get` ve `Set` bu özellik deyimlerinde. Aşağıdakilerden biri olabilir:  
  
-   [Korumalı](../../../visual-basic/language-reference/modifiers/protected.md)  
  
-   [Arkadaş](../../../visual-basic/language-reference/modifiers/friend.md)  
  
-   [Özel](../../../visual-basic/language-reference/modifiers/private.md)  
  
-   `Protected Friend`  
  
 Bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `value`  
 Gerekli. Özelliği için yeni değer içeren bir parametre.  
  
 `datatype`  
 Gerekli olursa `Option Strict` olan `On`. Veri türü `value` parametresi. Belirtilen veri türü özelliğin veri türü ile aynı olması gerekir, bu `Set` deyimi bildirildi.  
  
 `statements`  
 İsteğe bağlı. Çalıştırılan bir veya daha fazla deyimleri `Set` özellik yordamı çağrılır.  
  
 `End Set`  
 Gerekli. Tanımını sonlandırır `Set` özellik yordamı.  
  
## <a name="remarks"></a>Açıklamalar  
 Her özellik olmalıdır bir `Set` özellik yordamı özelliği işaretlenmemişse `ReadOnly`. `Set` Yordamı özelliğinin değeri ayarlamak için kullanılır.  
  
 Visual Basic otomatik olarak çağıran bir özelliğin `Set` atama deyiminin özelliğinde depolanması için bir değer sağladığında yordamı.  
  
 Visual Basic geçirir parametresi `Set` yordam sırasında özelliği atamaları. İçin bir parametre belirtmezseniz `Set`, tümleşik geliştirme ortamı (IDE) adlı bir örtük parametresini kullanır `value`. Parametre özelliğine atanan değer tutar. Genellikle bu değer bir özel yerel değişkende depolayın ve döndürün her `Get` yordamı çağrılır.  
  
 Özellik bildirimi gövdesi yalnızca özelliğin içerebilir `Get` ve `Set` yordamları arasında [Property deyimi](../../../visual-basic/language-reference/statements/property-statement.md) ve `End Property` deyimi. Bu yordamlar dışında her şey depolanamıyor. Özellikle, bu özelliğin geçerli değeri depolanamıyor. Özellik yordamları birini içinde depolamak, bir özellik yordamı, erişemediği için bu değeri özellik dışında depolamanız gerekir. Değeri depolamak için normal yaklaşımdır bir [özel](../../../visual-basic/language-reference/modifiers/private.md) değişkeni bildirilen özelliği ile aynı düzeyde. Tanımlamanız gerekir bir `Set` yordamı uygulandığı özelliği içinde.  
  
 `Set` Yordamı kullanmadığınız sürece, içeren özelliğinin erişim düzeyini varsayılan olarak `accessmodifier` içinde `Set` deyimi.  
  
## <a name="rules"></a>Kurallar  
  
-   **Karışık erişim düzeyleri.** Bir okuma-yazma özelliği tanımlıyorsanız, isteğe bağlı olarak farklı erişim düzeyi için ya da belirtebilirsiniz `Get` veya `Set` yordamı, ancak ikisini birden değil. Bunu yaparsanız, yordam erişim düzeyi özelliğin erişim düzeyinden daha kısıtlayıcı olması gerekir. Örneğin, özellik bildirilirse `Friend`, bildirebilirsiniz `Set` yordam `Private`, ama `Public`.  
  
     Tanımlıyorsanız, bir `WriteOnly` özelliği, `Set` yordamı tüm özelliğini temsil eder. Farklı bir erişim düzeyini bildiremezsiniz `Set`, özellik için iki erişim düzeyleri ayarlamanız gerekir.  
  
## <a name="behavior"></a>Davranış  
  
-   **Bir özellik yordamından döndürülüyor.** Zaman `Set` yordamı çağıran kodu döndürür, değerin depolanması için sağlanan deyimi yürütme devam eder.  
  
     `Set`özellik yordamları kullanarak dönebilirsiniz [dönüş deyimi](../../../visual-basic/language-reference/statements/return-statement.md) veya [çıkış deyimi](../../../visual-basic/language-reference/statements/exit-statement.md).  
  
     `Exit Property` Ve `Return` deyimleri neden hemen bir çıkış bir özellik yordam. Herhangi bir sayıda `Exit Property` ve `Return` deyimleri yordamda herhangi bir yerinde görünebilir ve karıştırabilir miyim `Exit Property` ve `Return` deyimleri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `Set` bir özelliğin değerini ayarlamak için ifade.  
  
 [!code-vb[VbVbalrStatements#55](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/set-statement_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Get deyimi](../../../visual-basic/language-reference/statements/get-statement.md)  
 [Property deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Sub deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Özellik yordamları](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
