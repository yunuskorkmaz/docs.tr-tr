---
title: 'Nasıl yapılır: üst bilgilere (C#) erişimle XML parçalarının Stream'
ms.date: 07/20/2015
ms.assetid: 7f242770-b0c7-418d-894b-643215e1f8aa
ms.openlocfilehash: 9c141b21a009f836fbf385c1f4179e288ec6c3b5
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44217080"
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-c"></a>Nasıl yapılır: üst bilgilere (C#) erişimle XML parçalarının Stream
Bazen büyük XML dosyaları okur ve bellek Ayak izi uygulamanın öngörülebilir böylece uygulamanız yazma gerekir. İle büyük bir XML dosyasını bir XML ağacı doldurma çalışırsanız, bellek kullanım için dosya boyutu orantılı — diğer bir deyişle, aşırı. Bu nedenle, bir akış teknik yerine kullanmanız gerekir.  
  
 Bir seçenektir kullanarak uygulamanızı yazmak için <xref:System.Xml.XmlReader>. Ancak, kullanmak isteyebilirsiniz [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] XML ağacı sorgulanamıyor. Bu durumda, kendi özel eksen yöntemi yazabilirsiniz. Daha fazla bilgi için [nasıl yapılır: LINQ to XML eksen yöntemi (C#) yazma](../../../../csharp/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md).  
  
 Kendi eksen yöntemi yazma için kullanan küçük bir yöntem yazmaktır. <xref:System.Xml.XmlReader> , olduğu ilgilenen düğümlerinden biri ulaşana dek düğümleri okumak için. Daha sonra yöntemi çağırır <xref:System.Xml.Linq.XNode.ReadFrom%2A>, hangi okur <xref:System.Xml.XmlReader> ve bir XML parçası başlatır. Ardından her parçayı aracılığıyla ortaya çıkarır `yield return` özel eksen yönteminizi numaralandırma yöntemi. Ardından, özel eksen yöntemi LINQ sorguları da yazabilirsiniz.  
  
 Akış teknikleri, burada yalnızca bir kez kaynak belge işlemek gereken ve belge sırada öğeleri işleyebilir durumlarda en iyi şekilde uygulanır. Belirli standart sorgu işleçleri gibi <xref:System.Linq.Enumerable.OrderBy%2A>kaynağına yineleme, tüm verileri Topla, sıralanmasını ve son sıradaki ilk öğeyi yield. İlk öğeyi oluşturan önce kaynağına gerçekleştiren bir sorgu işlecini kullanmak, bir küçük bellek Ayak izi korumaz unutmayın.  
  
## <a name="example"></a>Örnek  
 Bazı durumlarda biraz daha fazla ilgi çekici sorun alır. Aşağıdaki XML belgesindeki özel eksen yönteminizi tüketicisinin her öğenin ait olduğu müşterinin adını bilmek de vardır.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Root>  
  <Customer>  
    <Name>A. Datum Corporation</Name>  
    <Item>  
      <Key>0001</Key>  
    </Item>  
    <Item>  
      <Key>0002</Key>  
    </Item>  
    <Item>  
      <Key>0003</Key>  
    </Item>  
    <Item>  
      <Key>0004</Key>  
    </Item>  
  </Customer>  
  <Customer>  
    <Name>Fabrikam, Inc.</Name>  
    <Item>  
      <Key>0005</Key>  
    </Item>  
    <Item>  
      <Key>0006</Key>  
    </Item>  
    <Item>  
      <Key>0007</Key>  
    </Item>  
    <Item>  
      <Key>0008</Key>  
    </Item>  
  </Customer>  
  <Customer>  
    <Name>Southridge Video</Name>  
    <Item>  
      <Key>0009</Key>  
    </Item>  
    <Item>  
      <Key>0010</Key>  
    </Item>  
  </Customer>  
</Root>  
```  
  
 Bu örnek alan için bu üst bilgi bilgileri izlemek, üst bilgi bilgileri kaydedin ve ardından üst bilgi bilgileri hem numaralandırma ayrıntı içeren küçük bir XML ağacı oluşturmak için bir yaklaşımdır. Eksen yöntemi, ardından bu yeni, küçük XML ağacı verir. Sorgu, daha sonra ayrıntılı bilgilerin yanı sıra, üst bilgi bilgileri erişimi vardır.  
  
 Bu yaklaşım, küçük bellek Ayak izi sahiptir. Her ayrıntı XML parçası veriyor gibi başvuru için önceki parça tutulur ve çöp toplama için kullanılabilir. Bu teknik yığın üzerinde çok kısa süreli nesneleri oluşturur unutmayın.  
  
 Aşağıdaki örnek, uygulamak ve URI tarafından belirtilen dosyaya XML parçalarının akışını bir özel eksen yöntemi kullanmak gösterilmektedir. Bu özel eksen özellikle sahip bir belge beklediği gibi yazılır `Customer`, `Name`, ve `Item` öğeleri ve bu öğeleri olduğu gibi yukarıdaki düzenlenmesini, `Source.xml` belge. Bu basitleştirilmiş bir uygulamasıdır. Geçersiz bir belge ayrıştırmak için daha sağlam bir uygulama hazır.  
  
```csharp  
static IEnumerable<XElement> StreamCustomerItem(string uri)  
{  
    using (XmlReader reader = XmlReader.Create(uri))  
    {  
        XElement name = null;  
        XElement item = null;  
  
        reader.MoveToContent();  
  
        // Parse the file, save header information when encountered, and yield the  
        // Item XElement objects as they are created.  
  
        // loop through Customer elements  
        while (reader.Read())  
        {  
            if (reader.NodeType == XmlNodeType.Element  
                && reader.Name == "Customer")  
            {  
                // move to Name element  
                while (reader.Read())  
                {  
                    if (reader.NodeType == XmlNodeType.Element &&  
                        reader.Name == "Name")  
                    {  
                        name = XElement.ReadFrom(reader) as XElement;  
                        break;  
                    }  
                }  
  
                // loop through Item elements  
                while (reader.Read())  
                {  
                    if (reader.NodeType == XmlNodeType.EndElement)  
                        break;  
                    if (reader.NodeType == XmlNodeType.Element  
                        && reader.Name == "Item")  
                    {  
                        item = XElement.ReadFrom(reader) as XElement;  
                        if (item != null) {  
                            XElement tempRoot = new XElement("Root",  
                                new XElement(name)  
                            );  
                            tempRoot.Add(item);  
                            yield return item;  
                        }  
                    }  
                }  
            }  
        }  
    }  
}  
  
static void Main(string[] args)  
{  
    XElement xmlTree = new XElement("Root",  
        from el in StreamCustomerItem("Source.xml")  
        where (int)el.Element("Key") >= 3 && (int)el.Element("Key") <= 7  
        select new XElement("Item",  
            new XElement("Customer", (string)el.Parent.Element("Name")),  
            new XElement(el.Element("Key"))  
        )  
    );  
    Console.WriteLine(xmlTree);  
}  
```  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```xml  
<Root>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0003</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0004</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0005</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0006</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0007</Key>  
  </Item>  
</Root>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [Gelişmiş LINQ to XML programlama (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
