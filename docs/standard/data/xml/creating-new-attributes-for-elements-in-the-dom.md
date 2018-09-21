---
title: DOM öğeleri için yeni öznitelikler oluşturma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: dd6dc920-b011-418a-b3db-f1580a7d9251
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 870e800220031338557792fa612d4a3101e79f90
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46507852"
---
# <a name="creating-new-attributes-for-elements-in-the-dom"></a><span data-ttu-id="e18ea-102">DOM öğeleri için yeni öznitelikler oluşturma</span><span class="sxs-lookup"><span data-stu-id="e18ea-102">Creating New Attributes for Elements in the DOM</span></span>
<span data-ttu-id="e18ea-103">Yeni öznitelikler oluşturma öznitelikleri düğümler, ancak bir öğe düğümü özellikleridir ve içerdiği diğer düğüm türleri oluşturmaktan daha farklı bir **XmlAttributeCollection** öğeyle ilişkili.</span><span class="sxs-lookup"><span data-stu-id="e18ea-103">Creating new attributes is different than creating other node types, because attributes are not nodes, but are properties of an element node and are contained in an **XmlAttributeCollection** associated with the element.</span></span> <span data-ttu-id="e18ea-104">Bir öznitelik oluşturun ve öğe eklemek için birden çok yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="e18ea-104">There are multiple ways to create an attribute and attach it to an element:</span></span>  
  
-   <span data-ttu-id="e18ea-105">Öğe düğümü edinin ve kullanın **SetAttribute** o öğenin özniteliği koleksiyona bir öznitelik eklemek için.</span><span class="sxs-lookup"><span data-stu-id="e18ea-105">Get the element node and use **SetAttribute** to add an attribute to the attribute collection of that element.</span></span>  
  
-   <span data-ttu-id="e18ea-106">Oluşturma bir **XmlAttribute** düğümü kullanan **CreateAttribute** yöntemi, öğe düğümü alın ve ardından kullanmak **SetAttributeNode** bu öznitelik koleksiyon düğümü eklemek için öğe.</span><span class="sxs-lookup"><span data-stu-id="e18ea-106">Create an **XmlAttribute** node using the **CreateAttribute** method, get the element node, then use **SetAttributeNode** to add the node to the attribute collection of that element.</span></span>  
  
 <span data-ttu-id="e18ea-107">Aşağıdaki örnek, bir öznitelik kullanarak bir öğe ekleme işlemi gösterilmektedir **SetAttribute** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e18ea-107">The following example shows how to add an attribute to an element using the **SetAttribute** method.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
public class Sample  
  
  public shared sub Main()  
  
  Dim doc as XmlDocument = new XmlDocument()  
  doc.LoadXml("<book xmlns:bk='urn:samples' bk:ISBN='1-861001-57-5'>" & _  
              "<title>Pride And Prejudice</title>" & _  
              "</book>")  
  Dim root as XmlElement = doc.DocumentElement  
  
  'Add a new attribute.  
  root.SetAttribute("genre", "urn:samples", "novel")  
  
  Console.WriteLine("Display the modified XML...")  
  Console.WriteLine(doc.InnerXml)  
  
  end sub  
end class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
  public static void Main()  
  {  
    XmlDocument doc = new XmlDocument();  
    doc.LoadXml("<book xmlns:bk='urn:samples' bk:ISBN='1-861001-57-5'>" +  
                "<title>Pride And Prejudice</title>" +  
                "</book>");  
    XmlElement root = doc.DocumentElement;  
  
    // Add a new attribute.  
    root.SetAttribute("genre", "urn:samples", "novel");  
  
    Console.WriteLine("Display the modified XML...");  
    Console.WriteLine(doc.InnerXml);  
  }  
```  
  
 <span data-ttu-id="e18ea-108">Aşağıdaki örnek yeni bir gösterir kullanarak oluşturulan öznitelik **CreateAttribute** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e18ea-108">The following example shows a new attribute being created using the **CreateAttribute** method.</span></span> <span data-ttu-id="e18ea-109">Daha sonra bir öznitelik koleksiyonu için eklenen öznitelik gösterir **kitap** öğesini kullanarak **SetAttributeNode** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e18ea-109">It then shows the attribute added to the attribute collection of the **book** element using the **SetAttributeNode** method.</span></span>  
  
 <span data-ttu-id="e18ea-110">Aşağıdaki XML verilen:</span><span class="sxs-lookup"><span data-stu-id="e18ea-110">Given the following XML:</span></span>  
  
```xml  
<book genre='novel' ISBN='1-861001-57-5'>  
<title>Pride And Prejudice</title>  
</book>  
```  
  
 <span data-ttu-id="e18ea-111">Yeni bir öznitelik oluşturun ve bir değer verin:</span><span class="sxs-lookup"><span data-stu-id="e18ea-111">create a new attribute and give it a value:</span></span>  
  
```vb  
Dim attr As XmlAttribute = doc.CreateAttribute("publisher")  
   attr.Value = "WorldWide Publishing"  
```  
  
```csharp  
XmlAttribute attr = doc.CreateAttribute("publisher");  
attr.Value = "WorldWide Publishing";  
```  
  
 <span data-ttu-id="e18ea-112">ve öğesine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e18ea-112">and attach it to the element:</span></span>  
  
```vb  
doc.DocumentElement.SetAttributeNode(attr)  
```  
  
```csharp  
doc.DocumentElement.SetAttributeNode(attr);  
```  
  
 <span data-ttu-id="e18ea-113">**Output**</span><span class="sxs-lookup"><span data-stu-id="e18ea-113">**Output**</span></span>  
  
```xml  
<book genre="novel" ISBN="1-861001-57-5" publisher="WorldWide Publishing">  
<title>Pride And Prejudice</title>  
</book>  
```  
  
 <span data-ttu-id="e18ea-114">Tam kod örneği şu yolda bulunabilir: <xref:System.Xml.XmlDocument.CreateAttribute%2A>.</span><span class="sxs-lookup"><span data-stu-id="e18ea-114">The full code sample can be found at <xref:System.Xml.XmlDocument.CreateAttribute%2A>.</span></span>  
  
 <span data-ttu-id="e18ea-115">Oluşturabilirsiniz bir **XmlAttribute** düğüm ve kullanım **Insertbefore** veya **InsertAfter** yöntemleri bir koleksiyon içinde uygun konuma yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="e18ea-115">You can also create an **XmlAttribute** node and use the **InsertBefore** or **InsertAfter** methods to place it in the appropriate position in the collection.</span></span> <span data-ttu-id="e18ea-116">Aynı ada sahip bir öznitelik mevcut öznitelik koleksiyonda zaten varsa **XmlAttribute** koleksiyon ve yeni düğüm kaldırılır **XmlAttribute** düğümüne eklenir.</span><span class="sxs-lookup"><span data-stu-id="e18ea-116">If an attribute with the same name is already present in the attribute collection, the existing **XmlAttribute** node is removed from the collection and the new **XmlAttribute** node is inserted.</span></span> <span data-ttu-id="e18ea-117">Bu aynı şekilde gerçekleştirir **SetAttribute** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e18ea-117">This performs the same way as the **SetAttribute** method.</span></span> <span data-ttu-id="e18ea-118">Var olan bir düğüm yapmak için bir başvuru noktası olarak bir parametre olarak bu yöntemleri ele **Insertbefore** ve **InsertAfter**.</span><span class="sxs-lookup"><span data-stu-id="e18ea-118">These methods take, as a parameter, an existing node as a reference point to do the **InsertBefore** and **InsertAfter**.</span></span> <span data-ttu-id="e18ea-119">Bir başvuru düğümü yeni düğümü için varsayılan ekleneceği konum gösteren sağlayamazsanız **InsertAfter** yöntemdir koleksiyonu başında yeni düğümü eklemek için.</span><span class="sxs-lookup"><span data-stu-id="e18ea-119">If you do not provide a reference node indicating where to insert the new node, the default for the **InsertAfter** method is to insert the new node at the beginning of the collection.</span></span> <span data-ttu-id="e18ea-120">İçin varsayılan konum **Insertbefore**, hiçbir referans düğümün sağlanırsa, koleksiyonun sonuna ulaştı.</span><span class="sxs-lookup"><span data-stu-id="e18ea-120">The default position for the **InsertBefore**, if no reference node is provided, is at the end of the collection.</span></span>  
  
 <span data-ttu-id="e18ea-121">Oluşturduysanız bir **XmlNamedNodeMap** öznitelikleri, öznitelik adı'nı kullanarak ekleyebilirsiniz <xref:System.Xml.XmlNamedNodeMap.SetNamedItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="e18ea-121">If you created an **XmlNamedNodeMap** of attributes, you can add an attribute by name using the <xref:System.Xml.XmlNamedNodeMap.SetNamedItem%2A>.</span></span> <span data-ttu-id="e18ea-122">Daha fazla bilgi için [NamedNodeMaps ve NodeLists içindeki düğüm koleksiyonları](../../../../docs/standard/data/xml/node-collections-in-namednodemaps-and-nodelists.md).</span><span class="sxs-lookup"><span data-stu-id="e18ea-122">For more information, see [Node Collections in NamedNodeMaps and NodeLists](../../../../docs/standard/data/xml/node-collections-in-namednodemaps-and-nodelists.md).</span></span>  
  
## <a name="default-attributes"></a><span data-ttu-id="e18ea-123">Varsayılan öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e18ea-123">Default Attributes</span></span>  
 <span data-ttu-id="e18ea-124">Varsayılan özniteliği için bildirilmiş bir öğe oluşturun, ardından varsayılan değerine sahip yeni bir varsayılan öznitelik XML belge nesne modeli (DOM) tarafından oluşturulur ve öğesine bağlı.</span><span class="sxs-lookup"><span data-stu-id="e18ea-124">If you create an element that is declared to have a default attribute, then a new default attribute with its default value is created by the XML Document Object Model (DOM) and attached to the element.</span></span> <span data-ttu-id="e18ea-125">Varsayılan öznitelik alt düğümler de şu anda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e18ea-125">The child nodes of the default attribute are also created at this time.</span></span>  
  
## <a name="attribute-child-nodes"></a><span data-ttu-id="e18ea-126">Öznitelik alt düğümleri</span><span class="sxs-lookup"><span data-stu-id="e18ea-126">Attribute Child Nodes</span></span>  
 <span data-ttu-id="e18ea-127">Bir öznitelik düğümü değeri alt düğümlerinden olur.</span><span class="sxs-lookup"><span data-stu-id="e18ea-127">The value of an attribute node becomes its child nodes.</span></span> <span data-ttu-id="e18ea-128">Geçerli alt düğümleri yalnızca iki tür vardır: **XmlText** düğümleri ve **XmlEntityReference** düğümleri.</span><span class="sxs-lookup"><span data-stu-id="e18ea-128">There are only two types of valid child nodes: **XmlText** nodes, and **XmlEntityReference** nodes.</span></span> <span data-ttu-id="e18ea-129">Alt düğümleri anlamında gibi yöntemlerin bunlar **işlevi FirstChild** ve **LastChild** alt düğümleri olarak işlemeye.</span><span class="sxs-lookup"><span data-stu-id="e18ea-129">These are child nodes in the sense that methods such as **FirstChild** and **LastChild** process them as child nodes.</span></span> <span data-ttu-id="e18ea-130">Bu ayrım alt düğümleri sahip bir öznitelik, öznitelikler veya öznitelik alt düğümleri kaldırmaya çalışırken önemlidir.</span><span class="sxs-lookup"><span data-stu-id="e18ea-130">This distinction of an attribute having child nodes is important when trying to remove attributes or attribute child nodes.</span></span> <span data-ttu-id="e18ea-131">Daha fazla bilgi için [DOM'da bir öğe düğümünden öznitelikleri kaldırma](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="e18ea-131">For more information, see [Removing Attributes from an Element Node in the DOM](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e18ea-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e18ea-132">See also</span></span>

- [<span data-ttu-id="e18ea-133">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="e18ea-133">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
