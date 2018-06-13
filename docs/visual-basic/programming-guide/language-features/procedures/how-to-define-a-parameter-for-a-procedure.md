---
title: 'Nasıl yapılır: Bir Yordamın Parametresini Tanımlama (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure parameters [Visual Basic], defining data types for
- procedures [Visual Basic], parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters [Visual Basic], defining
ms.assetid: 7962808d-407e-4e84-984e-43e9857c53c9
ms.openlocfilehash: b058f593b8672da449dac250947563c75c8386bf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651119"
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
  
     Çağrıyı yapan kod için bir değer sağlamaz, `level` parametresi, Visual Basic ayarlar, 0 varsayılan değeri.  
  
     Tür denetleme geçiş yaparsanız ([Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) olan `Off`, `As` yan tümcesi olduğunda isteğe bağlı bir parametre tanımlayın. Ancak, herhangi bir parametre kullanıyorsa, bir `As` yan tümcesi, bunların tümünün gerekir kullanır. Anahtar denetimi türü ise `On`, `As` her parametre tanımı yan tümcesi gereklidir.  
  
     Veri türleri için tüm programlama öğeleri belirtme olarak bilinir *güçlü yazarak*. Ayarladığınızda `Option Strict On`, Visual Basic güçlü yazmaya zorlar. Bu, aşağıdaki nedenlerle önerilir:  
  
    -   Değişkenleri ve parametreleri için IntelliSense desteği sağlar. Bu, kodunuzda yazarken özelliklerini ve diğer üyeleri görmenize olanak sağlar.  
  
    -   Tür denetleme gerçekleştirmek derleyici sağlar. Bu, çalışma zamanında taşma gibi hatalar nedeniyle başarısız olabilir deyimleri catch yardımcı olur. Ayrıca bunları desteklemeyen nesnelerde yöntem çağrıları yakalar.  
  
    -   Kodunuzu daha hızlı yürütülmesini sonuçlanır. Bunun bir nedeni olan bir programlama öğesi için bir veri türü belirtmezseniz, Visual Basic derleyici onu atayacağını `Object` türü. Derlenmiş kodunuzu arasında ileri ve geri dönüştürmeniz gerekebilir `Object` ve performansını düşürür diğer veri türleri.  
  
## <a name="see-also"></a>Ayrıca bkz.

 [Yordamlar](./index.md)  
 [Alt Yordamlar](./sub-procedures.md)  
 [İşlev Yordamları](./function-procedures.md)  
 [Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme](./how-to-pass-arguments-to-a-procedure.md)  
 [Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme](./passing-arguments-by-value-and-by-reference.md)  
 [Özyinelemeli Yordamlar](./recursive-procedures.md)  
 [Yordam Aşırı Yüklemesi](./procedure-overloading.md)  
 [Nesneler ve Sınıflar](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [Nesne odaklı programlama (Visual Basic)](../../concepts/object-oriented-programming.md)  
