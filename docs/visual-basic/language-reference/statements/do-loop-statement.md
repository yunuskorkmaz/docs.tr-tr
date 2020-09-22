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
ms.openlocfilehash: 86a702aefeea1e5e359a579a3f29e9c06f1c619c
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90865929"
---
# <a name="doloop-statement-visual-basic"></a>Do...Loop Deyimi (Visual Basic)

Bir `Boolean` koşul olduğunda `True` veya koşul haline gelene kadar bir deyim bloğunu yineler `True` .  
  
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
|`Do`|Gereklidir. Döngünün tanımını başlatır `Do` .|  
|`While`|`Until`Kullanılmadıysa gereklidir. Loop olana kadar tekrarlayın `condition` `False` .|  
|`Until`|`While`Kullanılmadıysa gereklidir. Loop olana kadar tekrarlayın `condition` `True` .|  
|`condition`|İsteğe bağlı. `Boolean` ifadesini. İse `condition` `Nothing` , Visual Basic olduğu gibi davranır `False` .|  
|`statements`|İsteğe bağlı. , Veya Until gibi yinelenen bir veya daha fazla deyim `condition` `True` .|  
|`Continue Do`|İsteğe bağlı. Denetimi döngünün bir sonraki yinelemesine aktarır `Do` .|  
|`Exit Do`|İsteğe bağlı. Denetimi döngünün dışına aktarır `Do` .|  
|`Loop`|Gereklidir. Döngünün tanımını sonlandırır `Do` .|  
  
## <a name="remarks"></a>Açıklamalar  

 Bir `Do...Loop` deyim kümesini sınırsız sayıda yinelemek istediğinizde, bir koşul karşılanana kadar bir yapı kullanın. Deyimlerini bir dizi defa yinelemek istiyorsanız, [için... Sonraki Ifade](for-next-statement.md) genellikle daha iyi bir seçimdir.  
  
 `While`Ya da `Until` öğesini belirtmek için veya `condition` ikisini de kullanabilirsiniz.  
  
 `condition`Döngünün başlangıcında veya sonunda yalnızca bir kez test edebilirsiniz. Döngünün başlangıcında test ederseniz `condition` ( `Do` bildiriminde), döngü bir kez çalışmayabilir. Döngünün sonunda test ederseniz ( `Loop` bildiriminde), döngü her zaman en az bir kez çalışır.  
  
 Koşul genellikle iki değerin karşılaştırılmasının sonucunu verir, ancak [Boolean veri türü](../data-types/boolean-data-type.md) değeri (veya) olarak değerlendirilen herhangi bir ifade olabilir `True` `False` . Buna dönüştürülmüş sayısal türler gibi diğer veri türlerinin değerleri de dahildir `Boolean` .  
  
 Bir `Do` döngüyü diğerinin içine yerleştirerek döngüleri iç içe geçirebilirsiniz. Ayrıca, farklı türlerde denetim yapılarını birbirleriyle iç içe geçirebilirsiniz. Daha fazla bilgi için bkz. [Iç Içe denetim yapıları](../../programming-guide/language-features/control-flow/nested-control-structures.md).  
  
> [!NOTE]
> `Do...Loop`Yapı, çok daha fazla esneklik sağlar [... End while Ifadesinin sonu](while-end-while-statement.md) , ne zaman `condition` `True` veya ilk kez geldiğini sonlandırırken döngüyü sonlandırmaya karar vermenize olanak sağlar `True` . Ayrıca döngünün başlangıcında veya sonunda test etmenizi sağlar `condition` .  
  
## <a name="exit-do"></a>Çık  

 [Exit Do](exit-statement.md) deyimleri, bir çıkışı için alternatif bir yol sağlayabilir `Do…Loop` . `Exit Do` denetimi, ifadesiyle takip eden deyime hemen aktarır `Loop` .  
  
 `Exit Do` Genellikle, örneğin bir yapıda, bazı koşullar hesaplandıktan sonra kullanılır `If...Then...Else` . Hatalı bir değer veya sonlandırma isteği gibi yineleme işleminin devam etmesi için gereksiz veya imkansız hale getiren bir koşul tespit ederseniz bir döngüden çıkmak isteyebilirsiniz. Tek kullanımı, sonsuz bir `Exit Do` *döngüye*neden olabilecek bir durum için test etmek, büyük veya hatta sonsuz bir sayı çalışabilen bir döngüdür. `Exit Do`Döngüyü atlamak için ' i kullanabilirsiniz.  
  
 Herhangi `Exit Do` bir yerde herhangi bir sayıda deyim ekleyebilirsiniz `Do…Loop` .  
  
 İç içe döngüler içinde kullanıldığında `Do` , `Exit Do` denetimi en içteki döngünün dışına ve sonraki yüksek iç içe geçme düzeyine aktarır.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnekte, döngü içindeki deyimler, değişken 10 ' dan büyük olana kadar çalışmaya devam eder `index` . `Until`Yan tümce döngünün sonunda bulunur.  
  
 [!code-vb[VbVbalrStatements#131](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#131)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek `While` , bir yan tümce yerine bir yan tümce kullanır `Until` ve `condition` son yerine döngüsünün başlangıcında test edilir.  
  
 [!code-vb[VbVbalrStatements#132](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#132)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnekte, `condition` `index` değişken 100 ' den büyükse döngüyü sonlandırır. `If`Ancak, döngüdeki ifade, `Exit Do` Dizin değişkeni 10 ' dan büyük olduğunda deyimin döngüyü durdurmasına neden olur.  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek bir metin dosyasındaki tüm satırları okur. <xref:System.IO.File.OpenText%2A>Yöntemi dosyayı açar ve karakterleri okuyan bir döndürür <xref:System.IO.StreamReader> . Koşulunda, `Do...Loop` <xref:System.IO.StreamReader.Peek%2A> öğesinin yöntemi `StreamReader` ek karakter olup olmadığını belirler.  
  
 [!code-vb[VbVbalrStatements#134](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#134)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Döngü Yapıları](../../programming-guide/language-features/control-flow/loop-structures.md)
- [For...Next Deyimi](for-next-statement.md)
- [Boolean Veri Türü](../data-types/boolean-data-type.md)
- [İç İçe Geçmiş Denetim Yapıları](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit Deyimi](exit-statement.md)
- [While...End While Deyimi](while-end-while-statement.md)
