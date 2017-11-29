---
title: "DOM öğeleri için yeni öznitelikler oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: dd6dc920-b011-418a-b3db-f1580a7d9251
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6970ffc38e900c9b47c58c8ae4b81b9551f5589b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="creating-new-attributes-for-elements-in-the-dom"></a>DOM öğeleri için yeni öznitelikler oluşturma
Yeni öznitelikler oluşturulması öznitelikleri düğümleri, ancak bir öğe düğümü özelliklerinin ve içerdiği diğer düğüm türleri oluşturmaktan daha farklı bir **XmlAttributeCollection** öğeyle ilişkili. Bir öznitelik oluşturun ve bir öğe olarak eklemek için birden çok yolu vardır:  
  
-   Öğe düğümü almak ve kullanmak **SetAttribute** bir öznitelik, öğe özniteliği koleksiyona eklemek için.  
  
-   Oluşturma bir **XmlAttribute** düğümünü kullanarak **CreateAttribute** yöntemi, öğe düğümü alın ve ardından kullanmak **SetAttributeNode** bu öznitelik koleksiyon düğümü eklemek için öğesi.  
  
 Aşağıdaki örnek, bir öznitelik kullanarak bir öğe eklemek gösterilmiştir **SetAttribute** yöntemi.  
  
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
  
 Aşağıdaki örnek yeni bir gösterir kullanılarak oluşturulan öznitelik **CreateAttribute** yöntemi. Ardından öznitelik koleksiyonuna eklenen öznitelik gösterir **defteri** öğesi kullanılarak **SetAttributeNode** yöntemi.  
  
 Aşağıdaki XML verilen:  
  
```xml  
<book genre='novel' ISBN='1-861001-57-5'>  
<title>Pride And Prejudice</title>  
</book>  
```  
  
 Yeni bir öznitelik oluşturmak ve bir değer verin:  
  
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
  
 **Çıktı**  
  
```xml  
<book genre="novel" ISBN="1-861001-57-5" publisher="WorldWide Publishing">  
<title>Pride And Prejudice</title>  
</book>  
```  
  
 Tam kod örneği bulunabilir <xref:System.Xml.XmlDocument.CreateAttribute%2A>.  
  
 Ayrıca oluşturabilirsiniz bir **XmlAttribute** düğümü ve kullanım **Insertbefore** veya **InsertAfter** koleksiyondaki uygun konuma yerleştirmek için yöntemleri. Aynı ada sahip bir öznitelik zaten var olan öznitelik koleksiyonda mevcut değilse **XmlAttribute** düğümü, koleksiyon ve yeni kaldırılır **XmlAttribute** düğümüne eklenir. Bu aynı şekilde gerçekleştirir **SetAttribute** yöntemi. Varolan bir düğümü yapmak için bir başvuru noktası olarak bir parametre olarak bu yöntemlerden ele **Insertbefore** ve **InsertAfter**. Yeni düğüm için varsayılan eklemek istediğiniz yeri gösteren bir referans düğümün sağlamazsanız **InsertAfter** yöntemdir koleksiyonu başında yeni düğüm eklemek için. İçin varsayılan konum **Insertbefore**, referans düğümün sağlanırsa, koleksiyonun sonuna ulaştı.  
  
 Oluşturduysanız bir **XmlNamedNodeMap** özniteliklerini, özniteliğin adı kullanarak ekleyebilirsiniz <xref:System.Xml.XmlNamedNodeMap.SetNamedItem%2A>. Daha fazla bilgi için bkz: [düğümü koleksiyonlarda NamedNodeMaps ve NodeLists](../../../../docs/standard/data/xml/node-collections-in-namednodemaps-and-nodelists.md).  
  
## <a name="default-attributes"></a>Varsayılan öznitelikleri  
 Varsayılan bir özniteliği bulunması için bildirilen bir öğe oluşturun, sonra varsayılan değeri ile yeni bir varsayılan öznitelik XML belge nesne modeli (DOM) tarafından oluşturulur ve öğesine bağlı. Varsayılan özniteliğinin alt düğümler de şu anda oluşturulur.  
  
## <a name="attribute-child-nodes"></a>Öznitelik alt düğümleri  
 Öznitelik düğümü değeri, alt düğümleri olur. Geçerli alt düğümleri yalnızca iki tür vardır: **XmlText** düğümleri ve **XmlEntityReference** düğümleri. Bu yöntemleri gibi herkese açık alt düğümleri bunlar **işlevi FirstChild** ve **LastChild** alt düğümleri olarak işlem. Bu ayrım alt düğümleri sahip bir öznitelik, öznitelikler veya öznitelik alt düğümleri kaldırmak çalışırken önemlidir. Daha fazla bilgi için bkz: [DOM öğesi düğümünde kaldırma özniteliklerden](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML belge nesne modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
