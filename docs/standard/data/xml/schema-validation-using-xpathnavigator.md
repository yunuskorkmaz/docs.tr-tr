---
title: XPathNavigator kullanarak şema doğrulama
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 81fa0e41-d9c9-46f0-b22b-50da839c77f5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 335e6578767c130760f322aa2b015ea7b0f317f9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54557948"
---
# <a name="schema-validation-using-xpathnavigator"></a><span data-ttu-id="f7638-102">XPathNavigator kullanarak şema doğrulama</span><span class="sxs-lookup"><span data-stu-id="f7638-102">Schema Validation using XPathNavigator</span></span>
<span data-ttu-id="f7638-103">Kullanarak <xref:System.Xml.XmlDocument> sınıfı, içerdiği XML içeriği doğrulamak bir <xref:System.Xml.XmlDocument> iki yolla nesne.</span><span class="sxs-lookup"><span data-stu-id="f7638-103">Using the <xref:System.Xml.XmlDocument> class, you can validate the XML content contained in an <xref:System.Xml.XmlDocument> object in two ways.</span></span> <span data-ttu-id="f7638-104">Bir doğrulama kullanarak XML içeriği doğrulamak için ilk yoludur <xref:System.Xml.XmlReader> nesne ve ikinci yol ise <xref:System.Xml.XmlDocument.Validate%2A> yöntemi <xref:System.Xml.XmlDocument> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f7638-104">The first way is to validate the XML content using a validating <xref:System.Xml.XmlReader> object and the second way is to use the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="f7638-105">XML kullanarak içeriğin salt okunur doğrulama de gerçekleştirebilirsiniz <xref:System.Xml.XPath.XPathDocument> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f7638-105">You can also perform read-only validation of XML content using the <xref:System.Xml.XPath.XPathDocument> class.</span></span>  
  
## <a name="validating-xml-data"></a><span data-ttu-id="f7638-106">XML verileri doğrulama</span><span class="sxs-lookup"><span data-stu-id="f7638-106">Validating XML Data</span></span>  
 <span data-ttu-id="f7638-107"><xref:System.Xml.XmlDocument> Sınıfı, varsayılan olarak bir DTD'nin veya XML Şeması Tanım Dili (XSD) şeması doğrulama kullanarak bir XML belgesi doğrulamaz.</span><span class="sxs-lookup"><span data-stu-id="f7638-107">The <xref:System.Xml.XmlDocument> class does not validate an XML document using either DTD or XML schema definition language (XSD) schema validation by default.</span></span> <span data-ttu-id="f7638-108">Yalnızca XML belgesi biçimlendirilmemiş doğrular.</span><span class="sxs-lookup"><span data-stu-id="f7638-108">It only verifies that the XML document is well formed.</span></span>  
  
 <span data-ttu-id="f7638-109">Yüklenen olarak belgeyi doğrulamak için bir XML belgesi doğrulamak için ilk yol olduğu bir <xref:System.Xml.XmlDocument> bir doğrulama kullanarak nesne <xref:System.Xml.XmlReader> nesne.</span><span class="sxs-lookup"><span data-stu-id="f7638-109">The first way to validate an XML document is to validate the document as it is loaded into an <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="f7638-110">Daha önce yazılmamış bir XML belgesi kullanarak doğrulamak için ikinci yoludur <xref:System.Xml.XmlDocument.Validate%2A> yöntemi <xref:System.Xml.XmlDocument> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f7638-110">The second way is to validate a previously untyped XML document using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="f7638-111">Her iki durumda da doğrulanmış XML belgeye yapılan değişiklikler kullanarak yeniden doğrulanır <xref:System.Xml.XmlDocument.Validate%2A> yöntemi <xref:System.Xml.XmlDocument> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f7638-111">In both cases, changes to the validated XML document can be revalidated using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
### <a name="validating-a-document-as-it-is-loaded"></a><span data-ttu-id="f7638-112">Bir belge olarak doğrulama yüklendi</span><span class="sxs-lookup"><span data-stu-id="f7638-112">Validating a Document as it is Loaded</span></span>  
 <span data-ttu-id="f7638-113">Bir doğrulama <xref:System.Xml.XmlReader> nesnesi geçirerek oluşturulur bir <xref:System.Xml.XmlReaderSettings> nesnesini <xref:System.Xml.XmlReader.Create%2A> yöntemi <xref:System.Xml.XmlReader> alan sınıfı bir <xref:System.Xml.XmlReaderSettings> bir parametre olarak nesne.</span><span class="sxs-lookup"><span data-stu-id="f7638-113">A validating <xref:System.Xml.XmlReader> object is created by passing an <xref:System.Xml.XmlReaderSettings> object to the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class that takes an <xref:System.Xml.XmlReaderSettings> object as a parameter.</span></span> <span data-ttu-id="f7638-114"><xref:System.Xml.XmlReaderSettings> Nesnesi, bir parametre olarak geçirilen bir <xref:System.Xml.XmlReaderSettings.ValidationType%2A> özelliğini `Schema` ve yer alan XML belgesi için XML şeması bir <xref:System.Xml.XmlDocument> eklenen nesnenin kendi <xref:System.Xml.XmlReaderSettings.Schemas%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="f7638-114">The <xref:System.Xml.XmlReaderSettings> object passed as a parameter has a <xref:System.Xml.XmlReaderSettings.ValidationType%2A> property set to `Schema` and an XML Schema for the XML document contained in the <xref:System.Xml.XmlDocument> object added to its <xref:System.Xml.XmlReaderSettings.Schemas%2A> property.</span></span> <span data-ttu-id="f7638-115">Doğrulama <xref:System.Xml.XmlReader> nesne oluşturmak için kullanılan ardından <xref:System.Xml.XmlDocument> nesne.</span><span class="sxs-lookup"><span data-stu-id="f7638-115">The validating <xref:System.Xml.XmlReader> object is then used to create the <xref:System.Xml.XmlDocument> object.</span></span>  
  
 <span data-ttu-id="f7638-116">Aşağıdaki örnek doğrular `contosoBooks.xml` dosya içine yüklü <xref:System.Xml.XmlDocument> nesne oluşturarak <xref:System.Xml.XmlDocument> bir doğrulama kullanarak nesne <xref:System.Xml.XmlReader> nesne.</span><span class="sxs-lookup"><span data-stu-id="f7638-116">The following example validates the `contosoBooks.xml` file as it is loaded into the <xref:System.Xml.XmlDocument> object by creating the <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="f7638-117">XML belgesi şemasına göre geçerli olduğundan, hiçbir şema doğrulama hataları veya uyarıları üretilir.</span><span class="sxs-lookup"><span data-stu-id="f7638-117">Because the XML document is valid according to its schema, no schema validation errors or warnings are generated.</span></span>  
  
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
  
 <span data-ttu-id="f7638-118">Örnek alan `contosoBooks.xml` girdi olarak dosya.</span><span class="sxs-lookup"><span data-stu-id="f7638-118">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="f7638-119">Bu örnek ayrıca alır `contosoBooks.xsd` girdi olarak.</span><span class="sxs-lookup"><span data-stu-id="f7638-119">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 <span data-ttu-id="f7638-120">Yukarıdaki örnekte, bir <xref:System.Xml.Schema.XmlSchemaValidationException> ne zaman oluşturulur <xref:System.Xml.XmlDocument.Load%2A> herhangi bir öznitelik veya öğenin türü doğrulama şemasında belirtilen karşılık gelen türü eşleşmiyorsa çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f7638-120">In the above example, an <xref:System.Xml.Schema.XmlSchemaValidationException> will be thrown when <xref:System.Xml.XmlDocument.Load%2A> is called if any attribute or element type does not match the corresponding type specified in the validating schema.</span></span> <span data-ttu-id="f7638-121">Varsa bir <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> doğrulama ayarlanır <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> geçersiz bir türe karşılaşıldığında adlı.</span><span class="sxs-lookup"><span data-stu-id="f7638-121">If a <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> is set on the validating <xref:System.Xml.XmlReader>, the <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> will get called whenever an invalid type is encountered.</span></span>  
  
 <span data-ttu-id="f7638-122">Bir <xref:System.Xml.Schema.XmlSchemaException> bir öznitelik veya öğenin sahip olduğunda oluşturulur <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> kümesine `invalid` tarafından erişilen <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="f7638-122">An <xref:System.Xml.Schema.XmlSchemaException> will be thrown when an attribute or element with <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> set to `invalid` is accessed by the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
 <span data-ttu-id="f7638-123"><xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> Özelliği, bir tek öznitelik veya öğenin öznitelikleri veya öğelerin erişirken geçerli olup olmadığını belirlemek için kullanılabilir <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="f7638-123">The <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> property can be used to determine whether or not an individual attribute or element is valid when accessing attributes or elements with the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f7638-124">Ne zaman bir XML belgesi yüklendiği içine bir <xref:System.Xml.XmlDocument> varsayılan değerlerini tanımlayan ilişkili bir şeması ile nesne <xref:System.Xml.XmlDocument> nesne bu varsayılan XML belgesinde göründüğü gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="f7638-124">When an XML document is loaded into an <xref:System.Xml.XmlDocument> object with an associated schema that defines default values, the <xref:System.Xml.XmlDocument> object treats these defaults as if they appeared in the XML document.</span></span> <span data-ttu-id="f7638-125">Diğer bir deyişle <xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> özelliği her zaman döndürür `false` XML belgesinde boş bir öğe olarak yazılmış olsa bile şemadan varsayılan bir öğe için.</span><span class="sxs-lookup"><span data-stu-id="f7638-125">This means that the <xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> property  always returns `false` for an element that was defaulted from the schema, even if in the XML document it was written as an empty element.</span></span>  
  
### <a name="validating-a-document-using-the-validate-method"></a><span data-ttu-id="f7638-126">Doğrulama yöntemini kullanarak bir belge doğrulanıyor</span><span class="sxs-lookup"><span data-stu-id="f7638-126">Validating a Document using the Validate Method</span></span>  
 <span data-ttu-id="f7638-127"><xref:System.Xml.XmlDocument.Validate%2A> Yöntemi <xref:System.Xml.XmlDocument> sınıfı doğrular yer alan XML belgesi bir <xref:System.Xml.XmlDocument> nesne belirtilen şemaları karşı <xref:System.Xml.XmlDocument> nesnenin <xref:System.Xml.XmlDocument.Schemas%2A> özelliği ve sonrası bilgi kümesi güçlendirme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="f7638-127">The <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class validates the XML document contained in an <xref:System.Xml.XmlDocument> object against the schemas specified in the <xref:System.Xml.XmlDocument> object's <xref:System.Xml.XmlDocument.Schemas%2A> property and performs infoset augmentation.</span></span> <span data-ttu-id="f7638-128">Daha önce yazılmamış bir XML belgesinde sonucudur <xref:System.Xml.XmlDocument> nesne türü belirtilmiş bir belge ile değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="f7638-128">The result is a previously untyped XML document in the <xref:System.Xml.XmlDocument> object replaced with a typed document.</span></span>  
  
 <span data-ttu-id="f7638-129"><xref:System.Xml.XmlDocument> Nesnesi şema doğrulama hataları ve Uyarıları kullanarak raporları <xref:System.Xml.Schema.ValidationEventHandler> temsilci geçirilen bir parametre olarak <xref:System.Xml.XmlDocument.Validate%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f7638-129">The <xref:System.Xml.XmlDocument> object reports schema validation errors and warnings using the <xref:System.Xml.Schema.ValidationEventHandler> delegate passed as a parameter to the <xref:System.Xml.XmlDocument.Validate%2A> method.</span></span>  
  
 <span data-ttu-id="f7638-130">Aşağıdaki örnek doğrular `contosoBooks.xml` bulunan dosya <xref:System.Xml.XmlDocument> karşı nesne `contosoBooks.xsd` içindeki şeması <xref:System.Xml.XmlDocument> nesnenin <xref:System.Xml.XmlDocument.Schemas%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="f7638-130">The following example validates the `contosoBooks.xml` file contained in the <xref:System.Xml.XmlDocument> object against the `contosoBooks.xsd` schema contained in the <xref:System.Xml.XmlDocument> object's <xref:System.Xml.XmlDocument.Schemas%2A> property.</span></span>  
  
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
  
 <span data-ttu-id="f7638-131">Örnek alan `contosoBooks.xml` girdi olarak dosya.</span><span class="sxs-lookup"><span data-stu-id="f7638-131">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="f7638-132">Bu örnek ayrıca alır `contosoBooks.xsd` girdi olarak.</span><span class="sxs-lookup"><span data-stu-id="f7638-132">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
### <a name="validating-modifications"></a><span data-ttu-id="f7638-133">Değişiklikleri doğrulanıyor</span><span class="sxs-lookup"><span data-stu-id="f7638-133">Validating Modifications</span></span>  
 <span data-ttu-id="f7638-134">Bir XML belgesine değişiklikler yapıldıktan sonra değişikliklerin kullanarak XML belgesi için şemaya karşı doğrulayabilir <xref:System.Xml.XmlDocument.Validate%2A> yöntemi <xref:System.Xml.XmlDocument> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f7638-134">After modifications are made to an XML document, you can validate the modifications against the schema for the XML document using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="f7638-135">Aşağıdaki örnek doğrular `contosoBooks.xml` dosya içine yüklü <xref:System.Xml.XmlDocument> nesne oluşturarak <xref:System.Xml.XmlDocument> bir doğrulama kullanarak nesne <xref:System.Xml.XmlReader> nesne.</span><span class="sxs-lookup"><span data-stu-id="f7638-135">The following example validates the `contosoBooks.xml` file as it is loaded into the <xref:System.Xml.XmlDocument> object by creating the <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="f7638-136">XML belgesi yüklü herhangi bir şema doğrulama hataları veya uyarıları oluşturmadan başarıyla doğrulandı.</span><span class="sxs-lookup"><span data-stu-id="f7638-136">The XML document is validated successfully as it is loaded without generating any schema validation errors or warnings.</span></span> <span data-ttu-id="f7638-137">Örnek daha sonra göre geçersiz XML belgesi için iki değişiklik yapar `contosoBooks.xsd` şema.</span><span class="sxs-lookup"><span data-stu-id="f7638-137">The example then makes two modifications to the XML document that are invalid according to the `contosoBooks.xsd` schema.</span></span> <span data-ttu-id="f7638-138">İlk değişiklik bir şeması doğrulama hatası kaynaklanan geçersiz bir alt öğesi ekler ve ikinci değişiklik kaynaklanan bir özel durum düğüm türüne göre geçersiz bir değer türü belirtilmiş bir düğümün değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f7638-138">The first modification inserts an invalid child element resulting in a schema validation error, and the second modification sets the value of a typed node to a value that is invalid according to the type of the node resulting in an exception.</span></span>  
  
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
  
 <span data-ttu-id="f7638-139">Örnek alan `contosoBooks.xml` girdi olarak dosya.</span><span class="sxs-lookup"><span data-stu-id="f7638-139">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="f7638-140">Bu örnek ayrıca alır `contosoBooks.xsd` girdi olarak.</span><span class="sxs-lookup"><span data-stu-id="f7638-140">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 <span data-ttu-id="f7638-141">Yukarıdaki örnekte yer alan XML belgesi iki değişiklik yapılmadan <xref:System.Xml.XmlDocument> nesne.</span><span class="sxs-lookup"><span data-stu-id="f7638-141">In the example above, two modifications are made to the XML document contained in the <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="f7638-142">XML belgesi yüklendi olarak karşılaşılan şema doğrulama hataları alınan doğrulama olay işleyicisi yöntemi tarafından işlenen ve konsoluna yazılan.</span><span class="sxs-lookup"><span data-stu-id="f7638-142">As the XML document was loaded, any schema validation errors encountered would have been handled by the validation event handler method and written to the console.</span></span>  
  
 <span data-ttu-id="f7638-143">Bu örnekte, XML belgesi yüklendi ve kullanılarak bulunan sonra doğrulama hatalarını tanıtılan <xref:System.Xml.XmlDocument.Validate%2A> yöntemi <xref:System.Xml.XmlDocument> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f7638-143">In this example, the validation errors were introduced after the XML document was loaded and were found using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="f7638-144">Kullanarak yapılan değişiklikleri <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> yöntemi <xref:System.Xml.XPath.XPathNavigator> sınıfı sonuçlandı bir <xref:System.InvalidCastException> yeni değeri düğümün şema türüne göre geçersiz olduğundan.</span><span class="sxs-lookup"><span data-stu-id="f7638-144">Modifications made using the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class resulted in an <xref:System.InvalidCastException> because the new value was invalid according to the schema type of the node.</span></span>  
  
 <span data-ttu-id="f7638-145">Kullanarak değerleri değiştirme hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> yöntemi bkz [değiştirme XPathNavigator kullanarak XML verilerini](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) konu.</span><span class="sxs-lookup"><span data-stu-id="f7638-145">For more information about modifying values using the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method, see the [Modify XML Data using XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) topic.</span></span>  
  
### <a name="read-only-validation"></a><span data-ttu-id="f7638-146">Salt okunur doğrulama</span><span class="sxs-lookup"><span data-stu-id="f7638-146">Read-Only Validation</span></span>  
 <span data-ttu-id="f7638-147"><xref:System.Xml.XPath.XPathDocument> Sınıfı, bir XML belgesi salt okunur, bellek içi bir temsili.</span><span class="sxs-lookup"><span data-stu-id="f7638-147">The <xref:System.Xml.XPath.XPathDocument> class is a read-only, in-memory representation of an XML document.</span></span> <span data-ttu-id="f7638-148">Her iki <xref:System.Xml.XPath.XPathDocument> sınıfı ve <xref:System.Xml.XmlDocument> sınıfı oluşturma <xref:System.Xml.XPath.XPathNavigator> gidin ve XML belge düzenleme nesneleri.</span><span class="sxs-lookup"><span data-stu-id="f7638-148">Both the <xref:System.Xml.XPath.XPathDocument> class and the <xref:System.Xml.XmlDocument> class create <xref:System.Xml.XPath.XPathNavigator> objects to navigate and edit XML documents.</span></span> <span data-ttu-id="f7638-149">Çünkü <xref:System.Xml.XPath.XPathDocument> salt okunur sınıfı <xref:System.Xml.XPath.XPathNavigator> nesnesi döndürülen <xref:System.Xml.XPath.XPathDocument> nesneleri yer alan XML belgesi düzenlemek <xref:System.Xml.XPath.XPathDocument> nesne.</span><span class="sxs-lookup"><span data-stu-id="f7638-149">Because the <xref:System.Xml.XPath.XPathDocument> class is a read-only class, <xref:System.Xml.XPath.XPathNavigator> object's returned from <xref:System.Xml.XPath.XPathDocument> objects cannot edit the XML document contained in the <xref:System.Xml.XPath.XPathDocument> object.</span></span>  
  
 <span data-ttu-id="f7638-150">Doğrulama söz konusu olduğunda, oluşturduğunuz bir <xref:System.Xml.XPath.XPathDocument> oluşturduğunuz gibi nesne bir <xref:System.Xml.XmlDocument> bir doğrulama kullanarak nesne <xref:System.Xml.XmlReader> nesne bu konunun önceki kısımlarında açıklandığı gibi.</span><span class="sxs-lookup"><span data-stu-id="f7638-150">In the case of validation, you can create an <xref:System.Xml.XPath.XPathDocument> object just like you create an <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object as described earlier in this topic.</span></span> <span data-ttu-id="f7638-151"><xref:System.Xml.XPath.XPathDocument> Nesneyi doğrular XML belgesi yüklü olduğu gibi ancak XML verilerinde düzenleyemediğiniz <xref:System.Xml.XPath.XPathDocument> nesnesi, XML belgesi düzeltin olamaz.</span><span class="sxs-lookup"><span data-stu-id="f7638-151">The <xref:System.Xml.XPath.XPathDocument> object validates the XML document as it is loaded, but because you cannot edit the XML data in the <xref:System.Xml.XPath.XPathDocument> object, you cannot revalidate the XML document.</span></span>  
  
 <span data-ttu-id="f7638-152">Salt okunur ve düzenlenebilir hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator> nesneleri bkz [XPathDocument ve XmlDocument kullanarak XML verileri okuma](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md) konu.</span><span class="sxs-lookup"><span data-stu-id="f7638-152">For more information about read-only and editable <xref:System.Xml.XPath.XPathNavigator> objects, see the [Reading XML Data using XPathDocument and XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md) topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7638-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7638-153">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="f7638-154">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="f7638-154">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="f7638-155">XPathDocument ve XmlDocument Kullanarak XML Verilerini Okuma</span><span class="sxs-lookup"><span data-stu-id="f7638-155">Reading XML Data using XPathDocument and XmlDocument</span></span>](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)
- [<span data-ttu-id="f7638-156">XPathNavigator Kullanarak XML Verileri Seçme, Değerlendirme ve Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="f7638-156">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="f7638-157">XPathNavigator Kullanarak XML Verilerine Erişme</span><span class="sxs-lookup"><span data-stu-id="f7638-157">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="f7638-158">XPathNavigator Kullanarak XML Verilerini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="f7638-158">Editing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)
