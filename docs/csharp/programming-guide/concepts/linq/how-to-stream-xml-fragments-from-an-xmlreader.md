---
title: "Nasıl yapılır: Stream parçalarını xmlreader'dan (C#)"
ms.date: 07/20/2015
ms.assetid: 4a8f0e45-768a-42e2-bc5f-68bdf0e0a726
ms.openlocfilehash: 8e2baed3ca32ea4273993fe5bed43fef768204ce
ms.sourcegitcommit: f6343b070f3c66877338a05c8bfb0be9985255e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39221016"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-c"></a>Nasıl yapılır: Stream parçalarını xmlreader'dan (C#)
Büyük XML dosyalarını işlemek varsa, tüm XML ağacının belleğe yüklemek için uygun olmayabilir. Bu konuda gösterir kullanarak parçalarının akışını yapma hakkında bir <xref:System.Xml.XmlReader>.  
  
 Kullanmak için en etkili yollarından biri bir <xref:System.Xml.XmlReader> okunacak <xref:System.Xml.Linq.XElement> nesneleri, kendi özel eksen yöntem yazmaktır. Eksen yöntemi genellikle bir koleksiyonu gibi döndürür <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement>, bu konudaki örnekte gösterildiği gibi. Özel eksen yöntemi çağırarak XML parçası oluşturduktan sonra <xref:System.Xml.Linq.XNode.ReadFrom%2A> yöntemini kullanarak koleksiyon döndürmek `yield return`. Bu özel eksen yönteminize ertelenmiş yürütme semantiği sağlar.  
  
 XML ağacından oluşturduğunuzda bir <xref:System.Xml.XmlReader> nesnesi <xref:System.Xml.XmlReader> bir öğede konumlandırılmalıdır. <xref:System.Xml.Linq.XNode.ReadFrom%2A> Öğenin kapatma etiketi okudu kadar yöntemi döndürmez.  
  
 Kısmi bir ağaç oluşturmak istiyorsanız, oluşturabileceğiniz bir <xref:System.Xml.XmlReader>, dönüştürmek istediğiniz düğüme okuyucu getirin bir <xref:System.Xml.Linq.XElement> ağaç ve oluşturup <xref:System.Xml.Linq.XElement> nesne.  
  
 Konu [nasıl yapılır: üst bilgileri (C#) erişimi Stream parçalarını](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) bilgileri ve daha karmaşık bir belge akışı konusunda bir örnek içerir.  
  
 Konu [nasıl yapılır: gerçekleştirmek akış dönüştürme, büyük XML belgeleri (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) küçük bellek ayak izini sürdürürken son derece büyük XML belgelerini dönüştürmek için LINQ to XML kullanarak bir örnek içerir.  
  
## <a name="example"></a>Örnek  
 Bu örnek bir özel eksen yöntemi oluşturur. Kullanarak sorgulayabilirsiniz bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu. Özel eksen yöntemi `StreamRootChildDoc`, özellikle yinelenen olan bir belgeyi okumak için tasarlanmış bir yöntem `Child` öğesi.  
  
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
  
 Bu örnekte, kaynak belge çok küçüktür. Ancak, milyonlarca olsa bile `Child` öğeleri, bu örnekte küçük bellek Ayak izi yine de sahip.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Ayrıştırma (C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
