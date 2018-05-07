---
title: XPath Gezinti kullanarak düğümleri seçin
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 8e4450dc-56b3-472b-b467-32f5694f83ad
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8c5a7b9113dd5a4de929f5b88569be89bc1f2c89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="select-nodes-using-xpath-navigation"></a>XPath Gezinti kullanarak düğümleri seçin
XML belge nesne modeli (DOM) sorgu bilgileri XML Path dili (XPath) gezinme DOM kullanmanıza olanak sağlayan yöntemler içerir XPath tek, belirli bir düğümü bulunamadı veya bazı ölçütlere uyan tüm düğümleri bulmak için kullanabilirsiniz.  
  
## <a name="xpath-select-methods"></a>XPath seçin yöntemleri  
 DOM sınıflar XPath seçimi için iki yöntem sunar: <xref:System.Xml.XmlNode.SelectSingleNode%2A> yöntemi ve <xref:System.Xml.XmlNode.SelectNodes%2A> yöntemi. <xref:System.Xml.XmlNode.SelectSingleNode%2A> Yöntemi seçim ölçütleriyle eşleşen ilk düğümü döndürür. <xref:System.Xml.XmlNode.SelectNodes%2A> Yöntemi döndürür bir <xref:System.Xml.XmlNodeList> eşleşen düğümleri içerir.  
  
 Aşağıdaki örnek kullanır <xref:System.Xml.XmlNode.SelectSingleNode%2A> ilk seçmek için yöntemi `book` yazarın soyadı belirtilen ölçütleri karşılayan düğümü. (Bu konunun sonunda sağlanır) bookstore.xml dosyasını giriş dosyası olarak kullanılır.  
  
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
  
 Sonraki örnek kullanır <xref:System.Xml.XmlNode.SelectNodes%2A> yöntemi fiyat olduğu belirtilen miktardan büyük defter düğümleri seçin. Seçilen listede her kitap fiyatını program aracılığıyla on oranında azalır. Son olarak, güncelleştirilmiş dosya konsoluna yazılır. (Bu konunun sonunda sağlanır) bookstore.xml dosyasını giriş dosyası olarak kullanılır.  
  
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
  
 Yukarıdaki örneklerde belge öğesi XPath sorgusu başlatın. XPath için başlangıç noktası ayarlama sorgu XPath sorgusu için başlangıç noktasıdır bağlam düğümü ayarlar. Belge öğede başlatmak istiyor musunuz, ancak belgeyi öğesinin ilk alt başlatmak istediğiniz, select deyiminde aşağıdaki gibi kod:  
  
```vb  
doc.DocumentElement.FirstChild.SelectNodes(. . . )  
```  
  
```csharp  
this doc.DocumentElement.FirstChild.SelectNodes(. . .);  
```  
  
 Tüm <xref:System.Xml.XmlNodeList> nesneleri temel alınan belgenin ile eşitlenir. Bu nedenle, düğüm listesinden yinelemek ve bir düğüm değeri değiştirirseniz, o düğümü de geldiğini belge güncelleştirilir. Önceki örnekte dikkat edin, bir düğüm değiştirildiği seçili <xref:System.Xml.XmlNodeList> temel belge de değiştirilir.  
  
> [!NOTE]
>  Temel alınan belge değiştirildiğinde, select yeniden önerilir. Değiştirilen düğümü önceden değildi veya şimdi düğümü listeden kaldırılacak neden düğümü listeye eklenecek düğüm neden olabilecek bir ise, düğüm listesinden doğru olduğunu garanti yoktur.  
  
## <a name="namespaces-in-xpath-expressions"></a>XPath ifadelerinde ad alanları  
 XPath ifadeleri ad alanları içerebilir. Namespace çözümleme kullanarak desteklenir <xref:System.Xml.XmlNamespaceManager>. XPath ifadesi bir önek içeriyorsa, önek ve ad alanı URI çifti eklenmeli <xref:System.Xml.XmlNamespaceManager>ve <xref:System.Xml.XmlNamespaceManager> geçirilir <xref:System.Xml.XmlNode.SelectNodes%28System.String%2CSystem.Xml.XmlNamespaceManager%29> veya <xref:System.Xml.XmlNode.SelectSingleNode%28System.String%2CSystem.Xml.XmlNamespaceManager%29> yöntemi. Yukarıdaki kod örnekleri kullanır bildirimi <xref:System.Xml.XmlNamespaceManager> bookstore.xml belge ad alanı çözümlemek için.  
  
> [!NOTE]
>  XPath ifadesi bir önek içermiyorsa Tekdüzen Kaynak Tanımlayıcısı (URI) ad alanı boş ad alanı olduğu varsayılır. Varsayılan ad alanı, XML içeriyorsa, hala bir öneki ve ad alanı URI'si eklemelisiniz için <xref:System.Xml.XmlNamespaceManager>; Aksi halde, düğüm seçilir.  
  
#### <a name="input-file"></a>Giriş Dosyası  
 Bu konudaki örnekler giriş dosya olarak kullanılan bookstore.xml dosya verilmiştir:  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
