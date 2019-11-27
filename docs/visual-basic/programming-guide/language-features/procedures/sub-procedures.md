---
title: Alt Yordamlar
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
ms.openlocfilehash: 7848dc07d6462622685cdbea92202585f4d5d2c4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352530"
---
# <a name="sub-procedures-visual-basic"></a>Alt Yordamlar (Visual Basic)
`Sub` yordam, `Sub` ve `End Sub` deyimlerinin içine alınmış Visual Basic deyimlerinin bir dizisidir. `Sub` yordamı bir görevi gerçekleştirir ve ardından çağıran koda denetim döndürür, ancak çağıran koda bir değer döndürmez.  
  
 Yordam her çağrıldığında, `Sub` deyiminden sonra ilk yürütülebilir deyimden başlayıp ilk `End Sub`, `Exit Sub`veya `Return` ifadesiyle biten deyimleri yürütülür.  
  
 Modüller, sınıflar ve yapılar için bir `Sub` yordamı tanımlayabilirsiniz. Varsayılan olarak `Public`, bu, sizin tanımladığınız modüle, sınıfa veya yapıya erişimi olan uygulamanızdaki herhangi bir yerden çağırabilmeniz anlamına gelir. *Yöntemi*, tanımlama modülünün, sınıfın veya yapının dışından erişilen bir `Sub` veya `Function` yordamını açıklar. Daha fazla bilgi için bkz. [yordamlar](./index.md).  
  
 `Sub` yordam, çağıran kod tarafından buna geçirilen sabitler, değişkenler veya ifadeler gibi bağımsız değişkenler alabilir.  
  
## <a name="declaration-syntax"></a>Bildirim Söz Dizimi  
 `Sub` yordamı bildirmek için sözdizimi aşağıdaki gibidir:  
  
 `[` *değiştiriciler* `] Sub`*subname* `[(` *parameterlist* `)]`  
  
 `' Statements of the Sub procedure.`  
  
 `End Sub`  
  
 `modifiers`, erişim düzeyini ve aşırı yükleme, geçersiz kılma, paylaşma ve gölgeleme hakkında bilgileri belirtebilir. Daha fazla bilgi için bkz. [Sub deyimidir](../../../../visual-basic/language-reference/statements/sub-statement.md).  
  
## <a name="parameter-declaration"></a>Parametre bildirimi  
 Her yordam parametresini, parametre adını ve veri türünü belirterek bir değişkeni nasıl bildirdiğinizin benzer şekilde bildirirsiniz. Ayrıca, geçen mekanizmayı ve parametrenin isteğe bağlı veya bir parametre dizisi olduğunu belirtebilirsiniz.  
  
 Parametre listesindeki her bir parametre için sözdizimi aşağıdaki gibidir:  
  
 `[Optional] [ByVal | ByRef] [ParamArray]`*parametername*`As`*DataType*  
  
 Parametre isteğe bağlı ise, bildiriminin bir parçası olarak bir varsayılan değer de belirtmeniz gerekir. Varsayılan bir değer belirtmek için sözdizimi aşağıdaki gibidir:  
  
 `Optional [ByVal | ByRef]`*parametername*`As`*DataType*`=`*DefaultValue*  
  
### <a name="parameters-as-local-variables"></a>Yerel değişkenler olarak parametreler  
 Denetim yordama geçtiğinde, her bir parametre yerel bir değişken olarak değerlendirilir. Bu, yaşam süresinin prosedürünyle aynı olduğu ve kapsamı tüm yordam olduğu anlamına gelir.  
  
## <a name="calling-syntax"></a>Çağırma sözdizimi  
 Tek başına çağırma ifadesiyle bir `Sub` yordamını açık olarak çağırabilirsiniz. Bir ifadede adını kullanarak çağrılamaz. İsteğe bağlı olmayan tüm bağımsız değişkenlerin değerlerini sağlamanız gerekir ve bağımsız değişken listesini parantez içine almalısınız. Herhangi bir bağımsız değişken sağlanmazsa, isteğe bağlı olarak ayraçları atlayabilirsiniz. `Call` anahtar sözcüğünün kullanımı isteğe bağlıdır, ancak önerilmez.  
  
 `Sub` yordam çağrısı için sözdizimi aşağıdaki gibidir:  
  
 `[Call]`*subname* `[(` *argumentlist* `)]`  
  
 Bir `Sub` yöntemi, kendisini tanımlayan sınıfın dışından çağırabilirsiniz. İlk olarak, sınıfının bir örneğini oluşturmak veya sınıfının bir örneğini döndüren bir yöntemi çağırmak için `New` anahtar sözcüğünü kullanmanız gerekir. Daha fazla bilgi için bkz. [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md). Ardından, örnek nesnesinde `Sub` yöntemini çağırmak için aşağıdaki sözdizimini kullanabilirsiniz:  
  
 *Nesne*. *methodname*`[(`*argumentlist*`)]`  
  
### <a name="illustration-of-declaration-and-call"></a>Bildirim ve çağrı gösterimi  
 Aşağıdaki `Sub` yordam, bilgisayar işlecine uygulamanın hangi görevi gerçekleştirmesini söyler ve ayrıca bir zaman damgası görüntüler. Her görevin başlangıcında bu kodu çoğaltmak yerine, uygulama yalnızca çeşitli konumlardan `tellOperator` çağırır. Her çağrı, başlatılmakta olan görevi tanımlayan `task` bağımsız değişkeninde bir dize geçirir.  
  
 [!code-vb[VbVbcnProcedures#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#2)]  
  
 Aşağıdaki örnek `tellOperator`tipik bir çağrısını gösterir.  
  
 [!code-vb[VbVbcnProcedures#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [İşlev Yordamları](./function-procedures.md)
- [Özellik Yordamları](./property-procedures.md)
- [İşleç Yordamları](./operator-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Sub Deyimi](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Nasıl yapılır: Değer Döndürmeyen Bir Yordam Çağırma](./how-to-call-a-procedure-that-does-not-return-a-value.md)
- [Nasıl yapılır: Visual Basic bir olay Işleyicisini çağırma](./how-to-call-an-event-handler.md)
