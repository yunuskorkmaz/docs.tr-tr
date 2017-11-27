---
title: "XML XPathNavigator kullanarak verileri Kaldır"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 9f436bca-1b96-494b-a6d2-e102c7551752
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 29faf92b26908a37fb122dec00b2d4d6b5f3bf16
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="remove-xml-data-using-xpathnavigator"></a><span data-ttu-id="0798c-102">XML XPathNavigator kullanarak verileri Kaldır</span><span class="sxs-lookup"><span data-stu-id="0798c-102">Remove XML Data using XPathNavigator</span></span>
<span data-ttu-id="0798c-103"><xref:System.Xml.XPath.XPathNavigator> Sınıfı düğümleri ve değerleri bir XML belgesinden kaldırmak için kullanılan yöntemler kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="0798c-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to remove nodes and values from an XML document.</span></span> <span data-ttu-id="0798c-104">Bu yöntemleri kullanmak için <xref:System.Xml.XPath.XPathNavigator> nesnesi olmalıdır düzenlenebilir, diğer bir deyişle, kendi <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> olmalıdır `true`.</span><span class="sxs-lookup"><span data-stu-id="0798c-104">In order to use these methods, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be `true`.</span></span>  
  
 <span data-ttu-id="0798c-105"><xref:System.Xml.XPath.XPathNavigator>tarafından oluşturulan bir XML belgesi düzenleyebilirsiniz nesneleri <xref:System.Xml.XmlDocument.CreateNavigator%2A> yöntemi <xref:System.Xml.XmlDocument> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0798c-105"><xref:System.Xml.XPath.XPathNavigator> objects that can edit an XML document are created by the <xref:System.Xml.XmlDocument.CreateNavigator%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="0798c-106"><xref:System.Xml.XPath.XPathNavigator>tarafından oluşturulan nesneler <xref:System.Xml.XPath.XPathDocument> sınıfı salt okunur ve herhangi bir düzenleme yöntemlerini kullanmayı dener bir <xref:System.Xml.XPath.XPathNavigator> tarafından oluşturulan nesne bir <xref:System.Xml.XPath.XPathDocument> nesne sonuçlanıyor bir <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="0798c-106"><xref:System.Xml.XPath.XPathNavigator> objects created by the <xref:System.Xml.XPath.XPathDocument> class are read-only and any attempt to use the editing methods of an <xref:System.Xml.XPath.XPathNavigator> object created by an <xref:System.Xml.XPath.XPathDocument> object results in a <xref:System.NotSupportedException>.</span></span>  
  
 <span data-ttu-id="0798c-107">Düzenlenebilir oluşturma hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator> nesneleri bkz [XPathDocument ve XmlDocument kullanarak XML veri okunurken](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span><span class="sxs-lookup"><span data-stu-id="0798c-107">For more information about creating editable <xref:System.Xml.XPath.XPathNavigator> objects, see [Reading XML Data using XPathDocument and XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span></span>  
  
## <a name="removing-nodes"></a><span data-ttu-id="0798c-108">Düğümleri kaldırma</span><span class="sxs-lookup"><span data-stu-id="0798c-108">Removing Nodes</span></span>  
 <span data-ttu-id="0798c-109"><xref:System.Xml.XPath.XPathNavigator> SAX <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> bir XML belgesinden düğümler çıkarmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="0798c-109">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method to remove nodes from an XML document.</span></span>  
  
### <a name="removing-a-node"></a><span data-ttu-id="0798c-110">Düğüm kaldırma</span><span class="sxs-lookup"><span data-stu-id="0798c-110">Removing a Node</span></span>  
 <span data-ttu-id="0798c-111"><xref:System.Xml.XPath.XPathNavigator> SAX <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> yöntemi geçerli düğüm silmek için bir <xref:System.Xml.XPath.XPathNavigator> nesne şu anda konumlandırılır üzerinde bir XML belgesinden.</span><span class="sxs-lookup"><span data-stu-id="0798c-111">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method to delete the current node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on from an XML document.</span></span>  
  
 <span data-ttu-id="0798c-112">Kullanarak bir düğümü silindikten sonra <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> yöntemi, onu artık kökünden ulaşılabilir <xref:System.Xml.XmlDocument> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="0798c-112">After a node has been deleted using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method, it is no longer reachable from the root of the <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="0798c-113">Bir düğüm silindikten sonra <xref:System.Xml.XPath.XPathNavigator> Silinen düğümün üst düğümde konumlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="0798c-113">After a node has been deleted, the <xref:System.Xml.XPath.XPathNavigator> is positioned on the parent node of the deleted node.</span></span>  
  
 <span data-ttu-id="0798c-114">Bir silme işlemi herhangi konumunu etkilemez <xref:System.Xml.XPath.XPathNavigator> silinen düğümde konumlandırılmış nesnesi.</span><span class="sxs-lookup"><span data-stu-id="0798c-114">A delete operation doesn't affect the position of any <xref:System.Xml.XPath.XPathNavigator> object positioned on the deleted node.</span></span> <span data-ttu-id="0798c-115">Bunlar <xref:System.Xml.XPath.XPathNavigator> nesneler, silinen ağaçtaki taşıyabilir ancak ana düğüm kullanarak ağaç normal düğüm kümesi Gezinti yöntemlerinin taşınamaz anlamda geçerli <xref:System.Xml.XPath.XPathNavigator> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0798c-115">These <xref:System.Xml.XPath.XPathNavigator> objects are valid in the sense that they can move within the deleted subtree, but cannot be moved to the main node tree using the regular node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0798c-116"><xref:System.Xml.XPath.XPathNavigator.MoveTo%2A> Yöntemi <xref:System.Xml.XPath.XPathNavigator> sınıfı, bunlar taşımak için kullanılabilir <xref:System.Xml.XPath.XPathNavigator> nesneleri, silinen alt ağacı için ana düğüm ağaca ya da ana düğüm ağacından yedekleyin.</span><span class="sxs-lookup"><span data-stu-id="0798c-116">The <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class can be used to move these <xref:System.Xml.XPath.XPathNavigator> objects back into the main node tree, or from the main node tree to the deleted subtree.</span></span>  
  
 <span data-ttu-id="0798c-117">Aşağıdaki örnekte, `price` ilk öğesinin `book` öğesinin `contosoBooks.xml` dosyası kullanarak silinir <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0798c-117">In the following example, the `price` element of the first `book` element of the `contosoBooks.xml` file is deleted using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method.</span></span> <span data-ttu-id="0798c-118">Konumunu <xref:System.Xml.XPath.XPathNavigator> sonra nesne `price` öğesi silinir üzerinde üst `book` öğesi.</span><span class="sxs-lookup"><span data-stu-id="0798c-118">The position of the <xref:System.Xml.XPath.XPathNavigator> object after the `price` element is deleted is on the parent `book` element.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.DeleteSelf()  
  
Console.WriteLine("Position after delete: {0}", navigator.Name)  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("contosoBooks.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.DeleteSelf();  
  
Console.WriteLine("Position after delete: {0}", navigator.Name);  
Console.WriteLine(navigator.OuterXml);  
```  
  
 <span data-ttu-id="0798c-119">Örnek alır `contosoBooks.xml` dosyayı bir girdi olarak.</span><span class="sxs-lookup"><span data-stu-id="0798c-119">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-an-attribute-node"></a><span data-ttu-id="0798c-120">Öznitelik düğümü kaldırma</span><span class="sxs-lookup"><span data-stu-id="0798c-120">Removing an Attribute Node</span></span>  
 <span data-ttu-id="0798c-121">Öznitelik düğümleri kullanarak bir XML belgesi kaldırılır <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0798c-121">Attribute nodes are removed from an XML document using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method.</span></span>  
  
 <span data-ttu-id="0798c-122">Öznitelik düğümü silindikten sonra artık kök düğümden erişilebilir bir <xref:System.Xml.XmlDocument> nesne ve <xref:System.Xml.XPath.XPathNavigator> nesne üst öğede konumlandırılır.</span><span class="sxs-lookup"><span data-stu-id="0798c-122">After an attribute node has been deleted, it is no longer reachable from the root node of an <xref:System.Xml.XmlDocument> object and the <xref:System.Xml.XPath.XPathNavigator> object is positioned on the parent element.</span></span>  
  
#### <a name="default-attributes"></a><span data-ttu-id="0798c-123">Varsayılan öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="0798c-123">Default Attributes</span></span>  
 <span data-ttu-id="0798c-124">Öznitelikleri kaldırmak için kullanılan yöntemin bağımsız olarak DTD ya da XML Şeması XML belgesi için varsayılan öznitelikler olarak tanımlanan öznitelikleri kaldırma özel sınırlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="0798c-124">Regardless of the method used to remove attributes, there are special limitations on removing attributes that are defined as default attributes in the DTD or XML Schema for the XML document.</span></span> <span data-ttu-id="0798c-125">Ait oldukları öğesi de kaldırılmadığı sürece varsayılan öznitelikleri kaldırılamaz.</span><span class="sxs-lookup"><span data-stu-id="0798c-125">Default attributes cannot be removed unless the element they belong to is also removed.</span></span> <span data-ttu-id="0798c-126">Varsayılan öznitelikler, her zaman bildirilen, sonuç olarak, varsayılan özniteliği sonuçları öğesine eklenen bir değiştirme özniteliğinde silme ve varsayılan değerin bildirildi başlatıldı varsayılan özniteliklere sahip öğe yok.</span><span class="sxs-lookup"><span data-stu-id="0798c-126">Default attributes are always present for elements that have default attributes declared, and as a result, deleting a default attribute results in a replacement attribute being inserted into the element and initialized to the default value that was declared.</span></span>  
  
## <a name="removing-values"></a><span data-ttu-id="0798c-127">Değerleri kaldırılıyor</span><span class="sxs-lookup"><span data-stu-id="0798c-127">Removing Values</span></span>  
 <span data-ttu-id="0798c-128"><xref:System.Xml.XPath.XPathNavigator> SAX <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> ve <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> kaldırmak için yöntemleri türsüz ve yazılan bir XML belgesi değerleri.</span><span class="sxs-lookup"><span data-stu-id="0798c-128">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods to remove untyped and typed values from an XML document.</span></span>  
  
### <a name="removing-untyped-values"></a><span data-ttu-id="0798c-129">Türsüz değerleri kaldırılıyor</span><span class="sxs-lookup"><span data-stu-id="0798c-129">Removing Untyped Values</span></span>  
 <span data-ttu-id="0798c-130"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Yöntemi yalnızca ekler türsüz `string` değeri düğümün değeri olarak bir parametre olarak geçirilen <xref:System.Xml.XPath.XPathNavigator> nesnesi üzerinde şu anda konumlandırılır.</span><span class="sxs-lookup"><span data-stu-id="0798c-130">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method simply inserts the untyped `string` value passed as a parameter as the value of the node the <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="0798c-131">Boş bir dize olarak geçirme <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> yöntemi geçerli düğüm değerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="0798c-131">Passing an empty string to the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method removes the value of the current node.</span></span>  
  
 <span data-ttu-id="0798c-132">Aşağıdaki örnek değeri kaldırır `price` ilk öğesinin `book` öğesinde `contosoBooks.xml` kullanarak dosya <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0798c-132">The following example removes the value of the `price` element of the first `book` element in the `contosoBooks.xml` file using the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.SetValue("")  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("contosoBooks.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.SetValue("");  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 <span data-ttu-id="0798c-133">Örnek alır `contosoBooks.xml` dosyayı bir girdi olarak.</span><span class="sxs-lookup"><span data-stu-id="0798c-133">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-typed-values"></a><span data-ttu-id="0798c-134">Yazılan değerleri kaldırılıyor</span><span class="sxs-lookup"><span data-stu-id="0798c-134">Removing Typed Values</span></span>  
 <span data-ttu-id="0798c-135">Bir düğüm türü bir basit W3C XML Şeması olduğunda türü, tarafından eklenen yeni değer <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> değer ayarlamadan önce yöntemi basit türe ilişkin modelleri karşı denetlenir.</span><span class="sxs-lookup"><span data-stu-id="0798c-135">When the type of a node is a W3C XML Schema simple type, the new value inserted by the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method is checked against the facets of the simple type before the value is set.</span></span> <span data-ttu-id="0798c-136">Yeni değer düğüm türüne göre geçerli değilse (örneğin, bir değeri ayarlamak `-1` türü olan bir öğe üzerinde `xs:positiveInteger`), bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="0798c-136">If the new value is not valid according to the type of the node (for example, setting a value of `-1` on an element whose type is `xs:positiveInteger`), it results in an exception.</span></span> <span data-ttu-id="0798c-137"><xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> Yöntemi de yapamazsınız bayraklarıdır `null` bir parametre olarak.</span><span class="sxs-lookup"><span data-stu-id="0798c-137">The <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method also cannot be passed `null` as a parameter.</span></span> <span data-ttu-id="0798c-138">Sonuç olarak yazılan düğüm değerinin kaldırma düğümünün şema türü ile uyumlu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0798c-138">As a result removing the value of a typed node must comply with the schema type of the node.</span></span>  
  
 <span data-ttu-id="0798c-139">Aşağıdaki örnek değeri kaldırır `price` ilk öğesinin `book` öğesinde `contosoBooks.xml` kullanarak dosya <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> değeri ayarlayarak yöntemi `0`.</span><span class="sxs-lookup"><span data-stu-id="0798c-139">The following example removes the value of the `price` element of the first `book` element in the `contosoBooks.xml` file using the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method by setting the value to `0`.</span></span> <span data-ttu-id="0798c-140">Düğümün değerini kaldırılmaz, ancak kitap fiyat veri türüne göre kaldırıldı `xs:decimal`.</span><span class="sxs-lookup"><span data-stu-id="0798c-140">The value of the node is not removed, but the price of the book has been removed according to its data type of `xs:decimal`.</span></span>  
  
```vb  
Dim settings As XmlReaderSettings = New XmlReaderSettings()  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
settings.ValidationType = ValidationType.Schema  
  
Dim reader As XmlReader = XmlReader.Create("contosoBooks.xml", settings)  
  
Dim document As XmlDocument = New XmlDocument()  
document.Load(reader)  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.SetTypedValue(0)  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlReaderSettings settings = new XmlReaderSettings();  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
settings.ValidationType = ValidationType.Schema;  
  
XmlReader reader = XmlReader.Create("contosoBooks.xml", settings);  
  
XmlDocument document = new XmlDocument();  
document.Load(reader);  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.SetTypedValue(0);  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
## <a name="namespace-nodes"></a><span data-ttu-id="0798c-141">Namespace düğümler</span><span class="sxs-lookup"><span data-stu-id="0798c-141">Namespace Nodes</span></span>  
 <span data-ttu-id="0798c-142">Namespace düğümleri, gelen silinemez bir <xref:System.Xml.XmlDocument> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="0798c-142">Namespace nodes cannot be deleted from an <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="0798c-143">Ad alanı düğümleri kullanarak silme girişiminde <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> yöntemi bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="0798c-143">Attempts to delete namespace nodes using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method results in an exception.</span></span>  
  
## <a name="the-innerxml-and-outerxml-properties"></a><span data-ttu-id="0798c-144">InnerXml ve OuterXml özellikleri</span><span class="sxs-lookup"><span data-stu-id="0798c-144">The InnerXml and OuterXml Properties</span></span>  
 <span data-ttu-id="0798c-145"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özelliklerini <xref:System.Xml.XPath.XPathNavigator> sınıfı düğümlerin XML biçimlendirmesini değiştirme bir <xref:System.Xml.XPath.XPathNavigator> nesnesi üzerinde şu anda konumlandırılır.</span><span class="sxs-lookup"><span data-stu-id="0798c-145">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class change the XML markup of the nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="0798c-146"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Özellik alt düğümlerin XML biçimlendirme değişiklikleri bir <xref:System.Xml.XPath.XPathNavigator> nesne şu anda konumlandırılır üzerinde verilen XML ayrıştırılmış içeriğini `string`.</span><span class="sxs-lookup"><span data-stu-id="0798c-146">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on with the parsed contents of the given XML `string`.</span></span> <span data-ttu-id="0798c-147">Benzer şekilde, <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özellik alt düğümlerin XML biçimlendirme değişiklikleri bir <xref:System.Xml.XPath.XPathNavigator> nesne şu anda konumlandırılır üzerinde geçerli düğüm yanı sıra.</span><span class="sxs-lookup"><span data-stu-id="0798c-147">Similarly, the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on as well as the current node itself.</span></span>  
  
 <span data-ttu-id="0798c-148">Bu konuda, açıklanan yöntemlerden yanı sıra <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özellikleri, düğümleri ve değerleri bir XML belgesinden kaldırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0798c-148">In addition to the methods described in this topic, the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties can be used to remove nodes and values from an XML document.</span></span> <span data-ttu-id="0798c-149">Kullanma hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> düğümleri değiştirmek için özellikler bkz [XML XPathNavigator kullanarak verileri değiştirme](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) konu.</span><span class="sxs-lookup"><span data-stu-id="0798c-149">For more information about using the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties to modify nodes, see the [Modify XML Data using XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) topic.</span></span>  
  
## <a name="saving-an-xml-document"></a><span data-ttu-id="0798c-150">Bir XML belgesi kaydetme</span><span class="sxs-lookup"><span data-stu-id="0798c-150">Saving an XML Document</span></span>  
 <span data-ttu-id="0798c-151">Yapılan değişiklikler kaydedilirken bir <xref:System.Xml.XmlDocument> nesne bu konuda açıklanan yöntemlerden sonucunu yöntemleri kullanılarak gerçekleştirilir gibi <xref:System.Xml.XmlDocument> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0798c-151">Saving changes made to an <xref:System.Xml.XmlDocument> object as the result of the methods described in this topic is performed using the methods of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="0798c-152">Yapılan değişiklikleri kaydetme hakkında daha fazla bilgi için bir <xref:System.Xml.XmlDocument> nesne için bkz: [kaydetme ve bir belgeyi yazma](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span><span class="sxs-lookup"><span data-stu-id="0798c-152">For more information about saving changes made to an <xref:System.Xml.XmlDocument> object, see [Saving and Writing a Document](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0798c-153">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0798c-153">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="0798c-154">XPath veri modelini kullanarak işlem XML verileri</span><span class="sxs-lookup"><span data-stu-id="0798c-154">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="0798c-155">XML XPathNavigator kullanarak verileri ekleme</span><span class="sxs-lookup"><span data-stu-id="0798c-155">Insert XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="0798c-156">XML XPathNavigator kullanarak verileri değiştirme</span><span class="sxs-lookup"><span data-stu-id="0798c-156">Modify XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)
