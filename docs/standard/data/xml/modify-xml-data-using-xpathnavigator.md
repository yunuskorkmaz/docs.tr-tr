---
title: XML XPathNavigator kullanarak verileri değiştirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 03a7c5a1-b296-4af4-b209-043c958dc0a5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eb31c2ea504472a8707d700ff84b8c367467b607
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579125"
---
# <a name="modify-xml-data-using-xpathnavigator"></a><span data-ttu-id="4d15c-102">XML XPathNavigator kullanarak verileri değiştirme</span><span class="sxs-lookup"><span data-stu-id="4d15c-102">Modify XML Data using XPathNavigator</span></span>
<span data-ttu-id="4d15c-103"><xref:System.Xml.XPath.XPathNavigator> Sınıfı düğümleri ve bir XML belgesi değerleri değiştirmek için kullanılan yöntemler kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="4d15c-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to modify nodes and values in an XML document.</span></span> <span data-ttu-id="4d15c-104">Bu yöntemleri kullanmak için <xref:System.Xml.XPath.XPathNavigator> nesnesi olmalıdır düzenlenebilir, diğer bir deyişle, kendi <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> olmalıdır `true`.</span><span class="sxs-lookup"><span data-stu-id="4d15c-104">In order to use these methods, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be `true`.</span></span>  
  
 <span data-ttu-id="4d15c-105"><xref:System.Xml.XPath.XPathNavigator> tarafından oluşturulan bir XML belgesi düzenleyebilirsiniz nesneleri <xref:System.Xml.XmlDocument.CreateNavigator%2A> yöntemi <xref:System.Xml.XmlDocument> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4d15c-105"><xref:System.Xml.XPath.XPathNavigator> objects that can edit an XML document are created by the <xref:System.Xml.XmlDocument.CreateNavigator%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="4d15c-106"><xref:System.Xml.XPath.XPathNavigator> tarafından oluşturulan nesneler <xref:System.Xml.XPath.XPathDocument> sınıfı salt okunur ve herhangi bir düzenleme yöntemlerini kullanmayı dener bir <xref:System.Xml.XPath.XPathNavigator> tarafından oluşturulan nesne bir <xref:System.Xml.XPath.XPathDocument> nesne sonucunda bir <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="4d15c-106"><xref:System.Xml.XPath.XPathNavigator> objects created by the <xref:System.Xml.XPath.XPathDocument> class are read-only and any attempt to use the editing methods of an <xref:System.Xml.XPath.XPathNavigator> object created by an <xref:System.Xml.XPath.XPathDocument> object result in a <xref:System.NotSupportedException>.</span></span>  
  
 <span data-ttu-id="4d15c-107">Düzenlenebilir oluşturma hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator> nesneleri bkz [XPathDocument ve XmlDocument kullanarak XML veri okunurken](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span><span class="sxs-lookup"><span data-stu-id="4d15c-107">For more information about creating editable <xref:System.Xml.XPath.XPathNavigator> objects, see [Reading XML Data using XPathDocument and XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span></span>  
  
## <a name="modifying-nodes"></a><span data-ttu-id="4d15c-108">Düğümleri değiştirme</span><span class="sxs-lookup"><span data-stu-id="4d15c-108">Modifying Nodes</span></span>  
 <span data-ttu-id="4d15c-109">Bir düğüm değerini değiştirmek için basit bir teknik kullanmaktır <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> ve <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> yöntemlerinin <xref:System.Xml.XPath.XPathNavigator> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4d15c-109">A simple technique for changing the value of a node is to use the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 <span data-ttu-id="4d15c-110">Aşağıdaki tabloda bu yöntemleri etkilerini farklı düğüm türleri listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="4d15c-110">The following table lists the effects of these methods on different node types.</span></span>  
  
|<xref:System.Xml.XPath.XPathNodeType>|<span data-ttu-id="4d15c-111">Değiştirilen veri</span><span class="sxs-lookup"><span data-stu-id="4d15c-111">Data Changed</span></span>|  
|---------------------------------------------------------------------------------------------------------------------------------------------|------------------|  
|<xref:System.Xml.XPath.XPathNodeType.Root>|<span data-ttu-id="4d15c-112">Desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="4d15c-112">Not supported.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Element>|<span data-ttu-id="4d15c-113">Öğesinin içeriği.</span><span class="sxs-lookup"><span data-stu-id="4d15c-113">The content of the element.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Attribute>|<span data-ttu-id="4d15c-114">Öznitelik değeri.</span><span class="sxs-lookup"><span data-stu-id="4d15c-114">The value of the attribute.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Text>|<span data-ttu-id="4d15c-115">Metin içeriği.</span><span class="sxs-lookup"><span data-stu-id="4d15c-115">The text content.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.ProcessingInstruction>|<span data-ttu-id="4d15c-116">Hedef hariç içeriği.</span><span class="sxs-lookup"><span data-stu-id="4d15c-116">The content, excluding the target.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Comment>|<span data-ttu-id="4d15c-117">Açıklama içeriği.</span><span class="sxs-lookup"><span data-stu-id="4d15c-117">The content of the comment.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Namespace>|<span data-ttu-id="4d15c-118">Desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="4d15c-118">Not Supported.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="4d15c-119">Düzenleme <xref:System.Xml.XPath.XPathNodeType.Namespace> düğümleri veya <xref:System.Xml.XPath.XPathNodeType.Root> düğümü desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="4d15c-119">Editing <xref:System.Xml.XPath.XPathNodeType.Namespace> nodes or the <xref:System.Xml.XPath.XPathNodeType.Root> node is not supported.</span></span>  
  
 <span data-ttu-id="4d15c-120"><xref:System.Xml.XPath.XPathNavigator> Sınıfı ayrıca takın ve düğüm kaldırmak için kullanılan yöntemler kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="4d15c-120">The <xref:System.Xml.XPath.XPathNavigator> class also provides a set of methods used to insert and remove nodes.</span></span> <span data-ttu-id="4d15c-121">Ekleme ve bir XML belgesinden düğümleri kaldırma hakkında daha fazla bilgi için bkz: [XML XPathNavigator kullanarak veri ekleme](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md) ve [XML XPathNavigator kullanarak verileri Kaldır](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md) Konular.</span><span class="sxs-lookup"><span data-stu-id="4d15c-121">For more information about inserting and removing nodes from an XML document, see the [Insert XML Data using XPathNavigator](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md) and [Remove XML Data using XPathNavigator](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md) topics.</span></span>  
  
### <a name="modifying-untyped-values"></a><span data-ttu-id="4d15c-122">Türsüz değerlerini değiştirme</span><span class="sxs-lookup"><span data-stu-id="4d15c-122">Modifying Untyped Values</span></span>  
 <span data-ttu-id="4d15c-123"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Yöntemi yalnızca ekler türsüz `string` değeri düğümün değeri olarak bir parametre olarak geçirilen <xref:System.Xml.XPath.XPathNavigator> nesnesi üzerinde şu anda konumlandırılır.</span><span class="sxs-lookup"><span data-stu-id="4d15c-123">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method simply inserts the untyped `string` value passed as a parameter as the value of the node the <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="4d15c-124">Değer, herhangi bir tür olmadan veya şema bilgileri kullanılabiliyorsa, yeni değer düğüm türüne göre geçerli olduğunu doğrulama olmadan eklenir.</span><span class="sxs-lookup"><span data-stu-id="4d15c-124">The value is inserted without any type or without verifying that the new value is valid according to the type of the node if schema information is available.</span></span>  
  
 <span data-ttu-id="4d15c-125">Aşağıdaki örnekte, <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> yöntemi tüm güncelleştirmek için kullanılan `price` öğelerinde `contosoBooks.xml` dosya.</span><span class="sxs-lookup"><span data-stu-id="4d15c-125">In the following example, the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method is used to update all `price` elements in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 <span data-ttu-id="4d15c-126">Örnek alır `contosoBooks.xml` dosyayı bir girdi olarak.</span><span class="sxs-lookup"><span data-stu-id="4d15c-126">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="modifying-typed-values"></a><span data-ttu-id="4d15c-127">Yazılı değerlerini değiştirme</span><span class="sxs-lookup"><span data-stu-id="4d15c-127">Modifying Typed Values</span></span>  
 <span data-ttu-id="4d15c-128">Bir düğüm türü bir basit W3C XML Şeması olduğunda türü, tarafından eklenen yeni değer <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> değer ayarlamadan önce yöntemi basit türe ilişkin modelleri karşı denetlenir.</span><span class="sxs-lookup"><span data-stu-id="4d15c-128">When the type of a node is a W3C XML Schema simple type, the new value inserted by the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method is checked against the facets of the simple type before the value is set.</span></span> <span data-ttu-id="4d15c-129">Yeni değer düğüm türüne göre geçerli değilse (örneğin, bir değeri ayarlamak `-1` türü olan bir öğe üzerinde `xs:positiveInteger`), bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="4d15c-129">If the new value is not valid according to the type of the node (for example, setting a value of `-1` on an element whose type is `xs:positiveInteger`), it results in an exception.</span></span>  
  
 <span data-ttu-id="4d15c-130">Aşağıdaki örnek değerini değiştirme girişiminde `price` ilk öğesinin `book` öğesinde `contosoBooks.xml` dosyasını bir <xref:System.DateTime> değeri.</span><span class="sxs-lookup"><span data-stu-id="4d15c-130">The following example attempts to change the value of the `price` element of the first `book` element in the `contosoBooks.xml` file to a <xref:System.DateTime> value.</span></span> <span data-ttu-id="4d15c-131">XML şema türü olduğundan `price` öğesi olarak tanımlanır `xs:decimal` içinde `contosoBooks.xsd` dosyaları, bu sonuçları bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="4d15c-131">Because the XML Schema type of the `price` element is defined as `xs:decimal` in the `contosoBooks.xsd` files, this results in an exception.</span></span>  
  
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
  
navigator.SetTypedValue(DateTime.Now)  
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
  
navigator.SetTypedValue(DateTime.Now);  
```  
  
 <span data-ttu-id="4d15c-132">Örnek alır `contosoBooks.xml` dosyayı bir girdi olarak.</span><span class="sxs-lookup"><span data-stu-id="4d15c-132">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="4d15c-133">Bu örnek ayrıca alır `contosoBooks.xsd` bir girdi olarak.</span><span class="sxs-lookup"><span data-stu-id="4d15c-133">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
#### <a name="the-effects-of-editing-strongly-typed-xml-data"></a><span data-ttu-id="4d15c-134">Kesin türü belirtilmiş XML verileri düzenleme etkileri</span><span class="sxs-lookup"><span data-stu-id="4d15c-134">The Effects of Editing Strongly Typed XML Data</span></span>  
 <span data-ttu-id="4d15c-135"><xref:System.Xml.XPath.XPathNavigator> Sınıfını kullanır W3C XML Şeması temeli olarak kesin türü belirtilmiş XML açıklamak için.</span><span class="sxs-lookup"><span data-stu-id="4d15c-135">The <xref:System.Xml.XPath.XPathNavigator> class uses the W3C XML Schema as a basis for describing strongly-typed XML.</span></span> <span data-ttu-id="4d15c-136">Öğeleri ve özniteliklerinin W3C XML şema belgesi doğrulanması temel türü bilgilerle açıklama.</span><span class="sxs-lookup"><span data-stu-id="4d15c-136">Elements and attributes can be annotated with type information based on validation against a W3C XML Schema document.</span></span> <span data-ttu-id="4d15c-137">Metin içeriği yalnızca içerebilir o basit türler denir sırada diğer öğeleri ya da öznitelikleri içeren öğeler karmaşık türler denir.</span><span class="sxs-lookup"><span data-stu-id="4d15c-137">Elements that can contain other elements or attributes are called complex types, while those that can only contain textual content are called simple types.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4d15c-138">Özniteliklerin yalnızca basit türler olabilir.</span><span class="sxs-lookup"><span data-stu-id="4d15c-138">Attributes can only have simple types.</span></span>  
  
 <span data-ttu-id="4d15c-139">Öğe veya öznitelik şema türü tanımına belirli kuralları uyuyorsa geçerli olması için kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="4d15c-139">An element or attribute can be considered to be schema-valid if it conforms to all the rules specific to its type definition.</span></span> <span data-ttu-id="4d15c-140">Basit tür olan bir öğeyi `xs:int` -2147483648 ve 2147483647 arasında olacak şema geçerli olması için sayısal bir değer içermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="4d15c-140">An element that has the simple type `xs:int` has to contain a numeric value between -2147483648 and 2147483647 to be schema-valid.</span></span> <span data-ttu-id="4d15c-141">Karmaşık türler için öğenin şema geçerlilik şema-geçerliliği kendi alt öğeleri ve özniteliklerinin bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="4d15c-141">For complex types, the schema-validity of the element is dependent on the schema-validity of its child elements and attributes.</span></span> <span data-ttu-id="4d15c-142">Bu nedenle, karmaşık tür tanımına göre bir öğeyi geçerliyse, tüm alt öğeleri ve özniteliklerinin tür tanımlarını karşı geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4d15c-142">Thus if an element is valid against its complex type definition, all its child elements and attributes are valid against their type definitions.</span></span> <span data-ttu-id="4d15c-143">Alt öğeler biri bile veya bir öğenin öznitelikleri tür tanımına göre geçersiz veya bilinmeyen bir geçerlilik yüklüyse, benzer şekilde, öğe ayrıca geçersiz veya Bilinmeyen geçerlilik.</span><span class="sxs-lookup"><span data-stu-id="4d15c-143">Similarly, if even one of the child elements or attributes of an element is invalid against its type definition, or has an unknown validity, the element is also either invalid or of unknown validity.</span></span>  
  
 <span data-ttu-id="4d15c-144">Öğenin geçerliliğini kendi alt öğelerini ve özniteliklerini geçerliliğini bağımlı olması koşuluyla, değişiklik ya da daha önce geçerli ise, öğenin geçerliliğini değiştirilmesine neden.</span><span class="sxs-lookup"><span data-stu-id="4d15c-144">Given that the validity of an element is dependent on the validity of its child elements and attributes, modifications to either result in altering the validity of the element if it was previously valid.</span></span> <span data-ttu-id="4d15c-145">Alt öğe veya öğenin özniteliklerini eklendiğinde, güncelleştirilmiş, silinmiş veya, özellikle, ardından öğenin geçerliliğini bilinmeyen haline gelir.</span><span class="sxs-lookup"><span data-stu-id="4d15c-145">Specifically, if the child elements or attributes of an element are inserted, updated, or deleted, then the validity of the element becomes unknown.</span></span> <span data-ttu-id="4d15c-146">Bu tarafından temsil edilen <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> öğenin özelliğinin <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> özelliği ayarlanıyor <xref:System.Xml.Schema.XmlSchemaValidity.NotKnown>.</span><span class="sxs-lookup"><span data-stu-id="4d15c-146">This is represented by the <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> property of the element's <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property being set to <xref:System.Xml.Schema.XmlSchemaValidity.NotKnown>.</span></span> <span data-ttu-id="4d15c-147">Ayrıca, öğenin üst öğesi (ve kendi üst öğesi vb.) geçerliliğini de bilinmeyen azaldığından Bu etkiyi yukarı yinelemeli olarak XML belgesi aktarılır.</span><span class="sxs-lookup"><span data-stu-id="4d15c-147">Furthermore, this effect cascades upwards recursively across the XML document, because the validity of the element's parent element (and its parent element, and so on) also becomes unknown.</span></span>  
  
 <span data-ttu-id="4d15c-148">Şema doğrulama hakkında daha fazla bilgi ve <xref:System.Xml.XPath.XPathNavigator> sınıfı için bkz: [şema XPathNavigator kullanarak doğrulama](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="4d15c-148">For more information about schema validation and the <xref:System.Xml.XPath.XPathNavigator> class, see [Schema Validation using XPathNavigator](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md).</span></span>  
  
### <a name="modifying-attributes"></a><span data-ttu-id="4d15c-149">Özniteliklerini değiştirme</span><span class="sxs-lookup"><span data-stu-id="4d15c-149">Modifying Attributes</span></span>  
 <span data-ttu-id="4d15c-150"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Ve <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> yöntemleri, türsüz ve yazılı özniteliği düğümlerin yanı sıra "Düğümleri değiştirme" bölümünde listelenen diğer düğüm türleri değiştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4d15c-150">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods can be used to modify untyped and typed attribute nodes as well as the other node types listed in the "Modifying Nodes" section.</span></span>  
  
 <span data-ttu-id="4d15c-151">Aşağıdaki örnek değerini değiştirir `genre` ilk öznitelik `book` öğesinde `books.xml` dosya.</span><span class="sxs-lookup"><span data-stu-id="4d15c-151">The following example changes the value of the `genre` attribute of the first `book` element in the `books.xml` file.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", String.Empty)  
navigator.MoveToChild("book", String.Empty)  
navigator.MoveToAttribute("genre", String.Empty)  
  
navigator.SetValue("non-fiction")  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", String.Empty);  
navigator.MoveToChild("book", String.Empty);  
navigator.MoveToAttribute("genre", String.Empty);  
  
navigator.SetValue("non-fiction");  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 <span data-ttu-id="4d15c-152">Hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> ve <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> yöntemleri, "Türsüz değerleri değiştirme" ve "Yazdığınız değerleri değiştirme" bölümlerine bakın.</span><span class="sxs-lookup"><span data-stu-id="4d15c-152">For more information about the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods, see the "Modifying Untyped Values" and "Modifying Typed Values" sections.</span></span>  
  
## <a name="innerxml-and-outerxml-properties"></a><span data-ttu-id="4d15c-153">InnerXml ve OuterXml özellikleri</span><span class="sxs-lookup"><span data-stu-id="4d15c-153">InnerXml and OuterXml Properties</span></span>  
 <span data-ttu-id="4d15c-154"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özelliklerini <xref:System.Xml.XPath.XPathNavigator> sınıfı düğümlerin XML biçimlendirmesini değiştirme bir <xref:System.Xml.XPath.XPathNavigator> nesnesi üzerinde şu anda konumlandırılır.</span><span class="sxs-lookup"><span data-stu-id="4d15c-154">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class change the XML markup of the nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="4d15c-155"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Özellik alt düğümlerin XML biçimlendirme değişiklikleri bir <xref:System.Xml.XPath.XPathNavigator> nesne şu anda konumlandırılır üzerinde verilen XML ayrıştırılmış içeriğini `string`.</span><span class="sxs-lookup"><span data-stu-id="4d15c-155">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on with the parsed contents of the given XML `string`.</span></span> <span data-ttu-id="4d15c-156">Benzer şekilde, <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özellik alt düğümlerin XML biçimlendirme değişiklikleri bir <xref:System.Xml.XPath.XPathNavigator> nesne şu anda konumlandırılır üzerinde geçerli düğüm yanı sıra.</span><span class="sxs-lookup"><span data-stu-id="4d15c-156">Similarly, the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on as well as the current node itself.</span></span>  
  
 <span data-ttu-id="4d15c-157">Aşağıdaki örnek kullanır <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> değerini değiştirmek için özellik `price` öğesi ve yeni bir INSERT `discount` ilk öznitelikte `book` öğesinde `contosoBooks.xml` dosya.</span><span class="sxs-lookup"><span data-stu-id="4d15c-157">The following example uses the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property to modify the value of the `price` element and insert a new `discount` attribute on the first `book` element in the `contosoBooks.xml` file.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml");  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.OuterXml = "<price discount=\"0\">10.99</price>"  
  
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
  
navigator.OuterXml = "<price discount=\"0\">10.99</price>";  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 <span data-ttu-id="4d15c-158">Örnek alır `contosoBooks.xml` dosyayı bir girdi olarak.</span><span class="sxs-lookup"><span data-stu-id="4d15c-158">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
## <a name="modifying-namespace-nodes"></a><span data-ttu-id="4d15c-159">Namespace düğümleri değiştirme</span><span class="sxs-lookup"><span data-stu-id="4d15c-159">Modifying Namespace Nodes</span></span>  
 <span data-ttu-id="4d15c-160">Eklenen, güncelleştirilen silinmiş ve yönetilebilen normal öznitelikler varsa gibi belge nesne modeli (DOM)'da, ad alanı bildirimleri kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="4d15c-160">In the Document Object Model (DOM), namespace declarations are treated as if they are regular attributes that can be inserted, updated and deleted.</span></span> <span data-ttu-id="4d15c-161"><xref:System.Xml.XPath.XPathNavigator> Sınıfı izin vermiyor bu tür işlemler ad alanı düğümlerde ad alanı düğüm değerinin değiştirilmesi aşağıdaki örnekte gösterildiği gibi öğeleri ve öznitelikleri düğüm ad kapsamında kimliğini değişebileceği için.</span><span class="sxs-lookup"><span data-stu-id="4d15c-161">The <xref:System.Xml.XPath.XPathNavigator> class does not allow such operations on namespace nodes because altering the value of a namespace node can change the identity of the elements and attributes within the scope of the namespace node as illustrated in the following example.</span></span>  
  
```xml  
<root xmlns="http://www.contoso.com">  
    <child />  
</root>  
```  
  
 <span data-ttu-id="4d15c-162">Yukarıdaki XML örneği aşağıdaki şekilde değiştirilirse, her öğenin ad alanı URI değeri değiştiğinden bu etkin belgedeki her öğe yeniden adlandırır.</span><span class="sxs-lookup"><span data-stu-id="4d15c-162">If the XML example above is changed in the following way, this effectively renames every element in the document because the value of each element's namespace URI is changed.</span></span>  
  
```xml  
<root xmlns="urn:contoso.com">  
    <child />  
</root>  
```  
  
 <span data-ttu-id="4d15c-163">Ad alanı bildirimleri yerleştirildikleri kapsamındaki çakışmadığından ad alanı düğümleri ekleme tarafından verilir <xref:System.Xml.XPath.XPathNavigator> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4d15c-163">Inserting namespace nodes that do not conflict with namespace declarations at the scope that they are inserted in is allowed by the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="4d15c-164">Bu durumda, ad alanı bildirimleri XML belgesi olarak alt kapsamlar adresindeki bildirilmemiş ve aşağıdaki örnekte gösterildiği gibi yeniden adlandırarak sonuçlanmaz.</span><span class="sxs-lookup"><span data-stu-id="4d15c-164">In this case, the namespace declarations are not declared at lower scopes in the XML document and does not result in renaming as illustrated in the following example.</span></span>  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent>  
        <a:child />  
    </parent>  
</root>  
```  
  
 <span data-ttu-id="4d15c-165">Yukarıdaki XML örneği aşağıdaki şekilde değiştirdiyseniz, ad alanı bildirimleri düzgün bir ad alanı bildiriminin kapsamını aşağıda XML belgesi arasında yayılır.</span><span class="sxs-lookup"><span data-stu-id="4d15c-165">If the XML example above is changed in the following way, the namespace declarations are correctly propagated across the XML document below the scope of the other namespace declaration.</span></span>  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent a:parent-id="1234" xmlns:a="http://www.contoso.com/parent-id">  
        <a:child xmlns:a="http://www.contoso.com/">  
    </parent>  
</root>  
```  
  
 <span data-ttu-id="4d15c-166">Yukarıdaki, öznitelik XML örnekte `a:parent-id` eklenmesini `parent` öğesinde `http://www.contoso.com/parent-id` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="4d15c-166">In the XML example above, the attribute `a:parent-id` is inserted on the `parent` element in the `http://www.contoso.com/parent-id` namespace.</span></span> <span data-ttu-id="4d15c-167"><xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> Yöntemi üzerinde konumlandırılmış sırada özniteliğini eklemek için kullanılan `parent` öğesi.</span><span class="sxs-lookup"><span data-stu-id="4d15c-167">The <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> method is used to insert the attribute while positioned on the `parent` element.</span></span> <span data-ttu-id="4d15c-168">`http://www.contoso.com` Ad alanı bildirimi tarafından otomatik olarak eklenir <xref:System.Xml.XPath.XPathNavigator> XML belgenin geri kalanında tutarlılığını korumak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="4d15c-168">The `http://www.contoso.com` namespace declaration is automatically inserted by the <xref:System.Xml.XPath.XPathNavigator> class to preserve the consistency of the rest of the XML document.</span></span>  
  
## <a name="modifying-entity-reference-nodes"></a><span data-ttu-id="4d15c-169">Varlık başvurusu düğümleri değiştirme</span><span class="sxs-lookup"><span data-stu-id="4d15c-169">Modifying Entity Reference Nodes</span></span>  
 <span data-ttu-id="4d15c-170">Varlık başvurusu düğümler bir <xref:System.Xml.XmlDocument> nesne salt okunur ve ya da kullanarak düzenlenemez <xref:System.Xml.XPath.XPathNavigator> veya <xref:System.Xml.XmlNode> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="4d15c-170">Entity reference nodes in an <xref:System.Xml.XmlDocument> object are read-only and cannot be edited using either the <xref:System.Xml.XPath.XPathNavigator> or <xref:System.Xml.XmlNode> classes.</span></span> <span data-ttu-id="4d15c-171">Bir varlık referans düğümün değiştirmek için her türlü girişim sonuçlanıyor bir <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="4d15c-171">Any attempt to modify an entity reference node results in an <xref:System.InvalidOperationException>.</span></span>  
  
## <a name="modifying-xsinil-nodes"></a><span data-ttu-id="4d15c-172">Xsi: nil düğümleri değiştirme</span><span class="sxs-lookup"><span data-stu-id="4d15c-172">Modifying xsi:nil Nodes</span></span>  
 <span data-ttu-id="4d15c-173">W3C XML Şeması öneri bırakılabilir olan bir öğeyi kavramını sunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4d15c-173">The W3C XML Schema recommendation introduces the concept of an element being nillable.</span></span> <span data-ttu-id="4d15c-174">Bir öğe bırakılabilir olduğunda, öğenin içeriği olmamasına ve hala geçerli olması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="4d15c-174">When an element is nillable, it is possible for the element to have no content and still be valid.</span></span> <span data-ttu-id="4d15c-175">Bir nesne kurulduğunu kavramına bırakılabilir edilen bir öğenin kavram benzer `null`.</span><span class="sxs-lookup"><span data-stu-id="4d15c-175">The concept of an element being nillable is similar to the concept of an object being `null`.</span></span> <span data-ttu-id="4d15c-176">Ana fark bir `null` nesne olamaz herhangi bir şekilde erişilen, ancak bir `xsi:nil` öğesi hala erişilebilir, ancak içeriği (alt öğeler veya metin) yok öznitelikleri gibi özellikler içeriyor.</span><span class="sxs-lookup"><span data-stu-id="4d15c-176">The main difference is that a `null` object cannot be accessed in any way, while an `xsi:nil` element still has properties such as attributes that can be accessed, but has no content (child elements or text).</span></span> <span data-ttu-id="4d15c-177">Varlığını `xsi:nil` öznitelik değerini `true` bir öğede bir XML belgesi öğenin içeriği yok göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4d15c-177">The existence of the `xsi:nil` attribute with a value of `true` on an element in an XML document is used to indicate that an element has no content.</span></span>  
  
 <span data-ttu-id="4d15c-178">Varsa bir <xref:System.Xml.XPath.XPathNavigator> nesne geçerli bir öğesi ile içerik eklemek için kullanılan bir `xsi:nil` öznitelik değerini `true`, değerini kendi `xsi:nil` özniteliği olarak ayarlanmış `false`.</span><span class="sxs-lookup"><span data-stu-id="4d15c-178">If an <xref:System.Xml.XPath.XPathNavigator> object is used to add content to a valid element with an `xsi:nil` attribute with a value of `true`, the value of its `xsi:nil` attribute is set to `false`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4d15c-179">Varsa bir öğesiyle içeriğini bir `xsi:nil` özniteliğini `false` olduğu silinmiş, öznitelik değeri için değiştirilmez `true`.</span><span class="sxs-lookup"><span data-stu-id="4d15c-179">If the content of an element with an `xsi:nil` attribute set to `false` is deleted, the value of the attribute is not changed to `true`.</span></span>  
  
## <a name="saving-an-xml-document"></a><span data-ttu-id="4d15c-180">Bir XML belgesi kaydetme</span><span class="sxs-lookup"><span data-stu-id="4d15c-180">Saving an XML Document</span></span>  
 <span data-ttu-id="4d15c-181">Yapılan değişiklikler kaydedilirken bir <xref:System.Xml.XmlDocument> nesne bu konuda açıklanan düzenleme yöntemleri sonucunu yöntemleri kullanılarak gerçekleştirilir gibi <xref:System.Xml.XmlDocument> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4d15c-181">Saving changes made to an <xref:System.Xml.XmlDocument> object as the result of the editing methods described in this topic is performed using the methods of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="4d15c-182">Yapılan değişiklikleri kaydetme hakkında daha fazla bilgi için bir <xref:System.Xml.XmlDocument> nesne için bkz: [kaydetme ve bir belgeyi yazma](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span><span class="sxs-lookup"><span data-stu-id="4d15c-182">For more information about saving changes made to an <xref:System.Xml.XmlDocument> object, see [Saving and Writing a Document](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d15c-183">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4d15c-183">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="4d15c-184">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="4d15c-184">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="4d15c-185">XPathNavigator Kullanarak XML Verileri Ekleme</span><span class="sxs-lookup"><span data-stu-id="4d15c-185">Insert XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="4d15c-186">XPathNavigator Kullanarak XML Verilerini Kaldırma</span><span class="sxs-lookup"><span data-stu-id="4d15c-186">Remove XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)
