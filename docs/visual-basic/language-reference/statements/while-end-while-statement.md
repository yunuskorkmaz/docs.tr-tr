---
title: While...End While Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.While
- vb.While...EndWhile
helpviewer_keywords:
- While statement [Visual Basic], While...End While
- While statement [Visual Basic]
- While...End While statements [Visual Basic]
ms.assetid: b931d1ce-e8ed-44d8-a13d-92a4f5458a1e
ms.openlocfilehash: d9eb8cb95d46e860aa127954d7b44e37991d4a13
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84391592"
---
# <a name="whileend-while-statement-visual-basic"></a>While...End While Deyimi (Visual Basic)
Belirli bir koşul olduğu sürece bir dizi deyim çalıştırır `True` .  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
While condition  
    [ statements ]  
    [ Continue While ]  
    [ statements ]  
    [ Exit While ]  
    [ statements ]  
End While  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`condition`|Gereklidir. `Boolean`ifadesini. İse `condition` `Nothing` , Visual Basic olduğu gibi davranır `False` .|  
|`statements`|İsteğe bağlı. Aşağıdaki her seferinde çalıştırılan bir veya daha fazla deyim `While` `condition` `True` .|  
|`Continue While`|İsteğe bağlı. Denetimi bloğun bir sonraki yinelemesine aktarır `While` .|  
|`Exit While`|İsteğe bağlı. Denetimi bloğunun dışına aktarır `While` .|  
|`End While`|Gereklidir. Bloğunun tanımını sonlandırır `While` .|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir `While...End While` koşul, bir koşulun kaldığı sürece belirsiz sayıda deyim yinelemek istediğinizde bir yapı kullanın `True` . Koşulu test ettiğiniz veya ne sonuçla test ettiğiniz hakkında daha fazla esneklik istiyorsanız [Do... seçeneğini tercih edebilirsiniz. Loop deyimleri](do-loop-statement.md). Deyimlerini bir dizi defa yinelemek istiyorsanız, [için... Sonraki Ifade](for-next-statement.md) genellikle daha iyi bir seçimdir.  
  
> [!NOTE]
> `While`Anahtar sözcüğü de [Do... içinde kullanılır. Loop deyimi](do-loop-statement.md), [Skip While yan tümcesi](../queries/skip-while-clause.md) ve [Take While yan tümcesi](../queries/take-while-clause.md).  
  
 İse `condition` , `True` `statements` deyimle karşılaşana kadar tüm çalıştırmaya sahip olur `End While` . Sonra Denetim `While` ifadeye döner ve `condition` tekrar denetlenir. `condition`Hala varsa `True` , işlem tekrarlanır. Eğer ise `False` Denetim, ifadesiyle takip eden deyime geçer `End While` .  
  
 `While`İfade, döngüyü başlamadan önce her zaman koşulu denetler. Durum, koşul kaldığı sürece devam eder `True` . `condition` `False` Döngüyü ilk kez girdiğinizde, bir kez daha çalışır.  
  
 `condition`Genellikle iki değerin karşılaştırılmasının sonuçları, ancak [Boolean veri türü](../data-types/boolean-data-type.md) değeri (veya) olarak değerlendirilen herhangi bir ifade olabilir `True` `False` . Bu ifade, olarak dönüştürülmüş bir sayısal tür gibi başka bir veri türünün değerini içerebilir `Boolean` .  
  
 Bir `While` döngüyü diğerinin içine yerleştirerek iç içe geçirebilirsiniz. Ayrıca, farklı türlerde denetim yapılarını bir diğeri içinde iç içe geçirebilirsiniz. Daha fazla bilgi için bkz. [Iç Içe denetim yapıları](../../programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## <a name="exit-while"></a>Çıkış sırasında çıkış  
 [Exit While](exit-statement.md) deyimleri, bir döngüden çıkmak için başka bir yol sağlayabilir `While` . `Exit While`, denetimi hemen takip eden deyime aktarır `End While` .  
  
 Genellikle `Exit While` bir koşul hesaplandıktan sonra (örneğin, bir `If...Then...Else` yapıda) kullanırsınız. Hatalı bir değer veya sonlandırma isteği gibi yineleme işleminin devam etmesi için gereksiz veya imkansız hale getiren bir koşul tespit ederseniz bir döngüden çıkmak isteyebilirsiniz. Sonsuz `Exit While` *döngüye*neden olabilecek bir koşul için test ettiğinizde kullanabilirsiniz. Bu, son derece büyük veya hatta sonsuz bir sayı çalışabilen bir döngüdür. Ardından, `Exit While` döngüyü atlamak için kullanabilirsiniz.  
  
 `Exit While`Döngüde herhangi bir yere herhangi bir sayıda deyim yerleştirebilirsiniz `While` .  
  
 İç içe döngüler içinde kullanıldığında `While` , `Exit While` denetimi en içteki döngünün dışına ve sonraki yüksek iç içe geçme düzeyine aktarır.  
  
 `Continue While`Ekstre, denetimi hemen döngüsünün bir sonraki yinelemesine aktarır. Daha fazla bilgi için bkz. [Continue bildirisi](continue-statement.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, döngü içindeki deyimler, değişken 10 ' dan büyük olana kadar çalışmaya devam eder `index` .  
  
 [!code-vb[VbVbalrStatements#171](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#171)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `Continue While` ve deyimlerinin kullanımını gösterir `Exit While` .  
  
 [!code-vb[VbVbalrStatements#172](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#172)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir metin dosyasındaki tüm satırları okur. <xref:System.IO.File.OpenText%2A>Yöntemi dosyayı açar ve karakterleri okuyan bir döndürür <xref:System.IO.StreamReader> . Koşulunda, `While` <xref:System.IO.StreamReader.Peek%2A> öğesinin yöntemi `StreamReader` dosyanın ek karakterler içerip içermediğini belirler.  
  
 [!code-vb[VbVbalrStatements#173](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#173)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Döngü Yapıları](../../programming-guide/language-features/control-flow/loop-structures.md)
- [Do...Loop Deyimi](do-loop-statement.md)
- [For...Next Deyimi](for-next-statement.md)
- [Boolean Veri Türü](../data-types/boolean-data-type.md)
- [İç İçe Geçmiş Denetim Yapıları](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit Deyimi](exit-statement.md)
- [Continue bildirisi](continue-statement.md)
