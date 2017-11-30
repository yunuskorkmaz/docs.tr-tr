---
title: "TypeOf İşleci (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 51bd2af7af28aa229fa62770c5b92d31e461333b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
  
|Türü kategorisi`typename`|Uyumluluk ölçütü|  
|---------------------------------|-----------------------------|  
|örneği|`objectexpression`tür `typename` veya devralır`typename`|  
|Yapı|`objectexpression`türü`typename`|  
|Arabirim|`objectexpression`uygulayan `typename` veya uygulayan bir sınıftan`typename`|  
  
 Çalışma zamanı türü `objectexpression` uyumluluk ölçütü karşılayan `result` olan `True`. Aksi takdirde, `result` olan `False`.  Varsa `objectexpression` null ise `TypeOf`... `Is` döndürür `False`, ve... `IsNot` döndürür `True`.  
  
 `TypeOf`her zaman kullanılması `Is` oluşturmak için anahtar sözcüğü bir `TypeOf`... `Is` ifadesi veya ile `IsNot` oluşturmak için anahtar sözcüğü bir `TypeOf`... `IsNot` ifade.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `TypeOf`... `Is` iki tür uyumluluğunu test etmek için ifadeleri nesne başvuru değişkenini çeşitli veri türlerine sahip.  
  
 [!code-vb[VbVbalrOperators#39](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/typeof-operator_1.vb)]  
  
 Değişkeni `refInteger` bir çalışma zamanı türü `Integer`. İle uyumlu `Integer` bilgisayardı `Double`. Değişkeni `refForm` bir çalışma zamanı türü <xref:System.Windows.Forms.Form>. İle uyumlu <xref:System.Windows.Forms.Form> , kendi türü ile olduğundan <xref:System.Windows.Forms.Control> çünkü <xref:System.Windows.Forms.Form> devraldığı <xref:System.Windows.Forms.Control>ile <xref:System.ComponentModel.IComponent> çünkü <xref:System.Windows.Forms.Form> devraldığı <xref:System.ComponentModel.Component>, uygulayan<xref:System.ComponentModel.IComponent>. Ancak, `refForm` ile uyumlu olmayan <xref:System.Windows.Forms.Label>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Is işleci](../../../visual-basic/language-reference/operators/is-operator.md)  
 [IsNot işleci](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [Visual Basic'de Karşılaştırma işleçleri](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [İşlevselliğe göre listelenmiş işleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [İşleçler ve ifadeler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
