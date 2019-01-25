---
title: C# (LINQ to XML) XML ağaçları oluşturma
ms.date: 08/31/2018
ms.assetid: cc74234a-0bac-4327-9c8c-5a2ead15b595
ms.openlocfilehash: 3bac7b62d04c9690cdd08d1993b64db33c4e6ab8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54503176"
---
# <a name="creating-xml-trees-in-c-linq-to-xml"></a>C# (LINQ to XML) XML ağaçları oluşturma
Bu bölümde, C# dilinde XML ağaçları oluşturma hakkında bilgi sağlar.  
  
 LINQ sorguları sonuçları içerik için kullanma hakkında bilgi için bir <xref:System.Xml.Linq.XElement>, bkz: [işlevsel oluşturma (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).  
  
## <a name="constructing-elements"></a>Öğeleri oluşturma
 İmzalarını <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XAttribute> oluşturucular içeriği öğe veya öznitelik oluşturucusu için bağımsız değişken olarak geçirmenize olanak tanır. Değişken sayıda bağımsız değişken bir oluşturucular yararlandığı için herhangi bir sayıda alt öğeleri geçirebilirsiniz. Elbette, bu alt öğelerin her biri kendi alt öğelerini içerebilir. Herhangi bir öğe için herhangi bir sayıda öznitelikler ekleyebilirsiniz.  
  
 Eklerken <xref:System.Xml.Linq.XNode> (dahil olmak üzere <xref:System.Xml.Linq.XElement>) veya <xref:System.Xml.Linq.XAttribute> nesneler, yeni içerik üstü yoksa, nesneleri yalnızca bağlı XML ağacına. Yeni içerik zaten üst öğe ve başka bir XML ağacının bir parçası ise, yeni içerik kopyalanmış olan ve yeni kopyalanan içeriği XML ağacına eklenir. Bu konu Son örnekte bu gösterir.  
  
 Oluşturmak için bir `contacts` <xref:System.Xml.Linq.XElement>, aşağıdaki kodu kullanabilirsiniz:  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),   
            new XElement("Phone", "206-555-0144"),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
```  
  
 Düzgün bir şekilde oluşturmak için kod girintili varsa <xref:System.Xml.Linq.XElement> nesneleri temel alınan XML yapısını çok benzeyen.  
  
## <a name="xelement-constructors"></a>XElement oluşturucular  
 <xref:System.Xml.Linq.XElement> Sınıfı için işlevsel oluşturma şu oluşturuculardan kullanır. Diğer bazı oluşturucular için olduğunu unutmayın <xref:System.Xml.Linq.XElement>, ancak bunlar listelenmediğinden burada işlevsel oluşturma için kullanılmaz.  
  
|Oluşturucu|Açıklama|  
|-----------------|-----------------|  
|`XElement(XName name, object content)`|Oluşturur bir <xref:System.Xml.Linq.XElement>. `name` Parametresi belirtir; öğe adı `content` öğenin içeriğini belirtir.|  
|`XElement(XName name)`|Oluşturur bir <xref:System.Xml.Linq.XElement> ile kendi <xref:System.Xml.Linq.XName> belirtilen adla başlatıldı.|  
|`XElement(XName name, params object[] content)`|Oluşturur bir <xref:System.Xml.Linq.XElement> ile kendi <xref:System.Xml.Linq.XName> belirtilen adla başlatıldı. Parametre listesi içeriğinden özniteliklerini ve/veya alt öğeleri oluşturulur.|  
  
 `content` Parametre son derece esnektir. Tür geçerli bir alt nesneyi destekleyen bir <xref:System.Xml.Linq.XElement>. Bu parametreye geçirilen nesneleri farklı türleri için aşağıdaki kurallar geçerlidir:  
  
-   Bir dizeyi metin içeriği olarak eklenir.  
  
-   Bir <xref:System.Xml.Linq.XElement> bir alt öğesi eklenir.  
  
-   Bir <xref:System.Xml.Linq.XAttribute> öznitelik olarak eklenir.  
  
-   Bir <xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment>, veya <xref:System.Xml.Linq.XText> alt içerik eklenir.  
  
-   Bir <xref:System.Collections.IEnumerable> numaralandırılmış alan şeklinde ve bu kuralların sonuçları için özyinelemeli olarak uygulanır.  
  
-   Başka herhangi bir tür için kendi `ToString` yöntemi çağrılır ve sonuç metin içeriği eklenir.  
  
### <a name="creating-an-xelement-with-content"></a>Bir XElement ile içerik oluşturma  
 Oluşturabileceğiniz bir <xref:System.Xml.Linq.XElement> içeren tek bir yöntem çağrısı ile basit içerik. Bunu yapmak için ikinci parametre olarak, içeriği aşağıdaki gibi belirtin:  
  
```csharp  
XElement n = new XElement("Customer", "Adventure Works");  
Console.WriteLine(n);  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
 Nesnesinin her türlü içeriği olarak geçirebilirsiniz. Örneğin, aşağıdaki kod bir değişken içeren bir öğe oluşturur nokta içerik olarak sayısı:  
  
```csharp  
XElement n = new XElement("Cost", 324.50);  
Console.WriteLine(n);  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<Cost>324.5</Cost>  
```  
  
 Kayan nokta numarası Kutulu ve oluşturucuya geçirilen. Paketlenmiş sayıyı bir dizeye dönüştürülür ve öğenin içeriğini kullanılan.  
  
### <a name="creating-an-xelement-with-a-child-element"></a>Bir XElement olan bir alt öğesi oluşturma  
 Örneği geçirirseniz <xref:System.Xml.Linq.XElement> sınıfı Oluşturucu içerik bağımsız değişkeni için olan bir alt öğesi bir öğe oluşturur:  
  
```csharp  
XElement shippingUnit = new XElement("ShippingUnit",  
    new XElement("Cost", 324.50)  
);  
Console.WriteLine(shippingUnit);  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<ShippingUnit>  
  <Cost>324.5</Cost>  
</ShippingUnit>  
```  
  
### <a name="creating-an-xelement-with-multiple-child-elements"></a>Bir XElement ile birden çok alt öğeleri oluşturma  
 Bir süre içinde geçirdiğiniz <xref:System.Xml.Linq.XElement> içerik için nesneleri. Her biri <xref:System.Xml.Linq.XElement> nesneleri bir alt öğesi eklenmiştir.  
  
```csharp  
XElement address = new XElement("Address",  
    new XElement("Street1", "123 Main St"),  
    new XElement("City", "Mercer Island"),  
    new XElement("State", "WA"),  
    new XElement("Postal", "68042")  
);  
Console.WriteLine(address);  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<Address>  
  <Street1>123 Main St</Street1>  
  <City>Mercer Island</City>  
  <State>WA</State>  
  <Postal>68042</Postal>  
</Address>  
```  
  
 Yukarıdaki örnekte genişleterek tüm XML ağacının, şu şekilde oluşturabilirsiniz:  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),                                                   
            new XElement("Phone", "206-555-0144"),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
Console.WriteLine(contacts);  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<Contacts>  
  <Contact>  
    <Name>Patrick Hines</Name>  
    <Phone>206-555-0144</Phone>  
    <Address>  
      <Street1>123 Main St</Street1>  
      <City>Mercer Island</City>  
      <State>WA</State>  
      <Postal>68042</Postal>  
    </Address>  
  </Contact>  
</Contacts>  
```  

### <a name="creating-an-xelement-with-an-xattribute"></a>Bir XElement bir XAttribute ile oluşturma
 Örneği geçirirseniz <xref:System.Xml.Linq.XAttribute> sınıfı Oluşturucu içerik bağımsız değişkeni bir öznitelik bir öğe oluşturur:

```csharp  
XElement phone = new XElement("Phone",  
    new XAttribute("Type", "Home"),  
    "555-555-5555");  
Console.WriteLine(phone);  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>
```   

### <a name="creating-an-empty-element"></a>Boş bir öğe oluşturma  
 Boş bir oluşturmak için <xref:System.Xml.Linq.XElement>, oluşturucuya herhangi bir içerik geçirmeyin. Aşağıdaki örnek, boş bir öğe oluşturur:  
  
```csharp  
XElement n = new XElement("Customer");  
Console.WriteLine(n);  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<Customer />  
```  
  
### <a name="attaching-vs-cloning"></a>Ekleme ve kopyalama  
 Eklerken daha önce de belirtildiği <xref:System.Xml.Linq.XNode> (dahil olmak üzere <xref:System.Xml.Linq.XElement>) veya <xref:System.Xml.Linq.XAttribute> nesneler, yeni içerik üstü yoksa, nesneleri yalnızca bağlı XML ağacına. Yeni içerik zaten üst öğe ve başka bir XML ağacının bir parçası ise, yeni içerik kopyalanmış olan ve yeni kopyalanan içeriği XML ağacına eklenir.  

Aşağıdaki örnek, bir ağaca üst öğeye sahip bir öğe eklediğinizde ve bir ağaca hiçbir üst öğesi ile bir öğe eklediğinizde davranış gösterir.

```csharp  
// Create a tree with a child element.  
XElement xmlTree1 = new XElement("Root",  
    new XElement("Child1", 1)  
);  
  
// Create an element that is not parented.  
XElement child2 = new XElement("Child2", 2);  
  
// Create a tree and add Child1 and Child2 to it.  
XElement xmlTree2 = new XElement("Root",  
    xmlTree1.Element("Child1"),  
    child2  
);  
  
// Compare Child1 identity.  
Console.WriteLine("Child1 was {0}",  
    xmlTree1.Element("Child1") == xmlTree2.Element("Child1") ?  
    "attached" : "cloned");  
  
// Compare Child2 identity.  
Console.WriteLine("Child2 was {0}",  
    child2 == xmlTree2.Element("Child2") ?  
    "attached" : "cloned");  

// The example displays the following output:  
//    Child1 was cloned  
//    Child2 was attached  
```

## <a name="see-also"></a>Ayrıca bkz.

- [XML ağaçları oluşturma (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
