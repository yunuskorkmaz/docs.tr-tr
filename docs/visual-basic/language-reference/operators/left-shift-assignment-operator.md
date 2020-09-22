---
title: <<= İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.<<=
helpviewer_keywords:
- operator <<=
- assignment statements [Visual Basic], compound
- <<= operator [Visual Basic]
- statements [Visual Basic], compound assignment
- operator<<=
- compound assignment statements [Visual Basic]
ms.assetid: 8ad26613-faff-4e2f-89ee-63feee33bfda
ms.openlocfilehash: 72fc842002586a4d5e48bc39b5c785fc6a9e9451
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866901"
---
# <a name="-operator-visual-basic"></a>\<\<= İşleci (Visual Basic)

Bir değişkenin veya özelliğin değerinde aritmetik sola kaydırma gerçekleştirir ve sonucu değişkenine veya özelliğe geri atar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
variableorproperty <<= amount  
```  
  
## <a name="parts"></a>Bölümler  

 `variableorproperty`  
 Gereklidir. İntegral türünün değişkeni veya özelliği ( `SByte` ,,, `Byte` `Short` `UShort` , `Integer` , `UInteger` , `Long` , veya `ULong` ).  
  
 `amount`  
 Gereklidir. Widens tarafından kullanılan bir veri türünün sayısal ifadesi `Integer` .  
  
## <a name="remarks"></a>Açıklamalar  

 İşlecinin sol tarafındaki öğesi `<<=` basit bir skaler değişken, bir özellik veya bir dizi öğesi olabilir. Değişken veya özellik [ReadOnly](../modifiers/readonly.md)olamaz.  
  
 `<<=`İşleci ilk olarak değişkenin veya özelliğin değerinde bir aritmetik sola kaydırma gerçekleştirir. İşleci daha sonra bu işlemin sonucunu bu değişkene veya özelliğe yeniden atar.  
  
 Aritmetik vardiyalar dairesel değildir, bu da sonucun bir sonunun dışına sürüklenen bitlerin diğer uçta yeniden tanıtılmadığını gösterir. Aritmetik sola kaydırma içinde, sonuç veri türü aralığının ötesinde kaydırılan bitler atılır ve sağdaki bit konumları sıfır olarak ayarlanır.  
  
## <a name="overloading"></a>Aşırı Yükleme  

 [<< işleci](left-shift-operator.md) *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. İşleci aşırı yüklemek `<<` işlecin davranışını etkiler `<<=` . Kodunuzun `<<=` bir sınıf veya yapı üzerinde kullanması durumunda `<<` , yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `<<=` bir değişkenin bit modelini `Integer` belirtilen miktarda sola kaydırmak ve sonucu değişkenine atamak için işlecini kullanır.  
  
 [!code-vb[VbVbalrOperators#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#13)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [<< Işleci](left-shift-operator.md)
- [Atama Işleçleri](assignment-operators.md)
- [Bit Kaydırma İşleçleri](bit-shift-operators.md)
- [Visual Basic'de İşleç Önceliği](operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](operators-listed-by-functionality.md)
- [Deyimler](../../programming-guide/language-features/statements.md)
