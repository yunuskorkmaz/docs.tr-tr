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
ms.openlocfilehash: 3ff3d67f38f510b798da3e470de066cff1e98f29
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638781"
---
# <a name="doloop-statement-visual-basic"></a>Do...Loop Deyimi (Visual Basic)
Bir while deyimleri bloğunu bir `Boolean` koşul `True` veya koşulu olana kadar `True`.  
  
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
|`Do`|Gerekli. Tanımı başlar `Do` döngü.|  
|`While`|Sürece gerekli `Until` kullanılır. Döngüyü kadar `condition` olduğu `False`.|  
|`Until`|Sürece gerekli `While` kullanılır. Döngüyü kadar `condition` olduğu `True`.|  
|`condition`|İsteğe bağlı. `Boolean` ifade. Varsa `condition` olduğu `Nothing`, Visual Basic bunu algılar `False`.|  
|`statements`|İsteğe bağlı. Sırasında veya kadar yinelenen bir veya daha fazla deyimleri `condition` olduğu `True`.|  
|`Continue Do`|İsteğe bağlı. Denetim bir sonraki yinelemesine aktarır `Do` döngü.|  
|`Exit Do`|İsteğe bağlı. Dışı denetim aktarır `Do` döngü.|  
|`Loop`|Gerekli. Tanımını sonlandırır `Do` döngü.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım bir `Do...Loop` yapısı deyimleri belirsiz numarası bir kez, bir koşul sağlanana kadar bir dizi yinelemek istediğinizde. Bir kez sayıdaki deyimleri yinelemek istiyorsanız [için... Sonraki deyimi](../../../visual-basic/language-reference/statements/for-next-statement.md) genellikle daha iyi bir seçimdir.  
  
 Kullanabilirsiniz `While` veya `Until` belirtmek için `condition`, ikisini birden belirtmeyin.  
  
 Test edebilirsiniz `condition` başlangıç veya bitiş döngünün yalnızca bir kez. Test, `condition` döngünün başında (içinde `Do` deyimi), döngü bile bir kez çalışmayabilir. Döngü, sonunda test ederseniz (içinde `Loop` deyimi), döngü, her zaman en az bir kez çalışır.  
  
 Koşul genellikle iki değer karşılaştırması sonuçları ancak olarak değerlendirilen herhangi bir ifade olabilir bir [Boole veri türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md) değeri (`True` veya `False`). Bu değerler için dönüştürülen sayısal türleri gibi diğer veri türleri içerir `Boolean`.  
  
 İç içe yerleştirebilirsiniz `Do` içindeki başka bir döngü koyarak döngüleri. Farklı türlerde denetim yapılarını birbirine içinde iç içe yerleştirebilirsiniz. Daha fazla bilgi için [iç içe geçmiş denetim yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
> [!NOTE]
>  `Do...Loop` Yapısına göre daha fazla esneklik sağlar [sırada... End While deyimi](../../../visual-basic/language-reference/statements/while-end-while-statement.md) döngü sona karar olanak sağladığından, `condition` olmaktan çıkar `True` veya ne zaman ilk duruma `True`. Ayrıca, test etmek sağlar `condition` başlangıç veya bitiş döngünün.  
  
## <a name="exit-do"></a>Çıkış yapın  
 [Çıkış yapın](../../../visual-basic/language-reference/statements/exit-statement.md) deyimi, çıkmak için alternatif bir yol sağlayabilir bir `Do…Loop`. `Exit Do` Denetim takip eden deyime hemen aktarır `Loop` deyimi.  
  
 `Exit Do` Bazı koşullar örnekte değerlendirildikten sonra sık kullanılan bir `If...Then...Else` yapısı. Gereksiz veya hatalı bir değer veya bir sonlandırma isteği gibi yineleme devam etmek mümkün kılan bir koşul algılama bir döngüden çıkma isteyebilirsiniz. Bir kullanımını `Exit Do` neden olabilecek bir koşulu sınamak için bir *sonsuz bir döngüye*, bir büyük veya hatta sonsuz sayıda çalıştırabileceğiniz bir döngü olduğu. Kullanabileceğiniz `Exit Do` döngüden çıkma.  
  
 Herhangi bir sayıda içerebilir `Exit Do` deyimlerinde herhangi bir yerde bir `Do…Loop`.  
  
 Kullanıldığında içinde iç içe geçmiş `Do` döngüleri `Exit Do` denetimi iç döngü dışında ve iç içe geçme daha yüksek düzeydeki içine aktarır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, Döngüdeki deyimler kadar çalışmaya devam `index` değişkendir 10'dan büyük. `Until` Yan tümcesi ise döngü sonunda.  
  
 [!code-vb[VbVbalrStatements#131](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#131)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir `While` yan tümcesi yerine bir `Until` yan tümcesi ve `condition` sonunda yerine döngüsünün başında test edilir.  
  
 [!code-vb[VbVbalrStatements#132](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#132)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, `condition` döngü durdurur, `index` değişkendir 100'den büyük. `If` Döngü deyimi ancak neden `Exit Do` döngüyü dizin değişkeni 10'dan büyük olduğunda durdurmak için deyimi.  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir metin dosyasındaki tüm satırları okur. <xref:System.IO.File.OpenText%2A> Yöntemi dosyayı açar ve döndüren bir <xref:System.IO.StreamReader> , bir karakter okur. İçinde `Do...Loop` koşulu <xref:System.IO.StreamReader.Peek%2A> yöntemi `StreamReader` herhangi bir ek karakter olup olmadığını belirler.  
  
 [!code-vb[VbVbalrStatements#134](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#134)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Döngü Yapıları](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [For...Next Deyimi](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Boolean Veri Türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [İç İçe Geçmiş Denetim Yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit Deyimi](../../../visual-basic/language-reference/statements/exit-statement.md)
- [While...End While Deyimi](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
