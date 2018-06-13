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
ms.openlocfilehash: 3286df1a5babfcf7d6b759ff5c9a920bb44f51ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652571"
---
# <a name="sub-procedures-visual-basic"></a>Alt Yordamlar (Visual Basic)
A `Sub` yordamdır bir dizi kapsadığı Visual Basic deyimi `Sub` ve `End Sub` deyimleri. `Sub` Yordamı bir görevi gerçekleştirir ve çağrıyı yapan kod denetim verir, ancak çağıran kodu için bir değer döndürmüyor.  
  
 Yordam çağrıldığında, her zaman kendi deyimleri, sonra ilk yürütülebilir ifadesiyle başlayan yürütülür `Sub` deyimi ve ilk ile bitiş `End Sub`, `Exit Sub`, veya `Return` deyimiyle karşılaşıldı.  
  
 Tanımlayabileceğiniz bir `Sub` modülleri, sınıfları ve yapıları yordamda. Varsayılan olarak, olmasından `Public`, anlamına gelir, herhangi bir yerden çağırabilir modülü, sınıf veya yapı içinde tanımlanan bu erişimi, uygulamanızda. Terim *yöntemi*, açıklayan bir `Sub` veya `Function` kendi tanımlama dışında erişilen gelen yordamı modülü, sınıf veya yapı. Daha fazla bilgi için bkz: [yordamları](./index.md).  
  
 A `Sub` yordamı sabitleri, değişkenleri veya kendisine çağrıyı yapan kod tarafından geçirilen ifadeler gibi bağımsız değişkenleri alabilir.  
  
## <a name="declaration-syntax"></a>Bildirim Sözdizimi  
 Bildirme sözdizimi bir `Sub` yordam aşağıdaki gibidir:  
  
 `[` *değiştiriciler* `] Sub` *subname* `[(` *parametreListesi*  `)]`  
  
 `' Statements of the Sub procedure.`  
  
 `End Sub`  
  
 `modifiers` Erişim düzeyini ve aşırı yüklemesi, geçersiz kılma, paylaşımı ve gölgeleme hakkında bilgileri belirtebilirsiniz. Daha fazla bilgi için bkz: [Sub deyimi](../../../../visual-basic/language-reference/statements/sub-statement.md).  
  
## <a name="parameter-declaration"></a>Parametre bildirimi  
 Benzer şekilde nasıl parametre adını ve veri türünü belirten bir değişken bildirmek için her yordam parametresini bildirin. Geçirme mekanizması da belirtebilirsiniz ve parametre isteğe bağlı olup ya da bir parametre dizisi.  
  
 Parametre listesindeki her parametre için söz dizimi aşağıdaki gibidir:  
  
 `[Optional] [ByVal | ByRef] [ParamArray]`  *parametername*`As`*veri türü*   
  
 Parametre isteğe bağlı ise, varsayılan değer bildiriminden bir parçası olarak sağlamanız gerekir. Varsayılan bir değer belirtmek için sözdizimi aşağıdaki gibidir:  
  
 `Optional [ByVal | ByRef]`  *parametername*`As`*datatype*`=`*defaultvalue*   
  
### <a name="parameters-as-local-variables"></a>Yerel değişkenleri olarak Parametreler  
 Denetim yordama geçtiğinde, her bir parametreyi yerel değişken olarak kabul edilir. Bu yaşam yordamın aynıdır ve tüm yordamı kapsamı olduğu anlamına gelir.  
  
## <a name="calling-syntax"></a>Arama sözdizimi  
 Çağırmayı bir `Sub` açıkça ifadesiyle bir tek başına arama yordamı. Bir ifadeyi adını kullanarak çağrılamaz. İsteğe bağlı olmayan tüm bağımsız değişkenler için değerler sağlayın ve bağımsız değişken listesi parantez içine alın. Bağımsız değişkenler sağlandıysa, isteğe bağlı olarak parantez atlayabilirsiniz. Kullanımını `Call` anahtar sözcüğü isteğe bağlıdır, ancak önerilmez.  
  
 Çağrı sözdizimi bir `Sub` yordam aşağıdaki gibidir:  
  
 `[Call]`  *subname* `[(` *bağımsızdeğişkenListesi* `)]`  
  
 Arayabileceğiniz bir `Sub` yönteminden tanımladığı sınıfı dışında. İlk olarak, kullanmak zorunda `New` sınıfının bir örneğini oluşturmak veya bir yöntem çağrısı için anahtar sözcüğü sınıfının bir örneğini döndürür. Daha fazla bilgi için bkz: [yeni işleç](../../../../visual-basic/language-reference/operators/new-operator.md). Ardından, çağırmak için aşağıdaki söz dizimini kullanabilirsiniz `Sub` örneği nesnesi üzerinde yöntemi:  
  
 *Nesne*. *MethodName*`[(`*bağımsızdeğişkenListesi*`)]`  
  
### <a name="illustration-of-declaration-and-call"></a>Bildirim ve çağrı çizimi  
 Aşağıdaki `Sub` yordamı uygulamasıdır gerçekleştirmek üzere hangi görev bilgisayar işleci bildirir ve ayrıca bir zaman damgasını gösterir. Bu kodu her görev başlangıcında çoğaltmak yerine uygulama yalnızca çağırır `tellOperator` çeşitli konumlardan. Bir dizede her çağrı geçirir `task` başlatılmakta görevi tanımlar bağımsız değişkeni.  
  
 [!code-vb[VbVbcnProcedures#2](./codesnippet/VisualBasic/sub-procedures_1.vb)]  
  
 Aşağıdaki örnek tipik bir çağrı gösterilmektedir `tellOperator`.  
  
 [!code-vb[VbVbcnProcedures#3](./codesnippet/VisualBasic/sub-procedures_2.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yordamlar](./index.md)  
 [İşlev Yordamları](./function-procedures.md)  
 [Özellik Yordamları](./property-procedures.md)  
 [İşleç Yordamları](./operator-procedures.md)  
 [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)  
 [Sub Deyimi](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Nasıl yapılır: Değer Döndürmeyen Bir Yordam Çağırma](./how-to-call-a-procedure-that-does-not-return-a-value.md)  
 [Nasıl yapılır: Visual Basic'te bir olay işleyicisi çağırma](./how-to-call-an-event-handler.md)
