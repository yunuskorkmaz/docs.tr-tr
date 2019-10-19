---
title: Get açıklaması (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Get
helpviewer_keywords:
- Get statement [Visual Basic], syntax
- Get statement [Visual Basic]
- properties [Visual Basic], read-only
- read-only properties
- Get keyword [Visual Basic]
- property procedures [Visual Basic], Get statements
ms.assetid: 56b05cdc-bd64-4dfd-bb12-824eacec6f94
ms.openlocfilehash: d76155b8ff29e4f5e9206ae8fc689fa4fcaf3b8c
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581829"
---
# <a name="get-statement"></a>Get Deyimi
Bir özelliğin değerini almak için kullanılan bir `Get` özellik yordamı bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Get()  
    [ statements ]  
End Get  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`attributelist`|İsteğe bağlı. Bkz. [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Bu özelliğindeki `Get` ve `Set` deyimlerinin en az birinde isteğe bağlı. Aşağıdakilerden biri olabilir:<br /><br /> -   [korumalı](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [arkadaş](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [özel](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> [Visual Basic erişim düzeylerine](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)bakın.|  
|`statements`|İsteğe bağlı. @No__t_0 özellik yordamı çağrıldığında çalışan bir veya daha fazla deyim.|  
|`End Get`|Gerekli. @No__t_0 özelliği yordamının tanımını sonlandırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Özellik `WriteOnly` olarak işaretlenmedikçe her özelliğin `Get` Özellik yordamına sahip olması gerekir. @No__t_0 yordamı, özelliğin geçerli değerini döndürmek için kullanılır.  
  
 Visual Basic bir ifade özelliğin değerini istediğinde bir özelliğin `Get` yordamını otomatik olarak çağırır.  
  
 Özellik bildiriminin gövdesi, Property [ifadesiyle](../../../visual-basic/language-reference/statements/property-statement.md) `End Property` ifadesiyle yalnızca özelliğin `Get` ve `Set` yordamlarını içerebilir. Bu yordamlar dışında bir şey depolayamazsınız. Özellikle, özelliğin geçerli değerini depolayaamaz. Özellik yordamlarından birinde depolursa, diğer özellik yordamının bu değeri, özelliğin dışında depolamanız gerekir. Her zamanki yaklaşım, değeri özelliği ile aynı düzeyde belirtilen [özel](../../../visual-basic/language-reference/modifiers/private.md) bir değişkende depokullanmaktır. Bir `Get` yordamını, uygulandığı özelliğin içinde tanımlamanız gerekir.  
  
 @No__t_0 yordamı, `Get` ifadesinde `accessmodifier` kullanmadığınız durumlar dışında, kendisini kapsayan özelliğin erişim düzeyi olur.  
  
## <a name="rules"></a>Kurallar  
  
- **Karışık erişim düzeyleri.** Okuma-yazma özelliği tanımlıyorsanız, isteğe bağlı olarak `Get` ya da `Set` yordamı için farklı bir erişim düzeyi belirtebilirsiniz, ancak her ikisini birden belirtemezsiniz. Bunu yaparsanız, yordam erişim düzeyinin özelliğin erişim düzeyinden daha kısıtlayıcı olması gerekir. Örneğin, özellik `Friend` olarak bildirilirse, `Private` `Get` yordamını bildirebilirsiniz, ancak `Public`.  
  
     @No__t_0 özelliği tanımlıyorsanız, `Get` yordamı tüm özelliği temsil eder. Özelliği için iki erişim düzeyi ayarlayacağından, `Get` için farklı bir erişim düzeyi bildiremezsiniz.  
  
- **Dönüş türü.** [Property deyimleri](../../../visual-basic/language-reference/statements/property-statement.md) , döndürdüğü değerin veri türünü bildirebilir. @No__t_0 yordam bu veri türünü otomatik olarak döndürür. Herhangi bir veri türü veya bir numaralandırma, yapı, sınıf veya arabirim adı belirtebilirsiniz.  
  
     @No__t_0 deyimin `returntype` belirtmezse yordam `Object` döndürür.  
  
## <a name="behavior"></a>Davranış  
  
- **Bir yordamdan dönme.** @No__t_0 yordamı çağıran koda döndüğünde, yürütme özelliği değeri istenen deyimin içinde devam eder.  
  
     `Get` özellik yordamları, [return ifadesini](../../../visual-basic/language-reference/statements/return-statement.md) kullanarak ya da dönüş değerini özellik adına atayarak bir değer döndürebilir. Daha fazla bilgi için [Işlev deyimindeki](../../../visual-basic/language-reference/statements/function-statement.md)"dönüş değeri" başlığına bakın.  
  
     @No__t_0 ve `Return` deyimleri, bir özellik yordamından anında çıkış oluşmasına neden olur. Herhangi bir sayıda `Exit Property` ve `Return` deyimi yordamda herhangi bir yerde görünebilir ve `Exit Property` ve `Return` deyimlerini karıştırabilirsiniz.  
  
- **Dönüş değeri.** Bir `Get` yordamından bir değer döndürmek için, değeri özellik adına atayabilir ya da bir [Return ifadesine](../../../visual-basic/language-reference/statements/return-statement.md)dahil edebilirsiniz. @No__t_0 deyimleri aynı anda `Get` yordam dönüş değerini atar ve yordamdan çıkar.  
  
     Özellik adına bir değer atamadan `Exit Property` kullanırsanız, `Get` yordamı özelliğin veri türü için varsayılan değeri döndürür. Daha fazla bilgi için [Işlev deyimindeki](../../../visual-basic/language-reference/statements/function-statement.md)"dönüş değeri" başlığına bakın.  
  
     Aşağıdaki örnekte, salt okuma özelliğinin `quoteForTheDay` özel değişkende tutulan değeri döndürebileceği iki yol gösterilmektedir `quoteValue`.  
  
     [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]  
  
     [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]  
  
     [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir özelliğin değerini döndürmek için `Get` ifadesini kullanır.  
  
 [!code-vb[VbVbalrStatements#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#30)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Set Deyimi](../../../visual-basic/language-reference/statements/set-statement.md)
- [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)
- [Exit Deyimi](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Nesneler ve Sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [İzlenecek Yol: Sınıfları Tanımlama](../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)
