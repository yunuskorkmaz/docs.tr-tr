---
title: 'Nasıl yapılır: Bir özelliği (Visual Basic) oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, properties
- properties [Visual Basic]
ms.assetid: 4d229712-6be8-4c5c-bac5-06995ce9185a
ms.openlocfilehash: 91f34de36e88724ccab21097bf54a4604f7eee37
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59306722"
---
# <a name="how-to-create-a-property-visual-basic"></a>Nasıl yapılır: Bir özelliği (Visual Basic) oluşturma
Bir özellik tanımı arasında içine bir `Property` ifadesi ve bir `End Property` deyimi. Bu tanımı içinde tanımladığınız bir `Get` yordamı, bir `Set` yordamı veya her ikisi. Bu yordamlar özelliğin tüm kod arasındadır.  
  
 `Get` Yordamı özelliğin değerini alır ve `Set` yordamı bir değer depolar. Özelliği okuma/yazma erişimine sahip olmasını isterseniz, her iki yordam tanımlamanız gerekir. Bir salt okunur özelliği için yalnızca tanımladığınız `Get`, ve bir salt yazılır özelliği için yalnızca tanımladığınız `Set`.  
  
### <a name="to-create-a-property"></a>Bir özellik oluşturmak için  
  
1. Bir özellik veya yordamı dışında bir [Property deyimi](../../../../visual-basic/language-reference/statements/property-statement.md)ve ardından bir `End Property` deyimi.  
  
2. Parametre özelliği alır, izleyin `Property` yordamı sonra parantez parametre listesinde adıyla anahtar sözcüğü.  
  
3. Parantezler ile izleyin bir `As` yan özelliğinin değeri veri türünü belirtin. Salt yazılır özelliği için bile veri türünü belirtmeniz gerekir.  
  
4. Ekleme `Get` ve `Set` yordamlar, uygun şekilde. Aşağıdaki yönergeler bakın.  
  
### <a name="to-create-a-get-procedure-that-retrieves-a-property-value"></a>Bir özellik değerini alan bir Get yordamı oluşturmak için  
  
1. Arasında `Property` ve `End Property` deyimleri yazma bir [alma deyimi](../../../../visual-basic/language-reference/statements/get-statement.md)ve ardından bir `End Get` deyimi. Herhangi bir parametre tanımlayın gerekmez `Get` yordamı.  
  
2. Arasında özelliğin değerini almak için kod deyimlerini yerleştirin `Get` ve `End Get` deyimleri. Bu kod, diğer hesaplamaları ve oluşturma ve özelliğin değerini döndüren ek olarak, veri değişikliklerini içerebilir.  
  
3. Kullanım bir `Return` çağrıldığı koda bir özelliğin değerini döndürmek için deyimi.  
  
 Yazmanız gereken bir `Get` okuma-yazma özelliği ve salt okunur bir özellik için yordamı. Değil tanımlamalıdır bir `Get` yordam sadece yazılabilir bir özellik için.  
  
### <a name="to-create-a-set-procedure-that-writes-a-propertys-value"></a>Bir özelliğin değerini yazan bir kümesi yordam oluşturmak için  
  
1. Arasında `Property` ve `End Property` deyimleri yazma bir [bildirimine](../../../../visual-basic/language-reference/statements/set-statement.md)ve ardından bir `End Set` deyimi.  
  
2. İçinde `Set` deyimi izleyin `Set` anahtar sözcüğü ile parantez içinde bir parametre listesi. Bu parametre listesi çağıran kod tarafından geçirilen değeri için en az bir değer parametresini eklemeniz gerekir. Bu değer parametresi için varsayılan ad `Value`, ancak uygun olduğunda farklı bir ad kullanabilirsiniz. Değer parametresi, aynı veri özelliği olarak türüne sahip olmalıdır.  
  
3. Özellik arasında bir değeri depolamak için kod deyimlerini yerleştirin `Set` ve `End Set` deyimleri. Bu kod, diğer hesaplamaları ve doğrulama ve özellik değerini depolamak ek olarak, veri değişikliklerini içerebilir.  
  
4. Çağıran kod tarafından sağlanan değer kabul etmek için değer parametresini kullanın. Bu değer bir atama ifadesi doğrudan depolamak veya depolanacak iç değeri hesaplamak için bir deyim içinde kullanın.  
  
 Yazmanız gereken bir `Set` yordamı özelliği salt yazma ve okuma-yazma özelliği için. Değil tanımlamalıdır bir `Set` salt okunur bir özellik için yordamı.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir tam adı, iki bağlı ad, ad ve Soyadı depolayan bir okuma/yazma özelliği oluşturur. Çağıran kod zaman okur `fullName`, `Get` yordam iki bağlı adları birleştirir ve tam adını döndürür. Çağıran kod yeni bir tam ad atarken `Set` yordamı iki bağlı adlarına sonu dener. Bir alan bulamazsa, tüm ad depolar.  
  
 [!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]  
  
 Aşağıdaki örnek özellik yordamları tipik çağrıları gösterir `fullName`. İlk çağrı özellik değerini ayarlayan ve ikinci çağrı alır.  
  
 [!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Özellik Yordamları](./property-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Visual Basic'de Özellikler ve Değişkenler Arasındaki Farklar](./differences-between-properties-and-variables.md)
- [Nasıl yapılır: Bir Özelliği Karışık Erişim Düzeyleriyle Bildirme](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Nasıl yapılır: Bir Özellik Yordamı Çağırma](./how-to-call-a-property-procedure.md)
- [Nasıl yapılır: Bildirme ve Visual Basic'te bir varsayılan özelliğini çağırın](./how-to-declare-and-call-a-default-property.md)
- [Nasıl yapılır: Bir Özelliğe Değer Ekleme](./how-to-put-a-value-in-a-property.md)
- [Nasıl yapılır: Bir Özellikten Değer Alma](./how-to-get-a-value-from-a-property.md)
