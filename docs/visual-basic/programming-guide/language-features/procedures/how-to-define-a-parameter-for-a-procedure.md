---
title: 'Nasıl yapılır: (Visual Basic) için bir yordam parametresini tanımlama'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure parameters [Visual Basic], defining data types for
- procedures [Visual Basic], parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters [Visual Basic], defining
ms.assetid: 7962808d-407e-4e84-984e-43e9857c53c9
ms.openlocfilehash: 01b150d70c07897f8217ed6958e3654aa28fdf51
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971799"
---
# <a name="how-to-define-a-parameter-for-a-procedure-visual-basic"></a>Nasıl yapılır: (Visual Basic) için bir yordam parametresini tanımlama
A *parametre* çağıran kod, çağırdığında bir değeri yordama geçirmeye izin verir. Her parametre için bir yordam adı ve veri türünü belirten bir değişken bildirmek aynı şekilde bildirin. Ayrıca geçirme mekanizma belirtin ve parametre isteğe bağlıdır.  
  
 Daha fazla bilgi için [parametreler ve bağımsız değişkenler](./procedure-parameters-and-arguments.md).  
  
### <a name="to-define-a-procedure-parameter"></a>Bir yordamın parametresini tanımlama  
  
1.  Yordam bildiriminde parametre adı, diğer parametreler virgülle ayırarak, yordam parametre listesine ekleyin.  
  
2.  Parametrenin veri türünü karar verin.  
  
3.  Parametre adı ile bir `As` yan veri türü belirtin.  
  
4.  Parametresi için istediğiniz geçirme mekanizması karar verin. Normalde çağıran koddaki değeri değiştirebilmesi için yordamı istemediğiniz sürece değere göre bir parametre geçirin.  
  
5.  Parametre adıyla önünde [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) veya [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) geçirme mekanizması belirtmek için. Daha fazla bilgi için [farklar arasında geçen bir bağımsız değişken değer ve başvuru tarafından](./differences-between-passing-an-argument-by-value-and-by-reference.md).  
  
6.  Parametre isteğe bağlıysa geçirme mekanizmasıyla önünde [isteğe bağlı](../../../../visual-basic/language-reference/modifiers/optional.md) ve parametre veri türü bir eşittir işareti ile izleyin (`=`) ve varsayılan değeri.  
  
     Aşağıdaki örnek, ana hat tanımlar. bir `Sub` yordamı üç parametrelere sahip. İlk iki gereklidir ve üçüncü isteğe bağlıdır. Parametre bildirimleri parametre listesinde virgülle ayrılır.  
  
     [!code-vb[VbVbcnProcedures#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#33)]  
  
     İlk parametre kabul eden bir `customer` nesnesi ve `updateCustomer` doğrudan geçirilen değişkeni güncelleştirebilirsiniz `c` geçirilen bağımsız değişken olduğundan [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md). Geçirilen çünkü yordamın son iki bağımsız değişken değerlerini değiştiremezsiniz [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).  
  
     Çağıran kod için bir değer sağlamıyor varsa `level` parametre, Visual Basic ayarlar, varsayılan değeri 0 olarak.  
  
     Tür denetleme geçerseniz ([Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) olan `Off`, `As` yan tümcesi olduğunda isteğe bağlı bir parametre tanımlayın. Ancak, herhangi bir parametre kullanıyorsa bir `As` yan tümcesi, bunların tümünün gerekir kullanır. Geçiş denetimi türü ise `On`, `As` yan tümcesi için her bir parametre tanımında gereklidir.  
  
     Tüm programlama öğeleriniz için veri türlerini belirtme olarak bilinir *güçlü yazım, yazım*. Ayarladığınızda `Option Strict On`, Visual Basic güçlü yazım, yazım zorlar. Bu, aşağıdaki nedenlerden dolayı önerilir:  
  
    -   Bu değişkenler ve parametreler için IntelliSense desteği sağlar. Bunu siz kodunuzu yazarken, özelliklerini ve diğer üyeleri görmenizi sağlar.  
  
    -   Derleyicinin tür denetimi sağlar. Bu, catch taşma gibi hatalar nedeniyle çalışma zamanında başarısız olabilir deyimleri yardımcı olur. Ayrıca bunları desteği olmayan nesneler üzerinde yöntemlere yapılan çağrılar yakalar.  
  
    -   Bu, kodunuzun daha hızlı bir şekilde yürütülmesini sonuçlanır. Bunun bir nedeni olduğundan bir programlama öğesi için bir veri türü belirtmezseniz, Visual Basic Derleyicisi, atamasını `Object` türü. Derlenmiş kod arasında ileri ve geri dönüştürmek zorunda kalabilirsiniz `Object` ve diğer veri türleri, performansı azaltır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Alt Yordamlar](./sub-procedures.md)
- [İşlev Yordamları](./function-procedures.md)
- [Nasıl yapılır: Bir yordama bağımsız değişkenler geçirme](./how-to-pass-arguments-to-a-procedure.md)
- [Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme](./passing-arguments-by-value-and-by-reference.md)
- [Özyinelemeli Yordamlar](./recursive-procedures.md)
- [Yordam Aşırı Yüklemesi](./procedure-overloading.md)
- [Nesneler ve Sınıflar](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Nesne odaklı programlama (Visual Basic)](../../concepts/object-oriented-programming.md)
