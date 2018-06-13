---
title: 'Nasıl yapılır: akış parçalarını gelen XmlReader (C#)'
ms.date: 07/20/2015
ms.assetid: 4a8f0e45-768a-42e2-bc5f-68bdf0e0a726
ms.openlocfilehash: 8e2baed3ca32ea4273993fe5bed43fef768204ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33321070"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-c"></a>Nasıl yapılır: akış parçalarını gelen XmlReader (C#)
Büyük XML dosyalarını işlemek varsa, XML ağacın tamamı belleğe yüklemek için uygun olmayabilir. Bu konuda kullanarak parçaları akışı gösterilmektedir bir <xref:System.Xml.XmlReader>.  
  
 Kullanmak için en etkili yollarından biri, bir <xref:System.Xml.XmlReader> okumak için <xref:System.Xml.Linq.XElement> nesnedir kendi özel eksen yöntemi yazmak için. Bir eksen yöntemi bir koleksiyon gibi tipik döndürür <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement>, bu konuda örnekte gösterildiği gibi. Özel eksen yönteminde çağırarak XML parçası oluşturduktan sonra <xref:System.Xml.Linq.XNode.ReadFrom%2A> yöntemi kullanarak koleksiyon döndürmek `yield return`. Bu, özel eksen yönteminize ertelenmiş yürütme semantiği sağlar.  
  
 Bir XML ağacından oluşturduğunuzda bir <xref:System.Xml.XmlReader> nesnesi <xref:System.Xml.XmlReader> bir öğede konumlandırılmalıdır. <xref:System.Xml.Linq.XNode.ReadFrom%2A> Yöntemi öğenin kapatma etiketi okudu kadar döndürmez.  
  
 Kısmi bir ağaç oluşturmak istiyorsanız, örneği oluşturmak bir <xref:System.Xml.XmlReader>, dönüştürmek istediğiniz düğüme okuyucu getirin bir <xref:System.Xml.Linq.XElement> ağacı ve ardından oluşturun <xref:System.Xml.Linq.XElement> nesnesi.  
  
 Konu [nasıl yapılır: akışı XML parçaları üst bilgileri (C#) erişimi](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) bilgi ve daha karmaşık bir belge akış konusunda bir örnek içerir.  
  
 Konu [nasıl yapılır: gerçekleştirmek akış dönüştürme, büyük XML belgeleri (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) küçük bellek alanını korurken son derece büyük XML belgelerini dönüştürmek için LINQ-XML kullanarak bir örnek içerir.  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir özel eksen yöntemi oluşturur. Kullanarak sorgulama yapabilirsiniz bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu. Özel eksen yöntemi `StreamRootChildDoc`, özellikle yinelenen olan bir belgeyi okumak için tasarlanmış bir yöntemle `Child` öğesi.  
  
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
  
 Bu örnek şu çıkışı üretir:  
  
```  
bbb  
ccc  
```  
  
 Bu örnekte, kaynak belge çok küçük. Ancak, milyonlarca olsa bile `Child` öğeleri, bu örnekte küçük bellek alanını hala sahip olabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Ayrıştırma (C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
