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
ms.openlocfilehash: 49d4c36805b64d7232a94e818256723a0437b6ef
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404193"
---
# <a name="set-statement-visual-basic"></a>Set Deyimi (Visual Basic)
`Set`Bir özelliğe değer atamak için kullanılan bir özellik yordamı bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## <a name="parts"></a>Bölümler  
 `attributelist`  
 İsteğe bağlı. Bkz. [öznitelik listesi](attribute-list.md).  
  
 `accessmodifier`  
 `Get`Bu özellikte ve deyimlerden en fazla bir isteğe bağlı `Set` . Aşağıdakilerden biri olabilir:  
  
- [Korunamadı](../modifiers/protected.md)  
  
- [Dost](../modifiers/friend.md)  
  
- [Özelleştirme](../modifiers/private.md)  
  
- `Protected Friend`  
  
 [Visual Basic erişim düzeylerine](../../programming-guide/language-features/declared-elements/access-levels.md)bakın.  
  
 `value`  
 Gereklidir. Özelliği için yeni değeri içeren parametre.  
  
 `datatype`  
 İse gereklidir `Option Strict` `On` . Parametrenin veri türü `value` . Belirtilen veri türü, bu deyimin bildirildiği özelliğin veri türüyle aynı olmalıdır `Set` .  
  
 `statements`  
 İsteğe bağlı. Özellik yordamı çağrıldığında çalışan bir veya daha fazla deyim `Set` .  
  
 `End Set`  
 Gereklidir. `Set`Özellik yordamının tanımını sonlandırır.  
  
## <a name="remarks"></a>Açıklamalar  
 Özellik işaretlenmedikçe her özelliğin bir özellik yordamına sahip olması gerekir `Set` `ReadOnly` . `Set`Yordamı, özelliğinin değerini ayarlamak için kullanılır.  
  
 `Set`Bir atama ekstresi özellikte depolanacak bir değer sağlıyorsa, bir özelliğin yordamını otomatik olarak çağırır Visual Basic.  
  
 Visual Basic, `Set` özellik atamaları sırasında yordama bir parametre geçirir. İçin bir parametre belirtmezseniz `Set` , tümleşik geliştirme ortamı (IDE) adlı örtülü bir parametre kullanır `value` . Parametresi, özelliğine atanacak değeri tutar. Genellikle bu değeri özel bir yerel değişkende depoluyordu ve yordam her çağrıldığında döndürülür `Get` .  
  
 Özellik bildiriminin gövdesi, yalnızca Property Ifadesiyle ve ifadesiyle olan özellik `Get` ve yordamları içerebilir `Set` [Property Statement](property-statement.md) `End Property` . Bu yordamlar dışında bir şey depolayamazsınız. Özellikle, özelliğin geçerli değerini depolayaamaz. Özellik yordamlarından birinde depolursa, diğer özellik yordamının bu değeri, özelliğin dışında depolamanız gerekir. Her zamanki yaklaşım, değeri özelliği ile aynı düzeyde belirtilen [özel](../modifiers/private.md) bir değişkende depokullanmaktır. `Set`Uygulandığı özelliğin içinde bir yordam tanımlamanız gerekir.  
  
 `Set`Yöntemi, bildiriminde kullanmadığınız müddetçe, kendisini kapsayan özelliğin erişim düzeyi olur `accessmodifier` `Set` .  
  
## <a name="rules"></a>Kurallar  
  
- **Karışık erişim düzeyleri.** Okuma-yazma özelliği tanımlıyorsanız, isteğe bağlı olarak ya da yordam için farklı bir erişim düzeyi belirtebilirsiniz `Get` `Set` , ancak her ikisini birden belirtemezsiniz. Bunu yaparsanız, yordam erişim düzeyinin özelliğin erişim düzeyinden daha kısıtlayıcı olması gerekir. Örneğin, özelliği bildirilirse, `Friend` `Set` yordamı bildirebilirsiniz `Private` , ancak kullanamazsınız `Public` .  
  
     Bir `WriteOnly` özellik tanımlıyorsanız, `Set` yordam tüm özelliği temsil eder. `Set`Özelliği için iki erişim düzeyi ayarlayacağından, için farklı bir erişim düzeyi bildiremezsiniz.  
  
## <a name="behavior"></a>Davranış  
  
- **Bir özellik yordamından döndürülüyor.** `Set`Yordam çağıran koda döndüğünde, yürütme, depolanacak değeri sağlayan deyimden sonra devam eder.  
  
     `Set`özellik yordamları, [Return](return-statement.md) ya da [Exit deyimlerini](exit-statement.md)kullanarak dönebilir.  
  
     `Exit Property`Ve `Return` deyimleri, bir özellik yordamından anında çıkış oluşmasına neden olur. Herhangi bir sayıda `Exit Property` ve `Return` deyimi yordamda herhangi bir yerde görünebilir ve `Exit Property` ve deyimlerini karıştırabilirsiniz `Return` .  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `Set` bir özelliğin değerini ayarlamak için ifadesini kullanır.  
  
 [!code-vb[VbVbalrStatements#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#55)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Get Deyimi](get-statement.md)
- [Property Deyimi](property-statement.md)
- [Sub Deyimi](sub-statement.md)
- [Özellik Yordamları](../../programming-guide/language-features/procedures/property-procedures.md)
