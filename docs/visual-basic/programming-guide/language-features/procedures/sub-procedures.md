---
description: 'Daha fazla bilgi edinin: alt yordamlar (Visual Basic)'
title: Alt yordamlar
ms.date: 07/20/2015
helpviewer_keywords:
- Sub procedures [Visual Basic], about Sub procedures
- statement blocks
- Sub procedures [Visual Basic], calling
- procedures [Visual Basic], calling
- Sub procedures [Visual Basic], syntax
- Sub procedures
- procedures [Visual Basic], Sub
- syntax [Visual Basic], Sub procedures
ms.assetid: 6a0a4958-ed0a-4d3d-8d31-0772c82bda58
ms.openlocfilehash: fe9d26fb2d18fbd29820af7aca96b826d7b45d0b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466516"
---
# <a name="sub-procedures-visual-basic"></a>Alt yordamlar (Visual Basic)

`Sub`Yordam, ve deyimleri içine alınmış Visual Basic deyimlerinin bir dizisidir `Sub` `End Sub` . `Sub`Yordam bir görevi gerçekleştirir ve ardından çağıran koda denetim döndürür, ancak çağıran koda bir değer döndürmez.

Yordamın her çağrılışında, deyimleri, deyiminden sonraki ilk yürütülebilir deyim `Sub` ve ilk, veya ile biten ifadesiyle başlayarak yürütülür `End Sub` `Exit Sub` `Return` .

`Sub`Modüller, sınıflar ve yapılar için bir yordam tanımlayabilirsiniz. Varsayılan olarak, bu, sizin `Public` tanımladığınız modüle, sınıfa veya yapıya erişimi olan uygulamanızdaki herhangi bir yerden çağırabilmeniz anlamına gelir. Terimi *yöntemi* , `Sub` `Function` tanımlama modülünün, sınıfın veya yapının dışından erişilen bir veya yordamını açıklar. Daha fazla bilgi için bkz. [yordamlar](./index.md).

`Sub`Yordam, çağıran kod tarafından buna geçirilen sabitler, değişkenler veya ifadeler gibi bağımsız değişkenler alabilir.

## <a name="declaration-syntax"></a>Bildirim söz dizimi

Bir yordamı bildirmek için sözdizimi `Sub` aşağıdaki gibidir:

```vb
[modifiers] Sub SubName[(parameterList)]
    ' Statements of the Sub procedure.
End Sub
```

, `modifiers` Erişim düzeyini ve aşırı yükleme, geçersiz kılma, paylaşma ve gölgeleme hakkında bilgileri belirtebilir. Daha fazla bilgi için bkz. [Sub deyimidir](../../../language-reference/statements/sub-statement.md).

## <a name="parameter-declaration"></a>Parametre bildirimi

Her yordam parametresini, parametre adını ve veri türünü belirterek bir değişkeni nasıl bildirdiğinizin benzer şekilde bildirirsiniz. Ayrıca, geçen mekanizmayı ve parametrenin isteğe bağlı veya bir parametre dizisi olduğunu belirtebilirsiniz.

Parametre listesindeki her bir parametre için sözdizimi aşağıdaki gibidir:

```vb
[Optional] [ByVal | ByRef] [ParamArray] parameterName As DataType
```

Parametre isteğe bağlı ise, bildiriminin bir parçası olarak bir varsayılan değer de belirtmeniz gerekir. Varsayılan bir değer belirtmek için sözdizimi aşağıdaki gibidir:

```vb
Optional [ByVal | ByRef]  parameterName As DataType = defaultValue
```

### <a name="parameters-as-local-variables"></a>Yerel değişkenler olarak parametreler

Denetim yordama geçtiğinde, her bir parametre yerel bir değişken olarak değerlendirilir. Bu, yaşam süresinin prosedürünyle aynı olduğu ve kapsamı tüm yordam olduğu anlamına gelir.

## <a name="calling-syntax"></a>Çağırma sözdizimi

`Sub`Tek başına çağırma ifadesiyle bir yordamı açık olarak çağırabilirsiniz. Bir ifadede adını kullanarak çağrılamaz. İsteğe bağlı olmayan tüm bağımsız değişkenlerin değerlerini sağlamanız gerekir ve bağımsız değişken listesini parantez içine almalısınız. Herhangi bir bağımsız değişken sağlanmazsa, isteğe bağlı olarak ayraçları atlayabilirsiniz. `Call`Anahtar sözcüğünün kullanımı isteğe bağlıdır, ancak önerilmez.

Bir yordama yapılan çağrının sözdizimi aşağıdaki gibidir `Sub` :

```vb
[Call] SubName[(argumentlist)]
```

Bir `Sub` yöntemi, kendisini tanımlayan sınıfın dışından çağırabilirsiniz. İlk olarak, `New` sınıfının bir örneğini oluşturmak veya sınıfının bir örneğini döndüren bir yöntemi çağırmak için anahtar sözcüğünü kullanmanız gerekir. Daha fazla bilgi için bkz. [New Operator](../../../language-reference/operators/new-operator.md). Daha sonra, örnek nesnesinde yöntemini çağırmak için aşağıdaki sözdizimini kullanabilirsiniz `Sub` :

```vb
object.MethodName[(argumentList)]
```

### <a name="illustration-of-declaration-and-call"></a>Bildirim ve çağrı gösterimi

Aşağıdaki `Sub` yordam, bilgisayar işlecine uygulamanın hangi görevi gerçekleştirmesini söyler ve ayrıca bir zaman damgası görüntüler. Her görevin başlangıcında bu kodu çoğaltmak yerine, uygulama yalnızca `tellOperator` çeşitli konumlardan çağrı yapılır. Her çağrı, `task` başlatılmış görevi tanımlayan bağımsız değişkende bir dize geçirir.

[!code-vb[VbVbcnProcedures#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#2)]

Aşağıdaki örnekte, için tipik bir çağrı gösterilmektedir `tellOperator` .

[!code-vb[VbVbcnProcedures#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#3)]

## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [İşlev Yordamları](./function-procedures.md)
- [Özellik Yordamları](./property-procedures.md)
- [İşleç Yordamları](./operator-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Sub Deyimi](../../../language-reference/statements/sub-statement.md)
- [Nasıl yapılır: Değer Döndürmeyen Bir Yordam Çağırma](./how-to-call-a-procedure-that-does-not-return-a-value.md)
- [Nasıl yapılır: Olay İşleyicisi Çağırma (Visual Basic)](./how-to-call-an-event-handler.md)
