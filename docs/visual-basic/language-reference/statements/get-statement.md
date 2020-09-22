---
title: Get Deyimi
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
ms.openlocfilehash: 3da6c099b3f43a144484eaddf58605609eb0bbfe
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866206"
---
# <a name="get-statement"></a>Get Deyimi

`Get`Bir özelliğin değerini almak için kullanılan bir özellik yordamı bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Get()  
    [ statements ]  
End Get  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`attributelist`|İsteğe bağlı. Bkz. [öznitelik listesi](attribute-list.md).|  
|`accessmodifier`|`Get`Bu özellikte ve deyimlerden en fazla bir isteğe bağlı `Set` . Aşağıdakilerden biri olabilir:<br /><br /> -   [Korunamadı](../modifiers/protected.md)<br />-   [Dost](../modifiers/friend.md)<br />-   [Özelleştirme](../modifiers/private.md)<br />-   `Protected Friend`<br /><br /> [Visual Basic erişim düzeylerine](../../programming-guide/language-features/declared-elements/access-levels.md)bakın.|  
|`statements`|İsteğe bağlı. Özellik yordamı çağrıldığında çalışan bir veya daha fazla deyim `Get` .|  
|`End Get`|Gereklidir. `Get`Özellik yordamının tanımını sonlandırır.|  
  
## <a name="remarks"></a>Açıklamalar  

 Özellik işaretlenmedikçe her özelliğin bir özellik yordamına sahip olması gerekir `Get` `WriteOnly` . `Get`Yordamı, özelliğin geçerli değerini döndürmek için kullanılır.  
  
 Visual Basic, `Get` bir ifade özelliğin değerini istediğinde bir özelliğin yordamını otomatik olarak çağırır.  
  
 Özellik bildiriminin gövdesi, yalnızca Property Ifadesiyle ve ifadesiyle olan özellik `Get` ve yordamları içerebilir `Set` [Property Statement](property-statement.md) `End Property` . Bu yordamlar dışında bir şey depolayamazsınız. Özellikle, özelliğin geçerli değerini depolayaamaz. Özellik yordamlarından birinde depolursa, diğer özellik yordamının bu değeri, özelliğin dışında depolamanız gerekir. Her zamanki yaklaşım, değeri özelliği ile aynı düzeyde belirtilen [özel](../modifiers/private.md) bir değişkende depokullanmaktır. `Get`Uygulandığı özelliğin içinde bir yordam tanımlamanız gerekir.  
  
 `Get`Yöntemi, bildiriminde kullanmadığınız müddetçe, kendisini kapsayan özelliğin erişim düzeyi olur `accessmodifier` `Get` .  
  
## <a name="rules"></a>Kurallar  
  
- **Karışık erişim düzeyleri.** Okuma-yazma özelliği tanımlıyorsanız, isteğe bağlı olarak ya da yordam için farklı bir erişim düzeyi belirtebilirsiniz `Get` `Set` , ancak her ikisini birden belirtemezsiniz. Bunu yaparsanız, yordam erişim düzeyinin özelliğin erişim düzeyinden daha kısıtlayıcı olması gerekir. Örneğin, özelliği bildirilirse, `Friend` `Get` yordamı bildirebilirsiniz `Private` , ancak kullanamazsınız `Public` .  
  
     Bir `ReadOnly` özellik tanımlıyorsanız, `Get` yordam tüm özelliği temsil eder. `Get`Özelliği için iki erişim düzeyi ayarlayacağından, için farklı bir erişim düzeyi bildiremezsiniz.  
  
- **Dönüş türü.** [Property deyimleri](property-statement.md) , döndürdüğü değerin veri türünü bildirebilir. `Get`Yordam, bu veri türünü otomatik olarak döndürür. Herhangi bir veri türü veya bir numaralandırma, yapı, sınıf veya arabirim adı belirtebilirsiniz.  
  
     `Property`Deyimse `returntype` , yordam döndürür `Object` .  
  
## <a name="behavior"></a>Davranış  
  
- **Bir yordamdan dönme.** `Get`Yordam çağıran koda döndüğünde, yürütme özelliği değeri istenen deyimin içinde devam eder.  
  
     `Get` özellik yordamları, [dönüş ifadesini](return-statement.md) kullanarak veya dönüş değerini özellik adına atayarak bir değer döndürebilir. Daha fazla bilgi için [Işlev deyimindeki](function-statement.md)"dönüş değeri" başlığına bakın.  
  
     `Exit Property`Ve `Return` deyimleri, bir özellik yordamından anında çıkış oluşmasına neden olur. Herhangi bir sayıda `Exit Property` ve `Return` deyimi yordamda herhangi bir yerde görünebilir ve `Exit Property` ve deyimlerini karıştırabilirsiniz `Return` .  
  
- **Dönüş değeri.** Bir yordamdan bir değer döndürmek için `Get` , değeri özellik adına atayabilir ya da bir [Return ifadesine](return-statement.md)dahil edebilirsiniz. `Return`İfade, `Get` yordam dönüş değerini eşzamanlı olarak atar ve yordamdan çıkar.  
  
     `Exit Property`Özellik adına bir değer atamadan kullanırsanız, `Get` yordam özelliğin veri türü için varsayılan değeri döndürür. Daha fazla bilgi için [Işlev deyimindeki](function-statement.md)"dönüş değeri" başlığına bakın.  
  
     Aşağıdaki örnekte, salt okuma özelliğinin `quoteForTheDay` özel değişkende tutulan değeri döndürebileceği iki yol gösterilmektedir `quoteValue` .  
  
     [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]  
  
     [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]  
  
     [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `Get` bir özelliğin değerini döndürmek için ifadesini kullanır.  
  
 [!code-vb[VbVbalrStatements#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#30)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Set deyimleri](set-statement.md)
- [Property Deyimi](property-statement.md)
- [Exit Deyimi](exit-statement.md)
- [Nesneler ve sınıflar](../../programming-guide/language-features/objects-and-classes/index.md)
- [İzlenecek Yol: Sınıfları Tanımlama](../../programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)
