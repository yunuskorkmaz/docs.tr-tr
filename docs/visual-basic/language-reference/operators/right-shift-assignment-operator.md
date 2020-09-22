---
title: '>>= İşleci'
ms.date: 07/20/2015
f1_keywords:
- vb.>>=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator >>= [Visual Basic]
- compound assignment statements [Visual Basic]
- '>>= operator [Visual Basic]'
ms.assetid: 2bcd9abb-7a8c-4229-b75d-8816ff1dc700
ms.openlocfilehash: a1c2331791644155504183d3cf5767470a3bf17b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873358"
---
# <a name="-operator-visual-basic"></a>>>= Işleci (Visual Basic)

Bir değişkenin veya özelliğin değerinde aritmetik sağa kaydırma gerçekleştirir ve sonucu değişkenine veya özelliğe geri atar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a>Bölümler  

 `variableorproperty`  
 Gereklidir. İntegral türünün değişkeni veya özelliği ( `SByte` ,,, `Byte` `Short` `UShort` , `Integer` , `UInteger` , `Long` , veya `ULong` ).  
  
 `amount`  
 Gereklidir. Widens tarafından kullanılan bir veri türünün sayısal ifadesi `Integer` .  
  
## <a name="remarks"></a>Açıklamalar  

 İşlecinin sol tarafındaki öğesi `>>=` basit bir skaler değişken, bir özellik veya bir dizi öğesi olabilir. Değişken veya özellik [ReadOnly](../modifiers/readonly.md)olamaz.  
  
 `>>=`İşleci ilk olarak değişkenin veya özelliğin değerinde bir aritmetik sağa kaydırma gerçekleştirir. İşleci daha sonra bu işlemin sonucunu değişkenine veya özelliğe geri atar.  
  
 Aritmetik vardiyalar dairesel değildir, bu da sonucun bir sonunun dışına sürüklenen bitlerin diğer uçta yeniden tanıtılmadığını gösterir. Aritmetik sağa kaydırma ' de, en sağdaki bit konumlarından daha fazla kaydırılan bitler atılır ve en soldaki bit, sol taraftaki bit konumlarına yayılır. Yani `variableorproperty` negatif bir değer varsa, karıştırılmış konumlar bir olarak ayarlanır. `variableorproperty`Pozitif ise veya veri türü işaretsiz bir tür ise, karıştırılmış konumlar sıfır olarak ayarlanır.  
  
## <a name="overloading"></a>Aşırı Yükleme  

 [>> işleci](right-shift-operator.md) *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. İşleci aşırı yüklemek `>>` işlecin davranışını etkiler `>>=` . Kodunuzun `>>=` bir sınıf veya yapı üzerinde kullanması durumunda `>>` , yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `>>=` bir değişkenin bit modelini `Integer` belirtilen miktarda sağa kaydırmak ve sonucu değişkenine atamak için işlecini kullanır.  
  
 [!code-vb[VbVbalrOperators#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [>> Işleci](right-shift-operator.md)
- [Atama Işleçleri](assignment-operators.md)
- [Bit Kaydırma İşleçleri](bit-shift-operators.md)
- [Visual Basic'de İşleç Önceliği](operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](operators-listed-by-functionality.md)
- [Deyimler](../../programming-guide/language-features/statements.md)
