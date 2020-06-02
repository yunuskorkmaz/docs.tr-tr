---
title: XPathNavigator Kullanarak Şema Doğrulama
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 81fa0e41-d9c9-46f0-b22b-50da839c77f5
ms.openlocfilehash: f6e56616543bf7d2ad2e6be4d7bf7cbc50ba3a23
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84292013"
---
# <a name="schema-validation-using-xpathnavigator"></a>XPathNavigator Kullanarak Şema Doğrulama
Sınıfını kullanarak <xref:System.Xml.XmlDocument> bir nesnede bulunan XML içeriğini <xref:System.Xml.XmlDocument> iki şekilde doğrulayabilirsiniz. İlk yöntem, Validating nesnesini kullanarak XML içeriğini doğrulamak <xref:System.Xml.XmlReader> ve ikinci yöntem ise <xref:System.Xml.XmlDocument.Validate%2A> sınıfının yöntemini kullanmaktır <xref:System.Xml.XmlDocument> . Ayrıca, sınıfını kullanarak XML içeriğinin salt okunurdur doğrulamasını gerçekleştirebilirsiniz <xref:System.Xml.XPath.XPathDocument> .  
  
## <a name="validating-xml-data"></a>XML verileri doğrulanıyor  
 <xref:System.Xml.XmlDocument>Sınıf, varsayılan olarak DTD veya XML şeması tanım dili (xsd) şema doğrulamasını kullanarak BIR XML belgesini doğrulamaz. Yalnızca XML belgesinin düzgün biçimlendirildiğini doğrular.  
  
 Bir XML belgesini doğrulamaya yönelik ilk yol, doğrulama nesnesi kullanılarak bir nesneye yüklendiğinde belgeyi doğrulamaktır <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlReader> . İkinci yol, sınıfının yöntemini kullanarak daha önce türsüz bir XML belgesini doğrulamaktır <xref:System.Xml.XmlDocument.Validate%2A> <xref:System.Xml.XmlDocument> . Her iki durumda da, doğrulanan XML belgesinde yapılan değişiklikler, sınıfının yöntemi kullanılarak yeniden doğrulanabilir <xref:System.Xml.XmlDocument.Validate%2A> <xref:System.Xml.XmlDocument> .  
  
### <a name="validating-a-document-as-it-is-loaded"></a>Belge yüklendiği için doğrulanıyor  
 Bir nesne, bir nesneyi <xref:System.Xml.XmlReader> <xref:System.Xml.XmlReaderSettings> <xref:System.Xml.XmlReader.Create%2A> <xref:System.Xml.XmlReader> parametre olarak alan sınıfın yöntemine geçirerek bir doğrulama nesnesi oluşturulur <xref:System.Xml.XmlReaderSettings> . <xref:System.Xml.XmlReaderSettings>Parametre olarak geçirilen nesne, <xref:System.Xml.XmlReaderSettings.ValidationType%2A> özelliğine ayarlanmış bir özelliği `Schema` ve <xref:System.Xml.XmlDocument> ÖZELLIĞINE eklenen nesne içindeki XML belgesi için bir XML şeması içerir <xref:System.Xml.XmlReaderSettings.Schemas%2A> . Doğrulama <xref:System.Xml.XmlReader> nesnesi daha sonra nesneyi oluşturmak için kullanılır <xref:System.Xml.XmlDocument> .  
  
 Aşağıdaki örnek, `contosoBooks.xml` <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlDocument> bir doğrulama nesnesi kullanılarak nesnesini oluşturarak dosyayı nesnesine yüklendiği şekilde doğrular <xref:System.Xml.XmlReader> . XML belgesi şemasına göre geçerli olduğundan, şema doğrulama hataları veya uyarılar oluşturulmaz.  
  
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
  
 Örnek de `contosoBooks.xsd` bir giriş olarak alır.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 Yukarıdaki örnekte, bir <xref:System.Xml.Schema.XmlSchemaValidationException> <xref:System.Xml.XmlDocument.Load%2A> öznitelik veya öğe türü, doğrulama şemasında belirtilen ilgili türle eşleşmezse, çağrıldığında bir oluşturulur. <xref:System.Xml.XmlReaderSettings.ValidationEventHandler>Doğrulama üzerinde ayarlandıysa, <xref:System.Xml.XmlReader> <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> geçersiz bir tür ile karşılaşıldığında çağrılır.  
  
 <xref:System.Xml.Schema.XmlSchemaException>Öğesi tarafından olarak ayarlanmış bir özniteliğe veya öğeye erişildiğinde bir oluşturulur <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> `invalid` <xref:System.Xml.XPath.XPathNavigator> .  
  
 <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A>Özelliği, özniteliği veya öğelerine öğesine erişirken bağımsız bir özniteliğin veya öğenin geçerli olup olmadığını anlamak için kullanılabilir <xref:System.Xml.XPath.XPathNavigator> .  
  
> [!NOTE]
> Bir XML belgesi, <xref:System.Xml.XmlDocument> varsayılan değerleri tanımlayan ilişkili bir şemaya sahip bir nesneye yüklendiğinde, <xref:System.Xml.XmlDocument> nesne bu varsayılanlara XML belgesinde görünmiş gibi davranır. Bu, özelliğin, <xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> `false` boş bir öğe olarak yazılmış XML belgesinde olsa bile, her zaman şemanın varsayılan olarak ayarlanmış bir öğe için döndüğü anlamına gelir.  
  
### <a name="validating-a-document-using-the-validate-method"></a>Validate metodunu kullanarak bir belgeyi doğrulama  
 <xref:System.Xml.XmlDocument.Validate%2A>Sınıfının yöntemi, nesne <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlDocument> özelliğinde belirtilen şemalara karşı bır nesnede bulunan XML belgesini doğrular <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlDocument.Schemas%2A> ve bilgi kümesi genişletmesini gerçekleştirir. Sonuç olarak, <xref:System.Xml.XmlDocument> nesnede türü belirtilmiş bir belge ile değiştirilmiş olan, daha önce türsüz BIR XML belgesidir.  
  
 <xref:System.Xml.XmlDocument>Nesnesi, <xref:System.Xml.Schema.ValidationEventHandler> yöntemine parametre olarak geçirilen temsilciyi kullanarak şema doğrulama hatalarını ve uyarılarını raporlar <xref:System.Xml.XmlDocument.Validate%2A> .  
  
 Aşağıdaki örnek, nesnesinde `contosoBooks.xml` bulunan dosyayı <xref:System.Xml.XmlDocument> `contosoBooks.xsd` nesnenin özelliğinde bulunan şemaya karşı doğrular <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlDocument.Schemas%2A> .  
  
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
  
 Örnek de `contosoBooks.xsd` bir giriş olarak alır.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
### <a name="validating-modifications"></a>Değişiklikler doğrulanıyor  
 Bir XML belgesinde değişiklikler yapıldıktan sonra, sınıfının metodunu kullanarak XML belgesi şemasına karşı değişiklikleri doğrulayabilirsiniz <xref:System.Xml.XmlDocument.Validate%2A> <xref:System.Xml.XmlDocument> .  
  
 Aşağıdaki örnek, `contosoBooks.xml` <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlDocument> bir doğrulama nesnesi kullanılarak nesnesini oluşturarak dosyayı nesnesine yüklendiği şekilde doğrular <xref:System.Xml.XmlReader> . XML belgesi, şema doğrulama hataları veya uyarılar üretilmeden yüklendiğinden başarıyla doğrulanacaktır. Örnek daha sonra şemaya göre geçersiz olan XML belgesinde iki değişiklik yapar `contosoBooks.xsd` . İlk değişiklik, bir şema doğrulama hatasına neden olan geçersiz bir alt öğe ekliyor ve ikinci değişiklik, bir özel duruma neden olan düğümün türüne göre geçersiz bir değere sahip bir değer olarak belirlenmiş bir değerin değerini ayarlıyor.  
  
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
  
 Örnek de `contosoBooks.xsd` bir giriş olarak alır.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 Yukarıdaki örnekte, nesnesinde bulunan XML belgesinde iki değişiklik yapılmıştır <xref:System.Xml.XmlDocument> . XML belgesi yüklendiğinde, karşılaşılan tüm şema doğrulama hataları doğrulama olay işleyicisi yöntemi tarafından işlenirdi ve konsola yazılır.  
  
 Bu örnekte, doğrulama hataları XML belgesi yüklendikten sonra ve sınıfının yöntemi kullanılarak bulunduktan sonra tanıtılmıştı <xref:System.Xml.XmlDocument.Validate%2A> <xref:System.Xml.XmlDocument> .  
  
 Sınıfının yöntemi kullanılarak yapılan değişiklikler <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> <xref:System.Xml.XPath.XPathNavigator> <xref:System.InvalidCastException> , düğümün şema türüne göre yeni değer geçersiz olduğu için bir ile sonuçlandı.  
  
 Yöntemi kullanarak değerleri değiştirme hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> bkz. [XML verilerini XPathNavigator ile değiştirme](modify-xml-data-using-xpathnavigator.md) konusu.  
  
### <a name="read-only-validation"></a>Salt okuma doğrulaması  
 <xref:System.Xml.XPath.XPathDocument>Sınıfı, BIR XML belgesinin Salt okunabilir, bellek içi gösterimidir. Hem <xref:System.Xml.XPath.XPathDocument> sınıf hem de <xref:System.Xml.XmlDocument> sınıf, <xref:System.Xml.XPath.XPathNavigator> XML belgelerini gezinmek ve düzenlemek için nesneler oluşturur. <xref:System.Xml.XPath.XPathDocument>Sınıfı salt bir salt okunurdur, nesne nesnesinden <xref:System.Xml.XPath.XPathNavigator> döndürülen <xref:System.Xml.XPath.XPathDocument> nesneler, nesnede bulunan XML belgesini düzenleyemez <xref:System.Xml.XPath.XPathDocument> .  
  
 Doğrulama durumunda, <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlReader> Bu konuda daha önce açıklandığı gibi doğrulama nesnesini kullanarak bir nesne oluşturduğunuz gibi bir nesne oluşturabilirsiniz. <xref:System.Xml.XPath.XPathDocument>Nesne, yüklendiği gıbı XML belgesini doğrular, ancak nesne IÇINDEKI XML verilerini DÜZENLEYEMEDIĞINDEN <xref:System.Xml.XPath.XPathDocument> XML belgesini yeniden doğrulayamazsınız.  
  
 Salt okunurdur ve düzenlenebilir nesneler hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator> , [XPathDocument ve XMLDOCUMENT kullanarak XML verilerini okuma](reading-xml-data-using-xpathdocument-and-xmldocument.md) konusuna bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](process-xml-data-using-the-xpath-data-model.md)
- [XPathDocument ve XmlDocument Kullanarak XML Verilerini Okuma](reading-xml-data-using-xpathdocument-and-xmldocument.md)
- [XPathNavigator Kullanarak XML Verileri Seçme, Değerlendirme ve Eşleştirme](selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
- [XPathNavigator Kullanarak XML Verilerine Erişme](accessing-xml-data-using-xpathnavigator.md)
- [XPathNavigator Kullanarak XML Verilerini Düzenleme](editing-xml-data-using-xpathnavigator.md)
