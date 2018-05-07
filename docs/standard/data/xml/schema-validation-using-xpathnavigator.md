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
---
# <a name="schema-validation-using-xpathnavigator"></a>XPathNavigator kullanarak şema doğrulaması
Kullanarak <xref:System.Xml.XmlDocument> sınıfı, bulunan XML içeriği doğrulamak bir <xref:System.Xml.XmlDocument> iki yolla nesnesi. Bir doğrulama kullanarak XML içeriği doğrulamak için ilk yoludur <xref:System.Xml.XmlReader> nesne ve ikinci yol kullanmaktır <xref:System.Xml.XmlDocument.Validate%2A> yöntemi <xref:System.Xml.XmlDocument> sınıfı. XML kullanarak içeriğin salt okunur doğrulama de gerçekleştirebilirsiniz <xref:System.Xml.XPath.XPathDocument> sınıfı.  
  
## <a name="validating-xml-data"></a>XML verileri doğrulama  
 <xref:System.Xml.XmlDocument> Sınıfı DTD veya XML Şeması Tanım Dili (XSD) şema doğrulaması varsayılan olarak kullanarak bir XML belgesi doğrulamaz. Yalnızca XML belgesi doğru biçimlendirildiğinden emin doğrular.  
  
 Bir XML belgesi doğrulamak için ilk belge içine yüklenmiş olarak doğrulamak için yoludur bir <xref:System.Xml.XmlDocument> bir doğrulama kullanarak nesne <xref:System.Xml.XmlReader> nesne. Daha önce türü belirsiz XML belge kullanarak bir doğrulamak için ikinci yoludur <xref:System.Xml.XmlDocument.Validate%2A> yöntemi <xref:System.Xml.XmlDocument> sınıfı. Her iki durumda da doğrulanmış XML belgeye yapılan değişiklikler kullanarak yeniden doğrulanır <xref:System.Xml.XmlDocument.Validate%2A> yöntemi <xref:System.Xml.XmlDocument> sınıfı.  
  
### <a name="validating-a-document-as-it-is-loaded"></a>Bir belgeyle doğrulama yüklendi  
 Bir doğrulama <xref:System.Xml.XmlReader> nesne geçirerek oluşturulur bir <xref:System.Xml.XmlReaderSettings> nesnesini <xref:System.Xml.XmlReader.Create%2A> yöntemi <xref:System.Xml.XmlReader> geçen sınıfı bir <xref:System.Xml.XmlReaderSettings> nesnesini parametre olarak. <xref:System.Xml.XmlReaderSettings> Nesnesi geçirildi bir parametre içeriyor gibi bir <xref:System.Xml.XmlReaderSettings.ValidationType%2A> özelliğini `Schema` ve XML Şeması bulunan XML belgesi için bir <xref:System.Xml.XmlDocument> eklenen nesne kendi <xref:System.Xml.XmlReaderSettings.Schemas%2A> özelliği. Doğrulama <xref:System.Xml.XmlReader> nesnesi oluşturmak için kullanılan sonra <xref:System.Xml.XmlDocument> nesnesi.  
  
 Aşağıdaki örnek doğrular `contosoBooks.xml` dosya içine yüklenmiş gibi <xref:System.Xml.XmlDocument> oluşturarak nesne <xref:System.Xml.XmlDocument> bir doğrulama kullanarak nesne <xref:System.Xml.XmlReader> nesne. XML belgesi, şemaya göre geçerli olduğundan, hiçbir şema doğrulama hatalarıyla veya uyarıları üretilir.  
  
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
  
 Örnek alır `contosoBooks.xml` dosyayı bir girdi olarak.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Bu örnek ayrıca alır `contosoBooks.xsd` bir girdi olarak.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 Yukarıdaki örnekte, bir <xref:System.Xml.Schema.XmlSchemaValidationException> olduğunda oluşturulur <xref:System.Xml.XmlDocument.Load%2A> herhangi bir öznitelik veya öğe türü doğrulama şemasında belirtilen karşılık gelen türü eşleşmiyorsa olarak adlandırılır. Varsa bir <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> doğrulama üzerinde ayarlanır <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> geçersiz bir tür karşılaşıldığında çağrılmadığı.  
  
 Bir <xref:System.Xml.Schema.XmlSchemaException> bir öznitelik veya öğeyle durum <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> kümesine `invalid` tarafından erişilen <xref:System.Xml.XPath.XPathNavigator>.  
  
 <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> Özelliği, bir tek özniteliği veya öğenin öznitelikleri veya öğeleriyle erişirken geçerli olup olmadığını belirlemek için kullanılabilir <xref:System.Xml.XPath.XPathNavigator>.  
  
> [!NOTE]
>  Ne zaman bir XML belgesi yüklendiği içine bir <xref:System.Xml.XmlDocument> varsayılan değerleri tanımlayan bir ilişkili şema nesnesiyle <xref:System.Xml.XmlDocument> nesne XML belgesinde göründüğü gibi bu varsayılan değerlendirir. Bunun anlamı <xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> özelliği her zaman döndürür `false` XML belgesinde boş bir öğe olarak yazılmış olsa bile, şema, varsayılan bir öğe için.  
  
### <a name="validating-a-document-using-the-validate-method"></a>Doğrulama yöntemini kullanarak bir belge doğrulanıyor  
 <xref:System.Xml.XmlDocument.Validate%2A> Yöntemi <xref:System.Xml.XmlDocument> sınıfı doğrular bulunan XML belgesi bir <xref:System.Xml.XmlDocument> belirtilen şemaları nesneyle <xref:System.Xml.XmlDocument> nesnenin <xref:System.Xml.XmlDocument.Schemas%2A> özelliği ve bilgi augmentation'a gerçekleştirir. Daha önce türü belirsiz XML belgesinde sonucudur <xref:System.Xml.XmlDocument> nesne türü belirtilmiş bir belgeyle değiştirildi.  
  
 <xref:System.Xml.XmlDocument> Nesne, şema doğrulama hataları ve Uyarıları kullanarak raporları <xref:System.Xml.Schema.ValidationEventHandler> temsilci geçirilen parametre olarak <xref:System.Xml.XmlDocument.Validate%2A> yöntemi.  
  
 Aşağıdaki örnek doğrular `contosoBooks.xml` içinde yer alan dosya <xref:System.Xml.XmlDocument> karşı nesne `contosoBooks.xsd` içinde yer alan şema <xref:System.Xml.XmlDocument> nesnenin <xref:System.Xml.XmlDocument.Schemas%2A> özelliği.  
  
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
  
 Örnek alır `contosoBooks.xml` dosyayı bir girdi olarak.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Bu örnek ayrıca alır `contosoBooks.xsd` bir girdi olarak.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
### <a name="validating-modifications"></a>Değişiklikler doğrulanıyor  
 Bir XML belgesi değişiklikler yapıldıktan sonra XML belge kullanan bir şemaya karşı değişiklikleri doğrulamak için <xref:System.Xml.XmlDocument.Validate%2A> yöntemi <xref:System.Xml.XmlDocument> sınıfı.  
  
 Aşağıdaki örnek doğrular `contosoBooks.xml` dosya içine yüklenmiş gibi <xref:System.Xml.XmlDocument> oluşturarak nesne <xref:System.Xml.XmlDocument> bir doğrulama kullanarak nesne <xref:System.Xml.XmlReader> nesne. Herhangi bir şema doğrulama hatalarıyla veya uyarıları oluşturmadan yüklendi olarak XML belgesi başarıyla doğrulandı. Örnek sonra göre geçersiz olan iki XML belgesi değişiklikleri yapar `contosoBooks.xsd` şema. İlk değişikliği bir şeması doğrulama hatası kaynaklanan geçersiz bir alt öğesi ekler ve ikinci değişikliği bir özel durum kaynaklanan düğüm türüne göre geçersiz bir değere belirtilmiş bir düğüm değerini ayarlar.  
  
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
  
 Örnek alır `contosoBooks.xml` dosyayı bir girdi olarak.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Bu örnek ayrıca alır `contosoBooks.xsd` bir girdi olarak.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 Yukarıdaki örnekte, iki değişiklikler bulunan XML belgesi yapılan <xref:System.Xml.XmlDocument> nesnesi. XML belgesi yüklendi olarak karşılaşılan şema doğrulama hataları alınan doğrulama olay işleyicisi yöntemi tarafından işlenen ve konsola yazılmış.  
  
 Bu örnekte, XML belgesi yüklendi ve kullanarak bulundu sonra doğrulama hatalarını sunulan <xref:System.Xml.XmlDocument.Validate%2A> yöntemi <xref:System.Xml.XmlDocument> sınıfı.  
  
 Kullanılarak yapılan değişiklikler <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> yöntemi <xref:System.Xml.XPath.XPathNavigator> sınıfı sonuçlandı bir <xref:System.InvalidCastException> yeni değer göre düğümünün şema türü geçersiz olduğundan.  
  
 Kullanarak değerlerini değiştirme hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> yöntemi, bkz: [XML XPathNavigator kullanarak verileri değiştirme](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) konu.  
  
### <a name="read-only-validation"></a>Salt okunur doğrulama  
 <xref:System.Xml.XPath.XPathDocument> Sınıfı, bir XML belgesi salt okunur, bellek içi bir gösterimi. Her iki <xref:System.Xml.XPath.XPathDocument> sınıfı ve <xref:System.Xml.XmlDocument> sınıfı oluşturmak <xref:System.Xml.XPath.XPathNavigator> nesneleri sayfasına gidin ve XML belgelerini düzenleyin. Çünkü <xref:System.Xml.XPath.XPathDocument> sınıftır bir salt okunur, <xref:System.Xml.XPath.XPathNavigator> nesnesi döndürülen <xref:System.Xml.XPath.XPathDocument> nesneleri bulunan XML belgesi düzenleme <xref:System.Xml.XPath.XPathDocument> nesnesi.  
  
 Doğrulama söz konusu olduğunda, oluşturduğunuz bir <xref:System.Xml.XPath.XPathDocument> oluşturduğunuz gibi nesne bir <xref:System.Xml.XmlDocument> bir doğrulama kullanarak nesne <xref:System.Xml.XmlReader> nesne bu konunun önceki kısımlarında açıklandığı gibi. <xref:System.Xml.XPath.XPathDocument> Nesneyi doğrular XML belgesi olarak yüklendiği ancak XML verilerinde düzenleyemediğiniz <xref:System.Xml.XPath.XPathDocument> nesnesi, XML belgesi düzeltin olamaz.  
  
 Salt okunur ve düzenlenebilir hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator> nesneleri bkz [XPathDocument ve XmlDocument kullanarak XML veri okunurken](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md) konu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [XPath Veri Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [XPathDocument ve XmlDocument Kullanarak XML Verilerini Okuma](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)  
 [XPathNavigator Kullanarak XML Verileri Seçme, Değerlendirme ve Eşleştirme](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)  
 [XPathNavigator Kullanarak XML Verilerine Erişme](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 [XPathNavigator Kullanarak XML Verilerini Düzenleme](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)
