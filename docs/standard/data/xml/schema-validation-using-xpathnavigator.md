---
title: XPathNavigator kullanarak şema doğrulaması
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 81fa0e41-d9c9-46f0-b22b-50da839c77f5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 98403176c3af8e110bd8d7677fae715fee84baec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33578359"
---
# <a name="schema-validation-using-xpathnavigator"></a><span data-ttu-id="b2e48-102">XPathNavigator kullanarak şema doğrulaması</span><span class="sxs-lookup"><span data-stu-id="b2e48-102">Schema Validation using XPathNavigator</span></span>
<span data-ttu-id="b2e48-103">Kullanarak <xref:System.Xml.XmlDocument> sınıfı, bulunan XML içeriği doğrulamak bir <xref:System.Xml.XmlDocument> iki yolla nesnesi.</span><span class="sxs-lookup"><span data-stu-id="b2e48-103">Using the <xref:System.Xml.XmlDocument> class, you can validate the XML content contained in an <xref:System.Xml.XmlDocument> object in two ways.</span></span> <span data-ttu-id="b2e48-104">Bir doğrulama kullanarak XML içeriği doğrulamak için ilk yoludur <xref:System.Xml.XmlReader> nesne ve ikinci yol kullanmaktır <xref:System.Xml.XmlDocument.Validate%2A> yöntemi <xref:System.Xml.XmlDocument> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b2e48-104">The first way is to validate the XML content using a validating <xref:System.Xml.XmlReader> object and the second way is to use the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="b2e48-105">XML kullanarak içeriğin salt okunur doğrulama de gerçekleştirebilirsiniz <xref:System.Xml.XPath.XPathDocument> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b2e48-105">You can also perform read-only validation of XML content using the <xref:System.Xml.XPath.XPathDocument> class.</span></span>  
  
## <a name="validating-xml-data"></a><span data-ttu-id="b2e48-106">XML verileri doğrulama</span><span class="sxs-lookup"><span data-stu-id="b2e48-106">Validating XML Data</span></span>  
 <span data-ttu-id="b2e48-107"><xref:System.Xml.XmlDocument> Sınıfı DTD veya XML Şeması Tanım Dili (XSD) şema doğrulaması varsayılan olarak kullanarak bir XML belgesi doğrulamaz.</span><span class="sxs-lookup"><span data-stu-id="b2e48-107">The <xref:System.Xml.XmlDocument> class does not validate an XML document using either DTD or XML schema definition language (XSD) schema validation by default.</span></span> <span data-ttu-id="b2e48-108">Yalnızca XML belgesi doğru biçimlendirildiğinden emin doğrular.</span><span class="sxs-lookup"><span data-stu-id="b2e48-108">It only verifies that the XML document is well formed.</span></span>  
  
 <span data-ttu-id="b2e48-109">Bir XML belgesi doğrulamak için ilk belge içine yüklenmiş olarak doğrulamak için yoludur bir <xref:System.Xml.XmlDocument> bir doğrulama kullanarak nesne <xref:System.Xml.XmlReader> nesne.</span><span class="sxs-lookup"><span data-stu-id="b2e48-109">The first way to validate an XML document is to validate the document as it is loaded into an <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="b2e48-110">Daha önce türü belirsiz XML belge kullanarak bir doğrulamak için ikinci yoludur <xref:System.Xml.XmlDocument.Validate%2A> yöntemi <xref:System.Xml.XmlDocument> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b2e48-110">The second way is to validate a previously untyped XML document using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="b2e48-111">Her iki durumda da doğrulanmış XML belgeye yapılan değişiklikler kullanarak yeniden doğrulanır <xref:System.Xml.XmlDocument.Validate%2A> yöntemi <xref:System.Xml.XmlDocument> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b2e48-111">In both cases, changes to the validated XML document can be revalidated using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
### <a name="validating-a-document-as-it-is-loaded"></a><span data-ttu-id="b2e48-112">Bir belgeyle doğrulama yüklendi</span><span class="sxs-lookup"><span data-stu-id="b2e48-112">Validating a Document as it is Loaded</span></span>  
 <span data-ttu-id="b2e48-113">Bir doğrulama <xref:System.Xml.XmlReader> nesne geçirerek oluşturulur bir <xref:System.Xml.XmlReaderSettings> nesnesini <xref:System.Xml.XmlReader.Create%2A> yöntemi <xref:System.Xml.XmlReader> geçen sınıfı bir <xref:System.Xml.XmlReaderSettings> nesnesini parametre olarak.</span><span class="sxs-lookup"><span data-stu-id="b2e48-113">A validating <xref:System.Xml.XmlReader> object is created by passing an <xref:System.Xml.XmlReaderSettings> object to the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class that takes an <xref:System.Xml.XmlReaderSettings> object as a parameter.</span></span> <span data-ttu-id="b2e48-114"><xref:System.Xml.XmlReaderSettings> Nesnesi geçirildi bir parametre içeriyor gibi bir <xref:System.Xml.XmlReaderSettings.ValidationType%2A> özelliğini `Schema` ve XML Şeması bulunan XML belgesi için bir <xref:System.Xml.XmlDocument> eklenen nesne kendi <xref:System.Xml.XmlReaderSettings.Schemas%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="b2e48-114">The <xref:System.Xml.XmlReaderSettings> object passed as a parameter has a <xref:System.Xml.XmlReaderSettings.ValidationType%2A> property set to `Schema` and an XML Schema for the XML document contained in the <xref:System.Xml.XmlDocument> object added to its <xref:System.Xml.XmlReaderSettings.Schemas%2A> property.</span></span> <span data-ttu-id="b2e48-115">Doğrulama <xref:System.Xml.XmlReader> nesnesi oluşturmak için kullanılan sonra <xref:System.Xml.XmlDocument> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="b2e48-115">The validating <xref:System.Xml.XmlReader> object is then used to create the <xref:System.Xml.XmlDocument> object.</span></span>  
  
 <span data-ttu-id="b2e48-116">Aşağıdaki örnek doğrular `contosoBooks.xml` dosya içine yüklenmiş gibi <xref:System.Xml.XmlDocument> oluşturarak nesne <xref:System.Xml.XmlDocument> bir doğrulama kullanarak nesne <xref:System.Xml.XmlReader> nesne.</span><span class="sxs-lookup"><span data-stu-id="b2e48-116">The following example validates the `contosoBooks.xml` file as it is loaded into the <xref:System.Xml.XmlDocument> object by creating the <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="b2e48-117">XML belgesi, şemaya göre geçerli olduğundan, hiçbir şema doğrulama hatalarıyla veya uyarıları üretilir.</span><span class="sxs-lookup"><span data-stu-id="b2e48-117">Because the XML document is valid according to its schema, no schema validation errors or warnings are generated.</span></span>  
  
```vb  
Imports System  
Imports System.Xml  
Imports System.Xml.Schema  
Imports System.Xml.XPath  
  
Class ValidatingReaderExample  
  
    Shared Sub Main(ByVal args() As String)  
  
        Try  
            Dim settings As XmlReaderSettings = New XmlReaderSettings()  
            settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
            settings.ValidationType = ValidationType.Schema  
  
            Dim reader As XmlReader = XmlReader.Create("contosoBooks.xml", settings)  
  
            Dim document As XmlDocument = New XmlDocument()  
            document.Load(reader)  
            Dim navigator As XPathNavigator = document.CreateNavigator()  
  
        Catch e As Exception  
            Console.WriteLine("ValidatingReaderExample.Exception: {0}", e.Message)  
        End Try  
  
    End Sub  
  
    Shared Sub SchemaValidationHandler(ByVal sender As Object, ByVal e As ValidationEventArgs)  
  
        Select Case e.Severity  
            Case XmlSeverityType.Error  
                Console.WriteLine("Schema Validation Error: {0}", e.Message)  
                Exit Sub  
            Case XmlSeverityType.Warning  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message)  
                Exit Sub  
        End Select  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using System.Xml;  
using System.Xml.Schema;  
using System.Xml.XPath;  
  
class ValidatingReaderExample  
{  
    static void Main(string[] args)  
    {  
        try  
        {  
            XmlReaderSettings settings = new XmlReaderSettings();  
            settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
            settings.ValidationType = ValidationType.Schema;  
  
            XmlReader reader = XmlReader.Create("contosoBooks.xml", settings);  
  
            XmlDocument document = new XmlDocument();  
            document.Load(reader);  
            XPathNavigator navigator = document.CreateNavigator();  
        }  
        catch (Exception e)  
        {  
            Console.WriteLine("ValidatingReaderExample.Exception: {0}", e.Message);  
        }  
    }  
  
    static void SchemaValidationHandler(object sender, ValidationEventArgs e)  
    {  
        switch (e.Severity)  
        {  
            case XmlSeverityType.Error:  
                Console.WriteLine("Schema Validation Error: {0}", e.Message);  
                break;  
            case XmlSeverityType.Warning:  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message);  
                break;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="b2e48-118">Örnek alır `contosoBooks.xml` dosyayı bir girdi olarak.</span><span class="sxs-lookup"><span data-stu-id="b2e48-118">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="b2e48-119">Bu örnek ayrıca alır `contosoBooks.xsd` bir girdi olarak.</span><span class="sxs-lookup"><span data-stu-id="b2e48-119">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 <span data-ttu-id="b2e48-120">Yukarıdaki örnekte, bir <xref:System.Xml.Schema.XmlSchemaValidationException> olduğunda oluşturulur <xref:System.Xml.XmlDocument.Load%2A> herhangi bir öznitelik veya öğe türü doğrulama şemasında belirtilen karşılık gelen türü eşleşmiyorsa olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="b2e48-120">In the above example, an <xref:System.Xml.Schema.XmlSchemaValidationException> will be thrown when <xref:System.Xml.XmlDocument.Load%2A> is called if any attribute or element type does not match the corresponding type specified in the validating schema.</span></span> <span data-ttu-id="b2e48-121">Varsa bir <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> doğrulama üzerinde ayarlanır <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> geçersiz bir tür karşılaşıldığında çağrılmadığı.</span><span class="sxs-lookup"><span data-stu-id="b2e48-121">If a <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> is set on the validating <xref:System.Xml.XmlReader>, the <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> will get called whenever an invalid type is encountered.</span></span>  
  
 <span data-ttu-id="b2e48-122">Bir <xref:System.Xml.Schema.XmlSchemaException> bir öznitelik veya öğeyle durum <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> kümesine `invalid` tarafından erişilen <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="b2e48-122">An <xref:System.Xml.Schema.XmlSchemaException> will be thrown when an attribute or element with <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> set to `invalid` is accessed by the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
 <span data-ttu-id="b2e48-123"><xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> Özelliği, bir tek özniteliği veya öğenin öznitelikleri veya öğeleriyle erişirken geçerli olup olmadığını belirlemek için kullanılabilir <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="b2e48-123">The <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> property can be used to determine whether or not an individual attribute or element is valid when accessing attributes or elements with the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2e48-124">Ne zaman bir XML belgesi yüklendiği içine bir <xref:System.Xml.XmlDocument> varsayılan değerleri tanımlayan bir ilişkili şema nesnesiyle <xref:System.Xml.XmlDocument> nesne XML belgesinde göründüğü gibi bu varsayılan değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="b2e48-124">When an XML document is loaded into an <xref:System.Xml.XmlDocument> object with an associated schema that defines default values, the <xref:System.Xml.XmlDocument> object treats these defaults as if they appeared in the XML document.</span></span> <span data-ttu-id="b2e48-125">Bunun anlamı <xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> özelliği her zaman döndürür `false` XML belgesinde boş bir öğe olarak yazılmış olsa bile, şema, varsayılan bir öğe için.</span><span class="sxs-lookup"><span data-stu-id="b2e48-125">This means that the <xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> property  always returns `false` for an element that was defaulted from the schema, even if in the XML document it was written as an empty element.</span></span>  
  
### <a name="validating-a-document-using-the-validate-method"></a><span data-ttu-id="b2e48-126">Doğrulama yöntemini kullanarak bir belge doğrulanıyor</span><span class="sxs-lookup"><span data-stu-id="b2e48-126">Validating a Document using the Validate Method</span></span>  
 <span data-ttu-id="b2e48-127"><xref:System.Xml.XmlDocument.Validate%2A> Yöntemi <xref:System.Xml.XmlDocument> sınıfı doğrular bulunan XML belgesi bir <xref:System.Xml.XmlDocument> belirtilen şemaları nesneyle <xref:System.Xml.XmlDocument> nesnenin <xref:System.Xml.XmlDocument.Schemas%2A> özelliği ve bilgi augmentation'a gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="b2e48-127">The <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class validates the XML document contained in an <xref:System.Xml.XmlDocument> object against the schemas specified in the <xref:System.Xml.XmlDocument> object's <xref:System.Xml.XmlDocument.Schemas%2A> property and performs infoset augmentation.</span></span> <span data-ttu-id="b2e48-128">Daha önce türü belirsiz XML belgesinde sonucudur <xref:System.Xml.XmlDocument> nesne türü belirtilmiş bir belgeyle değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="b2e48-128">The result is a previously untyped XML document in the <xref:System.Xml.XmlDocument> object replaced with a typed document.</span></span>  
  
 <span data-ttu-id="b2e48-129"><xref:System.Xml.XmlDocument> Nesne, şema doğrulama hataları ve Uyarıları kullanarak raporları <xref:System.Xml.Schema.ValidationEventHandler> temsilci geçirilen parametre olarak <xref:System.Xml.XmlDocument.Validate%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b2e48-129">The <xref:System.Xml.XmlDocument> object reports schema validation errors and warnings using the <xref:System.Xml.Schema.ValidationEventHandler> delegate passed as a parameter to the <xref:System.Xml.XmlDocument.Validate%2A> method.</span></span>  
  
 <span data-ttu-id="b2e48-130">Aşağıdaki örnek doğrular `contosoBooks.xml` içinde yer alan dosya <xref:System.Xml.XmlDocument> karşı nesne `contosoBooks.xsd` içinde yer alan şema <xref:System.Xml.XmlDocument> nesnenin <xref:System.Xml.XmlDocument.Schemas%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="b2e48-130">The following example validates the `contosoBooks.xml` file contained in the <xref:System.Xml.XmlDocument> object against the `contosoBooks.xsd` schema contained in the <xref:System.Xml.XmlDocument> object's <xref:System.Xml.XmlDocument.Schemas%2A> property.</span></span>  
  
```vb  
Imports System  
Imports System.Xml  
Imports System.Xml.Schema  
Imports System.Xml.XPath  
  
Class ValidateExample  
  
    Shared Sub Main(ByVal args() As String)  
  
        Dim document As XmlDocument = New XmlDocument()  
        document.Load("contosoBooks.xml")  
        Dim navigator As XPathNavigator = document.CreateNavigator()  
  
        document.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
        Dim validation As ValidationEventHandler = New ValidationEventHandler(AddressOf SchemaValidationHandler)  
  
        document.Validate(validation)  
  
    End Sub  
  
    Shared Sub SchemaValidationHandler(ByVal sender As Object, ByVal e As ValidationEventArgs)  
  
        Select Case e.Severity  
            Case XmlSeverityType.Error  
                Console.WriteLine("Schema Validation Error: {0}", e.Message)  
                Exit Sub  
            Case XmlSeverityType.Warning  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message)  
                Exit Sub  
        End Select  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using System.Xml;  
using System.Xml.Schema;  
using System.Xml.XPath;  
  
class ValidateExample  
{  
    static void Main(string[] args)  
    {  
        XmlDocument document = new XmlDocument();  
        document.Load("contosoBooks.xml");  
        XPathNavigator navigator = document.CreateNavigator();  
  
        document.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
        ValidationEventHandler validation = new ValidationEventHandler(SchemaValidationHandler);  
  
        document.Validate(validation);  
    }  
  
    static void SchemaValidationHandler(object sender, ValidationEventArgs e)  
    {  
        switch (e.Severity)  
        {  
            case XmlSeverityType.Error:  
                Console.WriteLine("Schema Validation Error: {0}", e.Message);  
                break;  
            case XmlSeverityType.Warning:  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message);  
                break;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="b2e48-131">Örnek alır `contosoBooks.xml` dosyayı bir girdi olarak.</span><span class="sxs-lookup"><span data-stu-id="b2e48-131">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="b2e48-132">Bu örnek ayrıca alır `contosoBooks.xsd` bir girdi olarak.</span><span class="sxs-lookup"><span data-stu-id="b2e48-132">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
### <a name="validating-modifications"></a><span data-ttu-id="b2e48-133">Değişiklikler doğrulanıyor</span><span class="sxs-lookup"><span data-stu-id="b2e48-133">Validating Modifications</span></span>  
 <span data-ttu-id="b2e48-134">Bir XML belgesi değişiklikler yapıldıktan sonra XML belge kullanan bir şemaya karşı değişiklikleri doğrulamak için <xref:System.Xml.XmlDocument.Validate%2A> yöntemi <xref:System.Xml.XmlDocument> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b2e48-134">After modifications are made to an XML document, you can validate the modifications against the schema for the XML document using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="b2e48-135">Aşağıdaki örnek doğrular `contosoBooks.xml` dosya içine yüklenmiş gibi <xref:System.Xml.XmlDocument> oluşturarak nesne <xref:System.Xml.XmlDocument> bir doğrulama kullanarak nesne <xref:System.Xml.XmlReader> nesne.</span><span class="sxs-lookup"><span data-stu-id="b2e48-135">The following example validates the `contosoBooks.xml` file as it is loaded into the <xref:System.Xml.XmlDocument> object by creating the <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="b2e48-136">Herhangi bir şema doğrulama hatalarıyla veya uyarıları oluşturmadan yüklendi olarak XML belgesi başarıyla doğrulandı.</span><span class="sxs-lookup"><span data-stu-id="b2e48-136">The XML document is validated successfully as it is loaded without generating any schema validation errors or warnings.</span></span> <span data-ttu-id="b2e48-137">Örnek sonra göre geçersiz olan iki XML belgesi değişiklikleri yapar `contosoBooks.xsd` şema.</span><span class="sxs-lookup"><span data-stu-id="b2e48-137">The example then makes two modifications to the XML document that are invalid according to the `contosoBooks.xsd` schema.</span></span> <span data-ttu-id="b2e48-138">İlk değişikliği bir şeması doğrulama hatası kaynaklanan geçersiz bir alt öğesi ekler ve ikinci değişikliği bir özel durum kaynaklanan düğüm türüne göre geçersiz bir değere belirtilmiş bir düğüm değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b2e48-138">The first modification inserts an invalid child element resulting in a schema validation error, and the second modification sets the value of a typed node to a value that is invalid according to the type of the node resulting in an exception.</span></span>  
  
```vb  
Imports System  
Imports System.Xml  
Imports System.Xml.Schema  
Imports System.Xml.XPath  
  
Class ValidatingReaderExample  
  
    Shared Sub Main(ByVal args() As String)  
  
        Try  
            Dim settings As XmlReaderSettings = New XmlReaderSettings()  
            settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
            settings.ValidationType = ValidationType.Schema  
  
            Dim reader As XmlReader = XmlReader.Create("contosoBooks.xml", settings)  
  
            Dim document As XmlDocument = New XmlDocument()  
            document.Load(reader)  
            Dim navigator As XPathNavigator = document.CreateNavigator()  
  
            Dim validation As ValidationEventHandler = New ValidationEventHandler(AddressOf SchemaValidationHandler)  
  
            navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
            navigator.MoveToChild("book", "http://www.contoso.com/books")  
            navigator.MoveToChild("author", "http://www.contoso.com/books")  
  
            navigator.AppendChild("<title>Book Title</title>")  
  
            document.Validate(validation)  
  
            navigator.MoveToParent()  
            navigator.MoveToChild("price", "http://www.contoso.com/books")  
            navigator.SetTypedValue(DateTime.Now)  
        Catch e As Exception  
            Console.WriteLine("ValidatingReaderExample.Exception: {0}", e.Message)  
        End Try  
  
    End Sub  
  
    Shared Sub SchemaValidationHandler(ByVal sender As Object, ByVal e As ValidationEventArgs)  
  
        Select Case e.Severity  
            Case XmlSeverityType.Error  
                Console.WriteLine("Schema Validation Error: {0}", e.Message)  
                Exit Sub  
            Case XmlSeverityType.Warning  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message)  
                Exit Sub  
        End Select  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using System.Xml;  
using System.Xml.Schema;  
using System.Xml.XPath;  
  
class ValidatingReaderExample  
{  
    static void Main(string[] args)  
    {  
        try  
        {  
            XmlReaderSettings settings = new XmlReaderSettings();  
            settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
            settings.ValidationType = ValidationType.Schema;  
  
            XmlReader reader = XmlReader.Create("contosoBooks.xml", settings);  
  
            XmlDocument document = new XmlDocument();  
            document.Load(reader);  
            XPathNavigator navigator = document.CreateNavigator();  
  
            ValidationEventHandler validation = new ValidationEventHandler(SchemaValidationHandler);  
  
            navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
            navigator.MoveToChild("book", "http://www.contoso.com/books");  
            navigator.MoveToChild("author", "http://www.contoso.com/books");  
  
            navigator.AppendChild("<title>Book Title</title>");  
  
            document.Validate(validation);  
  
            navigator.MoveToParent();  
            navigator.MoveToChild("price", "http://www.contoso.com/books");  
            navigator.SetTypedValue(DateTime.Now);  
        }  
        catch (Exception e)  
        {  
            Console.WriteLine("ValidatingReaderExample.Exception: {0}", e.Message);  
        }  
    }  
  
    static void SchemaValidationHandler(object sender, ValidationEventArgs e)  
    {  
        switch (e.Severity)  
        {  
            case XmlSeverityType.Error:  
                Console.WriteLine("Schema Validation Error: {0}", e.Message);  
                break;  
            case XmlSeverityType.Warning:  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message);  
                break;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="b2e48-139">Örnek alır `contosoBooks.xml` dosyayı bir girdi olarak.</span><span class="sxs-lookup"><span data-stu-id="b2e48-139">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="b2e48-140">Bu örnek ayrıca alır `contosoBooks.xsd` bir girdi olarak.</span><span class="sxs-lookup"><span data-stu-id="b2e48-140">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 <span data-ttu-id="b2e48-141">Yukarıdaki örnekte, iki değişiklikler bulunan XML belgesi yapılan <xref:System.Xml.XmlDocument> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="b2e48-141">In the example above, two modifications are made to the XML document contained in the <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="b2e48-142">XML belgesi yüklendi olarak karşılaşılan şema doğrulama hataları alınan doğrulama olay işleyicisi yöntemi tarafından işlenen ve konsola yazılmış.</span><span class="sxs-lookup"><span data-stu-id="b2e48-142">As the XML document was loaded, any schema validation errors encountered would have been handled by the validation event handler method and written to the console.</span></span>  
  
 <span data-ttu-id="b2e48-143">Bu örnekte, XML belgesi yüklendi ve kullanarak bulundu sonra doğrulama hatalarını sunulan <xref:System.Xml.XmlDocument.Validate%2A> yöntemi <xref:System.Xml.XmlDocument> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b2e48-143">In this example, the validation errors were introduced after the XML document was loaded and were found using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="b2e48-144">Kullanılarak yapılan değişiklikler <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> yöntemi <xref:System.Xml.XPath.XPathNavigator> sınıfı sonuçlandı bir <xref:System.InvalidCastException> yeni değer göre düğümünün şema türü geçersiz olduğundan.</span><span class="sxs-lookup"><span data-stu-id="b2e48-144">Modifications made using the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class resulted in an <xref:System.InvalidCastException> because the new value was invalid according to the schema type of the node.</span></span>  
  
 <span data-ttu-id="b2e48-145">Kullanarak değerlerini değiştirme hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> yöntemi, bkz: [XML XPathNavigator kullanarak verileri değiştirme](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) konu.</span><span class="sxs-lookup"><span data-stu-id="b2e48-145">For more information about modifying values using the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method, see the [Modify XML Data using XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) topic.</span></span>  
  
### <a name="read-only-validation"></a><span data-ttu-id="b2e48-146">Salt okunur doğrulama</span><span class="sxs-lookup"><span data-stu-id="b2e48-146">Read-Only Validation</span></span>  
 <span data-ttu-id="b2e48-147"><xref:System.Xml.XPath.XPathDocument> Sınıfı, bir XML belgesi salt okunur, bellek içi bir gösterimi.</span><span class="sxs-lookup"><span data-stu-id="b2e48-147">The <xref:System.Xml.XPath.XPathDocument> class is a read-only, in-memory representation of an XML document.</span></span> <span data-ttu-id="b2e48-148">Her iki <xref:System.Xml.XPath.XPathDocument> sınıfı ve <xref:System.Xml.XmlDocument> sınıfı oluşturmak <xref:System.Xml.XPath.XPathNavigator> nesneleri sayfasına gidin ve XML belgelerini düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="b2e48-148">Both the <xref:System.Xml.XPath.XPathDocument> class and the <xref:System.Xml.XmlDocument> class create <xref:System.Xml.XPath.XPathNavigator> objects to navigate and edit XML documents.</span></span> <span data-ttu-id="b2e48-149">Çünkü <xref:System.Xml.XPath.XPathDocument> sınıftır bir salt okunur, <xref:System.Xml.XPath.XPathNavigator> nesnesi döndürülen <xref:System.Xml.XPath.XPathDocument> nesneleri bulunan XML belgesi düzenleme <xref:System.Xml.XPath.XPathDocument> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="b2e48-149">Because the <xref:System.Xml.XPath.XPathDocument> class is a read-only class, <xref:System.Xml.XPath.XPathNavigator> object's returned from <xref:System.Xml.XPath.XPathDocument> objects cannot edit the XML document contained in the <xref:System.Xml.XPath.XPathDocument> object.</span></span>  
  
 <span data-ttu-id="b2e48-150">Doğrulama söz konusu olduğunda, oluşturduğunuz bir <xref:System.Xml.XPath.XPathDocument> oluşturduğunuz gibi nesne bir <xref:System.Xml.XmlDocument> bir doğrulama kullanarak nesne <xref:System.Xml.XmlReader> nesne bu konunun önceki kısımlarında açıklandığı gibi.</span><span class="sxs-lookup"><span data-stu-id="b2e48-150">In the case of validation, you can create an <xref:System.Xml.XPath.XPathDocument> object just like you create an <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object as described earlier in this topic.</span></span> <span data-ttu-id="b2e48-151"><xref:System.Xml.XPath.XPathDocument> Nesneyi doğrular XML belgesi olarak yüklendiği ancak XML verilerinde düzenleyemediğiniz <xref:System.Xml.XPath.XPathDocument> nesnesi, XML belgesi düzeltin olamaz.</span><span class="sxs-lookup"><span data-stu-id="b2e48-151">The <xref:System.Xml.XPath.XPathDocument> object validates the XML document as it is loaded, but because you cannot edit the XML data in the <xref:System.Xml.XPath.XPathDocument> object, you cannot revalidate the XML document.</span></span>  
  
 <span data-ttu-id="b2e48-152">Salt okunur ve düzenlenebilir hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator> nesneleri bkz [XPathDocument ve XmlDocument kullanarak XML veri okunurken](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md) konu.</span><span class="sxs-lookup"><span data-stu-id="b2e48-152">For more information about read-only and editable <xref:System.Xml.XPath.XPathNavigator> objects, see the [Reading XML Data using XPathDocument and XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md) topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2e48-153">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b2e48-153">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="b2e48-154">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="b2e48-154">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="b2e48-155">XPathDocument ve XmlDocument Kullanarak XML Verilerini Okuma</span><span class="sxs-lookup"><span data-stu-id="b2e48-155">Reading XML Data using XPathDocument and XmlDocument</span></span>](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)  
 [<span data-ttu-id="b2e48-156">XPathNavigator Kullanarak XML Verileri Seçme, Değerlendirme ve Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="b2e48-156">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="b2e48-157">XPathNavigator Kullanarak XML Verilerine Erişme</span><span class="sxs-lookup"><span data-stu-id="b2e48-157">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="b2e48-158">XPathNavigator Kullanarak XML Verilerini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="b2e48-158">Editing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)
