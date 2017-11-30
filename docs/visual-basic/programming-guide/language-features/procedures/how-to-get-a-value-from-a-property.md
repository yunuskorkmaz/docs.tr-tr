---
title: "Nasıl yapılır: Bir Özellikten Değer Alma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6cde5408ea09398a79a3da01ae9b2d0202c58eaf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a>Nasıl yapılır: Bir Özellikten Değer Alma (Visual Basic)
Bir ifadeyi özellik adı dahil olmak üzere bir özelliğin değerini alır.  
  
 Özelliğin `Get` yordamı değeri alır, ancak siz açıkça, ada göre çağırmayın. Bir değişken kullandığınız özelliğini kullanın. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]özelliğin yordamlara çağrılar.  
  
### <a name="to-retrieve-a-value-from-a-property"></a>Bir özellikten değer almak için  
  
1.  Özellik adı bir ifade bir değişken adı kullanacağınız aynı şekilde kullanın. Bir özellik kullanabileceğiniz bir değişken veya sabit herhangi bir yerde kullanabilirsiniz.  
  
     veya  
  
     Eşittir aşağıdaki özellik adı kullanın (`=`) bir atama deyiminde oturum açın.  
  
     Aşağıdaki örnek değeri okuyan [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] `Now` örtük olarak arama özelliği, kendi `Get` yordamı.  
  
     [!code-vb[VbVbalrDateProperties#4](./codesnippet/VisualBasic/how-to-get-a-value-from-a-property_1.vb)]  
  
2.  Özellik bağımsız değişken alıyorsa, özellik adı bağımsız değişken listesi kapsamak için parantez ile izleyin. Bağımsız değişkenler varsa, isteğe bağlı olarak parantez atlayabilirsiniz.  
  
3.  Bağımsız değişkenler, virgülle ayrılmış parantez içinde bağımsız değişken listesinde yerleştirin. Bağımsız değişkenler özelliği ilgili parametreleri tanımlar aynı sırada sağladığınız emin olun.  
  
 İfade bir değişken olarak yalnızca özelliğin değerini katıldığı sabiti misiniz veya değişkenin veya özelliğin Atama ifadesinin sol tarafında depolanır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yordamları](./index.md)  
 [Özellik yordamları](./property-procedures.md)  
 [Parametreler ve bağımsız değişkenler](./procedure-parameters-and-arguments.md)  
 [Property deyimi](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [Visual Basic'de özellikler ve değişkenler arasındaki farklar](./differences-between-properties-and-variables.md)  
 [Nasıl yapılır: özellik oluşturma](./how-to-create-a-property.md)  
 [Nasıl yapılır: bir özelliği karışık erişim düzeyleriyle bildirme](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [Nasıl yapılır: bir özellik yordamı çağırma](./how-to-call-a-property-procedure.md)  
 [Nasıl yapılır: bildirme ve Visual Basic'te varsayılan özelliğini çağırın](./how-to-declare-and-call-a-default-property.md)  
 [Nasıl yapılır: bir özelliğe değer ekleme](./how-to-put-a-value-in-a-property.md)
