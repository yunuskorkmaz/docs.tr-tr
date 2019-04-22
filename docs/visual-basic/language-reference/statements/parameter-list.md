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
ms.openlocfilehash: 651f08812032aa1c5aacc04fdb3d7f491f12b607
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58836291"
---
# <a name="parameter-list-visual-basic"></a>Parametre Listesi (Visual Basic)
Bir yordam çağrıldığında bu bekliyor parametreleri belirtir. Birden çok parametre, virgüllerle ayrılır. Bir parametre için sözdizimi aşağıdadır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
[ <attributelist> ] [ Optional ] [{ ByVal | ByRef }] [ ParamArray ]   
parametername[( )] [ As parametertype ] [ = defaultvalue ]  
```  
  
## <a name="parts"></a>Bölümler  
 `attributelist`  
 İsteğe bağlı. Bu parametre için geçerli olan özniteliklerin listesi. İçine almalısınız [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md) açılı ayraçlar içinde ("`<`"ve"`>`").  
  
 `Optional`  
 İsteğe bağlı. Yordam çağrıldığında Bu parametre gerekli olmadığını belirtir.  
  
 `ByVal`  
 İsteğe bağlı. Yordam olamaz değiştirin veya karşılık gelen bağımsız değişkenin çağıran koddaki temel değişken öğe yeniden atama belirtir.  
  
 `ByRef`  
 İsteğe bağlı. Yordam aynı şekilde çağıran kod çağıran koddaki değişken öğe türüdür değiştirebilirsiniz belirtir.  
  
 `ParamArray`  
 İsteğe bağlı. Belirtilen veri türü öğeler için isteğe bağlı bir dizi parametre listesindeki son parametre olduğunu belirtir. Bu yordama bağımsız değişkenler rastgele bir sayıdan geçirmek çağıran kod sağlar.  
  
 `parametername`  
 Gerekli. Parametreyi temsil eden yerel değişkenin adı.  
  
 `parametertype`  
 Gerekli if `Option Strict` olduğu `On`. Parametreyi temsil eden yerel değişken veri türü.  
  
 `defaultvalue`  
 Gerekli `Optional` parametreleri. Parametrenin veri türü için değerlendirilen tüm sabit veya sabit ifade. Tür ise `Object`, veya bir sınıf, arabirim, dizi veya yapı, varsayılan değer yalnızca olabilir `Nothing`.  
  
## <a name="remarks"></a>Açıklamalar  
 Parametreleri parantez içine ve virgülle ayrılmış. Bir parametre herhangi bir veri türü ile bildirilebilir. Siz belirtmezseniz `parametertype`, varsayılan `Object`.  
  
 Çağıran kod yordamı çağırdığında arabimini bir *bağımsız değişken* her gerekli parametre. Daha fazla bilgi için [arasındaki farklar parametreler ve bağımsız değişkenler](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).  
  
 Çağıran kod her parametreye geçirmeden bağımsız değişken temel alınan bir öğe çağıran koddaki bir işaretçisidir. Bu öğe ise *nonvariable* (bir sabit, değişmez değeri, numaralandırma veya ifade), değiştirmek herhangi bir kod için mümkün değildir. Eğer öyleyse bir *değişkeni* öğesi (bir bildirilmiş bir değişken, alan, özelliği, dizi öğesi veya yapı öğesi), çağıran kodun bunu değiştirebilirsiniz. Daha fazla bilgi için [arasındaki farklar değiştirilebilir ve değiştirilemez bağımsız değişkenler](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).  
  
 Bir değişken öğesi iletilmezse `ByRef`, yordam de değiştirebilirsiniz. Daha fazla bilgi için [farklar arasında geçen bir bağımsız değişken değer ve başvuru tarafından](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).  
  
## <a name="rules"></a>Kurallar  
  
-   **Parantezler.** Parametre listesi belirtirseniz, parantez içine almalısınız. Hiçbir parametre varsa, boş bir liste çevreleyen parantezler kullanmaya devam edebilirsiniz. Bu öğe bir yordam olduğunu açıklığa kavuşturan tarafından kodunuzun okunabilirliği geliştirir.  
  
-   **İsteğe bağlı parametreler.** Kullanırsanız `Optional` bir parametre değiştiricisi, sonraki tüm parametreler listesinde isteğe bağlı olmalıdır ve kullanılarak bildirilen `Optional` değiştiricisi.  
  
     Her isteğe bağlı parametre bildirimi sağlamalısınız `defaultvalue` yan tümcesi.  
  
     Daha fazla bilgi için [isteğe bağlı parametreler](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md).  
  
-   **Parametre dizileri.** Belirtmelisiniz `ByVal` için bir `ParamArray` parametresi.  
  
     Her ikisini birden kullanamazsınız `Optional` ve `ParamArray` aynı parametre listesinde.  
  
     Daha fazla bilgi için [parametre dizileri](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).  
  
-   **Geçirme mekanizması.** Her bağımsız değişken için varsayılan mekanizmasıdır `ByVal`, yordam başka bir deyişle, temel alınan değişken öğesini değiştiremezsiniz. Öğeye bir başvuru türü ise, değiştirin veya nesneyi yeniden atama olsa bile ancak yordamı içeriği veya temel alınan bir nesnenin üyelerine değiştirebilirsiniz.  
  
-   **Parametre adları.** Parametrenin veri türü bir dizi ise izleyin `parametername` parantez tarafından hemen. Parametre adları hakkında daha fazla bilgi için bkz. [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte gösterildiği bir `Function` iki parametre tanımlayan yordamı.  
  
 [!code-vb[VbVbalrStatements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Declare Deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Structure Deyimi](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Option Strict Deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Öznitelikler genel bakış](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
