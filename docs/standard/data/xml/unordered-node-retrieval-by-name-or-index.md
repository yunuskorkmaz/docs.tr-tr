---
title: Ada veya dizine göre sırasız düğüm alma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 2038a90b-92af-4a0a-baaa-08e688d95194
author: mairaw
ms.author: mairaw
ms.openlocfilehash: da1c9f25052bb2354b435cd28b7ff55d4a754ed1
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46287364"
---
# <a name="unordered-node-retrieval-by-name-or-index"></a><span data-ttu-id="8cdbe-102">Ada veya dizine göre sırasız düğüm alma</span><span class="sxs-lookup"><span data-stu-id="8cdbe-102">Unordered Node Retrieval by Name or Index</span></span>
<span data-ttu-id="8cdbe-103">**XmlNamedNodeMap** NamedNodeMap olarak World Wide Web Consortium (W3C) belirtimi açıklanmıştır ve bunların adı veya dizin tarafından başvuru düğümleri olanağı sırasız bir dizi düğümü işlemek için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="8cdbe-103">The **XmlNamedNodeMap** is described in the World Wide Web Consortium (W3C) specification as the NamedNodeMap and is required to handle an unordered set of nodes with the ability to reference nodes by their name or index.</span></span> <span data-ttu-id="8cdbe-104">Tek yolu erişiminiz bir **XmlNamedNodeMap** olduğunda bir **XmlNamedNodeMap** bir yöntem veya özellik ile döndürülür.</span><span class="sxs-lookup"><span data-stu-id="8cdbe-104">The only way you have access to an **XmlNamedNodeMap** is when an **XmlNamedNodeMap** is returned through a method or property.</span></span> <span data-ttu-id="8cdbe-105">Üç yöntem veya döndüren özellikler bir **XmlNamedNodeMap**:</span><span class="sxs-lookup"><span data-stu-id="8cdbe-105">There are three methods or properties that return an **XmlNamedNodeMap**:</span></span>  
  
-   <span data-ttu-id="8cdbe-106">XmlElement.Attributes</span><span class="sxs-lookup"><span data-stu-id="8cdbe-106">XmlElement.Attributes</span></span>  
  
-   <span data-ttu-id="8cdbe-107">XmlDocumentType.Entities</span><span class="sxs-lookup"><span data-stu-id="8cdbe-107">XmlDocumentType.Entities</span></span>  
  
-   <span data-ttu-id="8cdbe-108">XmlDocumentType.Notations</span><span class="sxs-lookup"><span data-stu-id="8cdbe-108">XmlDocumentType.Notations</span></span>  
  
 <span data-ttu-id="8cdbe-109">Örneğin, **XmlDocumentType.Entities** özellik koleksiyonunu alır **XmlEntity** düğümleri belge türü bildirimi içinde bildirilmiş.</span><span class="sxs-lookup"><span data-stu-id="8cdbe-109">For example, the **XmlDocumentType.Entities** property gets the collection of **XmlEntity** nodes declared in the document type declaration.</span></span> <span data-ttu-id="8cdbe-110">Bu koleksiyonu olarak döndürülür bir **XmlNamedNodeMap**, ve kullanımı ile bir koleksiyon üzerinden yineleme **sayısı** özelliği ve görüntü varlık bilgileri.</span><span class="sxs-lookup"><span data-stu-id="8cdbe-110">This collection is returned as an **XmlNamedNodeMap**, and you can iterate through the collection with the use of the **Count** property and display entity information.</span></span> <span data-ttu-id="8cdbe-111">Bir örnek üzerinden yineleme için bir **XmlNamedNodeMap**, bkz: <xref:System.Xml.XmlDocumentType.Entities%2A>.</span><span class="sxs-lookup"><span data-stu-id="8cdbe-111">For an example of iterating through an **XmlNamedNodeMap**, see <xref:System.Xml.XmlDocumentType.Entities%2A>.</span></span>  
  
 <span data-ttu-id="8cdbe-112">**XmlAttributeCollection** türetilir **XmlNamedNodeMap** ve gösterimler ve varlıkların salt okunur olsa yalnızca öznitelikler değiştirilebilir,.</span><span class="sxs-lookup"><span data-stu-id="8cdbe-112">The **XmlAttributeCollection** is derived from **XmlNamedNodeMap** and only attributes are modifiable, while notations and entities are read-only.</span></span> <span data-ttu-id="8cdbe-113">Kullanarak **XmlNamedNodeMap** öznitelikler için kendi XML adlarına göre bu öznitelikleri için düğümleri alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8cdbe-113">Using the **XmlNamedNodeMap** for the attributes, you can get nodes for those attributes based on their XML names.</span></span> <span data-ttu-id="8cdbe-114">Bu, bir öğe düğümü üzerinde özniteliklerin koleksiyonunu yönetmek için kolay bir yöntemini sağlar.</span><span class="sxs-lookup"><span data-stu-id="8cdbe-114">This provides an easy method for manipulating the collection of attributes on an element node.</span></span> <span data-ttu-id="8cdbe-115">Bu doğrudan karşıtlıklar **XmlNodeList**, ayrıca uygulayan **IEnumerable** arabirimi, ancak dizin erişimci yerine bir dize.</span><span class="sxs-lookup"><span data-stu-id="8cdbe-115">This can be contrasted directly with **XmlNodeList**, which also implements the **IEnumerable** interface, but with an index accessor rather than a string.</span></span> <span data-ttu-id="8cdbe-116">**RemoveNamedItem** ve **SetNamedItem** yöntemleri karşı kullanılan yalnızca bir **XmlAttributeCollection**.</span><span class="sxs-lookup"><span data-stu-id="8cdbe-116">The **RemoveNamedItem** and **SetNamedItem** methods are only used against an **XmlAttributeCollection**.</span></span> <span data-ttu-id="8cdbe-117">Ekleme veya bir öznitelik koleksiyonundan olup olmadığını kaldırma **AttributeCollection** veya **XmlNamedNodeMap** uygulama, öznitelik koleksiyonundan öğesindeki değiştirir.</span><span class="sxs-lookup"><span data-stu-id="8cdbe-117">Adding or removing from an attribute collection, whether using the **AttributeCollection** or the **XmlNamedNodeMap** implementation, modifies the attribute collection on the element.</span></span> <span data-ttu-id="8cdbe-118">Aşağıdaki kod örneği, bir özniteliği Taşı ve yeni bir öznitelik oluşturmak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8cdbe-118">The following code example shows how to move an attribute and create a new attribute.</span></span>  
  
```vb  
Imports System  
Imports System.Xml  
  
Class test  
  
    Public Shared Sub Main()  
        Dim doc As New XmlDocument()  
        doc.LoadXml("<root> <child1 attr1='val1' attr2='val2'> text1 </child1> <child2 attr3='val3'> text2 </child2> </root> ")  
  
        ' Get the attributes of node "child2 "  
        Dim ac As XmlAttributeCollection = doc.DocumentElement.ChildNodes(1).Attributes  
  
        ' Print out the number of attributes and their names.  
        Console.WriteLine(("Number of Attributes: " + ac.Count))  
        Dim i As Integer  
        For i = 0 To ac.Count - 1  
            Console.WriteLine((i + 1 + ".  Attribute Name: '" + ac(i).Name + "'  Attribute Value:  '" + ac(i).Value + "'"))  
        Next i  
        ' Get the 'attr1' from child1.  
        Dim attr As XmlAttribute = doc.DocumentElement.ChildNodes(0).Attributes(0)  
  
        ' Add this attribute to the attributecollection "ac".  
        ac.SetNamedItem(attr)  
  
        ''attr1' will be removed from 'child1' and added to 'child2'.  
        ' Print out the number of attributes and their names.  
        Console.WriteLine(("Number of Attributes: " + ac.Count))  
  
        For i = 0 To ac.Count - 1  
            Console.WriteLine((i + 1 + ".  Attribute Name: '" + ac(i).Name + "'  Attribute Value:  '" + ac(i).Value + "'"))  
        Next i  
        ' Create a new attribute and add to the collection.  
        Dim attr2 As XmlAttribute = doc.CreateAttribute("attr4")  
        attr2.Value = "val4"  
        ac.SetNamedItem(attr2)  
  
        ' Print out the number of attributes and their names.  
        Console.WriteLine(("Number of Attributes: " + ac.Count))  
  
        For i = 0 To ac.Count - 1  
            Console.WriteLine((i + 1 + ".  Attribute Name: '" + ac(i).Name + "'  Attribute Value:  '" + ac(i).Value + "'"))  
        Next i  
    End Sub 'Main  
End Class 'test  
```  
  
```csharp  
using System;  
using System.Xml;  
class test {  
    public static void Main() {  
        XmlDocument doc = new XmlDocument();  
        doc.LoadXml( "<root> <child1 attr1='val1' attr2='val2'> text1 </child1> <child2 attr3='val3'> text2 </child2> </root> " );  
  
        // Get the attributes of node "child2"  
        XmlAttributeCollection ac = doc.DocumentElement.ChildNodes[1].Attributes;  
  
        // Print out the number of attributes and their names.  
        Console.WriteLine( "Number of Attributes: "+ac.Count );  
        for( int i = 0; i < ac.Count; i++ )  
            Console.WriteLine( (i+1) + ".  Attribute Name: '" +ac[i].Name+ "'  Attribute Value:  '"+ ac[i].Value +"'" );   
  
        // Get the 'attr1' from child1.  
        XmlAttribute attr = doc.DocumentElement.ChildNodes[0].Attributes[0];  
  
        // Add this attribute to the attributecollection "ac".  
        ac.SetNamedItem( attr );  
  
        // 'attr1' will be removed from 'child1' and added to 'child2'.  
        // Print out the number of attributes and their names.  
        Console.WriteLine( "Number of Attributes: "+ac.Count );          
        for( int i = 0; i < ac.Count; i++ )  
            Console.WriteLine( (i+1) + ".  Attribute Name: '" +ac[i].Name+ "'  Attribute Value:  '"+ ac[i].Value +"'" );   
  
        // Create a new attribute and add to the collection.  
        XmlAttribute attr2 = doc.CreateAttribute( "attr4" );  
        attr2.Value = "val4";  
        ac.SetNamedItem( attr2 );  
  
        // Print out the number of attributes and their names.  
        Console.WriteLine( "Number of Attributes: "+ac.Count );          
        for( int i = 0; i < ac.Count; i++ )  
            Console.WriteLine( (i+1) + ".  Attribute Name: '" +ac[i].Name+ "'  Attribute Value:  '"+ ac[i].Value +"'" );           
  
    }  
}  
```  
  
 <span data-ttu-id="8cdbe-119">Öğesinden kaldırılan bir öznitelik gösteren ek kod örneği görmek için bir **AttributeCollection**, bkz: [XmlNamedNodeMap.RemoveNamedItem yöntemi](Overload:System.Xml.XmlNamedNodeMap.RemoveNamedItem).</span><span class="sxs-lookup"><span data-stu-id="8cdbe-119">To see an additional code example which shows an attribute being removed from an **AttributeCollection**, see [XmlNamedNodeMap.RemoveNamedItem Method](Overload:System.Xml.XmlNamedNodeMap.RemoveNamedItem).</span></span> <span data-ttu-id="8cdbe-120">Özellikler ve yöntemler hakkında daha fazla bilgi için bkz. [XmlNamedNodeMap üyeleri](AllMembers.T:System.Xml.XmlNamedNodeMap).</span><span class="sxs-lookup"><span data-stu-id="8cdbe-120">For more information on the methods and properties, see [XmlNamedNodeMap Members](AllMembers.T:System.Xml.XmlNamedNodeMap).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cdbe-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8cdbe-121">See also</span></span>

- [<span data-ttu-id="8cdbe-122">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="8cdbe-122">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
