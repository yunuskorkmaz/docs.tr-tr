---
title: Do...Loop Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.Do
- vb.Loop
- vb.Until
helpviewer_keywords:
- conditional statements [Visual Basic], Do�Loop
- while statement [Visual Basic], Do...Loop
- execution [Visual Basic], conditional
- Do loops
- Until keyword [Visual Basic], Do...Loop statement
- Do...Loop statement
- instructions, repeating
- Do statement [Visual Basic]
- Exit statement [Visual Basic], in Do...Loop statements
- loop structures [Visual Basic], Do�Loop statements
- do-while statements [Visual Basic]
- loops, exiting
- Loop keyword [Visual Basic], Do...Loop statement
ms.assetid: 892f9096-b3e2-4aee-834d-83bc4e2c379d
ms.openlocfilehash: 9384cbb355189be448fa4b8d274721b4a7ca6a20
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351251"
---
# <a name="doloop-statement-visual-basic"></a>Do...Loop Deyimi (Visual Basic)
Bir `Boolean` koşulu `True` veya koşul `True`hale gelinceye kadar bir deyim bloğunu yineler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Do { While | Until } condition  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop  
' -or-  
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
|`Do`|Gerekli. `Do` döngüsünün tanımını başlatır.|  
|`While`|`Until` kullanılmadığı müddetçe gereklidir. `condition` `False`kadar döngüyü tekrarlayın.|  
|`Until`|`While` kullanılmadığı müddetçe gereklidir. `condition` `True`kadar döngüyü tekrarlayın.|  
|`condition`|İsteğe bağlı. `Boolean` ifadesi. `condition` `Nothing`, Visual Basic `False`olarak değerlendirir.|  
|`statements`|İsteğe bağlı. `condition`, veya Until olarak yinelenen bir veya daha fazla deyim `True`.|  
|`Continue Do`|İsteğe bağlı. Denetimi `Do` döngüsünün bir sonraki yinelemesine aktarır.|  
|`Exit Do`|İsteğe bağlı. `Do` döngüsünün dışına denetimini aktarır.|  
|`Loop`|Gerekli. `Do` döngüsünün tanımını sonlandırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir deyim kümesini sınırsız sayıda tekrarlamak istediğinizde, bir koşul karşılanana kadar `Do...Loop` yapısını kullanın. Deyimlerini bir dizi defa yinelemek istiyorsanız, [için... Sonraki Ifade](../../../visual-basic/language-reference/statements/for-next-statement.md) genellikle daha iyi bir seçimdir.  
  
 Yalnızca `condition`belirtmek için `While` ya da `Until` kullanabilirsiniz.  
  
 `condition` döngünün başlangıcında veya sonunda yalnızca bir kez test edebilirsiniz. Döngünün başlangıcında `condition` test ederseniz (`Do` bildiriminde), döngü bir kez çalışmayabilir. Döngünün sonunda test ederseniz (`Loop` bildiriminde), döngü her zaman en az bir kez çalışır.  
  
 Koşul genellikle iki değerin karşılaştırılmasının sonucunu verir, ancak [Boolean veri türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md) değeri (`True` veya `False`) değerlendirilen herhangi bir ifade olabilir. Bu, `Boolean`dönüştürülen sayısal türler gibi diğer veri türlerinin değerlerini içerir.  
  
 Bir döngüyü diğerinin içine yerleştirerek `Do` döngüleri iç içe geçirebilirsiniz. Ayrıca, farklı türlerde denetim yapılarını birbirleriyle iç içe geçirebilirsiniz. Daha fazla bilgi için bkz. [Iç Içe denetim yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
> [!NOTE]
> `Do...Loop` yapısı, çok daha fazla esneklik sağlar... [ End while Ifadesinin](../../../visual-basic/language-reference/statements/while-end-while-statement.md) `condition` `True` durdurulduğunda veya ilk `True`hale geldiği zaman döngünün sonlandırılmayacağına karar vermenize olanak sağlar. Ayrıca, döngünün başlangıcında veya sonunda `condition` test etmenizi sağlar.  
  
## <a name="exit-do"></a>Çık  
 [Exit Do](../../../visual-basic/language-reference/statements/exit-statement.md) deyimleri `Do…Loop`çıkmak için alternatif bir yol sağlayabilir. `Exit Do` denetimi, `Loop` bildirisini izleyen deyime hemen aktarır.  
  
 `Exit Do`, örneğin bir `If...Then...Else` yapısında bir koşul hesaplandıktan sonra kullanılır. Hatalı bir değer veya sonlandırma isteği gibi yineleme işleminin devam etmesi için gereksiz veya imkansız hale getiren bir koşul tespit ederseniz bir döngüden çıkmak isteyebilirsiniz. `Exit Do` kullanımı, sonsuz bir *döngüye*neden olabilecek, büyük veya hatta sonsuz bir sayı çalışabilen bir döngü olan bir koşulu test etmekle yöneliktir. Döngüyü atlamak için `Exit Do` kullanabilirsiniz.  
  
 Herhangi bir sayıda `Exit Do` deyimini `Do…Loop`herhangi bir yere ekleyebilirsiniz.  
  
 İç içe geçmiş `Do` döngüleri içinde kullanıldığında, `Exit Do` denetimi en içteki döngüden ve sonraki daha yüksek iç içe geçme düzeyine aktarır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, döngü içindeki deyimler `index` değişkeni 10 ' dan büyük olana kadar çalışmaya devam eder. `Until` yan tümcesi döngünün sonunda bulunur.  
  
 [!code-vb[VbVbalrStatements#131](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#131)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir `Until` yan tümcesi yerine bir `While` yan tümcesi kullanır ve `condition` son yerine döngünün başlangıcında test edilir.  
  
 [!code-vb[VbVbalrStatements#132](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#132)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, `index` değişkeni 100 ' den büyük olduğunda `condition` döngüyü sonlandırır. Ancak, döngüdeki `If` ifade, dizin değişkeni 10 ' dan büyük olduğunda `Exit Do` deyimin döngüyü durdurmasına neden olur.  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir metin dosyasındaki tüm satırları okur. <xref:System.IO.File.OpenText%2A> yöntemi dosyayı açar ve karakterleri okuyan bir <xref:System.IO.StreamReader> döndürür. `Do...Loop` koşulunda, `StreamReader` <xref:System.IO.StreamReader.Peek%2A> yöntemi herhangi bir ek karakter olup olmadığını belirler.  
  
 [!code-vb[VbVbalrStatements#134](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#134)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Döngü Yapıları](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [For...Next Deyimi](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Boolean Veri Türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [İç İçe Geçmiş Denetim Yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit Deyimi](../../../visual-basic/language-reference/statements/exit-statement.md)
- [While...End While Deyimi](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
