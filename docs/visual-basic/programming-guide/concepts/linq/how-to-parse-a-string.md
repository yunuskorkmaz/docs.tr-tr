---
title: 'Nasıl yapılır: Bir dize (Visual Basic) ayrıştırılamıyor'
ms.date: 07/20/2015
ms.assetid: 896e1b4b-f9bd-4975-8bc1-55b6badce1ac
ms.openlocfilehash: 815e94b3b41c2c0cc1d18d598307ab292919bea4
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827308"
---
# <a name="how-to-parse-a-string-visual-basic"></a><span data-ttu-id="74ec5-102">Nasıl yapılır: Bir dize (Visual Basic) ayrıştırılamıyor</span><span class="sxs-lookup"><span data-stu-id="74ec5-102">How to: Parse a String (Visual Basic)</span></span>
<span data-ttu-id="74ec5-103">Bu konuda, bir XML ağacı oluşturma işlemi gösterilmektedir C#.</span><span class="sxs-lookup"><span data-stu-id="74ec5-103">This topic shows how to create an XML tree in C#.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74ec5-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="74ec5-104">Example</span></span>  
 <span data-ttu-id="74ec5-105">Kullanarak, Visual Basic'te bir dizeyi ayrıştırmak `XElement.Parse` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="74ec5-105">You can parse a string in Visual Basic by using the `XElement.Parse` method.</span></span> <span data-ttu-id="74ec5-106">Ancak, XML değişmez değerleri, XML değişmez değerleri, bir dizedeki XML Ayrıştırma olarak aynı performans cezaları gelen karşılaşmaz çünkü aşağıdaki kodda gösterildiği gibi kullanmak daha verimlidir.</span><span class="sxs-lookup"><span data-stu-id="74ec5-106">However, it is more efficient to use XML literals, as shown in following code, because XML literals do not suffer from the same performance penalties as parsing XML from a string.</span></span>  
  
 <span data-ttu-id="74ec5-107">XML değişmez değerlerini kullanarak, yalnızca kopyalayın ve Visual Basic programınızı XML dosyanızı yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="74ec5-107">By using XML literals, you can just copy and paste your XML into your Visual Basic program.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="74ec5-108">Metni ayrıştırma veya bir metin dosyasından bir XML belgesi yüklenirken işlevsel oluşturma verimli değildir.</span><span class="sxs-lookup"><span data-stu-id="74ec5-108">Parsing text or loading an XML document from a text file is less efficient than functional construction.</span></span> <span data-ttu-id="74ec5-109">Bir XML ağacı koddan başlatırken, metin ayrıştırmak üzere daha işlevsel oluşturma kullanmak için daha az işlemci zamanı alır.</span><span class="sxs-lookup"><span data-stu-id="74ec5-109">If you are initializing an XML tree from code, it takes less processor time to use functional construction than to parse text.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="74ec5-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74ec5-110">See also</span></span>

- [<span data-ttu-id="74ec5-111">Ayrıştırma XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="74ec5-111">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
