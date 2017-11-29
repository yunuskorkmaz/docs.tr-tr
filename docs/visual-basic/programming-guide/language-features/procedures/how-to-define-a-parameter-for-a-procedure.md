---
title: "Nasıl yapılır: Bir Yordamın Parametresini Tanımlama (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedure parameters [Visual Basic], defining data types for
- procedures [Visual Basic], parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters [Visual Basic], defining
ms.assetid: 7962808d-407e-4e84-984e-43e9857c53c9
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3c909cfe1b45a42aae91948917f310474575f225
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-a-parameter-for-a-procedure-visual-basic"></a>Nasıl yapılır: Bir Yordamın Parametresini Tanımlama (Visual Basic)
A *parametresi* onu çağırdığında yordamı için bir değer geçirmek için çağıran kodu sağlar. Bir yordam için her parametre adı ve veri türünü belirten bir değişken bildirin aynı şekilde bildirin. Ayrıca geçirme mekanizması belirtin ve parametre isteğe bağlıdır.  
  
 Daha fazla bilgi için bkz: [parametreler ve bağımsız değişkenler](./procedure-parameters-and-arguments.md).  
  
### <a name="to-define-a-procedure-parameter"></a>Bir yordam parametresini tanımlamak için  
  
1.  Yordam bildiriminde yordam parametre listesi, diğer parametreler virgül ile ayırarak parametre adını ekleyin.  
  
2.  Parametresinin veri türü karar verin.  
  
3.  Parametre adı ile izleyin bir `As` veri türünü belirtmek için yan tümcesi.  
  
4.  Parametresi için istediğiniz geçirme mekanizması karar verin. Normalde, yordamı çağıran kodu değeriyle değiştirebilmesi istediğiniz sürece değer ile bir parametre geçirin.  
  
5.  Parametre adından [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) veya [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) geçirme düzeneğini belirtmek için. Daha fazla bilgi için bkz: [farklar arasında geçirme bir bağımsız değişken değer ve başvuru tarafından](./differences-between-passing-an-argument-by-value-and-by-reference.md).  
  
6.  Parametre isteğe bağlıysa geçirme mekanizmasıyla önünde [isteğe bağlı](../../../../visual-basic/language-reference/modifiers/optional.md) ve parametre veri türü eşittir işareti ile izleyin (`=`) ve varsayılan bir değer.  
  
     Aşağıdaki örnek, bir özeti tanımlar. bir `Sub` yordamı üç parametrelere sahip. İlk iki gereklidir ve üçüncü isteğe bağlıdır. Parametre bildirimleri parametre listesinde virgülle ayrılır.  
  
     [!code-vb[VbVbcnProcedures#33](./codesnippet/VisualBasic/how-to-define-a-parameter-for-a-procedure_1.vb)]  
  
     İlk parametre kabul eden bir `customer` nesnesi ve `updateCustomer` geçirilen değişken doğrudan güncelleştirebilirsiniz `c` bağımsız değişkeni geçtiğinden [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md). Geçirilen olduğundan yordamın son iki bağımsız değişken değerlerini değiştiremezsiniz [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).  
  
     Çağrıyı yapan kod için bir değer sağlamaz, `level` parametresi [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 0 varsayılan değerini ayarlar.  
  
     Tür denetleme geçiş yaparsanız ([Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) olan `Off`, `As` yan tümcesi olduğunda isteğe bağlı bir parametre tanımlayın. Ancak, herhangi bir parametre kullanıyorsa, bir `As` yan tümcesi, bunların tümünün gerekir kullanır. Anahtar denetimi türü ise `On`, `As` her parametre tanımı yan tümcesi gereklidir.  
  
     Veri türleri için tüm programlama öğeleri belirtme olarak bilinir *güçlü yazarak*. Ayarladığınızda `Option Strict On`, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] güçlü yazmaya zorlar. Bu, aşağıdaki nedenlerle önerilir:  
  
    -   Değişkenleri ve parametreleri için IntelliSense desteği sağlar. Bu, kodunuzda yazarken özelliklerini ve diğer üyeleri görmenize olanak sağlar.  
  
    -   Tür denetleme gerçekleştirmek derleyici sağlar. Bu, çalışma zamanında taşma gibi hatalar nedeniyle başarısız olabilir deyimleri catch yardımcı olur. Ayrıca bunları desteklemeyen nesnelerde yöntem çağrıları yakalar.  
  
    -   Kodunuzu daha hızlı yürütülmesini sonuçlanır. Bir Bunun nedeni, bir programlama öğesi için bir veri türü belirtmezseniz, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] derleyici atar `Object` türü. Derlenmiş kodunuzu arasında ileri ve geri dönüştürmeniz gerekebilir `Object` ve performansını düşürür diğer veri türleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yordamları](./index.md)  
 [Alt yordamlar](./sub-procedures.md)  
 [İşlev yordamları](./function-procedures.md)  
 [Nasıl yapılır: bir yordama bağımsız değişkenler geçirme](./how-to-pass-arguments-to-a-procedure.md)  
 [Bağımsız değişkenleri değere ve başvuruya göre geçirme](./passing-arguments-by-value-and-by-reference.md)  
 [Özyinelemeli yordamlar](./recursive-procedures.md)  
 [Yordam aşırı yüklemesi](./procedure-overloading.md)  
 [Nesneler ve sınıflar](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [Nesne odaklı programlama](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)
