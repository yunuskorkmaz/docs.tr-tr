---
title: Get deyimi (Visual Basic)
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
ms.openlocfilehash: ade54b2f00c540a1bf4ede311e1631b2c5d7e3ef
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54742399"
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
|`accessmodifier`|İsteğe bağlı biri `Get` ve `Set` bu özellik deyimlerinde. Aşağıdakilerden biri olabilir:<br /><br /> -   [Korumalı](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [arkadaş](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Özel](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> Bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`statements`|İsteğe bağlı. Çalıştırılan bir veya daha fazla deyim `Get` özelliği yordamı çağrılır.|  
|`End Get`|Gerekli. Tanımını sonlandırır `Get` özellik yordamı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Her özelliği bir `Get` özellik yordamı özelliği işaretlenmediği sürece `WriteOnly`. `Get` Yordamı özelliğinin geçerli değeri döndürmek için kullanılır.  
  
 Visual Basic otomatik olarak çağıran bir özelliğin `Get` özelliğinin değeri bir ifade istediğinde yordamı.  
  
 Özellik bildirimi gövdesi yalnızca özelliğin içerebilir `Get` ve `Set` yordamları arasında [Property deyimi](../../../visual-basic/language-reference/statements/property-statement.md) ve `End Property` deyimi. Bu yordamlar dışında her şey depolanamıyor. Özellikle, bu özelliğin geçerli değerini depolanamıyor. Özellik yordamları birini içinde depolamak, bir özellik yordamı, erişemediği için bu değer özelliği dışında depolamanız gerekir. Değeri depolamak için her zamanki yaklaşımdır bir [özel](../../../visual-basic/language-reference/modifiers/private.md) bildirilen değişkenin özelliği ile aynı düzeyde. Tanımlamanız gerekir bir `Get` yordam içinde geçerli olduğu özellik.  
  
 `Get` Yordamı kullanmadığınız sürece, kapsayan özelliği erişim düzeyi için varsayılan olarak `accessmodifier` içinde `Get` deyimi.  
  
## <a name="rules"></a>Kurallar  
  
-   **Karışık erişim düzeyleri.** Okuma-yazma özelliği tanımlıyorsanız, isteğe bağlı olarak farklı erişim düzeyi için belirtebilirsiniz `Get` veya `Set` yordamı, ancak ikisine birden değil. Bunu yaparsanız, yordam erişim düzeyi özellik erişim düzeyinden daha kısıtlayıcı olmalıdır. Örneğin, özellik bildirilirse `Friend`, bildirebilirsiniz `Get` yordamı `Private`, ama `Public`.  
  
     Tanımlıyorsanız, bir `ReadOnly` özelliği `Get` yordamı tüm özelliği temsil eder. Farklı bir erişim düzeyini bildiremezsiniz `Get`, iki erişim düzeyi özelliği ayarlamanız gerekir.  
  
-   **Dönüş türü.** [Property deyimi](../../../visual-basic/language-reference/statements/property-statement.md) döndürdüğü değerin veri türü bildirebilirsiniz. `Get` Yordamı otomatik olarak döndürür veri türü. Herhangi bir veri türü veya bir sabit listesi, yapısı, sınıf veya arabirim adını belirtebilirsiniz.  
  
     Varsa `Property` deyimi belirtmiyor `returntype`, yordam döndürür `Object`.  
  
## <a name="behavior"></a>Davranış  
  
-   **Bir yordam döndürüyor.** Zaman `Get` yordamı çağıran koda döndürür, özellik değeri istenen deyimi içinde yürütme devam eder.  
  
     `Get` özellik yordamları kullanarak bir değer döndürebilir [dönüş deyimi](../../../visual-basic/language-reference/statements/return-statement.md) ya da dönüş değeri, özellik adına atayarak. Daha fazla bilgi için bkz: "Value dönüş" [Function deyimi](../../../visual-basic/language-reference/statements/function-statement.md).  
  
     `Exit Property` Ve `Return` deyimleri neden hemen bir çıkış bir özellik yordamı. Herhangi bir sayıda `Exit Property` ve `Return` deyimleri yordamda herhangi bir yerinde görünebilir ve karıştırabilir miyim `Exit Property` ve `Return` deyimleri.  
  
-   **Dönüş değeri.** Bir değer döndürmek için bir `Get` yordam, özellik adı için değer atamak veya olmasını bir [dönüş deyimi](../../../visual-basic/language-reference/statements/return-statement.md). `Return` Deyimi aynı anda atar `Get` yordamı dönüş değeri ve yordamdan çıkar.  
  
     Kullanırsanız `Exit Property` özellik adı için bir değer atama olmadan `Get` yordamı özelliğin veri türü için varsayılan değeri döndürür. Daha fazla bilgi için bkz: "Value dönüş" [Function deyimi](../../../visual-basic/language-reference/statements/function-statement.md).  
  
     Aşağıdaki örnekte iki şekilde salt okunur özelliği `quoteForTheDay` özel değişkeninde tuttuğu değeri döndürebilir `quoteValue`.  
  
     [!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_1.vb)]  
  
     [!code-vb[VbVbalrStatements#28](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_2.vb)]  
  
     [!code-vb[VbVbalrStatements#29](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_3.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `Get` deyimini bir özelliğinin değerini döndürür.  
  
 [!code-vb[VbVbalrStatements#30](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_4.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Set Deyimi](../../../visual-basic/language-reference/statements/set-statement.md)
- [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)
- [Exit Deyimi](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Nesneler ve Sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [İzlenecek yol: Sınıfları tanımlama](../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)
