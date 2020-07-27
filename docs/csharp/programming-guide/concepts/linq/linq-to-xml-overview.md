---
title: LINQ to XML genel bakış (C#)
description: LINQ to XML, bellek içi belge değiştirme özellikleri ve XPath gibi işlevlerle sorgu ifadeleri sağlamak için .NET LINQ Framework 'ten yararlanır.
ms.date: 10/30/2018
ms.assetid: 716b94d3-0091-4de1-8e05-41bc069fa9dd
ms.openlocfilehash: d2e4cf4e63d1a6ed7c1f0c163c12bb422b55ba11
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165349"
---
# <a name="linq-to-xml-overview-c"></a>LINQ to XML genel bakış (C#)

LINQ to XML, .NET dil ile tümleşik sorgu (LINQ) çerçevesini kullanan bellek içi bir XML programlama arabirimi sağlar. LINQ to XML, .NET yeteneklerini kullanır ve güncelleştirilmiş, yeniden tasarlanan Belge Nesne Modeli (DOM) XML programlama arabirimine benzer.

XML, çok sayıda bağlamdaki verileri biçimlendirmeye yönelik bir yöntem olarak çok daha benimsemiştir. Örneğin, Web 'de, yapılandırma dosyalarında, Microsoft Office Word dosyalarında ve veritabanlarında XML bulabilirsiniz.

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], XML ile programlamaya yönelik güncel ve yeniden tasarlanan bir yaklaşımdır. Belge Nesne Modeli (DOM) için bellek içi belge değiştirme yeteneklerini sağlar ve LINQ sorgu ifadelerini destekler. Bu sorgu ifadeleri XPath 'ten farklı bir şekilde farklılık içerse de, benzer işlevler sağlarlar.

## <a name="linq-to-xml-developers"></a>LINQ to XML geliştiriciler

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]çeşitli geliştiricileri hedefler. Yalnızca bir şey yapmak isteyen ortalama bir geliştirici için, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] SQL 'e benzer bir sorgu deneyimi sağlayarak xml 'i daha kolay hale getirir. Yalnızca bir çok çalışma sayesinde programcılar, tercih ettiğiniz programlama dilinde kısa ve güçlü sorgular yazmayı öğreniyor.

Profesyonel geliştiriciler, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] üretkenliğini önemli ölçüde artırmak için kullanabilir. İle [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , daha açıklayıcı, daha kompakt ve daha güçlü bir kod yazabilir. Aynı anda birden çok veri etki alanından sorgu ifadeleri kullanabilirler.

## <a name="what-is-linq-to-xml"></a>LINQ to XML nedir?

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], .NET programlama dillerinin içinden XML ile çalışmanıza olanak sağlayan, LINQ özellikli, bellek içi bir XML programlama arabirimidir.

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], XML belgesini belleğe getiren Belge Nesne Modeli (DOM) gibidir. Belgeyi sorgulayabilir ve değiştirebilir ve değişiklik yaptıktan sonra dosyayı bir dosyaya kaydedebilir veya seri hale getirebilirsiniz ve Internet üzerinden gönderebilirsiniz. Ancak, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Dom 'dan farklıdır: daha hafif ve daha kolay bir şekilde çalışmak ve C# ' deki dil özelliklerinden yararlanmak için daha kolay olan yeni bir nesne modeli sağlar.

Uygulamasının en önemli avantajı, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dil Ile tümleşik sorgu (LINQ) ile tümleştirmedir. Bu tümleştirme, öğelerin ve özniteliklerin koleksiyonlarını almak için bellek içi XML belgesi üzerinde sorgular yazmanızı sağlar. Öğesinin sorgu özelliği, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XPath ve XQuery için işlevsellik (sözdiziminde değil) ile karşılaştırılabilir. C# ' deki LINQ tümleştirmesi daha güçlü yazma, derleme zamanı denetimi ve geliştirilmiş hata ayıklayıcı desteği sağlar.

' In başka bir avantajı, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgu sonuçlarının parametre olarak kullanılması <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XAttribute> nesne oluşturucuları, xml ağaçları oluşturmaya yönelik güçlü bir yaklaşım sağlar. *İşlevsel oluşturma*olarak adlandırılan bu yaklaşım, geliştiricilerin XML ağaçlarını bir şekilden diğerine kolayca dönüştürmelerine olanak sağlar.

Örneğin, örnek XML dosyasında açıklandığı gibi tipik bir XML satın alma siparişiniz olabilir [: tipik satın alma siparişi (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml-1.md). Kullanarak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , satın alma sırasındaki her öğe öğesi için bölüm numarası öznitelik değerini almak üzere aşağıdaki sorguyu çalıştırabilirsiniz:

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load(purchaseOrderFilepath);

IEnumerable<string> partNos =  from item in purchaseOrder.Descendants("Item")
                               select (string) item.Attribute("PartNumber");
```

Bu, yöntem sözdizimi biçiminde yeniden yazılabilir:

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

Bu, yöntem sözdizimi biçiminde yeniden yazılabilir:

```csharp
IEnumerable<XElement> pricesByPartNos = purchaseOrder.Descendants("Item")
                                        .Where(item => (int)item.Element("Quantity") * (decimal)item.Element("USPrice") > 100)
                                        .OrderBy(order => order.Element("PartNumber"));
```

Bu LINQ özelliklerine ek olarak, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] geliştirilmiş BIR XML programlama arabirimi sağlar. Kullanarak şunları [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] yapabilirsiniz:

- [Dosyalardan](how-to-load-xml-from-a-file.md) veya [akışlardan](how-to-stream-xml-fragments-from-an-xmlreader.md)XML yükleyin.

- XML 'yi dosyalara veya akışlara seri hale getirme.

- İşlevsel oluşturma kullanarak sıfırdan XML oluşturun.

- XPath benzeri eksenleri kullanarak XML 'yi sorgula.

- ,, Ve gibi yöntemleri kullanarak bellek içi xml ağacını işleme <xref:System.Xml.Linq.XContainer.Add%2A> <xref:System.Xml.Linq.XNode.Remove%2A> <xref:System.Xml.Linq.XNode.ReplaceWith%2A> <xref:System.Xml.Linq.XElement.SetValue%2A> .

- XSD kullanarak XML ağaçlarını doğrulayın.

- XML ağaçlarını bir şekilden diğerine dönüştürmek için bu özelliklerin birleşimini kullanın.

## <a name="creating-xml-trees"></a>XML Ağaçları Oluşturma

Programlama kullanmanın en önemli avantajlarından biri, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] xml ağaçları oluşturmak kolaydır. Örneğin, küçük bir XML ağacı oluşturmak için aşağıdaki gibi bir kod yazabilirsiniz:

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

Daha fazla bilgi için bkz. [xml ağaçları oluşturma (C#)](./creating-xml-trees-linq-to-xml-2.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Başvuru (LINQ to XML)](./reference-linq-to-xml.md)
- [LINQ to XML vs. DOM (C#)](./linq-to-xml-vs-dom.md)
- [LINQ to XML ile Diğer XML Teknolojileri Karşılaştırması](./linq-to-xml-vs-other-xml-technologies.md)
- <xref:System.Xml.Linq>
