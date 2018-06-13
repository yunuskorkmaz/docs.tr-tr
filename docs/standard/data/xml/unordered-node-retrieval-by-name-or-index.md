---
title: Adı veya dizin tarafından sırasız düğümü alma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 2038a90b-92af-4a0a-baaa-08e688d95194
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 785a609455a35dd87a9593f00b58fd160ac708e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572947"
---
# <a name="unordered-node-retrieval-by-name-or-index"></a>Adı veya dizin tarafından sırasız düğümü alma
**XmlNamedNodeMap** NamedNodeMap olarak World Wide Web Konsorsiyumu (W3C) belirtimi açıklandığı ve bunların adı veya dizin tarafından başvuru düğümlere yeteneği olan düğümler sırasız bir kümesini işlemek için gereklidir. Tek yolu erişiminiz bir **XmlNamedNodeMap** olduğunda bir **XmlNamedNodeMap** yöntemi veya özelliği döndürülür. Üç yöntem veya döndüren özellikleri bir **XmlNamedNodeMap**:  
  
-   XmlElement.Attributes  
  
-   XmlDocumentType.Entities  
  
-   XmlDocumentType.Notations  
  
 Örneğin, **XmlDocumentType.Entities** özelliği koleksiyonunu alır **XmlEntity** düğümleri belge türü bildiriminde bildirilmedi. Bu koleksiyonu olarak döndürülür bir **XmlNamedNodeMap**, ve kullanımı ile koleksiyon üzerinden yineleme **sayısı** özelliği ve görüntü varlık bilgileri. Üzerinden yineleme örneği için bir **XmlNamedNodeMap**, bkz: <xref:System.Xml.XmlDocumentType.Entities%2A>.  
  
 **XmlAttributeCollection** türetildiği **XmlNamedNodeMap** ve yalnızca öznitelikleri değiştirilebilir, gösterimler ve varlıkları salt okunur durumdayken. Kullanarak **XmlNamedNodeMap** özniteliklerini, bunların XML adlarını temel alarak bu öznitelikler için düğümleri elde edebilirsiniz. Bu, bir öğe düğümü üzerinde özniteliklerin koleksiyonu düzenleme için kolay bir yöntemini sağlar. Bu doğrudan contrasted **XmlNodeList**, ayrıca uygulayan **IEnumerable** arabirimi, ancak bir dize yerine bir dizin erişimci ile. **RemoveNamedItem** ve **SetNamedItem** yöntemleri karşı kullanılan yalnızca bir **XmlAttributeCollection**. Ekleme veya bir öznitelik koleksiyonundan kullanarak olup olmadığını kaldırma **AttributeCollection** veya **XmlNamedNodeMap** uygulaması, öznitelik koleksiyonu öğesindeki değiştirir. Aşağıdaki kod örneği, bir öznitelik taşıyın ve yeni bir öznitelik oluşturma gösterilmektedir.  
  
```vb  
Imports System  
Imports System.Xml  
  
Class test  
  
    Public Shared Sub Main()  
        Dim doc As New XmlDocument()  
        doc.LoadXml("<root> <child1 attr1='val1' attr2='val2'> text1 </child1> <child2 attr3='val3'> text2 </child2> </root> ")  
  
        ' Get the attributes of node "child2 "  
        Dim ac As XmlAttributeCollection = doc.DocumentElement.ChildNodes(1).Attributes  
  
        ' Print out the number of attributes and their names.  
        Console.WriteLine(("Number of Attributes: " + ac.Count))  
        Dim i As Integer  
        For i = 0 To ac.Count - 1  
            Console.WriteLine((i + 1 + ".  Attribute Name: '" + ac(i).Name + "'  Attribute Value:  '" + ac(i).Value + "'"))  
        Next i  
        ' Get the 'attr1' from child1.  
        Dim attr As XmlAttribute = doc.DocumentElement.ChildNodes(0).Attributes(0)  
  
        ' Add this attribute to the attributecollection "ac".  
        ac.SetNamedItem(attr)  
  
        ''attr1' will be removed from 'child1' and added to 'child2'.  
        ' Print out the number of attributes and their names.  
        Console.WriteLine(("Number of Attributes: " + ac.Count))  
  
        For i = 0 To ac.Count - 1  
            Console.WriteLine((i + 1 + ".  Attribute Name: '" + ac(i).Name + "'  Attribute Value:  '" + ac(i).Value + "'"))  
        Next i  
        ' Create a new attribute and add to the collection.  
        Dim attr2 As XmlAttribute = doc.CreateAttribute("attr4")  
        attr2.Value = "val4"  
        ac.SetNamedItem(attr2)  
  
        ' Print out the number of attributes and their names.  
        Console.WriteLine(("Number of Attributes: " + ac.Count))  
  
        For i = 0 To ac.Count - 1  
            Console.WriteLine((i + 1 + ".  Attribute Name: '" + ac(i).Name + "'  Attribute Value:  '" + ac(i).Value + "'"))  
        Next i  
    End Sub 'Main  
End Class 'test  
```  
  
```csharp  
using System;  
using System.Xml;  
class test {  
    public static void Main() {  
        XmlDocument doc = new XmlDocument();  
        doc.LoadXml( "<root> <child1 attr1='val1' attr2='val2'> text1 </child1> <child2 attr3='val3'> text2 </child2> </root> " );  
  
        // Get the attributes of node "child2"  
        XmlAttributeCollection ac = doc.DocumentElement.ChildNodes[1].Attributes;  
  
        // Print out the number of attributes and their names.  
        Console.WriteLine( "Number of Attributes: "+ac.Count );  
        for( int i = 0; i < ac.Count; i++ )  
            Console.WriteLine( (i+1) + ".  Attribute Name: '" +ac[i].Name+ "'  Attribute Value:  '"+ ac[i].Value +"'" );   
  
        // Get the 'attr1' from child1.  
        XmlAttribute attr = doc.DocumentElement.ChildNodes[0].Attributes[0];  
  
        // Add this attribute to the attributecollection "ac".  
        ac.SetNamedItem( attr );  
  
        // 'attr1' will be removed from 'child1' and added to 'child2'.  
        // Print out the number of attributes and their names.  
        Console.WriteLine( "Number of Attributes: "+ac.Count );          
        for( int i = 0; i < ac.Count; i++ )  
            Console.WriteLine( (i+1) + ".  Attribute Name: '" +ac[i].Name+ "'  Attribute Value:  '"+ ac[i].Value +"'" );   
  
        // Create a new attribute and add to the collection.  
        XmlAttribute attr2 = doc.CreateAttribute( "attr4" );  
        attr2.Value = "val4";  
        ac.SetNamedItem( attr2 );  
  
        // Print out the number of attributes and their names.  
        Console.WriteLine( "Number of Attributes: "+ac.Count );          
        for( int i = 0; i < ac.Count; i++ )  
            Console.WriteLine( (i+1) + ".  Attribute Name: '" +ac[i].Name+ "'  Attribute Value:  '"+ ac[i].Value +"'" );           
  
    }  
}  
```  
  
 Gelen kaldırılmakta olan bir öznitelik gösteren ek kod örneği görmek için bir **AttributeCollection**, bkz: [XmlNamedNodeMap.RemoveNamedItem yöntemi](Overload:System.Xml.XmlNamedNodeMap.RemoveNamedItem). Yöntemleri ve özellikleri hakkında daha fazla bilgi için bkz: [XmlNamedNodeMap üyeleri](AllMembers.T:System.Xml.XmlNamedNodeMap).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
