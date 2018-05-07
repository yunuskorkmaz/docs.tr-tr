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
ms.openlocfilehash: 90b805df902dcdfebe85421583dd54e9af04bec9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="mid-statement"></a>Mid Deyimi
Belirtilen sayıda karakteri değiştiren bir `String` başka bir dizeden karakterleri içeren değişken.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a>Bölümler  
 `Target`  
 Gerekli. Adını `String` değiştirmek için değişken.  
  
 `Start`  
 Gerekli. `Integer` İfade. Karakter konumda `Target` metin değiştirme başladığı. `Start` bir tabanlı bir dizin kullanır.  
  
 `Length`  
 İsteğe bağlı. `Integer` İfade. Değiştirilecek karakterler sayısı. Atlanırsa, tüm `String` kullanılır.  
  
 `StringExpression`  
 Gerekli. `String` bölümünü değiştirir ifade `Target`.  
  
## <a name="exceptions"></a>Özel Durumlar  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|`Start` < = 0 veya `Length` < 0.|  
  
## <a name="remarks"></a>Açıklamalar  
 Değiştirilen karakter sayısını her zaman karakter sayısı küçük veya buna eşit olan `Target`.  
  
 Visual Basic sahip bir <xref:Microsoft.VisualBasic.Strings.Mid%2A> işlevi ve `Mid` deyimi. Her ikisi de çalışan bir dizedeki karakter belirtilen sayıdaki bu öğeleri ancak `Mid` işlevi sırasında karakter döndürür `Mid` deyimi karakterleri yerini alır. Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Strings.Mid%2A>.  
  
> [!NOTE]
>  `MidB` Deyimi Visual Basic önceki sürümlerinin bir alt dizenin karakter yerine bayt yerini alır. Esas olarak çift baytlı karakter kümesi (DBCS) uygulamalarında dize dönüştürmek için kullanılır. Tüm Visual Basic dizeleri Unicode biçiminde olan ve `MidB` artık desteklenmiyor.  
  
## <a name="example"></a>Örnek  
 Bu örnekte `Mid` başka bir dizeden karakterleri içeren bir dize değişkeni karakter belirtilen sayıda değiştirmek için deyimi.  
  
 [!code-vb[VbVbalrStrings#5](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/mid-statement_1.vb)]  
  
## <a name="requirements"></a>Gereksinimler  
 **Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Modülü:** `Strings`  
  
 **Derleme:** [!INCLUDE[vbprvbruntime](~/includes/vbprvbruntime-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A>  
 [Dizeler](../../../visual-basic/programming-guide/language-features/strings/index.md)  
 [Visual Basic'de dizelere giriş](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
