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
ms.openlocfilehash: d6a6fdfd191de76871619dea3bd1794b487698aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="get-statement"></a>Get Deyimi
Bildiren bir `Get` özellik yordamı bir özelliğin değerini almak için kullanılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
[ <attributelist> ] [ accessmodifier ] Get()  
    [ statements ]  
End Get  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`attributelist`|İsteğe bağlı. Bkz: [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|İsteğe bağlı en `Get` ve `Set` bu özellik deyimlerinde. Aşağıdakilerden biri olabilir:<br /><br /> -   [Korumalı](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Arkadaş](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Özel](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> Bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`statements`|İsteğe bağlı. Çalıştırılan bir veya daha fazla deyimleri `Get` özellik yordamı çağrılır.|  
|`End Get`|Gerekli. Tanımını sonlandırır `Get` özellik yordamı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Her özellik olmalıdır bir `Get` özellik yordamı özelliği işaretlenmemişse `WriteOnly`. `Get` Yordamı özelliğinin geçerli değeri döndürmek için kullanılır.  
  
 Visual Basic otomatik olarak çağıran bir özelliğin `Get` özelliğin değerini bir deyim istediğinde, yordam.  
  
 Özellik bildirimi gövdesi yalnızca özelliğin içerebilir `Get` ve `Set` yordamları arasında [Property deyimi](../../../visual-basic/language-reference/statements/property-statement.md) ve `End Property` deyimi. Bu yordamlar dışında her şey depolanamıyor. Özellikle, bu özelliğin geçerli değeri depolanamıyor. Özellik yordamları birini içinde depolamak, bir özellik yordamı, erişemediği için bu değeri özellik dışında depolamanız gerekir. Değeri depolamak için normal yaklaşımdır bir [özel](../../../visual-basic/language-reference/modifiers/private.md) değişkeni bildirilen özelliği ile aynı düzeyde. Tanımlamanız gerekir bir `Get` yordamı uygulandığı özelliği içinde.  
  
 `Get` Yordamı kullanmadığınız sürece, içeren özelliğinin erişim düzeyini varsayılan olarak `accessmodifier` içinde `Get` deyimi.  
  
## <a name="rules"></a>Kurallar  
  
-   **Karışık erişim düzeyleri.** Bir okuma-yazma özelliği tanımlıyorsanız, isteğe bağlı olarak farklı erişim düzeyi için ya da belirtebilirsiniz `Get` veya `Set` yordamı, ancak ikisini birden değil. Bunu yaparsanız, yordam erişim düzeyi özelliğin erişim düzeyinden daha kısıtlayıcı olması gerekir. Örneğin, özellik bildirilirse `Friend`, bildirebilirsiniz `Get` yordam `Private`, ama `Public`.  
  
     Tanımlıyorsanız, bir `ReadOnly` özelliği, `Get` yordamı tüm özelliğini temsil eder. Farklı bir erişim düzeyini bildiremezsiniz `Get`, özellik için iki erişim düzeyleri ayarlamanız gerekir.  
  
-   **Dönüş türü.** [Property deyimi](../../../visual-basic/language-reference/statements/property-statement.md) döndürdüğü değerin veri türü bildirebilirsiniz. `Get` Yordamı otomatik olarak döndürür veri türü. Herhangi bir veri türü veya bir numaralandırma, yapısı, sınıf veya arabirim adını belirtebilirsiniz.  
  
     Varsa `Property` deyimi belirtmiyor `returntype`, yordam döndürür `Object`.  
  
## <a name="behavior"></a>Davranış  
  
-   **Bir yordam döndürülüyor.** Zaman `Get` yordamı çağıran kodu döndürür, özellik değeri istenen deyimi içinde yürütme devam eder.  
  
     `Get` özellik yordamları kullanarak bir değer dönebilirsiniz [dönüş deyimi](../../../visual-basic/language-reference/statements/return-statement.md) veya dönüş değeri özellik adına atayarak. Daha fazla bilgi için bkz: "Dönüş değeri" [Function deyimi](../../../visual-basic/language-reference/statements/function-statement.md).  
  
     `Exit Property` Ve `Return` deyimleri neden hemen bir çıkış bir özellik yordam. Herhangi bir sayıda `Exit Property` ve `Return` deyimleri yordamda herhangi bir yerinde görünebilir ve karıştırabilir miyim `Exit Property` ve `Return` deyimleri.  
  
-   **Dönüş değeri.** Bir değer almak için bir `Get` yordamı, özellik adı değerini atayın veya olmasını bir [dönüş deyimi](../../../visual-basic/language-reference/statements/return-statement.md). `Return` Deyimi aynı anda atar `Get` yordamı dönüş değeri ve yordamdan çıkar.  
  
     Kullanırsanız `Exit Property` özellik adı için bir değer atama olmadan `Get` yordamı özelliğin veri türü için varsayılan değeri döndürür. Daha fazla bilgi için bkz: "Dönüş değeri" [Function deyimi](../../../visual-basic/language-reference/statements/function-statement.md).  
  
     Aşağıdaki örnekte, iki yolla salt okunur özelliği gösterilmektedir `quoteForTheDay` özel değişkende tutulan değeri dönebilirsiniz `quoteValue`.  
  
     [!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_1.vb)]  
  
     [!code-vb[VbVbalrStatements#28](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_2.vb)]  
  
     [!code-vb[VbVbalrStatements#29](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_3.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `Get` deyimi bir özelliğin değerini döndürür.  
  
 [!code-vb[VbVbalrStatements#30](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_4.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Set Deyimi](../../../visual-basic/language-reference/statements/set-statement.md)  
 [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Exit Deyimi](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [Nesneler ve Sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [İzlenecek Yol: Sınıfları Tanımlama](../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)
