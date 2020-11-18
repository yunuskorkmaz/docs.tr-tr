---
title: Dizine Göre Sıralı Düğüm Alma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5412c90f-2703-4aa8-a9c4-1b8a35183c37
ms.openlocfilehash: 73c31c5249262fe9b6624201bc5b9bd6b1374d1e
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94823751"
---
# <a name="ordered-node-retrieval-by-index"></a><span data-ttu-id="e06fa-102">Dizine Göre Sıralı Düğüm Alma</span><span class="sxs-lookup"><span data-stu-id="e06fa-102">Ordered Node Retrieval by Index</span></span>
<span data-ttu-id="e06fa-103">World Wide Web Konsorsiyumu (W3C) XML Belge Nesne Modeli (DOM), **XmlNamedNodeMap** tarafından işlenen sıralanmamış bir küme aksine, sıralı düğüm listesini işleyebilme özelliğine sahip bir NodeList ' i de açıklar.</span><span class="sxs-lookup"><span data-stu-id="e06fa-103">The World Wide Web Consortium (W3C) XML Document Object Model (DOM) also describes a NodeList, which has the ability to handle an ordered list of nodes, as opposed to the unordered set handled by the **XmlNamedNodeMap**.</span></span> <span data-ttu-id="e06fa-104">Microsoft .NET çerçevesindeki NodeList, **XmlNodeList** olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="e06fa-104">The NodeList in the Microsoft .NET Framework is called **XmlNodeList**.</span></span> <span data-ttu-id="e06fa-105">Bir **XmlNodeList** döndüren yöntemler ve özellikler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e06fa-105">Methods and properties that return an **XmlNodeList** are:</span></span>  
  
- <span data-ttu-id="e06fa-106">XmlNode. ChildNodes</span><span class="sxs-lookup"><span data-stu-id="e06fa-106">XmlNode.ChildNodes</span></span>  
  
- <span data-ttu-id="e06fa-107">XmlDocument. GetElementsByTagName</span><span class="sxs-lookup"><span data-stu-id="e06fa-107">XmlDocument.GetElementsByTagName</span></span>  
  
- <span data-ttu-id="e06fa-108">XmlElement. GetElementsByTagName</span><span class="sxs-lookup"><span data-stu-id="e06fa-108">XmlElement.GetElementsByTagName</span></span>  
  
- <span data-ttu-id="e06fa-109">XmlNode. SelectNodes</span><span class="sxs-lookup"><span data-stu-id="e06fa-109">XmlNode.SelectNodes</span></span>  
  
 <span data-ttu-id="e06fa-110">**XmlNodeList** , aşağıdaki kod örneğinde gösterildiği gibi, **XmlNodeList** içindeki düğümler üzerinde yinelemek için döngüleri yazmak üzere kullanılabilecek bir **Count** özelliğine sahiptir:</span><span class="sxs-lookup"><span data-stu-id="e06fa-110">The **XmlNodeList** has a **Count** property that can be used to write loops to iterate over the nodes in the **XmlNodeList**, as shown in the following code sample:</span></span>  
  
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
  
 <span data-ttu-id="e06fa-111">**Count** özelliğine ek olarak, **GetEnumerator** `foreach` **XmlNodeList** içindeki düğümlerin koleksiyonu üzerinde bir stil yinelemesi sağlayan bir GetEnumerator yöntemi vardır.</span><span class="sxs-lookup"><span data-stu-id="e06fa-111">In addition to the **Count** property, there is a **GetEnumerator** method that provides a, `foreach` style iteration over the collection of nodes in the **XmlNodeList**.</span></span> <span data-ttu-id="e06fa-112">Aşağıdaki kod örneği, ifadesinin kullanımını gösterir `foreach` .</span><span class="sxs-lookup"><span data-stu-id="e06fa-112">The following code example shows the use of the `foreach` statement.</span></span>  
  
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
  
 <span data-ttu-id="e06fa-113">**XmlNodeList** üzerinde bulunan Yöntemler ve özellikler hakkında daha fazla bilgi için bkz <xref:System.Xml.XmlNodeList> ..</span><span class="sxs-lookup"><span data-stu-id="e06fa-113">For more information on the methods and properties available on the **XmlNodeList**, see <xref:System.Xml.XmlNodeList>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e06fa-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e06fa-114">See also</span></span>

- [<span data-ttu-id="e06fa-115">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="e06fa-115">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
