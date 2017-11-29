---
title: "İşlev Yordamları (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Function procedures
- return values [Visual Basic], function procedures
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], Function procedures
- syntax [Visual Basic], function procedures
ms.assetid: 1b9f632c-553b-4cb6-920a-ded117ead8c0
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9520a6555e65fd801a5c40d40748028e04a10739
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="function-procedures-visual-basic"></a>İşlev Yordamları (Visual Basic)
A `Function` yordamdır bir dizi [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] deyimleri içine tarafından `Function` ve `End Function` deyimleri. `Function` Yordamı bir görevi gerçekleştirir ve çağrıyı yapan kod denetimini döndürür. Denetim geri döndüğünde, çağrıyı yapan kod de bir değer döndürür.  
  
 Yordam çağrıldığında çalıştırmak, kendi deyimleri her zaman ilk yürütülebilir deyimi sonra başlayarak `Function` deyimi ve ilk ile bitiş `End Function`, `Exit Function`, veya `Return` deyimiyle karşılaşıldı.  
  
 Tanımlayabileceğiniz bir `Function` modülü, sınıf veya yapı yordamda. Bu `Public` varsayılan olarak, yani çağırabilirsiniz onu yerden modülü, sınıf veya yapı içinde tanımlanan bu erişimi, uygulamanızda.  
  
 A `Function` yordamı sabitleri, değişkenleri veya kendisine çağrıyı yapan kod tarafından geçirilen ifadeler gibi bağımsız değişkenleri alabilir.  
  
## <a name="declaration-syntax"></a>Bildirim Sözdizimi  
 Bildirme sözdizimi bir `Function` yordam aşağıdaki gibidir:  
  
```vb  
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType  
    [Statements]  
End Function  
```  
  
 *Değiştiricileri* erişim düzeyini ve aşırı yüklemesi, geçersiz kılma, paylaşımı ve gölgeleme ilgili bilgileri belirtebilirsiniz. Daha fazla bilgi için bkz: [Function deyimi](../../../../visual-basic/language-reference/statements/function-statement.md).  
  
 Her bir parametreyi yapmak için aynı şekilde bildirme [alt yordamlar](./sub-procedures.md).  
  
### <a name="data-type"></a>Veri Türü  
 Her `Function` yordamı sahip bir veri türü, yalnızca olarak her değişken yapar. Bu veri türü tarafından belirtilen `As` yan tümcesinde `Function` deyimi ve onu işlevi çağıran kodu döndürür değerinin veri türü belirler. Aşağıdaki örnek bildirimlerini bu gösterilmektedir.  
  
```vb  
Function yesterday() As Date  
End Function  
  
Function findSqrt(ByVal radicand As Single) As Single  
End Function  
```  
  
 Daha fazla bilgi için bkz: "Bölümleri" [Function deyimi](../../../../visual-basic/language-reference/statements/function-statement.md).  
  
## <a name="returning-values"></a>Dönüş değerleri  
 Değer bir `Function` yordamı gönderir çağıran kodu geri dönüş değerini çağrılır. Yordamın bu değer iki yoldan biriyle döndürür:  
  
-   Kullandığı `Return` döndürür ve dönüş değeri belirtmek için deyimi kontrol hemen çağıran program. Aşağıdaki örnek bunu göstermektedir.  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement immediately transfers control back  
    ' to the calling code and returns the value of Expression.  
    Return Expression  
End Function  
```  
  
-   Yordamın bir veya daha fazla deyimlerinde kendi işlev adı değeri atar. Çağıran program kadar denetim döndürmez bir `Exit Function` veya `End Function` deyimi gerçekleştirilir. Aşağıdaki örnek bunu göstermektedir.  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement does not transfer control back to the calling code.  
    FunctionName = Expression  
    ' When control returns to the calling code, Expression is the return value.  
End Function  
```  
  
 Dönüş değeri işlev adını atama avantajı bulduğu kadar denetim yordamdan döndürmüyor olan bir `Exit Function` veya `End Function` deyimi. Bu, başlangıç değeri atayın ve gerekirse daha sonra ayarlamak sağlar.  
  
 Dönüş değerleri hakkında daha fazla bilgi için bkz: [Function deyimi](../../../../visual-basic/language-reference/statements/function-statement.md). Diziler döndürme hakkında daha fazla bilgi için bkz: [diziler](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="calling-syntax"></a>Arama sözdizimi  
 Çağırmayı bir `Function` adını ve bağımsız değişkenler ya da Atama ifadesinin veya bir ifade sağ taraftaki ekleyerek yordamı. İsteğe bağlı olmayan tüm bağımsız değişkenler için değerler sağlayın ve bağımsız değişken listesi parantez içine alın. Bağımsız değişkenler sağlandıysa, isteğe bağlı olarak parantez atlayabilirsiniz.  
  
 Çağrı sözdizimi bir `Function` yordam aşağıdaki gibidir:  
  
 *lvalue*`=`*functionname* `[(` *bağımsızdeğişkenListesi*    `)]`  
  
 `If ((`*functionname* `[(` *bağımsızdeğişkenListesi* `)] / 3) <=` *ifade*  `) Then`  
  
 Çağırdığınızda bir `Function` yordamı, sahip olmadığınız dönüş değeri kullanılacak. Bunu yapmazsanız, işlevin tüm eylemler gerçekleştirilir, ancak dönüş değeri yoksayılır. <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>Genelde bu şekilde denir.  
  
### <a name="illustration-of-declaration-and-call"></a>Bildirim ve çağrı çizimi  
 Aşağıdaki `Function` yordamı en uzun taraf veya diğer iki kenara için değerlerine göre bir sağ üçgen hipotenüsü hesaplar.  
  
 [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/function-procedures_1.vb)]  
  
 Aşağıdaki örnek tipik bir çağrı gösterilmektedir `hypotenuse`.  
  
 [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/function-procedures_2.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yordamları](./index.md)  
 [Alt yordamlar](./sub-procedures.md)  
 [Özellik yordamları](./property-procedures.md)  
 [İşleç yordamları](./operator-procedures.md)  
 [Parametreler ve bağımsız değişkenler](./procedure-parameters-and-arguments.md)  
 [Function deyimi](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [Nasıl yapılır: değer döndüren bir yordam oluşturma](./how-to-create-a-procedure-that-returns-a-value.md)  
 [Nasıl yapılır: bir yordamdan değer döndürme](./how-to-return-a-value-from-a-procedure.md)  
 [Nasıl yapılır: değer döndüren bir yordam çağırma](./how-to-call-a-procedure-that-returns-a-value.md)
