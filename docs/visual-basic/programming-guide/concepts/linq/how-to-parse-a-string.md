---
title: 'Nasıl yapılır: Dize Ayrıştırma'
ms.date: 07/20/2015
ms.assetid: 896e1b4b-f9bd-4975-8bc1-55b6badce1ac
ms.openlocfilehash: 0a9076fc516bb8e6bc74732ca252fabfeda43d53
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398018"
---
# <a name="how-to-parse-a-string-visual-basic"></a>Nasıl yapılır: bir dizeyi ayrıştırma (Visual Basic)
Bu konu başlığı altında, C# ' de bir XML ağacının nasıl oluşturulacağı gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Yöntemini kullanarak Visual Basic bir dizeyi ayrıştırabilirsiniz `XElement.Parse` . Ancak, XML değişmez değerleri bir dizeden XML ayrıştırılırken aynı performans yaptırımlarından etkilemediğinden, aşağıdaki kodda gösterildiği gibi XML değişmez değerleri kullanmak daha verimlidir.  
  
 XML sabit değerlerini kullanarak yalnızca XML dosyanızı Visual Basic programınıza kopyalayabilir ve yapıştırabilirsiniz.  
  
> [!NOTE]
> Bir metin dosyasından metin ayrıştırma veya bir XML belgesi yükleme, işlevsel oluşturma işleminden daha az verimlidir. Koddan bir XML ağacı başlatdıysanız, işlevsel oluşturma işlevinin metin ayrıştırılmaya kıyasla daha az işlemci süresi sürer.  
  
```vb  
Dim contacts as XElement = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone Type="home">206-555-0144</Phone>  
            <Phone Type="work">425-555-0145</Phone>  
            <Address>  
            <Street1>123 Main St</Street1>  
            <City>Mercer Island</City>  
            <State>WA</State>  
            <Postal>68042</Postal>  
            </Address>  
            <NetWorth>10</NetWorth>  
        </Contact>  
        <Contact>  
            <Name>Gretchen Rivas</Name>  
            <Phone Type="mobile">206-555-0163</Phone>  
            <Address>  
            <Street1>123 Main St</Street1>  
            <City>Mercer Island</City>  
            <State>WA</State>  
            <Postal>68042</Postal>  
            </Address>  
            <NetWorth>11</NetWorth>  
        </Contact>  
    </Contacts>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML 'yi ayrıştırma (Visual Basic)](parsing-xml.md)
