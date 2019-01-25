---
title: Set Deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Set
helpviewer_keywords:
- property procedures [Visual Basic], Set statements
- Set statement [Visual Basic]
- Set statement [Visual Basic], syntax
- write-only properties
- properties [Visual Basic], write-only
ms.assetid: 9ecc27b4-df84-420d-9075-db25455fb3cd
ms.openlocfilehash: d77c7d3f2e70edcc1028c207150944c5394afbe0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54685379"
---
# <a name="set-statement-visual-basic"></a>Set Deyimi (Visual Basic)
Bildiren bir `Set` bir özelliğe değer atamak için kullanılan özellik yordamı.  
  
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
 İsteğe bağlı biri `Get` ve `Set` bu özellik deyimlerinde. Aşağıdakilerden biri olabilir:  
  
-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
-   [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
-   `Protected Friend`  
  
 Bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `value`  
 Gerekli. Özelliğin yeni değeri içeren bir parametre.  
  
 `datatype`  
 Gerekli if `Option Strict` olduğu `On`. Veri türü `value` parametresi. Belirtilen veri türü özelliğinin veri türü ile aynı olmalıdır nerede bu `Set` deyimi bildirilir.  
  
 `statements`  
 İsteğe bağlı. Çalıştırılan bir veya daha fazla deyim `Set` özelliği yordamı çağrılır.  
  
 `End Set`  
 Gerekli. Tanımını sonlandırır `Set` özellik yordamı.  
  
## <a name="remarks"></a>Açıklamalar  
 Her özelliği bir `Set` özellik yordamı özelliği işaretlenmediği sürece `ReadOnly`. `Set` Yordamı, özelliğin değerini ayarlamak için kullanılır.  
  
 Visual Basic otomatik olarak çağıran bir özelliğin `Set` atama deyiminin özelliğinde depolanacak bir değer sağladığında yordamı.  
  
 Visual Basic için bir parametre geçirir `Set` yordam sırasında özelliği atamaları. İçin bir parametre belirtmezseniz `Set`, tümleşik geliştirme ortamı (IDE) adlı bir örtük parametresini kullanan `value`. Özelliğe atanacak değer parametresi içerir. Genellikle bu değer özel bir yerel değişkene depolayın ve döndürün. her `Get` yordamı çağrılır.  
  
 Özellik bildirimi gövdesi yalnızca özelliğin içerebilir `Get` ve `Set` yordamları arasında [Property deyimi](../../../visual-basic/language-reference/statements/property-statement.md) ve `End Property` deyimi. Bu yordamlar dışında her şey depolanamıyor. Özellikle, bu özelliğin geçerli değerini depolanamıyor. Özellik yordamları birini içinde depolamak, bir özellik yordamı, erişemediği için bu değer özelliği dışında depolamanız gerekir. Değeri depolamak için her zamanki yaklaşımdır bir [özel](../../../visual-basic/language-reference/modifiers/private.md) bildirilen değişkenin özelliği ile aynı düzeyde. Tanımlamanız gerekir bir `Set` yordam içinde geçerli olduğu özellik.  
  
 `Set` Yordamı kullanmadığınız sürece, kapsayan özelliği erişim düzeyi için varsayılan olarak `accessmodifier` içinde `Set` deyimi.  
  
## <a name="rules"></a>Kurallar  
  
-   **Karışık erişim düzeyleri.** Okuma-yazma özelliği tanımlıyorsanız, isteğe bağlı olarak farklı erişim düzeyi için belirtebilirsiniz `Get` veya `Set` yordamı, ancak ikisine birden değil. Bunu yaparsanız, yordam erişim düzeyi özellik erişim düzeyinden daha kısıtlayıcı olmalıdır. Örneğin, özellik bildirilirse `Friend`, bildirebilirsiniz `Set` yordamı `Private`, ama `Public`.  
  
     Tanımlıyorsanız, bir `WriteOnly` özelliği `Set` yordamı tüm özelliği temsil eder. Farklı bir erişim düzeyini bildiremezsiniz `Set`, iki erişim düzeyi özelliği ayarlamanız gerekir.  
  
## <a name="behavior"></a>Davranış  
  
-   **Bir özellik yordamı döndürüyor.** Zaman `Set` yordamı çağıran koda döndürür, sağlanan depolanacak değer deyimi yürütme devam eder.  
  
     `Set` özellik yordamları kullanarak döndürebilir [dönüş deyimi](../../../visual-basic/language-reference/statements/return-statement.md) veya [çıkış bildirimi](../../../visual-basic/language-reference/statements/exit-statement.md).  
  
     `Exit Property` Ve `Return` deyimleri neden hemen bir çıkış bir özellik yordamı. Herhangi bir sayıda `Exit Property` ve `Return` deyimleri yordamda herhangi bir yerinde görünebilir ve karıştırabilir miyim `Exit Property` ve `Return` deyimleri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `Set` bir özelliğin değerini ayarlamak için ifade.  
  
 [!code-vb[VbVbalrStatements#55](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/set-statement_1.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Get Deyimi](../../../visual-basic/language-reference/statements/get-statement.md)
- [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)
- [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Özellik Yordamları](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
