---
title: XML Verilerine Nesne Hiyerarşisi Eşleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 450e350b-6a68-4634-a2a5-33f4dc33baf0
ms.openlocfilehash: 642a7e5321d0150865f74a66a811914bc9f5d21d
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160033"
---
# <a name="mapping-the-object-hierarchy-to-xml-data"></a>XML Verilerine Nesne Hiyerarşisi Eşleme
Bir XML belgesi bellekte olduğunda, kavramsal temsil bir ağaç olur. Programlama için ağacın düğümlerine erişmek üzere bir nesne hiyerarşiniz vardır. Aşağıdaki örnek, XML içeriğinin düğüm haline geldiğini gösterir.  
  
 XML, XML Belge Nesne Modeli (DOM) olarak okunduğu için parçalar düğümlere çevrilir ve bu düğümler kendi düğüm türleri ve değerleri gibi, kendileri hakkındaki ek meta verileri korurlar. Düğüm türü nesnesidir ve hangi eylemlerin gerçekleştirilebileceğini ve hangi özelliklerin ayarlanamayacağını veya alınamayacağını belirler.  
  
 Aşağıdaki basit XML 'e sahipseniz:  
  
 **Girdi**  
  
```xml  
<book>  
    <title>The Handmaid's Tale</title>  
</book>  
```  
  
 Giriş, atanan düğüm türü özelliği ile aşağıdaki düğüm ağacı olarak bellekte temsil edilir:  
  
 ![örnek düğüm ağacı](../../../../docs/standard/data/xml/media/simple-xml.gif "Simple_XML")  
Kitap ve başlık düğümü ağaç gösterimi  
  
 `book` öğesi bir **XmlElement** nesnesi olur, bir next öğesi `title`bir **XmlElement**olur, ancak element içeriği bir **XmlText** nesnesi haline gelir. **XmlElement** yöntemlerine ve özelliklerine bakarak, Yöntemler ve özellikler, **XmlText** nesnesinde bulunan yöntemlerden ve özelliklerden farklıdır. Bu nedenle, XML biçimlendirmesinin hangi düğüm türünde olacağını bilmek, düğüm türü gerçekleştirilebilecek eylemleri belirlediği için çok önemlidir.  
  
 Aşağıdaki örnek, XML verilerinde okur ve düğüm türüne bağlı olarak farklı metin yazar. Aşağıdaki XML veri dosyasını input, **Items. xml**olarak kullanma:  
  
 **Girdi**  
  
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
  
 Aşağıdaki kod örneği **Items. xml** dosyasını okur ve her düğüm türü için bilgileri görüntüler.  
  
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
  
 Örneğin çıktısı, verilerin düğüm türlerine eşlenmesinin ortaya çıkar.  
  
 **Çıktı**  
  
```xml  
<?xml version='1.0'?><!--This is a sample XML document --><!DOCTYPE Items [<!ENTITY number "123">]<Items><Item>Test with an entity: 123</Item><Item>test with a child element <more> stuff</Item><Item>test with a CDATA section <![CDATA[<456>]]> def</Item><Item>Test with a char entity: A</Item><--Fourteen chars in this element.--><Item>1234567890ABCD</Item></Items>  
```  
  
 Girişi bir kerede tek bir satıra götürdüğünde ve koddan oluşturulan çıktıyı kullanarak, hangi düğüm testinin çıktı satırlarını üretdiğini analiz etmek için aşağıdaki tabloyu kullanabilirsiniz. böylece, hangi XML verilerinin ne tür düğüm türünde olduğunu anlayabilirsiniz.  
  
|Girdi|Çıktı|Düğüm türü testi|  
|-----------|------------|--------------------|  
|\<? XML Version = "1.0"? >|\<? XML sürümü = ' 1.0 '? >|XmlNodeType. Xmlbildirimi|  
|Bu örnek bir XML belgesi olan \<!--. >|Bu örnek bir XML belgesi olan \<!--. >|XmlNodeType. Comment|  
|\<! DOCTYPE öğeleri [\<! VARLıK numarası "123" >] >|\<! DOCTYPE öğeleri [\<! VARLıK numarası "123" >]|XmlNodeType. DocumentType|  
|Öğeleri \<>|Öğeleri \<>|XmlNodeType. element|  
|Öğe > \<|Öğe > \<|XmlNodeType. element|  
|Bir varlıkla test edin: &number;|Bir varlıkla test: 123|XmlNodeType.Text|  
|\</Item >|\</Item >|XmlNodeType.EndElement|  
|Öğe > \<|Öğe > \<|XmNodeType. element|  
|alt öğe ile test etme|alt öğe ile test etme|XmlNodeType.Text|  
|\<daha >|\<daha >|XmlNodeType. element|  
|Çocuk|Çocuk|XmlNodeType.Text|  
|\</Item >|\</Item >|XmlNodeType.EndElement|  
|Öğe > \<|Öğe > \<|XmlNodeType. element|  
|CDATA bölümüyle test etme|CDATA bölümüyle test etme|XmlTest. Text|  
|<! [CDATA [\<456 >]]\>|<! [CDATA [\<456 >]]\>|XmlTest. CDATA|  
|def|def|XmlNodeType.Text|  
|\</Item >|\</Item >|XmlNodeType.EndElement|  
|Öğe > \<|Öğe > \<|XmlNodeType. element|  
|Bir Char varlığıyla test edin: &\#65;|Bir Char varlığı ile test: A|XmlNodeType.Text|  
|\</Item >|\</Item >|XmlNodeType.EndElement|  
|Bu öğedeki on dört karakter!--\<.-->|\<--bu öğedeki on dört karakter.-->|XmlNodeType. Comment|  
|Öğe > \<|Öğe > \<|XmlNodeType. element|  
|1234567890ABCD|1234567890ABCD|XmlNodeType.Text|  
|\</Item >|\</Item >|XmlNodeType.EndElement|  
|\</Items >|\</Items >|XmlNodeType.EndElement|  
  
 Düğüm türü ne tür eylemlerin geçerli olduğunu ve ne tür özellikleri ayarlayabileceğinizi ve alabildiğinizi kontrol etmek için hangi düğüm türünün atandığını bilmeniz gerekir.  
  
 Veriler DOM 'a **PreserveWhitespace** bayrağıyla yüklendiğinde, boşluk için düğüm oluşturma denetlenir. Daha fazla bilgi için bkz. [Dom yüklenirken beyaz boşluk ve önemli boşluk işleme](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).  
  
 DOM 'a yeni düğümler eklemek için bkz. [XML belgesine düğüm ekleme](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md). DOM 'dan düğüm kaldırmak için bkz. [BIR XML belgesinden düğümleri, içeriği ve değerleri kaldırma](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md). DOM 'daki düğümlerin içeriğini değiştirmek için bkz. [BIR XML belgesindeki düğümleri, içeriği ve değerleri değiştirme](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
