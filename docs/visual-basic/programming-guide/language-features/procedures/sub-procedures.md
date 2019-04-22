---
title: Alt Yordamlar (Visual Basic)
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
ms.openlocfilehash: b70594e002bbf08f0890586e78df901ccb26c7ce
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58843116"
---
# <a name="sub-procedures-visual-basic"></a>Alt Yordamlar (Visual Basic)
A `Sub` yordamdır kapsadığı Visual Basic deyimleri bir dizi `Sub` ve `End Sub` deyimleri. `Sub` Yordamı bir görevi gerçekleştirir ve çağıran koda denetim döndürür, ancak çağrıldığı koda bir değer döndürmez.  
  
 Yordam çağrıldığında, her zaman kendi deyimleri, sonra yürütülebilir ilk deyimi'ile başlayan yürütülür `Sub` deyimi ve ilk görmektesiniz `End Sub`, `Exit Sub`, veya `Return` deyimiyle karşılaşıldı.  
  
 Tanımlayabileceğiniz bir `Sub` modülleri, sınıfları ve yapıları yordamda. Varsayılan olarak, olduğu `Public`, anlamına yerden çağırabilirsiniz uygulamanızdaki modül, sınıf veya yapının, tanımlandığı da erişebilir. Terim *yöntemi*, açıklayan bir `Sub` veya `Function` kendi tanımlama dışından erişilen gelen yordamı modül, sınıf veya yapı. Daha fazla bilgi için [yordamları](./index.md).  
  
 A `Sub` yordamı, sabitleri, değişkenleri veya kendisine çağıran kod tarafından geçirilen ifadeler gibi bir bağımsız değişken alabilir.  
  
## <a name="declaration-syntax"></a>Bildirim Sözdizimi  
 Bildirmek için söz dizimi bir `Sub` yordam şu şekildedir:  
  
 `[` *değiştiriciler* `] Sub` *subname* `[(` *parameterlist* `)]`  
  
 `' Statements of the Sub procedure.`  
  
 `End Sub`  
  
 `modifiers` Erişim düzeyi ve aşırı yüklemesi, geçersiz kılma, paylaşımı ve gölgeleme hakkında bilgileri belirtebilirsiniz. Daha fazla bilgi için [Sub deyimi](../../../../visual-basic/language-reference/statements/sub-statement.md).  
  
## <a name="parameter-declaration"></a>Parametre bildirimi  
 Size nasıl parametre adı ile veri türünü belirten bir değişken bildirmek için benzer şekilde, her yordam parametresinin bildirin. Geçirme mekanizması belirtebilirsiniz ve parametrenin isteğe bağlı olduğundan veya bir parametre dizisi.  
  
 Parametre listesindeki her parametre için sözdizimi aşağıdaki gibidir:  
  
 `[Optional] [ByVal | ByRef] [ParamArray]`  *parametername*`As`*veri türü*  
  
 Parametre isteğe bağlıysa, varsayılan değer bildiriminin bir parçası olarak da belirtmeniz gerekir. Varsayılan bir değer belirtmek için sözdizimi aşağıdaki gibidir:  
  
 `Optional [ByVal | ByRef]`  *parametername*`As`*datatype*`=`*defaultvalue*  
  
### <a name="parameters-as-local-variables"></a>Yerel değişkenleri olarak Parametreler  
 Her bir parametre, yordama denetimi başarılı olduğunda, yerel bir değişken olarak kabul edilir. Bu, yaşam süresi yordamın aynıdır ve kapsamı bütün bir yordamdır anlamına gelir.  
  
## <a name="calling-syntax"></a>Arama söz dizimi  
 Çağırdığınızda bir `Sub` açıkça tek başına bir deyim çağırma yordamı. Adı bir ifade kullanarak çağrılamıyor. İsteğe bağlı olmayan tüm bağımsız değişkenler için değerler sağlaması gerekir ve bağımsız değişken listesi parantez içine almalısınız. Hiçbir bağımsız değişken sağlanmadıysa, parantezler isteğe bağlı olarak atlayabilirsiniz. Kullanımını `Call` anahtar sözcüğü isteğe bağlıdır, ancak önerilmez.  
  
 Bir çağrı sözdizimi bir `Sub` yordam şu şekildedir:  
  
 `[Call]`  *subname* `[(` *argumentlist* `)]`  
  
 Çağırabilirsiniz bir `Sub` yöntemi tanımlayan bir sınıf dışında. İlk olarak kullanmak zorunda `New` sınıfının bir örneğini oluşturmak veya, bir yöntem çağırmak için anahtar sözcüğü bir sınıf örneği döndürür. Daha fazla bilgi için [New işleci](../../../../visual-basic/language-reference/operators/new-operator.md). Ardından çağırmak için aşağıdaki söz dizimini kullanabilirsiniz `Sub` örneği nesnesi üzerinde yöntemi:  
  
 *Nesne*. *MethodName*`[(`*argumentlist*`)]`  
  
### <a name="illustration-of-declaration-and-call"></a>Bildirim ve çağrı gösterimi  
 Aşağıdaki `Sub` yordamı uygulamasıdır gerçekleştirmek üzere hangi görev bilgisayar işleci bildirir ve ayrıca bir zaman damgasını gösterir. Bu kod, her görevin başlangıcında çoğaltmak yerine uygulama yalnızca çağırır `tellOperator` çeşitli konumlardan. Her çağrı bir dizede geçirir `task` Başlatılmakta olan görevi tanımlayan bir bağımsız değişken.  
  
 [!code-vb[VbVbcnProcedures#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#2)]  
  
 Aşağıdaki örnek, tipik bir çağrı gösterir `tellOperator`.  
  
 [!code-vb[VbVbcnProcedures#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [İşlev Yordamları](./function-procedures.md)
- [Özellik Yordamları](./property-procedures.md)
- [İşleç Yordamları](./operator-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Sub Deyimi](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Nasıl yapılır: Bir değer döndürmeyen bir yordam çağırma](./how-to-call-a-procedure-that-does-not-return-a-value.md)
- [Nasıl yapılır: Visual Basic olay işleyicisi çağırma](./how-to-call-an-event-handler.md)
