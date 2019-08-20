---
title: 'Nasıl yapılır: XmlReader (C#) öğesinden XML parçaları akışı'
ms.date: 07/20/2015
ms.assetid: 4a8f0e45-768a-42e2-bc5f-68bdf0e0a726
ms.openlocfilehash: c27c2165af95b8b781564e14efc0668f596e3057
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592401"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-c"></a>Nasıl yapılır: XmlReader (C#) öğesinden XML parçaları akışı
Büyük XML dosyalarını işlemek zorunda olduğunuzda, tüm XML ağacının belleğe yüklenmesi mümkün olmayabilir. Bu konuda, kullanarak <xref:System.Xml.XmlReader>parçaların nasıl akışının yapılacağı gösterilmektedir.  
  
 Nesneleri okumak <xref:System.Xml.XmlReader> <xref:System.Xml.Linq.XElement> için kullanmanın en etkili yöntemlerinden biri kendi özel eksen yönteminizi yazmaktır. Bir Axis yöntemi <xref:System.Xml.Linq.XElement>, bu konudaki örnekte gösterildiği gibi <xref:System.Collections.Generic.IEnumerable%601> genellikle gibi bir koleksiyon döndürür. Özel eksen yönteminde, <xref:System.Xml.Linq.XNode.ReadFrom%2A> yöntemini çağırarak XML parçasını oluşturduktan sonra, kullanarak `yield return`koleksiyonu döndürün. Bu, özel eksen yönteminiz için ertelenmiş yürütme semantiğini sağlar.  
  
 <xref:System.Xml.XmlReader> Nesnesinden bir XML ağacı oluşturduğunuzda, öğesinin bir öğe üzerinde konumlandırılmış olmasıgerekir.<xref:System.Xml.XmlReader> <xref:System.Xml.Linq.XNode.ReadFrom%2A> Yöntemi, öğenin kapanış etiketini okuuncaya kadar döndürmez.  
  
 Kısmi bir ağaç oluşturmak isterseniz, bir <xref:System.Xml.XmlReader> <xref:System.Xml.Linq.XElement> ağaca dönüştürmek istediğiniz düğümde okuyucuyu konumlandırabilirsiniz ve sonra <xref:System.Xml.Linq.XElement> nesneyi oluşturabilirsiniz. Bu, bir ağacı oluşturabilir.  
  
 Bu konuda [nasıl yapılır: Üst bilgi bilgilerine (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md) erişimi olan akış XML parçaları, daha karmaşık bir belgenin nasıl akışla ilgili bilgi ve bir örnek içerir.  
  
 Bu konuda [nasıl yapılır: Büyük XML belgelerinin (C#)](./how-to-perform-streaming-transform-of-large-xml-documents.md) akış dönüşümünü gerçekleştirme, küçük bir bellek parmak düzeyini koruyarak son derece büyük XML belgelerini dönüştürmek için LINQ to XML kullanma örneği içerir.  
  
## <a name="example"></a>Örnek  
 Bu örnek bir özel eksen yöntemi oluşturur. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] Sorgu kullanarak sorgulama yapabilirsiniz. Özel eksen yöntemi `StreamRootChildDoc`, bir yinelenen `Child` öğesi olan bir belgeyi okumak için özel olarak tasarlanan bir yöntemdir.  
  
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
  
```  
bbb  
ccc  
```  
  
 Bu örnekte, kaynak belge çok küçüktür. Ancak milyonlarca `Child` öğe olsa bile, bu örnekte küçük bir bellek ayak izine sahip olmaya devam edersiniz.  
  