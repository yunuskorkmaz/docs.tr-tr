---
title: '##Const yönergesi (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.#Const
- '#vb.Const'
- '#Const'
helpviewer_keywords:
- '#Const directive'
- conditional compilation [Visual Basic], directives
- Const directive (#Const)
- Visual Basic compiler, compiler directives
- constants [Visual Basic], Const directive
- constants [Visual Basic], declaring
- Const statement [Visual Basic], directive (#Const)
- 'declaring constants [Visual Basic], #const directive'
ms.assetid: 707669e5-23f9-4f17-8622-a0d534429386
ms.openlocfilehash: 7e855f76a0fa8e6c06fd557a944c518641415f09
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710605"
---
# <a name="const-directive"></a>#Const Yönergesi
Visual Basic için koşullu derleyici sabitlerini tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
#Const constname = expression  
```  
  
## <a name="parts"></a>Bölümler  
 `constname`  
 Gerekli. Tanımlanan sabitin adı.  
  
 `expression`  
 Gerekli. Değişmez değeri, diğer koşullu derleyici sabiti ya da içeren tüm aritmetik veya mantıksal işleçleri dışında herhangi bir birleşimini `Is`.  
  
## <a name="remarks"></a>Açıklamalar  
 Koşullu derleyici sabitleri, göründükleri dosyaya her zaman özeldir. Genel derleyici sabitlerini kullanarak oluşturulamıyor `#Const` yönergesi; oluşturup bunları yalnızca kullanıcı arabirimi veya ile `/define` derleyici seçeneği.  
  
 Yalnızca koşullu derleyici sabitlerini ve sabit değerlerde kullanabileceğiniz `expression`. İle tanımlanan bir standart sabit kullanarak `Const` bir hataya neden olur. Buna karşılık, tanımlı sabitler kullanabileceğiniz `#Const` koşullu derleme için yalnızca anahtar sözcüğü. Sabitler de tanımlanmamışsa, bu durumda bunlar değerine sahip `Nothing`.  
  
## <a name="example"></a>Örnek  
 Bu örnekte `#Const` yönergesi.  
  
 [!code-vb[VbVbalrConditionalComp#3](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/const-directive_1.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [/ define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
- [#If...Then...#Else Yönergesi](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [Const Deyimi](../../../visual-basic/language-reference/statements/const-statement.md)
- [Koşullu Derleme](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [If...Then...Else Deyimi](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
