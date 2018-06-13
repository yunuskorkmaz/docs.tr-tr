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
ms.openlocfilehash: fe287794423048e993d953c83fc8590a06b7a5e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604061"
---
# <a name="typeof-operator-visual-basic"></a>TypeOf İşleci (Visual Basic)
Bir veri türü için bir nesne başvuru değişkenini karşılaştırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
result = TypeOf objectexpression Is typename  
```  
  
```  
result = TypeOf objectexpression IsNot typename  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Döndürdü. A `Boolean` değeri.  
  
 `objectexpression`  
 Gerekli. Bir başvuru türü değerlendirir herhangi bir ifade.  
  
 `typename`  
 Gerekli. Tüm veri türü adı.  
  
## <a name="remarks"></a>Açıklamalar  
 `TypeOf` İşleci belirler çalışma zamanı türü olup olmadığını `objectexpression` ile uyumlu `typename`. Uyumluluk ve türü kategorisine göre değişir `typename`. Aşağıdaki tabloda, uyumluluk nasıl belirlendiğini gösterir.  
  
|Türü kategorisi `typename`|Uyumluluk ölçütü|  
|---------------------------------|-----------------------------|  
|örneği|`objectexpression` tür `typename` veya devralır `typename`|  
|Yapı|`objectexpression` türü `typename`|  
|Arabirim|`objectexpression` uygulayan `typename` veya uygulayan bir sınıftan `typename`|  
  
 Çalışma zamanı türü `objectexpression` uyumluluk ölçütü karşılayan `result` olan `True`. Aksi takdirde, `result` olan `False`.  Varsa `objectexpression` null ise `TypeOf`... `Is` döndürür `False`, ve... `IsNot` döndürür `True`.  
  
 `TypeOf` her zaman kullanılması `Is` oluşturmak için anahtar sözcüğü bir `TypeOf`... `Is` ifadesi veya ile `IsNot` oluşturmak için anahtar sözcüğü bir `TypeOf`... `IsNot` ifade.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `TypeOf`... `Is` iki tür uyumluluğunu test etmek için ifadeleri nesne başvuru değişkenini çeşitli veri türlerine sahip.  
  
 [!code-vb[VbVbalrOperators#39](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/typeof-operator_1.vb)]  
  
 Değişkeni `refInteger` bir çalışma zamanı türü `Integer`. İle uyumlu `Integer` bilgisayardı `Double`. Değişkeni `refForm` bir çalışma zamanı türü <xref:System.Windows.Forms.Form>. İle uyumlu <xref:System.Windows.Forms.Form> , kendi türü ile olduğundan <xref:System.Windows.Forms.Control> çünkü <xref:System.Windows.Forms.Form> devraldığı <xref:System.Windows.Forms.Control>ile <xref:System.ComponentModel.IComponent> çünkü <xref:System.Windows.Forms.Form> devraldığı <xref:System.ComponentModel.Component>, uygulayan<xref:System.ComponentModel.IComponent>. Ancak, `refForm` ile uyumlu olmayan <xref:System.Windows.Forms.Label>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Is İşleci](../../../visual-basic/language-reference/operators/is-operator.md)  
 [IsNot İşleci](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [Visual Basic'de Karşılaştırma işleçleri](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [İşleçler ve İfadeler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
