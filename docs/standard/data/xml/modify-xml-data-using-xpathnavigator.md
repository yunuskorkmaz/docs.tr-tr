---
title: XPathNavigator kullanarak XML verilerini değiştirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 03a7c5a1-b296-4af4-b209-043c958dc0a5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 219327d246416cfb3d76919680aa74a58bae5fb3
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43884992"
---
# <a name="modify-xml-data-using-xpathnavigator"></a><span data-ttu-id="352f3-102">XPathNavigator kullanarak XML verilerini değiştirme</span><span class="sxs-lookup"><span data-stu-id="352f3-102">Modify XML Data using XPathNavigator</span></span>
<span data-ttu-id="352f3-103"><xref:System.Xml.XPath.XPathNavigator> Sınıfı düğümleri ve bir XML belgesi değerleri değiştirmek için kullanılan yöntemler kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="352f3-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to modify nodes and values in an XML document.</span></span> <span data-ttu-id="352f3-104">Bu yöntemleri kullanmak için <xref:System.Xml.XPath.XPathNavigator> nesne olmalıdır düzenlenemez, diğer bir deyişle, kendi <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> özelliği olmalıdır `true`.</span><span class="sxs-lookup"><span data-stu-id="352f3-104">In order to use these methods, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be `true`.</span></span>  
  
 <span data-ttu-id="352f3-105"><xref:System.Xml.XPath.XPathNavigator> bir XML belgesi düzenleyebilirsiniz nesneleri <xref:System.Xml.XmlDocument.CreateNavigator%2A> yöntemi <xref:System.Xml.XmlDocument> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="352f3-105"><xref:System.Xml.XPath.XPathNavigator> objects that can edit an XML document are created by the <xref:System.Xml.XmlDocument.CreateNavigator%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="352f3-106"><xref:System.Xml.XPath.XPathNavigator> tarafından oluşturulan nesnelerin <xref:System.Xml.XPath.XPathDocument> sınıfı salt okunurdur ve tüm düzenleme yöntemlerini kullanmayı dener bir <xref:System.Xml.XPath.XPathNavigator> nesnesi tarafından oluşturulan bir <xref:System.Xml.XPath.XPathDocument> nesne sonucunda bir <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="352f3-106"><xref:System.Xml.XPath.XPathNavigator> objects created by the <xref:System.Xml.XPath.XPathDocument> class are read-only and any attempt to use the editing methods of an <xref:System.Xml.XPath.XPathNavigator> object created by an <xref:System.Xml.XPath.XPathDocument> object result in a <xref:System.NotSupportedException>.</span></span>  
  
 <span data-ttu-id="352f3-107">Düzenlenebilir oluşturma hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator> nesneleri bkz [XPathDocument ve XmlDocument kullanarak XML verileri okuma](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span><span class="sxs-lookup"><span data-stu-id="352f3-107">For more information about creating editable <xref:System.Xml.XPath.XPathNavigator> objects, see [Reading XML Data using XPathDocument and XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span></span>  
  
## <a name="modifying-nodes"></a><span data-ttu-id="352f3-108">Düğümleri değiştirme</span><span class="sxs-lookup"><span data-stu-id="352f3-108">Modifying Nodes</span></span>  
 <span data-ttu-id="352f3-109">Bir düğümün değerini değiştirmek için basit bir yöntem kullanmaktır <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> ve <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> yöntemlerinin <xref:System.Xml.XPath.XPathNavigator> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="352f3-109">A simple technique for changing the value of a node is to use the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 <span data-ttu-id="352f3-110">Aşağıdaki tabloda, farklı bir düğüme türlerinin bu yöntemlerin efektleri listeler.</span><span class="sxs-lookup"><span data-stu-id="352f3-110">The following table lists the effects of these methods on different node types.</span></span>  
  
|<xref:System.Xml.XPath.XPathNodeType>|<span data-ttu-id="352f3-111">Değiştirilen veriler</span><span class="sxs-lookup"><span data-stu-id="352f3-111">Data Changed</span></span>|  
|---------------------------------------------------------------------------------------------------------------------------------------------|------------------|  
|<xref:System.Xml.XPath.XPathNodeType.Root>|<span data-ttu-id="352f3-112">Desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="352f3-112">Not supported.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Element>|<span data-ttu-id="352f3-113">Öğe içeriği.</span><span class="sxs-lookup"><span data-stu-id="352f3-113">The content of the element.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Attribute>|<span data-ttu-id="352f3-114">Öznitelik değeri.</span><span class="sxs-lookup"><span data-stu-id="352f3-114">The value of the attribute.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Text>|<span data-ttu-id="352f3-115">Metin içeriği.</span><span class="sxs-lookup"><span data-stu-id="352f3-115">The text content.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.ProcessingInstruction>|<span data-ttu-id="352f3-116">Hedef hariç içeriği.</span><span class="sxs-lookup"><span data-stu-id="352f3-116">The content, excluding the target.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Comment>|<span data-ttu-id="352f3-117">İçerik açıklaması.</span><span class="sxs-lookup"><span data-stu-id="352f3-117">The content of the comment.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Namespace>|<span data-ttu-id="352f3-118">Desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="352f3-118">Not Supported.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="352f3-119">Düzenleme <xref:System.Xml.XPath.XPathNodeType.Namespace> düğümleri veya <xref:System.Xml.XPath.XPathNodeType.Root> düğümü desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="352f3-119">Editing <xref:System.Xml.XPath.XPathNodeType.Namespace> nodes or the <xref:System.Xml.XPath.XPathNodeType.Root> node is not supported.</span></span>  
  
 <span data-ttu-id="352f3-120"><xref:System.Xml.XPath.XPathNavigator> Sınıfı ekleyin ve düğümleri kaldırma için kullanılan yöntemler kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="352f3-120">The <xref:System.Xml.XPath.XPathNavigator> class also provides a set of methods used to insert and remove nodes.</span></span> <span data-ttu-id="352f3-121">Ekleme ve bir XML belgesinden düğümleri kaldırma hakkında daha fazla bilgi için bkz. [Ekle XPathNavigator kullanarak XML verilerini](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md) ve [kaldırmak XPathNavigator kullanarak XML verilerini](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md) konuları.</span><span class="sxs-lookup"><span data-stu-id="352f3-121">For more information about inserting and removing nodes from an XML document, see the [Insert XML Data using XPathNavigator](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md) and [Remove XML Data using XPathNavigator](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md) topics.</span></span>  
  
### <a name="modifying-untyped-values"></a><span data-ttu-id="352f3-122">Yazılmamış değerlerini değiştirme</span><span class="sxs-lookup"><span data-stu-id="352f3-122">Modifying Untyped Values</span></span>  
 <span data-ttu-id="352f3-123"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Yöntemi yalnızca ekler yazılmamış `string` düğümün değeri olarak bir parametre olarak geçirilen değer <xref:System.Xml.XPath.XPathNavigator> nesne üzerinde konumlandırılmış şu anda.</span><span class="sxs-lookup"><span data-stu-id="352f3-123">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method simply inserts the untyped `string` value passed as a parameter as the value of the node the <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="352f3-124">Değer, her türlü olmadan veya şema bilgileri kullanılabilir durumdaysa, yeni değer düğüm türüne göre geçerli olduğu doğrulanıyor olmadan eklenir.</span><span class="sxs-lookup"><span data-stu-id="352f3-124">The value is inserted without any type or without verifying that the new value is valid according to the type of the node if schema information is available.</span></span>  
  
 <span data-ttu-id="352f3-125">Aşağıdaki örnekte, <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> tümünü güncelleştirmek için kullanılan yöntemi `price` öğelerinde `contosoBooks.xml` dosya.</span><span class="sxs-lookup"><span data-stu-id="352f3-125">In the following example, the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method is used to update all `price` elements in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 <span data-ttu-id="352f3-126">Örnek alan `contosoBooks.xml` girdi olarak dosya.</span><span class="sxs-lookup"><span data-stu-id="352f3-126">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="modifying-typed-values"></a><span data-ttu-id="352f3-127">Girilen değerleri değiştirme</span><span class="sxs-lookup"><span data-stu-id="352f3-127">Modifying Typed Values</span></span>  
 <span data-ttu-id="352f3-128">Bir düğüm türü basit bir W3C XML Şeması olduğunda tür, tarafından eklenen yeni değer <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> yöntemi değeri ayarlanmadan önce basit türe ilişkin modelleri karşı denetlenir.</span><span class="sxs-lookup"><span data-stu-id="352f3-128">When the type of a node is a W3C XML Schema simple type, the new value inserted by the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method is checked against the facets of the simple type before the value is set.</span></span> <span data-ttu-id="352f3-129">Yeni değer düğüm türüne göre geçerli değilse (örneğin, bir değeri ayarlamak `-1` türü olan bir öğede `xs:positiveInteger`), bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="352f3-129">If the new value is not valid according to the type of the node (for example, setting a value of `-1` on an element whose type is `xs:positiveInteger`), it results in an exception.</span></span>  
  
 <span data-ttu-id="352f3-130">Aşağıdaki örnek, değerini değiştirme girişiminde `price` ilk öğenin `book` öğesinde `contosoBooks.xml` dosyasını bir <xref:System.DateTime> değeri.</span><span class="sxs-lookup"><span data-stu-id="352f3-130">The following example attempts to change the value of the `price` element of the first `book` element in the `contosoBooks.xml` file to a <xref:System.DateTime> value.</span></span> <span data-ttu-id="352f3-131">XML şema türü olduğundan `price` öğesi olarak tanımlanmış olan `xs:decimal` içinde `contosoBooks.xsd` dosyaları, bu sonuçları bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="352f3-131">Because the XML Schema type of the `price` element is defined as `xs:decimal` in the `contosoBooks.xsd` files, this results in an exception.</span></span>  
  
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
  
 <span data-ttu-id="352f3-132">Örnek alan `contosoBooks.xml` girdi olarak dosya.</span><span class="sxs-lookup"><span data-stu-id="352f3-132">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="352f3-133">Bu örnek ayrıca alır `contosoBooks.xsd` girdi olarak.</span><span class="sxs-lookup"><span data-stu-id="352f3-133">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
#### <a name="the-effects-of-editing-strongly-typed-xml-data"></a><span data-ttu-id="352f3-134">Kesin türü belirtilmiş XML verilerini düzenleme etkileri</span><span class="sxs-lookup"><span data-stu-id="352f3-134">The Effects of Editing Strongly Typed XML Data</span></span>  
 <span data-ttu-id="352f3-135"><xref:System.Xml.XPath.XPathNavigator> Sınıfını kullanan W3C XML şema temel olarak kesin tür belirtilmiş XML açıklamak için.</span><span class="sxs-lookup"><span data-stu-id="352f3-135">The <xref:System.Xml.XPath.XPathNavigator> class uses the W3C XML Schema as a basis for describing strongly-typed XML.</span></span> <span data-ttu-id="352f3-136">Öğeler ve öznitelikler W3C XML şema belgesi karşı doğrulama temel türü bilgilerini ile açıklama eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="352f3-136">Elements and attributes can be annotated with type information based on validation against a W3C XML Schema document.</span></span> <span data-ttu-id="352f3-137">Metinsel içeriği yalnızca içerebilir bunlar basit türler olarak adlandırılır ancak diğer öğeler veya öznitelikleri içeren öğelerin karmaşık türler olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="352f3-137">Elements that can contain other elements or attributes are called complex types, while those that can only contain textual content are called simple types.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="352f3-138">Öznitelikleri Basit türler yalnızca olabilir.</span><span class="sxs-lookup"><span data-stu-id="352f3-138">Attributes can only have simple types.</span></span>  
  
 <span data-ttu-id="352f3-139">Bir öğe veya öznitelik şema türü tanımına belirli kuralları uyuyorsa geçerli olması için kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="352f3-139">An element or attribute can be considered to be schema-valid if it conforms to all the rules specific to its type definition.</span></span> <span data-ttu-id="352f3-140">Basit tür olan bir öğeyi `xs:int` -2147483648 ile 2147483647 şema geçerli olması için arasında sayısal bir değer içermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="352f3-140">An element that has the simple type `xs:int` has to contain a numeric value between -2147483648 and 2147483647 to be schema-valid.</span></span> <span data-ttu-id="352f3-141">Karmaşık türler için öğenin şema geçerlilik şema-geçerliliğini üzerinde kendi alt öğeler ve öznitelikler bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="352f3-141">For complex types, the schema-validity of the element is dependent on the schema-validity of its child elements and attributes.</span></span> <span data-ttu-id="352f3-142">Bu nedenle tüm alt öğeler ve öznitelikler, karmaşık tür tanımına göre bir öğe geçerliyse, tür tanımlarını karşı geçerli.</span><span class="sxs-lookup"><span data-stu-id="352f3-142">Thus if an element is valid against its complex type definition, all its child elements and attributes are valid against their type definitions.</span></span> <span data-ttu-id="352f3-143">Alt öğeleri bile birini veya bir öğenin öznitelikleri tür tanımına karşı geçersiz veya bilinmeyen bir geçerliliği vardır, benzer şekilde, öğe ayrıca geçersiz veya Bilinmeyen geçerlilik.</span><span class="sxs-lookup"><span data-stu-id="352f3-143">Similarly, if even one of the child elements or attributes of an element is invalid against its type definition, or has an unknown validity, the element is also either invalid or of unknown validity.</span></span>  
  
 <span data-ttu-id="352f3-144">Geçerlilik bir öğe, alt öğeler ve öznitelikler geçerliliğini bağımlı olduğu düşünüldüğünde, daha önce geçerli ise öğe geçerliliğini değiştirme ya da bir değişiklik neden.</span><span class="sxs-lookup"><span data-stu-id="352f3-144">Given that the validity of an element is dependent on the validity of its child elements and attributes, modifications to either result in altering the validity of the element if it was previously valid.</span></span> <span data-ttu-id="352f3-145">Bir öğenin öznitelikleri ve alt öğeleri eklenen, güncelleştirilen veya silinen, özellikle daha sonra geçerliliğini öğesinin bilinmeyen olur.</span><span class="sxs-lookup"><span data-stu-id="352f3-145">Specifically, if the child elements or attributes of an element are inserted, updated, or deleted, then the validity of the element becomes unknown.</span></span> <span data-ttu-id="352f3-146">Bu tarafından temsil edilen <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> öğenin özelliği <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> özelliği olan kümesine <xref:System.Xml.Schema.XmlSchemaValidity.NotKnown>.</span><span class="sxs-lookup"><span data-stu-id="352f3-146">This is represented by the <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> property of the element's <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property being set to <xref:System.Xml.Schema.XmlSchemaValidity.NotKnown>.</span></span> <span data-ttu-id="352f3-147">Ayrıca, öğenin üst öğesi (ve kendi üst öğesi vb.) geçerliliğini ayrıca bilinmeyen olur çünkü bu etkiyi yukarı yinelemeli olarak XML belgesi aktarılır.</span><span class="sxs-lookup"><span data-stu-id="352f3-147">Furthermore, this effect cascades upwards recursively across the XML document, because the validity of the element's parent element (and its parent element, and so on) also becomes unknown.</span></span>  
  
 <span data-ttu-id="352f3-148">Şema doğrulaması hakkında daha fazla bilgi ve <xref:System.Xml.XPath.XPathNavigator> sınıfı [XPathNavigator kullanarak şema doğrulama](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="352f3-148">For more information about schema validation and the <xref:System.Xml.XPath.XPathNavigator> class, see [Schema Validation using XPathNavigator](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md).</span></span>  
  
### <a name="modifying-attributes"></a><span data-ttu-id="352f3-149">Öznitelikleri değiştirme</span><span class="sxs-lookup"><span data-stu-id="352f3-149">Modifying Attributes</span></span>  
 <span data-ttu-id="352f3-150"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Ve <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> yöntemleri, türü belirsiz ve yazılmış öznitelik düğümleri ve bunun yanı sıra "Düğümleri değiştirme" bölümünde listelenen diğer düğüm türleri değiştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="352f3-150">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods can be used to modify untyped and typed attribute nodes as well as the other node types listed in the "Modifying Nodes" section.</span></span>  
  
 <span data-ttu-id="352f3-151">Aşağıdaki örnek değiştirir `genre` ilk öznitelik `book` öğesinde `books.xml` dosya.</span><span class="sxs-lookup"><span data-stu-id="352f3-151">The following example changes the value of the `genre` attribute of the first `book` element in the `books.xml` file.</span></span>  
  
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
  
 <span data-ttu-id="352f3-152">Hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> ve <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> yöntemleri "Yazılmamış değerler değiştirme" ve "Yazılan değerleri değiştirme" bölümlere bakın.</span><span class="sxs-lookup"><span data-stu-id="352f3-152">For more information about the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods, see the "Modifying Untyped Values" and "Modifying Typed Values" sections.</span></span>  
  
## <a name="innerxml-and-outerxml-properties"></a><span data-ttu-id="352f3-153">Sınıfının InnerXml ve OuterXml özellikleri</span><span class="sxs-lookup"><span data-stu-id="352f3-153">InnerXml and OuterXml Properties</span></span>  
 <span data-ttu-id="352f3-154"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özelliklerini <xref:System.Xml.XPath.XPathNavigator> sınıfını değiştirin XML işaretlemesini düğümlerin bir <xref:System.Xml.XPath.XPathNavigator> nesne üzerinde konumlandırılmış şu anda.</span><span class="sxs-lookup"><span data-stu-id="352f3-154">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class change the XML markup of the nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="352f3-155"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Özelliğini değiştirir XML işaretlemesini alt düğümlerin bir <xref:System.Xml.XPath.XPathNavigator> nesne şu anda yerde konumlandırılır üzerinde belirli XML ayrıştırılmış içeriğiyle `string`.</span><span class="sxs-lookup"><span data-stu-id="352f3-155">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on with the parsed contents of the given XML `string`.</span></span> <span data-ttu-id="352f3-156">Benzer şekilde, <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özelliğini değiştirir XML işaretlemesini alt düğümlerin bir <xref:System.Xml.XPath.XPathNavigator> nesne şu anda yerde konumlandırılır üzerinde geçerli düğüm yanı sıra kendisini.</span><span class="sxs-lookup"><span data-stu-id="352f3-156">Similarly, the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on as well as the current node itself.</span></span>  
  
 <span data-ttu-id="352f3-157">Aşağıdaki örnekte <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özellik değerini değiştirmek için `price` öğesi ve yeni bir ekleme `discount` ilk öznitelik `book` öğesinde `contosoBooks.xml` dosya.</span><span class="sxs-lookup"><span data-stu-id="352f3-157">The following example uses the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property to modify the value of the `price` element and insert a new `discount` attribute on the first `book` element in the `contosoBooks.xml` file.</span></span>  
  
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
  
 <span data-ttu-id="352f3-158">Örnek alan `contosoBooks.xml` girdi olarak dosya.</span><span class="sxs-lookup"><span data-stu-id="352f3-158">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
## <a name="modifying-namespace-nodes"></a><span data-ttu-id="352f3-159">Namespace düğümleri değiştirme</span><span class="sxs-lookup"><span data-stu-id="352f3-159">Modifying Namespace Nodes</span></span>  
 <span data-ttu-id="352f3-160">Eklenen, güncelleştirilen silindi ve normal öznitelikleri olmaları durumunda gibi belge nesne modeli (DOM)'da, ad alanı bildirimi kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="352f3-160">In the Document Object Model (DOM), namespace declarations are treated as if they are regular attributes that can be inserted, updated and deleted.</span></span> <span data-ttu-id="352f3-161"><xref:System.Xml.XPath.XPathNavigator> Sınıfı izin vermez ad alanı düğümleri bu işlemleri çünkü bir ad alanı düğümü değerini değiştirerek aşağıdaki örnekte gösterildiği gibi öğeleri ve öznitelikleri ad alanı düğümünü kapsamında kimliğini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="352f3-161">The <xref:System.Xml.XPath.XPathNavigator> class does not allow such operations on namespace nodes because altering the value of a namespace node can change the identity of the elements and attributes within the scope of the namespace node as illustrated in the following example.</span></span>  
  
```xml  
<root xmlns="http://www.contoso.com">  
    <child />  
</root>  
```  
  
 <span data-ttu-id="352f3-162">Yukarıdaki XML örneği aşağıdaki şekilde değiştirilirse, her öğenin ad alanı URI değerini değiştiğinden bu etkili bir şekilde belge içindeki her öğe yeniden adlandırır.</span><span class="sxs-lookup"><span data-stu-id="352f3-162">If the XML example above is changed in the following way, this effectively renames every element in the document because the value of each element's namespace URI is changed.</span></span>  
  
```xml  
<root xmlns="urn:contoso.com">  
    <child />  
</root>  
```  
  
 <span data-ttu-id="352f3-163">Ad alanı bildirimi yerleştirildikleri kapsamda ile çakışmadığından ad alanı düğümleri ekleme tarafından verilir <xref:System.Xml.XPath.XPathNavigator> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="352f3-163">Inserting namespace nodes that do not conflict with namespace declarations at the scope that they are inserted in is allowed by the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="352f3-164">Bu durumda, ad alanı bildirimi XML belgesi alt kapsamlar, bildirilmemiş ve aşağıdaki örnekte gösterildiği gibi yeniden adlandırarak sonuçlanmaz.</span><span class="sxs-lookup"><span data-stu-id="352f3-164">In this case, the namespace declarations are not declared at lower scopes in the XML document and does not result in renaming as illustrated in the following example.</span></span>  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent>  
        <a:child />  
    </parent>  
</root>  
```  
  
 <span data-ttu-id="352f3-165">Yukarıdaki XML örneği aşağıdaki şekilde değiştirilirse, ad alanı bildirimi bir ad alanı bildirimi kapsamını aşağıdaki XML belgesi üzerinde doğru şekilde yayılır.</span><span class="sxs-lookup"><span data-stu-id="352f3-165">If the XML example above is changed in the following way, the namespace declarations are correctly propagated across the XML document below the scope of the other namespace declaration.</span></span>  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent a:parent-id="1234" xmlns:a="http://www.contoso.com/parent-id">  
        <a:child xmlns:a="http://www.contoso.com/">  
    </parent>  
</root>  
```  
  
 <span data-ttu-id="352f3-166">Yukarıdaki öznitelik XML örnekte `a:parent-id` eklenmesini `parent` öğesinde `http://www.contoso.com/parent-id` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="352f3-166">In the XML example above, the attribute `a:parent-id` is inserted on the `parent` element in the `http://www.contoso.com/parent-id` namespace.</span></span> <span data-ttu-id="352f3-167"><xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> Konumlandırılıp sırada özniteliğini eklemek için kullanılan yöntemi `parent` öğesi.</span><span class="sxs-lookup"><span data-stu-id="352f3-167">The <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> method is used to insert the attribute while positioned on the `parent` element.</span></span> <span data-ttu-id="352f3-168">`http://www.contoso.com` Ad alanı bildirimi tarafından otomatik olarak eklenir <xref:System.Xml.XPath.XPathNavigator> XML belgenin geri kalanında tutarlılığını korumak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="352f3-168">The `http://www.contoso.com` namespace declaration is automatically inserted by the <xref:System.Xml.XPath.XPathNavigator> class to preserve the consistency of the rest of the XML document.</span></span>  
  
## <a name="modifying-entity-reference-nodes"></a><span data-ttu-id="352f3-169">Varlık başvurusu düğümleri değiştirme</span><span class="sxs-lookup"><span data-stu-id="352f3-169">Modifying Entity Reference Nodes</span></span>  
 <span data-ttu-id="352f3-170">Varlık başvurusu düğümlerin bir <xref:System.Xml.XmlDocument> nesnesi salt okunurdur ve düzenlenemez kullanarak <xref:System.Xml.XPath.XPathNavigator> veya <xref:System.Xml.XmlNode> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="352f3-170">Entity reference nodes in an <xref:System.Xml.XmlDocument> object are read-only and cannot be edited using either the <xref:System.Xml.XPath.XPathNavigator> or <xref:System.Xml.XmlNode> classes.</span></span> <span data-ttu-id="352f3-171">Bir varlık referans düğümün değiştirmek için her türlü girişim sonuçlanıyor bir <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="352f3-171">Any attempt to modify an entity reference node results in an <xref:System.InvalidOperationException>.</span></span>  
  
## <a name="modifying-xsinil-nodes"></a><span data-ttu-id="352f3-172">Xsi: nil düğümleri değiştirme</span><span class="sxs-lookup"><span data-stu-id="352f3-172">Modifying xsi:nil Nodes</span></span>  
 <span data-ttu-id="352f3-173">W3C XML Şeması öneri nillable edilen bir öğenin kavram tanıtılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="352f3-173">The W3C XML Schema recommendation introduces the concept of an element being nillable.</span></span> <span data-ttu-id="352f3-174">Bir öğe nillable, öğenin içeriği olmamasına ve hala geçerli olması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="352f3-174">When an element is nillable, it is possible for the element to have no content and still be valid.</span></span> <span data-ttu-id="352f3-175">Bir nesne olan kavramı nillable edilen bir öğenin kavram benzerdir `null`.</span><span class="sxs-lookup"><span data-stu-id="352f3-175">The concept of an element being nillable is similar to the concept of an object being `null`.</span></span> <span data-ttu-id="352f3-176">Ana fark bir `null` nesne olamaz herhangi bir yolla erişilen, while bir `xsi:nil` öğesi, hala erişilebilir, ancak içerik (alt öğeleri veya metin) yok öznitelikleri gibi özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="352f3-176">The main difference is that a `null` object cannot be accessed in any way, while an `xsi:nil` element still has properties such as attributes that can be accessed, but has no content (child elements or text).</span></span> <span data-ttu-id="352f3-177">Varlığını `xsi:nil` değerine sahip öznitelik `true` bir öğedeki bir XML belge bir öğenin içerik sahip olduğunu göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="352f3-177">The existence of the `xsi:nil` attribute with a value of `true` on an element in an XML document is used to indicate that an element has no content.</span></span>  
  
 <span data-ttu-id="352f3-178">Varsa bir <xref:System.Xml.XPath.XPathNavigator> nesnesi ile geçerli bir öğesi için içerik eklemek için kullanılır bir `xsi:nil` değerine sahip öznitelik `true`, değerini kendi `xsi:nil` özniteliği `false`.</span><span class="sxs-lookup"><span data-stu-id="352f3-178">If an <xref:System.Xml.XPath.XPathNavigator> object is used to add content to a valid element with an `xsi:nil` attribute with a value of `true`, the value of its `xsi:nil` attribute is set to `false`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="352f3-179">Varsa ile bir öğenin içeriğini bir `xsi:nil` özniteliğini `false` olduğu silinmiş, öznitelik değeri için değişmez `true`.</span><span class="sxs-lookup"><span data-stu-id="352f3-179">If the content of an element with an `xsi:nil` attribute set to `false` is deleted, the value of the attribute is not changed to `true`.</span></span>  
  
## <a name="saving-an-xml-document"></a><span data-ttu-id="352f3-180">Bir XML belgesi kaydediliyor</span><span class="sxs-lookup"><span data-stu-id="352f3-180">Saving an XML Document</span></span>  
 <span data-ttu-id="352f3-181">Yapılan değişiklikler kaydedilirken bir <xref:System.Xml.XmlDocument> nesne bu konuda açıklanan düzenleme yöntemlerini sonucunu yöntemleri kullanılarak gerçekleştirilir gibi <xref:System.Xml.XmlDocument> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="352f3-181">Saving changes made to an <xref:System.Xml.XmlDocument> object as the result of the editing methods described in this topic is performed using the methods of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="352f3-182">Yapılan değişiklikleri kaydetme hakkında daha fazla bilgi için bir <xref:System.Xml.XmlDocument> nesne, bkz: [kaydetme ve belge yazma](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span><span class="sxs-lookup"><span data-stu-id="352f3-182">For more information about saving changes made to an <xref:System.Xml.XmlDocument> object, see [Saving and Writing a Document](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="352f3-183">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="352f3-183">See also</span></span>

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [<span data-ttu-id="352f3-184">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="352f3-184">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [<span data-ttu-id="352f3-185">XPathNavigator Kullanarak XML Verileri Ekleme</span><span class="sxs-lookup"><span data-stu-id="352f3-185">Insert XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)  
- [<span data-ttu-id="352f3-186">XPathNavigator Kullanarak XML Verilerini Kaldırma</span><span class="sxs-lookup"><span data-stu-id="352f3-186">Remove XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)
