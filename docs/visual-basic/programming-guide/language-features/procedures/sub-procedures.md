---
title: Alt Yordamlar (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e20e0dd5ff9e2b931e5792bebb3144930826f89
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="sub-procedures-visual-basic"></a>Alt Yordamlar (Visual Basic)
A `Sub` yordamdır bir dizi [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] deyimleri içine tarafından `Sub` ve `End Sub` deyimleri. `Sub` Yordamı bir görevi gerçekleştirir ve çağrıyı yapan kod denetim verir, ancak çağıran kodu için bir değer döndürmüyor.  
  
 Yordam çağrıldığında, her zaman kendi deyimleri, sonra ilk yürütülebilir ifadesiyle başlayan yürütülür `Sub` deyimi ve ilk ile bitiş `End Sub`, `Exit Sub`, veya `Return` deyimiyle karşılaşıldı.  
  
 Tanımlayabileceğiniz bir `Sub` modülleri, sınıfları ve yapıları yordamda. Varsayılan olarak, olmasından `Public`, anlamına gelir, herhangi bir yerden çağırabilir modülü, sınıf veya yapı içinde tanımlanan bu erişimi, uygulamanızda. Terim *yöntemi*, açıklayan bir `Sub` veya `Function` kendi tanımlama dışında erişilen gelen yordamı modülü, sınıf veya yapı. Daha fazla bilgi için bkz: [yordamları](./index.md).  
  
 A `Sub` yordamı sabitleri, değişkenleri veya kendisine çağrıyı yapan kod tarafından geçirilen ifadeler gibi bağımsız değişkenleri alabilir.  
  
## <a name="declaration-syntax"></a>Bildirim Sözdizimi  
 Bildirme sözdizimi bir `Sub` yordam aşağıdaki gibidir:  
  
 `[`*değiştiricileri* `] Sub` *subname* `[(` *parametreListesi*  `)]`  
  
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
  
 `[Call]`  *subname* `[(` *bağımsızdeğişkenListesi*`)]`  
  
 Arayabileceğiniz bir `Sub` yönteminden tanımladığı sınıfı dışında. İlk olarak, kullanmak zorunda `New` sınıfının bir örneğini oluşturmak veya bir yöntem çağrısı için anahtar sözcüğü sınıfının bir örneğini döndürür. Daha fazla bilgi için bkz: [yeni işleç](../../../../visual-basic/language-reference/operators/new-operator.md). Ardından, çağırmak için aşağıdaki söz dizimini kullanabilirsiniz `Sub` örneği nesnesi üzerinde yöntemi:  
  
 *Nesne*. *MethodName*`[(`*bağımsızdeğişkenListesi*`)]`  
  
### <a name="illustration-of-declaration-and-call"></a>Bildirim ve çağrı çizimi  
 Aşağıdaki `Sub` yordamı uygulamasıdır gerçekleştirmek üzere hangi görev bilgisayar işleci bildirir ve ayrıca bir zaman damgasını gösterir. Bu kodu her görev başlangıcında çoğaltmak yerine uygulama yalnızca çağırır `tellOperator` çeşitli konumlardan. Bir dizede her çağrı geçirir `task` başlatılmakta görevi tanımlar bağımsız değişkeni.  
  
 [!code-vb[VbVbcnProcedures#2](./codesnippet/VisualBasic/sub-procedures_1.vb)]  
  
 Aşağıdaki örnek tipik bir çağrı gösterilmektedir `tellOperator`.  
  
 [!code-vb[VbVbcnProcedures#3](./codesnippet/VisualBasic/sub-procedures_2.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yordamları](./index.md)  
 [İşlev yordamları](./function-procedures.md)  
 [Özellik yordamları](./property-procedures.md)  
 [İşleç yordamları](./operator-procedures.md)  
 [Parametreler ve bağımsız değişkenler](./procedure-parameters-and-arguments.md)  
 [Sub deyimi](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Nasıl yapılır: bir değer döndürmeyen bir yordam çağırma](./how-to-call-a-procedure-that-does-not-return-a-value.md)  
 [Nasıl yapılır: Visual Basic'te bir olay işleyicisi çağırma](./how-to-call-an-event-handler.md)
