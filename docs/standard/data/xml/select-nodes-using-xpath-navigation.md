---
title: XPath gezintisi kullanarak düğüm seçme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 8e4450dc-56b3-472b-b467-32f5694f83ad
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9e02dd304893e4d9354144c5b412dfd145161c6e
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45557859"
---
# <a name="select-nodes-using-xpath-navigation"></a><span data-ttu-id="b83cb-102">XPath gezintisi kullanarak düğüm seçme</span><span class="sxs-lookup"><span data-stu-id="b83cb-102">Select Nodes Using XPath Navigation</span></span>
<span data-ttu-id="b83cb-103">XML belge nesne modeli (DOM) DOM'da XML Path Language (XPath) sorgusu bilgi gitme kullanmanıza olanak sağlayan yöntemler içerir.</span><span class="sxs-lookup"><span data-stu-id="b83cb-103">The XML Document Object Model (DOM) contains methods that allow you to use XML Path Language (XPath) navigation to query information in the DOM.</span></span> <span data-ttu-id="b83cb-104">XPath tek, belirli bir düğümü bulunamadı veya bazı ölçütleri ile eşleşen tüm düğümleri bulmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b83cb-104">You can use XPath to find a single, specific node or to find all nodes that match some criteria.</span></span>  
  
## <a name="xpath-select-methods"></a><span data-ttu-id="b83cb-105">XPath seçin yöntemleri</span><span class="sxs-lookup"><span data-stu-id="b83cb-105">XPath Select Methods</span></span>  
 <span data-ttu-id="b83cb-106">DOM sınıfları XPath seçimine için iki yöntem sunar: <xref:System.Xml.XmlNode.SelectSingleNode%2A> yöntemi ve <xref:System.Xml.XmlNode.SelectNodes%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b83cb-106">The DOM classes provide two methods for XPath selection: the <xref:System.Xml.XmlNode.SelectSingleNode%2A> method and the <xref:System.Xml.XmlNode.SelectNodes%2A> method.</span></span> <span data-ttu-id="b83cb-107"><xref:System.Xml.XmlNode.SelectSingleNode%2A> Seçim ölçütleriyle eşleşen ilk düğümü yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="b83cb-107">The <xref:System.Xml.XmlNode.SelectSingleNode%2A> method returns the first node that matches the selection criteria.</span></span> <span data-ttu-id="b83cb-108"><xref:System.Xml.XmlNode.SelectNodes%2A> Yöntemi döndürür bir <xref:System.Xml.XmlNodeList> , eşleşen düğümleri içerir.</span><span class="sxs-lookup"><span data-stu-id="b83cb-108">The <xref:System.Xml.XmlNode.SelectNodes%2A> method returns an <xref:System.Xml.XmlNodeList> that contains the matching nodes.</span></span>  
  
 <span data-ttu-id="b83cb-109">Aşağıdaki örnekte <xref:System.Xml.XmlNode.SelectSingleNode%2A> ilk seçmek için `book` son yazarın adı belirtilen ölçütleri karşılayan düğümü.</span><span class="sxs-lookup"><span data-stu-id="b83cb-109">The following example uses the <xref:System.Xml.XmlNode.SelectSingleNode%2A> method to select the first `book` node in which the author's last name meets the specified criteria.</span></span> <span data-ttu-id="b83cb-110">Bu konunun sonunda sağlanır) bookstore.xml dosyasını (giriş dosyası olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b83cb-110">The bookstore.xml file (which is provided at the end of this topic) is used as the input file.</span></span>  
  
```vb  
Dim doc As New XmlDocument()  
doc.Load("bookstore.xml")  
Dim root As XmlNode = doc.DocumentElement  
  
' Add the namespace.  
Dim nsmgr As New XmlNamespaceManager(doc.NameTable)  
nsmgr.AddNamespace("bk", "urn:newbooks-schema")  
  
' Select and display the first node in which the author's   
' last name is Kingsolver.  
Dim node As XmlNode = root.SelectSingleNode( _  
     "descendant::bk:book[bk:author/bk:last-name='Kingsolver']", nsmgr)  
Console.WriteLine(node.InnerXml)  
```  
  
```csharp  
// Load the document and set the root element.  
XmlDocument doc = new XmlDocument();  
doc.Load("bookstore.xml");  
XmlNode root = doc.DocumentElement;  
  
// Add the namespace.  
XmlNamespaceManager nsmgr = new XmlNamespaceManager(doc.NameTable);  
nsmgr.AddNamespace("bk", "urn:newbooks-schema");  
  
// Select and display the first node in which the author's   
// last name is Kingsolver.  
XmlNode node = root.SelectSingleNode(  
    "descendant::bk:book[bk:author/bk:last-name='Kingsolver']", nsmgr);  
Console.WriteLine(node.InnerXml);  
```  
  
 <span data-ttu-id="b83cb-111">Sonraki örnekte <xref:System.Xml.XmlNode.SelectNodes%2A> fiyat olduğu belirtilen miktardan daha fazla kitap düğümleri seçmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b83cb-111">The next example uses the <xref:System.Xml.XmlNode.SelectNodes%2A> method to select all the book nodes in which the price is greater than a specified amount.</span></span> <span data-ttu-id="b83cb-112">Seçili listedeki her bir kitabın fiyatı, on oranında programlı olarak azaltılır.</span><span class="sxs-lookup"><span data-stu-id="b83cb-112">The price for each book in the selected list is then programmatically reduced by ten percent.</span></span> <span data-ttu-id="b83cb-113">Son olarak, güncelleştirilmiş dosyayı konsoluna yazılır.</span><span class="sxs-lookup"><span data-stu-id="b83cb-113">Finally, the updated file is written to the console.</span></span> <span data-ttu-id="b83cb-114">Bu konunun sonunda sağlanır) bookstore.xml dosyasını (giriş dosyası olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b83cb-114">The bookstore.xml file (which is provided at the end of this topic) is used as the input file.</span></span>  
  
```vb  
' Load the document and set the root element.  
Dim doc As New XmlDocument()  
doc.Load("bookstore.xml")  
Dim root As XmlNode = doc.DocumentElement  
  
' Add the namespace.  
Dim nsmgr As New XmlNamespaceManager(doc.NameTable)  
nsmgr.AddNamespace("bk", "urn:newbooks-schema")  
  
' Select all nodes where the book price is greater than 10.00.  
Dim nodeList As XmlNodeList = root.SelectNodes( _  
     "descendant::bk:book[bk:price>10.00]", nsmgr)  
For Each book As XmlNode In nodeList  
     Dim price As Double  
     price = Math.Round(Convert.ToSingle( _  
          book.LastChild.InnerText) * 0.9, 2)  
     book.LastChild.InnerText = price.ToString()  
Next  
  
' Display the updated document.  
doc.Save(Console.Out)  
```  
  
```csharp  
// Load the document and set the root element.  
XmlDocument doc = new XmlDocument();  
doc.Load("bookstore.xml");  
XmlNode root = doc.DocumentElement;  
  
// Add the namespace.  
XmlNamespaceManager nsmgr = new XmlNamespaceManager(doc.NameTable);  
nsmgr.AddNamespace("bk", "urn:newbooks-schema");  
  
// Select all nodes where the book price is greater than 10.00.  
XmlNodeList nodeList = root.SelectNodes(  
     "descendant::bk:book[bk:price>10.00]", nsmgr);  
foreach (XmlNode book in nodeList)  
{  
     // Discount prices by 10%.  
     double price;  
     price = Math.Round(Convert.ToSingle(  
          book.LastChild.InnerText) * 0.9, 2);  
     book.LastChild.InnerText = price.ToString();  
}  
  
// Display the updated document.  
doc.Save(Console.Out);  
```  
  
 <span data-ttu-id="b83cb-115">Yukarıdaki örneklerde, belge öğesi XPath sorgusu başlatın.</span><span class="sxs-lookup"><span data-stu-id="b83cb-115">The examples above start the XPath query at the document element.</span></span> <span data-ttu-id="b83cb-116">XPath için başlangıç noktası ayarı sorgu XPath sorgusu için başlangıç noktası olan bağlam düğümünün ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b83cb-116">Setting the starting point for the XPath query sets the context node, which is the starting point for the XPath query.</span></span> <span data-ttu-id="b83cb-117">Belge öğesi başlatmak istiyor musunuz, ancak belge öğesi ilk alt başlamak istiyorsanız, select deyimini aşağıdaki şekilde kod yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b83cb-117">If you do not want to start at the document element, but want to start from the first child of the document element, you can code the select statement as follows:</span></span>  
  
```vb  
doc.DocumentElement.FirstChild.SelectNodes(. . . )  
```  
  
```csharp  
this doc.DocumentElement.FirstChild.SelectNodes(. . .);  
```  
  
 <span data-ttu-id="b83cb-118">Tüm <xref:System.Xml.XmlNodeList> nesneler, temel alınan belge ile eşitlenir.</span><span class="sxs-lookup"><span data-stu-id="b83cb-118">All <xref:System.Xml.XmlNodeList> objects are synchronized with the underlying document.</span></span> <span data-ttu-id="b83cb-119">Bu nedenle, düğüm listesini yineleme yapmak ve bir düğümün değerini değiştirebilir, düğüm de nereden geldiğini belge güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b83cb-119">Therefore, if you iterate through the node list and modify the value of a node, that node is also updated in the document it came from.</span></span> <span data-ttu-id="b83cb-120">Önceki örnekte bildirimi, bir düğüm değiştirildiğinde seçili <xref:System.Xml.XmlNodeList> temel alınan belge de değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="b83cb-120">Notice in the previous example that when a node is modified in the selected <xref:System.Xml.XmlNodeList> the underlying document is also modified.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b83cb-121">Temel alınan belge değiştirildiğinde seçin yeniden çalıştırmak için önerilir.</span><span class="sxs-lookup"><span data-stu-id="b83cb-121">When the underlying document is modified, it is advisable to rerun the select.</span></span> <span data-ttu-id="b83cb-122">Daha önce değildi veya artık düğümü listeden kaldırılacak neden düğüm listesine eklenecek düğüm neden olabilecek bir değişiklik düğümü ise, düğüm listesini doğru olduğunu garantisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="b83cb-122">If the node modified is one that could cause the node to be added to the node list when it was not previously, or would now cause it to be removed from the node list, there is no guarantee that the node list is now accurate.</span></span>  
  
## <a name="namespaces-in-xpath-expressions"></a><span data-ttu-id="b83cb-123">XPath ifadeleri ad alanları</span><span class="sxs-lookup"><span data-stu-id="b83cb-123">Namespaces in XPath Expressions</span></span>  
 <span data-ttu-id="b83cb-124">XPath ifadeleri ad alanları içerebilir.</span><span class="sxs-lookup"><span data-stu-id="b83cb-124">XPath expressions can include namespaces.</span></span> <span data-ttu-id="b83cb-125">Namespace çözümleme kullanarak desteklenen <xref:System.Xml.XmlNamespaceManager>.</span><span class="sxs-lookup"><span data-stu-id="b83cb-125">Namespace resolution is supported using the <xref:System.Xml.XmlNamespaceManager>.</span></span> <span data-ttu-id="b83cb-126">XPath ifadesi bir önek varsa, önek ve ad alanı URI çifti eklenmelidir <xref:System.Xml.XmlNamespaceManager>ve <xref:System.Xml.XmlNamespaceManager> geçirilir <xref:System.Xml.XmlNode.SelectNodes%28System.String%2CSystem.Xml.XmlNamespaceManager%29> veya <xref:System.Xml.XmlNode.SelectSingleNode%28System.String%2CSystem.Xml.XmlNamespaceManager%29> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b83cb-126">If the XPath expression includes a prefix, the prefix and namespace URI pair must be added to the <xref:System.Xml.XmlNamespaceManager>, and the <xref:System.Xml.XmlNamespaceManager> is passed to the <xref:System.Xml.XmlNode.SelectNodes%28System.String%2CSystem.Xml.XmlNamespaceManager%29> or <xref:System.Xml.XmlNode.SelectSingleNode%28System.String%2CSystem.Xml.XmlNamespaceManager%29> method.</span></span> <span data-ttu-id="b83cb-127">Yukarıdaki kod örnekleri kullanma bildirimi <xref:System.Xml.XmlNamespaceManager> bookstore.xml belgenin ad alanı çözümlenecek.</span><span class="sxs-lookup"><span data-stu-id="b83cb-127">Notice that the code examples above use the <xref:System.Xml.XmlNamespaceManager> to resolve the namespace of the bookstore.xml document.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b83cb-128">XPath ifadesi bir önek yoksa, ad alanı Tekdüzen Kaynak Tanımlayıcısı (URI) boş ad alanı olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="b83cb-128">If the XPath expression does not include a prefix, it is assumed that the namespace Uniform Resource Identifier (URI) is the empty namespace.</span></span> <span data-ttu-id="b83cb-129">XML dosyanızı varsayılan ad alanı varsa, yine de bir önek ve ad alanı URI eklemelisiniz için <xref:System.Xml.XmlNamespaceManager>; Aksi takdirde, düğüm seçilir.</span><span class="sxs-lookup"><span data-stu-id="b83cb-129">If your XML includes a default namespace, you must still add a prefix and namespace URI to the <xref:System.Xml.XmlNamespaceManager>; otherwise, no nodes will be selected.</span></span>  
  
#### <a name="input-file"></a><span data-ttu-id="b83cb-130">Giriş Dosyası</span><span class="sxs-lookup"><span data-stu-id="b83cb-130">Input File</span></span>  
 <span data-ttu-id="b83cb-131">Bu konudaki örneklerde giriş dosyası olarak kullanılan bookstore.xml dosyası aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="b83cb-131">The following is the bookstore.xml file that is used as the input file in the examples in this topic:</span></span>  
  
```xml  
<?xml version='1.0'?>  
<bookstore xmlns="urn:newbooks-schema">  
  <book genre="novel" style="hardcover">  
    <title>The Handmaid's Tale</title>  
    <author>  
      <first-name>Margaret</first-name>  
      <last-name>Atwood</last-name>  
    </author>  
    <price>19.95</price>  
  </book>  
  <book genre="novel" style="other">  
    <title>The Poisonwood Bible</title>  
    <author>  
      <first-name>Barbara</first-name>  
      <last-name>Kingsolver</last-name>  
    </author>  
    <price>11.99</price>  
  </book>  
  <book genre="novel" style="paperback">  
    <title>The Bean Trees</title>  
    <author>  
      <first-name>Barbara</first-name>  
      <last-name>Kingsolver</last-name>  
    </author>  
    <price>5.99</price>  
  </book>  
</bookstore>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b83cb-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b83cb-132">See also</span></span>

- [<span data-ttu-id="b83cb-133">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="b83cb-133">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
