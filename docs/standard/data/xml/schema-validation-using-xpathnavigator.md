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
<xref:System.Xml.XmlDocument> sınıfını kullanarak, bir <xref:System.Xml.XmlDocument> nesnesinde bulunan XML içeriğini iki şekilde doğrulayabilirsiniz. İlk yöntem, Validating <xref:System.Xml.XmlReader> nesnesini kullanarak XML içeriğini doğrulamak ve ikinci yöntem <xref:System.Xml.XmlDocument> sınıfının <xref:System.Xml.XmlDocument.Validate%2A> yöntemini kullanmaktır. Ayrıca, <xref:System.Xml.XPath.XPathDocument> sınıfını kullanarak XML içeriğinin salt okunurdur doğrulamasını gerçekleştirebilirsiniz.  
  
## <a name="validating-xml-data"></a>XML verileri doğrulanıyor  
 <xref:System.Xml.XmlDocument> sınıfı, varsayılan olarak DTD veya XML şeması tanım dili (XSD) şema doğrulamasını kullanarak bir XML belgesini doğrulamaz. Yalnızca XML belgesinin düzgün biçimlendirildiğini doğrular.  
  
 Bir XML belgesini doğrulamaya yönelik ilk yol, bir <xref:System.Xml.XmlDocument> nesnesine bir doğrulama <xref:System.Xml.XmlReader> nesnesi kullanılarak yüklendiği için belgeyi doğrulamaktır. İkinci yöntem, <xref:System.Xml.XmlDocument> sınıfının <xref:System.Xml.XmlDocument.Validate%2A> yöntemini kullanarak daha önce türsüz bir XML belgesini doğrulamaktır. Her iki durumda da, doğrulanan XML belgesinde yapılan değişiklikler <xref:System.Xml.XmlDocument> sınıfının <xref:System.Xml.XmlDocument.Validate%2A> yöntemi kullanılarak yeniden doğrulanabilir.  
  
### <a name="validating-a-document-as-it-is-loaded"></a>Belge yüklendiği için doğrulanıyor  
 Bir <xref:System.Xml.XmlReaderSettings> nesnesi, bir <xref:System.Xml.XmlReaderSettings> nesnesini parametre olarak alan <xref:System.Xml.XmlReader> sınıfının <xref:System.Xml.XmlReader.Create%2A> yöntemine geçirerek bir doğrulama <xref:System.Xml.XmlReader> nesnesi oluşturulur. Parametre olarak geçirilen <xref:System.Xml.XmlReaderSettings> nesnesi, <xref:System.Xml.XmlReaderSettings.Schemas%2A> özelliğine eklenen <xref:System.Xml.XmlDocument> nesnesindeki XML belgesi için `Schema` ve bir XML şemasına ayarlanmış bir <xref:System.Xml.XmlReaderSettings.ValidationType%2A> özelliğine sahiptir. Doğrulama <xref:System.Xml.XmlReader> nesnesi daha sonra <xref:System.Xml.XmlDocument> nesnesini oluşturmak için kullanılır.  
  
 Aşağıdaki örnek, bir doğrulama <xref:System.Xml.XmlReader> nesnesi kullanarak <xref:System.Xml.XmlDocument> nesnesini oluşturarak <xref:System.Xml.XmlDocument> nesnesine yüklendiği için `contosoBooks.xml` dosyasını doğrular. XML belgesi şemasına göre geçerli olduğundan, şema doğrulama hataları veya uyarılar oluşturulmaz.  
  
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
  
 Örnek, `contosoBooks.xml` dosyasını girdi olarak alır.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Örnek ayrıca `contosoBooks.xsd` giriş olarak alır.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 Yukarıdaki örnekte, herhangi bir öznitelik veya öğe türü, doğrulama şemasında belirtilen ilgili türle eşleşmezse <xref:System.Xml.XmlDocument.Load%2A> çağrıldığında bir <xref:System.Xml.Schema.XmlSchemaValidationException> atılır. Doğrulama <xref:System.Xml.XmlReader>bir <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> ayarlandıysa, geçersiz bir tür ile karşılaşıldığında <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> çağrılır.  
  
 <xref:System.Xml.XPath.XPathNavigator>tarafından `invalid` olarak ayarlanan <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> bir özniteliğe veya öğeye erişildiğinde <xref:System.Xml.Schema.XmlSchemaException> oluşur.  
  
 <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> özelliği, bir öznitelik veya öğenin, <xref:System.Xml.XPath.XPathNavigator>özniteliklere veya öğelerine erişirken geçerli olup olmadığını anlamak için kullanılabilir.  
  
> [!NOTE]
> Bir XML belgesi, varsayılan değerleri tanımlayan ilişkili bir şemaya sahip bir <xref:System.Xml.XmlDocument> nesnesine yüklendiğinde, <xref:System.Xml.XmlDocument> nesnesi bu Varsayılanları XML belgesinde görünmiş gibi davranır. Bu, <xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> özelliğinin her zaman, XML belgesinde boş bir öğe olarak yazılmış olsa bile, varsayılan olarak şemadan alınan bir öğe için `false` döndürdüğü anlamına gelir.  
  
### <a name="validating-a-document-using-the-validate-method"></a>Validate metodunu kullanarak bir belgeyi doğrulama  
 <xref:System.Xml.XmlDocument> sınıfının <xref:System.Xml.XmlDocument.Validate%2A> yöntemi, <xref:System.Xml.XmlDocument> nesnesinin <xref:System.Xml.XmlDocument.Schemas%2A> özelliğinde belirtilen şemalara karşı bir <xref:System.Xml.XmlDocument> nesnesinde bulunan XML belgesini doğrular ve bilgi kümesi genişletmesini gerçekleştirir. Sonuç olarak, <xref:System.Xml.XmlDocument> nesnesindeki daha önce türsüz bir XML belgesi, türü belirlenmiş bir belgeyle değiştirilmiştir.  
  
 <xref:System.Xml.XmlDocument> nesnesi, <xref:System.Xml.XmlDocument.Validate%2A> yöntemine parametre olarak geçirilen <xref:System.Xml.Schema.ValidationEventHandler> temsilcisini kullanarak şema doğrulama hatalarını ve uyarılarını raporlar.  
  
 Aşağıdaki örnek, <xref:System.Xml.XmlDocument> nesnesinin <xref:System.Xml.XmlDocument.Schemas%2A> özelliğinde bulunan `contosoBooks.xsd` şemasına karşı <xref:System.Xml.XmlDocument> nesnesinde bulunan `contosoBooks.xml` dosyasını doğrular.  
  
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
  
 Örnek, `contosoBooks.xml` dosyasını girdi olarak alır.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Örnek ayrıca `contosoBooks.xsd` giriş olarak alır.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
### <a name="validating-modifications"></a>Değişiklikler doğrulanıyor  
 Bir XML belgesinde değişiklikler yapıldıktan sonra, <xref:System.Xml.XmlDocument> sınıfının <xref:System.Xml.XmlDocument.Validate%2A> yöntemini kullanarak XML belgesi şemasına karşı değişiklikleri doğrulayabilirsiniz.  
  
 Aşağıdaki örnek, bir doğrulama <xref:System.Xml.XmlReader> nesnesi kullanarak <xref:System.Xml.XmlDocument> nesnesini oluşturarak <xref:System.Xml.XmlDocument> nesnesine yüklendiği için `contosoBooks.xml` dosyasını doğrular. XML belgesi, şema doğrulama hataları veya uyarılar üretilmeden yüklendiğinden başarıyla doğrulanacaktır. Örnek daha sonra, `contosoBooks.xsd` şemasına göre geçersiz olan XML belgesinde iki değişiklik yapar. İlk değişiklik, bir şema doğrulama hatasına neden olan geçersiz bir alt öğe ekliyor ve ikinci değişiklik, bir özel duruma neden olan düğümün türüne göre geçersiz bir değere sahip bir değer olarak belirlenmiş bir değerin değerini ayarlıyor.  
  
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
  
 Örnek, `contosoBooks.xml` dosyasını girdi olarak alır.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Örnek ayrıca `contosoBooks.xsd` giriş olarak alır.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 Yukarıdaki örnekte, <xref:System.Xml.XmlDocument> nesnesinde bulunan XML belgesinde iki değişiklik yapılmıştır. XML belgesi yüklendiğinde, karşılaşılan tüm şema doğrulama hataları doğrulama olay işleyicisi yöntemi tarafından işlenirdi ve konsola yazılır.  
  
 Bu örnekte, doğrulama hataları XML belgesi yüklendikten sonra ve <xref:System.Xml.XmlDocument> sınıfının <xref:System.Xml.XmlDocument.Validate%2A> yöntemi kullanılarak bulunduktan sonra tanıtılmıştı.  
  
 <xref:System.Xml.XPath.XPathNavigator> sınıfının <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> yöntemi kullanılarak yapılan değişiklikler, yeni değer düğümün şema türüne göre geçersiz olduğu için bir <xref:System.InvalidCastException> sonuçlandı.  
  
 <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> yöntemi kullanılarak değerleri değiştirme hakkında daha fazla bilgi için, bkz. [XPathNavigator kullanarak XML verilerini değiştirme](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) konusu.  
  
### <a name="read-only-validation"></a>Salt okuma doğrulaması  
 <xref:System.Xml.XPath.XPathDocument> sınıfı, bir XML belgesinin Salt okunabilir, bellek içi gösterimidir. Hem <xref:System.Xml.XPath.XPathDocument> sınıfı hem de <xref:System.Xml.XmlDocument> sınıfı, XML belgelerini gezinmek ve düzenlemek için <xref:System.Xml.XPath.XPathNavigator> nesneler oluşturur. <xref:System.Xml.XPath.XPathDocument> sınıfı salt okunurdur bir sınıf olduğundan, <xref:System.Xml.XPath.XPathDocument> nesnelerinden döndürülen <xref:System.Xml.XPath.XPathNavigator> nesne <xref:System.Xml.XPath.XPathDocument> nesnesindeki XML belgesini düzenleyemez.  
  
 Doğrulama durumunda, bu konunun önceki kısımlarında açıklandığı gibi, doğrulama <xref:System.Xml.XmlReader> nesnesini kullanarak bir <xref:System.Xml.XmlDocument> nesnesi oluşturduğunuz gibi <xref:System.Xml.XPath.XPathDocument> bir nesne oluşturabilirsiniz. <xref:System.Xml.XPath.XPathDocument> nesnesi, yüklendiği gibi XML belgesini doğrular, ancak <xref:System.Xml.XPath.XPathDocument> nesnesindeki XML verilerini düzenleyemediğinden XML belgesini yeniden doğrulayamazsınız.  
  
 Salt okunurdur ve düzenlenebilir <xref:System.Xml.XPath.XPathNavigator> nesneler hakkında daha fazla bilgi için, [XPathDocument ve XmlDocument kullanarak XML verilerini okuma](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md) konusunun bölümüne bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [XPathDocument ve XmlDocument Kullanarak XML Verilerini Okuma](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)
- [XPathNavigator Kullanarak XML Verileri Seçme, Değerlendirme ve Eşleştirme](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
- [XPathNavigator Kullanarak XML Verilerine Erişme](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)
- [XPathNavigator Kullanarak XML Verilerini Düzenleme](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)
