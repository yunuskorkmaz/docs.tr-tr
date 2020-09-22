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
ms.openlocfilehash: 0a01b49cf1e0bf9ad7b2ce541cee39cba83025ca
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875301"
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
 Döndürüldüğünde. Bir `Boolean` değer.  
  
 `objectexpression`  
 Gereklidir. Bir başvuru türü değerlendirilen herhangi bir ifade.  
  
 `typename`  
 Gereklidir. Herhangi bir veri türü adı.  
  
## <a name="remarks"></a>Açıklamalar  

 `TypeOf`İşleci, çalışma zamanı türünün ile uyumlu olup olmadığını belirler `objectexpression` `typename` . Uyumluluk, öğesinin tür kategorisine bağlıdır `typename` . Aşağıdaki tabloda uyumluluğun nasıl belirlendiği gösterilmektedir.  
  
|Tür kategorisi `typename`|Uyumluluk ölçütü|  
|---------------------------------|-----------------------------|  
|Sınıf|`objectexpression` tür `typename` veya devralınıyor `typename`|  
|Yapı|`objectexpression` tür `typename`|  
|Arabirim|`objectexpression``typename`uygulayan bir sınıftan uygular veya devralır`typename`|  
  
 Çalışma zamanı türü `objectexpression` Uyumluluk ölçütünü karşılıyorsa,, `result` olur `True` . Aksi halde `result` , `False` .  `objectexpression`Null ise... `TypeOf` `Is` döndürüyor `False` , ve... `IsNot` döndürüyor `True` .  
  
 `TypeOf` her zaman `Is` bir... ifadesi oluşturmak için `TypeOf` `Is` veya bir... `IsNot` ifadesi oluşturmak için anahtar `TypeOf` `IsNot` sözcüğüyle birlikte kullanılır.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `TypeOf` `Is` çeşitli veri türleriyle iki nesne başvuru değişkenlerinin tür uyumluluğunu test etmek için... ifadelerini kullanır.  
  
 [!code-vb[VbVbalrOperators#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#39)]  
  
 Değişkeninin `refInteger` çalışma zamanı türü vardır `Integer` . İle uyumludur `Integer` ancak ile uyumlu değildir `Double` . Değişkeninin `refForm` çalışma zamanı türü vardır <xref:System.Windows.Forms.Form> . İle uyumludur çünkü bu, ' <xref:System.Windows.Forms.Form> <xref:System.Windows.Forms.Control> <xref:System.Windows.Forms.Form> den devraldığından <xref:System.Windows.Forms.Control> ve ' <xref:System.ComponentModel.IComponent> <xref:System.Windows.Forms.Form> <xref:System.ComponentModel.Component> den devraldığından, ' den ' dır <xref:System.ComponentModel.IComponent> . Ancak, `refForm` ile uyumlu değildir <xref:System.Windows.Forms.Label> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Is İşleci](is-operator.md)
- [IsNot İşleci](isnot-operator.md)
- [Visual Basic'de Karşılaştırma İşleçleri](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Visual Basic'de İşleç Önceliği](operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](operators-listed-by-functionality.md)
- [İşleçler ve Ifadeler](../../programming-guide/language-features/operators-and-expressions/index.md)
