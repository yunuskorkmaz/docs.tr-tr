---
title: Do...Loop Deyimi (Visual Basic)
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
ms.openlocfilehash: 75a2129a9f332024831d97021e381f1b3d4fa048
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942992"
---
# <a name="doloop-statement-visual-basic"></a>Do...Loop Deyimi (Visual Basic)
Bir `Boolean` koşul olduğunda `True` veya koşul haline `True`gelene kadar bir deyim bloğunu yineler.  
  
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
|`Do`|Gerekli. `Do` Döngünün tanımını başlatır.|  
|`While`|Kullanılmadıysa `Until` gereklidir. Loop olana kadar `condition` `False`tekrarlayın.|  
|`Until`|Kullanılmadıysa `While` gereklidir. Loop olana kadar `condition` `True`tekrarlayın.|  
|`condition`|İsteğe bağlı. `Boolean`ifadesini. İse, Visual Basic olduğu gibi `False`davranır. `Nothing` `condition`|  
|`statements`|İsteğe bağlı. , Veya Until gibi `condition` `True`yinelenen bir veya daha fazla deyim.|  
|`Continue Do`|İsteğe bağlı. Denetimi `Do` döngünün bir sonraki yinelemesine aktarır.|  
|`Exit Do`|İsteğe bağlı. Denetimi `Do` döngünün dışına aktarır.|  
|`Loop`|Gerekli. `Do` Döngünün tanımını sonlandırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir deyim `Do...Loop` kümesini sınırsız sayıda yinelemek istediğinizde, bir koşul karşılanana kadar bir yapı kullanın. Deyimlerini bir dizi defa yinelemek istiyorsanız, [için... Sonraki Ifade](../../../visual-basic/language-reference/statements/for-next-statement.md) genellikle daha iyi bir seçimdir.  
  
 Ya da `While` öğesini belirtmek `condition`için `Until` veya ikisini de kullanabilirsiniz.  
  
 Döngünün başlangıcında veya `condition` sonunda yalnızca bir kez test edebilirsiniz. Döngünün başlangıcında test `condition` ederseniz ( `Do` bildiriminde), döngü bir kez çalışmayabilir. Döngünün sonunda test ederseniz ( `Loop` bildiriminde), döngü her zaman en az bir kez çalışır.  
  
 Koşul genellikle iki değerin karşılaştırılmasının sonucunu verir, ancak [Boolean veri türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md) değeri (`True` veya `False`) olarak değerlendirilen herhangi bir ifade olabilir. Buna dönüştürülmüş `Boolean`sayısal türler gibi diğer veri türlerinin değerleri de dahildir.  
  
 Bir döngüyü diğerinin `Do` içine yerleştirerek döngüleri iç içe geçirebilirsiniz. Ayrıca, farklı türlerde denetim yapılarını birbirleriyle iç içe geçirebilirsiniz. Daha fazla bilgi için bkz. [Iç Içe denetim yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
> [!NOTE]
> `Do...Loop` Yapı, çok daha fazla esneklik sağlar... [ End while ifadesinin sonu](../../../visual-basic/language-reference/statements/while-end-while-statement.md) , ne zaman veya ilk kez `condition` `True`geldiğini `True` sonlandırırken döngüyü sonlandırmaya karar vermenize olanak sağlar. Ayrıca döngünün başlangıcında veya sonunda test `condition` etmenizi sağlar.  
  
## <a name="exit-do"></a>Çık  
 [Exit Do](../../../visual-basic/language-reference/statements/exit-statement.md) deyimleri, bir çıkışı için alternatif bir `Do…Loop`yol sağlayabilir. `Exit Do`denetimi, `Loop` ifadesiyle takip eden deyime hemen aktarır.  
  
 `Exit Do`Genellikle, örneğin bir `If...Then...Else` yapıda, bazı koşullar hesaplandıktan sonra kullanılır. Hatalı bir değer veya sonlandırma isteği gibi yineleme işleminin devam etmesi için gereksiz veya imkansız hale getiren bir koşul tespit ederseniz bir döngüden çıkmak isteyebilirsiniz. Tek kullanımı `Exit Do` , sonsuz bir *döngüye*neden olabilecek bir durum için test etmek, büyük veya hatta sonsuz bir sayı çalışabilen bir döngüdür. Döngüyü atlamak için `Exit Do` ' i kullanabilirsiniz.  
  
 Herhangi bir yerde herhangi bir `Exit Do` `Do…Loop`sayıda deyim ekleyebilirsiniz.  
  
 İç içe `Do` döngüler içinde kullanıldığında, `Exit Do` denetimi en içteki döngünün dışına ve sonraki yüksek iç içe geçme düzeyine aktarır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, döngü içindeki deyimler, `index` değişken 10 ' dan büyük olana kadar çalışmaya devam eder. `Until` Yan tümce döngünün sonunda bulunur.  
  
 [!code-vb[VbVbalrStatements#131](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#131)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir `While` `Until` yan tümce yerine bir yan tümce kullanır ve `condition` son yerine döngüsünün başlangıcında test edilir.  
  
 [!code-vb[VbVbalrStatements#132](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#132)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, `index` değişken 100 `condition` ' den büyükse döngüyü sonlandırır. Ancak, döngüdeki `Exit Do` ifade,dizindeğişkeni10'danbüyükolduğundadeyimindöngüyü`If` durdurmasına neden olur.  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir metin dosyasındaki tüm satırları okur. Yöntemi dosyayı açar ve karakterleri okuyan bir <xref:System.IO.StreamReader> döndürür. <xref:System.IO.File.OpenText%2A> Koşulunda, öğesinin`StreamReader` yöntemi ek karakter olup olmadığını belirler. <xref:System.IO.StreamReader.Peek%2A> `Do...Loop`  
  
 [!code-vb[VbVbalrStatements#134](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#134)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Döngü Yapıları](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [For...Next Deyimi](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Boolean Veri Türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [İç İçe Geçmiş Denetim Yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit Deyimi](../../../visual-basic/language-reference/statements/exit-statement.md)
- [While...End While Deyimi](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
