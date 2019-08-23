---
title: 'Nasıl yapılır: Bir dizeyi ayrıştırma (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 896e1b4b-f9bd-4975-8bc1-55b6badce1ac
ms.openlocfilehash: b97ce93c1018ec48649ab8b259d5f1a07109b9fe
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956372"
---
# <a name="how-to-parse-a-string-visual-basic"></a><span data-ttu-id="b68e2-102">Nasıl yapılır: Bir dizeyi ayrıştırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b68e2-102">How to: Parse a String (Visual Basic)</span></span>
<span data-ttu-id="b68e2-103">Bu konuda ' de C#bir xml ağacının nasıl oluşturulacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b68e2-103">This topic shows how to create an XML tree in C#.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b68e2-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="b68e2-104">Example</span></span>  
 <span data-ttu-id="b68e2-105">`XElement.Parse` Yöntemini kullanarak Visual Basic bir dizeyi ayrıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b68e2-105">You can parse a string in Visual Basic by using the `XElement.Parse` method.</span></span> <span data-ttu-id="b68e2-106">Ancak, XML değişmez değerleri bir dizeden XML ayrıştırılırken aynı performans yaptırımlarından etkilemediğinden, aşağıdaki kodda gösterildiği gibi XML değişmez değerleri kullanmak daha verimlidir.</span><span class="sxs-lookup"><span data-stu-id="b68e2-106">However, it is more efficient to use XML literals, as shown in following code, because XML literals do not suffer from the same performance penalties as parsing XML from a string.</span></span>  
  
 <span data-ttu-id="b68e2-107">XML sabit değerlerini kullanarak yalnızca XML dosyanızı Visual Basic programınıza kopyalayabilir ve yapıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b68e2-107">By using XML literals, you can just copy and paste your XML into your Visual Basic program.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b68e2-108">Bir metin dosyasından metin ayrıştırma veya bir XML belgesi yükleme, işlevsel oluşturma işleminden daha az verimlidir.</span><span class="sxs-lookup"><span data-stu-id="b68e2-108">Parsing text or loading an XML document from a text file is less efficient than functional construction.</span></span> <span data-ttu-id="b68e2-109">Koddan bir XML ağacı başlatdıysanız, işlevsel oluşturma işlevinin metin ayrıştırılmaya kıyasla daha az işlemci süresi sürer.</span><span class="sxs-lookup"><span data-stu-id="b68e2-109">If you are initializing an XML tree from code, it takes less processor time to use functional construction than to parse text.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b68e2-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b68e2-110">See also</span></span>

- [<span data-ttu-id="b68e2-111">XML 'yi ayrıştırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b68e2-111">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
