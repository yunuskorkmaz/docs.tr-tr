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
ms.openlocfilehash: 706fc2414806db5608cce410bf4156839ec2d83e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404323"
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
İsteğe bağlı. Bu parametre için uygulanan özniteliklerin listesi. [Öznitelik listesini](attribute-list.md) açılı ayraçlar (" `<` " ve " `>` ") içine almalısınız.

`Optional`  
İsteğe bağlı. Yordam çağrıldığında bu parametrenin gerekli değildir olduğunu belirtir.

`ByVal`  
İsteğe bağlı. Yordamın, çağıran koddaki karşılık gelen bağımsız değişkeni temel alan değişken öğesini değiştirmez veya yeniden atayacağınızı belirtir.

`ByRef`  
İsteğe bağlı. Yordamın, çağıran koddaki temeldeki değişken öğesini çağıran kodun kendisi ile aynı şekilde değiştirebileceğini belirtir.

`ParamArray`  
İsteğe bağlı. Parametre listesindeki son parametrenin, belirtilen veri türü için isteğe bağlı bir öğe dizisi olduğunu belirtir. Bu, çağıran kodun yordama rastgele sayıda bağımsız değişken geçirmelerini sağlar.

`parametername`  
Gereklidir. Parametreyi temsil eden yerel değişkenin adı.

`parametertype`  
İse gereklidir `Option Strict` `On` . Parametreyi temsil eden yerel değişkenin veri türü.

`defaultvalue`  
Parametreler için gereklidir `Optional` . Parametrenin veri türünü değerlendiren herhangi bir sabit veya sabit ifade. Tür `Object` veya bir sınıf, arabirim, dizi ya da yapı ise, varsayılan değer yalnızca olabilir `Nothing` .

## <a name="remarks"></a>Açıklamalar

Parametreler parantezler ile çevrelenmiş ve virgülle ayrılmalıdır. Bir parametre herhangi bir veri türü ile bildirilebilecek. Belirtmezseniz `parametertype` , varsayılan olarak olur `Object` .

Çağıran kod yordamı çağırdığında, gerekli her parametreye bir *bağımsız değişken* geçirir. Daha fazla bilgi için bkz. [Parametreler ve bağımsız değişkenler arasındaki farklar](../../programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).

Çağıran kodun her parametreye geçtiği bağımsız değişken, çağıran koddaki temeldeki öğenin bir işaretçisidir. Bu öğe *değişken olmayan* bir değerse (bir sabit, değişmez değer, sabit listesi veya ifade), herhangi bir kodun değiştirilmesi olanaksızdır. *Değişken* bir öğe ise (belirtilen değişken, alan, özellik, dizi öğesi veya yapı öğesi), çağıran kod değiştirebilir. Daha fazla bilgi için bkz. [değiştirilebilir ve değiştirilemez bağımsız değişkenler arasındaki farklar](../../programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).

Bir değişken öğesi geçmişse `ByRef` , yordam de değiştirebilir. Daha fazla bilgi için, [bir bağımsız değişkeni değere ve başvuruya göre geçirme arasındaki farklılıklar](../../programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md)bölümüne bakın.

## <a name="rules"></a>Kurallar

- **Ayraçlar.** Bir parametre listesi belirtirseniz, parantez içine almanız gerekir. Parametre yoksa boş bir listeyi kapsayan ayraçları kullanmaya devam edebilirsiniz. Bunun yapılması, öğenin bir yordam olduğunu açıklığa kavuşturarak kodunuzun okunabilirliğini geliştirir.

- **İsteğe bağlı parametreler.** `Optional`Değiştirici bir parametre üzerinde kullanırsanız, listedeki izleyen tüm parametrelerin da isteğe bağlı olması ve değiştirici kullanılarak bildirilenler gerekir `Optional` .

     Her isteğe bağlı parametre bildirimi `defaultvalue` yan tümceyi sağlamalıdır.

     Daha fazla bilgi için bkz. [Isteğe bağlı parametreler](../../programming-guide/language-features/procedures/optional-parameters.md).

- **Parametre dizileri.** `ByVal`Bir parametre için belirtmeniz gerekir `ParamArray` .

     Hem hem de `Optional` `ParamArray` aynı parametre listesinde kullanamazsınız.

     Daha fazla bilgi için bkz. [parametre dizileri](../../programming-guide/language-features/procedures/parameter-arrays.md).

- **Geçirme mekanizması.** Her bağımsız değişken için varsayılan mekanizma, `ByVal` Bu yordamın temel alınan değişken öğesini değiştiremeyeceği anlamına gelir. Ancak, öğe bir başvuru türü ise, yordam nesnenin kendisini değiştiremese veya yeniden atanmasa bile, temel nesnenin içeriğini veya üyelerini değiştirebilir.

- **Parametre adları.** Parametrenin veri türü bir diziyse, `parametername` hemen parantez ile izleyin. Parametre adları hakkında daha fazla bilgi için bkz. [bildirilmemiş öğe adları](../../programming-guide/language-features/declared-elements/declared-element-names.md).

## <a name="example"></a>Örnek

Aşağıdaki örnekte `Function` iki parametre tanımlayan bir yordam gösterilmektedir.

[!code-vb[VbVbalrStatements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#2)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [Function Deyimi](function-statement.md)
- [Sub Deyimi](sub-statement.md)
- [Declare Deyimi](declare-statement.md)
- [Structure Yapısı](structure-statement.md)
- [Option Strict Deyimi](option-strict-statement.md)
- [Özniteliklere genel bakış](../../programming-guide/concepts/attributes/index.md)
- [Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
