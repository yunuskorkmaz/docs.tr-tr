---
title: XPathNavigator Kullanarak Şema Doğrulama
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 81fa0e41-d9c9-46f0-b22b-50da839c77f5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0199efb172466305af22c4ade7c47115a5cefd8f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939614"
---
# <a name="schema-validation-using-xpathnavigator"></a>XPathNavigator Kullanarak Şema Doğrulama
Sınıfını kullanarak bir <xref:System.Xml.XmlDocument> nesnede bulunan XML içeriğini iki şekilde doğrulayabilirsiniz. <xref:System.Xml.XmlDocument> İlk yöntem, Validating <xref:System.Xml.XmlReader> nesnesini kullanarak XML içeriğini doğrulamak ve ikinci yöntem ise <xref:System.Xml.XmlDocument> sınıfının <xref:System.Xml.XmlDocument.Validate%2A> yöntemini kullanmaktır. Ayrıca, <xref:System.Xml.XPath.XPathDocument> sınıfını kullanarak XML içeriğinin salt okunurdur doğrulamasını gerçekleştirebilirsiniz.  
  
## <a name="validating-xml-data"></a>XML verileri doğrulanıyor  
 Sınıf <xref:System.Xml.XmlDocument> , varsayılan olarak DTD veya XML şeması tanım dili (xsd) şema doğrulamasını kullanarak bir XML belgesini doğrulamaz. Yalnızca XML belgesinin düzgün biçimlendirildiğini doğrular.  
  
 Bir XML belgesini doğrulamaya yönelik ilk yol, doğrulama <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlReader> nesnesi kullanılarak bir nesneye yüklendiğinde belgeyi doğrulamaktır. İkinci yol, <xref:System.Xml.XmlDocument.Validate%2A> <xref:System.Xml.XmlDocument> sınıfının yöntemini kullanarak daha önce türsüz bir XML belgesini doğrulamaktır. Her iki durumda da, doğrulanan xml belgesinde yapılan değişiklikler, <xref:System.Xml.XmlDocument.Validate%2A> <xref:System.Xml.XmlDocument> sınıfının yöntemi kullanılarak yeniden doğrulanabilir.  
  
### <a name="validating-a-document-as-it-is-loaded"></a>Belge yüklendiği için doğrulanıyor  
 Bir nesne <xref:System.Xml.XmlReader> , bir nesneyi parametre olarak alan <xref:System.Xml.XmlReaderSettings> <xref:System.Xml.XmlReader.Create%2A> <xref:System.Xml.XmlReader> <xref:System.Xml.XmlReaderSettings> sınıfın yöntemine geçirerek bir doğrulama nesnesi oluşturulur. <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlReaderSettings.ValidationType%2A> `Schema` Parametre olarak geçirilen <xref:System.Xml.XmlReaderSettings.Schemas%2A> nesne, özelliğine ayarlanmış bir özelliği ve özelliğine eklenen nesne içindeki XML belgesi için bir XML şeması içerir. <xref:System.Xml.XmlReaderSettings> Doğrulama <xref:System.Xml.XmlReader> nesnesi daha sonra <xref:System.Xml.XmlDocument> nesneyi oluşturmak için kullanılır.  
  
 Aşağıdaki örnek, bir doğrulama `contosoBooks.xml` <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlDocument> nesnesi<xref:System.Xml.XmlReader> kullanılarak nesnesini oluşturarak dosyayı nesnesine yüklendiği şekilde doğrular. XML belgesi şemasına göre geçerli olduğundan, şema doğrulama hataları veya uyarılar oluşturulmaz.  
  
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
  
 Örnek, `contosoBooks.xml` dosyayı bir giriş olarak alır.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Örnek de bir giriş `contosoBooks.xsd` olarak alır.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 Yukarıdaki örnekte, bir öznitelik veya <xref:System.Xml.Schema.XmlSchemaValidationException> öğe türü, doğrulama <xref:System.Xml.XmlDocument.Load%2A> şemasında belirtilen ilgili türle eşleşmezse, çağrıldığında bir oluşturulur. <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> Doğrulama<xref:System.Xml.XmlReader>üzerinde ayarlandıysa,geçersizbirtür<xref:System.Xml.XmlReaderSettings.ValidationEventHandler> ile karşılaşıldığında çağrılır.  
  
 Öğesi tarafından <xref:System.Xml.Schema.XmlSchemaException> olarak`invalid` ayarlanmış bir özniteliğe veya öğeye erişildiğinde bir oluşturulur. <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A>  
  
 <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> Özelliği ,<xref:System.Xml.XPath.XPathNavigator>özniteliği veya öğelerine öğesine erişirken bağımsız bir özniteliğin veya öğenin geçerli olup olmadığını anlamak için kullanılabilir.  
  
> [!NOTE]
> Bir XML belgesi, varsayılan değerleri tanımlayan ilişkili <xref:System.Xml.XmlDocument> bir şemaya sahip bir nesneye yüklendiğinde <xref:System.Xml.XmlDocument> , nesne bu varsayılanlara XML belgesinde görünmiş gibi davranır. Bu, <xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> özelliğin, boş bir öğe `false` olarak yazılmış XML belgesinde olsa bile, her zaman şemanın varsayılan olarak ayarlanmış bir öğe için döndüğü anlamına gelir.  
  
### <a name="validating-a-document-using-the-validate-method"></a>Validate metodunu kullanarak bir belgeyi doğrulama  
 <xref:System.Xml.XmlDocument.Validate%2A> <xref:System.Xml.XmlDocument> Sınıfının yöntemi ,nesne<xref:System.Xml.XmlDocument.Schemas%2A> özelliğinde belirtilen<xref:System.Xml.XmlDocument> şemalara karşı bir nesnede bulunan XML belgesini doğrular ve bilgi kümesi genişletmesini gerçekleştirir. <xref:System.Xml.XmlDocument> Sonuç olarak <xref:System.Xml.XmlDocument> , nesnede türü belirtilmiş bir belge ile değiştirilmiş olan, daha önce türsüz bir XML belgesidir.  
  
 Nesnesi, yöntemine parametre olarak geçirilen <xref:System.Xml.Schema.ValidationEventHandler> temsilciyi kullanarak şema doğrulama hatalarını ve uyarılarını raporlar. <xref:System.Xml.XmlDocument.Validate%2A> <xref:System.Xml.XmlDocument>  
  
 Aşağıdaki örnek, nesnesinde bulunan `contosoBooks.xml` <xref:System.Xml.XmlDocument> dosyayı `contosoBooks.xsd` <xref:System.Xml.XmlDocument> nesnenin<xref:System.Xml.XmlDocument.Schemas%2A> özelliğinde bulunan şemaya karşı doğrular.  
  
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
  
 Örnek, `contosoBooks.xml` dosyayı bir giriş olarak alır.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Örnek de bir giriş `contosoBooks.xsd` olarak alır.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
### <a name="validating-modifications"></a>Değişiklikler doğrulanıyor  
 Bir XML belgesinde değişiklikler yapıldıktan sonra, <xref:System.Xml.XmlDocument.Validate%2A> <xref:System.Xml.XmlDocument> sınıfının metodunu kullanarak XML belgesi şemasına karşı değişiklikleri doğrulayabilirsiniz.  
  
 Aşağıdaki örnek, bir doğrulama `contosoBooks.xml` <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlDocument> nesnesi<xref:System.Xml.XmlReader> kullanılarak nesnesini oluşturarak dosyayı nesnesine yüklendiği şekilde doğrular. XML belgesi, şema doğrulama hataları veya uyarılar üretilmeden yüklendiğinden başarıyla doğrulanacaktır. Örnek daha sonra `contosoBooks.xsd` şemaya göre geçersiz olan XML belgesinde iki değişiklik yapar. İlk değişiklik, bir şema doğrulama hatasına neden olan geçersiz bir alt öğe ekliyor ve ikinci değişiklik, bir özel duruma neden olan düğümün türüne göre geçersiz bir değere sahip bir değer olarak belirlenmiş bir değerin değerini ayarlıyor.  
  
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
  
 Örnek, `contosoBooks.xml` dosyayı bir giriş olarak alır.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Örnek de bir giriş `contosoBooks.xsd` olarak alır.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 Yukarıdaki örnekte, <xref:System.Xml.XmlDocument> nesnesinde bulunan XML belgesinde iki değişiklik yapılmıştır. XML belgesi yüklendiğinde, karşılaşılan tüm şema doğrulama hataları doğrulama olay işleyicisi yöntemi tarafından işlenirdi ve konsola yazılır.  
  
 Bu örnekte, doğrulama hataları XML belgesi yüklendikten sonra ve <xref:System.Xml.XmlDocument.Validate%2A> <xref:System.Xml.XmlDocument> sınıfının yöntemi kullanılarak bulunduktan sonra tanıtılmıştı.  
  
 Sınıfının yöntemi kullanılarak yapılan değişiklikler, düğümün şema türüne göre yeni <xref:System.InvalidCastException> değer geçersiz olduğu için bir ile sonuçlandı. <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> <xref:System.Xml.XPath.XPathNavigator>  
  
 <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> Yöntemi kullanarak değerleri değiştirme hakkında daha fazla bilgi için bkz. [XML verilerini XPathNavigator ile değiştirme](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) konusu.  
  
### <a name="read-only-validation"></a>Salt okuma doğrulaması  
 <xref:System.Xml.XPath.XPathDocument> Sınıfı, bir XML belgesinin Salt okunabilir, bellek içi gösterimidir. Hem sınıf hem de sınıf, XML belgelerini gezinmek ve düzenlemek için nesneler oluşturur <xref:System.Xml.XPath.XPathNavigator>. <xref:System.Xml.XmlDocument> <xref:System.Xml.XPath.XPathDocument> Sınıfı salt bir salt okunurdur, <xref:System.Xml.XPath.XPathNavigator> nesne nesnesinden döndürülen <xref:System.Xml.XPath.XPathDocument> nesneler, <xref:System.Xml.XPath.XPathDocument> nesnede bulunan XML belgesini düzenleyemez. <xref:System.Xml.XPath.XPathDocument>  
  
 Doğrulama durumunda, bu konuda daha önce açıklandığı gibi doğrulama <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlReader> nesnesini kullanarak bir nesne oluşturduğunuz gibi <xref:System.Xml.XmlDocument> bir nesne oluşturabilirsiniz. Nesne, yüklendiği gibi XML belgesini doğrular, ancak <xref:System.Xml.XPath.XPathDocument> nesne içindeki XML verilerini düzenleyemediğinden XML belgesini yeniden doğrulayamazsınız. <xref:System.Xml.XPath.XPathDocument>  
  
 Salt okunurdur ve düzenlenebilir <xref:System.Xml.XPath.XPathNavigator> nesneler hakkında daha fazla bilgi için, [XPathDocument ve XmlDocument kullanarak XML verilerini okuma](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md) konusuna bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [XPathDocument ve XmlDocument Kullanarak XML Verilerini Okuma](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)
- [XPathNavigator Kullanarak XML Verileri Seçme, Değerlendirme ve Eşleştirme](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
- [XPathNavigator Kullanarak XML Verilerine Erişme](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)
- [XPathNavigator Kullanarak XML Verilerini Düzenleme](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)
