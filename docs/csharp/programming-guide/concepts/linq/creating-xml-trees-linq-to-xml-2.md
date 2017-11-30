---
title: "C# (LINQ-XML) XML ağaçları oluşturma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: cc74234a-0bac-4327-9c8c-5a2ead15b595
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2e37ee7cd61058157b9c6c7d37784e215faf900a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="creating-xml-trees-in-c-linq-to-xml"></a>C# (LINQ-XML) XML ağaçları oluşturma
Bu bölümde XML ağaçları C# ' ta oluşturma hakkında bilgi sağlar.  
  
 LINQ sorgularını sonuçlarını için içerik olarak kullanma hakkında bilgi için bir <xref:System.Xml.Linq.XElement>, bkz: [işlevsel yapımı (LINQ-XML) (C#)](../../../../csharp/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).  
  
## <a name="constructing-elements"></a>Öğeleri oluşturma  
 İmzalarını <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XAttribute> oluşturucular öğe veya öznitelik içeriğini oluşturucuya bağımsız değişken olarak geçirmenize olanak tanır. Oluşturuculardan birine değişken sayıda bağımsız değişken aldığından herhangi bir sayıda alt öğelerini geçirebilirsiniz. Elbette, bu alt öğelerin her biri kendi alt öğelerini içerebilir. Herhangi bir öğe için herhangi bir sayıda öznitelikler ekleyebilirsiniz.  
  
 Eklerken <xref:System.Xml.Linq.XNode> (dahil olmak üzere <xref:System.Xml.Linq.XElement>) veya <xref:System.Xml.Linq.XAttribute> nesneler, yeni içeriğe üst öğeye sahipse, nesneleri basitçe bağlı XML ağacına. Yeni içerik zaten üst öğe ve başka bir XML ağacının bir parçası ise, yeni içerik kopyalanabilen ve yeni kopyalanmış içerik XML ağacına eklenir. Bu konudaki son örnek bu gösterir.  
  
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
  
 Doğru şekilde oluşturmak için kodu girintili varsa <xref:System.Xml.Linq.XElement> nesneleri temel alınan XML yapısını yakından benzer.  
  
## <a name="xelement-constructors"></a>XElement oluşturucular  
 <xref:System.Xml.Linq.XElement> Sınıfı, şu oluşturuculardan işlevsel yapımı için kullanır. Diğer bir oluşturucuları için Not <xref:System.Xml.Linq.XElement>, ancak bunlar listelenmez burada işlevsel yapımı için kullanılmaz.  
  
|Oluşturucu|Açıklama|  
|-----------------|-----------------|  
|`XElement(XName name, object content)`|Oluşturur bir <xref:System.Xml.Linq.XElement>. `name` Parametresi; öğesinin adını belirtir `content` öğenin içeriğini belirtir.|  
|`XElement(XName name)`|Oluşturur bir <xref:System.Xml.Linq.XElement> ile kendi <xref:System.Xml.Linq.XName> belirtilen adla başlatıldı.|  
|`XElement(XName name, params object[] content)`|Oluşturur bir <xref:System.Xml.Linq.XElement> ile kendi <xref:System.Xml.Linq.XName> belirtilen adla başlatıldı. Parametre listesi içeriğinden özniteliklerini ve/veya alt öğeleri oluşturulur.|  
  
 `content` Parametredir son derece esnek. Geçerli bir alt nesne herhangi bir türde destekleyen bir <xref:System.Xml.Linq.XElement>. Bu parametreye geçirilen nesneleri farklı türleri için aşağıdaki kurallar geçerlidir:  
  
-   Bir dize metin içeriği eklenir.  
  
-   Bir <xref:System.Xml.Linq.XElement> bir alt öğesi eklenir.  
  
-   Bir <xref:System.Xml.Linq.XAttribute> bir özniteliği olarak eklenir.  
  
-   Bir <xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment>, veya <xref:System.Xml.Linq.XText> alt içerik eklenir.  
  
-   Bir <xref:System.Collections.IEnumerable> numaralandırılan ve bu kuralları sonuçlara özyinelemeli olarak uygulanır.  
  
-   Diğer herhangi bir türü için kendi `ToString` yöntemi çağrılır ve sonuç metin içeriği eklenir.  
  
### <a name="creating-an-xelement-with-content"></a>İçerik ile bir XElement oluşturma  
 Oluşturabileceğiniz bir <xref:System.Xml.Linq.XElement> tek yöntem çağrısı basit içerikle içerir. Bunu yapmak için ikinci parametre olarak içeriği aşağıdaki gibi belirtin:  
  
```csharp  
XElement n = new XElement("Customer", "Adventure Works");  
Console.WriteLine(n);  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
 Herhangi bir türde nesne içeriği olarak geçirebilirsiniz. Örneğin, aşağıdaki kod bir kayan içeren bir öğeyi oluşturur nokta içerik olarak sayısı:  
  
```csharp  
XElement n = new XElement("Cost", 324.50);  
Console.WriteLine(n);  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<Cost>324.5</Cost>  
```  
  
 Kayan nokta sayısı Kutulu ve oluşturucuya geçirilen. Paketlenmiş numarası bir dizeye dönüştürülür ve öğenin içeriğini kullanılır.  
  
### <a name="creating-an-xelement-with-a-child-element"></a>Bir XElement olan bir alt öğesi oluşturma  
 Örneği geçirirseniz <xref:System.Xml.Linq.XElement> sınıfı oluşturucusu içerik bağımsız değişkeni için bir alt öğesi ile öğenin oluşturur:  
  
```csharp  
XElement shippingUnit = new XElement("ShippingUnit",  
    new XElement("Cost", 324.50)  
);  
Console.WriteLine(shippingUnit);  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<ShippingUnit>  
  <Cost>324.5</Cost>  
</ShippingUnit>  
```  
  
### <a name="creating-an-xelement-with-multiple-child-elements"></a>Birden çok alt öğesi ile bir XElement oluşturma  
 Bir süre içinde geçirdiğiniz <xref:System.Xml.Linq.XElement> içerik için nesneleri. Her biri <xref:System.Xml.Linq.XElement> nesneleri, bir alt öğesi eklenir.  
  
```csharp  
XElement address = new XElement("Address",  
    new XElement("Street1", "123 Main St"),  
    new XElement("City", "Mercer Island"),  
    new XElement("State", "WA"),  
    new XElement("Postal", "68042")  
);  
Console.WriteLine(address);  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<Address>  
  <Street1>123 Main St</Street1>  
  <City>Mercer Island</City>  
  <State>WA</State>  
  <Postal>68042</Postal>  
</Address>  
```  
  
 Yukarıdaki örnekte genişleterek, tüm bir XML ağacında aşağıdaki gibi oluşturabilirsiniz:  
  
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
  
 Bu örnek şu çıkışı üretir:  
  
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
  
### <a name="creating-an-empty-element"></a>Boş bir öğe oluşturma  
 Boş bir oluşturmak için <xref:System.Xml.Linq.XElement>, herhangi bir içerik oluşturucuya geçmeyin. Aşağıdaki örnek, boş bir öğesini oluşturur:  
  
```csharp  
XElement n = new XElement("Customer");  
Console.WriteLine(n);  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<Customer />  
```  
  
### <a name="attaching-vs-cloning"></a>VS ekleniyor. Kopyalama  
 Eklerken, daha önce belirtildiği gibi <xref:System.Xml.Linq.XNode> (dahil olmak üzere <xref:System.Xml.Linq.XElement>) veya <xref:System.Xml.Linq.XAttribute> nesneler, yeni içeriğe üst öğeye sahipse, nesneleri basitçe bağlı XML ağacına. Yeni içerik zaten üst öğe ve başka bir XML ağacının bir parçası ise, yeni içerik kopyalanabilen ve yeni kopyalanmış içerik XML ağacına eklenir.  
  
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
```  
  
 Bu örnek şu çıkışı üretir:  
  
```  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Oluşturma XML ağaçları (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
