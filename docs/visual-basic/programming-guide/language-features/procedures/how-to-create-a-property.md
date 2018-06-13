---
title: 'Nasıl yapılır: Özellik Oluşturma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, properties
- properties [Visual Basic]
ms.assetid: 4d229712-6be8-4c5c-bac5-06995ce9185a
ms.openlocfilehash: 6e3faed9880b6417f17ab8fe84bc5162e803c437
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656249"
---
# <a name="how-to-create-a-property-visual-basic"></a>Nasıl yapılır: Özellik Oluşturma (Visual Basic)
Özellik tanımı arasında içine bir `Property` deyimi ve bir `End Property` deyimi. Bu tanımı içinde tanımladığınız bir `Get` yordamı, bir `Set` yordam veya her ikisi de. Bu yordamlar özelliğin tüm kod arasındadır.  
  
 `Get` Yordamı özelliğin değerini alır ve `Set` yordamı depolayan bir değer. Özelliği okuma/yazma erişimine sahip olmasını istiyorsanız, her iki yordamı tanımlamanız gerekir. Salt okunur özelliği için yalnızca tanımladığınız `Get`, ve salt yazılır özelliği için yalnızca tanımladığınız `Set`.  
  
### <a name="to-create-a-property"></a>Bir özellik oluşturmak için  
  
1.  Tüm özellik veya yordamı dışında bir [Property deyimi](../../../../visual-basic/language-reference/statements/property-statement.md), ardından bir `End Property` deyimi.  
  
2.  Özelliği, parametreler alıyorsa izleyin `Property` yordamı sonra parantez içinde parametre listesi adı olan anahtar sözcük.  
  
3.  Parantezler ile izleyin bir `As` yan tümcesini özelliğin değerinin veri türü belirtin. Salt yazılır özellik için bile veri türünü belirtmeniz gerekir.  
  
4.  Ekleme `Get` ve `Set` uygun yordamlar. Aşağıdaki yönergeler bakın.  
  
### <a name="to-create-a-get-procedure-that-retrieves-a-property-value"></a>Get yordamı oluşturmak için bir özellik değeri alır.  
  
1.  Arasında `Property` ve `End Property` deyimleri yazma bir [alma deyimi](../../../../visual-basic/language-reference/statements/get-statement.md)takip eden bir `End Get` deyimi. Herhangi bir parametre tanımlayın gerekmez `Get` yordamı.  
  
2.  Özelliğin değeri arasında almak için kod deyimleri yerleştirin `Get` ve `End Get` deyimleri. Bu kod, diğer hesaplamalar ve oluşturma ve özelliğin değerini döndüren ek olarak veri değişikliklerini içerebilir.  
  
3.  Kullanım bir `Return` çağıran kodu özelliğin değerini döndürmek için deyimi.  
  
 Yazmanız gereken bir `Get` okuma-yazma özelliği için ve salt okunur bir özellik için yordamı. Değil tanımlamalısınız bir `Get` salt yazılır özelliği için yordamı.  
  
### <a name="to-create-a-set-procedure-that-writes-a-propertys-value"></a>Bir özelliğin değerini Yazar kümesi yordam oluşturma  
  
1.  Arasında `Property` ve `End Property` deyimleri yazma bir [Set deyimi](../../../../visual-basic/language-reference/statements/set-statement.md)takip eden bir `End Set` deyimi.  
  
2.  İçinde `Set` deyimi, izleyin `Set` parantez içinde parametre listesi olan anahtar sözcük. Bu parametre listesi çağrıyı yapan kod tarafından geçirilen değeri için en az bir değer parametresini eklemeniz gerekir. Bu değer parametresi için varsayılan ad `Value`, ancak uygun durumlarda farklı bir ad kullanabilirsiniz. Değer parametresi type özelliği aynı verilerine sahip olması gerekir.  
  
3.  Özellik arasında bir değer depolamak üzere kod deyimleri yerleştirin `Set` ve `End Set` deyimleri. Bu kod, diğer hesaplamalar ve doğrulama ve özelliğin değerini depolama yanı sıra veri değişikliklerini içerebilir.  
  
4.  Çağrıyı yapan kod tarafından sağlanan değer kabul etmek için değer parametresini kullanın. Bu değer bir atama deyimde doğrudan depolamak veya depolanması için iç değerini hesaplamak için bir ifadede kullanabilirsiniz.  
  
 Yazmanız gereken bir `Set` yordamı salt yazılır özellik ve okuma-yazma özelliği için. Değil tanımlamalısınız bir `Set` salt okunur bir özellik için yordamı.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir tam ad iki bağlı adları, ad ve Soyadı depolayan bir okuma/yazma özelliği oluşturur. Ne zaman çağıran kodu okur `fullName`, `Get` yordamı iki bağlı adları birleştirir ve tam adını döndürür. Çağrıyı yapan kod yeni bir tam ad atarken `Set` yordamı iki bağlı adlarına bölün dener. Bir alan bulamazsa, tüm ad depolar.  
  
 [!code-vb[VbVbcnProcedures#8](./codesnippet/VisualBasic/how-to-create-a-property_1.vb)]  
  
 Aşağıdaki örnek özellik yordamları tipik çağrı gösterilir `fullName`. İlk çağrıda özellik değerini ayarlar ve ikinci çağrı alır.  
  
 [!code-vb[VbVbcnProcedures#9](./codesnippet/VisualBasic/how-to-create-a-property_2.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yordamlar](./index.md)  
 [Özellik Yordamları](./property-procedures.md)  
 [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)  
 [Visual Basic'de özellikler ve değişkenler arasındaki farklar](./differences-between-properties-and-variables.md)  
 [Nasıl yapılır: Bir Özelliği Karışık Erişim Düzeyleriyle Bildirme](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [Nasıl yapılır: Bir Özellik Yordamı Çağırma](./how-to-call-a-property-procedure.md)  
 [Nasıl yapılır: bildirme ve Visual Basic'te varsayılan özelliğini çağırın](./how-to-declare-and-call-a-default-property.md)  
 [Nasıl yapılır: Bir Özelliğe Değer Ekleme](./how-to-put-a-value-in-a-property.md)  
 [Nasıl yapılır: Bir Özellikten Değer Alma](./how-to-get-a-value-from-a-property.md)
