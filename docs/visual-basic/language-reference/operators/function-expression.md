---
title: İşlev İfadesi (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
ms.openlocfilehash: 0ab4a77395b478df06f34240212438f3e6e18f6e
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592200"
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
|`statements`|Gerekli. @No__t-0 deyimini kullanarak bir değer döndüren deyimlerin listesi. ( [Return ifadesine](../../../visual-basic/language-reference/statements/return-statement.md)bakın.) Döndürülen değerin türü, işlevin dönüş türüdür.|  
  
## <a name="remarks"></a>Açıklamalar  
 *Lambda ifadesi* , bir değeri hesaplayan ve döndüren bir ad olmayan bir işlevdir. @No__t-0 ' a bir bağımsız değişken hariç olmak üzere, bir temsilci türü kullanabileceğiniz her yerde bir lambda ifadesi kullanabilirsiniz. Temsilciler ve temsilcilerle lambda ifadelerinin kullanımı hakkında daha fazla bilgi için bkz. [Delegate deyimi](../../../visual-basic/language-reference/statements/delegate-statement.md) ve [gevşek temsilci dönüştürme](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).  
  
## <a name="lambda-expression-syntax"></a>Lambda İfadesi Sözdizimi  
 Bir lambda ifadesinin sözdizimi, standart bir işleve benzer. Farklar şunlardır:  
  
- Lambda ifadesinin adı yoktur.  
  
- Lambda ifadelerinde `Overloads` veya `Overrides` gibi değiştiriciler olamaz.  
  
- Lambda ifadeleri, işlevin dönüş türünü belirlemek için `As` yan tümcesi kullanmaz. Bunun yerine, tür, tek satırlık lambda ifadesinin gövdesinin değerlendirilen değerden veya çok satırlı lambda ifadesinin dönüş değerine göre algılanır. Örneğin, tek satırlık bir lambda ifadesinin gövdesi `Where cust.City = "London"` ise, dönüş türü `Boolean` ' dir.  
  
- Tek satırlık lambda ifadesinin gövdesi deyim değil bir ifade olmalıdır. Gövde, bir işlev yordamının bir çağrısından oluşabilir, ancak Sub yordamına çağrı olamaz.  
  
- Tüm parametrelerin belirtilmiş veri türleri olmalıdır veya hepsi çıkarsanmalıdır.  
  
- İsteğe bağlı ve ParamArray parametrelerine izin verilmez.  
  
- Genel parametrelere izin verilmiyor.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örneklerde basit lambda ifadeleri oluşturmanın iki yolu gösterilmektedir. İlki, işlev için bir ad sağlamak üzere `Dim` kullanır. İşlevini çağırmak için, parametresi için bir değer gönderin.  
  
 [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
## <a name="example"></a>Örnek  
 Alternatif olarak, işlevini aynı anda bildirebilir ve çalıştırabilirsiniz.  
  
 [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
## <a name="example"></a>Örnek  
 Aşağıda, bağımsız değişkenini artıran ve değeri döndüren bir lambda ifadesinin örneği verilmiştir. Örnek, bir işlev için hem tek satırlı hem çok satırlı lambda ifadesi sözdizimini gösterir. Daha fazla örnek için bkz. [lambda ifadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]  
  
## <a name="example"></a>Örnek  
 Lambda ifadeleri [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] ' daki sorgu işleçlerinin birçoğunu ve Yöntem tabanlı sorgularda açıkça kullanılabilir. Aşağıdaki örnek tipik bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgusu gösterir ve ardından sorgu yöntem biçimine çeviri izler.  
  
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
