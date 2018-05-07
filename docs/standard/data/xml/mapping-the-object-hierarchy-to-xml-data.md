---
title: XML verilerine nesne hiyerarşisi eşleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 450e350b-6a68-4634-a2a5-33f4dc33baf0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 45f39701d409ba76e3c3f428f484b6fd5e538fbe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="mapping-the-object-hierarchy-to-xml-data"></a>XML verilerine nesne hiyerarşisi eşleme
Bir XML belgesi bellekte kavramsal temsili bir ağaç olur. Programlama için ağaç düğümleri erişmek için bir nesne hiyerarşisi vardır. Aşağıdaki örnekte nasıl XML içeriği düğümleri duruma gösterir.  
  
 XML XML belge nesne modeli (DOM) içine okurken parçaları düğümlerin içine dönüştürülür ve bu düğümler, düğüm türü ve değerleri gibi kendileri hakkında ek meta veriler korumak. Düğüm türü, nesne ve hangi eylemleri gerçekleştirilebilir belirler ve hangi özelliklerin ayarlayın veya alınır.  
  
 Aşağıdaki basit XML varsa:  
  
 **Giriş**  
  
```xml  
<book>  
    <title>The Handmaid's Tale</title>  
</book>  
```  
  
 Giriş bellekte atanan düğüm türü özelliği aşağıdaki düğüm ağacıyla olarak temsil edilir:  
  
 ![örnek düğüm ağacı](../../../../docs/standard/data/xml/media/simple-xml.gif "Simple_XML")  
Kitap ve başlık düğümü ağaç gösterimi  
  
 `book` Öğe haline gelir bir **XmlElement** nesnesi, sonraki öğeye `title`, haline bir **XmlElement**, öğe içeriği olurken bir **XmlText** nesnesi. Bakarak içinde **XmlElement** yöntemleri ve özellikleri, yöntemleri ve özellikleri yöntemleri ve özellikleri kullanılabilir farklı bir **XmlText** nesnesi. Bu nedenle gerçekleştirilecek eylemler düğüm türünü belirleyen XML Biçimlendirme hale hangi düğüm türü önemlidir bilerek.  
  
 Aşağıdaki örnekte, XML verileri okur ve düğüm türüne bağlı olarak farklı bir metin çıkışı yazar. Girdi olarak şu XML veri dosyası kullanarak **items.xml**:  
  
 **Giriş**  
  
```xml  
<?xml version="1.0"?>  
<!-- This is a sample XML document -->  
<!DOCTYPE Items [<!ENTITY number "123">]>  
<Items>  
  <Item>Test with an entity: &number;</Item>  
  <Item>test with a child element <more/> stuff</Item>  
  <Item>test with a CDATA section <![CDATA[<456>]]> def</Item>  
  <Item>Test with a char entity: A</Item>  
  <!-- Fourteen chars in this element.-->  
  <Item>1234567890ABCD</Item>  
</Items>  
```  
  
 Aşağıdaki kod örneği okuma **items.xml** dosya ve her düğüm türünün bilgilerini görüntüler.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
    Private Const filename As String = "items.xml"  
  
    Public Shared Sub Main()  
  
        Dim reader As XmlTextReader = Nothing  
  
        Try  
            ' Load the reader with the data file and   
            'ignore all white space nodes.   
            reader = New XmlTextReader(filename)  
            reader.WhitespaceHandling = WhitespaceHandling.None  
  
            ' Parse the file and display each of the nodes.  
            While reader.Read()  
                Select Case reader.NodeType  
                    Case XmlNodeType.Element  
                        Console.Write("<{0}>", reader.Name)  
                    Case XmlNodeType.Text  
                        Console.Write(reader.Value)  
                    Case XmlNodeType.CDATA  
                        Console.Write("<![CDATA[{0}]]>", reader.Value)  
                    Case XmlNodeType.ProcessingInstruction  
                        Console.Write("<?{0} {1}?>", reader.Name, reader.Value)  
                    Case XmlNodeType.Comment  
                        Console.Write("<!--{0}-->", reader.Value)  
                    Case XmlNodeType.XmlDeclaration  
                        Console.Write("<?xml version='1.0'?>")  
                    Case XmlNodeType.Document  
                    Case XmlNodeType.DocumentType  
                        Console.Write("<!DOCTYPE {0} [{1}]", reader.Name, reader.Value)  
                    Case XmlNodeType.EntityReference  
                        Console.Write(reader.Name)  
                    Case XmlNodeType.EndElement  
                        Console.Write("</{0}>", reader.Name)  
                End Select  
            End While  
  
        Finally  
            If Not (reader Is Nothing) Then  
                reader.Close()  
            End If  
        End Try  
    End Sub 'Main ' End class  
End Class 'Sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
    private const String filename = "items.xml";  
  
    public static void Main()  
    {  
        XmlTextReader reader = null;  
  
        try  
        {  
            // Load the reader with the data file and ignore   
            // all white space nodes.  
            reader = new XmlTextReader(filename);  
            reader.WhitespaceHandling = WhitespaceHandling.None;  
  
            // Parse the file and display each of the nodes.  
            while (reader.Read())  
            {  
                switch (reader.NodeType)  
                {  
                    case XmlNodeType.Element:  
                        Console.Write("<{0}>", reader.Name);  
                        break;  
                    case XmlNodeType.Text:  
                        Console.Write(reader.Value);  
                        break;  
                    case XmlNodeType.CDATA:  
                        Console.Write("<![CDATA[{0}]]>", reader.Value);  
                        break;  
                    case XmlNodeType.ProcessingInstruction:  
                        Console.Write("<?{0} {1}?>", reader.Name, reader.Value);  
                        break;  
                    case XmlNodeType.Comment:  
                        Console.Write("<!--{0}-->", reader.Value);  
                        break;  
                    case XmlNodeType.XmlDeclaration:  
                        Console.Write("<?xml version='1.0'?>");  
                        break;  
                    case XmlNodeType.Document:  
                        break;  
                    case XmlNodeType.DocumentType:  
                        Console.Write("<!DOCTYPE {0} [{1}]", reader.Name, reader.Value);  
                        break;  
                    case XmlNodeType.EntityReference:  
                        Console.Write(reader.Name);  
                        break;  
                    case XmlNodeType.EndElement:  
                        Console.Write("</{0}>", reader.Name);  
                        break;  
                }  
            }  
        }  
  
        finally  
        {  
            if (reader != null)  
                reader.Close();  
        }  
    }  
} // End class  
```  
  
 Örneğin çıktısını düğüm türleri için verilerin eşleşmesini ortaya çıkarır.  
  
 **Output**  
  
```xml  
<?xml version='1.0'?><!--This is a sample XML document --><!DOCTYPE Items [<!ENTITY number "123">]<Items><Item>Test with an entity: 123</Item><Item>test with a child element <more> stuff</Item><Item>test with a CDATA section <![CDATA[<456>]]> def</Item><Item>Test with a char entity: A</Item><--Fourteen chars in this element.--><Item>1234567890ABCD</Item></Items>  
```  
  
 Aynı anda tek bir giriş çizgi alma ve koddan oluşturulan çıktı kullanarak, böylece XML verileri ne tür bir düğüm türü hale geldiğini anlamak hangi düğümü test çıkışı, hangi satırların üretilen çözümlemek için aşağıdaki tabloda kullanabilirsiniz.  
  
|Giriş|Çıkış|Düğüm türü sınaması|  
|-----------|------------|--------------------|  
|\<? xml version = "1.0"? >|\<? xml sürümü ='1.0 '? >|XmlNodeType.XmlDeclaration|  
|\<!--Örnek bir XML belgesi budur-->|\<!--Örnek bir XML belgesi budur-->|XmlNodeType.Comment|  
|\<! DOCTYPE öğeleri [\<! Varlık numarası "123" >] >|\<! DOCTYPE öğeleri [\<! Varlık numarası "123" >]|XmlNodeType.DocumentType|  
|\<Öğeleri >|\<Öğeleri >|XmlNodeType.Element|  
|\<Öğe >|\<Öğe >|XmlNodeType.Element|  
|Bir varlık ile test edin: &number;|Bir varlığı olan test: 123|XmlNodeType.Text|  
|\</ Öğesi >|\</ Öğesi >|XmlNodeType.EndElement|  
|\<Öğe >|\<Öğe >|XmNodeType.Element|  
|bir alt öğesi ile test|bir alt öğesi ile test|XmlNodeType.Text|  
|\<Daha fazla >|\<Daha fazla >|XmlNodeType.Element|  
|Hizmetler|Hizmetler|XmlNodeType.Text|  
|\</ Öğesi >|\</ Öğesi >|XmlNodeType.EndElement|  
|\<Öğe >|\<Öğe >|XmlNodeType.Element|  
|CDATA bölümü ile test|CDATA bölümü ile test|XmlTest.Text|  
|&LT;! [CDATA [\<456 &GT;]]\>|&LT;! [CDATA [\<456 &GT;]]\>|XmlTest.CDATA|  
|def|def|XmlNodeType.Text|  
|\</ Öğesi >|\</ Öğesi >|XmlNodeType.EndElement|  
|\<Öğe >|\<Öğe >|XmlNodeType.Element|  
|Char varlığı ile test: &\#65;|Char varlığı ile test: A|XmlNodeType.Text|  
|\</ Öğesi >|\</ Öğesi >|XmlNodeType.EndElement|  
|\<!----> On dört karakter bu öğesi.|\<--Bu öğe. on dört karakter-->|XmlNodeType.Comment|  
|\<Öğe >|\<Öğe >|XmlNodeType.Element|  
|1234567890ABCD|1234567890ABCD|XmlNodeType.Text|  
|\</ Öğesi >|\</ Öğesi >|XmlNodeType.EndElement|  
|\</ Öğeleri >|\</ Öğeleri >|XmlNodeType.EndElement|  
  
 Düğüm türü atanmış bilmeniz gerekir, hangi tür Eylemler geçerli olduğunu ve ne tür bir ayarlamak ve almak özellikleri düğüm olarak türü denetler.  
  
 Boşluk düğüm oluşturma, veri tarafından DOM içine yüklendiğinde denetlenir **PreserveWhitespace** bayrağı. Daha fazla bilgi için bkz: [boşluk ve önemli boşluk DOM yüklenirken işleme](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).  
  
 DOM yeni düğümler eklemek için bkz: [ekleme düğümlerin bir XML belgesi içine](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md). DOM düğümleri kaldırmak için bkz: [düğümleri kaldırma, içerik ve bir XML belgesi değerlerinden](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md). DOM düğümler içeriğini değiştirmek için bkz: [değiştirme düğümleri, içerik ve bir XML belgesi değerleri](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
