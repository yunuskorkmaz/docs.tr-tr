---
title: TypeOf İşleci (Visual Basic)
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
ms.openlocfilehash: c6028f524a16b836310f0c8d564205244515cdc9
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701293"
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
 Döndürüldüğünde. @No__t-0 değeri.  
  
 `objectexpression`  
 Gerekli. Bir başvuru türü değerlendirilen herhangi bir ifade.  
  
 `typename`  
 Gerekli. Herhangi bir veri türü adı.  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t-0 işleci, `objectexpression` ' in çalışma zamanı türünün `typename` ile uyumlu olup olmadığını belirler. Uyumluluk `typename` ' ın tür kategorisine bağlıdır. Aşağıdaki tabloda uyumluluğun nasıl belirlendiği gösterilmektedir.  
  
|@No__t kategori türü-0|Uyumluluk ölçütü|  
|---------------------------------|-----------------------------|  
|örneği|`objectexpression` `typename` türündedir veya `typename` ' den devralır|  
|Yapı|`objectexpression` `typename` türündedir|  
|Arabirim|`objectexpression` ' i @no__t uygular veya `typename` uygulayan bir sınıftan devralır|  
  
 @No__t-0 ' ın çalışma zamanı türü uyumluluk ölçütünü karşılıyorsa, `result` `True` ' dir. Aksi takdirde, `result` `False` ' dir.  @No__t-0 null ise, `TypeOf`... `Is` `False` ve... `IsNot` döndürür `True` döndürür.  
  
 `TypeOf`, her zaman bir `TypeOf`... `IsNot` ifadesi oluşturmak için `Is` anahtar sözcüğüyle birlikte `TypeOf`... `Is` ifadesi veya `IsNot` anahtar sözcüğüyle birlikte kullanılır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, çeşitli veri türleriyle iki nesne başvuru değişkenlerinin tür uyumluluğunu test etmek için `TypeOf`... `Is` ifadelerini kullanır.  
  
 [!code-vb[VbVbalrOperators#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#39)]  
  
 @No__t-0 değişkeninin çalışma zamanı türü `Integer`. @No__t-0 ile uyumludur ancak `Double` ' i içermez. @No__t-0 değişkeninin çalışma zamanı türü <xref:System.Windows.Forms.Form>. @No__t-@no__t 2 ' yi uygulayan <xref:System.Windows.Forms.Form> ' ten devraldığı için, <xref:System.Windows.Forms.Form> ' dır, çünkü onun türü <xref:System.Windows.Forms.Control> ve <xref:System.ComponentModel.IComponent> ile @no__t. Ancak, `refForm` <xref:System.Windows.Forms.Label> ile uyumlu değildir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Is İşleci](../../../visual-basic/language-reference/operators/is-operator.md)
- [IsNot İşleci](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Visual Basic karşılaştırma Işleçleri](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [İşleçler ve İfadeler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
