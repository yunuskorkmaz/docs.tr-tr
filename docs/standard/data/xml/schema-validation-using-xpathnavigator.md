---
title: XPathNavigator Kullanarak Şema Doğrulama
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 81fa0e41-d9c9-46f0-b22b-50da839c77f5
ms.openlocfilehash: bfcbf7306e896af54808c49e25f95d0631f5bcc0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710212"
---
# <a name="schema-validation-using-xpathnavigator"></a><span data-ttu-id="d6d07-102">XPathNavigator Kullanarak Şema Doğrulama</span><span class="sxs-lookup"><span data-stu-id="d6d07-102">Schema Validation using XPathNavigator</span></span>
<span data-ttu-id="d6d07-103"><xref:System.Xml.XmlDocument> Sınıfını kullanarak bir <xref:System.Xml.XmlDocument> nesnede bulunan XML içeriğini iki şekilde doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d6d07-103">Using the <xref:System.Xml.XmlDocument> class, you can validate the XML content contained in an <xref:System.Xml.XmlDocument> object in two ways.</span></span> <span data-ttu-id="d6d07-104">İlk yöntem, Validating <xref:System.Xml.XmlReader> NESNESINI kullanarak XML içeriğini doğrulamak ve ikinci yöntem ise <xref:System.Xml.XmlDocument.Validate%2A> <xref:System.Xml.XmlDocument> sınıfının yöntemini kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="d6d07-104">The first way is to validate the XML content using a validating <xref:System.Xml.XmlReader> object and the second way is to use the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="d6d07-105">Ayrıca, <xref:System.Xml.XPath.XPathDocument> SıNıFıNı kullanarak XML içeriğinin salt okunurdur doğrulamasını gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d6d07-105">You can also perform read-only validation of XML content using the <xref:System.Xml.XPath.XPathDocument> class.</span></span>  
  
## <a name="validating-xml-data"></a><span data-ttu-id="d6d07-106">XML verileri doğrulanıyor</span><span class="sxs-lookup"><span data-stu-id="d6d07-106">Validating XML Data</span></span>  
 <span data-ttu-id="d6d07-107">Sınıf <xref:System.Xml.XmlDocument> , varsayılan olarak DTD veya XML şeması tanım DILI (xsd) şema doğrulamasını kullanarak bir XML belgesini doğrulamaz.</span><span class="sxs-lookup"><span data-stu-id="d6d07-107">The <xref:System.Xml.XmlDocument> class does not validate an XML document using either DTD or XML schema definition language (XSD) schema validation by default.</span></span> <span data-ttu-id="d6d07-108">Yalnızca XML belgesinin düzgün biçimlendirildiğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="d6d07-108">It only verifies that the XML document is well formed.</span></span>  
  
 <span data-ttu-id="d6d07-109">Bir XML belgesini doğrulamaya yönelik ilk yol, doğrulama <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlReader> nesnesi kullanılarak bir nesneye yüklendiğinde belgeyi doğrulamaktır.</span><span class="sxs-lookup"><span data-stu-id="d6d07-109">The first way to validate an XML document is to validate the document as it is loaded into an <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="d6d07-110">İkinci yol, <xref:System.Xml.XmlDocument.Validate%2A> <xref:System.Xml.XmlDocument> sınıfının yöntemini kullanarak daha önce türsüz bir XML belgesini doğrulamaktır.</span><span class="sxs-lookup"><span data-stu-id="d6d07-110">The second way is to validate a previously untyped XML document using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="d6d07-111">Her iki durumda da, doğrulanan XML belgesinde yapılan değişiklikler, <xref:System.Xml.XmlDocument.Validate%2A> <xref:System.Xml.XmlDocument> sınıfının yöntemi kullanılarak yeniden doğrulanabilir.</span><span class="sxs-lookup"><span data-stu-id="d6d07-111">In both cases, changes to the validated XML document can be revalidated using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
### <a name="validating-a-document-as-it-is-loaded"></a><span data-ttu-id="d6d07-112">Belge yüklendiği için doğrulanıyor</span><span class="sxs-lookup"><span data-stu-id="d6d07-112">Validating a Document as it is Loaded</span></span>  
 <span data-ttu-id="d6d07-113">Bir nesne <xref:System.Xml.XmlReader> , bir nesneyi parametre olarak alan <xref:System.Xml.XmlReaderSettings> <xref:System.Xml.XmlReader.Create%2A> <xref:System.Xml.XmlReader> <xref:System.Xml.XmlReaderSettings> sınıfın yöntemine geçirerek bir doğrulama nesnesi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d6d07-113">A validating <xref:System.Xml.XmlReader> object is created by passing an <xref:System.Xml.XmlReaderSettings> object to the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class that takes an <xref:System.Xml.XmlReaderSettings> object as a parameter.</span></span> <span data-ttu-id="d6d07-114">Parametre <xref:System.Xml.XmlReaderSettings> olarak geçirilen <xref:System.Xml.XmlReaderSettings.ValidationType%2A> nesne, `Schema` <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlReaderSettings.Schemas%2A> özelliğine ayarlanmış bir ÖZELLIĞI ve özelliğine eklenen nesne içindeki XML belgesi için bir XML şeması içerir.</span><span class="sxs-lookup"><span data-stu-id="d6d07-114">The <xref:System.Xml.XmlReaderSettings> object passed as a parameter has a <xref:System.Xml.XmlReaderSettings.ValidationType%2A> property set to `Schema` and an XML Schema for the XML document contained in the <xref:System.Xml.XmlDocument> object added to its <xref:System.Xml.XmlReaderSettings.Schemas%2A> property.</span></span> <span data-ttu-id="d6d07-115">Doğrulama <xref:System.Xml.XmlReader> nesnesi daha sonra <xref:System.Xml.XmlDocument> nesneyi oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d6d07-115">The validating <xref:System.Xml.XmlReader> object is then used to create the <xref:System.Xml.XmlDocument> object.</span></span>  
  
 <span data-ttu-id="d6d07-116">Aşağıdaki örnek, bir doğrulama `contosoBooks.xml` <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlReader> nesnesi kullanılarak nesnesini oluşturarak dosyayı <xref:System.Xml.XmlDocument> nesnesine yüklendiği şekilde doğrular.</span><span class="sxs-lookup"><span data-stu-id="d6d07-116">The following example validates the `contosoBooks.xml` file as it is loaded into the <xref:System.Xml.XmlDocument> object by creating the <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="d6d07-117">XML belgesi şemasına göre geçerli olduğundan, şema doğrulama hataları veya uyarılar oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="d6d07-117">Because the XML document is valid according to its schema, no schema validation errors or warnings are generated.</span></span>  
  
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
  
 <span data-ttu-id="d6d07-118">Örnek, `contosoBooks.xml` dosyayı bir giriş olarak alır.</span><span class="sxs-lookup"><span data-stu-id="d6d07-118">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="d6d07-119">Örnek de bir giriş `contosoBooks.xsd` olarak alır.</span><span class="sxs-lookup"><span data-stu-id="d6d07-119">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 <span data-ttu-id="d6d07-120">Yukarıdaki örnekte, bir öznitelik veya <xref:System.Xml.Schema.XmlSchemaValidationException> öğe türü, doğrulama <xref:System.Xml.XmlDocument.Load%2A> şemasında belirtilen ilgili türle eşleşmezse, çağrıldığında bir oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d6d07-120">In the above example, an <xref:System.Xml.Schema.XmlSchemaValidationException> will be thrown when <xref:System.Xml.XmlDocument.Load%2A> is called if any attribute or element type does not match the corresponding type specified in the validating schema.</span></span> <span data-ttu-id="d6d07-121"><xref:System.Xml.XmlReaderSettings.ValidationEventHandler> <xref:System.Xml.XmlReader>Doğrulama <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> üzerinde ayarlandıysa, geçersiz bir tür ile karşılaşıldığında çağrılır.</span><span class="sxs-lookup"><span data-stu-id="d6d07-121">If a <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> is set on the validating <xref:System.Xml.XmlReader>, the <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> will get called whenever an invalid type is encountered.</span></span>  
  
 <span data-ttu-id="d6d07-122">Öğesi <xref:System.Xml.Schema.XmlSchemaException> tarafından olarak <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> ayarlanmış `invalid` bir özniteliğe veya öğeye erişildiğinde bir oluşturulur. <xref:System.Xml.XPath.XPathNavigator></span><span class="sxs-lookup"><span data-stu-id="d6d07-122">An <xref:System.Xml.Schema.XmlSchemaException> will be thrown when an attribute or element with <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> set to `invalid` is accessed by the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
 <span data-ttu-id="d6d07-123"><xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> Özelliği, <xref:System.Xml.XPath.XPathNavigator>özniteliği veya öğelerine öğesine erişirken bağımsız bir özniteliğin veya öğenin geçerli olup olmadığını anlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d6d07-123">The <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> property can be used to determine whether or not an individual attribute or element is valid when accessing attributes or elements with the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d6d07-124">Bir XML belgesi, varsayılan değerleri tanımlayan ilişkili <xref:System.Xml.XmlDocument> bir şemaya sahip bir nesneye yüklendiğinde, <xref:System.Xml.XmlDocument> nesne bu varsayılanlara XML belgesinde görünmiş gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="d6d07-124">When an XML document is loaded into an <xref:System.Xml.XmlDocument> object with an associated schema that defines default values, the <xref:System.Xml.XmlDocument> object treats these defaults as if they appeared in the XML document.</span></span> <span data-ttu-id="d6d07-125">Bu, <xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> özelliğin, boş bir öğe `false` olarak yazılmış XML belgesinde olsa bile, her zaman şemanın varsayılan olarak ayarlanmış bir öğe için döndüğü anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d6d07-125">This means that the <xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> property  always returns `false` for an element that was defaulted from the schema, even if in the XML document it was written as an empty element.</span></span>  
  
### <a name="validating-a-document-using-the-validate-method"></a><span data-ttu-id="d6d07-126">Validate metodunu kullanarak bir belgeyi doğrulama</span><span class="sxs-lookup"><span data-stu-id="d6d07-126">Validating a Document using the Validate Method</span></span>  
 <span data-ttu-id="d6d07-127"><xref:System.Xml.XmlDocument> Sınıfının <xref:System.Xml.XmlDocument.Validate%2A> yöntemi, nesne <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlDocument.Schemas%2A> özelliğinde belirtilen şemalara karşı bir nesnede bulunan XML belgesini doğrular ve bilgi kümesi genişletmesini gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="d6d07-127">The <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class validates the XML document contained in an <xref:System.Xml.XmlDocument> object against the schemas specified in the <xref:System.Xml.XmlDocument> object's <xref:System.Xml.XmlDocument.Schemas%2A> property and performs infoset augmentation.</span></span> <span data-ttu-id="d6d07-128">Sonuç olarak, <xref:System.Xml.XmlDocument> nesnede türü belirtilmiş bir belge ile değiştirilmiş olan, daha önce TÜRSÜZ bir XML belgesidir.</span><span class="sxs-lookup"><span data-stu-id="d6d07-128">The result is a previously untyped XML document in the <xref:System.Xml.XmlDocument> object replaced with a typed document.</span></span>  
  
 <span data-ttu-id="d6d07-129"><xref:System.Xml.XmlDocument> Nesnesi, <xref:System.Xml.Schema.ValidationEventHandler> <xref:System.Xml.XmlDocument.Validate%2A> yöntemine parametre olarak geçirilen temsilciyi kullanarak şema doğrulama hatalarını ve uyarılarını raporlar.</span><span class="sxs-lookup"><span data-stu-id="d6d07-129">The <xref:System.Xml.XmlDocument> object reports schema validation errors and warnings using the <xref:System.Xml.Schema.ValidationEventHandler> delegate passed as a parameter to the <xref:System.Xml.XmlDocument.Validate%2A> method.</span></span>  
  
 <span data-ttu-id="d6d07-130">Aşağıdaki örnek, nesnesinde bulunan `contosoBooks.xml` <xref:System.Xml.XmlDocument> dosyayı `contosoBooks.xsd` <xref:System.Xml.XmlDocument> nesnenin <xref:System.Xml.XmlDocument.Schemas%2A> özelliğinde bulunan şemaya karşı doğrular.</span><span class="sxs-lookup"><span data-stu-id="d6d07-130">The following example validates the `contosoBooks.xml` file contained in the <xref:System.Xml.XmlDocument> object against the `contosoBooks.xsd` schema contained in the <xref:System.Xml.XmlDocument> object's <xref:System.Xml.XmlDocument.Schemas%2A> property.</span></span>  
  
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
  
 <span data-ttu-id="d6d07-131">Örnek, `contosoBooks.xml` dosyayı bir giriş olarak alır.</span><span class="sxs-lookup"><span data-stu-id="d6d07-131">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="d6d07-132">Örnek de bir giriş `contosoBooks.xsd` olarak alır.</span><span class="sxs-lookup"><span data-stu-id="d6d07-132">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
### <a name="validating-modifications"></a><span data-ttu-id="d6d07-133">Değişiklikler doğrulanıyor</span><span class="sxs-lookup"><span data-stu-id="d6d07-133">Validating Modifications</span></span>  
 <span data-ttu-id="d6d07-134">Bir XML belgesinde değişiklikler yapıldıktan sonra, <xref:System.Xml.XmlDocument.Validate%2A> <xref:System.Xml.XmlDocument> sınıfının metodunu kullanarak XML belgesi şemasına karşı değişiklikleri doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d6d07-134">After modifications are made to an XML document, you can validate the modifications against the schema for the XML document using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="d6d07-135">Aşağıdaki örnek, bir doğrulama `contosoBooks.xml` <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlReader> nesnesi kullanılarak nesnesini oluşturarak dosyayı <xref:System.Xml.XmlDocument> nesnesine yüklendiği şekilde doğrular.</span><span class="sxs-lookup"><span data-stu-id="d6d07-135">The following example validates the `contosoBooks.xml` file as it is loaded into the <xref:System.Xml.XmlDocument> object by creating the <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="d6d07-136">XML belgesi, şema doğrulama hataları veya uyarılar üretilmeden yüklendiğinden başarıyla doğrulanacaktır.</span><span class="sxs-lookup"><span data-stu-id="d6d07-136">The XML document is validated successfully as it is loaded without generating any schema validation errors or warnings.</span></span> <span data-ttu-id="d6d07-137">Örnek daha sonra `contosoBooks.xsd` şemaya göre GEÇERSIZ olan XML belgesinde iki değişiklik yapar.</span><span class="sxs-lookup"><span data-stu-id="d6d07-137">The example then makes two modifications to the XML document that are invalid according to the `contosoBooks.xsd` schema.</span></span> <span data-ttu-id="d6d07-138">İlk değişiklik, bir şema doğrulama hatasına neden olan geçersiz bir alt öğe ekliyor ve ikinci değişiklik, bir özel duruma neden olan düğümün türüne göre geçersiz bir değere sahip bir değer olarak belirlenmiş bir değerin değerini ayarlıyor.</span><span class="sxs-lookup"><span data-stu-id="d6d07-138">The first modification inserts an invalid child element resulting in a schema validation error, and the second modification sets the value of a typed node to a value that is invalid according to the type of the node resulting in an exception.</span></span>  
  
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
  
 <span data-ttu-id="d6d07-139">Örnek, `contosoBooks.xml` dosyayı bir giriş olarak alır.</span><span class="sxs-lookup"><span data-stu-id="d6d07-139">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="d6d07-140">Örnek de bir giriş `contosoBooks.xsd` olarak alır.</span><span class="sxs-lookup"><span data-stu-id="d6d07-140">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 <span data-ttu-id="d6d07-141">Yukarıdaki örnekte, <xref:System.Xml.XmlDocument> NESNESINDE bulunan XML belgesinde iki değişiklik yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="d6d07-141">In the example above, two modifications are made to the XML document contained in the <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="d6d07-142">XML belgesi yüklendiğinde, karşılaşılan tüm şema doğrulama hataları doğrulama olay işleyicisi yöntemi tarafından işlenirdi ve konsola yazılır.</span><span class="sxs-lookup"><span data-stu-id="d6d07-142">As the XML document was loaded, any schema validation errors encountered would have been handled by the validation event handler method and written to the console.</span></span>  
  
 <span data-ttu-id="d6d07-143">Bu örnekte, doğrulama hataları XML belgesi yüklendikten sonra ve <xref:System.Xml.XmlDocument.Validate%2A> <xref:System.Xml.XmlDocument> sınıfının yöntemi kullanılarak bulunduktan sonra tanıtılmıştı.</span><span class="sxs-lookup"><span data-stu-id="d6d07-143">In this example, the validation errors were introduced after the XML document was loaded and were found using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="d6d07-144">Sınıfının yöntemi kullanılarak yapılan değişiklikler, düğümün şema türüne göre yeni <xref:System.InvalidCastException> değer geçersiz olduğu için bir ile sonuçlandı. <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> <xref:System.Xml.XPath.XPathNavigator></span><span class="sxs-lookup"><span data-stu-id="d6d07-144">Modifications made using the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class resulted in an <xref:System.InvalidCastException> because the new value was invalid according to the schema type of the node.</span></span>  
  
 <span data-ttu-id="d6d07-145"><xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> Yöntemi kullanarak değerleri değiştirme hakkında daha fazla bilgi için bkz. [XML verilerini XPathNavigator ile değiştirme](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) konusu.</span><span class="sxs-lookup"><span data-stu-id="d6d07-145">For more information about modifying values using the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method, see the [Modify XML Data using XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) topic.</span></span>  
  
### <a name="read-only-validation"></a><span data-ttu-id="d6d07-146">Salt okuma doğrulaması</span><span class="sxs-lookup"><span data-stu-id="d6d07-146">Read-Only Validation</span></span>  
 <span data-ttu-id="d6d07-147"><xref:System.Xml.XPath.XPathDocument> Sınıfı, bir XML belgesinin Salt okunabilir, bellek içi gösterimidir.</span><span class="sxs-lookup"><span data-stu-id="d6d07-147">The <xref:System.Xml.XPath.XPathDocument> class is a read-only, in-memory representation of an XML document.</span></span> <span data-ttu-id="d6d07-148">Hem <xref:System.Xml.XPath.XPathDocument> sınıf hem de <xref:System.Xml.XmlDocument> sınıf, XML <xref:System.Xml.XPath.XPathNavigator> belgelerini gezinmek ve düzenlemek için nesneler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d6d07-148">Both the <xref:System.Xml.XPath.XPathDocument> class and the <xref:System.Xml.XmlDocument> class create <xref:System.Xml.XPath.XPathNavigator> objects to navigate and edit XML documents.</span></span> <span data-ttu-id="d6d07-149"><xref:System.Xml.XPath.XPathDocument> Sınıfı salt bir salt okunurdur, <xref:System.Xml.XPath.XPathNavigator> nesne nesnesinden döndürülen <xref:System.Xml.XPath.XPathDocument> nesneler, <xref:System.Xml.XPath.XPathDocument> nesnede bulunan XML belgesini düzenleyemez.</span><span class="sxs-lookup"><span data-stu-id="d6d07-149">Because the <xref:System.Xml.XPath.XPathDocument> class is a read-only class, <xref:System.Xml.XPath.XPathNavigator> object's returned from <xref:System.Xml.XPath.XPathDocument> objects cannot edit the XML document contained in the <xref:System.Xml.XPath.XPathDocument> object.</span></span>  
  
 <span data-ttu-id="d6d07-150">Doğrulama durumunda, bu konuda daha önce açıklandığı gibi doğrulama <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlReader> nesnesini kullanarak bir nesne oluşturduğunuz gibi <xref:System.Xml.XmlDocument> bir nesne oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d6d07-150">In the case of validation, you can create an <xref:System.Xml.XPath.XPathDocument> object just like you create an <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object as described earlier in this topic.</span></span> <span data-ttu-id="d6d07-151"><xref:System.Xml.XPath.XPathDocument> Nesne, YÜKLENDIĞI gibi XML belgesini doğrular, ancak <xref:System.Xml.XPath.XPathDocument> nesne içindeki XML verilerini düzenleyemediğinden XML belgesini yeniden doğrulayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="d6d07-151">The <xref:System.Xml.XPath.XPathDocument> object validates the XML document as it is loaded, but because you cannot edit the XML data in the <xref:System.Xml.XPath.XPathDocument> object, you cannot revalidate the XML document.</span></span>  
  
 <span data-ttu-id="d6d07-152">Salt okunurdur ve düzenlenebilir <xref:System.Xml.XPath.XPathNavigator> nesneler hakkında daha fazla bilgi Için, [XPathDocument ve XmlDocument kullanarak XML verilerini okuma](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md) konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="d6d07-152">For more information about read-only and editable <xref:System.Xml.XPath.XPathNavigator> objects, see the [Reading XML Data using XPathDocument and XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md) topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6d07-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d6d07-153">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="d6d07-154">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="d6d07-154">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="d6d07-155">XPathDocument ve XmlDocument Kullanarak XML Verilerini Okuma</span><span class="sxs-lookup"><span data-stu-id="d6d07-155">Reading XML Data using XPathDocument and XmlDocument</span></span>](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)
- [<span data-ttu-id="d6d07-156">XPathNavigator Kullanarak XML Verileri Seçme, Değerlendirme ve Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="d6d07-156">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="d6d07-157">XPathNavigator Kullanarak XML Verilerine Erişme</span><span class="sxs-lookup"><span data-stu-id="d6d07-157">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="d6d07-158">XPathNavigator Kullanarak XML Verilerini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="d6d07-158">Editing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)
