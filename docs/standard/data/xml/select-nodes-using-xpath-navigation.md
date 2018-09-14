---
title: XPath gezintisi kullanarak düğüm seçme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 8e4450dc-56b3-472b-b467-32f5694f83ad
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9e02dd304893e4d9354144c5b412dfd145161c6e
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45596955"
---
# <a name="select-nodes-using-xpath-navigation"></a>XPath gezintisi kullanarak düğüm seçme
XML belge nesne modeli (DOM) DOM'da XML Path Language (XPath) sorgusu bilgi gitme kullanmanıza olanak sağlayan yöntemler içerir. XPath tek, belirli bir düğümü bulunamadı veya bazı ölçütleri ile eşleşen tüm düğümleri bulmak için kullanabilirsiniz.  
  
## <a name="xpath-select-methods"></a>XPath seçin yöntemleri  
 DOM sınıfları XPath seçimine için iki yöntem sunar: <xref:System.Xml.XmlNode.SelectSingleNode%2A> yöntemi ve <xref:System.Xml.XmlNode.SelectNodes%2A> yöntemi. <xref:System.Xml.XmlNode.SelectSingleNode%2A> Seçim ölçütleriyle eşleşen ilk düğümü yöntemi döndürür. <xref:System.Xml.XmlNode.SelectNodes%2A> Yöntemi döndürür bir <xref:System.Xml.XmlNodeList> , eşleşen düğümleri içerir.  
  
 Aşağıdaki örnekte <xref:System.Xml.XmlNode.SelectSingleNode%2A> ilk seçmek için `book` son yazarın adı belirtilen ölçütleri karşılayan düğümü. Bu konunun sonunda sağlanır) bookstore.xml dosyasını (giriş dosyası olarak kullanılır.  
  
```vb  
Dim doc As New XmlDocument()  
doc.Load("bookstore.xml")  
Dim root As XmlNode = doc.DocumentElement  
  
' Add the namespace.  
Dim nsmgr As New XmlNamespaceManager(doc.NameTable)  
nsmgr.AddNamespace("bk", "urn:newbooks-schema")  
  
' Select and display the first node in which the author's   
' last name is Kingsolver.  
Dim node As XmlNode = root.SelectSingleNode( _  
     "descendant::bk:book[bk:author/bk:last-name='Kingsolver']", nsmgr)  
Console.WriteLine(node.InnerXml)  
```  
  
```csharp  
// Load the document and set the root element.  
XmlDocument doc = new XmlDocument();  
doc.Load("bookstore.xml");  
XmlNode root = doc.DocumentElement;  
  
// Add the namespace.  
XmlNamespaceManager nsmgr = new XmlNamespaceManager(doc.NameTable);  
nsmgr.AddNamespace("bk", "urn:newbooks-schema");  
  
// Select and display the first node in which the author's   
// last name is Kingsolver.  
XmlNode node = root.SelectSingleNode(  
    "descendant::bk:book[bk:author/bk:last-name='Kingsolver']", nsmgr);  
Console.WriteLine(node.InnerXml);  
```  
  
 Sonraki örnekte <xref:System.Xml.XmlNode.SelectNodes%2A> fiyat olduğu belirtilen miktardan daha fazla kitap düğümleri seçmek için yöntemi. Seçili listedeki her bir kitabın fiyatı, on oranında programlı olarak azaltılır. Son olarak, güncelleştirilmiş dosyayı konsoluna yazılır. Bu konunun sonunda sağlanır) bookstore.xml dosyasını (giriş dosyası olarak kullanılır.  
  
```vb  
' Load the document and set the root element.  
Dim doc As New XmlDocument()  
doc.Load("bookstore.xml")  
Dim root As XmlNode = doc.DocumentElement  
  
' Add the namespace.  
Dim nsmgr As New XmlNamespaceManager(doc.NameTable)  
nsmgr.AddNamespace("bk", "urn:newbooks-schema")  
  
' Select all nodes where the book price is greater than 10.00.  
Dim nodeList As XmlNodeList = root.SelectNodes( _  
     "descendant::bk:book[bk:price>10.00]", nsmgr)  
For Each book As XmlNode In nodeList  
     Dim price As Double  
     price = Math.Round(Convert.ToSingle( _  
          book.LastChild.InnerText) * 0.9, 2)  
     book.LastChild.InnerText = price.ToString()  
Next  
  
' Display the updated document.  
doc.Save(Console.Out)  
```  
  
```csharp  
// Load the document and set the root element.  
XmlDocument doc = new XmlDocument();  
doc.Load("bookstore.xml");  
XmlNode root = doc.DocumentElement;  
  
// Add the namespace.  
XmlNamespaceManager nsmgr = new XmlNamespaceManager(doc.NameTable);  
nsmgr.AddNamespace("bk", "urn:newbooks-schema");  
  
// Select all nodes where the book price is greater than 10.00.  
XmlNodeList nodeList = root.SelectNodes(  
     "descendant::bk:book[bk:price>10.00]", nsmgr);  
foreach (XmlNode book in nodeList)  
{  
     // Discount prices by 10%.  
     double price;  
     price = Math.Round(Convert.ToSingle(  
          book.LastChild.InnerText) * 0.9, 2);  
     book.LastChild.InnerText = price.ToString();  
}  
  
// Display the updated document.  
doc.Save(Console.Out);  
```  
  
 Yukarıdaki örneklerde, belge öğesi XPath sorgusu başlatın. XPath için başlangıç noktası ayarı sorgu XPath sorgusu için başlangıç noktası olan bağlam düğümünün ayarlar. Belge öğesi başlatmak istiyor musunuz, ancak belge öğesi ilk alt başlamak istiyorsanız, select deyimini aşağıdaki şekilde kod yazabilirsiniz:  
  
```vb  
doc.DocumentElement.FirstChild.SelectNodes(. . . )  
```  
  
```csharp  
this doc.DocumentElement.FirstChild.SelectNodes(. . .);  
```  
  
 Tüm <xref:System.Xml.XmlNodeList> nesneler, temel alınan belge ile eşitlenir. Bu nedenle, düğüm listesini yineleme yapmak ve bir düğümün değerini değiştirebilir, düğüm de nereden geldiğini belge güncelleştirilir. Önceki örnekte bildirimi, bir düğüm değiştirildiğinde seçili <xref:System.Xml.XmlNodeList> temel alınan belge de değiştirilir.  
  
> [!NOTE]
>  Temel alınan belge değiştirildiğinde seçin yeniden çalıştırmak için önerilir. Daha önce değildi veya artık düğümü listeden kaldırılacak neden düğüm listesine eklenecek düğüm neden olabilecek bir değişiklik düğümü ise, düğüm listesini doğru olduğunu garantisi yoktur.  
  
## <a name="namespaces-in-xpath-expressions"></a>XPath ifadeleri ad alanları  
 XPath ifadeleri ad alanları içerebilir. Namespace çözümleme kullanarak desteklenen <xref:System.Xml.XmlNamespaceManager>. XPath ifadesi bir önek varsa, önek ve ad alanı URI çifti eklenmelidir <xref:System.Xml.XmlNamespaceManager>ve <xref:System.Xml.XmlNamespaceManager> geçirilir <xref:System.Xml.XmlNode.SelectNodes%28System.String%2CSystem.Xml.XmlNamespaceManager%29> veya <xref:System.Xml.XmlNode.SelectSingleNode%28System.String%2CSystem.Xml.XmlNamespaceManager%29> yöntemi. Yukarıdaki kod örnekleri kullanma bildirimi <xref:System.Xml.XmlNamespaceManager> bookstore.xml belgenin ad alanı çözümlenecek.  
  
> [!NOTE]
>  XPath ifadesi bir önek yoksa, ad alanı Tekdüzen Kaynak Tanımlayıcısı (URI) boş ad alanı olduğu varsayılır. XML dosyanızı varsayılan ad alanı varsa, yine de bir önek ve ad alanı URI eklemelisiniz için <xref:System.Xml.XmlNamespaceManager>; Aksi takdirde, düğüm seçilir.  
  
#### <a name="input-file"></a>Giriş Dosyası  
 Bu konudaki örneklerde giriş dosyası olarak kullanılan bookstore.xml dosyası aşağıda verilmiştir:  
  
```xml  
<?xml version='1.0'?>  
<bookstore xmlns="urn:newbooks-schema">  
  <book genre="novel" style="hardcover">  
    <title>The Handmaid's Tale</title>  
    <author>  
      <first-name>Margaret</first-name>  
      <last-name>Atwood</last-name>  
    </author>  
    <price>19.95</price>  
  </book>  
  <book genre="novel" style="other">  
    <title>The Poisonwood Bible</title>  
    <author>  
      <first-name>Barbara</first-name>  
      <last-name>Kingsolver</last-name>  
    </author>  
    <price>11.99</price>  
  </book>  
  <book genre="novel" style="paperback">  
    <title>The Bean Trees</title>  
    <author>  
      <first-name>Barbara</first-name>  
      <last-name>Kingsolver</last-name>  
    </author>  
    <price>5.99</price>  
  </book>  
</bookstore>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
