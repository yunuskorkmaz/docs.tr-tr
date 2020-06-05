---
title: Sub İfadesi
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
ms.openlocfilehash: f862730220d0595faecaa915b1eaad2a3cdc0053
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406325"
---
# <a name="sub-expression-visual-basic"></a>Alt İfade (Visual Basic)
Bir altyordam lambda ifadesi tanımlayan parametreleri ve kodu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Sub ( [ parameterlist ] ) statement  
- or -  
Sub ( [ parameterlist ] )  
  [ statements ]  
End Sub  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`parameterlist`|İsteğe bağlı. Yordamın parametrelerini temsil eden yerel değişken adlarının bir listesi. Liste boş olduğunda bile parantezler mevcut olmalıdır. Daha fazla bilgi için bkz. [parametre listesi](../statements/parameter-list.md).|  
|`statement`|Gereklidir. Tek bir ifade.|  
|`statements`|Gereklidir. Deyimler listesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 *Lambda ifadesi* , bir ada sahip olmayan ve bir veya daha fazla deyimi yürüten bir altyordam. Bir lambda ifadesini, için bağımsız değişken dışında bir temsilci türü kullanabileceğiniz her yerde kullanabilirsiniz `RemoveHandler` . Temsilciler ve temsilcilerle lambda ifadelerinin kullanımı hakkında daha fazla bilgi için bkz. [Delegate deyimi](../statements/delegate-statement.md) ve [gevşek temsilci dönüştürme](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md).  
  
## <a name="lambda-expression-syntax"></a>Lambda İfadesi Sözdizimi  
 Bir lambda ifadesinin sözdizimi, standart bir alt yordamın sözdizimine benzer. Farklar şunlardır:  
  
- Lambda ifadesinin adı yoktur.  
  
- Lambda ifadesi, veya gibi bir değiştiriciye sahip olamaz `Overloads` `Overrides` .  
  
- Tek satırlık lambda ifadesinin gövdesi bir ifade değil, deyim olmalıdır. Gövde, bir alt yordam çağrısından oluşabilir, ancak bir işlev yordamına çağrı değildir.  
  
- Bir lambda ifadesinde, tüm parametrelerin belirtilen veri türleri olmalıdır veya tüm parametrelerin çıkarsanmalıdır.  
  
- Lambda ifadelerinde isteğe bağlı ve `ParamArray` parametrelere izin verilmez.  
  
- Lambda ifadelerinde genel parametrelere izin verilmez.  
  
## <a name="example"></a>Örnek  
 Aşağıda, konsola bir değer yazan bir lambda ifadesinin örneği verilmiştir. Örnek, bir altyordam için hem tek satırlı hem çok satırlı lambda ifadesi sözdizimini gösterir. Daha fazla örnek için bkz. [lambda ifadeleri](../../programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sub Deyimi](../statements/sub-statement.md)
- [Lambda Ifadeleri](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [İşleçler ve Ifadeler](../../programming-guide/language-features/operators-and-expressions/index.md)
- [Deyimler](../../programming-guide/language-features/statements.md)
- [Gevşek Temsilci Dönüştürme](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
