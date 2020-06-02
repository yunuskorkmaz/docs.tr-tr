---
title: Ada veya Dizine Göre Sırasız Düğüm Alma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 2038a90b-92af-4a0a-baaa-08e688d95194
ms.openlocfilehash: 6847f3c5d233b720f8f4c41cfc52ac663e5e810f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288634"
---
# <a name="unordered-node-retrieval-by-name-or-index"></a>Ada veya Dizine Göre Sırasız Düğüm Alma
**XmlNamedNodeMap** , world WIDE Web KONSORSIYUMU (W3C) belirtiminde NamedNodeMap olarak tanımlanır ve düğümler adına veya dizinine göre başvuru yeteneğine sahip sıralanmamış bir düğüm kümesini işlemek için gereklidir. **XmlNamedNodeMap** 'e erişiminizin tek yolu, bir **XmlNamedNodeMap** bir yöntem veya özellik aracılığıyla döndürüldüğünde olur. **XmlNamedNodeMap**döndüren üç yöntem veya özellik vardır:  
  
- XmlElement. Attributes  
  
- XmlDocumentType. Entities  
  
- XmlDocumentType. gösterimler  
  
 Örneğin, **XmlDocumentType. Entities** özelliği, belge türü bildiriminde belirtilen **XmlEntity** düğümlerinin koleksiyonunu alır. Bu koleksiyon bir **XmlNamedNodeMap**olarak döndürülür ve koleksiyon içinde **Count** özelliğinin kullanımıyla ve varlık bilgilerini görüntüleyecek şekilde yineleyebilirsiniz. Bir **XmlNamedNodeMap**aracılığıyla yineleme örneği için bkz <xref:System.Xml.XmlDocumentType.Entities%2A> ..  
  
 **XmlAttributeCollection** , **XmlNamedNodeMap** 'ten türetilir ve yalnızca öznitelikler değiştirilebilir, ancak gösterimler ve varlıklar salt okunurdur. Öznitelikler için **XmlNamedNodeMap** ' i kullanarak, XML adlarına göre bu özniteliklerin düğümlerini alabilirsiniz. Bu, bir öğe düğümündeki özniteliklerin koleksiyonunu işlemek için kolay bir yöntem sağlar. Bu, doğrudan **XmlNodeList**ile oluşturulabilir, bu da **IEnumerable** arabirimini de uygular, ancak bir dize yerine dizin erişimcisi vardır. **Removenamedidıtem** ve **setnamedidıtem** yöntemleri yalnızca bir **XmlAttributeCollection**ile kullanılır. Öznitelik koleksiyonunu ekleme veya kaldırma, **AttributeCollection** veya **XmlNamedNodeMap** uygulamasının kullanılmasına bakılmaksızın, öğesindeki öznitelik koleksiyonunu değiştirir. Aşağıdaki kod örneği, bir özniteliğin nasıl taşınacağını ve yeni bir özniteliğin nasıl oluşturulacağını gösterir.  
  
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
  
 Bir **AttributeCollection**'dan çıkarılan bir özniteliği gösteren ek bir kod örneği görmek için bkz. [XmlNamedNodeMap. Removenamedidıtem yöntemi](xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A). Yöntemler ve özellikler hakkında daha fazla bilgi için bkz. [XmlNamedNodeMap üyeleri](xref:System.Xml.XmlNamedNodeMap).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](xml-document-object-model-dom.md)
