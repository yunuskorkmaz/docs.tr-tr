---
title: XPathNavigator Kullanarak XML Verilerini Değiştirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 03a7c5a1-b296-4af4-b209-043c958dc0a5
ms.openlocfilehash: 3b64bc8666274798ebaefc87ef3883fcec1ef6b1
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288842"
---
# <a name="modify-xml-data-using-xpathnavigator"></a><span data-ttu-id="aced1-102">XPathNavigator Kullanarak XML Verilerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="aced1-102">Modify XML Data using XPathNavigator</span></span>
<span data-ttu-id="aced1-103">Sınıfı, bir <xref:System.Xml.XPath.XPathNavigator> XML belgesindeki düğümleri ve değerleri değiştirmek için kullanılan bir yöntemler kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="aced1-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to modify nodes and values in an XML document.</span></span> <span data-ttu-id="aced1-104">Bu yöntemleri kullanabilmeniz için <xref:System.Xml.XPath.XPathNavigator> nesnesi düzenlenebilir olmalıdır, yani <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> özelliği olmalıdır `true` .</span><span class="sxs-lookup"><span data-stu-id="aced1-104">In order to use these methods, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be `true`.</span></span>  
  
 <span data-ttu-id="aced1-105"><xref:System.Xml.XPath.XPathNavigator>bir XML belgesini düzenleyebilen nesneler, <xref:System.Xml.XmlDocument.CreateNavigator%2A> sınıfının yöntemiyle oluşturulur <xref:System.Xml.XmlDocument> .</span><span class="sxs-lookup"><span data-stu-id="aced1-105"><xref:System.Xml.XPath.XPathNavigator> objects that can edit an XML document are created by the <xref:System.Xml.XmlDocument.CreateNavigator%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="aced1-106"><xref:System.Xml.XPath.XPathNavigator>sınıfı tarafından oluşturulan nesneler <xref:System.Xml.XPath.XPathDocument> salt okunurdur ve <xref:System.Xml.XPath.XPathNavigator> bir nesne tarafından oluşturulan nesnenin Editing yöntemlerini kullanma girişimleri <xref:System.Xml.XPath.XPathDocument> bir ile sonuçlanır <xref:System.NotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="aced1-106"><xref:System.Xml.XPath.XPathNavigator> objects created by the <xref:System.Xml.XPath.XPathDocument> class are read-only and any attempt to use the editing methods of an <xref:System.Xml.XPath.XPathNavigator> object created by an <xref:System.Xml.XPath.XPathDocument> object result in a <xref:System.NotSupportedException>.</span></span>  
  
 <span data-ttu-id="aced1-107">Düzenlenebilir nesneler oluşturma hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator> bkz. [XPathDocument ve XMLDOCUMENT kullanarak XML verilerini okuma](reading-xml-data-using-xpathdocument-and-xmldocument.md).</span><span class="sxs-lookup"><span data-stu-id="aced1-107">For more information about creating editable <xref:System.Xml.XPath.XPathNavigator> objects, see [Reading XML Data using XPathDocument and XmlDocument](reading-xml-data-using-xpathdocument-and-xmldocument.md).</span></span>  
  
## <a name="modifying-nodes"></a><span data-ttu-id="aced1-108">Düğümleri değiştirme</span><span class="sxs-lookup"><span data-stu-id="aced1-108">Modifying Nodes</span></span>  
 <span data-ttu-id="aced1-109">Bir düğümün değerini değiştirmenin basit bir tekniği, <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> sınıfının ve yöntemlerini kullanmaktır <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="aced1-109">A simple technique for changing the value of a node is to use the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 <span data-ttu-id="aced1-110">Aşağıdaki tabloda, bu yöntemlerin farklı düğüm türlerinde etkileri listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="aced1-110">The following table lists the effects of these methods on different node types.</span></span>  
  
|<xref:System.Xml.XPath.XPathNodeType>|<span data-ttu-id="aced1-111">Değiştirilen veriler</span><span class="sxs-lookup"><span data-stu-id="aced1-111">Data Changed</span></span>|  
|---------------------------------------------------------------------------------------------------------------------------------------------|------------------|  
|<xref:System.Xml.XPath.XPathNodeType.Root>|<span data-ttu-id="aced1-112">Desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="aced1-112">Not supported.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Element>|<span data-ttu-id="aced1-113">Öğenin içeriği.</span><span class="sxs-lookup"><span data-stu-id="aced1-113">The content of the element.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Attribute>|<span data-ttu-id="aced1-114">Özniteliğin değeri.</span><span class="sxs-lookup"><span data-stu-id="aced1-114">The value of the attribute.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Text>|<span data-ttu-id="aced1-115">Metin içeriği.</span><span class="sxs-lookup"><span data-stu-id="aced1-115">The text content.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.ProcessingInstruction>|<span data-ttu-id="aced1-116">Hedef hariç içerik.</span><span class="sxs-lookup"><span data-stu-id="aced1-116">The content, excluding the target.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Comment>|<span data-ttu-id="aced1-117">Yorumun içeriği.</span><span class="sxs-lookup"><span data-stu-id="aced1-117">The content of the comment.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Namespace>|<span data-ttu-id="aced1-118">Desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="aced1-118">Not Supported.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="aced1-119">Düğüm <xref:System.Xml.XPath.XPathNodeType.Namespace> veya düğüm düzenlenme <xref:System.Xml.XPath.XPathNodeType.Root> desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="aced1-119">Editing <xref:System.Xml.XPath.XPathNodeType.Namespace> nodes or the <xref:System.Xml.XPath.XPathNodeType.Root> node is not supported.</span></span>  
  
 <span data-ttu-id="aced1-120"><xref:System.Xml.XPath.XPathNavigator>Sınıfı ayrıca düğüm eklemek ve kaldırmak için kullanılan bir yöntemler kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="aced1-120">The <xref:System.Xml.XPath.XPathNavigator> class also provides a set of methods used to insert and remove nodes.</span></span> <span data-ttu-id="aced1-121">XML belgesinden düğüm ekleme ve kaldırma hakkında daha fazla bilgi için bkz. [XML verilerini XPathNavigator kullanarak ekleme](insert-xml-data-using-xpathnavigator.md) ve XPathNavigator 'YI [kullanarak XML verilerini kaldırma](remove-xml-data-using-xpathnavigator.md) .</span><span class="sxs-lookup"><span data-stu-id="aced1-121">For more information about inserting and removing nodes from an XML document, see the [Insert XML Data using XPathNavigator](insert-xml-data-using-xpathnavigator.md) and [Remove XML Data using XPathNavigator](remove-xml-data-using-xpathnavigator.md) topics.</span></span>  
  
### <a name="modifying-untyped-values"></a><span data-ttu-id="aced1-122">Türsüz değerleri değiştirme</span><span class="sxs-lookup"><span data-stu-id="aced1-122">Modifying Untyped Values</span></span>  
 <span data-ttu-id="aced1-123"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A>Yöntemi, `string` bir parametre olarak geçirilen türsüz değeri <xref:System.Xml.XPath.XPathNavigator> nesnenin şu anda konumlandırılmış olan düğümün değeri olarak ekler.</span><span class="sxs-lookup"><span data-stu-id="aced1-123">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method simply inserts the untyped `string` value passed as a parameter as the value of the node the <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="aced1-124">Değer, herhangi bir tür olmadan veya şema bilgileri kullanılabiliyorsa düğüm türüne göre yeni değerin geçerli olduğunu doğrulamadan eklenir.</span><span class="sxs-lookup"><span data-stu-id="aced1-124">The value is inserted without any type or without verifying that the new value is valid according to the type of the node if schema information is available.</span></span>  
  
 <span data-ttu-id="aced1-125">Aşağıdaki örnekte, <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> yöntemi dosyadaki tüm öğeleri güncelleştirmek için kullanılır `price` `contosoBooks.xml` .</span><span class="sxs-lookup"><span data-stu-id="aced1-125">In the following example, the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method is used to update all `price` elements in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 <span data-ttu-id="aced1-126">Örnek, `contosoBooks.xml` dosyayı bir giriş olarak alır.</span><span class="sxs-lookup"><span data-stu-id="aced1-126">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="modifying-typed-values"></a><span data-ttu-id="aced1-127">Yazılan değerleri değiştirme</span><span class="sxs-lookup"><span data-stu-id="aced1-127">Modifying Typed Values</span></span>  
 <span data-ttu-id="aced1-128">Bir düğümün türü bir W3C XML şeması basit türü olduğunda, yöntemi tarafından yerleştirilen yeni değer, <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> değer ayarlanmadan önce basit türdeki modellerle denetlenir.</span><span class="sxs-lookup"><span data-stu-id="aced1-128">When the type of a node is a W3C XML Schema simple type, the new value inserted by the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method is checked against the facets of the simple type before the value is set.</span></span> <span data-ttu-id="aced1-129">Yeni değer, düğüm türüne göre geçerli değilse (örneğin, `-1` türü olan bir öğe üzerinde değerini ayarlamak `xs:positiveInteger` ), bir özel durumla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="aced1-129">If the new value is not valid according to the type of the node (for example, setting a value of `-1` on an element whose type is `xs:positiveInteger`), it results in an exception.</span></span>  
  
 <span data-ttu-id="aced1-130">Aşağıdaki örnek, `price` dosyasındaki ilk öğe öğesinin değerini `book` `contosoBooks.xml` bir değere değiştirmeye çalışır <xref:System.DateTime> .</span><span class="sxs-lookup"><span data-stu-id="aced1-130">The following example attempts to change the value of the `price` element of the first `book` element in the `contosoBooks.xml` file to a <xref:System.DateTime> value.</span></span> <span data-ttu-id="aced1-131">Öğesinin XML şeması türü `price` dosyalarda olarak tanımlandığından `xs:decimal` `contosoBooks.xsd` , bu durum bir özel durumla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="aced1-131">Because the XML Schema type of the `price` element is defined as `xs:decimal` in the `contosoBooks.xsd` files, this results in an exception.</span></span>  
  
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
  
 <span data-ttu-id="aced1-132">Örnek, `contosoBooks.xml` dosyayı bir giriş olarak alır.</span><span class="sxs-lookup"><span data-stu-id="aced1-132">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="aced1-133">Örnek de `contosoBooks.xsd` bir giriş olarak alır.</span><span class="sxs-lookup"><span data-stu-id="aced1-133">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
#### <a name="the-effects-of-editing-strongly-typed-xml-data"></a><span data-ttu-id="aced1-134">Türü kesin belirlenmiş XML verilerinin düzenlenmesinin etkileri</span><span class="sxs-lookup"><span data-stu-id="aced1-134">The Effects of Editing Strongly Typed XML Data</span></span>  
 <span data-ttu-id="aced1-135"><xref:System.Xml.XPath.XPathNavigator>Sınıfı, türü kesin BELIRLENMIŞ XML 'yi açıklamak için temel olarak W3C XML şemasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="aced1-135">The <xref:System.Xml.XPath.XPathNavigator> class uses the W3C XML Schema as a basis for describing strongly typed XML.</span></span> <span data-ttu-id="aced1-136">Bir W3C XML şema belgesine karşı doğrulamaya dayalı tür bilgileriyle öğe ve özniteliklere açıklama eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="aced1-136">Elements and attributes can be annotated with type information based on validation against a W3C XML Schema document.</span></span> <span data-ttu-id="aced1-137">Diğer öğeleri veya öznitelikleri içerebilen öğelere karmaşık türler denir, ancak yalnızca metinsel içeriğe sahip olanlar basit türler olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="aced1-137">Elements that can contain other elements or attributes are called complex types, while those that can only contain textual content are called simple types.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aced1-138">Özniteliklerde yalnızca basit türler olabilir.</span><span class="sxs-lookup"><span data-stu-id="aced1-138">Attributes can only have simple types.</span></span>  
  
 <span data-ttu-id="aced1-139">Bir öğe veya öznitelik, tür tanımına özgü tüm kurallara uygunsa şema geçerli olarak kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="aced1-139">An element or attribute can be considered to be schema-valid if it conforms to all the rules specific to its type definition.</span></span> <span data-ttu-id="aced1-140">Basit türe sahip bir öğe, `xs:int` şema geçerli olması için-2147483648 ile 2147483647 arasında bir sayısal değer içermelidir.</span><span class="sxs-lookup"><span data-stu-id="aced1-140">An element that has the simple type `xs:int` has to contain a numeric value between -2147483648 and 2147483647 to be schema-valid.</span></span> <span data-ttu-id="aced1-141">Karmaşık türler için, öğenin şema geçerliliği, alt öğelerinin ve özniteliklerinin şema geçerliliği üzerine bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="aced1-141">For complex types, the schema-validity of the element is dependent on the schema-validity of its child elements and attributes.</span></span> <span data-ttu-id="aced1-142">Bu nedenle, bir öğe karmaşık tür tanımına karşı geçerliyse, tüm alt öğeleri ve öznitelikleri tür tanımlarına göre geçerli olur.</span><span class="sxs-lookup"><span data-stu-id="aced1-142">Thus if an element is valid against its complex type definition, all its child elements and attributes are valid against their type definitions.</span></span> <span data-ttu-id="aced1-143">Benzer şekilde, alt öğelerinden biri veya bir öğenin öznitelikleri tür tanımına göre geçersizdir veya bilinmeyen bir geçerlilik içeriyorsa, öğe geçersiz ya da bilinmeyen bir geçerlilik olur.</span><span class="sxs-lookup"><span data-stu-id="aced1-143">Similarly, if even one of the child elements or attributes of an element is invalid against its type definition, or has an unknown validity, the element is also either invalid or of unknown validity.</span></span>  
  
 <span data-ttu-id="aced1-144">Bir öğenin geçerliliği alt öğelerinin ve özniteliklerinin geçerlilik süresine bağlı olduğu için, daha önceden geçerliyse, öğenin geçerliliğini değiştirmeye neden olan değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="aced1-144">Given that the validity of an element is dependent on the validity of its child elements and attributes, modifications to either result in altering the validity of the element if it was previously valid.</span></span> <span data-ttu-id="aced1-145">Özellikle, alt öğeleri veya bir öğenin öznitelikleri eklenirse, güncelleştirilirse veya silinirse, öğenin geçerliliği bilinmiyor olur.</span><span class="sxs-lookup"><span data-stu-id="aced1-145">Specifically, if the child elements or attributes of an element are inserted, updated, or deleted, then the validity of the element becomes unknown.</span></span> <span data-ttu-id="aced1-146">Bu, <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> öğesinin <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> özelliği olarak ayarlanan özelliği tarafından temsil edilir <xref:System.Xml.Schema.XmlSchemaValidity.NotKnown> .</span><span class="sxs-lookup"><span data-stu-id="aced1-146">This is represented by the <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> property of the element's <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property being set to <xref:System.Xml.Schema.XmlSchemaValidity.NotKnown>.</span></span> <span data-ttu-id="aced1-147">Ayrıca, bu efekt, öğenin üst öğesi (ve onun üst öğesi, vb.) geçerliliği da bilinmediği için, bu efekt, XML belgesi genelinde özyinelemeli olarak yukarı doğru bir şekilde basamaklanır.</span><span class="sxs-lookup"><span data-stu-id="aced1-147">Furthermore, this effect cascades upwards recursively across the XML document, because the validity of the element's parent element (and its parent element, and so on) also becomes unknown.</span></span>  
  
 <span data-ttu-id="aced1-148">Şema doğrulaması ve sınıfı hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator> bkz. [XPathNavigator kullanarak şema doğrulaması](schema-validation-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="aced1-148">For more information about schema validation and the <xref:System.Xml.XPath.XPathNavigator> class, see [Schema Validation using XPathNavigator](schema-validation-using-xpathnavigator.md).</span></span>  
  
### <a name="modifying-attributes"></a><span data-ttu-id="aced1-149">Öznitelikleri değiştirme</span><span class="sxs-lookup"><span data-stu-id="aced1-149">Modifying Attributes</span></span>  
 <span data-ttu-id="aced1-150"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A>Ve <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> yöntemleri, türsüz ve yazılan öznitelik düğümlerini ve "düğümleri değiştirme" bölümünde listelenen diğer düğüm türlerini değiştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="aced1-150">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods can be used to modify untyped and typed attribute nodes as well as the other node types listed in the "Modifying Nodes" section.</span></span>  
  
 <span data-ttu-id="aced1-151">Aşağıdaki örnek, `genre` dosyasındaki ilk öğenin özniteliğinin değerini değiştirir `book` `books.xml` .</span><span class="sxs-lookup"><span data-stu-id="aced1-151">The following example changes the value of the `genre` attribute of the first `book` element in the `books.xml` file.</span></span>  
  
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
  
 <span data-ttu-id="aced1-152">Ve yöntemleri hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> , "türsüz değerleri değiştirme" ve "yazılı değerleri değiştirme" bölümlerine bakın.</span><span class="sxs-lookup"><span data-stu-id="aced1-152">For more information about the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods, see the "Modifying Untyped Values" and "Modifying Typed Values" sections.</span></span>  
  
## <a name="innerxml-and-outerxml-properties"></a><span data-ttu-id="aced1-153">InnerXml ve OuterXml özellikleri</span><span class="sxs-lookup"><span data-stu-id="aced1-153">InnerXml and OuterXml Properties</span></span>  
 <span data-ttu-id="aced1-154"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A>Sınıfının ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> Özellikleri, <xref:System.Xml.XPath.XPathNavigator> bir <xref:System.Xml.XPath.XPathNavigator> nesnenin şu anda konumlandırılmış olduğu düğümlerin XML işaretlemesini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="aced1-154">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class change the XML markup of the nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="aced1-155"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A>Özelliği, <xref:System.Xml.XPath.XPathNavigator> belirtilen XML 'nin ayrıştırılmış içeriğiyle bir nesne şu anda konumlandırılmış olan alt düğümlerin XML işaretlemesini değiştirir `string` .</span><span class="sxs-lookup"><span data-stu-id="aced1-155">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on with the parsed contents of the given XML `string`.</span></span> <span data-ttu-id="aced1-156">Benzer şekilde, <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özelliği de bir nesnenin şu anda bulunduğu alt DÜĞÜMLERIN XML işaretlemesini ve <xref:System.Xml.XPath.XPathNavigator> geçerli düğümün kendisini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="aced1-156">Similarly, the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on as well as the current node itself.</span></span>  
  
 <span data-ttu-id="aced1-157">Aşağıdaki örnek, <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> öğesinin değerini değiştirmek `price` ve `discount` dosyadaki ilk öğeye yeni bir öznitelik eklemek için özelliğini kullanır `book` `contosoBooks.xml` .</span><span class="sxs-lookup"><span data-stu-id="aced1-157">The following example uses the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property to modify the value of the `price` element and insert a new `discount` attribute on the first `book` element in the `contosoBooks.xml` file.</span></span>  
  
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
  
 <span data-ttu-id="aced1-158">Örnek, `contosoBooks.xml` dosyayı bir giriş olarak alır.</span><span class="sxs-lookup"><span data-stu-id="aced1-158">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
## <a name="modifying-namespace-nodes"></a><span data-ttu-id="aced1-159">Ad alanı düğümlerini değiştirme</span><span class="sxs-lookup"><span data-stu-id="aced1-159">Modifying Namespace Nodes</span></span>  
 <span data-ttu-id="aced1-160">Belge Nesne Modeli (DOM) içinde, ad alanı bildirimleri eklenebilir, güncelleştirilemeyebilir ve silinebilecek normal öznitelikler gibi değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="aced1-160">In the Document Object Model (DOM), namespace declarations are treated as if they are regular attributes that can be inserted, updated and deleted.</span></span> <span data-ttu-id="aced1-161"><xref:System.Xml.XPath.XPathNavigator>Bir ad alanı düğümünün değerini değiştirme, aşağıdaki örnekte gösterildiği gibi ad alanı düğümünün kapsamındaki öğelerin ve özniteliklerin kimliğini değiştirebildiğinden, sınıf ad alanı düğümleri üzerinde bu tür işlemlere izin vermez.</span><span class="sxs-lookup"><span data-stu-id="aced1-161">The <xref:System.Xml.XPath.XPathNavigator> class does not allow such operations on namespace nodes because altering the value of a namespace node can change the identity of the elements and attributes within the scope of the namespace node as illustrated in the following example.</span></span>  
  
```xml  
<root xmlns="http://www.contoso.com">  
    <child />  
</root>  
```  
  
 <span data-ttu-id="aced1-162">Yukarıdaki XML örneği aşağıdaki şekilde değiştirilirse, her bir öğenin ad alanı URI 'sinin değeri değiştiği için bu, belgedeki her öğeyi etkili bir şekilde yeniden adlandırır.</span><span class="sxs-lookup"><span data-stu-id="aced1-162">If the XML example above is changed in the following way, this effectively renames every element in the document because the value of each element's namespace URI is changed.</span></span>  
  
```xml  
<root xmlns="urn:contoso.com">  
    <child />  
</root>  
```  
  
 <span data-ttu-id="aced1-163">İçinde eklendiği kapsamda ad alanı bildirimleriyle çakışmayan ad alanı düğümlerine ekleme, sınıfı tarafından izin veriliyor <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="aced1-163">Inserting namespace nodes that do not conflict with namespace declarations at the scope that they are inserted in is allowed by the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="aced1-164">Bu durumda, ad alanı bildirimleri XML belgesindeki daha düşük kapsamlar olarak bildirilmez ve aşağıdaki örnekte gösterildiği gibi yeniden adlandırmayla sonuçlanmaz.</span><span class="sxs-lookup"><span data-stu-id="aced1-164">In this case, the namespace declarations are not declared at lower scopes in the XML document and does not result in renaming as illustrated in the following example.</span></span>  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent>  
        <a:child />  
    </parent>  
</root>  
```  
  
 <span data-ttu-id="aced1-165">Yukarıdaki XML örneği aşağıdaki şekilde değiştirilirse, ad alanı bildirimleri diğer ad alanı bildiriminin kapsamındaki XML belgesi üzerine doğru şekilde yayılır.</span><span class="sxs-lookup"><span data-stu-id="aced1-165">If the XML example above is changed in the following way, the namespace declarations are correctly propagated across the XML document below the scope of the other namespace declaration.</span></span>  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent a:parent-id="1234" xmlns:a="http://www.contoso.com/parent-id">  
        <a:child xmlns:a="http://www.contoso.com/" />  
    </parent>  
</root>  
```  
  
 <span data-ttu-id="aced1-166">Yukarıdaki XML örneğinde, özniteliği `a:parent-id` `parent` `http://www.contoso.com/parent-id` ad alanındaki öğesine eklenir.</span><span class="sxs-lookup"><span data-stu-id="aced1-166">In the XML example above, the attribute `a:parent-id` is inserted on the `parent` element in the `http://www.contoso.com/parent-id` namespace.</span></span> <span data-ttu-id="aced1-167"><xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A>Yöntemi, öğesinde konumlandırılmış özniteliği eklemek için kullanılır `parent` .</span><span class="sxs-lookup"><span data-stu-id="aced1-167">The <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> method is used to insert the attribute while positioned on the `parent` element.</span></span> <span data-ttu-id="aced1-168">`http://www.contoso.com`Ad alanı bildirimi, <xref:System.Xml.XPath.XPathNavigator> XML belgesinin geri kalanının tutarlılığını korumak için sınıfı tarafından otomatik olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="aced1-168">The `http://www.contoso.com` namespace declaration is automatically inserted by the <xref:System.Xml.XPath.XPathNavigator> class to preserve the consistency of the rest of the XML document.</span></span>  
  
## <a name="modifying-entity-reference-nodes"></a><span data-ttu-id="aced1-169">Varlık başvurusu düğümlerini değiştirme</span><span class="sxs-lookup"><span data-stu-id="aced1-169">Modifying Entity Reference Nodes</span></span>  
 <span data-ttu-id="aced1-170">Bir nesnedeki varlık başvuru düğümleri <xref:System.Xml.XmlDocument> salt okunurdur ve ya da sınıfları kullanılarak düzenlenemez <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XmlNode> .</span><span class="sxs-lookup"><span data-stu-id="aced1-170">Entity reference nodes in an <xref:System.Xml.XmlDocument> object are read-only and cannot be edited using either the <xref:System.Xml.XPath.XPathNavigator> or <xref:System.Xml.XmlNode> classes.</span></span> <span data-ttu-id="aced1-171">Bir varlık başvuru düğümünü değiştirme girişimleri bir ile sonuçlanır <xref:System.InvalidOperationException> .</span><span class="sxs-lookup"><span data-stu-id="aced1-171">Any attempt to modify an entity reference node results in an <xref:System.InvalidOperationException>.</span></span>  
  
## <a name="modifying-xsinil-nodes"></a><span data-ttu-id="aced1-172">Xsi: Nil düğümlerini değiştirme</span><span class="sxs-lookup"><span data-stu-id="aced1-172">Modifying xsi:nil Nodes</span></span>  
 <span data-ttu-id="aced1-173">W3C XML şeması önerisi, boş bırakılamakta olan bir öğe kavramını tanıtır.</span><span class="sxs-lookup"><span data-stu-id="aced1-173">The W3C XML Schema recommendation introduces the concept of an element being nillable.</span></span> <span data-ttu-id="aced1-174">Bir öğe boş bırakıldığında, öğede içerik olmaması ve hala geçerli olması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="aced1-174">When an element is nillable, it is possible for the element to have no content and still be valid.</span></span> <span data-ttu-id="aced1-175">Boş bırakılmakta olan bir öğe kavramı, nesne kavramıyla benzerdir `null` .</span><span class="sxs-lookup"><span data-stu-id="aced1-175">The concept of an element being nillable is similar to the concept of an object being `null`.</span></span> <span data-ttu-id="aced1-176">Temel fark, bir `null` nesneye hiçbir şekilde erişilememektedir, `xsi:nil` ancak bir öğesi erişilebilir ancak içeriğe (alt öğe veya metin) sahip olmayan nitelikler gibi özelliklere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="aced1-176">The main difference is that a `null` object cannot be accessed in any way, while an `xsi:nil` element still has properties such as attributes that can be accessed, but has no content (child elements or text).</span></span> <span data-ttu-id="aced1-177">Bir `xsi:nil` XML belgesindeki öğesi üzerinde değeri olan özniteliğin varlığı, `true` bir öğenin içeriğe sahip olmadığını göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aced1-177">The existence of the `xsi:nil` attribute with a value of `true` on an element in an XML document is used to indicate that an element has no content.</span></span>  
  
 <span data-ttu-id="aced1-178">Bir <xref:System.Xml.XPath.XPathNavigator> nesnesi, değeri olan bir özniteliğe sahip geçerli bir öğeye içerik eklemek için kullanılırsa `xsi:nil` `true` , `xsi:nil` özniteliğinin değeri olarak ayarlanır `false` .</span><span class="sxs-lookup"><span data-stu-id="aced1-178">If an <xref:System.Xml.XPath.XPathNavigator> object is used to add content to a valid element with an `xsi:nil` attribute with a value of `true`, the value of its `xsi:nil` attribute is set to `false`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aced1-179">`xsi:nil`Özniteliği olarak ayarlanmış bir öğenin içeriği `false` silinirse, özniteliğinin değeri olarak değiştirilmez `true` .</span><span class="sxs-lookup"><span data-stu-id="aced1-179">If the content of an element with an `xsi:nil` attribute set to `false` is deleted, the value of the attribute is not changed to `true`.</span></span>  
  
## <a name="saving-an-xml-document"></a><span data-ttu-id="aced1-180">XML belgesi kaydetme</span><span class="sxs-lookup"><span data-stu-id="aced1-180">Saving an XML Document</span></span>  
 <span data-ttu-id="aced1-181"><xref:System.Xml.XmlDocument>Bu konu başlığı altında açıklanan Düzenle yöntemlerinin sonucu olarak bir nesne üzerinde yapılan değişikliklerin kaydedilmesi, sınıfının yöntemleri kullanılarak gerçekleştirilir <xref:System.Xml.XmlDocument> .</span><span class="sxs-lookup"><span data-stu-id="aced1-181">Saving changes made to an <xref:System.Xml.XmlDocument> object as the result of the editing methods described in this topic is performed using the methods of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="aced1-182">Bir nesne üzerinde yapılan değişiklikleri kaydetme hakkında daha fazla bilgi için <xref:System.Xml.XmlDocument> bkz. [belgeyi kaydetme ve yazma](saving-and-writing-a-document.md).</span><span class="sxs-lookup"><span data-stu-id="aced1-182">For more information about saving changes made to an <xref:System.Xml.XmlDocument> object, see [Saving and Writing a Document](saving-and-writing-a-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aced1-183">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aced1-183">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="aced1-184">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="aced1-184">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="aced1-185">XPathNavigator Kullanarak XML Verileri Ekleme</span><span class="sxs-lookup"><span data-stu-id="aced1-185">Insert XML Data using XPathNavigator</span></span>](insert-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="aced1-186">XPathNavigator Kullanarak XML Verilerini Kaldırma</span><span class="sxs-lookup"><span data-stu-id="aced1-186">Remove XML Data using XPathNavigator</span></span>](remove-xml-data-using-xpathnavigator.md)
