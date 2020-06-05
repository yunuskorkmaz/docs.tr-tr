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
ms.openlocfilehash: 928d7fb6a40873641ae3e91e057c272b946a0091
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393720"
---
# <a name="data-types-in-visual-basic"></a>Visual Basic'de Veri Türleri
Bir programlama öğesinin *veri türü* , ne tür verileri tutabileceğini ve bu verileri nasıl depoladığını gösterir. Veri türleri, bilgisayar belleğinde depolanabilecek veya bir ifadenin değerlendirmesine katılan tüm değerlere uygulanır. Her değişken, sabit değer, sabit, numaralandırma, özellik, yordam parametresi, yordam bağımsız değişkeni ve yordam dönüş değeri bir veri türüne sahiptir.  
  
## <a name="declared-data-types"></a>Belirtilen veri türleri  
 Bir WITH bildirimi deyimi ile bir programlama öğesi tanımlarsınız ve onun veri türünü `As` yan tümcesiyle belirlersiniz. Aşağıdaki tabloda, çeşitli öğeleri bildirmek için kullandığınız deyimler gösterilmektedir.  
  
|Programlama öğesi|Veri türü bildirimi|  
|-------------------------|---------------------------|  
|Değişken|Bir [Dim ifadesinde](../../../language-reference/statements/dim-statement.md)<br /><br /> `Dim`   `amount As Double`<br /><br /> `Static`   `yourName As String`<br /><br /> `Public`   `billsPaid As Decimal = 0`|  
|Değişmez değer|Sabit bir tür karakteriyle birlikte; [tür karakterinde](type-characters.md) "değişmez değer türü karakterleri" başlığına bakın<br /><br /> `Dim searchChar As Char = "."`  `C`|  
|Sabit|[Const ifadesinde](../../../language-reference/statements/const-statement.md)<br /><br /> `Const`   `modulus As Single = 4.17825F`|  
|Sabit Listesi|Bir [enum ifadesinde](../../../language-reference/statements/enum-statement.md)<br /><br /> `Public`   `Enum`   `colors`|  
|Özellik|Bir [Property ifadesinde](../../../language-reference/statements/property-statement.md)<br /><br /> `Property`   `region() As String`|  
|Yordam parametresi|Bir [Sub ifadesinde](../../../language-reference/statements/sub-statement.md), [Function Ifadesinde](../../../language-reference/statements/function-statement.md)veya [operator ifadesinde](../../../language-reference/statements/operator-statement.md)<br /><br /> `Sub addSale(ByVal`   `amount`   `As Double)`|  
|Yordam bağımsız değişkeni|Çağıran kodda; Her bağımsız değişken önceden tanımlanmış bir programlama öğesidir veya tanımlanmış öğeleri içeren bir ifade<br /><br /> `subString = Left(`  `inputString`  `,`   `5`  `)`|  
|Yordam dönüş değeri|Bir [Function ifadesinde](../../../language-reference/statements/function-statement.md) veya [işleç ifadesinde](../../../language-reference/statements/operator-statement.md)<br /><br /> `Function convert(ByVal b As Byte)`   `As String`|  
  
 Visual Basic veri türleri listesi için bkz. [veri türleri](../../../language-reference/data-types/index.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tür Karakterleri](type-characters.md)
- [Başlangıç Veri Türleri](elementary-data-types.md)
- [Bileşik Veri Türleri](composite-data-types.md)
- [Visual Basic genel türler](generic-types.md)
- [Değer Türleri ve Başvuru Türleri](value-types-and-reference-types.md)
- [Visual Basic'de Tür Dönüştürmeleri](type-conversions.md)
- [Yapılar](structures.md)
- [Demetler](tuples.md)
- [Veri Türü Sorunlarını Giderme](troubleshooting-data-types.md)
- [Veri türleri](../../../language-reference/data-types/index.md)
- [Veri Türlerinin Etkili Kullanımı](efficient-use-of-data-types.md)
