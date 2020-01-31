---
title: İşlev yordamları
ms.date: 07/20/2015
helpviewer_keywords:
- Function procedures
- return values [Visual Basic], function procedures
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], Function procedures
- syntax [Visual Basic], function procedures
ms.assetid: 1b9f632c-553b-4cb6-920a-ded117ead8c0
ms.openlocfilehash: d7a0293e2ec520c2278f67156be56315d1def2b5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76780090"
---
# <a name="function-procedures-visual-basic"></a>İşlev yordamları (Visual Basic)

`Function` yordam, `Function` ve `End Function` deyimlerinin içine alınmış Visual Basic deyimlerinin bir dizisidir. `Function` yordam bir görevi gerçekleştirir ve ardından çağıran koda denetim döndürür. Denetimi döndürdüğünde, çağıran koda de bir değer döndürür.

Yordamın her çağrılışında, deyimleri `Function` deyiminden sonra ilk yürütülebilir deyimden başlayarak ve ilk `End Function`, `Exit Function`veya `Return` ifadesiyle sona ermek üzere çalışır.

Bir modül, sınıf veya yapıda `Function` yordamı tanımlayabilirsiniz. Varsayılan olarak `Public`, bu, uygulamanızı tanımladığınız modüle, sınıfa veya yapıya erişimi olan uygulamanızdaki herhangi bir yerden çağırabilmeniz anlamına gelir.

`Function` yordam, çağıran kod tarafından buna geçirilen sabitler, değişkenler veya ifadeler gibi bağımsız değişkenler alabilir.

## <a name="declaration-syntax"></a>Bildirim söz dizimi

`Function` yordamı bildirmek için sözdizimi aşağıdaki gibidir:

```vb
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType
    [Statements]
End Function
```

*Değiştiriciler* , aşırı yükleme, geçersiz kılma, paylaşma ve gölgeleme ile ilgili erişim düzeyini ve bilgileri belirtebilir. Daha fazla bilgi için bkz. [Işlev açıklaması](../../../language-reference/statements/function-statement.md).

Her parametreyi [alt yordamlar](./sub-procedures.md)için yaptığınız gibi bildirirsiniz.

### <a name="data-type"></a>Veri türü

Her `Function` yordamı her değişken için olduğu gibi bir veri türüne sahiptir. Bu veri türü, `Function` deyimindeki `As` yan tümcesi tarafından belirtilir ve işlevin çağıran koda döndürdüğü değerin veri türünü belirler. Aşağıdaki örnek bildirimlerde bu gösterilmektedir.

```vb
Function Yesterday() As Date
End Function

Function FindSqrt(radicand As Single) As Single
End Function
```

Daha fazla bilgi için bkz. [Işlev deyimindeki](../../../language-reference/statements/function-statement.md)"parçalar".

### <a name="returning-values"></a>Değer döndürme

Çağıran koda geri gönderilen `Function` yordamının değeri, dönüş değeri olarak adlandırılır. Yordam bu değeri iki şekilde döndürür:

- Dönüş değerini belirtmek için `Return` ifadesini kullanır ve denetimi çağıran programa hemen döndürür. Aşağıdaki örnek bunu göstermektedir.

  ```vb
  Function FunctionName [(ParameterList)] As ReturnType
      ' The following statement immediately transfers control back
      ' to the calling code and returns the value of Expression.
      Return Expression
  End Function
  ```

- Yordamın bir veya daha fazla deyiminde kendi işlev adına bir değer atar. Denetim, bir `Exit Function` veya `End Function` deyimleri yürütülene kadar çağıran programa geri dönmez. Aşağıdaki örnek bunu göstermektedir.

  ```vb
  Function FunctionName [(ParameterList)] As ReturnType
      ' The following statement does not transfer control back to the calling code.
      FunctionName = Expression
      ' When control returns to the calling code, Expression is the return value.
  End Function
  ```

İşlev adına dönüş değerinin atanmasından faydalanması, denetimin `Exit Function` veya `End Function` ifadesiyle karşılaşana kadar yordamdan dönmediği avantajdır. Bu, bir ön değer atamanıza ve gerekirse daha sonra ayarlamanıza olanak sağlar.

Değer döndürme hakkında daha fazla bilgi için bkz. [Function deyimleri](../../../language-reference/statements/function-statement.md). Dizileri döndürme hakkında daha fazla bilgi için bkz. [diziler](../arrays/index.md).

## <a name="calling-syntax"></a>Çağırma sözdizimi

Bir `Function` yordamını, adını ve bağımsız değişkenlerini atama deyiminin sağ tarafına ya da bir ifadeye ekleyerek çağırılır. İsteğe bağlı olmayan tüm bağımsız değişkenlerin değerlerini sağlamanız gerekir ve bağımsız değişken listesini parantez içine almalısınız. Herhangi bir bağımsız değişken sağlanmazsa, isteğe bağlı olarak ayraçları atlayabilirsiniz.

`Function` yordam çağrısı için sözdizimi aşağıdaki gibidir.

*lvalue*`=`*fonksiyonadı* `[(` *bağımsız değişkenler listesi* `)]`

`If ((` *fonksiyonadı* `[(` *bağımsız değişkenler listesi* `)] / 3) <=`*ifadesi* `) Then`

Bir `Function` yordamını çağırdığınızda, dönüş değerini kullanmak zorunda değilsiniz. Bunu yapmazsanız, işlevin tüm eylemleri gerçekleştirilir, ancak dönüş değeri yok sayılır. <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> genellikle bu şekilde çağrılır.

### <a name="illustration-of-declaration-and-call"></a>Bildirim ve çağrı gösterimi

Aşağıdaki `Function` yordam, iki tarafa ait değerler verildiğinde, doğru bir üçgenin en uzun tarafını veya hipotenüsü değerini hesaplar.

[!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]

Aşağıdaki örnek `hypotenuse`tipik bir çağrısını gösterir.

[!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]

## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Alt Yordamlar](./sub-procedures.md)
- [Özellik Yordamları](./property-procedures.md)
- [İşleç Yordamları](./operator-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Function Deyimi](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Nasıl yapılır: Değer Döndüren Bir Yordam Oluşturma](./how-to-create-a-procedure-that-returns-a-value.md)
- [Nasıl yapılır: Bir Yordamdan Değer Döndürme](./how-to-return-a-value-from-a-procedure.md)
- [Nasıl yapılır: Değer Döndüren Bir Yordam Çağırma](./how-to-call-a-procedure-that-returns-a-value.md)
