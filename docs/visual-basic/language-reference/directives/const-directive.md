---
title: '#Const Yönergesi'
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
ms.openlocfilehash: 278219edb1bb5d1c0bb015611d69cbe4ae70014b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343840"
---
# <a name="const-directive"></a>#Const Yönergesi

Visual Basic için koşullu derleyici sabitleri tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
#Const constname = expression  
```  
  
## <a name="parts"></a>Bölümler  

 `constname`  
 Gerekli. Tanımlanmakta olan sabitin adı.  
  
 `expression`  
 Gerekli. Değişmez değer, diğer koşullu derleyici sabiti veya `Is`dışında herhangi bir ya da tüm aritmetik veya mantıksal işleçleri içeren herhangi bir bileşim.  
  
## <a name="remarks"></a>Açıklamalar  

 Koşullu derleyici sabitleri, her zaman göründükleri dosya için özeldir. `#Const` yönergesini kullanarak ortak derleyici sabitleri oluşturamazsınız; Onları yalnızca Kullanıcı arabiriminde veya `/define` derleyici seçeneğiyle oluşturabilirsiniz.  
  
 `expression`yalnızca koşullu derleyici sabitlerini ve sabit değerlerini kullanabilirsiniz. `Const` ile tanımlanmış standart bir sabit kullanmak hataya neden olur. Buna karşılık, yalnızca koşullu derleme için `#Const` anahtar sözcüğüyle tanımlanmış sabitleri kullanabilirsiniz. Sabitler de tanımsız olabilir ve bu durumda `Nothing`değeri vardır.  
  
## <a name="example"></a>Örnek  

 Bu örnek `#Const` yönergesini kullanır.  
  
 [!code-vb[VbVbalrConditionalComp#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [-tanımla (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
- [#If...Then...#Else Yönergesi](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [Const Deyimi](../../../visual-basic/language-reference/statements/const-statement.md)
- [Koşullu Derleme](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [If...Then...Else Deyimi](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
