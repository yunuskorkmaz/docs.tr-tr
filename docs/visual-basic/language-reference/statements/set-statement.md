---
title: Set Deyimi
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
ms.openlocfilehash: 75ad6d87f1785fea13a282d953f117c9c234e203
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349563"
---
# <a name="set-statement-visual-basic"></a>Set Deyimi (Visual Basic)
Bir özelliğe değer atamak için kullanılan bir `Set` özellik yordamı bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## <a name="parts"></a>Bölümler  
 `attributelist`  
 İsteğe bağlı. Bkz. [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md).  
  
 `accessmodifier`  
 Bu özelliğindeki `Get` ve `Set` deyimlerinin en az birinde isteğe bağlı. Aşağıdakilerden biri olabilir:  
  
- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
- [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
- `Protected Friend`  
  
 [Visual Basic erişim düzeylerine](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)bakın.  
  
 `value`  
 Gerekli. Özelliği için yeni değeri içeren parametre.  
  
 `datatype`  
 `Option Strict` `On`olması gerekir. `value` parametresinin veri türü. Belirtilen veri türü, bu `Set` deyimin bildirildiği özelliğin veri türüyle aynı olmalıdır.  
  
 `statements`  
 İsteğe bağlı. `Set` özellik yordamı çağrıldığında çalışan bir veya daha fazla deyim.  
  
 `End Set`  
 Gerekli. `Set` özelliği yordamının tanımını sonlandırır.  
  
## <a name="remarks"></a>Açıklamalar  
 Özellik `ReadOnly`olarak işaretlenmedikçe her özelliğin `Set` Özellik yordamına sahip olması gerekir. `Set` yordamı, özelliğinin değerini ayarlamak için kullanılır.  
  
 Bir atama ekstresi özellikte depolanacak bir değer sağlıyorsa, Visual Basic bir özelliğin `Set` yordamını otomatik olarak çağırır.  
  
 Visual Basic, özellik atamaları sırasında `Set` yordama bir parametre geçirir. `Set`için bir parametre belirtmezseniz, tümleşik geliştirme ortamı (IDE) `value`adlı örtük bir parametre kullanır. Parametresi, özelliğine atanacak değeri tutar. Genellikle bu değeri özel bir yerel değişkende depolar ve `Get` yordamı her çağrıldığında döndürün.  
  
 Özellik bildiriminin gövdesi, Property [ifadesiyle](../../../visual-basic/language-reference/statements/property-statement.md) `End Property` ifadesiyle yalnızca özelliğin `Get` ve `Set` yordamlarını içerebilir. Bu yordamlar dışında bir şey depolayamazsınız. Özellikle, özelliğin geçerli değerini depolayaamaz. Özellik yordamlarından birinde depolursa, diğer özellik yordamının bu değeri, özelliğin dışında depolamanız gerekir. Her zamanki yaklaşım, değeri özelliği ile aynı düzeyde belirtilen [özel](../../../visual-basic/language-reference/modifiers/private.md) bir değişkende depokullanmaktır. Bir `Set` yordamını, uygulandığı özelliğin içinde tanımlamanız gerekir.  
  
 `Set` yordamı, `Set` ifadesinde `accessmodifier` kullanmadığınız durumlar dışında, kendisini kapsayan özelliğin erişim düzeyi olur.  
  
## <a name="rules"></a>Kurallar  
  
- **Karışık erişim düzeyleri.** Okuma-yazma özelliği tanımlıyorsanız, isteğe bağlı olarak `Get` ya da `Set` yordamı için farklı bir erişim düzeyi belirtebilirsiniz, ancak her ikisini birden belirtemezsiniz. Bunu yaparsanız, yordam erişim düzeyinin özelliğin erişim düzeyinden daha kısıtlayıcı olması gerekir. Örneğin, özellik `Friend`olarak bildirilirse, `Private``Set` yordamını bildirebilirsiniz, ancak `Public`.  
  
     `WriteOnly` özelliği tanımlıyorsanız, `Set` yordamı tüm özelliği temsil eder. Özelliği için iki erişim düzeyi ayarlayacağından, `Set`için farklı bir erişim düzeyi bildiremezsiniz.  
  
## <a name="behavior"></a>Davranış  
  
- **Bir özellik yordamından döndürülüyor.** `Set` yordamı çağıran koda döndüğünde, yürütme, depolanacak değeri sağlayan deyimden sonra devam eder.  
  
     `Set` özellik yordamları, [Return](../../../visual-basic/language-reference/statements/return-statement.md) veya [Exit deyimlerini](../../../visual-basic/language-reference/statements/exit-statement.md)kullanarak dönebilir.  
  
     `Exit Property` ve `Return` deyimleri, bir özellik yordamından anında çıkış oluşmasına neden olur. Herhangi bir sayıda `Exit Property` ve `Return` deyimi yordamda herhangi bir yerde görünebilir ve `Exit Property` ve `Return` deyimlerini karıştırabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir özelliğin değerini ayarlamak için `Set` ifadesini kullanır.  
  
 [!code-vb[VbVbalrStatements#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#55)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Get Deyimi](../../../visual-basic/language-reference/statements/get-statement.md)
- [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)
- [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Özellik Yordamları](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
