---
title: Ada veya Dizine Göre Sırasız Düğüm Alma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 2038a90b-92af-4a0a-baaa-08e688d95194
ms.openlocfilehash: 55ea0e31bb8a2863dc0e0eb30f6ca5700c3110b8
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78155743"
---
# <a name="unordered-node-retrieval-by-name-or-index"></a><span data-ttu-id="8f493-102">Ada veya Dizine Göre Sırasız Düğüm Alma</span><span class="sxs-lookup"><span data-stu-id="8f493-102">Unordered Node Retrieval by Name or Index</span></span>
<span data-ttu-id="8f493-103">**XmlNamedNodeMap** , world WIDE Web KONSORSIYUMU (W3C) belirtiminde NamedNodeMap olarak tanımlanır ve düğümler adına veya dizinine göre başvuru yeteneğine sahip sıralanmamış bir düğüm kümesini işlemek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8f493-103">The **XmlNamedNodeMap** is described in the World Wide Web Consortium (W3C) specification as the NamedNodeMap and is required to handle an unordered set of nodes with the ability to reference nodes by their name or index.</span></span> <span data-ttu-id="8f493-104">**XmlNamedNodeMap** 'e erişiminizin tek yolu, bir **XmlNamedNodeMap** bir yöntem veya özellik aracılığıyla döndürüldüğünde olur.</span><span class="sxs-lookup"><span data-stu-id="8f493-104">The only way you have access to an **XmlNamedNodeMap** is when an **XmlNamedNodeMap** is returned through a method or property.</span></span> <span data-ttu-id="8f493-105">**XmlNamedNodeMap**döndüren üç yöntem veya özellik vardır:</span><span class="sxs-lookup"><span data-stu-id="8f493-105">There are three methods or properties that return an **XmlNamedNodeMap**:</span></span>  
  
- <span data-ttu-id="8f493-106">XmlElement. Attributes</span><span class="sxs-lookup"><span data-stu-id="8f493-106">XmlElement.Attributes</span></span>  
  
- <span data-ttu-id="8f493-107">XmlDocumentType. Entities</span><span class="sxs-lookup"><span data-stu-id="8f493-107">XmlDocumentType.Entities</span></span>  
  
- <span data-ttu-id="8f493-108">XmlDocumentType. gösterimler</span><span class="sxs-lookup"><span data-stu-id="8f493-108">XmlDocumentType.Notations</span></span>  
  
 <span data-ttu-id="8f493-109">Örneğin, **XmlDocumentType. Entities** özelliği, belge türü bildiriminde belirtilen **XmlEntity** düğümlerinin koleksiyonunu alır.</span><span class="sxs-lookup"><span data-stu-id="8f493-109">For example, the **XmlDocumentType.Entities** property gets the collection of **XmlEntity** nodes declared in the document type declaration.</span></span> <span data-ttu-id="8f493-110">Bu koleksiyon bir **XmlNamedNodeMap**olarak döndürülür ve koleksiyon içinde **Count** özelliğinin kullanımıyla ve varlık bilgilerini görüntüleyecek şekilde yineleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f493-110">This collection is returned as an **XmlNamedNodeMap**, and you can iterate through the collection with the use of the **Count** property and display entity information.</span></span> <span data-ttu-id="8f493-111">Bir **XmlNamedNodeMap**aracılığıyla yineleme örneği için bkz <xref:System.Xml.XmlDocumentType.Entities%2A>..</span><span class="sxs-lookup"><span data-stu-id="8f493-111">For an example of iterating through an **XmlNamedNodeMap**, see <xref:System.Xml.XmlDocumentType.Entities%2A>.</span></span>  
  
 <span data-ttu-id="8f493-112">**XmlAttributeCollection** , **XmlNamedNodeMap** 'ten türetilir ve yalnızca öznitelikler değiştirilebilir, ancak gösterimler ve varlıklar salt okunurdur.</span><span class="sxs-lookup"><span data-stu-id="8f493-112">The **XmlAttributeCollection** is derived from **XmlNamedNodeMap** and only attributes are modifiable, while notations and entities are read-only.</span></span> <span data-ttu-id="8f493-113">Öznitelikler için **XmlNamedNodeMap** ' i kullanarak, XML adlarına göre bu özniteliklerin düğümlerini alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f493-113">Using the **XmlNamedNodeMap** for the attributes, you can get nodes for those attributes based on their XML names.</span></span> <span data-ttu-id="8f493-114">Bu, bir öğe düğümündeki özniteliklerin koleksiyonunu işlemek için kolay bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="8f493-114">This provides an easy method for manipulating the collection of attributes on an element node.</span></span> <span data-ttu-id="8f493-115">Bu, doğrudan **XmlNodeList**ile oluşturulabilir, bu da **IEnumerable** arabirimini de uygular, ancak bir dize yerine dizin erişimcisi vardır.</span><span class="sxs-lookup"><span data-stu-id="8f493-115">This can be contrasted directly with **XmlNodeList**, which also implements the **IEnumerable** interface, but with an index accessor rather than a string.</span></span> <span data-ttu-id="8f493-116">**Removenamedidıtem** ve **setnamedidıtem** yöntemleri yalnızca bir **XmlAttributeCollection**ile kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8f493-116">The **RemoveNamedItem** and **SetNamedItem** methods are only used against an **XmlAttributeCollection**.</span></span> <span data-ttu-id="8f493-117">Öznitelik koleksiyonunu ekleme veya kaldırma, **AttributeCollection** veya **XmlNamedNodeMap** uygulamasının kullanılmasına bakılmaksızın, öğesindeki öznitelik koleksiyonunu değiştirir.</span><span class="sxs-lookup"><span data-stu-id="8f493-117">Adding or removing from an attribute collection, whether using the **AttributeCollection** or the **XmlNamedNodeMap** implementation, modifies the attribute collection on the element.</span></span> <span data-ttu-id="8f493-118">Aşağıdaki kod örneği, bir özniteliğin nasıl taşınacağını ve yeni bir özniteliğin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8f493-118">The following code example shows how to move an attribute and create a new attribute.</span></span>  
  
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
  
 <span data-ttu-id="8f493-119">Bir **AttributeCollection**'dan çıkarılan bir özniteliği gösteren ek bir kod örneği görmek için bkz. [XmlNamedNodeMap. Removenamedidıtem yöntemi](xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A).</span><span class="sxs-lookup"><span data-stu-id="8f493-119">To see an additional code example which shows an attribute being removed from an **AttributeCollection**, see [XmlNamedNodeMap.RemoveNamedItem Method](xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A).</span></span> <span data-ttu-id="8f493-120">Yöntemler ve özellikler hakkında daha fazla bilgi için bkz. [XmlNamedNodeMap üyeleri](xref:System.Xml.XmlNamedNodeMap).</span><span class="sxs-lookup"><span data-stu-id="8f493-120">For more information on the methods and properties, see [XmlNamedNodeMap Members](xref:System.Xml.XmlNamedNodeMap).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f493-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f493-121">See also</span></span>

- [<span data-ttu-id="8f493-122">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="8f493-122">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
