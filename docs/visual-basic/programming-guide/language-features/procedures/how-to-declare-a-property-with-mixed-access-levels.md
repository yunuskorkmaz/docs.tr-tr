---
title: "Nasıl yapılır: Bir Özelliği Karışık Erişim Düzeyleriyle Bildirme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- access levels [Visual Basic], properties
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- mixed access levels
- Visual Basic code, properties
- properties [Visual Basic], access levels
- Property statement [Visual Basic], declaring mixed access levels
ms.assetid: fdbb2d97-279a-4956-b26c-cbdfbc34915a
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 90fe20303f6f2ed692e54e44ee8cc65897531543
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-a-property-with-mixed-access-levels-visual-basic"></a>Nasıl yapılır: Bir Özelliği Karışık Erişim Düzeyleriyle Bildirme (Visual Basic)
İsterseniz `Get` ve `Set` yordamlarını bir özelliğe farklı erişim düzeyleri olması, daha fazla izin düzeyi kullanabilir `Property` deyimi ve ya da daha kısıtlayıcı düzeyi `Get` veya `Set` deyimi. Belirli özelliğin değerini almak kod parçalarını ve belirli bir değeri değiştirmek kod bölümlerini istediğinizde bir özelliği karışık erişim düzeyleri kullanın.  
  
 Erişim düzeyleri hakkında daha fazla bilgi için bkz: [erişim düzeyini Visual Basic'te](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
### <a name="to-declare-a-property-with-mixed-access-levels"></a>Bir özelliği karışık erişim düzeyleriyle bildirme  
  
1.  Normal bir şekilde özelliği bildirme ve daha az kısıtlayıcı erişim düzeyini belirtin (gibi `Public`) içinde `Property` deyimi.  
  
2.  Ya da bildirme `Get` veya `Set` daha kısıtlayıcı erişim düzeyini belirterek yordamı (gibi `Friend`).  
  
3.  Erişim düzeyi, bir özellik yordamı üzerinde belirtmeyin. Bildirilen erişim düzeyi varsayar `Property` deyimi. Özellik yordamları yalnızca birinde erişimi kısıtlayabilirsiniz.  
  
     [!code-vb[VbVbcnProcedures#10](./codesnippet/VisualBasic/how-to-declare-a-property-with-mixed-access-levels_1.vb)]  
  
     Önceki örnekte `Get` yordamı sahip aynı `Protected` özelliği kendisini olarak erişim sırada `Set` yordamı sahip `Private` erişim. Öğesinden türetilmiş bir sınıf `employee` okuyabilirsiniz `salary` değeri, ancak yalnızca `employee` sınıfı ayarlayabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yordamları](./index.md)  
 [Özellik yordamları](./property-procedures.md)  
 [Parametreler ve bağımsız değişkenler](./procedure-parameters-and-arguments.md)  
 [Property deyimi](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [Visual Basic'de özellikler ve değişkenler arasındaki farklar](./differences-between-properties-and-variables.md)  
 [Nasıl yapılır: özellik oluşturma](./how-to-create-a-property.md)  
 [Nasıl yapılır: bir özellik yordamı çağırma](./how-to-call-a-property-procedure.md)  
 [Nasıl yapılır: bildirme ve Visual Basic'te varsayılan özelliğini çağırın](./how-to-declare-and-call-a-default-property.md)  
 [Nasıl yapılır: bir özelliğe değer ekleme](./how-to-put-a-value-in-a-property.md)  
 [Nasıl yapılır: bir özellikten değer alma](./how-to-get-a-value-from-a-property.md)
