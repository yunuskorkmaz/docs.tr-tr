---
title: 'Nasıl yapılır: Bir Yordamın Parametresini Tanımlama'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure parameters [Visual Basic], defining data types for
- procedures [Visual Basic], parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters [Visual Basic], defining
ms.assetid: 7962808d-407e-4e84-984e-43e9857c53c9
ms.openlocfilehash: 411959a7be92ea49a59558b508e992bfba8eff95
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344880"
---
# <a name="how-to-define-a-parameter-for-a-procedure-visual-basic"></a>Nasıl yapılır: Bir Yordamın Parametresini Tanımlama (Visual Basic)
Bir *parametre* çağıran kodun, çağrı yaptığı zaman yordama bir değer geçmesini sağlar. Bir yordam için her parametreyi, adını ve veri türünü belirterek bir değişkeni bildirdiğiniz şekilde bildirirsiniz. Ayrıca, geçen mekanizmayı ve parametrenin isteğe bağlı olup olmadığını da belirtirsiniz.  
  
 Daha fazla bilgi için bkz. [yordam parametreleri ve bağımsız değişkenleri](./procedure-parameters-and-arguments.md).  
  
### <a name="to-define-a-procedure-parameter"></a>Bir yordam parametresi tanımlamak için  
  
1. Yordam bildiriminde, parametre adını yordamın parametre listesine ekleyerek diğer parametrelerden virgülle ayırın.  
  
2. Parametrenin veri türüne karar verin.  
  
3. Veri türünü belirtmek için bir `As` yan tümcesiyle parametre adını izleyin.  
  
4. Parametre için istediğiniz geçirme mekanizmasına karar verin. Genellikle yordamın, çağıran koddaki değerini değiştirebilmesini istemediğiniz müddetçe, bir parametreyi değere göre geçirirsiniz.  
  
5. Geçen mekanizmayı belirtmek için parametre adından [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) veya [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) ile önce gelmeli. Daha fazla bilgi için, [bir bağımsız değişkeni değere ve başvuruya göre geçirme arasındaki farklılıklar](./differences-between-passing-an-argument-by-value-and-by-reference.md)bölümüne bakın.  
  
6. Parametre isteğe bağlı ise, geçirme mekanizmasından [Isteğe bağlı](../../../../visual-basic/language-reference/modifiers/optional.md) olarak önüne koyun ve bir eşittir işareti (`=`) ve varsayılan bir değer ile parametre veri türünü izleyin.  
  
     Aşağıdaki örnek, üç parametreli bir `Sub` yordamının ana hattını tanımlar. İlk ikisi gereklidir ve üçüncü değer isteğe bağlıdır. Parametre bildirimleri parametre listesinde virgülle ayrılır.  
  
     [!code-vb[VbVbcnProcedures#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#33)]  
  
     İlk parametre bir `customer` nesnesini kabul eder ve `updateCustomer` bağımsız değişken [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)olarak geçirildiğinden `c` geçirilen değişkeni doğrudan güncelleştirebilir. Yordam, [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)geçirildiğinden, son iki bağımsız değişkenin değerlerini değiştiremez.  
  
     Çağıran kod `level` parametresi için bir değer sağlamalarsa Visual Basic varsayılan değeri olan 0 ' a ayarlanır.  
  
     Tür denetimi anahtarı ([Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) `Off`ise, bir parametre tanımladığınızda `As` yan tümcesi isteğe bağlıdır. Ancak, herhangi bir parametre `As` yan tümcesi kullanıyorsa, bunların hepsi tarafından kullanılmalıdır. Tür denetleme anahtarı `On`, her parametre tanımı için `As` yan tümcesi gereklidir.  
  
     Tüm programlama öğelerinizin veri türlerini belirtme, *güçlü yazma*olarak bilinir. `Option Strict On`ayarladığınızda Visual Basic güçlü yazma uygular. Bu, aşağıdaki nedenlerden dolayı kesinlikle önerilir:  
  
    - Değişkenleriniz ve parametreleriniz için IntelliSense desteği sunar. Bu, kodunuzda yazarken özelliklerini ve diğer üyelerini görmenizi sağlar.  
  
    - Derleyicinin tür denetimi gerçekleştirmesini sağlar. Bu, taşma gibi hatalar nedeniyle çalışma zamanında başarısız olan catch deyimlerine yardımcı olur. Ayrıca, bunları desteklemeyen nesneler üzerindeki yöntemlere yapılan çağrıları yakalar.  
  
    - Kodunuzun daha hızlı yürütülmesine neden olur. Bunun bir nedeni, bir programlama öğesi için bir veri türü belirtplanlamıyorsanız Visual Basic derleyicisinin onu `Object` türüne atamasını sağlamaz. Derlenmiş kodunuzun `Object` ve diğer veri türleri arasında geri ve ileri dönüştürmek, bu da performansı azaltır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Alt Yordamlar](./sub-procedures.md)
- [İşlev Yordamları](./function-procedures.md)
- [Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme](./how-to-pass-arguments-to-a-procedure.md)
- [Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme](./passing-arguments-by-value-and-by-reference.md)
- [Özyinelemeli Yordamlar](./recursive-procedures.md)
- [Yordam Aşırı Yüklemesi](./procedure-overloading.md)
- [Nesneler ve Sınıflar](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Nesne odaklı programlama (Visual Basic)](../../concepts/object-oriented-programming.md)
