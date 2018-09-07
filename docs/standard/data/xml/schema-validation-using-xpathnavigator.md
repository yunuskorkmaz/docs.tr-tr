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
ms.openlocfilehash: d2b04006c46edb29fd4fe05e63224220ed1876af
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44085283"
---
# <a name="schema-validation-using-xpathnavigator"></a>XPathNavigator kullanarak şema doğrulama
Kullanarak <xref:System.Xml.XmlDocument> sınıfı, içerdiği XML içeriği doğrulamak bir <xref:System.Xml.XmlDocument> iki yolla nesne. Bir doğrulama kullanarak XML içeriği doğrulamak için ilk yoludur <xref:System.Xml.XmlReader> nesne ve ikinci yol ise <xref:System.Xml.XmlDocument.Validate%2A> yöntemi <xref:System.Xml.XmlDocument> sınıfı. XML kullanarak içeriğin salt okunur doğrulama de gerçekleştirebilirsiniz <xref:System.Xml.XPath.XPathDocument> sınıfı.  
  
## <a name="validating-xml-data"></a>XML verileri doğrulama  
 <xref:System.Xml.XmlDocument> Sınıfı, varsayılan olarak bir DTD'nin veya XML Şeması Tanım Dili (XSD) şeması doğrulama kullanarak bir XML belgesi doğrulamaz. Yalnızca XML belgesi biçimlendirilmemiş doğrular.  
  
 Yüklenen olarak belgeyi doğrulamak için bir XML belgesi doğrulamak için ilk yol olduğu bir <xref:System.Xml.XmlDocument> bir doğrulama kullanarak nesne <xref:System.Xml.XmlReader> nesne. Daha önce yazılmamış bir XML belgesi kullanarak doğrulamak için ikinci yoludur <xref:System.Xml.XmlDocument.Validate%2A> yöntemi <xref:System.Xml.XmlDocument> sınıfı. Her iki durumda da doğrulanmış XML belgeye yapılan değişiklikler kullanarak yeniden doğrulanır <xref:System.Xml.XmlDocument.Validate%2A> yöntemi <xref:System.Xml.XmlDocument> sınıfı.  
  
### <a name="validating-a-document-as-it-is-loaded"></a>Bir belge olarak doğrulama yüklendi  
 Bir doğrulama <xref:System.Xml.XmlReader> nesnesi geçirerek oluşturulur bir <xref:System.Xml.XmlReaderSettings> nesnesini <xref:System.Xml.XmlReader.Create%2A> yöntemi <xref:System.Xml.XmlReader> alan sınıfı bir <xref:System.Xml.XmlReaderSettings> bir parametre olarak nesne. <xref:System.Xml.XmlReaderSettings> Nesnesi, bir parametre olarak geçirilen bir <xref:System.Xml.XmlReaderSettings.ValidationType%2A> özelliğini `Schema` ve yer alan XML belgesi için XML şeması bir <xref:System.Xml.XmlDocument> eklenen nesnenin kendi <xref:System.Xml.XmlReaderSettings.Schemas%2A> özelliği. Doğrulama <xref:System.Xml.XmlReader> nesne oluşturmak için kullanılan ardından <xref:System.Xml.XmlDocument> nesne.  
  
 Aşağıdaki örnek doğrular `contosoBooks.xml` dosya içine yüklü <xref:System.Xml.XmlDocument> nesne oluşturarak <xref:System.Xml.XmlDocument> bir doğrulama kullanarak nesne <xref:System.Xml.XmlReader> nesne. XML belgesi şemasına göre geçerli olduğundan, hiçbir şema doğrulama hataları veya uyarıları üretilir.  
  
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
  
 Örnek alan `contosoBooks.xml` girdi olarak dosya.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Bu örnek ayrıca alır `contosoBooks.xsd` girdi olarak.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 Yukarıdaki örnekte, bir <xref:System.Xml.Schema.XmlSchemaValidationException> ne zaman oluşturulur <xref:System.Xml.XmlDocument.Load%2A> herhangi bir öznitelik veya öğenin türü doğrulama şemasında belirtilen karşılık gelen türü eşleşmiyorsa çağrılır. Varsa bir <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> doğrulama ayarlanır <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> geçersiz bir türe karşılaşıldığında adlı.  
  
 Bir <xref:System.Xml.Schema.XmlSchemaException> bir öznitelik veya öğenin sahip olduğunda oluşturulur <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> kümesine `invalid` tarafından erişilen <xref:System.Xml.XPath.XPathNavigator>.  
  
 <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> Özelliği, bir tek öznitelik veya öğenin öznitelikleri veya öğelerin erişirken geçerli olup olmadığını belirlemek için kullanılabilir <xref:System.Xml.XPath.XPathNavigator>.  
  
> [!NOTE]
>  Ne zaman bir XML belgesi yüklendiği içine bir <xref:System.Xml.XmlDocument> varsayılan değerlerini tanımlayan ilişkili bir şeması ile nesne <xref:System.Xml.XmlDocument> nesne bu varsayılan XML belgesinde göründüğü gibi davranır. Diğer bir deyişle <xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> özelliği her zaman döndürür `false` XML belgesinde boş bir öğe olarak yazılmış olsa bile şemadan varsayılan bir öğe için.  
  
### <a name="validating-a-document-using-the-validate-method"></a>Doğrulama yöntemini kullanarak bir belge doğrulanıyor  
 <xref:System.Xml.XmlDocument.Validate%2A> Yöntemi <xref:System.Xml.XmlDocument> sınıfı doğrular yer alan XML belgesi bir <xref:System.Xml.XmlDocument> nesne belirtilen şemaları karşı <xref:System.Xml.XmlDocument> nesnenin <xref:System.Xml.XmlDocument.Schemas%2A> özelliği ve sonrası bilgi kümesi güçlendirme gerçekleştirir. Daha önce yazılmamış bir XML belgesinde sonucudur <xref:System.Xml.XmlDocument> nesne türü belirtilmiş bir belge ile değiştirildi.  
  
 <xref:System.Xml.XmlDocument> Nesnesi şema doğrulama hataları ve Uyarıları kullanarak raporları <xref:System.Xml.Schema.ValidationEventHandler> temsilci geçirilen bir parametre olarak <xref:System.Xml.XmlDocument.Validate%2A> yöntemi.  
  
 Aşağıdaki örnek doğrular `contosoBooks.xml` bulunan dosya <xref:System.Xml.XmlDocument> karşı nesne `contosoBooks.xsd` içindeki şeması <xref:System.Xml.XmlDocument> nesnenin <xref:System.Xml.XmlDocument.Schemas%2A> özelliği.  
  
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
  
 Örnek alan `contosoBooks.xml` girdi olarak dosya.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Bu örnek ayrıca alır `contosoBooks.xsd` girdi olarak.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
### <a name="validating-modifications"></a>Değişiklikleri doğrulanıyor  
 Bir XML belgesine değişiklikler yapıldıktan sonra değişikliklerin kullanarak XML belgesi için şemaya karşı doğrulayabilir <xref:System.Xml.XmlDocument.Validate%2A> yöntemi <xref:System.Xml.XmlDocument> sınıfı.  
  
 Aşağıdaki örnek doğrular `contosoBooks.xml` dosya içine yüklü <xref:System.Xml.XmlDocument> nesne oluşturarak <xref:System.Xml.XmlDocument> bir doğrulama kullanarak nesne <xref:System.Xml.XmlReader> nesne. XML belgesi yüklü herhangi bir şema doğrulama hataları veya uyarıları oluşturmadan başarıyla doğrulandı. Örnek daha sonra göre geçersiz XML belgesi için iki değişiklik yapar `contosoBooks.xsd` şema. İlk değişiklik bir şeması doğrulama hatası kaynaklanan geçersiz bir alt öğesi ekler ve ikinci değişiklik kaynaklanan bir özel durum düğüm türüne göre geçersiz bir değer türü belirtilmiş bir düğümün değerini ayarlar.  
  
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
  
 Örnek alan `contosoBooks.xml` girdi olarak dosya.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Bu örnek ayrıca alır `contosoBooks.xsd` girdi olarak.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 Yukarıdaki örnekte yer alan XML belgesi iki değişiklik yapılmadan <xref:System.Xml.XmlDocument> nesne. XML belgesi yüklendi olarak karşılaşılan şema doğrulama hataları alınan doğrulama olay işleyicisi yöntemi tarafından işlenen ve konsoluna yazılan.  
  
 Bu örnekte, XML belgesi yüklendi ve kullanılarak bulunan sonra doğrulama hatalarını tanıtılan <xref:System.Xml.XmlDocument.Validate%2A> yöntemi <xref:System.Xml.XmlDocument> sınıfı.  
  
 Kullanarak yapılan değişiklikleri <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> yöntemi <xref:System.Xml.XPath.XPathNavigator> sınıfı sonuçlandı bir <xref:System.InvalidCastException> yeni değeri düğümün şema türüne göre geçersiz olduğundan.  
  
 Kullanarak değerleri değiştirme hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> yöntemi bkz [değiştirme XPathNavigator kullanarak XML verilerini](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) konu.  
  
### <a name="read-only-validation"></a>Salt okunur doğrulama  
 <xref:System.Xml.XPath.XPathDocument> Sınıfı, bir XML belgesi salt okunur, bellek içi bir temsili. Her iki <xref:System.Xml.XPath.XPathDocument> sınıfı ve <xref:System.Xml.XmlDocument> sınıfı oluşturma <xref:System.Xml.XPath.XPathNavigator> gidin ve XML belge düzenleme nesneleri. Çünkü <xref:System.Xml.XPath.XPathDocument> salt okunur sınıfı <xref:System.Xml.XPath.XPathNavigator> nesnesi döndürülen <xref:System.Xml.XPath.XPathDocument> nesneleri yer alan XML belgesi düzenlemek <xref:System.Xml.XPath.XPathDocument> nesne.  
  
 Doğrulama söz konusu olduğunda, oluşturduğunuz bir <xref:System.Xml.XPath.XPathDocument> oluşturduğunuz gibi nesne bir <xref:System.Xml.XmlDocument> bir doğrulama kullanarak nesne <xref:System.Xml.XmlReader> nesne bu konunun önceki kısımlarında açıklandığı gibi. <xref:System.Xml.XPath.XPathDocument> Nesneyi doğrular XML belgesi yüklü olduğu gibi ancak XML verilerinde düzenleyemediğiniz <xref:System.Xml.XPath.XPathDocument> nesnesi, XML belgesi düzeltin olamaz.  
  
 Salt okunur ve düzenlenebilir hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator> nesneleri bkz [XPathDocument ve XmlDocument kullanarak XML verileri okuma](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md) konu.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [XPathDocument ve XmlDocument Kullanarak XML Verilerini Okuma](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)  
- [XPathNavigator Kullanarak XML Verileri Seçme, Değerlendirme ve Eşleştirme](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)  
- [XPathNavigator Kullanarak XML Verilerine Erişme](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
- [XPathNavigator Kullanarak XML Verilerini Düzenleme](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)
