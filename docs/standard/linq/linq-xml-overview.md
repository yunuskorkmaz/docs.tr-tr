---
title: Genel Bakış-LINQ to XML
description: LINQ to XML, .NET özelliklerine dayanan ve güncelleştirilmiş bir DOM API 'sine benzer bir bellek içi XML programlama arabirimi sağlar.
ms.date: 10/30/2018
dev_langs:
- csharp
- vb
ms.assetid: 716b94d3-0091-4de1-8e05-41bc069fa9dd
ms.openlocfilehash: f805d757c9059a07988c6cb16e41ffed017fe853
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553357"
---
# <a name="linq-to-xml-overview"></a>LINQ to XML genel bakış

LINQ to XML, .NET dil ile tümleşik sorgu (LINQ) çerçevesini kullanan bellek içi bir XML programlama arabirimi sağlar. LINQ to XML, .NET yeteneklerini kullanır ve güncelleştirilmiş, yeniden tasarlanan Belge Nesne Modeli (DOM) XML programlama arabirimine benzer.

XML, çok sayıda bağlamdaki verileri biçimlendirmeye yönelik bir yöntem olarak çok daha benimsemiştir. Örneğin, Web 'de, yapılandırma dosyalarında, Microsoft Office Word dosyalarında ve veritabanlarında XML bulabilirsiniz.

LINQ to XML, XML ile programlamaya yönelik güncel ve yeniden tasarlanan bir yaklaşımdır. Belge Nesne Modeli (DOM) için bellek içi belge değiştirme yeteneklerini sağlar ve LINQ sorgu ifadelerini destekler. Bu sorgu ifadeleri XPath 'ten farklı bir şekilde farklılık içerse de, benzer işlevler sağlarlar.

## <a name="linq-to-xml-developers"></a>LINQ to XML geliştiriciler

LINQ to XML çeşitli geliştiricilere hedefler. Yalnızca bir şey yapmak isteyen ortalama bir geliştirici için, SQL 'e benzer bir sorgu deneyimi sağlayarak XML 'i daha kolay hale getirir LINQ to XML. Yalnızca bir çok çalışma sayesinde programcılar, tercih ettiğiniz programlama dilinde kısa ve güçlü sorgular yazmayı öğreniyor.

Profesyonel geliştiriciler, üretkenliğini önemli ölçüde artırmak için LINQ to XML kullanabilir. LINQ to XML sayesinde, daha açıklayıcı, daha kompakt ve daha güçlü bir kod yazabilir. Aynı anda birden çok veri etki alanından sorgu ifadeleri kullanabilirler.

## <a name="linq-to-xml-is-an-xml-programming-interface"></a>LINQ to XML bir XML programlama arabirimidir

LINQ to XML, .NET programlama dillerinin içinden XML ile çalışmanıza olanak sağlayan, LINQ özellikli, bellek içi bir XML programlama arabirimidir.

LINQ to XML, XML belgesini belleğe getiren Belge Nesne Modeli (DOM) gibidir. Belgeyi sorgulayabilir ve değiştirebilir ve değişiklik yaptıktan sonra dosyayı bir dosyaya kaydedebilir veya seri hale getirebilirsiniz ve Internet üzerinden gönderebilirsiniz. Ancak, LINQ to XML DOM 'dan farklıdır:

- Daha açık ağırlığı olan yeni bir nesne modeli sağlar ve bunlarla daha kolay çalışabilir.
- C# ve Visual Basic dil özelliklerinden yararlanır.

LINQ to XML en önemli avantajı, dil ile tümleşik sorgu (LINQ) ile tümleştirmedir. Bu tümleştirme, öğelerin ve özniteliklerin koleksiyonlarını almak için bellek içi XML belgesi üzerinde sorgular yazmanızı sağlar. LINQ to XML sorgu özelliği, XPath ve XQuery için (sözdiziminde olmasa da) işlev olarak karşılaştırılabilir. C# ve Visual Basic LINQ 'ın tümleştirilmesi, daha güçlü yazma, derleme zamanı denetimi ve geliştirilmiş hata ayıklayıcı desteği sağlar.

LINQ to XML başka bir avantajı, sorgu sonuçlarının parametre olarak kullanılması <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XAttribute> nesne OLUŞTURUCULARı, xml ağaçları oluşturmaya yönelik güçlü bir yaklaşım sağlar. *İşlevsel oluşturma*olarak adlandırılan bu yaklaşım, geliştiricilerin XML ağaçlarını bir şekilden diğerine kolayca dönüştürmelerine olanak sağlar.

Örneğin, [örnek xml dosyası: tipik satın alma siparişi](sample-xml-file-typical-purchase-order.md)bölümünde açıklandığı gibi tıpık bir XML satın alma siparişiniz olabilir. LINQ to XML kullanarak, satın alma sırasındaki her öğe öğesi için bölüm numarası öznitelik değerini almak üzere aşağıdaki sorguyu çalıştırabilirsiniz:

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load(purchaseOrderFilepath);

IEnumerable<string> partNos =  from item in purchaseOrder.Descendants("Item")
                               select (string) item.Attribute("PartNumber");
```

```vb
' Load the XML file from our project directory containing the purchase orders
Dim filename = "PurchaseOrder.xml"
Dim currentDirectory = Directory.GetCurrentDirectory()
Dim purchaseOrderFilepath = Path.Combine(currentDirectory, filename)

Dim purchaseOrder As XElement = XElement.Load(purchaseOrderFilepath)

Dim partNos = _
    From item In purchaseOrder...<Item> _
    Select item.@PartNumber
```

C# dilinde bu, yöntem sözdizimi biçiminde yeniden yazılabilir:

```csharp
IEnumerable<string> partNos = purchaseOrder.Descendants("Item").Select(x => (string) x.Attribute("PartNumber"));
```

Başka bir örnek olarak, $100 'den büyük bir değere sahip olan öğelerin bölüm numarasına göre sıralanmış bir liste olmasını isteyebilirsiniz. Bu bilgileri almak için aşağıdaki sorguyu çalıştırabilirsiniz:

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load(purchaseOrderFilepath);

IEnumerable<XElement> pricesByPartNos =  from item in purchaseOrder.Descendants("Item")
                                 where (int) item.Element("Quantity") * (decimal) item.Element("USPrice") > 100
                                 orderby (string)item.Element("PartNumber")
                                 select item;
```

```vb
' Load the XML file from our project directory containing the purchase orders
Dim filename = "PurchaseOrder.xml"
Dim currentDirectory = Directory.GetCurrentDirectory()
Dim purchaseOrderFilepath = Path.Combine(currentDirectory, filename)

Dim purchaseOrder As XElement = XElement.Load(purchaseOrderFilepath)

Dim partNos = _
From item In purchaseOrder...<Item> _
Where (item.<Quantity>.Value * _
       item.<USPrice>.Value) > 100 _
Order By item.<PartNumber>.Value _
Select item
```

Yine C# dilinde bu, yöntem sözdizimi biçiminde yeniden yazılabilir:

```csharp
IEnumerable<XElement> pricesByPartNos = purchaseOrder.Descendants("Item")
                                        .Where(item => (int)item.Element("Quantity") * (decimal)item.Element("USPrice") > 100)
                                        .OrderBy(order => order.Element("PartNumber"));
```

Bu LINQ özelliklerine ek olarak, LINQ to XML geliştirilmiş bir XML programlama arabirimi sağlar. LINQ to XML kullanarak şunları yapabilirsiniz:

- [Dosyalardan](load-xml-file.md) veya [akışlardan](stream-xml-fragments-xmlreader.md)XML yükleyin.
- XML 'yi dosyalara veya akışlara seri hale getirme.
- İşlevsel oluşturma kullanarak sıfırdan XML oluşturun.
- XPath benzeri eksenleri kullanarak XML 'yi sorgula.
- ,, Ve gibi yöntemleri kullanarak bellek içi xml ağacını işleme <xref:System.Xml.Linq.XContainer.Add%2A> <xref:System.Xml.Linq.XNode.Remove%2A> <xref:System.Xml.Linq.XNode.ReplaceWith%2A> <xref:System.Xml.Linq.XElement.SetValue%2A> .
- XSD kullanarak XML ağaçlarını doğrulayın.
- XML ağaçlarını bir şekilden diğerine dönüştürmek için bu özelliklerin birleşimini kullanın.

## <a name="create-xml-trees"></a>XML ağaçları oluşturma

LINQ to XML ile programlama kullanmanın en önemli avantajlarından biri, XML ağaçları oluşturmanın kolay bir işlemdir. Örneğin, küçük bir XML ağacı oluşturmak için aşağıdaki gibi bir kod yazabilirsiniz:

```csharp
XElement contacts =
new XElement("Contacts",
    new XElement("Contact",
        new XElement("Name", "Patrick Hines"),
        new XElement("Phone", "206-555-0144",
            new XAttribute("Type", "Home")),
        new XElement("phone", "425-555-0145",
            new XAttribute("Type", "Work")),
        new XElement("Address",
            new XElement("Street1", "123 Main St"),
            new XElement("City", "Mercer Island"),
            new XElement("State", "WA"),
            new XElement("Postal", "68042")
        )
    )
);
```

```vb
Dim contacts As XElement = _
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

> [!NOTE]
> Örneğin Visual Basic sürümü XML sabit değerlerini kullanır. Ayrıca <xref:System.Xml.Linq.XElement> , C# sürümünde olduğu gibi Visual Basic de kullanabilirsiniz.

Daha fazla bilgi için bkz. [xml ağaçları](functional-construction.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Başvuru](reference.md)
- [LINQ to XML ile DOM Karşılaştırması](linq-xml-vs-dom.md)
- [LINQ to XML ve diğer XML Teknolojileri](linq-xml-vs-xml-technologies.md)
- <xref:System.Xml.Linq>
