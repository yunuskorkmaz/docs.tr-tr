---
title: 'Nasıl yapılır: XML parçaları üst bilgileri (C#) erişim akışı'
ms.date: 07/20/2015
ms.assetid: 7f242770-b0c7-418d-894b-643215e1f8aa
ms.openlocfilehash: af8f83ba746292289bb97f591103cc91d6febbad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-c"></a>Nasıl yapılır: XML parçaları üst bilgileri (C#) erişim akışı
Bazen büyük XML dosyaları okuma ve böylece uygulamanın bellek alanını tahmin edilebilir uygulamanızı yazma gerekir. Bir XML ağaç içeren büyük bir XML dosyası doldurmak çalışırsanız, bellek kullanımı dosyasının boyutunu orantılı — diğer bir deyişle, aşırı. Bu nedenle, bir akış teknik yerine kullanmanız gerekir.  
  
 Bir seçenektir kullanarak uygulamanızı yazmak için <xref:System.Xml.XmlReader>. Ancak, kullanmak isteyebilirsiniz [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] XML ağaç sorgulanamıyor. Bu durumda, kendi özel eksen yöntemi yazabilirsiniz. Daha fazla bilgi için bkz: [nasıl yapılır: bir LINQ XML eksen yöntemine (C#) yazma](../../../../csharp/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md).  
  
 Kendi eksen yöntemi yazmak için kullandığı küçük bir yöntem yazmak <xref:System.Xml.XmlReader> içinde ilgi düğümlerinden biri ulaşana kadar düğümleri okumak için. Daha sonra yöntemi çağırır <xref:System.Xml.Linq.XNode.ReadFrom%2A>, olarak okuyan <xref:System.Xml.XmlReader> ve bir XML parçası başlatır. Ardından her parça aracılığıyla verir `yield return` özel eksen yönteminizi numaralandırma yöntemi. Ardından, özel eksen yöntemi LINQ sorgularını yazabilirsiniz.  
  
 Akış teknikleri en iyi kaynak belge yalnızca bir kez işlem gerekir ve belge sırayla öğeleri işleyebilmesi için durumlarda uygulanır. Belirli standart sorgu işleçleri gibi <xref:System.Linq.Enumerable.OrderBy%2A>kendi kaynak yinelemek, tüm verileri toplamak, sıralanmasını ve son olarak dizinin ilk öğesi verim. İlk öğe sağlayan önce kaynağı gerçeğe bir sorgu işleci kullanırsanız, bir küçük bellek alanını bulamayacaktır unutmayın.  
  
## <a name="example"></a>Örnek  
 Bazen biraz daha fazla ilginç sorun alır. Aşağıdaki XML belgesinde özel eksen yönteminizi tüketici ayrıca her öğenin ait olduğu müşterinin adını bilmesi gerekir.  
  
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
  
 Bu örnek alan aynı zamanda bu başlık bilgilerini izleme, üst bilgileri kaydedin ve üst bilgileri ve numaralandırma ayrıntı içeren küçük bir XML ağaç yapı yaklaşımdır. Eksen yöntemi, daha sonra bu yeni, küçük XML ağaç verir. Sorgu daha sonra ayrıntılı bilgilerin yanı sıra üst bilgileri erişebilir.  
  
 Bu yaklaşımın küçük bellek kaplama alanı vardır. Her ayrıntı XML parçası verdiğini gibi başvuru önceki parça tutulur ve atık toplama için kullanılabilir. Bu teknik öbek üzerinde birçok kısa süreli nesne oluşturduğuna dikkat edin.  
  
 Aşağıdaki örnek XML parçaları URI tarafından belirtilen dosyadan akışları özel eksen yöntemi uygulamak ve nasıl kullanılacağını gösterir. Bu özel eksen özellikle sahip bir belge bekliyor gibi yazılır `Customer`, `Name`, ve `Item` öğeleri ve bu öğeleri yukarıdaki olduğu gibi düzenlenmesini, `Source.xml` belge. Bu simplistic bir uygulamasıdır. Geçersiz bir belge ayrıştırmak için daha sağlam bir uygulama hazırlanması.  
  
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
 [Gelişmiş LINQ-XML programlama (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
