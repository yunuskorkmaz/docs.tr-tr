---
description: 'Daha fazla bilgi edinin: dizine göre sıralı düğüm alımı'
title: Dizine Göre Sıralı Düğüm Alma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5412c90f-2703-4aa8-a9c4-1b8a35183c37
ms.openlocfilehash: b6bf7491b4e237a0dcd21c1a75a90160425db922
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783293"
---
# <a name="ordered-node-retrieval-by-index"></a><span data-ttu-id="e2b1d-103">Dizine Göre Sıralı Düğüm Alma</span><span class="sxs-lookup"><span data-stu-id="e2b1d-103">Ordered Node Retrieval by Index</span></span>

<span data-ttu-id="e2b1d-104">World Wide Web Konsorsiyumu (W3C) XML Belge Nesne Modeli (DOM), **XmlNamedNodeMap** tarafından işlenen sıralanmamış bir küme aksine, sıralı düğüm listesini işleyebilme özelliğine sahip bir NodeList ' i de açıklar.</span><span class="sxs-lookup"><span data-stu-id="e2b1d-104">The World Wide Web Consortium (W3C) XML Document Object Model (DOM) also describes a NodeList, which has the ability to handle an ordered list of nodes, as opposed to the unordered set handled by the **XmlNamedNodeMap**.</span></span> <span data-ttu-id="e2b1d-105">Microsoft .NET çerçevesindeki NodeList, **XmlNodeList** olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="e2b1d-105">The NodeList in the Microsoft .NET Framework is called **XmlNodeList**.</span></span> <span data-ttu-id="e2b1d-106">Bir **XmlNodeList** döndüren yöntemler ve özellikler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e2b1d-106">Methods and properties that return an **XmlNodeList** are:</span></span>  
  
- <span data-ttu-id="e2b1d-107">XmlNode. ChildNodes</span><span class="sxs-lookup"><span data-stu-id="e2b1d-107">XmlNode.ChildNodes</span></span>  
  
- <span data-ttu-id="e2b1d-108">XmlDocument. GetElementsByTagName</span><span class="sxs-lookup"><span data-stu-id="e2b1d-108">XmlDocument.GetElementsByTagName</span></span>  
  
- <span data-ttu-id="e2b1d-109">XmlElement. GetElementsByTagName</span><span class="sxs-lookup"><span data-stu-id="e2b1d-109">XmlElement.GetElementsByTagName</span></span>  
  
- <span data-ttu-id="e2b1d-110">XmlNode. SelectNodes</span><span class="sxs-lookup"><span data-stu-id="e2b1d-110">XmlNode.SelectNodes</span></span>  
  
 <span data-ttu-id="e2b1d-111">**XmlNodeList** , aşağıdaki kod örneğinde gösterildiği gibi, **XmlNodeList** içindeki düğümler üzerinde yinelemek için döngüleri yazmak üzere kullanılabilecek bir **Count** özelliğine sahiptir:</span><span class="sxs-lookup"><span data-stu-id="e2b1d-111">The **XmlNodeList** has a **Count** property that can be used to write loops to iterate over the nodes in the **XmlNodeList**, as shown in the following code sample:</span></span>  
  
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
  
 <span data-ttu-id="e2b1d-112">**Count** özelliğine ek olarak,  `foreach` **XmlNodeList** içindeki düğümlerin koleksiyonu üzerinde bir stil yinelemesi sağlayan bir GetEnumerator yöntemi vardır.</span><span class="sxs-lookup"><span data-stu-id="e2b1d-112">In addition to the **Count** property, there is a **GetEnumerator** method that provides a, `foreach` style iteration over the collection of nodes in the **XmlNodeList**.</span></span> <span data-ttu-id="e2b1d-113">Aşağıdaki kod örneği, ifadesinin kullanımını gösterir `foreach` .</span><span class="sxs-lookup"><span data-stu-id="e2b1d-113">The following code example shows the use of the `foreach` statement.</span></span>  
  
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
  
 <span data-ttu-id="e2b1d-114">**XmlNodeList** üzerinde bulunan Yöntemler ve özellikler hakkında daha fazla bilgi için bkz <xref:System.Xml.XmlNodeList> ..</span><span class="sxs-lookup"><span data-stu-id="e2b1d-114">For more information on the methods and properties available on the **XmlNodeList**, see <xref:System.Xml.XmlNodeList>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2b1d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2b1d-115">See also</span></span>

- [<span data-ttu-id="e2b1d-116">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="e2b1d-116">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
