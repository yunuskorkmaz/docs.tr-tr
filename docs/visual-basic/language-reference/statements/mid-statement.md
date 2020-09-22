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
ms.openlocfilehash: 0379a6cabe819365b22994a5e4f9353d98b2c768
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873198"
---
# <a name="mid-statement"></a>Mid Deyimi

Bir değişkende belirtilen sayıda karakteri `String` , başka bir dizeden karakterlerle değiştirir.  
  
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
 Gereklidir. `String`Değiştirilecek değişkenin adı.  
  
 `Start`  
 Gereklidir. `Integer` ifadesini. `Target`Metnin yerini değiştirme işleminin başladığı karakter konumu. `Start` tek tabanlı bir dizin kullanır.  
  
 `Length`  
 İsteğe bağlı. `Integer` ifadesini. Değiştirilecek karakter sayısı. Atlanırsa, tümü `String` kullanılır.  
  
 `StringExpression`  
 Gereklidir. `String` bölümünün yerini alan ifade `Target` .  
  
## <a name="exceptions"></a>Özel durumlar  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|`Start` <= 0 veya `Length` < 0.|  
  
## <a name="remarks"></a>Açıklamalar  

 Değiştirilmekte olan karakter sayısı her zaman içindeki karakter sayısından daha küçüktür veya eşittir `Target` .  
  
 Visual Basic bir <xref:Microsoft.VisualBasic.Strings.Mid%2A> işleve ve ifadeye sahiptir `Mid` . Bu öğeler her ikisi de bir dizedeki belirtilen sayıda karakter üzerinde çalışır, ancak işlev, `Mid` ifadenin karakterleri değiştirdiği sırada karakterleri döndürür `Mid` . Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Strings.Mid%2A>.  
  
> [!NOTE]
> `MidB`Visual Basic önceki sürümleri, bir alt dizeyi karakterler yerine bayt olarak değiştirir. Esas olarak çift baytlı karakter kümesi (DBCS) uygulamalarında dize dönüştürmek için kullanılır. Tüm Visual Basic dizeleri Unicode ve `MidB` artık desteklenmiyor.  
  
## <a name="example"></a>Örnek  

 Bu örnek, bir `Mid` dize değişkeninde belirtilen sayıda karakteri başka bir dizeden karakterler ile değiştirmek için ifadesini kullanır.  
  
 [!code-vb[VbVbalrStrings#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#5)]  
  
## <a name="requirements"></a>Gereksinimler  

 **Ad alanı:** [Microsoft. VisualBasic](../runtime-library-members.md)  
  
 **Modül:**`Strings`  
  
 **Bütünleştirilmiş kod:** Visual Basic çalışma zamanı kitaplığı (Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- [Dizeler](../../programming-guide/language-features/strings/index.md)
- [Visual Basic'de Dizelere Giriş](../../programming-guide/language-features/strings/introduction-to-strings.md)
