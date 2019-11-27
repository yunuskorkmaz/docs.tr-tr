---
title: TypeOf İşleci
ms.date: 07/20/2015
f1_keywords:
- TypeOf
- vb.TypeOf
helpviewer_keywords:
- types [Visual Basic], compatible
- comparison operators [Visual Basic]
- TypeOf...Is expression
- data types [Visual Basic], compatible
- TypeOf operator [Visual Basic]
- compatible data types [Visual Basic]
ms.assetid: 33f65296-659a-4b9a-9a29-c2a91cff68b2
ms.openlocfilehash: 22af5b8f8488ca44e388596530decd52e33525dc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350887"
---
# <a name="typeof-operator-visual-basic"></a>TypeOf İşleci (Visual Basic)
Bir ifadenin sonucunun çalışma zamanı türünün belirtilen türle tür uyumlu olup olmadığını denetler.
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
result = TypeOf objectexpression Is typename  
```  
  
```vb  
result = TypeOf objectexpression IsNot typename  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Döndürüldüğünde. Bir `Boolean` değeri.  
  
 `objectexpression`  
 Gerekli. Bir başvuru türü değerlendirilen herhangi bir ifade.  
  
 `typename`  
 Gerekli. Herhangi bir veri türü adı.  
  
## <a name="remarks"></a>Açıklamalar  
 `TypeOf` işleci, `objectexpression` çalışma zamanı türünün `typename`uyumlu olup olmadığını belirler. Uyumluluk `typename`türü kategorisine bağlıdır. Aşağıdaki tabloda uyumluluğun nasıl belirlendiği gösterilmektedir.  
  
|`typename` kategorisi türü|Uyumluluk ölçütü|  
|---------------------------------|-----------------------------|  
|Sınıf|`objectexpression` `typename` veya `typename` devralınıyor|  
|Yapı|`objectexpression` türü `typename`|  
|Arabirim|`objectexpression`, `typename` uygular veya `typename` uygulayan bir sınıftan devralır|  
  
 `objectexpression` çalışma zamanı türü uyumluluk ölçütünü karşılıyorsa `result` `True`. Aksi takdirde, `result` `False`.  `objectexpression` null ise, `TypeOf`...`Is` `False`döndürür ve...`IsNot` `True`döndürür.  
  
 `TypeOf` her zaman bir `TypeOf`...`Is` ifadesi oluşturmak için `Is` anahtar sözcüğüyle veya `IsNot`... `TypeOf`ifadesi oluşturmak için`IsNot` anahtar sözcüğüyle birlikte kullanılır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, çeşitli veri türleriyle iki nesne başvuru değişkenlerinin tür uyumluluğunu test etmek için `TypeOf`...`Is` ifadelerini kullanır.  
  
 [!code-vb[VbVbalrOperators#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#39)]  
  
 `refInteger` değişken `Integer`çalışma zamanı türüne sahiptir. `Integer` ile uyumludur, ancak `Double`değildir. `refForm` değişken <xref:System.Windows.Forms.Form>çalışma zamanı türüne sahiptir. <xref:System.Windows.Forms.Form> ile uyumludur çünkü bu, <xref:System.Windows.Forms.Form> <xref:System.Windows.Forms.Control>devraldığından ve <xref:System.ComponentModel.IComponent> <xref:System.Windows.Forms.Form> uygulayan <xref:System.ComponentModel.Component>devraldığından <xref:System.ComponentModel.IComponent>ile <xref:System.Windows.Forms.Control>. Ancak, `refForm` <xref:System.Windows.Forms.Label>uyumlu değildir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Is İşleci](../../../visual-basic/language-reference/operators/is-operator.md)
- [IsNot İşleci](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Visual Basic karşılaştırma Işleçleri](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [İşleçler ve İfadeler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
