---
title: "Nasıl yapılır: Bir Özelliğe Değer Ekleme (Visual Basic)"
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
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 44e7c4a92ea3d087c12e74aa2ede33a52c8730cf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a>Nasıl yapılır: Bir Özelliğe Değer Ekleme (Visual Basic)
Bir özellik değeri Atama ifadesinin sol tarafta özellik adını koyarak depolar.  
  
 Özelliğin `Set` yordamı bir değer depolar, ancak siz açıkça, ada göre çağırmayın. Bir değişken kullandığınız özelliğini kullanın. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]özelliğin yordamlara çağrılar.  
  
### <a name="to-store-a-value-in-a-property"></a>Bir özelliğin değeri depolamak için  
  
1.  Özellik adı atama ifadesinin sol taraftaki kullanın.  
  
     Aşağıdaki örnek değerini ayarlar [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] `TimeOfDay` öğlen, örtük çağırma özelliğine kendi `Set` yordamı.  
  
     [!code-vb[VbVbcnProcedures#11](./codesnippet/VisualBasic/how-to-put-a-value-in-a-property_1.vb)]  
  
2.  Özellik bağımsız değişken alıyorsa, özellik adı bağımsız değişken listesi kapsamak için parantez ile izleyin. Bağımsız değişkenler varsa, isteğe bağlı olarak parantez atlayabilirsiniz.  
  
3.  Bağımsız değişkenler, virgülle ayrılmış parantez içinde bağımsız değişken listesinde yerleştirin. Bağımsız değişkenler özelliği ilgili parametreleri tanımlar aynı sırada sağladığınız emin olun.  
  
4.  Atama ifadesinin sağ tarafında oluşturulan değeri özelliğinde depolanır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>  
 [Özellik yordamları](./property-procedures.md)  
 [Parametreler ve bağımsız değişkenler](./procedure-parameters-and-arguments.md)  
 [Property deyimi](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [Visual Basic'de özellikler ve değişkenler arasındaki farklar](./differences-between-properties-and-variables.md)  
 [Nasıl yapılır: özellik oluşturma](./how-to-create-a-property.md)  
 [Nasıl yapılır: bir özelliği karışık erişim düzeyleriyle bildirme](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [Nasıl yapılır: bir özellik yordamı çağırma](./how-to-call-a-property-procedure.md)  
 [Nasıl yapılır: bildirme ve Visual Basic'te varsayılan özelliğini çağırın](./how-to-declare-and-call-a-default-property.md)  
 [Nasıl yapılır: bir özellikten değer alma](./how-to-get-a-value-from-a-property.md)
