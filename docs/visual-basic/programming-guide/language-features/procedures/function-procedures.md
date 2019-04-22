---
title: İşlev Yordamları (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Function procedures
- return values [Visual Basic], function procedures
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], Function procedures
- syntax [Visual Basic], function procedures
ms.assetid: 1b9f632c-553b-4cb6-920a-ded117ead8c0
ms.openlocfilehash: 568489d6034316e895cd999801241fa995aadefa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834250"
---
# <a name="function-procedures-visual-basic"></a>İşlev Yordamları (Visual Basic)
A `Function` yordamdır kapsadığı Visual Basic deyimleri bir dizi `Function` ve `End Function` deyimleri. `Function` Yordamı bir görevi gerçekleştirir ve çağıran koda denetimini döndürür. Denetimi geri döndüğünde, ayrıca çağrıldığı koda bir değer döndürür.  
  
 Yordam çağrıldığında, kendi deyimleri çalıştırın, her bir saat sonra yürütülebilir ilk deyimi başlayarak `Function` deyimi ve ilk görmektesiniz `End Function`, `Exit Function`, veya `Return` deyimiyle karşılaşıldı.  
  
 Tanımlayabileceğiniz bir `Function` yordamda bir modül, sınıf veya yapı. Bu `Public` varsayılan olarak, yani çağırabilirsiniz, her yerden uygulamanızdaki modül, sınıf veya yapının, tanımlandığı da erişebilir.  
  
 A `Function` yordamı, sabitleri, değişkenleri veya kendisine çağıran kod tarafından geçirilen ifadeler gibi bir bağımsız değişken alabilir.  
  
## <a name="declaration-syntax"></a>Bildirim Sözdizimi  
 Bildirmek için söz dizimi bir `Function` yordam şu şekildedir:  
  
```vb  
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType  
    [Statements]  
End Function  
```  
  
 *Değiştiriciler* erişim düzeyi ve aşırı yüklemesi, geçersiz kılma, paylaşımı ve gölgeleme ilgili bilgileri belirtebilirsiniz. Daha fazla bilgi için [Function deyimi](../../../../visual-basic/language-reference/statements/function-statement.md).  
  
 Her parametre için yaptığınız gibi bildirdiğiniz [alt yordamlar](./sub-procedures.md).  
  
### <a name="data-type"></a>Veri Türü  
 Her `Function` yordamı sahip bir veri türü, yalnızca olarak her değişken yok. Bu veri türü tarafından belirtilen `As` yan tümcesinde `Function` ifadesi ve işlevin çağrıldığı koda döndürdüğü değer veri türünü belirler. Aşağıdaki örnek bildirimleri bu göstermektedir.  
  
```vb  
Function yesterday() As Date  
End Function  
  
Function findSqrt(ByVal radicand As Single) As Single  
End Function  
```  
  
 Daha fazla bilgi için bkz: "Bölümleri" [Function deyimi](../../../../visual-basic/language-reference/statements/function-statement.md).  
  
## <a name="returning-values"></a>Değerler döndüren  
 Değer bir `Function` yordamı gönderir çağıran koda geri dönüş değeri olarak adlandırılır. Yordam bu değer iki yoldan birini döndürür:  
  
-   Kullandığı `Return` deyimi döndürür ve dönüş değeri belirtmek için çağırma program hemen denetim. Aşağıdaki örnek bunu göstermektedir.  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement immediately transfers control back  
    ' to the calling code and returns the value of Expression.  
    Return Expression  
End Function  
```  
  
-   Bir veya daha fazla deyim yordamın, kendi işlev adı için bir değer atar. Denetim kadar çağıran program döndürmez bir `Exit Function` veya `End Function` deyimi yürütülür. Aşağıdaki örnek bunu göstermektedir.  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement does not transfer control back to the calling code.  
    FunctionName = Expression  
    ' When control returns to the calling code, Expression is the return value.  
End Function  
```  
  
 Dönüş değeri, işlev adını atama bulduğu kadar denetim yordamdan döndürmeyen avantajlarındandır bir `Exit Function` veya `End Function` deyimi. Bu, bir ön değer atamak ve gerekirse daha sonra ayarlamak sağlar.  
  
 Değerler döndüren hakkında daha fazla bilgi için bkz. [Function deyimi](../../../../visual-basic/language-reference/statements/function-statement.md). Dizi döndüren hakkında daha fazla bilgi için bkz [diziler](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="calling-syntax"></a>Arama söz dizimi  
 Çağırdığınızda bir `Function` adı ve bağımsız değişkenler veya işlecin sağ tarafındaki Atama ifadesinin veya bir ifadede ekleyerek yordamı. İsteğe bağlı olmayan tüm bağımsız değişkenler için değerler sağlaması gerekir ve bağımsız değişken listesi parantez içine almalısınız. Hiçbir bağımsız değişken sağlanmadıysa, parantezler isteğe bağlı olarak atlayabilirsiniz.  
  
 Bir çağrı sözdizimi bir `Function` yordam şu şekildedir:  
  
 *lvalue*`=`*functionname* `[(` *argumentlist* `)]`  
  
 `If ((` *FunctionName* `[(` *argumentlist* `)] / 3) <=` *ifadesi* `) Then`  
  
 Çağırdığınızda bir `Function` yordamı sahip olmadığınız dönüş değeri kullanılacak. Bunu yapmazsanız, işlevin tüm eylemlerin gerçekleştirildiğinden, ancak dönüş değeri yok sayılır. <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> Genellikle bu şekilde adlandırılır.  
  
### <a name="illustration-of-declaration-and-call"></a>Bildirim ve çağrı gösterimi  
 Aşağıdaki `Function` yordamı, en uzun kenar veya, diğer iki yüz için değerlerine dik üçgenin, hipotenüsü hesaplar.  
  
 [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
 Aşağıdaki örnek, tipik bir çağrı gösterir `hypotenuse`.  
  
 [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Alt Yordamlar](./sub-procedures.md)
- [Özellik Yordamları](./property-procedures.md)
- [İşleç Yordamları](./operator-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Function Deyimi](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Nasıl yapılır: Bir değer döndüren bir yordam oluşturma](./how-to-create-a-procedure-that-returns-a-value.md)
- [Nasıl yapılır: Bir yordamdan değer döndürme](./how-to-return-a-value-from-a-procedure.md)
- [Nasıl yapılır: Bir değer döndüren bir yordam çağırma](./how-to-call-a-procedure-that-returns-a-value.md)
