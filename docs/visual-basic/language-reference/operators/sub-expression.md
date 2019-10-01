---
title: Alt İfade (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
ms.openlocfilehash: 2330b410f54b54d8f6cb7d8ad6f9b39a3f4d31bc
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701342"
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
|`parameterlist`|İsteğe bağlı. Yordamın parametrelerini temsil eden yerel değişken adlarının bir listesi. Liste boş olduğunda bile parantezler mevcut olmalıdır. Daha fazla bilgi için bkz. [parametre listesi](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`statement`|Gerekli. Tek bir ifade.|  
|`statements`|Gerekli. Deyimler listesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 *Lambda ifadesi* , bir ada sahip olmayan ve bir veya daha fazla deyimi yürüten bir altyordam. @No__t-0 ' a bir bağımsız değişken hariç, bir temsilci türü kullanabileceğiniz her yerde lambda ifadesini kullanabilirsiniz. Temsilciler ve temsilcilerle lambda ifadelerinin kullanımı hakkında daha fazla bilgi için bkz. [Delegate deyimi](../../../visual-basic/language-reference/statements/delegate-statement.md) ve [gevşek temsilci dönüştürme](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).  
  
## <a name="lambda-expression-syntax"></a>Lambda İfadesi Sözdizimi  
 Bir lambda ifadesinin sözdizimi, standart bir alt yordamın sözdizimine benzer. Farklar şunlardır:  
  
- Lambda ifadesinin adı yoktur.  
  
- Lambda ifadesi `Overloads` veya `Overrides` gibi bir değiştiriciye sahip olamaz.  
  
- Tek satırlık lambda ifadesinin gövdesi bir ifade değil, deyim olmalıdır. Gövde, bir alt yordam çağrısından oluşabilir, ancak bir işlev yordamına çağrı değildir.  
  
- Bir lambda ifadesinde, tüm parametrelerin belirtilen veri türleri olmalıdır veya tüm parametrelerin çıkarsanmalıdır.  
  
- İsteğe bağlı ve `ParamArray` parametrelerine Lambda ifadelerinde izin verilmez.  
  
- Lambda ifadelerinde genel parametrelere izin verilmez.  
  
## <a name="example"></a>Örnek  
 Aşağıda, konsola bir değer yazan bir lambda ifadesinin örneği verilmiştir. Örnek, bir altyordam için hem tek satırlı hem çok satırlı lambda ifadesi sözdizimini gösterir. Daha fazla örnek için bkz. [lambda ifadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Lambda İfadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [İşleçler ve İfadeler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Deyimler](../../../visual-basic/programming-guide/language-features/statements.md)
- [Gevşek Temsilci Dönüştürme](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
