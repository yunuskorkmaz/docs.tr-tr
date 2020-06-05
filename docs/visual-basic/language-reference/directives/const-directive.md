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
ms.openlocfilehash: 91152771a4ef5ec74a7408511ccc2afe28dd442e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415472"
---
# <a name="const-directive"></a>#Const Yönergesi

Visual Basic için koşullu derleyici sabitleri tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
#Const constname = expression  
```  
  
## <a name="parts"></a>Bölümler  

 `constname`  
 Gereklidir. Tanımlanmakta olan sabitin adı.  
  
 `expression`  
 Gereklidir. Değişmez değer, diğer koşullu derleyici sabiti veya hariç herhangi bir ya da tüm aritmetik ya da mantıksal işleçleri içeren herhangi bir bileşim `Is` .  
  
## <a name="remarks"></a>Açıklamalar  

 Koşullu derleyici sabitleri, her zaman göründükleri dosya için özeldir. Yönergesini kullanarak genel derleyici sabitleri oluşturamazsınız `#Const` ; bunları yalnızca Kullanıcı arabiriminde veya `/define` derleyici seçeneğiyle oluşturabilirsiniz.  
  
 Yalnızca koşullu derleyici sabitlerini ve sabit değerlerini kullanabilirsiniz `expression` . İle tanımlanmış standart bir sabit kullanılması `Const` hataya neden olur. Buna karşılık, `#Const` yalnızca koşullu derleme için anahtar sözcükle tanımlanmış sabitleri kullanabilirsiniz. Sabitler de tanımsız olabilir ve bu durumda bir değeri olur `Nothing` .  
  
## <a name="example"></a>Örnek  

 Bu örnek, `#Const` yönergesini kullanır.  
  
 [!code-vb[VbVbalrConditionalComp#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [-tanımla (Visual Basic)](../../reference/command-line-compiler/define.md)
- [#If... Sonra... #Else yönergeler](if-then-else-directives.md)
- [Const Deyimi](../statements/const-statement.md)
- [Koşullu Derleme](../../programming-guide/program-structure/conditional-compilation.md)
- [If...Then...Else Deyimi](../statements/if-then-else-statement.md)
