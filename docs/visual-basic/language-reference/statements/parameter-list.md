---
title: Parametre Listesi
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
ms.openlocfilehash: ec4ce0f12b540478d889832fb18f1ef008613f1f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346477"
---
# <a name="parameter-list-visual-basic"></a>Parametre Listesi (Visual Basic)

Bir yordamın çağrıldığında beklediği parametreleri belirtir. Birden çok parametre virgülle ayrılır. Bir parametre için sözdizimi aşağıda verilmiştir.

## <a name="syntax"></a>Sözdizimi

```vb
[ <attributelist> ] [ Optional ] [{ ByVal | ByRef }] [ ParamArray ]
parametername[( )] [ As parametertype ] [ = defaultvalue ]
```

## <a name="parts"></a>Bölümler

`attributelist`  
İsteğe bağlı. Bu parametre için uygulanan özniteliklerin listesi. [Öznitelik listesini](../../../visual-basic/language-reference/statements/attribute-list.md) açılı ayraç içine almalısınız ("`<`" ve "`>`").

`Optional`  
İsteğe bağlı. Yordam çağrıldığında bu parametrenin gerekli değildir olduğunu belirtir.

`ByVal`  
İsteğe bağlı. Yordamın, çağıran koddaki karşılık gelen bağımsız değişkeni temel alan değişken öğesini değiştirmez veya yeniden atayacağınızı belirtir.

`ByRef`  
İsteğe bağlı. Yordamın, çağıran koddaki temeldeki değişken öğesini çağıran kodun kendisi ile aynı şekilde değiştirebileceğini belirtir.

`ParamArray`  
İsteğe bağlı. Parametre listesindeki son parametrenin, belirtilen veri türü için isteğe bağlı bir öğe dizisi olduğunu belirtir. Bu, çağıran kodun yordama rastgele sayıda bağımsız değişken geçirmelerini sağlar.

`parametername`  
Gerekli. Parametreyi temsil eden yerel değişkenin adı.

`parametertype`  
`Option Strict` `On`olması gerekir. Parametreyi temsil eden yerel değişkenin veri türü.

`defaultvalue`  
`Optional` parametreleri için gereklidir. Parametrenin veri türünü değerlendiren herhangi bir sabit veya sabit ifade. Tür `Object`, ya da bir sınıf, arabirim, dizi ya da yapı ise, varsayılan değer yalnızca `Nothing`olabilir.

## <a name="remarks"></a>Açıklamalar

Parametreler parantezler ile çevrelenmiş ve virgülle ayrılmalıdır. Bir parametre herhangi bir veri türü ile bildirilebilecek. `parametertype`belirtmezseniz, varsayılan olarak `Object`.

Çağıran kod yordamı çağırdığında, gerekli her parametreye bir *bağımsız değişken* geçirir. Daha fazla bilgi için bkz. [Parametreler ve bağımsız değişkenler arasındaki farklar](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).

Çağıran kodun her parametreye geçtiği bağımsız değişken, çağıran koddaki temeldeki öğenin bir işaretçisidir. Bu öğe *değişken olmayan* bir değerse (bir sabit, değişmez değer, sabit listesi veya ifade), herhangi bir kodun değiştirilmesi olanaksızdır. *Değişken* bir öğe ise (belirtilen değişken, alan, özellik, dizi öğesi veya yapı öğesi), çağıran kod değiştirebilir. Daha fazla bilgi için bkz. [değiştirilebilir ve değiştirilemez bağımsız değişkenler arasındaki farklar](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).

Bir değişken öğesi `ByRef`geçirildiğinde yordam de değiştirebilir. Daha fazla bilgi için, [bir bağımsız değişkeni değere ve başvuruya göre geçirme arasındaki farklılıklar](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md)bölümüne bakın.

## <a name="rules"></a>Kurallar

- **Ayraçlar.** Bir parametre listesi belirtirseniz, parantez içine almanız gerekir. Parametre yoksa boş bir listeyi kapsayan ayraçları kullanmaya devam edebilirsiniz. Bunun yapılması, öğenin bir yordam olduğunu açıklığa kavuşturarak kodunuzun okunabilirliğini geliştirir.

- **İsteğe bağlı parametreler.** Bir parametre üzerinde `Optional` değiştiricisini kullanırsanız, listedeki sonraki tüm parametrelerin da isteğe bağlı olması ve `Optional` değiştiricisi kullanılarak bildirilmelidir.

     Her isteğe bağlı parametre bildirimi `defaultvalue` yan tümcesini sağlamalıdır.

     Daha fazla bilgi için bkz. [Isteğe bağlı parametreler](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md).

- **Parametre dizileri.** Bir `ParamArray` parametresi için `ByVal` belirtmeniz gerekir.

     Aynı parametre listesinde hem `Optional` hem de `ParamArray` kullanamazsınız.

     Daha fazla bilgi için bkz. [parametre dizileri](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).

- **Geçirme mekanizması.** Her bağımsız değişken için varsayılan mekanizma `ByVal`, bu da yordamın temeldeki değişken öğesini değiştiremeyeceği anlamına gelir. Ancak, öğe bir başvuru türü ise, yordam nesnenin kendisini değiştiremese veya yeniden atanmasa bile, temel nesnenin içeriğini veya üyelerini değiştirebilir.

- **Parametre adları.** Parametrenin veri türü bir diziyse, ayraçları hemen `parametername` izleyin. Parametre adları hakkında daha fazla bilgi için bkz. [bildirilmemiş öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, iki parametre tanımlayan bir `Function` yordamını gösterir.

[!code-vb[VbVbalrStatements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#2)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Declare Deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Structure Deyimi](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Option Strict Deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Özniteliklere genel bakış](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
