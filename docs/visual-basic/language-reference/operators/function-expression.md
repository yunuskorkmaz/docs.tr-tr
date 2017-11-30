---
title: "İşlev İfadesi (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e1d9d1223b340b2172c12bd8c2f364e314e764b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="function-expression-visual-basic"></a>İşlev İfadesi (Visual Basic)
Parametreleri ve işlev lambda ifadesi tanımlamak kod bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`parameterlist`|İsteğe bağlı. Bu yordam parametreleri temsil eden yerel değişken adları listesi. Parantez listesi boş olsa bile mevcut olması gerekir. Bkz: [parametre listesi](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`expression`|Gerekli. Tek bir ifade. İşlevinin dönüş türü ifade türüdür.|  
|`statements`|Gerekli. Kullanarak bir değer döndürür deyimleri listesini `Return` deyimi. (Bkz [dönüş deyimi](../../../visual-basic/language-reference/statements/return-statement.md).) İşlevinin dönüş türü döndürülen değer türüdür.|  
  
## <a name="remarks"></a>Açıklamalar  
 A *lambda ifadesi* hesaplar ve bir değer döndüren bir ad olmadan bir işlev değil. Lambda ifadesi kullanabileceğiniz her yerde bir temsilci türü dışında bağımsız değişken olarak kullanabileceğiniz `RemoveHandler`. Temsilciler ve temsilciler ile lambda ifadeleri kullanma hakkında daha fazla bilgi için bkz: [temsilci deyimi](../../../visual-basic/language-reference/statements/delegate-statement.md) ve [gevşek temsilci dönüşümü](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).  
  
## <a name="lambda-expression-syntax"></a>Lambda İfadesi Sözdizimi  
 Lambda ifadesi sözdizimi, standart bir işlev benzer. Farkları aşağıdaki gibidir:  
  
-   Lambda ifadesi bir adı yok.  
  
-   Lambda ifadeleri olamaz değiştiriciler, gibi `Overloads` veya `Overrides`.  
  
-   Lambda ifadeleri kullanma bir `As` işlevin dönüş türünü atamak için yan tümcesi. Bunun yerine, türü tek satırlı lambda ifadesi gövdesi değerlendiren değeri veya çok satırlı lambda ifadesi dönüş değerini algılanır. Örneğin, tek satırlı lambda ifadesi gövdesi ise `Where cust.City = "London"`, kendi dönüş türü `Boolean`.  
  
-   Tek satırlı lambda ifadesi gövdesi bir ifade, bir deyim olmalıdır. Gövdesi bir işlev yordam çağrısı, ancak olmayan bir alt yordam çağrısı oluşabilir.  
  
-   Veri türleri veya tüm olayla gerekir ya da tüm parametreleri belirledikten gerekir.  
  
-   İsteğe bağlı ve Paramarray parametreleri izin verilmez.  
  
-   Genel Parametreler izin verilmez.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekler basit lambda ifadeleri oluşturmanın iki yolunu gösterir. İlk kullandığı bir `Dim` işlevi için bir ad vermek için. Bir işlevi çağırmak için parametre için bir değer gönderin.  
  
 [!code-vb[VbVbalrLambdas#1](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_1.vb)]  
  
 [!code-vb[VbVbalrLambdas#2](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_2.vb)]  
  
## <a name="example"></a>Örnek  
 Alternatif olarak, bildirme ve aynı anda işlevi çalıştırın.  
  
 [!code-vb[VbVbalrLambdas#3](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_3.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki bağımsız değişkeni artırır ve değer döndüren bir lambda ifadesi bir örnektir. Aşağıdaki örnekte, hem tek satırlı ve çok satırlı lambda ifadesi sözdizimi işlevi için gösterilir. Daha fazla örnek için bkz: [Lambda ifadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbVbalrLambdas#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_4.vb)]  
  
## <a name="example"></a>Örnek  
 Lambda ifadeleri sorgu işleçleri çoğunu temelini oluşturan [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]ve yöntem temelli sorgular açıkça kullanılabilir. Aşağıdaki örnek gösterilmektedir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] yöntemi biçimine sorgusunun çevirisi tarafından izlenen sorgu.  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 Sorgu yöntemleri hakkında daha fazla bilgi için bkz: [sorguları](../../../visual-basic/language-reference/queries/queries.md). Standart sorgu işleçleri hakkında daha fazla bilgi için bkz: [standart sorgu işleçlerine genel bakış](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Function deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Lambda ifadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [İşleçler ve ifadeler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [Deyimleri](../../../visual-basic/programming-guide/language-features/statements.md)  
 [Değer karşılaştırmaları](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [Boole ifadeleri](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [Varsa işleci](../../../visual-basic/language-reference/operators/if-operator.md)  
 [Gevşek temsilci dönüşümü](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
