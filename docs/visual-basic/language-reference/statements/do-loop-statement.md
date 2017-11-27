---
title: Do...Loop Deyimi (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Do
- vb.Loop
- vb.Until
helpviewer_keywords:
- "conditional statements [Visual Basic], Do�Loop"
- while statement [Visual Basic], Do...Loop
- execution [Visual Basic], conditional
- Do loops
- Until keyword [Visual Basic], Do...Loop statement
- Do...Loop statement
- instructions, repeating
- Do statement [Visual Basic]
- Exit statement [Visual Basic], in Do...Loop statements
- "loop structures [Visual Basic], Do�Loop statements"
- do-while statements [Visual Basic]
- loops, exiting
- Loop keyword [Visual Basic], Do...Loop statement
ms.assetid: 892f9096-b3e2-4aee-834d-83bc4e2c379d
caps.latest.revision: "37"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 79d25dce963f383a84b56ce2c9b600fc2d5a7937
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="doloop-statement-visual-basic"></a>Do...Loop Deyimi (Visual Basic)
While deyimleri bloğunu yinelenen bir `Boolean` koşul `True` veya koşul olana kadar `True`.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Do { While | Until } condition  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop  
-or-  
Do  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop { While | Until } condition  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`Do`|Gerekli. Tanımını başlatır `Do` döngü.|  
|`While`|Sürece gerekli `Until` kullanılır. Döngüyü kadar `condition` olan `False`.|  
|`Until`|Sürece gerekli `While` kullanılır. Döngüyü kadar `condition` olan `True`.|  
|`condition`|İsteğe bağlı. `Boolean`ifade. Varsa `condition` olan `Nothing`, Visual Basic da işler `False`.|  
|`statements`|İsteğe bağlı. Sırasında veya kadar yinelenen bir veya daha fazla deyimleri `condition` olan `True`.|  
|`Continue Do`|İsteğe bağlı. Sonraki yinelemesini denetim aktarır `Do` döngü.|  
|`Exit Do`|İsteğe bağlı. Denetimin dışarı aktarır `Do` döngü.|  
|`Loop`|Gerekli. Tanımını sonlandırır `Do` döngü.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım bir `Do...Loop` yapısı belirsiz numarası bir deyimleri bir koşul sağlanırsa kadar kaç kez, bir dizi yineleyin istediğinizde. İfadeler kümesi birkaç kez yineleyin istiyorsanız [için... Sonraki deyim](../../../visual-basic/language-reference/statements/for-next-statement.md) genellikle daha iyi bir seçimdir.  
  
 Kullanabilirsiniz `While` veya `Until` belirtmek için `condition`, ancak ikisini birden değil.  
  
 Test edebilirsiniz `condition` başlangıç veya döngüsünün sonuna yalnızca bir kez. Test ederseniz `condition` döngü başlangıcında (içinde `Do` deyimi), döngü bile bir kez çalışmayabilir. Döngü sonunda test ederseniz (içinde `Loop` deyimi), döngünün her zaman en az bir kez çalışır.  
  
 Koşul genellikle iki değer karşılaştırmadan olur, ancak veren herhangi bir ifade olabilir bir [Boole veri türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md) değeri (`True` veya `False`). Bu değerleri için dönüştürülen sayısal türler gibi diğer veri türleri içerir `Boolean`.  
  
 Geçirebilmenize `Do` döngüler içinde başka bir döngü koyarak kullanılabilir. Ayrıca, değişik birbirine içindeki denetim yapıları yerleştirebilirsiniz. Daha fazla bilgi için bkz: [iç içe geçmiş denetim yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
> [!NOTE]
>  `Do...Loop` Yapısı size daha fazla esneklik [sırada... End While deyimi](../../../visual-basic/language-reference/statements/while-end-while-statement.md) , döngü sona erdirmek karar vermek sağladığından, `condition` olan durdurur `True` veya zaman ilk olacağını `True`. Ayrıca, test etmek sağlar `condition` başlangıç veya döngüsü sonu.  
  
## <a name="exit-do"></a>Çık  
 [Çıkış yapmak](../../../visual-basic/language-reference/statements/exit-statement.md) deyimi, çıkmak için alternatif bir yol sağlayabilir bir `Do…Loop`. `Exit Do`aşağıdaki deyim denetimi hemen aktarır `Loop` deyimi.  
  
 `Exit Do`Bazı koşul örnekte değerlendirildikten sonra sık kullanılan bir `If...Then...Else` yapısı. Gereksiz veya hatalı bir değer veya bir sonlandırma isteği gibi yineleme devam mümkün kılan bir koşul algılama döngü çıkmak isteyebilirsiniz. Bir kullanımını `Exit Do` neden olabilecek bir koşulu sınamak için bir *sonsuz bir döngüde*, bir büyük veya hatta sonsuz sayıda çalışacak bir döngü değil. Kullanabileceğiniz `Exit Do` döngü kaçınmak için.  
  
 Herhangi bir sayıda içerebilir `Exit Do` deyimlerinde herhangi bir yerden bir `Do…Loop`.  
  
 Kullanıldığında içinde iç içe geçmiş `Do` döngüler, `Exit Do` denetimi en içteki döngü dışında ve iç içe geçme sonraki daha yüksek düzeyde uygulamasına aktarır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, döngü deyimlerinde kadar çalışmaya devam `index` değişkenidir 10'dan büyük. `Until` Yan tümcesi olan döngü sonunda.  
  
 [!code-vb[VbVbalrStatements#131](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_1.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanan bir `While` yan tümcesi yerine bir `Until` yan tümcesi ve `condition` yerine döngü sonunda başlangıcında test.  
  
 [!code-vb[VbVbalrStatements#132](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_2.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, `condition` döngü durur zaman `index` değişkenidir 100'den büyük. `If` Döngüdeki deyimi ancak neden `Exit Do` deyimi dizin değişken 10'dan büyük olduğunda döngü durdurmak için.  
  
 [!code-vb[VbVbalrStatements#133](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_3.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir metin dosyasındaki tüm satırları okur. <xref:System.IO.File.OpenText%2A> Yöntemi dosyayı açar ve döndürür bir <xref:System.IO.StreamReader> karakterleri okur. İçinde `Do...Loop` koşulu <xref:System.IO.StreamReader.Peek%2A> yöntemi `StreamReader` herhangi bir ek karakter olup olmadığını belirler.  
  
 [!code-vb[VbVbalrStatements#134](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_4.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Döngü yapıları](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [İçin... Sonraki deyim](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Boole veri türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md)  
 [İç içe geçmiş denetim yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [Exit deyimi](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [While... End While deyimi](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
