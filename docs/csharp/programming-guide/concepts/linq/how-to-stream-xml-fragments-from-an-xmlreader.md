---
title: Bir XmlReader 'dan XML parçalarını akışa alma (C#)
description: Bir XmlReader 'dan XML parçalarını akışa alma hakkında bilgi edinin. Bu yöntem, büyük XML dosyalarını işlemek için kullanılır.
ms.date: 07/20/2015
ms.assetid: 4a8f0e45-768a-42e2-bc5f-68bdf0e0a726
ms.openlocfilehash: e35322724712816180d48c1957719cf87079aedd
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301027"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-c"></a>Bir XmlReader 'dan XML parçalarını akışa alma (C#)

Büyük XML dosyalarını işlemek zorunda olduğunuzda, tüm XML ağacının belleğe yüklenmesi mümkün olmayabilir. Bu konuda, kullanarak parçaların nasıl akışının yapılacağı gösterilmektedir <xref:System.Xml.XmlReader> .  
  
 Nesneleri okumak için kullanmanın en etkili yöntemlerinden biri <xref:System.Xml.XmlReader> <xref:System.Xml.Linq.XElement> kendi özel eksen yönteminizi yazmaktır. Bir Axis yöntemi <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> , bu konudaki örnekte gösterildiği gibi genellikle gibi bir koleksiyon döndürür. Özel eksen yönteminde, yöntemini çağırarak XML parçasını oluşturduktan sonra <xref:System.Xml.Linq.XNode.ReadFrom%2A> , kullanarak koleksiyonu döndürün `yield return` . Bu, özel eksen yönteminiz için ertelenmiş yürütme semantiğini sağlar.  
  
 Nesnesinden bir XML ağacı oluşturduğunuzda, <xref:System.Xml.XmlReader> <xref:System.Xml.XmlReader> öğesinin bir öğe üzerinde konumlandırılmış olması gerekir. <xref:System.Xml.Linq.XNode.ReadFrom%2A>Yöntemi, öğenin kapanış etiketini okuuncaya kadar döndürmez.  
  
 Kısmi bir ağaç oluşturmak isterseniz, bir <xref:System.Xml.XmlReader> ağaca dönüştürmek istediğiniz düğümde okuyucuyu konumlandırabilirsiniz <xref:System.Xml.Linq.XElement> ve sonra nesneyi oluşturabilirsiniz. Bu, bir ağacı oluşturabilir <xref:System.Xml.Linq.XElement> .  
  
[Başlık bilgilerine erişimi olan XML parçalarının nasıl akışının yapılacağı konusu (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md) , daha karmaşık bir belgeyi akışa alma hakkında bilgi ve bir örnek içerir.
  
 [Büyük XML belgelerinin akış dönüşümünü gerçekleştirme konusu (C#)](./how-to-perform-streaming-transform-of-large-xml-documents.md) , küçük bir bellek parmak izini sağlarken çok büyük XML belgelerini dönüştürmek için LINQ to XML kullanma örneği içerir.  
  
## <a name="example"></a>Örnek  
 Bu örnek bir özel eksen yöntemi oluşturur. Bir LINQ sorgusu kullanarak bunu sorgulayabilirsiniz. Özel eksen yöntemi, bir `StreamRootChildDoc` yinelenen öğesi olan bir belgeyi okumak için özel olarak tasarlanan bir yöntemdir `Child` .  
  
```csharp  
static IEnumerable<XElement> StreamRootChildDoc(StringReader stringReader)  
{  
    using (XmlReader reader = XmlReader.Create(stringReader))  
    {  
        reader.MoveToContent();  
        // Parse the file and display each of the nodes.  
        while (reader.Read())  
        {  
            switch (reader.NodeType)  
            {  
                case XmlNodeType.Element:  
                    if (reader.Name == "Child") {  
                        XElement el = XElement.ReadFrom(reader) as XElement;  
                        if (el != null)  
                            yield return el;  
                    }  
                    break;  
            }  
        }  
    }  
}  
  
static void Main(string[] args)  
{  
    string markup = @"<Root>  
      <Child Key=""01"">  
        <GrandChild>aaa</GrandChild>  
      </Child>  
      <Child Key=""02"">  
        <GrandChild>bbb</GrandChild>  
      </Child>  
      <Child Key=""03"">  
        <GrandChild>ccc</GrandChild>  
      </Child>  
    </Root>";  
  
    IEnumerable<string> grandChildData =  
        from el in StreamRootChildDoc(new StringReader(markup))  
        where (int)el.Attribute("Key") > 1  
        select (string)el.Element("GrandChild");  
  
    foreach (string str in grandChildData) {  
        Console.WriteLine(str);  
    }  
}  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```output  
bbb  
ccc  
```  
  
 Bu örnekte, kaynak belge çok küçüktür. Ancak milyonlarca öğe olsa bile `Child` , bu örnekte küçük bir bellek ayak izine sahip olmaya devam edersiniz.  
