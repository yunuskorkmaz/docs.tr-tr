---
description: 'Hakkında daha fazla bilgi edinin: Işlev Ifadesi (Visual Basic)'
title: Function İfadesi
ms.date: 07/20/2015
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
ms.openlocfilehash: bef5db7f167b615c2a0c20539521c186683da985
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666023"
---
# <a name="function-expression-visual-basic"></a>İşlev İfadesi (Visual Basic)

Bir işlev lambda ifadesi tanımlayan parametreleri ve kodu bildirir.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
```  
  
## <a name="parts"></a>Bölümler  
  
|Süre|Tanım|  
|---|---|  
|`parameterlist`|İsteğe bağlı. Bu yordamın parametrelerini temsil eden yerel değişken adlarının bir listesi. Liste boş olduğunda bile parantezler mevcut olmalıdır. Bkz. [parametre listesi](../statements/parameter-list.md).|  
|`expression`|Gereklidir. Tek bir ifade. İfadenin türü, işlevin dönüş türüdür.|  
|`statements`|Gereklidir. Deyimini kullanarak bir değer döndüren deyimlerin listesi `Return` . ( [Return ifadesine](../statements/return-statement.md)bakın.) Döndürülen değerin türü, işlevin dönüş türüdür.|  
  
## <a name="remarks"></a>Açıklamalar  

 *Lambda ifadesi* , bir değeri hesaplayan ve döndüren bir ad olmayan bir işlevdir. Bir lambda ifadesini, için bağımsız değişken dışında bir temsilci türü kullanabileceğiniz her yerde kullanabilirsiniz `RemoveHandler` . Temsilciler ve temsilcilerle lambda ifadelerinin kullanımı hakkında daha fazla bilgi için bkz. [Delegate deyimi](../statements/delegate-statement.md) ve [gevşek temsilci dönüştürme](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md).  
  
## <a name="lambda-expression-syntax"></a>Lambda İfadesi Sözdizimi  

 Bir lambda ifadesinin sözdizimi, standart bir işleve benzer. Farklar şunlardır:  
  
- Lambda ifadesinin adı yoktur.  
  
- Lambda ifadelerinin veya gibi değiştiriciler olamaz `Overloads` `Overrides` .  
  
- Lambda ifadeleri `As` , işlevin dönüş türünü belirlemek için bir yan tümce kullanmaz. Bunun yerine, tür, tek satırlık lambda ifadesinin gövdesinin değerlendirilen değerden veya çok satırlı lambda ifadesinin dönüş değerine göre algılanır. Örneğin, tek satırlık bir lambda ifadesinin gövdesi ise, `Where cust.City = "London"` dönüş türü olur `Boolean` .  
  
- Tek satırlık lambda ifadesinin gövdesi deyim değil bir ifade olmalıdır. Gövde, bir işlev yordamının bir çağrısından oluşabilir, ancak Sub yordamına çağrı olamaz.  
  
- Tüm parametrelerin belirtilmiş veri türleri olmalıdır veya hepsi çıkarsanmalıdır.  
  
- İsteğe bağlı ve ParamArray parametrelerine izin verilmez.  
  
- Genel parametrelere izin verilmiyor.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örneklerde basit lambda ifadeleri oluşturmanın iki yolu gösterilmektedir. İlki, `Dim` işlev için bir ad sağlamak üzere bir kullanır. İşlevini çağırmak için, parametresi için bir değer gönderin.  
  
 [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
## <a name="example"></a>Örnek  

 Alternatif olarak, işlevini aynı anda bildirebilir ve çalıştırabilirsiniz.  
  
 [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
## <a name="example"></a>Örnek  

 Aşağıda, bağımsız değişkenini artıran ve değeri döndüren bir lambda ifadesinin örneği verilmiştir. Örnek, bir işlev için hem tek satırlı hem çok satırlı lambda ifadesi sözdizimini gösterir. Daha fazla örnek için bkz. [lambda ifadeleri](../../programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]  
  
## <a name="example"></a>Örnek  

 Lambda ifadeleri Language-Integrated sorgusunda (LINQ) sorgu işleçlerinin birçoğunu alt olarak kullanır ve Yöntem tabanlı sorgularda açıkça kullanılabilir. Aşağıdaki örnek tipik bir LINQ sorgusunu ve ardından sorgunun yöntem biçimine çevirisini gösterir.  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 Sorgu yöntemleri hakkında daha fazla bilgi için bkz. [sorgular](../queries/index.md). Standart sorgu işleçleri hakkında daha fazla bilgi için bkz. [Standart sorgu Işleçlerine genel bakış](../../programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Function Deyimi](../statements/function-statement.md)
- [Lambda Ifadeleri](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [İşleçler ve Ifadeler](../../programming-guide/language-features/operators-and-expressions/index.md)
- [Deyimler](../../programming-guide/language-features/statements.md)
- [Değer Karşılaştırmaları](../../programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [Boole Ifadeleri](../../programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [If İşleci](if-operator.md)
- [Gevşek Temsilci Dönüştürme](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
