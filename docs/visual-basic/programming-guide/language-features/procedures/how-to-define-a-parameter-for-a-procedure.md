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
ms.openlocfilehash: e703346113348556b8a3ea41a7934a55a8008522
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388082"
---
# <a name="how-to-define-a-parameter-for-a-procedure-visual-basic"></a>Nasıl yapılır: Bir Yordamın Parametresini Tanımlama (Visual Basic)
Bir *parametre* çağıran kodun, çağrı yaptığı zaman yordama bir değer geçmesini sağlar. Bir yordam için her parametreyi, adını ve veri türünü belirterek bir değişkeni bildirdiğiniz şekilde bildirirsiniz. Ayrıca, geçen mekanizmayı ve parametrenin isteğe bağlı olup olmadığını da belirtirsiniz.  
  
 Daha fazla bilgi için bkz. [yordam parametreleri ve bağımsız değişkenleri](./procedure-parameters-and-arguments.md).  
  
### <a name="to-define-a-procedure-parameter"></a>Bir yordam parametresi tanımlamak için  
  
1. Yordam bildiriminde, parametre adını yordamın parametre listesine ekleyerek diğer parametrelerden virgülle ayırın.  
  
2. Parametrenin veri türüne karar verin.  
  
3. `As`Veri türünü belirtmek için bir yan tümcesiyle birlikte parametre adını izleyin.  
  
4. Parametre için istediğiniz geçirme mekanizmasına karar verin. Genellikle yordamın, çağıran koddaki değerini değiştirebilmesini istemediğiniz müddetçe, bir parametreyi değere göre geçirirsiniz.  
  
5. Geçen mekanizmayı belirtmek için parametre adından [ByVal](../../../language-reference/modifiers/byval.md) veya [ByRef](../../../language-reference/modifiers/byref.md) ile önce gelmeli. Daha fazla bilgi için, [bir bağımsız değişkeni değere ve başvuruya göre geçirme arasındaki farklılıklar](./differences-between-passing-an-argument-by-value-and-by-reference.md)bölümüne bakın.  
  
6. Parametre isteğe bağlı ise, geçiş mekanizmasından [Isteğe bağlı](../../../language-reference/modifiers/optional.md) olarak önüne koyun ve bir eşittir işareti ( `=` ) ve varsayılan bir değer ile parametre veri türünü izleyin.  
  
     Aşağıdaki örnek, üç parametreli bir yordamın ana hattını tanımlar `Sub` . İlk ikisi gereklidir ve üçüncü değer isteğe bağlıdır. Parametre bildirimleri parametre listesinde virgülle ayrılır.  
  
     [!code-vb[VbVbcnProcedures#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#33)]  
  
     İlk parametre bir nesneyi kabul eder `customer` ve `updateCustomer` `c` bağımsız değişken [ByRef](../../../language-reference/modifiers/byref.md)olarak geçirildiğinden, öğesine geçirilen değişkeni doğrudan güncelleştirebilir. Yordam, [ByVal](../../../language-reference/modifiers/byval.md)geçirildiğinden, son iki bağımsız değişkenin değerlerini değiştiremez.  
  
     Çağıran kod parametre için bir değer sağlamadıysanız `level` , Visual Basic varsayılan değer olan 0 ' a ayarlar.  
  
     Tür denetleme anahtarı ([Option Strict deyimi](../../../language-reference/statements/option-strict-statement.md)) ise `Off` , `As` bir parametre tanımladığınızda yan tümce isteğe bağlıdır. Ancak, herhangi bir parametre bir `As` yan tümce kullanıyorsa, tümünün onu kullanması gerekir. Tür denetleme anahtarı ise `On` , `As` yan tümce her parametre tanımı için gereklidir.  
  
     Tüm programlama öğelerinizin veri türlerini belirtme, *güçlü yazma*olarak bilinir. Ayarladığınızda `Option Strict On` , Visual Basic güçlü yazma uygular. Bu, aşağıdaki nedenlerden dolayı kesinlikle önerilir:  
  
    - Değişkenleriniz ve parametreleriniz için IntelliSense desteği sunar. Bu, kodunuzda yazarken özelliklerini ve diğer üyelerini görmenizi sağlar.  
  
    - Derleyicinin tür denetimi gerçekleştirmesini sağlar. Bu, taşma gibi hatalar nedeniyle çalışma zamanında başarısız olan catch deyimlerine yardımcı olur. Ayrıca, bunları desteklemeyen nesneler üzerindeki yöntemlere yapılan çağrıları yakalar.  
  
    - Kodunuzun daha hızlı yürütülmesine neden olur. Bunun bir nedeni, bir programlama öğesi için bir veri türü belirtplanlamıyorsanız Visual Basic derleyicisinin bu türü atamasını sağlamaz `Object` . Derlenmiş kodunuzun `Object` , ve diğer veri türleri arasında geri ve ileri dönüştürmek için performansı azaltan bir işlem olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Alt Yordamlar](./sub-procedures.md)
- [İşlev Yordamları](./function-procedures.md)
- [Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme](./how-to-pass-arguments-to-a-procedure.md)
- [Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme](./passing-arguments-by-value-and-by-reference.md)
- [Özyinelemeli Yordamlar](./recursive-procedures.md)
- [Yordam Aşırı Yüklemesi](./procedure-overloading.md)
- [Nesneler ve sınıflar](../objects-and-classes/index.md)
- [Nesne odaklı programlama (Visual Basic)](../../concepts/object-oriented-programming.md)
