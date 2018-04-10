---
title: Visual Basic'de Veri Türleri
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- data types [Visual Basic], declaring
- typing
- data types [Visual Basic]
- Visual Basic code, data types
- data types [Visual Basic], improving speed with
ms.assetid: 5e1b9aaf-c7ca-4b29-9b22-0e82ed8e85e2
caps.latest.revision: 28
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 20a24c8632e1f2193cfa86319a824dfcc038d9d8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="data-types-in-visual-basic"></a>Visual Basic'de Veri Türleri
*Veri türü* ne tür veriler tutun ve nasıl verileri depolayan bir programlama öğesi başvuruyor. Veri türleri, bilgisayar belleğinde depolanabilir veya bir ifadenin değerlendirmesine katılan tüm değerleri için geçerlidir. Her değişken, değişmez değeri, sabiti, numaralandırma, özellik, yordam parametresini, yordam bağımsız değişkenini ve yordamı dönüş değeri bir veri türü vardır.  
  
## <a name="declared-data-types"></a>Veri türleri bildirilen  
 Bir bildirim deyimi programlama bir öğesiyle tanımlayın ve kendi veri türüyle belirtin `As` yan tümcesi. Aşağıdaki tabloda, çeşitli öğeleri bildirmek için kullandığınız değerlerini gösterir.  
  
|Programlama öğesi|Veri türü bildirimi|  
|-------------------------|---------------------------|  
|Değişken|İçinde bir [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md)<br /><br /> `Dim`   `amount As Double`<br /><br /> `Static`   `yourName As String`<br /><br /> `Public`   `billsPaid As Decimal = 0`|  
|Değişmez değer|Değişmez değer türü karakteri ile; "Değişmez değer türü karakterleri" bölümüne bakın [türü karakterleri](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)<br /><br /> `Dim searchChar As Char = "."`  `C`|  
|Sabit|İçinde bir [Const deyimi](../../../../visual-basic/language-reference/statements/const-statement.md)<br /><br /> `Const`   `modulus As Single = 4.17825F`|  
|Sabit Listesi|İçinde bir [Enum deyimi](../../../../visual-basic/language-reference/statements/enum-statement.md)<br /><br /> `Public`   `Enum`   `colors`|  
|Özellik|İçinde bir [Property deyimi](../../../../visual-basic/language-reference/statements/property-statement.md)<br /><br /> `Property`   `region() As String`|  
|Yordam parametresi|İçinde bir [Sub deyimi](../../../../visual-basic/language-reference/statements/sub-statement.md), [işlev ifadesi](../../../../visual-basic/language-reference/statements/function-statement.md), veya [Operator deyimi](../../../../visual-basic/language-reference/statements/operator-statement.md)<br /><br /> `Sub addSale(ByVal`   `amount`   `As Double)`|  
|Yordam bağımsız değişken|Çağrıyı yapan kod; Her değişkeni zaten bildirilmiş bir programlama öğesi veya bir ifade içeren bildirilen öğeler<br /><br /> `subString = Left(`  `inputString`  `,`   `5`  `)`|  
|Yordam dönüş değeri|İçinde bir [işlev ifadesi](../../../../visual-basic/language-reference/statements/function-statement.md) veya [Operator deyimi](../../../../visual-basic/language-reference/statements/operator-statement.md)<br /><br /> `Function convert(ByVal b As Byte)`   `As String`|  
  
 Visual Basic veri türleri listesi için bkz: [veri türleri](../../../../visual-basic/language-reference/data-types/data-type-summary.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tür karakterleri](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
 [Başlangıç veri türleri](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Bileşik veri türleri](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [Visual Basic'de genel türler](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Değer türleri ve başvuru türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Visual Basic'de tür dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Yapıları](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Diziler](tuples.md)     
 [Veri türleri sorunlarını giderme](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Veri türleri](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Veri türlerinin etkili kullanımı](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
