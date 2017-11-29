---
title: "#<a name=\"const-directive\"></a>Const yönergesi"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a6e162b01dc5c99fb7708337d259f9e66ddd6b64
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="const-directive"></a>#Const Yönergesi
Koşullu derleme sabitleri için Visual Basic tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
#Const constname = expression  
```  
  
## <a name="parts"></a>Bölümler  
 `constname`  
 Gerekli. Tanımlanan sabiti adı.  
  
 `expression`  
 Gerekli. Değişmez değeri, diğer koşullu derleme sabiti ya da tüm aritmetik veya mantıksal işleçler dışında içeren herhangi bir birleşimini `Is`.  
  
## <a name="remarks"></a>Açıklamalar  
 Koşullu derleme sabitleri her zaman göründükleri dosyasına özeldir. Genel derleyici sabitleri kullanarak oluşturulamıyor `#Const` yönerge; oluşturabileceğiniz bunları yalnızca kullanıcı arabiriminde veya ile `/define` derleyici seçeneği.  
  
 Yalnızca koşullu derleyici sabit ve değişmez değerlerine kullanabilirsiniz `expression`. İle tanımlanan bir standart sabit kullanarak `Const` bir hataya neden olur. Buna karşılık, tanımlanmış sabitleri kullanabilirsiniz `#Const` anahtar sözcüğü yalnızca koşullu derleme için. Sabitleri ayrıca tanımlanmamış, bu durumda bunlar değerine sahip `Nothing`.  
  
## <a name="example"></a>Örnek  
 Bu örnekte `#Const` yönergesi.  
  
 [!code-vb[VbVbalrConditionalComp#3](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/const-directive_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [/ define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)  
 [#If... Then... #Else yönergeleri](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [Const deyimi](../../../visual-basic/language-reference/statements/const-statement.md)  
 [Koşullu derleme](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 [If... Then... Else deyimi](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
