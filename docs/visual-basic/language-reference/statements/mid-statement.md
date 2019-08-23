---
title: Mid açıklaması (Visual Basic)
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
ms.openlocfilehash: 212ce1f06a01c39acbce43d8d069dae3526b1b4d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963545"
---
# <a name="mid-statement"></a>Mid Deyimi
Bir `String` değişkende belirtilen sayıda karakteri, başka bir dizeden karakterlerle değiştirir.  
  
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
 Gerekli. `String` Değiştirilecek değişkenin adı.  
  
 `Start`  
 Gerekli. `Integer`ifadesini. Metnin yerini değiştirme `Target` işleminin başladığı karakter konumu. `Start`tek tabanlı bir dizin kullanır.  
  
 `Length`  
 İsteğe bağlı. `Integer`ifadesini. Değiştirilecek karakter sayısı. Atlanırsa, tümü `String` kullanılır.  
  
 `StringExpression`  
 Gerekli. `String`bölümünün yerini alan ifade `Target`.  
  
## <a name="exceptions"></a>Özel Durumlar  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|`Start`< = 0 veya `Length` < 0.|  
  
## <a name="remarks"></a>Açıklamalar  
 Değiştirilmekte olan karakter sayısı her zaman içindeki `Target`karakter sayısından daha küçüktür veya eşittir.  
  
 Visual Basic bir <xref:Microsoft.VisualBasic.Strings.Mid%2A> işleve `Mid` ve ifadeye sahiptir. Bu öğeler her ikisi de bir dizedeki belirtilen sayıda karakter üzerinde çalışır, ancak `Mid` işlev, `Mid` ifadenin karakterleri değiştirdiği sırada karakterleri döndürür. Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Strings.Mid%2A>.  
  
> [!NOTE]
> Visual Basic `MidB` önceki sürümleri, bir alt dizeyi karakterler yerine bayt olarak değiştirir. Esas olarak çift baytlı karakter kümesi (DBCS) uygulamalarında dize dönüştürmek için kullanılır. Tüm Visual Basic dizeleri Unicode ve `MidB` artık desteklenmiyor.  
  
## <a name="example"></a>Örnek  
 Bu örnek, `Mid` bir dize değişkeninde belirtilen sayıda karakteri başka bir dizeden karakterler ile değiştirmek için ifadesini kullanır.  
  
 [!code-vb[VbVbalrStrings#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#5)]  
  
## <a name="requirements"></a>Gereksinimler  
 **Uzayına** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Modül:** `Strings`  
  
 **Derleme** Visual Basic Çalışma Zamanı Kitaplığı (Microsoft.VisualBasic.dll içinde)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- [Dizeler](../../../visual-basic/programming-guide/language-features/strings/index.md)
- [Visual Basic dizelere giriş](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
