---
title: Visual Basic'de Veri Türleri
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], declaring
- typing
- data types [Visual Basic]
- Visual Basic code, data types
- data types [Visual Basic], improving speed with
ms.assetid: 5e1b9aaf-c7ca-4b29-9b22-0e82ed8e85e2
ms.openlocfilehash: 83c3d9976f61513165e917da73dd50e846db3e83
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44205698"
---
# <a name="data-types-in-visual-basic"></a>Visual Basic'de Veri Türleri
*Veri türü* programlama öğesinin, içerebileceği verilerin türünü ve bu verileri nasıl depoladı ifade eder. Veri türleri, bilgisayar belleğinde depolanabilir veya bir ifade değerlendirmesi katılabilirsiniz tüm değerleri için geçerlidir. Her değişken, değişmez değeri, sabiti, numaralandırma, özellik, yordam parametresi, yordam bağımsız değişkeninin ve yordamın dönüş değerini bir veri türüne sahip.  
  
## <a name="declared-data-types"></a>Veri türleri bildirilen  
 Bir bildirim deyiminin olan bir programlama öğesi tanımlayın ve veri türünü belirtmeniz `As` yan tümcesi. Aşağıdaki tabloda, çeşitli öğeleri bildirmek için kullandığınız deyimleri gösterilmektedir.  
  
|Programlama öğesi|Veri türü bildirimi|  
|-------------------------|---------------------------|  
|Değişken|İçinde bir [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md)<br /><br /> `Dim`   `amount As Double`<br /><br /> `Static`   `yourName As String`<br /><br /> `Public`   `billsPaid As Decimal = 0`|  
|değişmez değer|Değişmez değer türü karakteri ile; "Değişmez değer türü karakterleri" bölümüne bakın [türü karakterleri](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)<br /><br /> `Dim searchChar As Char = "."`  `C`|  
|Sabit|İçinde bir [Const deyimi](../../../../visual-basic/language-reference/statements/const-statement.md)<br /><br /> `Const`   `modulus As Single = 4.17825F`|  
|Sabit Listesi|İçinde bir [Enum deyimi](../../../../visual-basic/language-reference/statements/enum-statement.md)<br /><br /> `Public`   `Enum`   `colors`|  
|Özellik|İçinde bir [Property deyimi](../../../../visual-basic/language-reference/statements/property-statement.md)<br /><br /> `Property`   `region() As String`|  
|Yordam parametresi|İçinde bir [Sub deyimi](../../../../visual-basic/language-reference/statements/sub-statement.md), [işlev bildirimi](../../../../visual-basic/language-reference/statements/function-statement.md), veya [Operator deyimi](../../../../visual-basic/language-reference/statements/operator-statement.md)<br /><br /> `Sub addSale(ByVal`   `amount`   `As Double)`|  
|Yordam bağımsız değişkeninin|Çağıran kod; Her değişkeni zaten bildirilmiş bir programlama öğesi veya içeren bir ifadede bildirilen öğeler<br /><br /> `subString = Left(`  `inputString`  `,`   `5`  `)`|  
|Yordam dönüş değeri|İçinde bir [işlev bildirimi](../../../../visual-basic/language-reference/statements/function-statement.md) veya [Operator deyimi](../../../../visual-basic/language-reference/statements/operator-statement.md)<br /><br /> `Function convert(ByVal b As Byte)`   `As String`|  
  
 Visual Basic veri türleri listesi için bkz. [veri türleri](../../../../visual-basic/language-reference/data-types/index.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tür Karakterleri](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
 [Başlangıç Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Bileşik Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [Visual Basic'de genel türler](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Değer Türleri ve Başvuru Türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Visual Basic'de tür dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Yapılar](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Diziler](tuples.md)     
 [Veri Türü Sorunlarını Giderme](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Veri Türleri](../../../../visual-basic/language-reference/data-types/index.md)  
 [Veri Türlerinin Etkili Kullanımı](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
