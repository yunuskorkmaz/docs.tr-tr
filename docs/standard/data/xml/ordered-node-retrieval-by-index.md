---
title: Düğüm alma dizine göre sıralı
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 5412c90f-2703-4aa8-a9c4-1b8a35183c37
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 515edf26df6190d2bf4906f3de2d019b1a4175fb
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45512510"
---
# <a name="ordered-node-retrieval-by-index"></a><span data-ttu-id="25fb0-102">Düğüm alma dizine göre sıralı</span><span class="sxs-lookup"><span data-stu-id="25fb0-102">Ordered Node Retrieval by Index</span></span>
<span data-ttu-id="25fb0-103">World Wide Web Consortium (W3C) XML belge nesne modeli (DOM) tarafından işlenen sıralanmamış aksine düğümleri sıralı bir listesi işleyebilme yeteneği olan bir düğüm listesine de açıklar **XmlNamedNodeMap**.</span><span class="sxs-lookup"><span data-stu-id="25fb0-103">The World Wide Web Consortium (W3C) XML Document Object Model (DOM) also describes a NodeList, which has the ability to handle an ordered list of nodes, as opposed to the unordered set handled by the **XmlNamedNodeMap**.</span></span> <span data-ttu-id="25fb0-104">Bir düğüm listesine neden Microsoft .NET Framework adlı **XmlNodeList**.</span><span class="sxs-lookup"><span data-stu-id="25fb0-104">The NodeList in the Microsoft .NET Framework is called **XmlNodeList**.</span></span> <span data-ttu-id="25fb0-105">Yöntemleri ve döndüren özellikler bir **XmlNodeList** şunlardır:</span><span class="sxs-lookup"><span data-stu-id="25fb0-105">Methods and properties that return an **XmlNodeList** are:</span></span>  
  
-   <span data-ttu-id="25fb0-106">XmlNode.ChildNodes</span><span class="sxs-lookup"><span data-stu-id="25fb0-106">XmlNode.ChildNodes</span></span>  
  
-   <span data-ttu-id="25fb0-107">XmlDocument.GetElementsByTagName</span><span class="sxs-lookup"><span data-stu-id="25fb0-107">XmlDocument.GetElementsByTagName</span></span>  
  
-   <span data-ttu-id="25fb0-108">XmlElement.GetElementsByTagName</span><span class="sxs-lookup"><span data-stu-id="25fb0-108">XmlElement.GetElementsByTagName</span></span>  
  
-   <span data-ttu-id="25fb0-109">XmlNode.SelectNodes</span><span class="sxs-lookup"><span data-stu-id="25fb0-109">XmlNode.SelectNodes</span></span>  
  
 <span data-ttu-id="25fb0-110">**XmlNodeList** sahip bir **sayısı** düğümler üzerinden yinelemek için döngüleri yazmak için kullanılan özellik **XmlNodeList**aşağıdaki kod örneğinde gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="25fb0-110">The **XmlNodeList** has a **Count** property that can be used to write loops to iterate over the nodes in the **XmlNodeList**, as shown in the following code sample:</span></span>  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
   doc.Load("books.xml")  
  
    ' Retrieve all book titles.  
    Dim root as XmlElement = doc.DocumentElement  
    Dim elemList as XmlNodeList = root.GetElementsByTagName("title")  
    Dim i as integer  
    for i=0  to elemList.Count-1  
        ' Display all book titles in the Node List.  
        Console.WriteLine(elemList.ItemOf(i).InnerXml)  
    next  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.Load("books.xml");  
// Retrieve all book titles.  
XmlElement root = doc.DocumentElement;  
XmlNodeList elemList = root.GetElementsByTagName("title");  
for (int i=0; i < elemList.Count; i++)  
{     
   // Display all book titles in the Node List.  
   Console.WriteLine(elemList[i].InnerXml);  
}   
```  
  
 <span data-ttu-id="25fb0-111">Ek olarak **sayısı** özelliği var. bir **GetEnumerator** sağlayan yöntemi `foreach` düğümleri koleksiyonu üzerinden yineleme stil **XmlNodeList**.</span><span class="sxs-lookup"><span data-stu-id="25fb0-111">In addition to the **Count** property, there is a **GetEnumerator** method that provides a, `foreach` style iteration over the collection of nodes in the **XmlNodeList**.</span></span> <span data-ttu-id="25fb0-112">Aşağıdaki kod örneği, kullanımını gösterir `foreach` deyimi.</span><span class="sxs-lookup"><span data-stu-id="25fb0-112">The following code example shows the use of the `foreach` statement.</span></span>  
  
```vb  
Dim doc As New XmlDocument()  
doc.Load("books.xml")  
  
' Get book titles.  
Dim root As XmlElement = doc.DocumentElement  
Dim elemList As XmlNodeList = root.GetElementsByTagName("title")  
Dim ienum As IEnumerator = elemList.GetEnumerator()  
' Loop over the XmlNodeList using the enumerator ienum          
While ienum.MoveNext()  
    ' Display the book title.  
    Dim title As XmlNode = CType(ienum.Current, XmlNode)  
    Console.WriteLine(title.InnerText)  
End While  
```  
  
```csharp  
{  
     XmlDocument doc = new XmlDocument();  
     doc.Load("books.xml");  
  
     // Get book titles.  
     XmlElement root = doc.DocumentElement;  
     XmlNodeList elemList = root.GetElementsByTagName("title");  
     IEnumerator ienum = elemList.GetEnumerator();    
     // Loop over the XmlNodeList using the enumerator ienum          
     while (ienum.MoveNext())  
     {  
          // Display the book title.  
           XmlNode title = (XmlNode) ienum.Current;  
           Console.WriteLine(title.InnerText);  
     }  
  }  
```  
  
 <span data-ttu-id="25fb0-113">Kullanılabilir özellikler ve yöntemler hakkında daha fazla bilgi için **XmlNodeList**, bkz: <xref:System.Xml.XmlNodeList>.</span><span class="sxs-lookup"><span data-stu-id="25fb0-113">For more information on the methods and properties available on the **XmlNodeList**, see <xref:System.Xml.XmlNodeList>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25fb0-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25fb0-114">See also</span></span>

- [<span data-ttu-id="25fb0-115">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="25fb0-115">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
