---
title: C# ' de XML ağaçları oluşturma-LINQ to XML
description: C# ' de bir XML ağacını LINQ to XML XElement ve XAttribute oluşturucularını kullanarak oluşturabilirsiniz ve kodu temel alınan XML yapısına benzer hale getirebilirsiniz.
ms.date: 08/31/2018
ms.assetid: cc74234a-0bac-4327-9c8c-5a2ead15b595
ms.openlocfilehash: 97bf40d84f40eabf6fa84f10bf4febb7697b10f5
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553911"
---
# <a name="create-xml-trees-in-c-linq-to-xml"></a>C# dilinde XML ağaçları oluşturma (LINQ to XML)

Bu makalede C# dilinde XML ağaçları oluşturma hakkında bilgi sağlanır.

LINQ sorgularının sonuçlarını bir için içerik olarak kullanma hakkında daha fazla bilgi için <xref:System.Xml.Linq.XElement> bkz. [işlevsel oluşturma](functional-construction.md).

## <a name="construct-elements"></a>Yapı öğeleri

Ve oluşturucuların imzaları, <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute> öğe veya özniteliğin içeriğini oluşturucuya bağımsız değişken olarak geçirmenize olanak sağlar. Oluşturuculardan biri değişken sayıda bağımsız değişken kullandığından, herhangi bir sayıda alt öğe geçirebilirsiniz. Kuşkusuz, bu alt öğelerin her biri kendi alt öğelerini içerebilir. Herhangi bir öğe için istediğiniz sayıda öznitelik ekleyebilirsiniz.

<xref:System.Xml.Linq.XNode>(Dahil <xref:System.Xml.Linq.XElement> ) veya nesneleri eklerken <xref:System.Xml.Linq.XAttribute> , yeni içeriğin üst öğesi yoksa, nesneler yalnızca XML ağacına eklenir. Yeni içerik zaten üst öğe ise ve başka bir XML ağacının parçasıysa, yeni içerik kopyalanır ve yeni kopyalanan içerik XML ağacına eklenir. Bu makaledeki Son örnekte bu gösterilmektedir.

Oluşturmak için `contacts` <xref:System.Xml.Linq.XElement> aşağıdaki kodu kullanabilirsiniz:

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

Doğru şekilde girintilense, nesneleri oluşturmak için kullanılan kod, <xref:System.Xml.Linq.XElement> temel ALıNAN XML yapısına benzer.

## <a name="xelement-constructors"></a>XElement oluşturucuları

<xref:System.Xml.Linq.XElement>Sınıfı, işlevsel oluşturma için aşağıdaki oluşturucuları kullanır. İçin başka bazı oluşturucular olduğuna <xref:System.Xml.Linq.XElement> , ancak işlevsel oluşturma için kullanıldıklarından, burada listelenmemiştir.

|Oluşturucu|Description|
|-----------------|-----------------|
|`XElement(XName name, object content)`|Oluşturur <xref:System.Xml.Linq.XElement> . `name`Parametresi, öğesinin adını belirtir; `content` öğesinin içeriğini belirtir.|
|`XElement(XName name)`|<xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XName> Başlatıldıktan sonra belirtilen ada sahip bir oluşturur.|
|`XElement(XName name, params object[] content)`|<xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XName> Başlatıldıktan sonra belirtilen ada sahip bir oluşturur. Öznitelikler ve/veya alt öğeleri parametre listesinin içeriğinden oluşturulur.|

`content`Parametresi son derece esnektir. Geçerli bir alt öğesi olan herhangi bir nesne türünü destekler <xref:System.Xml.Linq.XElement> . Bu parametreye geçirilen farklı nesne türleri için aşağıdaki kurallar geçerlidir:

- Metin içeriği olarak bir dize eklenir.
- Bir <xref:System.Xml.Linq.XElement> alt öğesi olarak eklenir.
- Bir <xref:System.Xml.Linq.XAttribute> öznitelik olarak eklenir.
- <xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment> Veya <xref:System.Xml.Linq.XText> alt içerik olarak eklenir.
- Bir <xref:System.Collections.IEnumerable> numaralandırılır ve bu kurallar sonuçlara özyinelemeli olarak uygulanır.
- Diğer herhangi bir tür için, `ToString` metodu çağrılır ve sonuç metin içeriği olarak eklenir.

## <a name="example-create-an-xelement-with-content"></a>Örnek: içerikle birlikte XElement oluşturma

<xref:System.Xml.Linq.XElement>Tek bir yöntem çağrısıyla basit içerik içeren bir oluşturabilirsiniz. Bunu yapmak için, içeriği ikinci parametre olarak aşağıdaki gibi belirtin:

```csharp
XElement n = new XElement("Customer", "Adventure Works");
Console.WriteLine(n);
```

Bu örnek aşağıdaki çıktıyı üretir:

```xml
<Customer>Adventure Works</Customer>
```

Herhangi bir nesne türünü içerik olarak geçirebilirsiniz. Örneğin, aşağıdaki kod, içerik olarak kayan noktalı sayı içeren bir öğe oluşturur:

```csharp
XElement n = new XElement("Cost", 324.50);
Console.WriteLine(n);
```

Bu örnek aşağıdaki çıktıyı üretir:

```xml
<Cost>324.5</Cost>
```

Kayan nokta numarası paketlenmelidir ve oluşturucuya geçirilir. Kutulanmış sayı bir dizeye dönüştürülür ve öğesinin içeriği olarak kullanılır.

## <a name="example-create-an-xelement-with-a-child-element"></a>Örnek: bir alt öğe ile XElement oluşturma

<xref:System.Xml.Linq.XElement>İçerik bağımsız değişkeni için sınıfının bir örneğini geçirirseniz, Oluşturucu bir alt öğesi olan bir öğesi oluşturur:

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

## <a name="example-create-an-xelement-with-multiple-child-elements"></a>Örnek: birden çok alt öğe içeren bir XElement oluşturma

<xref:System.Xml.Linq.XElement>İçerik için bir dizi nesne geçirebilirsiniz. Nesnelerin her biri <xref:System.Xml.Linq.XElement> bir alt öğe olarak dahil edilir.

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

Önceki örneği genişleterek, bir XML ağacının tamamını aşağıdaki gibi oluşturabilirsiniz:

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

## <a name="example-create-an-xelement-with-an-xattribute"></a>Örnek: XAttribute ile XElement oluşturma

<xref:System.Xml.Linq.XAttribute>İçerik bağımsız değişkeni için sınıfının bir örneğini geçirirseniz, Oluşturucu bir özniteliği olan bir öğesi oluşturur:

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

## <a name="example-create-an-empty-element"></a>Örnek: boş bir öğe oluştur

Boş bir oluşturmak için <xref:System.Xml.Linq.XElement> , oluşturucuya herhangi bir içerik geçirmeyin. Aşağıdaki örnek boş bir öğe oluşturur:

```csharp
XElement n = new XElement("Customer");
Console.WriteLine(n);
```

Bu örnek aşağıdaki çıktıyı üretir:

```xml
<Customer />
```

## <a name="example-attach-vs-clone"></a>Örnek: Ekle ve Kopyala

Daha önce belirtildiği gibi, <xref:System.Xml.Linq.XNode> (dahil <xref:System.Xml.Linq.XElement> ) veya nesneleri eklerken (dahil), <xref:System.Xml.Linq.XAttribute> yeni içeriğin üst öğesi yoksa, nesneler yalnızca XML ağacına eklenir. Yeni içerik zaten üst öğe ise ve başka bir XML ağacının parçasıysa, yeni içerik kopyalanır ve yeni kopyalanan içerik XML ağacına eklenir.

Aşağıdaki örnek, bir ağaca bir üst öğeye sahip bir öğe eklediğinizde ve bir ağaca üst öğesi olmayan bir öğe eklediğinizde oluşan davranışı gösterir:

```csharp
// Create a tree with a child element.
XElement xmlTree1 = new XElement("Root",
    new XElement("Child1", 1)
);

// Create an element that's not parented.
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

// This example produces the following output:
//    Child1 was cloned
//    Child2 was attached
```

## <a name="see-also"></a>Ayrıca bkz.

- [İşlevsel oluşturma](functional-construction.md)
