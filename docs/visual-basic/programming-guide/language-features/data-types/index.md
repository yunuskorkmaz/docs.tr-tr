---
title: Veri Türleri
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], declaring
- typing
- data types [Visual Basic]
- Visual Basic code, data types
- data types [Visual Basic], improving speed with
ms.assetid: 5e1b9aaf-c7ca-4b29-9b22-0e82ed8e85e2
ms.openlocfilehash: 01529b36a68b8db6febb80b69a7bd81486a47087
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346357"
---
# <a name="data-types-in-visual-basic"></a>Visual Basic'de Veri Türleri
Bir programlama öğesinin *veri türü* , ne tür verileri tutabileceğini ve bu verileri nasıl depoladığını gösterir. Veri türleri, bilgisayar belleğinde depolanabilecek veya bir ifadenin değerlendirmesine katılan tüm değerlere uygulanır. Her değişken, sabit değer, sabit, numaralandırma, özellik, yordam parametresi, yordam bağımsız değişkeni ve yordam dönüş değeri bir veri türüne sahiptir.  
  
## <a name="declared-data-types"></a>Belirtilen veri türleri  
 Bir WITH bildirim deyimi ile bir programlama öğesi tanımlar ve veri türünü `As` yan tümcesiyle belirlersiniz. Aşağıdaki tabloda, çeşitli öğeleri bildirmek için kullandığınız deyimler gösterilmektedir.  
  
|Programlama öğesi|Veri türü bildirimi|  
|-------------------------|---------------------------|  
|Değişken|Bir [Dim ifadesinde](../../../../visual-basic/language-reference/statements/dim-statement.md)<br /><br /> `Dim`   `amount As Double`<br /><br /> `Static`   `yourName As String`<br /><br /> `Public`   `billsPaid As Decimal = 0`|  
|Ayarını|Sabit bir tür karakteriyle birlikte; [tür karakterinde](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md) "değişmez değer türü karakterleri" başlığına bakın<br /><br /> `Dim searchChar As Char = "."`  `C`|  
|Sabit|[Const ifadesinde](../../../../visual-basic/language-reference/statements/const-statement.md)<br /><br /> `Const`   `modulus As Single = 4.17825F`|  
|Numaralandırma|Bir [enum ifadesinde](../../../../visual-basic/language-reference/statements/enum-statement.md)<br /><br /> `Public`   `Enum`   `colors`|  
|Özellik|Bir [Property ifadesinde](../../../../visual-basic/language-reference/statements/property-statement.md)<br /><br /> `Property`   `region() As String`|  
|Yordam parametresi|Bir [Sub ifadesinde](../../../../visual-basic/language-reference/statements/sub-statement.md), [Function Ifadesinde](../../../../visual-basic/language-reference/statements/function-statement.md)veya [operator ifadesinde](../../../../visual-basic/language-reference/statements/operator-statement.md)<br /><br /> `Sub addSale(ByVal`   `amount`   `As Double)`|  
|Yordam bağımsız değişkeni|Çağıran kodda; Her bağımsız değişken önceden tanımlanmış bir programlama öğesidir veya tanımlanmış öğeleri içeren bir ifade<br /><br /> `subString = Left(`  `inputString`  `,`   `5`  `)`|  
|Yordam dönüş değeri|Bir [Function ifadesinde](../../../../visual-basic/language-reference/statements/function-statement.md) veya [işleç ifadesinde](../../../../visual-basic/language-reference/statements/operator-statement.md)<br /><br /> `Function convert(ByVal b As Byte)`   `As String`|  
  
 Visual Basic veri türleri listesi için bkz. [veri türleri](../../../../visual-basic/language-reference/data-types/index.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tür Karakterleri](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [Başlangıç Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Bileşik Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Visual Basic genel türler](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Değer Türleri ve Başvuru Türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Visual Basic dönüşümler yazın](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Yapılar](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Demetler](tuples.md)
- [Veri Türü Sorunlarını Giderme](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Veri Türleri](../../../../visual-basic/language-reference/data-types/index.md)
- [Veri Türlerinin Etkili Kullanımı](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
