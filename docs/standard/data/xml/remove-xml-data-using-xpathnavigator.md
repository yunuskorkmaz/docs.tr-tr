---
title: XPathNavigator kullanarak XML verilerini kaldırma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 9f436bca-1b96-494b-a6d2-e102c7551752
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1827e40256bc4307006ce081cbb6cbc44a89a0bc
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48837277"
---
# <a name="remove-xml-data-using-xpathnavigator"></a><span data-ttu-id="d5694-102">XPathNavigator kullanarak XML verilerini kaldırma</span><span class="sxs-lookup"><span data-stu-id="d5694-102">Remove XML Data using XPathNavigator</span></span>
<span data-ttu-id="d5694-103"><xref:System.Xml.XPath.XPathNavigator> Sınıf bir XML belgesinden düğümleri ve değerleri kaldırmak için kullanılan yöntemler kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d5694-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to remove nodes and values from an XML document.</span></span> <span data-ttu-id="d5694-104">Bu yöntemleri kullanmak için <xref:System.Xml.XPath.XPathNavigator> nesne olmalıdır düzenlenemez, diğer bir deyişle, kendi <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> özelliği olmalıdır `true`.</span><span class="sxs-lookup"><span data-stu-id="d5694-104">In order to use these methods, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be `true`.</span></span>  
  
 <span data-ttu-id="d5694-105"><xref:System.Xml.XPath.XPathNavigator> bir XML belgesi düzenleyebilirsiniz nesneleri <xref:System.Xml.XmlDocument.CreateNavigator%2A> yöntemi <xref:System.Xml.XmlDocument> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d5694-105"><xref:System.Xml.XPath.XPathNavigator> objects that can edit an XML document are created by the <xref:System.Xml.XmlDocument.CreateNavigator%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="d5694-106"><xref:System.Xml.XPath.XPathNavigator> tarafından oluşturulan nesnelerin <xref:System.Xml.XPath.XPathDocument> sınıfı salt okunurdur ve tüm düzenleme yöntemlerini kullanmayı dener bir <xref:System.Xml.XPath.XPathNavigator> nesnesi tarafından oluşturulan bir <xref:System.Xml.XPath.XPathDocument> nesne sonuçlanıyor bir <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="d5694-106"><xref:System.Xml.XPath.XPathNavigator> objects created by the <xref:System.Xml.XPath.XPathDocument> class are read-only and any attempt to use the editing methods of an <xref:System.Xml.XPath.XPathNavigator> object created by an <xref:System.Xml.XPath.XPathDocument> object results in a <xref:System.NotSupportedException>.</span></span>  
  
 <span data-ttu-id="d5694-107">Düzenlenebilir oluşturma hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator> nesneleri bkz [XPathDocument ve XmlDocument kullanarak XML verileri okuma](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span><span class="sxs-lookup"><span data-stu-id="d5694-107">For more information about creating editable <xref:System.Xml.XPath.XPathNavigator> objects, see [Reading XML Data using XPathDocument and XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span></span>  
  
## <a name="removing-nodes"></a><span data-ttu-id="d5694-108">Düğümleri kaldırma</span><span class="sxs-lookup"><span data-stu-id="d5694-108">Removing Nodes</span></span>  
 <span data-ttu-id="d5694-109"><xref:System.Xml.XPath.XPathNavigator> Sağlar sınıfını <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> yöntemi bir XML belgesinden düğümleri kaldırma.</span><span class="sxs-lookup"><span data-stu-id="d5694-109">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method to remove nodes from an XML document.</span></span>  
  
### <a name="removing-a-node"></a><span data-ttu-id="d5694-110">Düğüm kaldırma</span><span class="sxs-lookup"><span data-stu-id="d5694-110">Removing a Node</span></span>  
 <span data-ttu-id="d5694-111"><xref:System.Xml.XPath.XPathNavigator> Sağlar sınıfını <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> geçerli düğüm silmek için yöntemi bir <xref:System.Xml.XPath.XPathNavigator> nesne şu anda yerde konumlandırılır üzerinde bir XML belgesinden.</span><span class="sxs-lookup"><span data-stu-id="d5694-111">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method to delete the current node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on from an XML document.</span></span>  
  
 <span data-ttu-id="d5694-112">Kullanarak bir düğümü silindikten sonra <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> yöntemi, artık kökünden erişilebilir <xref:System.Xml.XmlDocument> nesne.</span><span class="sxs-lookup"><span data-stu-id="d5694-112">After a node has been deleted using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method, it is no longer reachable from the root of the <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="d5694-113">Bir düğüm silindikten sonra <xref:System.Xml.XPath.XPathNavigator> Silinen düğümün üst düğümde konumlandırılır.</span><span class="sxs-lookup"><span data-stu-id="d5694-113">After a node has been deleted, the <xref:System.Xml.XPath.XPathNavigator> is positioned on the parent node of the deleted node.</span></span>  
  
 <span data-ttu-id="d5694-114">Bir silme işlemi herhangi bir konumunu etkilemez <xref:System.Xml.XPath.XPathNavigator> silinen düğüm üzerinde konumlandırılmış bir nesne.</span><span class="sxs-lookup"><span data-stu-id="d5694-114">A delete operation doesn't affect the position of any <xref:System.Xml.XPath.XPathNavigator> object positioned on the deleted node.</span></span> <span data-ttu-id="d5694-115">Bunlar <xref:System.Xml.XPath.XPathNavigator> nesnelerdir silinmiş alt ağacı içinde geçebilirsiniz ancak ana düğüm ağacı kullanarak normal bir düğüm kümesi gezinme yöntemlerinden biri taşınamaz anlamda geçerli <xref:System.Xml.XPath.XPathNavigator> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d5694-115">These <xref:System.Xml.XPath.XPathNavigator> objects are valid in the sense that they can move within the deleted subtree, but cannot be moved to the main node tree using the regular node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d5694-116"><xref:System.Xml.XPath.XPathNavigator.MoveTo%2A> Yöntemi <xref:System.Xml.XPath.XPathNavigator> sınıfı, bunları taşımak için kullanılabilir <xref:System.Xml.XPath.XPathNavigator> nesneler, silinen alt ağacı için ana düğüm ağaca veya ana düğüm ağacı geri.</span><span class="sxs-lookup"><span data-stu-id="d5694-116">The <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class can be used to move these <xref:System.Xml.XPath.XPathNavigator> objects back into the main node tree, or from the main node tree to the deleted subtree.</span></span>  
  
 <span data-ttu-id="d5694-117">Aşağıdaki örnekte, `price` ilk öğenin `book` öğesinin `contosoBooks.xml` dosyası kullanarak silinir <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d5694-117">In the following example, the `price` element of the first `book` element of the `contosoBooks.xml` file is deleted using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method.</span></span> <span data-ttu-id="d5694-118">Konumunu <xref:System.Xml.XPath.XPathNavigator> sonra nesne `price` silinir üzerinde üst `book` öğesi.</span><span class="sxs-lookup"><span data-stu-id="d5694-118">The position of the <xref:System.Xml.XPath.XPathNavigator> object after the `price` element is deleted is on the parent `book` element.</span></span>  
  
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
  
 <span data-ttu-id="d5694-119">Örnek alan `contosoBooks.xml` girdi olarak dosya.</span><span class="sxs-lookup"><span data-stu-id="d5694-119">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-an-attribute-node"></a><span data-ttu-id="d5694-120">Bir öznitelik düğümü kaldırma</span><span class="sxs-lookup"><span data-stu-id="d5694-120">Removing an Attribute Node</span></span>  
 <span data-ttu-id="d5694-121">Öznitelik düğümleri kullanarak bir XML belgesi kaldırılır <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d5694-121">Attribute nodes are removed from an XML document using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method.</span></span>  
  
 <span data-ttu-id="d5694-122">Bir öznitelik düğümü silindikten sonra artık ' kök düğümünden erişilebilir değil bir <xref:System.Xml.XmlDocument> nesne ve <xref:System.Xml.XPath.XPathNavigator> nesnenin üst öğede konumlanan.</span><span class="sxs-lookup"><span data-stu-id="d5694-122">After an attribute node has been deleted, it is no longer reachable from the root node of an <xref:System.Xml.XmlDocument> object and the <xref:System.Xml.XPath.XPathNavigator> object is positioned on the parent element.</span></span>  
  
#### <a name="default-attributes"></a><span data-ttu-id="d5694-123">Varsayılan öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d5694-123">Default Attributes</span></span>  
 <span data-ttu-id="d5694-124">Öznitelikleri kaldırmak için kullanılan yöntem ne olursa olsun DTD'nin veya XML Şeması XML belgesi için varsayılan öznitelikler olarak tanımlanan öznitelikleri kaldırma hakkında özel sınırlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="d5694-124">Regardless of the method used to remove attributes, there are special limitations on removing attributes that are defined as default attributes in the DTD or XML Schema for the XML document.</span></span> <span data-ttu-id="d5694-125">Ayrıca ait oldukları öğesi kaldırılmadığı sürece, varsayılan öznitelikler kaldırılamaz.</span><span class="sxs-lookup"><span data-stu-id="d5694-125">Default attributes cannot be removed unless the element they belong to is also removed.</span></span> <span data-ttu-id="d5694-126">Varsayılan öznitelikleri her zaman bildirilen, sonuç olarak, varsayılan öznitelik sonuçları öğesine eklenen bir değiştirme özniteliğinde silme ve bildirilen varsayılan değeri olarak başlatılan varsayılan öznitelikleri olan öğeler için yok.</span><span class="sxs-lookup"><span data-stu-id="d5694-126">Default attributes are always present for elements that have default attributes declared, and as a result, deleting a default attribute results in a replacement attribute being inserted into the element and initialized to the default value that was declared.</span></span>  
  
## <a name="removing-values"></a><span data-ttu-id="d5694-127">Değerleri kaldırılıyor</span><span class="sxs-lookup"><span data-stu-id="d5694-127">Removing Values</span></span>  
 <span data-ttu-id="d5694-128"><xref:System.Xml.XPath.XPathNavigator> Sağlar sınıfını <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> ve <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> kaldırmak için yöntemleri türsüz ve yazılan değerleri bir XML belgesi.</span><span class="sxs-lookup"><span data-stu-id="d5694-128">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods to remove untyped and typed values from an XML document.</span></span>  
  
### <a name="removing-untyped-values"></a><span data-ttu-id="d5694-129">Yazılmamış değerleri kaldırılıyor</span><span class="sxs-lookup"><span data-stu-id="d5694-129">Removing Untyped Values</span></span>  
 <span data-ttu-id="d5694-130"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Yöntemi yalnızca ekler yazılmamış `string` düğümün değeri olarak bir parametre olarak geçirilen değer <xref:System.Xml.XPath.XPathNavigator> nesne üzerinde konumlandırılmış şu anda.</span><span class="sxs-lookup"><span data-stu-id="d5694-130">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method simply inserts the untyped `string` value passed as a parameter as the value of the node the <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="d5694-131">Boş dize olarak geçirerek <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> yöntemi değeri geçerli düğümün kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d5694-131">Passing an empty string to the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method removes the value of the current node.</span></span>  
  
 <span data-ttu-id="d5694-132">Aşağıdaki örnek, değeri kaldırır `price` ilk öğenin `book` öğesinde `contosoBooks.xml` kullanarak dosya <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d5694-132">The following example removes the value of the `price` element of the first `book` element in the `contosoBooks.xml` file using the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method.</span></span>  
  
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
  
 <span data-ttu-id="d5694-133">Örnek alan `contosoBooks.xml` girdi olarak dosya.</span><span class="sxs-lookup"><span data-stu-id="d5694-133">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-typed-values"></a><span data-ttu-id="d5694-134">Yazılan değerleri kaldırılıyor</span><span class="sxs-lookup"><span data-stu-id="d5694-134">Removing Typed Values</span></span>  
 <span data-ttu-id="d5694-135">Bir düğüm türü basit bir W3C XML Şeması olduğunda tür, tarafından eklenen yeni değer <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> yöntemi değeri ayarlanmadan önce basit türe ilişkin modelleri karşı denetlenir.</span><span class="sxs-lookup"><span data-stu-id="d5694-135">When the type of a node is a W3C XML Schema simple type, the new value inserted by the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method is checked against the facets of the simple type before the value is set.</span></span> <span data-ttu-id="d5694-136">Yeni değer düğüm türüne göre geçerli değilse (örneğin, bir değeri ayarlamak `-1` türü olan bir öğede `xs:positiveInteger`), bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="d5694-136">If the new value is not valid according to the type of the node (for example, setting a value of `-1` on an element whose type is `xs:positiveInteger`), it results in an exception.</span></span> <span data-ttu-id="d5694-137"><xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> Yöntemi de geçirilemez `null` bir parametre olarak.</span><span class="sxs-lookup"><span data-stu-id="d5694-137">The <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method also cannot be passed `null` as a parameter.</span></span> <span data-ttu-id="d5694-138">Sonuç olarak belirlenmiş bir düğümün değerini kaldırma, düğüm şema türü ile uyumlu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d5694-138">As a result removing the value of a typed node must comply with the schema type of the node.</span></span>  
  
 <span data-ttu-id="d5694-139">Aşağıdaki örnek, değeri kaldırır `price` ilk öğenin `book` öğesinde `contosoBooks.xml` kullanarak dosya <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> değeri ayarlanarak yöntemi `0`.</span><span class="sxs-lookup"><span data-stu-id="d5694-139">The following example removes the value of the `price` element of the first `book` element in the `contosoBooks.xml` file using the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method by setting the value to `0`.</span></span> <span data-ttu-id="d5694-140">Bir düğümün değerini kaldırılmaz, ancak kendi veri türüne göre fiyat kitabın kaldırıldı `xs:decimal`.</span><span class="sxs-lookup"><span data-stu-id="d5694-140">The value of the node is not removed, but the price of the book has been removed according to its data type of `xs:decimal`.</span></span>  
  
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
  
## <a name="namespace-nodes"></a><span data-ttu-id="d5694-141">Namespace düğümleri</span><span class="sxs-lookup"><span data-stu-id="d5694-141">Namespace Nodes</span></span>  
 <span data-ttu-id="d5694-142">Namespace düğümleri, gelen silinemiyor bir <xref:System.Xml.XmlDocument> nesne.</span><span class="sxs-lookup"><span data-stu-id="d5694-142">Namespace nodes cannot be deleted from an <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="d5694-143">Ad alanı düğümleri kullanarak silmeyi dener <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> yöntemi bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="d5694-143">Attempts to delete namespace nodes using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method results in an exception.</span></span>  
  
## <a name="the-innerxml-and-outerxml-properties"></a><span data-ttu-id="d5694-144">Sınıfının InnerXml ve OuterXml özellikleri</span><span class="sxs-lookup"><span data-stu-id="d5694-144">The InnerXml and OuterXml Properties</span></span>  
 <span data-ttu-id="d5694-145"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özelliklerini <xref:System.Xml.XPath.XPathNavigator> sınıfını değiştirin XML işaretlemesini düğümlerin bir <xref:System.Xml.XPath.XPathNavigator> nesne üzerinde konumlandırılmış şu anda.</span><span class="sxs-lookup"><span data-stu-id="d5694-145">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class change the XML markup of the nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="d5694-146"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Özelliğini değiştirir XML işaretlemesini alt düğümlerin bir <xref:System.Xml.XPath.XPathNavigator> nesne şu anda yerde konumlandırılır üzerinde belirli XML ayrıştırılmış içeriğiyle `string`.</span><span class="sxs-lookup"><span data-stu-id="d5694-146">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on with the parsed contents of the given XML `string`.</span></span> <span data-ttu-id="d5694-147">Benzer şekilde, <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özelliğini değiştirir XML işaretlemesini alt düğümlerin bir <xref:System.Xml.XPath.XPathNavigator> nesne şu anda yerde konumlandırılır üzerinde geçerli düğüm yanı sıra kendisini.</span><span class="sxs-lookup"><span data-stu-id="d5694-147">Similarly, the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on as well as the current node itself.</span></span>  
  
 <span data-ttu-id="d5694-148">Bu konuda, açıklanan yöntemlerin yanı sıra <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özellikleri, bir XML belgesinden düğümleri ve değerleri kaldırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d5694-148">In addition to the methods described in this topic, the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties can be used to remove nodes and values from an XML document.</span></span> <span data-ttu-id="d5694-149">Kullanma hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> düğümleri değiştirilecek özellikleri görmek [değiştirme XPathNavigator kullanarak XML verilerini](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) konu.</span><span class="sxs-lookup"><span data-stu-id="d5694-149">For more information about using the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties to modify nodes, see the [Modify XML Data using XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) topic.</span></span>  
  
## <a name="saving-an-xml-document"></a><span data-ttu-id="d5694-150">Bir XML belgesi kaydediliyor</span><span class="sxs-lookup"><span data-stu-id="d5694-150">Saving an XML Document</span></span>  
 <span data-ttu-id="d5694-151">Yapılan değişiklikler kaydedilirken bir <xref:System.Xml.XmlDocument> nesne bu konuda açıklanan yöntemlerden sonucunu yöntemleri kullanılarak gerçekleştirilir gibi <xref:System.Xml.XmlDocument> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d5694-151">Saving changes made to an <xref:System.Xml.XmlDocument> object as the result of the methods described in this topic is performed using the methods of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="d5694-152">Yapılan değişiklikleri kaydetme hakkında daha fazla bilgi için bir <xref:System.Xml.XmlDocument> nesne, bkz: [kaydetme ve belge yazma](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span><span class="sxs-lookup"><span data-stu-id="d5694-152">For more information about saving changes made to an <xref:System.Xml.XmlDocument> object, see [Saving and Writing a Document](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5694-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5694-153">See also</span></span>

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [<span data-ttu-id="d5694-154">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="d5694-154">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [<span data-ttu-id="d5694-155">XPathNavigator Kullanarak XML Verileri Ekleme</span><span class="sxs-lookup"><span data-stu-id="d5694-155">Insert XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)  
- [<span data-ttu-id="d5694-156">XPathNavigator Kullanarak XML Verilerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="d5694-156">Modify XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)
