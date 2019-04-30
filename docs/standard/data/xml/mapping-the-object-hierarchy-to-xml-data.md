---
title: XML Verilerine Nesne Hiyerarşisi Eşleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 450e350b-6a68-4634-a2a5-33f4dc33baf0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1808121049c6344b72b1c9d99e19c46422dfa0c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61650287"
---
# <a name="mapping-the-object-hierarchy-to-xml-data"></a>XML Verilerine Nesne Hiyerarşisi Eşleme
Bir XML belgesi bellekte olduğunda, kavramsal bir ağaç gösterimidir. Programlama için ağaç düğümleri erişmek için bir nesne hiyerarşisine sahip. Aşağıdaki örnek nasıl düğümleri XML içeriği haline gelir gösterir.  
  
 XML XML belge nesne modeli (DOM) içine okunduğu gibi parçaları düğümlere çevrilir ve bu düğümler, düğüm türü ve değerleri gibi kendileri hakkında ek meta veriler korur. Düğüm türü, nesne ve hangi işlemler gerçekleştirilebilir belirler ve hangi özellikleri ayarlamak veya alınır.  
  
 Aşağıdaki basit XML varsa:  
  
 **Giriş**  
  
```xml  
<book>  
    <title>The Handmaid's Tale</title>  
</book>  
```  
  
 Giriş bellekte aşağıdaki düğüm ağacı atanan düğüm türü özelliği ile gösterilir:  
  
 ![örnek düğüm ağacı](../../../../docs/standard/data/xml/media/simple-xml.gif "Simple_XML")  
Kitap ve başlık düğüm ağacı gösterimi  
  
 `book` Öğesi olur bir **XmlElement** nesnesi, sonraki öğeye `title`, ayrıca olur bir **XmlElement**, öğe içerik olurken bir **XmlText** nesne. Bakarak içinde **XmlElement** yöntemleri ve özellikleri, yöntemleri ve özellikleri yöntemleri ve özellikleri kullanılabilir daha farklı bir **XmlText** nesne. Bu nedenle kendi düğüm türü gerçekleştirilecek işlemleri belirleyen XML işaretlemesini haline gelir hangi düğüm türü önemlidir bilerek.  
  
 Aşağıdaki örnek, XML verileri okur ve düğüm türüne bağlı olarak farklı metin yazar. Giriş olarak aşağıdaki XML veri dosyasını kullanarak **items.xml**:  
  
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
  
 Aşağıdaki kod örneği okuma **items.xml** dosya ve her düğüm türü bilgilerini görüntüler.  
  
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
  
 Örnekteki çıktının eşleme düğüm türleri verileri ortaya çıkarır.  
  
 **Output**  
  
```xml  
<?xml version='1.0'?><!--This is a sample XML document --><!DOCTYPE Items [<!ENTITY number "123">]<Items><Item>Test with an entity: 123</Item><Item>test with a child element <more> stuff</Item><Item>test with a CDATA section <![CDATA[<456>]]> def</Item><Item>Test with a char entity: A</Item><--Fourteen chars in this element.--><Item>1234567890ABCD</Item></Items>  
```  
  
 Aynı anda tek giriş satırı alma ve koddan oluşturulan çıktı kullanarak, hangi düğüm sınaması çıktı satırları oluşturulan XML verileri ne tür bir düğüm türü hale geldi. böylece anlama analiz etmek için aşağıdaki tabloyu kullanın.  
  
|Giriş|Çıkış|Düğüm türü Test|  
|-----------|------------|--------------------|  
|\<? xml version = "1.0"? >|\<? xml version ='1.0 '? >|XmlNodeType.XmlDeclaration|  
|\<!--Bu örnek bir XML belgesi,-->|\<!--Bu örnek bir XML belgesi,-->|XmlNodeType.Comment|  
|\<! DOCTYPE öğeleri [\<! Varlık numarası "123" >] >|\<! DOCTYPE öğeleri [\<! Varlık numarası "123" >]|XmlNodeType.DocumentType|  
|\<Öğeler >|\<Öğeler >|XmlNodeType.Element|  
|\<Öğesi >|\<Öğesi >|XmlNodeType.Element|  
|Bir varlık ile test edin: &number;|Bir varlık ile test edin: 123|XmlNodeType.Text|  
|\</ Öğesi >|\</ Öğesi >|XmlNodeType.EndElement|  
|\<Öğesi >|\<Öğesi >|XmNodeType.Element|  
|bir alt öğesi ile test|bir alt öğesi ile test|XmlNodeType.Text|  
|\<Daha fazla >|\<Daha fazla >|XmlNodeType.Element|  
|öğe|öğe|XmlNodeType.Text|  
|\</ Öğesi >|\</ Öğesi >|XmlNodeType.EndElement|  
|\<Öğesi >|\<Öğesi >|XmlNodeType.Element|  
|CDATA bölümü ile test|CDATA bölümü ile test|XmlTest.Text|  
|&LT;! [CDATA [\<456 &GT;]]\>|&LT;! [CDATA [\<456 &GT;]]\>|XmlTest.CDATA|  
|def|def|XmlNodeType.Text|  
|\</ Öğesi >|\</ Öğesi >|XmlNodeType.EndElement|  
|\<Öğesi >|\<Öğesi >|XmlNodeType.Element|  
|Char varlığı ile test: &\#65;|Bir karakter varlık ile test edin: BİR|XmlNodeType.Text|  
|\</ Öğesi >|\</ Öğesi >|XmlNodeType.EndElement|  
|\<!--Bu öğe. on dört karakter-->|\<--Bu öğe. on dört karakter-->|XmlNodeType.Comment|  
|\<Öğesi >|\<Öğesi >|XmlNodeType.Element|  
|1234567890ABCD|1234567890ABCD|XmlNodeType.Text|  
|\</ Öğesi >|\</ Öğesi >|XmlNodeType.EndElement|  
|\</ Öğeler >|\</ Öğeler >|XmlNodeType.EndElement|  
  
 Düğüm türüne atanan bilmeniz gerekir, düğüm olarak türü Eylemler ne tür geçerli olduğunu ve ne tür bir ayarlayın ve alma özellikleri denetler.  
  
 Boşluk düğüm oluşturma, verileri içine DOM tarafından yüklendiğinde denetlenir **PreserveWhitespace** bayrağı. Daha fazla bilgi için [boşluk ve önemli boşluk DOM yüklerken işleme](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).  
  
 DOM'da yeni düğümler eklemek için bkz [bir XML belgesine düğüm ekleme](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md). DOM'dan düğümleri kaldırma için bkz: [düğümleri kaldırma, içerik ve değerleri XML belgesinden](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md). DOM düğümleri içeriğini değiştirmek için bkz: [değiştirme düğümleri, içeriği ve değerleri bir XML belgesi](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
