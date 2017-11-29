---
title: "Nasıl yapılır: bir dize (Visual Basic) ayrıştırılamıyor"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 896e1b4b-f9bd-4975-8bc1-55b6badce1ac
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 10b80c72cae70437ff812c4b67b2532d708f1e69
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-parse-a-string-visual-basic"></a><span data-ttu-id="25a65-102">Nasıl yapılır: bir dize (Visual Basic) ayrıştırılamıyor</span><span class="sxs-lookup"><span data-stu-id="25a65-102">How to: Parse a String (Visual Basic)</span></span>
<span data-ttu-id="25a65-103">Bu konuda bir XML ağacı C# ' ta oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="25a65-103">This topic shows how to create an XML tree in C#.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25a65-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="25a65-104">Example</span></span>  
 <span data-ttu-id="25a65-105">Bir dizede ayrıştıramıyor [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kullanarak `XElement.Parse` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="25a65-105">You can parse a string in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] by using the `XElement.Parse` method.</span></span> <span data-ttu-id="25a65-106">Bununla birlikte bir dizeden XML Ayrıştırma olarak aynı performans cezaları gelen XML değişmez değerleri karşılaşmaz çünkü aşağıdaki kodda gösterildiği gibi XML değişmez değerleri kullanmak için daha verimli olur.</span><span class="sxs-lookup"><span data-stu-id="25a65-106">However, it is more efficient to use XML literals, as shown in following code, because XML literals do not suffer from the same performance penalties as parsing XML from a string.</span></span>  
  
 <span data-ttu-id="25a65-107">XML değişmez değerleri kullanarak, yalnızca kopyalayabilir ve XML dosyanızı içine yapıştırın, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.</span><span class="sxs-lookup"><span data-stu-id="25a65-107">By using XML literals, you can just copy and paste your XML into your [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="25a65-108">Metni ayrıştırma veya bir metin dosyasından bir XML belgesi yüklenirken işlevsel yapı az verimli değil.</span><span class="sxs-lookup"><span data-stu-id="25a65-108">Parsing text or loading an XML document from a text file is less efficient than functional construction.</span></span> <span data-ttu-id="25a65-109">Kod XML ağacından başlatma metni ayrıştırılamıyor daha işlevsel yapım kullanmak için daha az işlemci zamanı kazanır.</span><span class="sxs-lookup"><span data-stu-id="25a65-109">If you are initializing an XML tree from code, it takes less processor time to use functional construction than to parse text.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="25a65-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="25a65-110">See Also</span></span>  
 [<span data-ttu-id="25a65-111">Ayrıştırma XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="25a65-111">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
