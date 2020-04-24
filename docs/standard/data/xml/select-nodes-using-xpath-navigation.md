---
title: XPath Gezintisi Kullanarak Düğüm Seçme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 8e4450dc-56b3-472b-b467-32f5694f83ad
ms.openlocfilehash: 58f1487486c2802a2c64b51afcecb01c76dd291a
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78155613"
---
# <a name="select-nodes-using-xpath-navigation"></a>XPath Gezintisi Kullanarak Düğüm Seçme
XML Belge Nesne Modeli (DOM), DOM 'daki sorgu bilgilerini kullanarak XML yol dili (XPath) gezintisini kullanmanıza imkan tanıyan yöntemler içerir. XPath 'i tek, belirli bir düğüm bulmak veya bazı ölçütlerle eşleşen tüm düğümleri bulmak için kullanabilirsiniz.  
  
## <a name="xpath-select-methods"></a>XPath seçme yöntemleri  
 DOM sınıfları XPath seçimi için iki yöntem sağlar: <xref:System.Xml.XmlNode.SelectSingleNode%2A> yöntemi ve <xref:System.Xml.XmlNode.SelectNodes%2A> yöntemi. <xref:System.Xml.XmlNode.SelectSingleNode%2A> Yöntemi, seçim ölçütleriyle eşleşen ilk düğümü döndürür. <xref:System.Xml.XmlNode.SelectNodes%2A> Yöntemi, eşleşen düğümleri <xref:System.Xml.XmlNodeList> içeren bir döndürür.  
  
 Aşağıdaki örnek, yazarın en <xref:System.Xml.XmlNode.SelectSingleNode%2A> son adının belirtilen ölçütlere uyan `book` ilk düğümü seçmek için yöntemini kullanır. Bu konunun sonunda belirtilen kitaplığı. xml dosyası, giriş dosyası olarak kullanılır.  
  
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
  
 Sonraki örnekte, fiyatın belirtilen <xref:System.Xml.XmlNode.SelectNodes%2A> miktardan daha büyük olduğu tüm kitap düğümlerini seçmek için yöntemi kullanılmaktadır. Seçili listedeki her bir kitabın fiyatı, daha sonra program aracılığıyla yüzde on oranında azaltılır. Son olarak, güncelleştirilmiş dosya konsola yazılır. Bu konunun sonunda belirtilen kitaplığı. xml dosyası, giriş dosyası olarak kullanılır.  
  
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
  
 Yukarıdaki örneklerde, belge öğesinde XPath sorgusu başlatılır. XPath sorgusu için başlangıç noktası ayarlandığında, XPath sorgusunun başlangıç noktası olan bağlam düğümü ayarlanır. Belge öğesinde başlamak istemiyorsanız, ancak belge öğesinin ilk alt öğesinden başlamak istiyorsanız, SELECT ifadesini aşağıdaki gibi kodlayın:  
  
```vb  
doc.DocumentElement.FirstChild.SelectNodes(. . . )  
```  
  
```csharp  
this doc.DocumentElement.FirstChild.SelectNodes(. . .);  
```  
  
 Tüm <xref:System.Xml.XmlNodeList> nesneler, temel alınan belgeyle eşitlenir. Bu nedenle, düğüm listesini yineleyebilir ve bir düğümün değerini değiştirirseniz bu düğüm, geldiği belgede de güncelleştirilir. Önceki örnekte, bir düğüm seçili <xref:System.Xml.XmlNodeList> olarak değiştirildiğinde, temel alınan belgede de değişiklik yapıldığında dikkat edin.  
  
> [!NOTE]
> Temel alınan belge değiştirildiğinde, seçimi yeniden çalıştırmanız önerilir. Değiştirilen düğüm, düğüm listesine daha önce olmadığında veya düğüm listesinden kaldırılmasına neden olacak şekilde, düğüm listesinin artık doğru olduğundan emin olmak için bir değer olarak değiştirilmiştir.  
  
## <a name="namespaces-in-xpath-expressions"></a>XPath Ifadelerinde ad alanları  
 XPath ifadeleri ad alanı içerebilir. Ad alanı çözümlemesi, <xref:System.Xml.XmlNamespaceManager>kullanılarak desteklenir. XPath ifadesi bir ön ek içeriyorsa, önek ve ad alanı <xref:System.Xml.XmlNamespaceManager>URI çiftinin öğesine eklenmelidir ve, <xref:System.Xml.XmlNamespaceManager> <xref:System.Xml.XmlNode.SelectNodes%28System.String%2CSystem.Xml.XmlNamespaceManager%29> veya <xref:System.Xml.XmlNode.SelectSingleNode%28System.String%2CSystem.Xml.XmlNamespaceManager%29> yöntemine geçirilir. Yukarıdaki kod örneklerinin, <xref:System.Xml.XmlNamespaceManager> kitaplığı. xml belgesinin ad alanını çözümlemek için öğesini kullandığına dikkat edin.  
  
> [!NOTE]
> XPath ifadesi bir ön ek içermiyorsa, ad alanı Tekdüzen Kaynak tanımlayıcısı 'nın (URI) boş ad alanı olduğu varsayılır. XML 'niz bir varsayılan ad alanı içeriyorsa, yine de bir ön ek ve ad alanı URI 'SI eklemeniz <xref:System.Xml.XmlNamespaceManager>gerekir. Aksi takdirde hiçbir düğüm seçilmeyecektir.  
  
#### <a name="input-file"></a>Giriş Dosyası  
 Aşağıda, bu konudaki örneklerde bulunan giriş dosyası olarak kullanılan kitaplığı. xml dosyası verilmiştir:  
  
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
