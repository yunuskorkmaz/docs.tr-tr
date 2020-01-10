---
title: XmlReader (C#) öğesinden XML parçalarını akışa alma
ms.date: 07/20/2015
ms.assetid: 4a8f0e45-768a-42e2-bc5f-68bdf0e0a726
ms.openlocfilehash: f7914d33622518f983a685dd2e844a25fd3ca15f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714648"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-c"></a>XmlReader (C#) öğesinden XML parçalarını akışa alma

Büyük XML dosyalarını işlemek zorunda olduğunuzda, tüm XML ağacının belleğe yüklenmesi mümkün olmayabilir. Bu konuda, <xref:System.Xml.XmlReader>kullanarak parçaların nasıl akışının yapılacağı gösterilmektedir.  
  
 <xref:System.Xml.Linq.XElement> nesneleri okumak için <xref:System.Xml.XmlReader> kullanmanın en etkili yöntemlerinden biri kendi özel eksen yönteminizi yazmaktır. Bir Axis yöntemi genellikle bu konudaki örnekte gösterildiği gibi, <xref:System.Xml.Linq.XElement><xref:System.Collections.Generic.IEnumerable%601> gibi bir koleksiyon döndürür. Özel eksen yönteminde, <xref:System.Xml.Linq.XNode.ReadFrom%2A> yöntemini çağırarak XML parçasını oluşturduktan sonra, `yield return`kullanarak koleksiyonu döndürün. Bu, özel eksen yönteminiz için ertelenmiş yürütme semantiğini sağlar.  
  
 Bir <xref:System.Xml.XmlReader> nesnesinden bir XML ağacı oluşturduğunuzda, <xref:System.Xml.XmlReader> bir öğe üzerinde konumlandırılmalıdır. <xref:System.Xml.Linq.XNode.ReadFrom%2A> yöntemi, öğenin kapanış etiketini okuuncaya kadar döndürmez.  
  
 Kısmi bir ağaç oluşturmak istiyorsanız, bir <xref:System.Xml.XmlReader>örneği oluşturabilir, okuyucuyu <xref:System.Xml.Linq.XElement> ağacına dönüştürmek istediğiniz düğüme konumlandırabilirsiniz ve sonra <xref:System.Xml.Linq.XElement> nesnesini oluşturabilirsiniz.  
  
Üst bilgi [bilgilerine erişimi olan XML parçalarının nasıl akışının yapılacağı konusu (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md) , daha karmaşık bir belgenin nasıl akışla ilgili bilgi ve bir örnek içerir.
  
 [Büyük XML belgelerinin (C#) akış dönüşümünü gerçekleştirme](./how-to-perform-streaming-transform-of-large-xml-documents.md) konusu, küçük bir bellek parmak izi sağlarken çok büyük XML belgelerini dönüştürmek için LINQ to XML kullanma örneği içerir.  
  
## <a name="example"></a>Örnek  
 Bu örnek bir özel eksen yöntemi oluşturur. Bir LINQ sorgusu kullanarak bunu sorgulayabilirsiniz. `StreamRootChildDoc`özel eksen yöntemi, bir yinelenen `Child` öğesi olan bir belgeyi okumak için özel olarak tasarlanan bir yöntemdir.  
  
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
  
 Bu örnekte, kaynak belge çok küçüktür. Ancak milyonlarca `Child` öğesi olsa bile, bu örnekte küçük bir bellek ayak izine sahip olmaya devam edersiniz.  
