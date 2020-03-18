---
title: Üstbilgi bilgilerine erişim (C#) ile XML parçaları akışı nasıl
ms.date: 07/20/2015
ms.assetid: 7f242770-b0c7-418d-894b-643215e1f8aa
ms.openlocfilehash: 5bc10bcadae0e33ee63f953608ca841d44dd6527
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712396"
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-c"></a>Üstbilgi bilgilerine erişim (C#) ile XML parçaları akışı nasıl
Bazen rasgele büyük XML dosyaları okumak ve uygulamanın bellek ayak izi öngörülebilir böylece uygulama yazmak zorunda. Bir XML ağacını büyük bir XML dosyasıyla doldurmaya çalışırsanız, bellek kullanımınız dosyanın boyutuyla orantılı olacaktır, yani aşırı. Bu nedenle, bunun yerine bir akış tekniği kullanmanız gerekir.  
  
Bir seçenek kullanarak <xref:System.Xml.XmlReader>uygulamanızı yazmaktır. Ancak, XML ağacını sorgulamak için LINQ'yi kullanmak isteyebilirsiniz. Bu durumda, kendi özel eksen yönteminizi yazabilirsiniz. Daha fazla bilgi için, [XML ekseni yöntemine (C#) linq nasıl yazılır.](./how-to-write-a-linq-to-xml-axis-method.md)
  
 Kendi eksen yönteminizi yazmak için, ilgilendiğiniz <xref:System.Xml.XmlReader> düğümlerden birine ulaşana kadar düğümleri okumak için kullanan küçük bir yöntem yazarsınız. Yöntem daha <xref:System.Xml.Linq.XNode.ReadFrom%2A>sonra çağırır , <xref:System.Xml.XmlReader> hangi okur ve bir XML parçası anlık. Daha sonra her parçayı özel eksen yönteminizi sayısallaştırıyor `yield return` yönteminize verir. Daha sonra özel eksen yönteminize LINQ sorguları yazabilirsiniz.  
  
 Akış teknikleri en iyi kaynak belgeyi yalnızca bir kez işlemeniz gereken durumlarda uygulanır ve öğeleri belge sırasına göre işleyebilirsiniz. Kaynaklarını yineleyin, <xref:System.Linq.Enumerable.OrderBy%2A>tüm verileri toplar, sıralar ve ardından son olarak dizideki ilk öğeyi verir. İlk öğeyi vermeden önce kaynağını somutlaştıran bir sorgu işleci kullanırsanız, küçük bir bellek ayak izini saklamazsınız.  
  
## <a name="example"></a>Örnek  

Bazen sorun biraz daha ilginç oluyor. Aşağıdaki XML belgesinde, özel eksen yönteminizin tüketicisinin de her öğenin ait olduğu müşterinin adını bilmesi gerekiyor.  
  
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
  
 Bu örnekte aldığı yaklaşım, bu üstbilgi bilgilerini izlemek, üstbilgi bilgilerini kaydetmek ve sonra hem üstbilgi hem de sayısalbilgilerinizi içeren küçük bir XML ağacı oluşturmaktır. Eksen yöntemi daha sonra bu yeni, küçük XML ağacı verir. Sorgu daha sonra üstbilgi bilgilerinin yanı sıra ayrıntı bilgilerine de erişebilir.  
  
 Bu yaklaşım küçük bir bellek ayak izi vardır. Her ayrıntı XML parçası verim olarak, önceki parçaya hiçbir başvuru tutulur ve çöp toplama için kullanılabilir. Bu teknik yığın üzerinde birçok kısa ömürlü nesneler oluşturur.  
  
 Aşağıdaki örnek, URI tarafından belirtilen dosyadan XML parçalarını aktaran özel bir eksen yönteminin nasıl uygulanacağını ve kullanılacağını gösterir. Bu `Customer`özel eksen, , , ve `Name` `Item` öğeleri olan bir belge bekliyor ve bu öğeleri `Source.xml` yukarıdaki belgede olduğu gibi düzenlenecek şekilde yazılır. Bu basit bir uygulamadır. Geçersiz bir belgeyi ayrıştırmak için daha sağlam bir uygulama hazırlanacak.  
  
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
