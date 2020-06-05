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
ms.openlocfilehash: b0ba96a875fd8785e45eee565beefe4b961ffc9d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388757"
---
# <a name="function-procedures-visual-basic"></a>İşlev yordamları (Visual Basic)

`Function`Yordam, ve deyimleri içine alınmış Visual Basic deyimlerinin bir dizisidir `Function` `End Function` . `Function`Yordam bir görevi gerçekleştirir ve ardından çağıran koda denetim döndürür. Denetimi döndürdüğünde, çağıran koda de bir değer döndürür.

Yordamın her çağrılışında deyimleri, deyiminden sonra ilk yürütülebilir deyimden başlayarak `Function` ve ilk `End Function` , `Exit Function` , veya ifadesiyle sona ermek üzere çalışır `Return` .

`Function`Modül, sınıf veya yapıda bir yordam tanımlayabilirsiniz. Bu, `Public` Varsayılan olarak sizin tanımladığınız modüle, sınıfa veya yapıya erişimi olan uygulamanızdaki herhangi bir yerden çağırabilmeniz anlamına gelir.

`Function`Yordam, çağıran kod tarafından buna geçirilen sabitler, değişkenler veya ifadeler gibi bağımsız değişkenler alabilir.

## <a name="declaration-syntax"></a>Bildirim söz dizimi

Bir yordamı bildirmek için sözdizimi `Function` aşağıdaki gibidir:

```vb
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType
    [Statements]
End Function
```

*Değiştiriciler* , aşırı yükleme, geçersiz kılma, paylaşma ve gölgeleme ile ilgili erişim düzeyini ve bilgileri belirtebilir. Daha fazla bilgi için bkz. [Işlev açıklaması](../../../language-reference/statements/function-statement.md).

Her parametreyi [alt yordamlar](./sub-procedures.md)için yaptığınız gibi bildirirsiniz.

### <a name="data-type"></a>Veri türü

Her `Function` yordamın, her değişken için olduğu gibi bir veri türü vardır. Bu veri türü, `As` deyimindeki yan tümce tarafından belirtilir `Function` ve işlevin çağıran koda döndürdüğü değerin veri türünü belirler. Aşağıdaki örnek bildirimlerde bu gösterilmektedir.

```vb
Function Yesterday() As Date
End Function

Function FindSqrt(radicand As Single) As Single
End Function
```

Daha fazla bilgi için bkz. [Işlev deyimindeki](../../../language-reference/statements/function-statement.md)"parçalar".

### <a name="returning-values"></a>Değer döndürme

`Function`Çağıran koda geri gönderen bir yordamın değeri, dönüş değeri olarak adlandırılır. Yordam bu değeri iki şekilde döndürür:

- `Return`Dönüş değerini belirtmek için ifadesini kullanır ve denetimi çağıran programa hemen döndürür. Aşağıdaki örnek bunu göstermektedir.

  ```vb
  Function FunctionName [(ParameterList)] As ReturnType
      ' The following statement immediately transfers control back
      ' to the calling code and returns the value of Expression.
      Return Expression
  End Function
  ```

- Yordamın bir veya daha fazla deyiminde kendi işlev adına bir değer atar. Denetim, bir `Exit Function` veya deyimleri yürütülene kadar çağıran programa geri dönmez `End Function` . Aşağıdaki örnek bunu göstermektedir.

  ```vb
  Function FunctionName [(ParameterList)] As ReturnType
      ' The following statement does not transfer control back to the calling code.
      FunctionName = Expression
      ' When control returns to the calling code, Expression is the return value.
  End Function
  ```

İşlev adına dönüş değeri atamanın avantajı, denetimin bir veya ifadesiyle karşılaşana kadar yordamdan dönmediği avantajdır `Exit Function` `End Function` . Bu, bir ön değer atamanıza ve gerekirse daha sonra ayarlamanıza olanak sağlar.

Değer döndürme hakkında daha fazla bilgi için bkz. [Function deyimleri](../../../language-reference/statements/function-statement.md). Dizileri döndürme hakkında daha fazla bilgi için bkz. [diziler](../arrays/index.md).

## <a name="calling-syntax"></a>Çağırma sözdizimi

Bir `Function` yordamı, adını ve bağımsız değişkenlerini atama deyiminin sağ tarafına ya da bir ifadeye ekleyerek çağırılır. İsteğe bağlı olmayan tüm bağımsız değişkenlerin değerlerini sağlamanız gerekir ve bağımsız değişken listesini parantez içine almalısınız. Herhangi bir bağımsız değişken sağlanmazsa, isteğe bağlı olarak ayraçları atlayabilirsiniz.

Bir yordama yapılan çağrının sözdizimi aşağıdaki gibidir `Function` .

*lvalue* `=` *fonksiyonadı* `[(` *bağımsız değişkenler listesi*    `)]`

`If ((`*fonksiyonadı* `[(` *bağımsız değişkenler listesi* `)] / 3) <=` *ifade*  `) Then`

Bir `Function` yordamı çağırdığınızda, dönüş değerini kullanmak zorunda değilsiniz. Bunu yapmazsanız, işlevin tüm eylemleri gerçekleştirilir, ancak dönüş değeri yok sayılır. <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>genellikle bu şekilde çağırılır.

### <a name="illustration-of-declaration-and-call"></a>Bildirim ve çağrı gösterimi

Aşağıdaki `Function` yordam, iki kenarı için değerler verildiğinde, doğru bir üçgenin en uzun tarafını veya hipotenüsü değerini hesaplar.

[!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]

Aşağıdaki örnekte, için tipik bir çağrı gösterilmektedir `hypotenuse` .

[!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]

## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Alt Yordamlar](./sub-procedures.md)
- [Özellik Yordamları](./property-procedures.md)
- [İşleç Yordamları](./operator-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Function Deyimi](../../../language-reference/statements/function-statement.md)
- [Nasıl yapılır: Değer Döndüren Bir Yordam Oluşturma](./how-to-create-a-procedure-that-returns-a-value.md)
- [Nasıl yapılır: Bir Yordamdan Değer Döndürme](./how-to-return-a-value-from-a-procedure.md)
- [Nasıl yapılır: Değer Döndüren Bir Yordam Çağırma](./how-to-call-a-procedure-that-returns-a-value.md)
