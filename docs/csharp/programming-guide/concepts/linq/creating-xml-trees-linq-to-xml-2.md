---
title: C# Dilinde XML Ağaçları Oluşturma (LINQ to XML)
ms.date: 08/31/2018
ms.assetid: cc74234a-0bac-4327-9c8c-5a2ead15b595
ms.openlocfilehash: 4794e4fe019b30d8f2acb3eb255bb77ba2f7f290
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169551"
---
# <a name="creating-xml-trees-in-c-linq-to-xml"></a>C# 'da XML ağaçları oluşturma (LINQ-XML)
Bu bölümde C#'da XML ağaçları oluşturma hakkında bilgi verilmektedir.  
  
 Linq sorgularının sonuçlarını bir <xref:System.Xml.Linq.XElement>içerik olarak kullanma hakkında bilgi için bkz: Fonksiyonel Yapı [(LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).  
  
## <a name="constructing-elements"></a>Öğeleri oluşturma
 Ve <xref:System.Xml.Linq.XAttribute> oluşturucuların <xref:System.Xml.Linq.XElement> imzaları, öğenin içeriğini veya özniteliği oluşturucuya bağımsız değişken olarak geçirmenize izin verebiliyor. Oluşturuculardan biri değişken sayıda bağımsız değişken aldığından, herhangi bir sayıda alt öğeyi geçirebilirsiniz. Tabii ki, bu alt öğelerin her biri kendi alt öğeleri içerebilir. Herhangi bir öğe için, herhangi bir sayıda öznitelik ekleyebilirsiniz.  
  
 Eklerken <xref:System.Xml.Linq.XNode> (dahil) <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute> veya nesneler, yeni içeriğin üst öğesi yoksa, nesneler yalnızca XML ağacına eklenir. Yeni içerik zaten ebeveynliyse ve başka bir XML ağacının parçasıysa, yeni içerik klonlanır ve yeni klonlanan içerik XML ağacına eklenir. Bu konudaki son örnek bunu göstermektedir.  
  
 Bir `contacts` <xref:System.Xml.Linq.XElement>, oluşturmak için aşağıdaki kodu kullanabilirsiniz:  
  
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
  
 Düzgün girintisi varsa, nesneleri <xref:System.Xml.Linq.XElement> oluşturmak için kod yakından temel XML yapısına benzer.  
  
## <a name="xelement-constructors"></a>XElement yapıcılar  
 Sınıf, <xref:System.Xml.Linq.XElement> işlevsel yapı için aşağıdaki yapıcıları kullanır. Bazı diğer yapıcılar için <xref:System.Xml.Linq.XElement>olduğunu unutmayın , ancak işlevsel inşaat için kullanılmadığı için burada listelenmez.  
  
|Oluşturucu|Açıklama|  
|-----------------|-----------------|  
|`XElement(XName name, object content)`|Bir <xref:System.Xml.Linq.XElement>. `name` Parametre öğenin adını belirtir; `content` öğenin içeriğini belirtir.|  
|`XElement(XName name)`|Belirtilen ada <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XName> başharfleri olan bir oluşturur.|  
|`XElement(XName name, params object[] content)`|Belirtilen ada <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XName> başharfleri olan bir oluşturur. Öznitelikler ve/veya alt öğeler parametre listesinin içeriğinden oluşturulur.|  
  
 Parametre `content` son derece esnektir. Geçerli bir alt olan herhangi bir nesne <xref:System.Xml.Linq.XElement>türünü destekler. Aşağıdaki kurallar, bu parametrede geçirilen farklı nesne türleri için geçerlidir:  
  
- Metin içeriği olarak bir dize eklenir.  
  
- Bir <xref:System.Xml.Linq.XElement> alt öğe olarak eklenir.  
  
- Bir <xref:System.Xml.Linq.XAttribute> öznitelik olarak eklenir.  
  
- Bir <xref:System.Xml.Linq.XProcessingInstruction> <xref:System.Xml.Linq.XComment>, <xref:System.Xml.Linq.XText> veya alt içerik olarak eklenir.  
  
- Bir <xref:System.Collections.IEnumerable> numaranumaralanır ve bu kurallar sonuçlara özyinelemeli olarak uygulanır.  
  
- Başka bir tür `ToString` için, yöntemi çağrılır ve sonuç metin içeriği olarak eklenir.  
  
### <a name="creating-an-xelement-with-content"></a>İçerikle XElement Oluşturma  
 Tek bir <xref:System.Xml.Linq.XElement> yöntem çağrısıyla basit içerik içeren bir yöntem oluşturabilirsiniz. Bunu yapmak için, içeriği ikinci parametre olarak aşağıdaki gibi belirtin:  
  
```csharp  
XElement n = new XElement("Customer", "Adventure Works");  
Console.WriteLine(n);  
```  
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
 İçerik olarak herhangi bir nesne türünü geçirebilirsiniz. Örneğin, aşağıdaki kod içerik olarak kayan nokta numarası içeren bir öğe oluşturur:  
  
```csharp  
XElement n = new XElement("Cost", 324.50);  
Console.WriteLine(n);  
```  
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```xml  
<Cost>324.5</Cost>  
```  
  
 Kayan nokta numarası kutulanır ve yapıcıya aktarılır. Kutulu sayı bir dize dönüştürülür ve öğenin içeriği olarak kullanılır.  
  
### <a name="creating-an-xelement-with-a-child-element"></a>Alt öğeyle xele oluşturma  
 İçerik bağımsız değişkeni <xref:System.Xml.Linq.XElement> için sınıfın bir örneğini geçerseniz, oluşturucu alt öğeiçeren bir öğe oluşturur:  
  
```csharp  
XElement shippingUnit = new XElement("ShippingUnit",  
    new XElement("Cost", 324.50)  
);  
Console.WriteLine(shippingUnit);  
```  
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```xml  
<ShippingUnit>  
  <Cost>324.5</Cost>  
</ShippingUnit>  
```  
  
### <a name="creating-an-xelement-with-multiple-child-elements"></a>Birden çok alt öğeiçeren bir XElement oluşturma  
 İçerik için bir dizi <xref:System.Xml.Linq.XElement> nesne geçirebilirsiniz. <xref:System.Xml.Linq.XElement> Nesnelerin her biri bir alt öğe olarak dahildir.  
  
```csharp  
XElement address = new XElement("Address",  
    new XElement("Street1", "123 Main St"),  
    new XElement("City", "Mercer Island"),  
    new XElement("State", "WA"),  
    new XElement("Postal", "68042")  
);  
Console.WriteLine(address);  
```  
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```xml  
<Address>  
  <Street1>123 Main St</Street1>  
  <City>Mercer Island</City>  
  <State>WA</State>  
  <Postal>68042</Postal>  
</Address>  
```  
  
 Yukarıdaki örneği genişleterek, aşağıdaki gibi tüm bir XML ağacı oluşturabilirsiniz:  
  
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
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
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

### <a name="creating-an-xelement-with-an-xattribute"></a>XAttribute ile XElement oluşturma
 İçerik bağımsız değişkeni <xref:System.Xml.Linq.XAttribute> için sınıfın bir örneğini geçerseniz, oluşturucu özniteliği olan bir öğe oluşturur:

```csharp  
XElement phone = new XElement("Phone",  
    new XAttribute("Type", "Home"),  
    "555-555-5555");  
Console.WriteLine(phone);  
```  
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>
```

### <a name="creating-an-empty-element"></a>Boş bir öğe oluşturma  
 Boş <xref:System.Xml.Linq.XElement>bir , oluşturucuya herhangi bir içerik geçirmedin. Aşağıdaki örnek boş bir öğe oluşturur:  
  
```csharp  
XElement n = new XElement("Customer");  
Console.WriteLine(n);  
```  
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```xml  
<Customer />  
```  
  
### <a name="attaching-vs-cloning"></a>Yapıştırma ve klonlama  
 Daha önce de belirtildiği <xref:System.Xml.Linq.XNode> gibi, <xref:System.Xml.Linq.XElement>eklerken <xref:System.Xml.Linq.XAttribute> (dahil) veya nesneler, yeni içeriğin üst öğesi yoksa, nesneler yalnızca XML ağacına eklenir. Yeni içerik zaten ebeveynliyse ve başka bir XML ağacının parçasıysa, yeni içerik klonlanır ve yeni klonlanan içerik XML ağacına eklenir.  

Aşağıdaki örnek, bir ağaca bir üst öğe eklediğinizde ve bir ağaca üst öğesi eklemediğinizde davranışı gösterir.

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

- [XML Ağaçları Oluşturma (C#)](./linq-to-xml-overview.md)
