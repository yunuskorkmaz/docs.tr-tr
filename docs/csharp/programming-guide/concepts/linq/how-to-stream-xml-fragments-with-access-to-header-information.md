---
title: Üst bilgi bilgilerine erişimi olan XML parçalarını akışa alma (C#)
ms.date: 07/20/2015
ms.assetid: 7f242770-b0c7-418d-894b-643215e1f8aa
ms.openlocfilehash: 5bc10bcadae0e33ee63f953608ca841d44dd6527
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712396"
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-c"></a>Üst bilgi bilgilerine erişimi olan XML parçalarını akışa alma (C#)
Bazen rastgele büyük XML dosyalarını okumanız ve uygulamanın bellek parmak izin tahmin edilebilir olması için uygulamanızı yazmanız gerekir. Bir XML ağacını büyük bir XML dosyası ile doldurmayı denerseniz, bellek kullanımınız dosyanın boyutuyla orantılıdır; yani çok fazla. Bu nedenle, bunun yerine bir akış tekniği kullanmanız gerekir.  
  
Bir seçenek <xref:System.Xml.XmlReader>kullanarak uygulamanızı yazmaktır. Ancak, XML ağacını sorgulamak için LINQ kullanmak isteyebilirsiniz. Bu durumda, kendi özel eksen yönteminizi yazabilirsiniz. Daha fazla bilgi için bkz. [LINQ to XML eksen yöntemi yazmaC#()](./how-to-write-a-linq-to-xml-axis-method.md).
  
 Kendi eksen yönteminizi yazmak için, ilgilendiğiniz düğümlerin birine ulaşıncaya kadar düğümleri okumak için <xref:System.Xml.XmlReader> kullanan küçük bir yöntem yazarsınız. Daha sonra yöntemi, <xref:System.Xml.XmlReader> okuyan ve bir XML parçasını örnekleyen <xref:System.Xml.Linq.XNode.ReadFrom%2A>çağırır. Daha sonra, her parçayı özel eksen yönteminizin numaralandırıldığı yönteme `yield return` olarak verir. Daha sonra özel eksen yönteinizde LINQ sorguları yazabilirsiniz.  
  
 Akış teknikleri en iyi şekilde, kaynak belgeyi yalnızca bir kez işleyebilmeniz ve öğeleri belge düzeninde işleyebilirsiniz. <xref:System.Linq.Enumerable.OrderBy%2A>gibi bazı standart sorgu işleçleri, kaynaklarını yineleyebilir, tüm verileri toplar, sıralar ve son olarak dizideki ilk öğeyi verir. İlk öğeyi bırakmadan önce kaynağını üreten bir sorgu işleci kullanırsanız, küçük bir bellek parmak izini saklayacaksınız.  
  
## <a name="example"></a>Örnek  

Bazen sorun biraz daha ilginç olur. Aşağıdaki XML belgesinde, özel eksen yönteminizin tüketicisi, her öğenin ait olduğu müşterinin adını da bilmelidir.  
  
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
  
 Bu örnekte geçen yaklaşım ayrıca, bu üstbilgi bilgilerini izlemek, üst bilgi bilgilerini kaydetmek ve ardından hem başlık bilgilerini hem de numaralandırdığınız ayrıntıyı içeren küçük bir XML ağacı oluşturmanızı kullanmaktır. Ardından Axis yöntemi bu yeni, küçük XML ağacını verir. Sorgu daha sonra başlık bilgilerine ve ayrıntı bilgilerine erişimi de vardır.  
  
 Bu yaklaşımın küçük bir bellek ayak izi vardır. Her ayrıntı XML parçası, bir önceki parçaya hiçbir başvuru tutulmazsa ve çöp toplama için kullanılabilir. Bu teknik yığın üzerinde birçok kısa süreli nesne oluşturur.  
  
 Aşağıdaki örnek, URI tarafından belirtilen dosyadan XML parçalarını akıyan bir özel eksen yönteminin nasıl uygulanacağını ve kullanılacağını gösterir. Bu özel eksen, `Customer`, `Name`ve `Item` öğelerine sahip bir belgeyi beklediğinden ve bu öğelerin yukarıdaki `Source.xml` belgesinde olarak düzenlenebilmesini sağlayacak şekilde yazılmıştır. Bu bir uyarlaması uygulamasıdır. Daha sağlam bir uygulama, geçersiz bir belgeyi ayrıştırmaya hazırlanmalıdır.  
  
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
