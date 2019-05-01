---
title: İsteğe Bağlı Parametreler (Visual Basic)
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
ms.openlocfilehash: 4ae2366552426af0107c8d7a35bb5368fe30c8a7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791969"
---
# <a name="optional-parameters-visual-basic"></a>İsteğe Bağlı Parametreler (Visual Basic)
Bir yordam parametresinin isteğe bağlı olduğunu ve yordam çağrıldığında bu parametre için hiçbir bağımsız değişken sağlanmaması gerektiğini belirtebilirsiniz. *İsteğe bağlı parametreler* tarafından belirtilen `Optional` yordam tanımında anahtar sözcüğü. Aşağıdaki kurallar geçerlidir:  
  
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
  
 Aşağıdaki örnek, çeşitli çağrılar yapılmaktadır `MsgBox` işlevi. `MsgBox` bir parametre ve iki isteğe bağlı parametreleri zorunludur.  
  
 İlk çağrıda `MsgBox` sırayla üç bağımsız değişken sağlar, `MsgBox` bunları tanımlar. İkinci çağrı yalnızca gerekli bağımsız değişkeni sağlar. Üçüncü ve dördüncü çağrılar, birinci ve üçüncü bağımsız değişkenleri sağlar. Üçüncü çağrı bunu konuma göre ve dördüncü çağrı ise ada göre yapar.  
  
 [!code-vb[VbVbcnProcedures#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#47)]  
  
## <a name="determining-whether-an-optional-argument-is-present"></a>İsteğe Bağlı Bağımsız Değişkenin Var Olup Olmadığını Belirleme  
 Bir yordam, verilen bir bağımsız değişkenin atlanıp atlanmadığını veya çağırma kodunun varsayılan değeri açıkça sağlayıp sağlamadığını çalışma zamanında algılayamaz. Bu ayrımı yapmanız gerekiyorsa, olasılık dışı bir değeri varsayılan olarak ayarlayabilirsiniz. Aşağıdaki yordam isteğe bağlı parametresi tanımlar `office`ve testler için varsayılan değerine `QJZ`bu çağrıda atlanıp atlanmadığını görmek için:  
  
 [!code-vb[VbVbcnProcedures#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#46)]  
  
 İsteğe bağlı parametresi gibi bir başvuru türü ise bir `String`, kullanabileceğiniz `Nothing` varsayılan değer olarak, bu bağımsız değişken için beklenen bir değer belirtilen değil.  
  
## <a name="optional-parameters-and-overloading"></a>İsteğe Bağlı Parametreler ve Aşırı Yükleme  
 İsteğe bağlı parametreler içeren bir yordam tanımlamanın bir başka yolu aşırı yüklemeyi kullanmaktır. İsteğe bağlı tek bir parametreniz varsa, prosedürün iki aşırı yüklenmiş sürümünü (biri parametreyi kabul eden, diğeri ise parametresiz olmak üzere) tanımlayabilirsiniz. Bu yaklaşım, isteğe bağlı parametrelerin sayısı arttıkça daha karmaşık hale gelir. Ancak avantajı, çağırma programının her bir isteğe bağlı bağımsız değişkeni sağlayıp sağlamadığından kesin emin olabilmenizdir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme](./passing-arguments-by-value-and-by-reference.md)
- [Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme](./passing-arguments-by-position-and-by-name.md)
- [Parametre Dizileri](./parameter-arrays.md)
- [Yordam Aşırı Yüklemesi](./procedure-overloading.md)
- [Optional](../../../../visual-basic/language-reference/modifiers/optional.md)
- [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)
