---
title: Mid Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.MidB
- vb.Mid
helpviewer_keywords:
- substrings [Visual Basic], Mid statement
- strings [Visual Basic], substrings
- Mid statement [Visual Basic]
- strings [Visual Basic], replacing
ms.assetid: 2b82d7a8-9646-4cb0-bec5-80abc98297bf
ms.openlocfilehash: eeef4c13743b75a3d5e61ac46afb94d9ea105b7a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348033"
---
# <a name="mid-statement"></a>Mid Deyimi
Bir `String` değişkeninde belirtilen sayıda karakteri başka bir dizeden karakterlerle değiştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a>Bölümler  
 `Target`  
 Gerekli. Değiştirilecek `String` değişkeninin adı.  
  
 `Start`  
 Gerekli. `Integer` ifadesi. Metnin değiştirme işleminin başladığı `Target` karakter konumu. `Start`, tek tabanlı bir dizin kullanır.  
  
 `Length`  
 İsteğe bağlı. `Integer` ifadesi. Değiştirilecek karakter sayısı. Atlanırsa, tüm `String` kullanılır.  
  
 `StringExpression`  
 Gerekli. `Target`kısmını değiştiren `String` ifadesi.  
  
## <a name="exceptions"></a>Özel Durumlar  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|`Start` < = 0 veya `Length` < 0.|  
  
## <a name="remarks"></a>Açıklamalar  
 Değişen karakterlerin sayısı her zaman `Target`karakter sayısından küçüktür veya eşittir.  
  
 Visual Basic bir <xref:Microsoft.VisualBasic.Strings.Mid%2A> işlevi ve bir `Mid` deyimidir. Bu öğeler her ikisi de bir dizedeki belirtilen sayıda karakter üzerinde çalışır, ancak `Mid` işlevi, `Mid` ifadesinin karakterleri değiştirdiği sırada karakterleri döndürür. Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Strings.Mid%2A>.  
  
> [!NOTE]
> Önceki Visual Basic sürümlerindeki `MidB` deyimleri karakter yerine bayt cinsinden bir alt dizenin yerini alır. Esas olarak çift baytlı karakter kümesi (DBCS) uygulamalarında dize dönüştürmek için kullanılır. Tüm Visual Basic dizeleri Unicode 'Dur ve `MidB` artık desteklenmez.  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir dize değişkeninde belirtilen sayıda karakteri başka bir dizeden karakterler ile değiştirmek için `Mid` ifadesini kullanır.  
  
 [!code-vb[VbVbalrStrings#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#5)]  
  
## <a name="requirements"></a>Gereksinimler  
 **Ad alanı:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Modül:** `Strings`  
  
 **Bütünleştirilmiş kod:** Visual Basic çalışma zamanı kitaplığı (Microsoft. VisualBasic. dll içinde)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- [Dizeler](../../../visual-basic/programming-guide/language-features/strings/index.md)
- [Visual Basic dizelere giriş](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
