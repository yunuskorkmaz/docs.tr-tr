---
title: İşlev İfadesi
ms.date: 07/20/2015
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
ms.openlocfilehash: d14d7c9bc701b5e06c51202c07c3b79832aba7cc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331077"
---
# <a name="function-expression-visual-basic"></a>İşlev İfadesi (Visual Basic)
Bir işlev lambda ifadesi tanımlayan parametreleri ve kodu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`parameterlist`|İsteğe bağlı. Bu yordamın parametrelerini temsil eden yerel değişken adlarının bir listesi. Liste boş olduğunda bile parantezler mevcut olmalıdır. Bkz. [parametre listesi](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`expression`|Gerekli. Tek bir ifade. İfadenin türü, işlevin dönüş türüdür.|  
|`statements`|Gerekli. `Return` deyimini kullanarak bir değer döndüren deyimlerin listesi. ( [Return ifadesine](../../../visual-basic/language-reference/statements/return-statement.md)bakın.) Döndürülen değerin türü, işlevin dönüş türüdür.|  
  
## <a name="remarks"></a>Açıklamalar  
 *Lambda ifadesi* , bir değeri hesaplayan ve döndüren bir ad olmayan bir işlevdir. Bir lambda ifadesini, `RemoveHandler`bir bağımsız değişken hariç, temsilci türü kullanabileceğiniz her yerde kullanabilirsiniz. Temsilciler ve temsilcilerle lambda ifadelerinin kullanımı hakkında daha fazla bilgi için bkz. [Delegate deyimi](../../../visual-basic/language-reference/statements/delegate-statement.md) ve [gevşek temsilci dönüştürme](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).  
  
## <a name="lambda-expression-syntax"></a>Lambda İfadesi Sözdizimi  
 Bir lambda ifadesinin sözdizimi, standart bir işleve benzer. Farklar şunlardır:  
  
- Lambda ifadesinin adı yoktur.  
  
- Lambda ifadelerinde `Overloads` veya `Overrides`gibi değiştiriciler olamaz.  
  
- Lambda ifadeleri, işlevin dönüş türünü belirlemek için bir `As` yan tümcesi kullanmaz. Bunun yerine, tür, tek satırlık lambda ifadesinin gövdesinin değerlendirilen değerden veya çok satırlı lambda ifadesinin dönüş değerine göre algılanır. Örneğin, tek satırlık bir lambda ifadesinin gövdesi `Where cust.City = "London"`, dönüş türü `Boolean`.  
  
- Tek satırlık lambda ifadesinin gövdesi deyim değil bir ifade olmalıdır. Gövde, bir işlev yordamının bir çağrısından oluşabilir, ancak Sub yordamına çağrı olamaz.  
  
- Tüm parametrelerin belirtilmiş veri türleri olmalıdır veya hepsi çıkarsanmalıdır.  
  
- İsteğe bağlı ve ParamArray parametrelerine izin verilmez.  
  
- Genel parametrelere izin verilmiyor.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örneklerde basit lambda ifadeleri oluşturmanın iki yolu gösterilmektedir. İlki, işlev için bir ad sağlamak üzere bir `Dim` kullanır. İşlevini çağırmak için, parametresi için bir değer gönderin.  
  
 [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
## <a name="example"></a>Örnek  
 Alternatif olarak, işlevini aynı anda bildirebilir ve çalıştırabilirsiniz.  
  
 [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
## <a name="example"></a>Örnek  
 Aşağıda, bağımsız değişkenini artıran ve değeri döndüren bir lambda ifadesinin örneği verilmiştir. Örnek, bir işlev için hem tek satırlı hem çok satırlı lambda ifadesi sözdizimini gösterir. Daha fazla örnek için bkz. [lambda ifadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]  
  
## <a name="example"></a>Örnek  
 Lambda ifadeleri [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]içindeki sorgu işleçlerinin birçoğunu daha fazla kullanır ve Yöntem tabanlı sorgularda açık bir şekilde kullanılabilir. Aşağıdaki örnek tipik bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorguyu ve ardından sorgunun yöntem biçimine çevirisini gösterir.  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 Sorgu yöntemleri hakkında daha fazla bilgi için bkz. [sorgular](../../../visual-basic/language-reference/queries/index.md). Standart sorgu işleçleri hakkında daha fazla bilgi için bkz. [Standart sorgu Işleçlerine genel bakış](../../programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)
- [Lambda İfadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [İşleçler ve İfadeler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Deyimler](../../../visual-basic/programming-guide/language-features/statements.md)
- [Değer Karşılaştırmaları](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [Boole İfadeleri](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [If İşleci](../../../visual-basic/language-reference/operators/if-operator.md)
- [Gevşek Temsilci Dönüştürme](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
