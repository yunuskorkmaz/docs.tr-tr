---
title: "Nasıl yapılır: Yeni Değişken Oluşturma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Dim statement [Visual Basic]
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a6806dcbe9e00cbae77181b79d74ddb9a1e1493f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-new-variable-visual-basic"></a>Nasıl yapılır: Yeni Değişken Oluşturma (Visual Basic)
Sahip bir değişken oluşturmak bir [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md).  
  
### <a name="to-create-a-new-variable"></a>Yeni bir değişken oluşturmak için  
  
1.  Değişken bildirme bir `Dim` deyimi.  
  
    ```  
    Dim newCustomer  
    ```  
  
2.  Değişkenin özellikleri için belirtimleri gibi içeren [özel](../../../../visual-basic/language-reference/modifiers/private.md), [statik](../../../../visual-basic/language-reference/modifiers/static.md), [gölgeleri](../../../../visual-basic/language-reference/modifiers/shadows.md), veya [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md). Daha fazla bilgi için bkz: [bildirilen öğe özellikleri](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).  
  
    ```  
    Public Static newCustomer  
    ```  
  
     İhtiyacınız olmayan `Dim` bildiriminde diğer anahtar sözcükler kullanırsanız, anahtar sözcük.  
  
3.  İzlemeniz gereken değişkenin adını belirtimlere izleyin [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kurallar. Daha fazla bilgi için bkz: [bildirilen öğe adları](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
    ```  
    Public Static newCustomer  
    ```  
  
4.  Adlı izleyin [olarak](../../../../visual-basic/language-reference/statements/as-clause.md) yan tümcesini değişkenin veri türü belirtin.  
  
    ```  
    Public Static newCustomer As Customer  
    ```  
  
     Veri türünü belirtmezseniz varsayılan kullanır: `Object`.  
  
5.  İzleyin `As` yan tümcesi eşittir işareti (`=`) ve değişken ilk değerinin eşittir işaretiyle izleyin.  
  
     [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]Belirtilen değer her çalıştığında değişkenine atar `Dim` deyimi. Bir başlangıç değeri belirtmezseniz, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] ilk içeren kodu girdiğinde değişkenin veri türü için varsayılan başlangıç değeri atar `Dim` deyimi.  
  
     Değişkeni bir başvuru türü ise dahil ederek kendi sınıfının bir örneğini oluşturabilirsiniz [New işleci](../../../../visual-basic/language-reference/operators/new-operator.md) anahtar sözcük `As` yan tümcesi. Kullanmıyorsanız, `New`, ilk değer değişkenin [hiçbir şey](../../../../visual-basic/language-reference/nothing.md).  
  
    ```  
    Public Static newCustomer As New Customer  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [Değişken bildirimi](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Bildirilen öğe adları](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Bildirilen öğe özellikleri](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [Değer türleri ve başvuru türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Deyimleri](../../../../visual-basic/language-reference/statements/index.md)  
 [Yerel tür çıkarımı](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Option Infer deyimi](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
