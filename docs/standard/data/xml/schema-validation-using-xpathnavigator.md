---
description: 'Daha fazla bilgi edinin: XPathNavigator kullanarak şema doğrulama'
title: XPathNavigator Kullanarak Şema Doğrulama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 81fa0e41-d9c9-46f0-b22b-50da839c77f5
ms.openlocfilehash: 69b57aa4f2efc08ba196e0abe1f4d8a0b91887db
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782994"
---
# <a name="schema-validation-using-xpathnavigator"></a><span data-ttu-id="2c1e7-103">XPathNavigator Kullanarak Şema Doğrulama</span><span class="sxs-lookup"><span data-stu-id="2c1e7-103">Schema Validation using XPathNavigator</span></span>

<span data-ttu-id="2c1e7-104">Sınıfını kullanarak <xref:System.Xml.XmlDocument> bir nesnede bulunan XML içeriğini <xref:System.Xml.XmlDocument> iki şekilde doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2c1e7-104">Using the <xref:System.Xml.XmlDocument> class, you can validate the XML content contained in an <xref:System.Xml.XmlDocument> object in two ways.</span></span> <span data-ttu-id="2c1e7-105">İlk yöntem, Validating nesnesini kullanarak XML içeriğini doğrulamak <xref:System.Xml.XmlReader> ve ikinci yöntem ise <xref:System.Xml.XmlDocument.Validate%2A> sınıfının yöntemini kullanmaktır <xref:System.Xml.XmlDocument> .</span><span class="sxs-lookup"><span data-stu-id="2c1e7-105">The first way is to validate the XML content using a validating <xref:System.Xml.XmlReader> object and the second way is to use the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="2c1e7-106">Ayrıca, sınıfını kullanarak XML içeriğinin salt okunurdur doğrulamasını gerçekleştirebilirsiniz <xref:System.Xml.XPath.XPathDocument> .</span><span class="sxs-lookup"><span data-stu-id="2c1e7-106">You can also perform read-only validation of XML content using the <xref:System.Xml.XPath.XPathDocument> class.</span></span>  
  
## <a name="validating-xml-data"></a><span data-ttu-id="2c1e7-107">XML verileri doğrulanıyor</span><span class="sxs-lookup"><span data-stu-id="2c1e7-107">Validating XML Data</span></span>  

 <span data-ttu-id="2c1e7-108"><xref:System.Xml.XmlDocument>Sınıf, varsayılan olarak DTD veya XML şeması tanım dili (xsd) şema doğrulamasını kullanarak BIR XML belgesini doğrulamaz.</span><span class="sxs-lookup"><span data-stu-id="2c1e7-108">The <xref:System.Xml.XmlDocument> class does not validate an XML document using either DTD or XML schema definition language (XSD) schema validation by default.</span></span> <span data-ttu-id="2c1e7-109">Yalnızca XML belgesinin düzgün biçimlendirildiğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="2c1e7-109">It only verifies that the XML document is well formed.</span></span>  
  
 <span data-ttu-id="2c1e7-110">Bir XML belgesini doğrulamaya yönelik ilk yol, doğrulama nesnesi kullanılarak bir nesneye yüklendiğinde belgeyi doğrulamaktır <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="2c1e7-110">The first way to validate an XML document is to validate the document as it is loaded into an <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="2c1e7-111">İkinci yol, sınıfının yöntemini kullanarak daha önce türsüz bir XML belgesini doğrulamaktır <xref:System.Xml.XmlDocument.Validate%2A> <xref:System.Xml.XmlDocument> .</span><span class="sxs-lookup"><span data-stu-id="2c1e7-111">The second way is to validate a previously untyped XML document using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="2c1e7-112">Her iki durumda da, doğrulanan XML belgesinde yapılan değişiklikler, sınıfının yöntemi kullanılarak yeniden doğrulanabilir <xref:System.Xml.XmlDocument.Validate%2A> <xref:System.Xml.XmlDocument> .</span><span class="sxs-lookup"><span data-stu-id="2c1e7-112">In both cases, changes to the validated XML document can be revalidated using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
### <a name="validating-a-document-as-it-is-loaded"></a><span data-ttu-id="2c1e7-113">Belge yüklendiği için doğrulanıyor</span><span class="sxs-lookup"><span data-stu-id="2c1e7-113">Validating a Document as it is Loaded</span></span>  

 <span data-ttu-id="2c1e7-114">Bir nesne, bir nesneyi <xref:System.Xml.XmlReader> <xref:System.Xml.XmlReaderSettings> <xref:System.Xml.XmlReader.Create%2A> <xref:System.Xml.XmlReader> parametre olarak alan sınıfın yöntemine geçirerek bir doğrulama nesnesi oluşturulur <xref:System.Xml.XmlReaderSettings> .</span><span class="sxs-lookup"><span data-stu-id="2c1e7-114">A validating <xref:System.Xml.XmlReader> object is created by passing an <xref:System.Xml.XmlReaderSettings> object to the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class that takes an <xref:System.Xml.XmlReaderSettings> object as a parameter.</span></span> <span data-ttu-id="2c1e7-115"><xref:System.Xml.XmlReaderSettings>Parametre olarak geçirilen nesne, <xref:System.Xml.XmlReaderSettings.ValidationType%2A> özelliğine ayarlanmış bir özelliği `Schema` ve <xref:System.Xml.XmlDocument> ÖZELLIĞINE eklenen nesne içindeki XML belgesi için bir XML şeması içerir <xref:System.Xml.XmlReaderSettings.Schemas%2A> .</span><span class="sxs-lookup"><span data-stu-id="2c1e7-115">The <xref:System.Xml.XmlReaderSettings> object passed as a parameter has a <xref:System.Xml.XmlReaderSettings.ValidationType%2A> property set to `Schema` and an XML Schema for the XML document contained in the <xref:System.Xml.XmlDocument> object added to its <xref:System.Xml.XmlReaderSettings.Schemas%2A> property.</span></span> <span data-ttu-id="2c1e7-116">Doğrulama <xref:System.Xml.XmlReader> nesnesi daha sonra nesneyi oluşturmak için kullanılır <xref:System.Xml.XmlDocument> .</span><span class="sxs-lookup"><span data-stu-id="2c1e7-116">The validating <xref:System.Xml.XmlReader> object is then used to create the <xref:System.Xml.XmlDocument> object.</span></span>  
  
 <span data-ttu-id="2c1e7-117">Aşağıdaki örnek, `contosoBooks.xml` <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlDocument> bir doğrulama nesnesi kullanılarak nesnesini oluşturarak dosyayı nesnesine yüklendiği şekilde doğrular <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="2c1e7-117">The following example validates the `contosoBooks.xml` file as it is loaded into the <xref:System.Xml.XmlDocument> object by creating the <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="2c1e7-118">XML belgesi şemasına göre geçerli olduğundan, şema doğrulama hataları veya uyarılar oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="2c1e7-118">Because the XML document is valid according to its schema, no schema validation errors or warnings are generated.</span></span>  
  
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
  
 <span data-ttu-id="2c1e7-119">Örnek, `contosoBooks.xml` dosyayı bir giriş olarak alır.</span><span class="sxs-lookup"><span data-stu-id="2c1e7-119">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="2c1e7-120">Örnek de `contosoBooks.xsd` bir giriş olarak alır.</span><span class="sxs-lookup"><span data-stu-id="2c1e7-120">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 <span data-ttu-id="2c1e7-121">Yukarıdaki örnekte, bir <xref:System.Xml.Schema.XmlSchemaValidationException> <xref:System.Xml.XmlDocument.Load%2A> öznitelik veya öğe türü, doğrulama şemasında belirtilen ilgili türle eşleşmezse, çağrıldığında bir oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2c1e7-121">In the above example, an <xref:System.Xml.Schema.XmlSchemaValidationException> will be thrown when <xref:System.Xml.XmlDocument.Load%2A> is called if any attribute or element type does not match the corresponding type specified in the validating schema.</span></span> <span data-ttu-id="2c1e7-122"><xref:System.Xml.XmlReaderSettings.ValidationEventHandler>Doğrulama üzerinde ayarlandıysa, <xref:System.Xml.XmlReader> <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> geçersiz bir tür ile karşılaşıldığında çağrılır.</span><span class="sxs-lookup"><span data-stu-id="2c1e7-122">If a <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> is set on the validating <xref:System.Xml.XmlReader>, the <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> will get called whenever an invalid type is encountered.</span></span>  
  
 <span data-ttu-id="2c1e7-123"><xref:System.Xml.Schema.XmlSchemaException>Öğesi tarafından olarak ayarlanmış bir özniteliğe veya öğeye erişildiğinde bir oluşturulur <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> `invalid` <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="2c1e7-123">An <xref:System.Xml.Schema.XmlSchemaException> will be thrown when an attribute or element with <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> set to `invalid` is accessed by the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
 <span data-ttu-id="2c1e7-124"><xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A>Özelliği, özniteliği veya öğelerine öğesine erişirken bağımsız bir özniteliğin veya öğenin geçerli olup olmadığını anlamak için kullanılabilir <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="2c1e7-124">The <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> property can be used to determine whether or not an individual attribute or element is valid when accessing attributes or elements with the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2c1e7-125">Bir XML belgesi, <xref:System.Xml.XmlDocument> varsayılan değerleri tanımlayan ilişkili bir şemaya sahip bir nesneye yüklendiğinde, <xref:System.Xml.XmlDocument> nesne bu varsayılanlara XML belgesinde görünmiş gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="2c1e7-125">When an XML document is loaded into an <xref:System.Xml.XmlDocument> object with an associated schema that defines default values, the <xref:System.Xml.XmlDocument> object treats these defaults as if they appeared in the XML document.</span></span> <span data-ttu-id="2c1e7-126">Bu, özelliğin, <xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> `false` boş bir öğe olarak yazılmış XML belgesinde olsa bile, her zaman şemanın varsayılan olarak ayarlanmış bir öğe için döndüğü anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="2c1e7-126">This means that the <xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> property  always returns `false` for an element that was defaulted from the schema, even if in the XML document it was written as an empty element.</span></span>  
  
### <a name="validating-a-document-using-the-validate-method"></a><span data-ttu-id="2c1e7-127">Validate metodunu kullanarak bir belgeyi doğrulama</span><span class="sxs-lookup"><span data-stu-id="2c1e7-127">Validating a Document using the Validate Method</span></span>  

 <span data-ttu-id="2c1e7-128"><xref:System.Xml.XmlDocument.Validate%2A>Sınıfının yöntemi, nesne <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlDocument> özelliğinde belirtilen şemalara karşı bır nesnede bulunan XML belgesini doğrular <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlDocument.Schemas%2A> ve bilgi kümesi genişletmesini gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="2c1e7-128">The <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class validates the XML document contained in an <xref:System.Xml.XmlDocument> object against the schemas specified in the <xref:System.Xml.XmlDocument> object's <xref:System.Xml.XmlDocument.Schemas%2A> property and performs infoset augmentation.</span></span> <span data-ttu-id="2c1e7-129">Sonuç olarak, <xref:System.Xml.XmlDocument> nesnede türü belirtilmiş bir belge ile değiştirilmiş olan, daha önce türsüz BIR XML belgesidir.</span><span class="sxs-lookup"><span data-stu-id="2c1e7-129">The result is a previously untyped XML document in the <xref:System.Xml.XmlDocument> object replaced with a typed document.</span></span>  
  
 <span data-ttu-id="2c1e7-130"><xref:System.Xml.XmlDocument>Nesnesi, <xref:System.Xml.Schema.ValidationEventHandler> yöntemine parametre olarak geçirilen temsilciyi kullanarak şema doğrulama hatalarını ve uyarılarını raporlar <xref:System.Xml.XmlDocument.Validate%2A> .</span><span class="sxs-lookup"><span data-stu-id="2c1e7-130">The <xref:System.Xml.XmlDocument> object reports schema validation errors and warnings using the <xref:System.Xml.Schema.ValidationEventHandler> delegate passed as a parameter to the <xref:System.Xml.XmlDocument.Validate%2A> method.</span></span>  
  
 <span data-ttu-id="2c1e7-131">Aşağıdaki örnek, nesnesinde `contosoBooks.xml` bulunan dosyayı <xref:System.Xml.XmlDocument> `contosoBooks.xsd` nesnenin özelliğinde bulunan şemaya karşı doğrular <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlDocument.Schemas%2A> .</span><span class="sxs-lookup"><span data-stu-id="2c1e7-131">The following example validates the `contosoBooks.xml` file contained in the <xref:System.Xml.XmlDocument> object against the `contosoBooks.xsd` schema contained in the <xref:System.Xml.XmlDocument> object's <xref:System.Xml.XmlDocument.Schemas%2A> property.</span></span>  
  
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
  
 <span data-ttu-id="2c1e7-132">Örnek, `contosoBooks.xml` dosyayı bir giriş olarak alır.</span><span class="sxs-lookup"><span data-stu-id="2c1e7-132">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="2c1e7-133">Örnek de `contosoBooks.xsd` bir giriş olarak alır.</span><span class="sxs-lookup"><span data-stu-id="2c1e7-133">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
### <a name="validating-modifications"></a><span data-ttu-id="2c1e7-134">Değişiklikler doğrulanıyor</span><span class="sxs-lookup"><span data-stu-id="2c1e7-134">Validating Modifications</span></span>  

 <span data-ttu-id="2c1e7-135">Bir XML belgesinde değişiklikler yapıldıktan sonra, sınıfının metodunu kullanarak XML belgesi şemasına karşı değişiklikleri doğrulayabilirsiniz <xref:System.Xml.XmlDocument.Validate%2A> <xref:System.Xml.XmlDocument> .</span><span class="sxs-lookup"><span data-stu-id="2c1e7-135">After modifications are made to an XML document, you can validate the modifications against the schema for the XML document using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="2c1e7-136">Aşağıdaki örnek, `contosoBooks.xml` <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlDocument> bir doğrulama nesnesi kullanılarak nesnesini oluşturarak dosyayı nesnesine yüklendiği şekilde doğrular <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="2c1e7-136">The following example validates the `contosoBooks.xml` file as it is loaded into the <xref:System.Xml.XmlDocument> object by creating the <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="2c1e7-137">XML belgesi, şema doğrulama hataları veya uyarılar üretilmeden yüklendiğinden başarıyla doğrulanacaktır.</span><span class="sxs-lookup"><span data-stu-id="2c1e7-137">The XML document is validated successfully as it is loaded without generating any schema validation errors or warnings.</span></span> <span data-ttu-id="2c1e7-138">Örnek daha sonra şemaya göre geçersiz olan XML belgesinde iki değişiklik yapar `contosoBooks.xsd` .</span><span class="sxs-lookup"><span data-stu-id="2c1e7-138">The example then makes two modifications to the XML document that are invalid according to the `contosoBooks.xsd` schema.</span></span> <span data-ttu-id="2c1e7-139">İlk değişiklik, bir şema doğrulama hatasına neden olan geçersiz bir alt öğe ekliyor ve ikinci değişiklik, bir özel duruma neden olan düğümün türüne göre geçersiz bir değere sahip bir değer olarak belirlenmiş bir değerin değerini ayarlıyor.</span><span class="sxs-lookup"><span data-stu-id="2c1e7-139">The first modification inserts an invalid child element resulting in a schema validation error, and the second modification sets the value of a typed node to a value that is invalid according to the type of the node resulting in an exception.</span></span>  
  
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
  
 <span data-ttu-id="2c1e7-140">Örnek, `contosoBooks.xml` dosyayı bir giriş olarak alır.</span><span class="sxs-lookup"><span data-stu-id="2c1e7-140">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="2c1e7-141">Örnek de `contosoBooks.xsd` bir giriş olarak alır.</span><span class="sxs-lookup"><span data-stu-id="2c1e7-141">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 <span data-ttu-id="2c1e7-142">Yukarıdaki örnekte, nesnesinde bulunan XML belgesinde iki değişiklik yapılmıştır <xref:System.Xml.XmlDocument> .</span><span class="sxs-lookup"><span data-stu-id="2c1e7-142">In the example above, two modifications are made to the XML document contained in the <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="2c1e7-143">XML belgesi yüklendiğinde, karşılaşılan tüm şema doğrulama hataları doğrulama olay işleyicisi yöntemi tarafından işlenirdi ve konsola yazılır.</span><span class="sxs-lookup"><span data-stu-id="2c1e7-143">As the XML document was loaded, any schema validation errors encountered would have been handled by the validation event handler method and written to the console.</span></span>  
  
 <span data-ttu-id="2c1e7-144">Bu örnekte, doğrulama hataları XML belgesi yüklendikten sonra ve sınıfının yöntemi kullanılarak bulunduktan sonra tanıtılmıştı <xref:System.Xml.XmlDocument.Validate%2A> <xref:System.Xml.XmlDocument> .</span><span class="sxs-lookup"><span data-stu-id="2c1e7-144">In this example, the validation errors were introduced after the XML document was loaded and were found using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="2c1e7-145">Sınıfının yöntemi kullanılarak yapılan değişiklikler <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> <xref:System.Xml.XPath.XPathNavigator> <xref:System.InvalidCastException> , düğümün şema türüne göre yeni değer geçersiz olduğu için bir ile sonuçlandı.</span><span class="sxs-lookup"><span data-stu-id="2c1e7-145">Modifications made using the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class resulted in an <xref:System.InvalidCastException> because the new value was invalid according to the schema type of the node.</span></span>  
  
 <span data-ttu-id="2c1e7-146">Yöntemi kullanarak değerleri değiştirme hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> bkz. [XML verilerini XPathNavigator ile değiştirme](modify-xml-data-using-xpathnavigator.md) konusu.</span><span class="sxs-lookup"><span data-stu-id="2c1e7-146">For more information about modifying values using the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method, see the [Modify XML Data using XPathNavigator](modify-xml-data-using-xpathnavigator.md) topic.</span></span>  
  
### <a name="read-only-validation"></a><span data-ttu-id="2c1e7-147">Read-Only doğrulaması</span><span class="sxs-lookup"><span data-stu-id="2c1e7-147">Read-Only Validation</span></span>  

 <span data-ttu-id="2c1e7-148"><xref:System.Xml.XPath.XPathDocument>Sınıfı, BIR XML belgesinin Salt okunabilir, bellek içi gösterimidir.</span><span class="sxs-lookup"><span data-stu-id="2c1e7-148">The <xref:System.Xml.XPath.XPathDocument> class is a read-only, in-memory representation of an XML document.</span></span> <span data-ttu-id="2c1e7-149">Hem <xref:System.Xml.XPath.XPathDocument> sınıf hem de <xref:System.Xml.XmlDocument> sınıf, <xref:System.Xml.XPath.XPathNavigator> XML belgelerini gezinmek ve düzenlemek için nesneler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2c1e7-149">Both the <xref:System.Xml.XPath.XPathDocument> class and the <xref:System.Xml.XmlDocument> class create <xref:System.Xml.XPath.XPathNavigator> objects to navigate and edit XML documents.</span></span> <span data-ttu-id="2c1e7-150"><xref:System.Xml.XPath.XPathDocument>Sınıfı salt bir salt okunurdur, nesne nesnesinden <xref:System.Xml.XPath.XPathNavigator> döndürülen <xref:System.Xml.XPath.XPathDocument> nesneler, nesnede bulunan XML belgesini düzenleyemez <xref:System.Xml.XPath.XPathDocument> .</span><span class="sxs-lookup"><span data-stu-id="2c1e7-150">Because the <xref:System.Xml.XPath.XPathDocument> class is a read-only class, <xref:System.Xml.XPath.XPathNavigator> object's returned from <xref:System.Xml.XPath.XPathDocument> objects cannot edit the XML document contained in the <xref:System.Xml.XPath.XPathDocument> object.</span></span>  
  
 <span data-ttu-id="2c1e7-151">Doğrulama durumunda, <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlReader> Bu konuda daha önce açıklandığı gibi doğrulama nesnesini kullanarak bir nesne oluşturduğunuz gibi bir nesne oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2c1e7-151">In the case of validation, you can create an <xref:System.Xml.XPath.XPathDocument> object just like you create an <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object as described earlier in this topic.</span></span> <span data-ttu-id="2c1e7-152"><xref:System.Xml.XPath.XPathDocument>Nesne, yüklendiği gıbı XML belgesini doğrular, ancak nesne IÇINDEKI XML verilerini DÜZENLEYEMEDIĞINDEN <xref:System.Xml.XPath.XPathDocument> XML belgesini yeniden doğrulayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="2c1e7-152">The <xref:System.Xml.XPath.XPathDocument> object validates the XML document as it is loaded, but because you cannot edit the XML data in the <xref:System.Xml.XPath.XPathDocument> object, you cannot revalidate the XML document.</span></span>  
  
 <span data-ttu-id="2c1e7-153">Salt okunurdur ve düzenlenebilir nesneler hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator> , [XPathDocument ve XMLDOCUMENT kullanarak XML verilerini okuma](reading-xml-data-using-xpathdocument-and-xmldocument.md) konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="2c1e7-153">For more information about read-only and editable <xref:System.Xml.XPath.XPathNavigator> objects, see the [Reading XML Data using XPathDocument and XmlDocument](reading-xml-data-using-xpathdocument-and-xmldocument.md) topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c1e7-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c1e7-154">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="2c1e7-155">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="2c1e7-155">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="2c1e7-156">XPathDocument ve XmlDocument Kullanarak XML Verilerini Okuma</span><span class="sxs-lookup"><span data-stu-id="2c1e7-156">Reading XML Data using XPathDocument and XmlDocument</span></span>](reading-xml-data-using-xpathdocument-and-xmldocument.md)
- [<span data-ttu-id="2c1e7-157">XPathNavigator Kullanarak XML Verileri Seçme, Değerlendirme ve Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="2c1e7-157">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="2c1e7-158">XPathNavigator Kullanarak XML Verilerine Erişme</span><span class="sxs-lookup"><span data-stu-id="2c1e7-158">Accessing XML Data using XPathNavigator</span></span>](accessing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="2c1e7-159">XPathNavigator Kullanarak XML Verilerini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="2c1e7-159">Editing XML Data using XPathNavigator</span></span>](editing-xml-data-using-xpathnavigator.md)
