---
title: Parametre Listesi (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic
- parameters [Visual Basic], lists
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- arguments [Visual Basic], Visual Basic
- procedures [Visual Basic], parameter lists
ms.assetid: 5d737319-0c34-4df9-a23d-188fc840becd
ms.openlocfilehash: 147a2501219db9f1f1c10f9cf1a81aa395b5ec2b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605062"
---
# <a name="parameter-list-visual-basic"></a>Parametre Listesi (Visual Basic)
Bunu çağrıldığında bir yordam bekliyor parametreleri belirtir. Birden çok parametre virgülle ayrılır. Bir parametre sözdizimi verilmiştir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
[ <attributelist> ] [ Optional ] [{ ByVal | ByRef }] [ ParamArray ]   
parametername[( )] [ As parametertype ] [ = defaultvalue ]  
```  
  
## <a name="parts"></a>Bölümler  
 `attributelist`  
 İsteğe bağlı. Bu parametre için geçerli öznitelikler listesi. İçine almalısınız [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md) açılı ayraç ("`<`"ve"`>`").  
  
 `Optional`  
 İsteğe bağlı. Yordam çağrıldığında, bu parametre gerekli olmadığını belirtir.  
  
 `ByVal`  
 İsteğe bağlı. Yordamı olamaz veya Değiştir çağıran kodu karşılık gelen değişkeninde temel değişken öğesi yeniden atama belirtir.  
  
 `ByRef`  
 İsteğe bağlı. Yordamı çağıran kod aynı şekilde çağıran kodu temel değişken öğesinde değiştirebilirsiniz belirtir.  
  
 `ParamArray`  
 İsteğe bağlı. Parametre listesi son parametresinde belirtilen veri türündeki öğeler isteğe bağlı bir dizi olduğunu belirtir. Bu yordama rastgele sayıda bağımsız değişken geçirme çağıran kodu sağlar.  
  
 `parametername`  
 Gerekli. Parametreyi temsil eden yerel değişkeninin adı.  
  
 `parametertype`  
 Gerekli olursa `Option Strict` olan `On`. Parametreyi temsil eden yerel değişken veri türü.  
  
 `defaultvalue`  
 İçin gerekli `Optional` parametreleri. Parametresinin veri türü değerlendiren herhangi sabit veya sabit bir ifade. Tür ise `Object`, ya da bir sınıf, arabirim, dizi veya yapısı, varsayılan değer yalnızca olabilir `Nothing`.  
  
## <a name="remarks"></a>Açıklamalar  
 Parametreleri ayraç içinde kullanılması ve virgülle ayrılmış. Bir parametre ile herhangi bir veri türü bildirilebilir. Belirtmezseniz, `parametertype`, onu varsayılan olarak `Object`.  
  
 Çağıran kodu yordamı çağırdığında geçirmeden bir *bağımsız değişkeni* her gerekli parametre için. Daha fazla bilgi için bkz: [arasındaki farklar parametreler ve bağımsız değişkenler](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).  
  
 Her bir parametreyi çağıran kodu geçirmeden bağımsız değişkeni, çağıran kodun temel bir öğe için bir işaretçidir. Bu öğe ise *nonvariable* (bir sabit değişmez değeri, numaralandırma veya ifadesi), bunu değiştirmek için herhangi bir kod için mümkün değildir. Eğer öyleyse bir *değişkeni* öğesi (bir bildirilen değişkeni, alan, özellik, dizi öğesi veya yapı öğesi), çağrıyı yapan kod bunu değiştirebilirsiniz. Daha fazla bilgi için bkz: [arasındaki farklar değiştirilebilir ve değiştirilemez bağımsız değişkenler](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).  
  
 Bir değişken öğesi aktarılırsa `ByRef`, yordamı da değiştirebilirsiniz. Daha fazla bilgi için bkz: [farklar arasında geçirme bir bağımsız değişken değer ve başvuru tarafından](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).  
  
## <a name="rules"></a>Kurallar  
  
-   **Parantez.** Parametre listesi belirtirseniz, parantez içine almanız gerekir. Hiçbir parametre varsa, boş bir liste kapsayan parantez kullanmaya devam edebilirsiniz. Bu öğe bir yordam olduğunu açıklığa kavuşturan tarafından kodunuzun okunabilirliğini artırır.  
  
-   **İsteğe bağlı parametreler.** Kullanırsanız `Optional` parametresi değiştiricisi, listedeki sonraki tüm parametreler isteğe bağlı olmalıdır ve kullanarak bildirilmesi `Optional` değiştiricisi.  
  
     Her isteğe bağlı parametre bildirimi sağlamalısınız `defaultvalue` yan tümcesi.  
  
     Daha fazla bilgi için bkz: [isteğe bağlı parametreler](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md).  
  
-   **Parametre dizileri.** Belirtmeniz gerekir `ByVal` için bir `ParamArray` parametresi.  
  
     Her ikisini birden kullanamazsınız `Optional` ve `ParamArray` aynı parametre listesinde.  
  
     Daha fazla bilgi için bkz: [parametre dizileri](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).  
  
-   **Geçirme mekanizması.** Her bağımsız değişkeni için varsayılan mekanizmasıdır `ByVal`, yordam başka bir deyişle, temel alınan değişken öğesini değiştiremezsiniz. Öğesi bir başvuru türü ise, değiştirir veya nesneyi yeniden olsa bile ancak yordamı içeriği veya temel alınan nesnenin üyelerine değiştirebilirsiniz.  
  
-   **Parametre adları.** Parametrenin veri türü bir dizi ise izleyin `parametername` parantez göre hemen. Parametre adları hakkında daha fazla bilgi için bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte gösterildiği bir `Function` iki parametreyi tanımlayan yordamı.  
  
 [!code-vb[VbVbalrStatements#2](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/parameter-list_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.InteropServices.DllImportAttribute>  
 [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Declare Deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [Structure Deyimi](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Option Strict Deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Öznitelikler genel bakış](../../../visual-basic/programming-guide/concepts/attributes/index.md)  
 [Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
