---
title: 'Nasıl yapılır: bir dize (Visual Basic) ayrıştırılamıyor'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 896e1b4b-f9bd-4975-8bc1-55b6badce1ac
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d0fd7c7adcfbd7e2136d1a652017d470634016b9
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-parse-a-string-visual-basic"></a><span data-ttu-id="da7f1-102">Nasıl yapılır: bir dize (Visual Basic) ayrıştırılamıyor</span><span class="sxs-lookup"><span data-stu-id="da7f1-102">How to: Parse a String (Visual Basic)</span></span>
<span data-ttu-id="da7f1-103">Bu konuda bir XML ağacı C# ' ta oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="da7f1-103">This topic shows how to create an XML tree in C#.</span></span>  
  
## <a name="example"></a><span data-ttu-id="da7f1-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="da7f1-104">Example</span></span>  
 <span data-ttu-id="da7f1-105">Visual Basic'te bir dizeyi kullanarak ayrıştıramıyor `XElement.Parse` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="da7f1-105">You can parse a string in Visual Basic by using the `XElement.Parse` method.</span></span> <span data-ttu-id="da7f1-106">Bununla birlikte bir dizeden XML Ayrıştırma olarak aynı performans cezaları gelen XML değişmez değerleri karşılaşmaz çünkü aşağıdaki kodda gösterildiği gibi XML değişmez değerleri kullanmak için daha verimli olur.</span><span class="sxs-lookup"><span data-stu-id="da7f1-106">However, it is more efficient to use XML literals, as shown in following code, because XML literals do not suffer from the same performance penalties as parsing XML from a string.</span></span>  
  
 <span data-ttu-id="da7f1-107">XML değişmez değerleri kullanarak, yalnızca kopyalayın ve Visual Basic programınızı XML dosyanızı yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="da7f1-107">By using XML literals, you can just copy and paste your XML into your Visual Basic program.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da7f1-108">Metni ayrıştırma veya bir metin dosyasından bir XML belgesi yüklenirken işlevsel yapı az verimli değil.</span><span class="sxs-lookup"><span data-stu-id="da7f1-108">Parsing text or loading an XML document from a text file is less efficient than functional construction.</span></span> <span data-ttu-id="da7f1-109">Kod XML ağacından başlatma metni ayrıştırılamıyor daha işlevsel yapım kullanmak için daha az işlemci zamanı kazanır.</span><span class="sxs-lookup"><span data-stu-id="da7f1-109">If you are initializing an XML tree from code, it takes less processor time to use functional construction than to parse text.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="da7f1-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="da7f1-110">See Also</span></span>  
 [<span data-ttu-id="da7f1-111">Ayrıştırma XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="da7f1-111">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
