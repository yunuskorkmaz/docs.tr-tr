---
title: DOM öğeleri için yeni öznitelikler oluşturma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: dd6dc920-b011-418a-b3db-f1580a7d9251
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 870e800220031338557792fa612d4a3101e79f90
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45675567"
---
# <a name="creating-new-attributes-for-elements-in-the-dom"></a>DOM öğeleri için yeni öznitelikler oluşturma
Yeni öznitelikler oluşturma öznitelikleri düğümler, ancak bir öğe düğümü özellikleridir ve içerdiği diğer düğüm türleri oluşturmaktan daha farklı bir **XmlAttributeCollection** öğeyle ilişkili. Bir öznitelik oluşturun ve öğe eklemek için birden çok yolu vardır:  
  
-   Öğe düğümü edinin ve kullanın **SetAttribute** o öğenin özniteliği koleksiyona bir öznitelik eklemek için.  
  
-   Oluşturma bir **XmlAttribute** düğümü kullanan **CreateAttribute** yöntemi, öğe düğümü alın ve ardından kullanmak **SetAttributeNode** bu öznitelik koleksiyon düğümü eklemek için öğe.  
  
 Aşağıdaki örnek, bir öznitelik kullanarak bir öğe ekleme işlemi gösterilmektedir **SetAttribute** yöntemi.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
public class Sample  
  
  public shared sub Main()  
  
  Dim doc as XmlDocument = new XmlDocument()  
  doc.LoadXml("<book xmlns:bk='urn:samples' bk:ISBN='1-861001-57-5'>" & _  
              "<title>Pride And Prejudice</title>" & _  
              "</book>")  
  Dim root as XmlElement = doc.DocumentElement  
  
  'Add a new attribute.  
  root.SetAttribute("genre", "urn:samples", "novel")  
  
  Console.WriteLine("Display the modified XML...")  
  Console.WriteLine(doc.InnerXml)  
  
  end sub  
end class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
  public static void Main()  
  {  
    XmlDocument doc = new XmlDocument();  
    doc.LoadXml("<book xmlns:bk='urn:samples' bk:ISBN='1-861001-57-5'>" +  
                "<title>Pride And Prejudice</title>" +  
                "</book>");  
    XmlElement root = doc.DocumentElement;  
  
    // Add a new attribute.  
    root.SetAttribute("genre", "urn:samples", "novel");  
  
    Console.WriteLine("Display the modified XML...");  
    Console.WriteLine(doc.InnerXml);  
  }  
```  
  
 Aşağıdaki örnek yeni bir gösterir kullanarak oluşturulan öznitelik **CreateAttribute** yöntemi. Daha sonra bir öznitelik koleksiyonu için eklenen öznitelik gösterir **kitap** öğesini kullanarak **SetAttributeNode** yöntemi.  
  
 Aşağıdaki XML verilen:  
  
```xml  
<book genre='novel' ISBN='1-861001-57-5'>  
<title>Pride And Prejudice</title>  
</book>  
```  
  
 Yeni bir öznitelik oluşturun ve bir değer verin:  
  
```vb  
Dim attr As XmlAttribute = doc.CreateAttribute("publisher")  
   attr.Value = "WorldWide Publishing"  
```  
  
```csharp  
XmlAttribute attr = doc.CreateAttribute("publisher");  
attr.Value = "WorldWide Publishing";  
```  
  
 ve öğesine ekleyin:  
  
```vb  
doc.DocumentElement.SetAttributeNode(attr)  
```  
  
```csharp  
doc.DocumentElement.SetAttributeNode(attr);  
```  
  
 **Output**  
  
```xml  
<book genre="novel" ISBN="1-861001-57-5" publisher="WorldWide Publishing">  
<title>Pride And Prejudice</title>  
</book>  
```  
  
 Tam kod örneği şu yolda bulunabilir: <xref:System.Xml.XmlDocument.CreateAttribute%2A>.  
  
 Oluşturabilirsiniz bir **XmlAttribute** düğüm ve kullanım **Insertbefore** veya **InsertAfter** yöntemleri bir koleksiyon içinde uygun konuma yerleştirin. Aynı ada sahip bir öznitelik mevcut öznitelik koleksiyonda zaten varsa **XmlAttribute** koleksiyon ve yeni düğüm kaldırılır **XmlAttribute** düğümüne eklenir. Bu aynı şekilde gerçekleştirir **SetAttribute** yöntemi. Var olan bir düğüm yapmak için bir başvuru noktası olarak bir parametre olarak bu yöntemleri ele **Insertbefore** ve **InsertAfter**. Bir başvuru düğümü yeni düğümü için varsayılan ekleneceği konum gösteren sağlayamazsanız **InsertAfter** yöntemdir koleksiyonu başında yeni düğümü eklemek için. İçin varsayılan konum **Insertbefore**, hiçbir referans düğümün sağlanırsa, koleksiyonun sonuna ulaştı.  
  
 Oluşturduysanız bir **XmlNamedNodeMap** öznitelikleri, öznitelik adı'nı kullanarak ekleyebilirsiniz <xref:System.Xml.XmlNamedNodeMap.SetNamedItem%2A>. Daha fazla bilgi için [NamedNodeMaps ve NodeLists içindeki düğüm koleksiyonları](../../../../docs/standard/data/xml/node-collections-in-namednodemaps-and-nodelists.md).  
  
## <a name="default-attributes"></a>Varsayılan öznitelikler  
 Varsayılan özniteliği için bildirilmiş bir öğe oluşturun, ardından varsayılan değerine sahip yeni bir varsayılan öznitelik XML belge nesne modeli (DOM) tarafından oluşturulur ve öğesine bağlı. Varsayılan öznitelik alt düğümler de şu anda oluşturulur.  
  
## <a name="attribute-child-nodes"></a>Öznitelik alt düğümleri  
 Bir öznitelik düğümü değeri alt düğümlerinden olur. Geçerli alt düğümleri yalnızca iki tür vardır: **XmlText** düğümleri ve **XmlEntityReference** düğümleri. Alt düğümleri anlamında gibi yöntemlerin bunlar **işlevi FirstChild** ve **LastChild** alt düğümleri olarak işlemeye. Bu ayrım alt düğümleri sahip bir öznitelik, öznitelikler veya öznitelik alt düğümleri kaldırmaya çalışırken önemlidir. Daha fazla bilgi için [DOM'da bir öğe düğümünden öznitelikleri kaldırma](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
