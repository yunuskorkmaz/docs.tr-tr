---
title: LINQ - XML Genel Bakış (C#)
ms.date: 10/30/2018
ms.assetid: 716b94d3-0091-4de1-8e05-41bc069fa9dd
ms.openlocfilehash: 334788a50832b8fe42ecc9a3272dd71f2f2af4ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168421"
---
# <a name="linq-to-xml-overview-c"></a>LINQ - XML Genel Bakış (C#)

LINQ to XML, .NET Dil-Tümleşik Sorgu (LINQ) Çerçevesi'nden yararlanan bir bellek içi XML programlama arabirimi sağlar. LINQ to XML .NET özelliklerini kullanır ve güncelleştirilmiş, yeniden tasarlanmış Belge Nesnesi Modeli (DOM) XML programlama arabirimiile karşılaştırılabilir.

XML yaygın olarak birçok bağlamda veri biçimlendirmek için bir yol olarak kabul edilmiştir. Örneğin, XML'i Web'de, yapılandırma dosyalarında, Microsoft Office Word dosyalarında ve veritabanlarında bulabilirsiniz.

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]XML ile programlamaya güncel, yeniden tasarlanmış bir yaklaşımdır. Belge Nesnesi Modeli'nin (DOM) bellek içi belge değişiklik özelliklerini sağlar ve LINQ sorgu ifadelerini destekler. Bu sorgu ifadeleri sözdizimi olarak XPath'ten farklı olsa da, benzer işlevler sağlar.

## <a name="linq-to-xml-developers"></a>LINQ XML Geliştiriciler için

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]geliştiricilerin çeşitli hedefler. Sadece bir şey yapmak isteyen ortalama [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bir geliştirici için, SQL benzer bir sorgu deneyimi sağlayarak XML kolaylaştırır. Sadece biraz çalışma ile, programcılar tercih ettikleri programlama dilinde kısa ve güçlü sorgular yazmayı öğrenebilirsiniz.

Profesyonel geliştiriciler [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] büyük ölçüde verimliliklerini artırmak için kullanabilirsiniz. Ile [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], onlar daha anlamlı, daha kompakt ve daha güçlü daha az kod yazabilirsiniz. Aynı anda birden çok veri etki alanından gelen sorgu ifadelerini kullanabilirler.

## <a name="what-is-linq-to-xml"></a>XML'e LINQ Nedir?

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].NET Framework programlama dillerinden XML ile çalışmanızı sağlayan LINQ özellikli, bellek içi XML programlama arabirimidir.

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]XML belgesini belleğe getirdiği Belge Nesnesi Modeli (DOM) gibidir. Belgeyi sorgulayabilir ve değiştirebilir, değiştirdikten sonra da belgeyi bir dosyaya kaydedebilir veya seri hale getirebilir ve Internet üzerinden gönderebilirsiniz. Ancak, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] DOM farklıdır: Daha hafif ve çalışması daha kolay yeni bir nesne modeli sağlar ve C#'daki dil özelliklerinden yararlanır.

Bunun en önemli [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] avantajı, Dil-Entegre Sorgu (LINQ) ile bütünleşmesidir. Bu tümleştirme, öğelerin ve özniteliklerin koleksiyonlarını almak için bellek içi XML belgesine sorgu yazmanızı sağlar. Sorgu yeteneği [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] xpath ve XQuery işlevsellik (sözdiziminde olmasa da) karşılaştırılabilir. LINQ'nin C# ile tümleştirilmesi daha güçlü yazma, derleme zamanı denetimi ve geliştirilmiş hata ayıklama desteği sağlar.

Bir diğer [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] avantajı da sorgu sonuçlarını parametreler <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute> olarak kullanabilmektir ve nesne oluşturucular XML ağaçları oluşturmak için güçlü bir yaklaşım sağlar. *İşlevsel yapı*adı verilen bu yaklaşım, geliştiricilerin XML ağaçlarını bir şekilden diğerine kolayca dönüştürmelerine olanak tanır.

Örneğin, Örnek XML Dosyasında açıklandığı gibi tipik bir XML satın alma siparişine sahip [olabilirsiniz: Tipik Satınalma Siparişi (LINQ-XML)](sample-xml-file-typical-purchase-order-linq-to-xml-1.md). [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Kullanarak, satınalma siparişindeki her madde öğesi için parça numarası özniteliği değerini elde etmek için aşağıdaki sorguyu çalıştırabilirsiniz:

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load(purchaseOrderFilepath);

IEnumerable<string> partNos =  from item in purchaseOrder.Descendants("Item")
                               select (string) item.Attribute("PartNumber");
```

Bu yöntem sözdizimi şeklinde yeniden yazılabilir:

```csharp
IEnumerable<string> partNos = purchaseOrder.Descendants("Item").Select(x => (string) x.Attribute("PartNumber"));
```

Başka bir örnek olarak, değeri 100 TL'den büyük olan öğelerin parça numarasına göre sıralanmış bir liste isteyebilirsiniz. Bu bilgileri elde etmek için aşağıdaki sorguyu çalıştırabilirsiniz:

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

Yine, bu yöntem sözdizimi şeklinde yeniden yazılabilir:

```csharp
IEnumerable<XElement> pricesByPartNos = purchaseOrder.Descendants("Item")
                                        .Where(item => (int)item.Element("Quantity") * (decimal)item.Element("USPrice") > 100)
                                        .OrderBy(order => order.Element("PartNumber"));
```

Bu LINQ yeteneklerine ek [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] olarak, geliştirilmiş bir XML programlama arabirimi sağlar. Kullanarak, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]şunları yapabilirsiniz:

- [XML'i dosyalardan](how-to-load-xml-from-a-file.md) veya [akışlardan](how-to-stream-xml-fragments-from-an-xmlreader.md)yükleyin.

- XML'i dosyalara veya akışlara seri leştirin.

- Fonksiyonel yapıyı kullanarak sıfırdan XML oluşturun.

- XPath benzeri eksenler kullanarak XML sorgula.

- Bellek içi XML <xref:System.Xml.Linq.XContainer.Add%2A>ağacını , , <xref:System.Xml.Linq.XNode.Remove%2A> <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, ve <xref:System.Xml.Linq.XElement.SetValue%2A>.

- XSD kullanarak XML ağaçlarını doğrulayın.

- XML ağaçlarını bir şekilden diğerine dönüştürmek için bu özelliklerin bir birleşimini kullanın.

## <a name="creating-xml-trees"></a>XML Ağaçları Oluşturma

Programlamanın en önemli avantajlarından [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] biri XML ağaçları oluşturmak kolay olmasıdır. Örneğin, küçük bir XML ağacı oluşturmak için aşağıdaki gibi kod yazabilirsiniz:

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

Daha fazla bilgi için Bkz. [XML Ağaçları Oluşturma (C#)](./creating-xml-trees-linq-to-xml-2.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Başvuru (LINQ to XML)](./reference-linq-to-xml.md)
- [LINQ - XML vs. DOM (C#)](./linq-to-xml-vs-dom.md)
- [LINQ ve XML ve Diğer XML Teknolojileri](./linq-to-xml-vs-other-xml-technologies.md)
- <xref:System.Xml.Linq>
