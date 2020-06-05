---
title: İsteğe Bağlı Parametreler
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [Visual Basic], optional
- Visual Basic code, procedures
- procedures [Visual Basic], optional arguments
- optional arguments
- named arguments [Visual Basic], and optional arguments
- optional parameters
- Optional keyword [Visual Basic], optional arguments
- arguments [Visual Basic], optional
- optional arguments [Visual Basic], and named arguments
ms.assetid: 398d2845-1069-4e94-b934-a73b545c8b87
ms.openlocfilehash: 4e07b75c94b4aea681e6e862e161bda80b2833fc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364337"
---
# <a name="optional-parameters-visual-basic"></a>İsteğe Bağlı Parametreler (Visual Basic)
Bir yordam parametresinin isteğe bağlı olduğunu ve yordam çağrıldığında bu parametre için hiçbir bağımsız değişken sağlanmaması gerektiğini belirtebilirsiniz. *Isteğe bağlı parametreler* , `Optional` yordam tanımındaki anahtar kelimesiyle belirtilir. Aşağıdaki kurallar geçerlidir:  
  
- Yordam tanımındaki her isteğe bağlı parametre bir varsayılan değer belirtmelidir.  
  
- İsteğe bağlı parametreye ilişkin varsayılan değer bir sabit ifade olmalıdır.  
  
- Yordam tanımında isteğe bağlı parametreden sonra gelen her parametre de isteğe bağlı olmalıdır.  
  
 Aşağıdaki sözdiziminde, isteğe bağlı parametresi bulunan bir yordam bildirimi gösterilmektedir:  
  
```vb  
Sub name(ByVal parameter1 As datatype1, Optional ByVal parameter2 As datatype2 = defaultvalue)  
```  
  
## <a name="calling-procedures-with-optional-parameters"></a>İsteğe Bağlı Parametreler İçeren Yordamları Çağırma  
 İsteğe bağlı parametre içeren bir yordamı çağırdığınızda, bağımsız değişkeni sağlayıp sağlamamayı seçebilirsiniz. Bunu yapmazsanız, yordam bu parametre için bildirilen varsayılan değeri kullanır.  
  
 Bağımsız değişken listesinde bir veya daha fazla isteğe bağlı bağımsız değişkeni atladığınızda, bunların konumlarını işaretlemek için ardışık virgüller kullanırsınız. Aşağıdaki örnek çağrı birinci ve dördüncü bağımsız değişkeni sağlamakta, ancak ikinci veya üçüncüyü sağlamamaktadır:  
  
```vb  
Sub name(argument 1, , , argument 4)  
```  
  
 Aşağıdaki örnek, işlevine birkaç çağrı yapar `MsgBox` . `MsgBox`bir gerekli parametreye ve iki isteğe bağlı parametreye sahiptir.  
  
 İçin ilk çağrı, `MsgBox` her üç bağımsız değişkeni bunları tanımlayan sırayla sağlar `MsgBox` . İkinci çağrı yalnızca gerekli bağımsız değişkeni sağlar. Üçüncü ve dördüncü çağrılar, birinci ve üçüncü bağımsız değişkenleri sağlar. Üçüncü çağrı bunu konuma göre ve dördüncü çağrı ise ada göre yapar.  
  
 [!code-vb[VbVbcnProcedures#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#47)]  
  
## <a name="determining-whether-an-optional-argument-is-present"></a>İsteğe Bağlı Bağımsız Değişkenin Var Olup Olmadığını Belirleme  
 Bir yordam, verilen bir bağımsız değişkenin atlanıp atlanmadığını veya çağırma kodunun varsayılan değeri açıkça sağlayıp sağlamadığını çalışma zamanında algılayamaz. Bu ayrımı yapmanız gerekiyorsa, olasılık dışı bir değeri varsayılan olarak ayarlayabilirsiniz. Aşağıdaki yordam isteğe bağlı parametresini tanımlar `office` ve `QJZ` çağrının atlandığını görmek için varsayılan değerini sınar:  
  
 [!code-vb[VbVbcnProcedures#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#46)]  
  
 İsteğe bağlı parametre gibi bir başvuru türü ise `String` , `Nothing` varsayılan değer olarak kullanabilirsiniz; Bu, bağımsız değişken için beklenen bir değer değildir.  
  
## <a name="optional-parameters-and-overloading"></a>İsteğe Bağlı Parametreler ve Aşırı Yükleme  
 İsteğe bağlı parametreler içeren bir yordam tanımlamanın bir başka yolu aşırı yüklemeyi kullanmaktır. İsteğe bağlı tek bir parametreniz varsa, prosedürün iki aşırı yüklenmiş sürümünü (biri parametreyi kabul eden, diğeri ise parametresiz olmak üzere) tanımlayabilirsiniz. Bu yaklaşım, isteğe bağlı parametrelerin sayısı arttıkça daha karmaşık hale gelir. Ancak avantajı, çağırma programının her bir isteğe bağlı bağımsız değişkeni sağlayıp sağlamadığından kesin emin olabilmenizdir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme](./passing-arguments-by-value-and-by-reference.md)
- [Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme](./passing-arguments-by-position-and-by-name.md)
- [Parametre Dizileri](./parameter-arrays.md)
- [Yordam Aşırı Yüklemesi](./procedure-overloading.md)
- [İsteğe Bağlı](../../../language-reference/modifiers/optional.md)
- [ParamArray](../../../language-reference/modifiers/paramarray.md)
