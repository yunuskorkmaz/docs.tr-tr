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
ms.openlocfilehash: 7162fcc24595bbb16d268d5d9e1ea4d82f6e67fb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61920542"
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
 Gerekli. Bir başvuru türü için değerlendirilen bir ifade.  
  
 `typename`  
 Gerekli. Tüm veri türü adı.  
  
## <a name="remarks"></a>Açıklamalar  
 `TypeOf` İşleci belirler çalışma zamanı türü olup olmadığını `objectexpression` uyumludur `typename`. Uyumluluk türü kategorisi bağlıdır `typename`. Aşağıdaki tabloda, uyumluluk nasıl belirlendiğini gösterir.  
  
|Tür kategorisi `typename`|Uyumluluk ölçütü|  
|---------------------------------|-----------------------------|  
|örneği|`objectexpression` tür `typename` veya devralır `typename`|  
|Yapı|`objectexpression` türü `typename`|  
|Arabirim|`objectexpression` uygulayan `typename` veya uygulayan bir sınıftan devraldığı `typename`|  
  
 Çalışma zamanı türü `objectexpression` uyumluluk ölçütü karşılayan `result` olduğu `True`. Aksi takdirde, `result` olduğu `False`.  Varsa `objectexpression` null ise `TypeOf`... `Is` döndürür `False`, ve... `IsNot` döndürür `True`.  
  
 `TypeOf` her zaman ile kullanılan `Is` oluşturmak için anahtar sözcüğü bir `TypeOf`... `Is` ifade veya `IsNot` oluşturmak için anahtar sözcüğü bir `TypeOf`... `IsNot` ifade.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `TypeOf`... `Is` ifadeler iki tür uyumluluğu test etmek için çeşitli veri türleri ile başvuru değişkenleri nesne.  
  
 [!code-vb[VbVbalrOperators#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#39)]  
  
 Değişken `refInteger` bir çalışma zamanı türü `Integer`. İle uyumlu `Integer` bilgisayardı `Double`. Değişken `refForm` bir çalışma zamanı türü <xref:System.Windows.Forms.Form>. İle uyumlu <xref:System.Windows.Forms.Form> ile kendi türü olduğu için <xref:System.Windows.Forms.Control> çünkü <xref:System.Windows.Forms.Form> devraldığı <xref:System.Windows.Forms.Control>ile <xref:System.ComponentModel.IComponent> çünkü <xref:System.Windows.Forms.Form> devralan <xref:System.ComponentModel.Component>, uygulayan<xref:System.ComponentModel.IComponent>. Ancak, `refForm` ile uyumlu olmayan <xref:System.Windows.Forms.Label>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Is İşleci](../../../visual-basic/language-reference/operators/is-operator.md)
- [IsNot İşleci](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Visual Basic'de Karşılaştırma işleçleri](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [İşleçler ve İfadeler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
