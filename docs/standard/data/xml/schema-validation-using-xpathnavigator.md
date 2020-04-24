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
# <a name="schema-validation-using-xpathnavigator"></a>XPathNavigator Kullanarak Şema Doğrulama
<xref:System.Xml.XmlDocument> Sınıfını kullanarak bir <xref:System.Xml.XmlDocument> nesnede bulunan XML içeriğini iki şekilde doğrulayabilirsiniz. İlk yöntem, Validating <xref:System.Xml.XmlReader> NESNESINI kullanarak XML içeriğini doğrulamak ve ikinci yöntem ise <xref:System.Xml.XmlDocument.Validate%2A> <xref:System.Xml.XmlDocument> sınıfının yöntemini kullanmaktır. Ayrıca, <xref:System.Xml.XPath.XPathDocument> SıNıFıNı kullanarak XML içeriğinin salt okunurdur doğrulamasını gerçekleştirebilirsiniz.  
  
## <a name="validating-xml-data"></a>XML verileri doğrulanıyor  
 Sınıf <xref:System.Xml.XmlDocument> , varsayılan olarak DTD veya XML şeması tanım DILI (xsd) şema doğrulamasını kullanarak bir XML belgesini doğrulamaz. Yalnızca XML belgesinin düzgün biçimlendirildiğini doğrular.  
  
 Bir XML belgesini doğrulamaya yönelik ilk yol, doğrulama <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlReader> nesnesi kullanılarak bir nesneye yüklendiğinde belgeyi doğrulamaktır. İkinci yol, <xref:System.Xml.XmlDocument.Validate%2A> <xref:System.Xml.XmlDocument> sınıfının yöntemini kullanarak daha önce türsüz bir XML belgesini doğrulamaktır. Her iki durumda da, doğrulanan XML belgesinde yapılan değişiklikler, <xref:System.Xml.XmlDocument.Validate%2A> <xref:System.Xml.XmlDocument> sınıfının yöntemi kullanılarak yeniden doğrulanabilir.  
  
### <a name="validating-a-document-as-it-is-loaded"></a>Belge yüklendiği için doğrulanıyor  
 Bir nesne <xref:System.Xml.XmlReader> , bir nesneyi parametre olarak alan <xref:System.Xml.XmlReaderSettings> <xref:System.Xml.XmlReader.Create%2A> <xref:System.Xml.XmlReader> <xref:System.Xml.XmlReaderSettings> sınıfın yöntemine geçirerek bir doğrulama nesnesi oluşturulur. Parametre <xref:System.Xml.XmlReaderSettings> olarak geçirilen <xref:System.Xml.XmlReaderSettings.ValidationType%2A> nesne, `Schema` <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlReaderSettings.Schemas%2A> özelliğine ayarlanmış bir ÖZELLIĞI ve özelliğine eklenen nesne içindeki XML belgesi için bir XML şeması içerir. Doğrulama <xref:System.Xml.XmlReader> nesnesi daha sonra <xref:System.Xml.XmlDocument> nesneyi oluşturmak için kullanılır.  
  
 Aşağıdaki örnek, bir doğrulama `contosoBooks.xml` <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlReader> nesnesi kullanılarak nesnesini oluşturarak dosyayı <xref:System.Xml.XmlDocument> nesnesine yüklendiği şekilde doğrular. XML belgesi şemasına göre geçerli olduğundan, şema doğrulama hataları veya uyarılar oluşturulmaz.  
  
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
  
 Yukarıdaki örnekte, bir öznitelik veya <xref:System.Xml.Schema.XmlSchemaValidationException> öğe türü, doğrulama <xref:System.Xml.XmlDocument.Load%2A> şemasında belirtilen ilgili türle eşleşmezse, çağrıldığında bir oluşturulur. <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> <xref:System.Xml.XmlReader>Doğrulama <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> üzerinde ayarlandıysa, geçersiz bir tür ile karşılaşıldığında çağrılır.  
  
 Öğesi <xref:System.Xml.Schema.XmlSchemaException> tarafından olarak <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> ayarlanmış `invalid` bir özniteliğe veya öğeye erişildiğinde bir oluşturulur. <xref:System.Xml.XPath.XPathNavigator>  
  
 <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> Özelliği, <xref:System.Xml.XPath.XPathNavigator>özniteliği veya öğelerine öğesine erişirken bağımsız bir özniteliğin veya öğenin geçerli olup olmadığını anlamak için kullanılabilir.  
  
> [!NOTE]
> Bir XML belgesi, varsayılan değerleri tanımlayan ilişkili <xref:System.Xml.XmlDocument> bir şemaya sahip bir nesneye yüklendiğinde, <xref:System.Xml.XmlDocument> nesne bu varsayılanlara XML belgesinde görünmiş gibi davranır. Bu, <xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> özelliğin, boş bir öğe `false` olarak yazılmış XML belgesinde olsa bile, her zaman şemanın varsayılan olarak ayarlanmış bir öğe için döndüğü anlamına gelir.  
  
### <a name="validating-a-document-using-the-validate-method"></a>Validate metodunu kullanarak bir belgeyi doğrulama  
 <xref:System.Xml.XmlDocument> Sınıfının <xref:System.Xml.XmlDocument.Validate%2A> yöntemi, nesne <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlDocument.Schemas%2A> özelliğinde belirtilen şemalara karşı bir nesnede bulunan XML belgesini doğrular ve bilgi kümesi genişletmesini gerçekleştirir. Sonuç olarak, <xref:System.Xml.XmlDocument> nesnede türü belirtilmiş bir belge ile değiştirilmiş olan, daha önce TÜRSÜZ bir XML belgesidir.  
  
 <xref:System.Xml.XmlDocument> Nesnesi, <xref:System.Xml.Schema.ValidationEventHandler> <xref:System.Xml.XmlDocument.Validate%2A> yöntemine parametre olarak geçirilen temsilciyi kullanarak şema doğrulama hatalarını ve uyarılarını raporlar.  
  
 Aşağıdaki örnek, nesnesinde bulunan `contosoBooks.xml` <xref:System.Xml.XmlDocument> dosyayı `contosoBooks.xsd` <xref:System.Xml.XmlDocument> nesnenin <xref:System.Xml.XmlDocument.Schemas%2A> özelliğinde bulunan şemaya karşı doğrular.  
  
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
  
 Aşağıdaki örnek, bir doğrulama `contosoBooks.xml` <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlReader> nesnesi kullanılarak nesnesini oluşturarak dosyayı <xref:System.Xml.XmlDocument> nesnesine yüklendiği şekilde doğrular. XML belgesi, şema doğrulama hataları veya uyarılar üretilmeden yüklendiğinden başarıyla doğrulanacaktır. Örnek daha sonra `contosoBooks.xsd` şemaya göre GEÇERSIZ olan XML belgesinde iki değişiklik yapar. İlk değişiklik, bir şema doğrulama hatasına neden olan geçersiz bir alt öğe ekliyor ve ikinci değişiklik, bir özel duruma neden olan düğümün türüne göre geçersiz bir değere sahip bir değer olarak belirlenmiş bir değerin değerini ayarlıyor.  
  
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
  
 Yukarıdaki örnekte, <xref:System.Xml.XmlDocument> NESNESINDE bulunan XML belgesinde iki değişiklik yapılmıştır. XML belgesi yüklendiğinde, karşılaşılan tüm şema doğrulama hataları doğrulama olay işleyicisi yöntemi tarafından işlenirdi ve konsola yazılır.  
  
 Bu örnekte, doğrulama hataları XML belgesi yüklendikten sonra ve <xref:System.Xml.XmlDocument.Validate%2A> <xref:System.Xml.XmlDocument> sınıfının yöntemi kullanılarak bulunduktan sonra tanıtılmıştı.  
  
 Sınıfının yöntemi kullanılarak yapılan değişiklikler, düğümün şema türüne göre yeni <xref:System.InvalidCastException> değer geçersiz olduğu için bir ile sonuçlandı. <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> <xref:System.Xml.XPath.XPathNavigator>  
  
 <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> Yöntemi kullanarak değerleri değiştirme hakkında daha fazla bilgi için bkz. [XML verilerini XPathNavigator ile değiştirme](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) konusu.  
  
### <a name="read-only-validation"></a>Salt okuma doğrulaması  
 <xref:System.Xml.XPath.XPathDocument> Sınıfı, bir XML belgesinin Salt okunabilir, bellek içi gösterimidir. Hem <xref:System.Xml.XPath.XPathDocument> sınıf hem de <xref:System.Xml.XmlDocument> sınıf, XML <xref:System.Xml.XPath.XPathNavigator> belgelerini gezinmek ve düzenlemek için nesneler oluşturur. <xref:System.Xml.XPath.XPathDocument> Sınıfı salt bir salt okunurdur, <xref:System.Xml.XPath.XPathNavigator> nesne nesnesinden döndürülen <xref:System.Xml.XPath.XPathDocument> nesneler, <xref:System.Xml.XPath.XPathDocument> nesnede bulunan XML belgesini düzenleyemez.  
  
 Doğrulama durumunda, bu konuda daha önce açıklandığı gibi doğrulama <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlReader> nesnesini kullanarak bir nesne oluşturduğunuz gibi <xref:System.Xml.XmlDocument> bir nesne oluşturabilirsiniz. <xref:System.Xml.XPath.XPathDocument> Nesne, YÜKLENDIĞI gibi XML belgesini doğrular, ancak <xref:System.Xml.XPath.XPathDocument> nesne içindeki XML verilerini düzenleyemediğinden XML belgesini yeniden doğrulayamazsınız.  
  
 Salt okunurdur ve düzenlenebilir <xref:System.Xml.XPath.XPathNavigator> nesneler hakkında daha fazla bilgi Için, [XPathDocument ve XmlDocument kullanarak XML verilerini okuma](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md) konusuna bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [XPathDocument ve XmlDocument Kullanarak XML Verilerini Okuma](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)
- [XPathNavigator Kullanarak XML Verileri Seçme, Değerlendirme ve Eşleştirme](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
- [XPathNavigator Kullanarak XML Verilerine Erişme](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)
- [XPathNavigator Kullanarak XML Verilerini Düzenleme](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)
