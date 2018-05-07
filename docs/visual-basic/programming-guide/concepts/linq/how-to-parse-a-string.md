---
title: 'Nasıl yapılır: bir dize (Visual Basic) ayrıştırılamıyor'
ms.date: 07/20/2015
ms.assetid: 896e1b4b-f9bd-4975-8bc1-55b6badce1ac
ms.openlocfilehash: da12ec98e03acceae375bbed4fc6ad4c2a71ec2d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-parse-a-string-visual-basic"></a>Nasıl yapılır: bir dize (Visual Basic) ayrıştırılamıyor
Bu konuda bir XML ağacı C# ' ta oluşturulacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Visual Basic'te bir dizeyi kullanarak ayrıştıramıyor `XElement.Parse` yöntemi. Bununla birlikte bir dizeden XML Ayrıştırma olarak aynı performans cezaları gelen XML değişmez değerleri karşılaşmaz çünkü aşağıdaki kodda gösterildiği gibi XML değişmez değerleri kullanmak için daha verimli olur.  
  
 XML değişmez değerleri kullanarak, yalnızca kopyalayın ve Visual Basic programınızı XML dosyanızı yapıştırın.  
  
> [!NOTE]
>  Metni ayrıştırma veya bir metin dosyasından bir XML belgesi yüklenirken işlevsel yapı az verimli değil. Kod XML ağacından başlatma metni ayrıştırılamıyor daha işlevsel yapım kullanmak için daha az işlemci zamanı kazanır.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ayrıştırma XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
