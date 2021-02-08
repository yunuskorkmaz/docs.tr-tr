---
description: 'Daha fazla bilgi edinin: Loosely-Typed uzantıları örneği'
title: Geniş Yazılmış Uzantılar Örneği
ms.date: 03/30/2017
ms.assetid: 56ce265b-8163-4b85-98e7-7692a12c4357
ms.openlocfilehash: cd430a922a35baf0ed9ce387b7df81fa3af6b35d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793239"
---
# <a name="loosely-typed-extensions-sample"></a><span data-ttu-id="58bcd-103">Geniş Yazılmış Uzantılar Örneği</span><span class="sxs-lookup"><span data-stu-id="58bcd-103">Loosely-Typed Extensions Sample</span></span>

<span data-ttu-id="58bcd-104">Dağıtım nesnesi modeli, uzantı verileriyle çalışma için zengin destek sağlar — bir dağıtım akışının XML gösteriminde bulunan ancak ve gibi sınıflar tarafından açıkça gösterilmeyen bilgiler <xref:System.ServiceModel.Syndication.SyndicationFeed> <xref:System.ServiceModel.Syndication.SyndicationItem> .</span><span class="sxs-lookup"><span data-stu-id="58bcd-104">The Syndication object model provides rich support for working with extension data—information that is present in a syndication feed's XML representation but not explicitly exposed by classes such as <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem>.</span></span> <span data-ttu-id="58bcd-105">Bu örnek, uzantı verileriyle çalışmaya yönelik temel teknikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="58bcd-105">This sample illustrates the basic techniques for working with extension data.</span></span>  
  
 <span data-ttu-id="58bcd-106">Örnek, <xref:System.ServiceModel.Syndication.SyndicationFeed> örnek amacıyla sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="58bcd-106">The sample uses the <xref:System.ServiceModel.Syndication.SyndicationFeed> class for the purposes of the example.</span></span> <span data-ttu-id="58bcd-107">Ancak, bu örnekte gösterilen desenler uzantı verilerini destekleyen tüm dağıtım sınıflarıyla birlikte kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="58bcd-107">However, the patterns demonstrated in this sample can be used with all of the Syndication classes that support extension data:</span></span>  
  
 <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
 <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
 <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
 <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
## <a name="sample-xml"></a><span data-ttu-id="58bcd-108">Örnek XML</span><span class="sxs-lookup"><span data-stu-id="58bcd-108">Sample XML</span></span>  

 <span data-ttu-id="58bcd-109">Başvuru için, bu örnekte aşağıdaki XML belgesi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="58bcd-109">For reference, the following XML document is used in this sample.</span></span>  
  
```xml  
<?xml version="1.0" encoding="IBM437"?>  
<feed myAttribute="someValue" xmlns="http://www.w3.org/2005/Atom">  
  <title type="text"></title>  
  <id>uuid:8f60c7b3-a3c0-4de7-a642-2165d77ce3c1;id=1</id>  
  <updated>2007-09-07T22:15:34Z</updated>  
  <simpleString xmlns="">hello, world!</simpleString>  
  <simpleString xmlns="">another simple string</simpleString>  
  <DataContractExtension xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.d  
atacontract.org/2004/07/Microsoft.Syndication.Samples">  
    <Key>X</Key>  
    <Value>4</Value>  
  </DataContractExtension>  
  <XmlSerializerExtension xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://ww  
w.w3.org/2001/XMLSchema" xmlns="">  
    <Key>Y</Key>  
    <Value>8</Value>  
  </XmlSerializerExtension>  
  <xElementExtension xmlns="">  
    <Key attr1="someValue">Z</Key>  
    <Value attr1="someValue">15</Value>  
  </xElementExtension>  
</feed>  
```  
  
 <span data-ttu-id="58bcd-110">Bu belge aşağıdaki uzantı verisi parçalarını içerir:</span><span class="sxs-lookup"><span data-stu-id="58bcd-110">This document contains the following pieces of extension data:</span></span>  
  
- <span data-ttu-id="58bcd-111">`myAttribute` `<feed>` Öğesinin özniteliği.</span><span class="sxs-lookup"><span data-stu-id="58bcd-111">The `myAttribute` attribute of the `<feed>` element.</span></span>  
  
- <span data-ttu-id="58bcd-112">`<simpleString>` dosyalarında.</span><span class="sxs-lookup"><span data-stu-id="58bcd-112">`<simpleString>` element.</span></span>  
  
- <span data-ttu-id="58bcd-113">`<DataContractExtension>` dosyalarında.</span><span class="sxs-lookup"><span data-stu-id="58bcd-113">`<DataContractExtension>` element.</span></span>  
  
- <span data-ttu-id="58bcd-114">`<XmlSerializerExtension>` dosyalarında.</span><span class="sxs-lookup"><span data-stu-id="58bcd-114">`<XmlSerializerExtension>` element.</span></span>  
  
- <span data-ttu-id="58bcd-115">`<xElementExtension>` dosyalarında.</span><span class="sxs-lookup"><span data-stu-id="58bcd-115">`<xElementExtension>` element.</span></span>  
  
## <a name="writing-extension-data"></a><span data-ttu-id="58bcd-116">Uzantı verileri yazma</span><span class="sxs-lookup"><span data-stu-id="58bcd-116">Writing Extension Data</span></span>  

 <span data-ttu-id="58bcd-117">Öznitelik uzantıları, <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> Aşağıdaki örnek kodda gösterildiği gibi koleksiyona giriş eklenerek oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="58bcd-117">Attribute extensions are created by adding entries to the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection as shown in the following sample code.</span></span>  
  
```csharp  
//Attribute extensions are stored in a dictionary indexed by
// XmlQualifiedName  
feed.AttributeExtensions.Add(new XmlQualifiedName("myAttribute", ""), "someValue");  
```  
  
 <span data-ttu-id="58bcd-118">Öğe uzantıları, koleksiyona girdi eklenerek oluşturulur <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> .</span><span class="sxs-lookup"><span data-stu-id="58bcd-118">Element extensions are created by adding entries to the <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> collection.</span></span> <span data-ttu-id="58bcd-119">Bu uzantılar, dizeler gibi temel değerler, .NET Framework nesnelerin XML serileştirmeleri veya el ile kodlanmış XML düğümleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="58bcd-119">These extensions can by basic values such as strings, XML serializations of .NET Framework objects, or XML nodes coded by hand.</span></span>  
  
 <span data-ttu-id="58bcd-120">Aşağıdaki örnek kod adlı bir uzantı öğesi oluşturur `simpleString` .</span><span class="sxs-lookup"><span data-stu-id="58bcd-120">The following sample code creates an extension element named `simpleString`.</span></span>  
  
```csharp  
feed.ElementExtensions.Add("simpleString", "", "hello, world!");  
```  
  
 <span data-ttu-id="58bcd-121">Bu öğenin XML ad alanı boş ("") ad alanıdır ve değeri "Hello, World!" dizesini içeren bir metin düğümüdür.</span><span class="sxs-lookup"><span data-stu-id="58bcd-121">The XML namespace for this element is the empty namespace ("") and its value is a text node that contains the string "hello, world!".</span></span>  
  
 <span data-ttu-id="58bcd-122">Birçok iç içe öğeden oluşan karmaşık öğe uzantıları oluşturmanın bir yolu, aşağıdaki örneklerde gösterildiği gibi serileştirme için .NET Framework API 'Leri kullanmaktır (hem hem de <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Xml.Serialization.XmlSerializer> desteklenir).</span><span class="sxs-lookup"><span data-stu-id="58bcd-122">One way to create complex element extensions that consist of many nested elements is to use the .NET Framework APIs for serialization (both the <xref:System.Runtime.Serialization.DataContractSerializer> and the <xref:System.Xml.Serialization.XmlSerializer> are supported) as shown in the following examples.</span></span>  
  
```csharp  
feed.ElementExtensions.Add( new DataContractExtension() { Key = "X", Value = 4 } );  
feed.ElementExtensions.Add( new XmlSerializerExtension { Key = "Y", Value = 8 }, new XmlSerializer( typeof( XmlSerializerExtension ) ) );  
```  
  
 <span data-ttu-id="58bcd-123">Bu örnekte, ve, `DataContractExtension` `XmlSerializerExtension` serileştirici ile kullanılmak üzere yazılmış özel türlerdir.</span><span class="sxs-lookup"><span data-stu-id="58bcd-123">In this example, the `DataContractExtension` and `XmlSerializerExtension` are custom types written for use with a serializer.</span></span>  
  
 <span data-ttu-id="58bcd-124"><xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection>Sınıfı bir örnekten öğe uzantıları oluşturmak için de kullanılabilir <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="58bcd-124">The <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> class can also be used to create element extensions from an <xref:System.Xml.XmlReader> instance.</span></span> <span data-ttu-id="58bcd-125">Bu <xref:System.Xml.Linq.XElement> , aşağıdaki örnek kodda gösterildiği gıbı XML Işleme API 'leriyle kolay tümleştirme sağlar.</span><span class="sxs-lookup"><span data-stu-id="58bcd-125">This allows for easy integration with XML processing APIs such as <xref:System.Xml.Linq.XElement> as shown in the following sample code.</span></span>  
  
```csharp  
feed.ElementExtensions.Add(new XElement("xElementExtension",  
        new XElement("Key", new XAttribute("attr1", "someValue"), "Z"),  
        new XElement("Value", new XAttribute("attr1", "someValue"),
        "15")).CreateReader());  
```  
  
## <a name="reading-extension-data"></a><span data-ttu-id="58bcd-126">Uzantı verilerini okuma</span><span class="sxs-lookup"><span data-stu-id="58bcd-126">Reading Extension Data</span></span>  

 <span data-ttu-id="58bcd-127">Öznitelik uzantılarının değerleri, <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> <xref:System.Xml.XmlQualifiedName> Aşağıdaki örnek kodda gösterildiği gibi, koleksiyonundaki özniteliğe bakılarak elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="58bcd-127">The values for attribute extensions can be obtained by looking up the attribute in the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection by its <xref:System.Xml.XmlQualifiedName> as shown in the following sample code.</span></span>  
  
```csharp  
Console.WriteLine( feed.AttributeExtensions[ new XmlQualifiedName( "myAttribute", "" )]);  
```  
  
 <span data-ttu-id="58bcd-128">Öğe uzantılarına yöntemi kullanılarak erişilir `ReadElementExtensions<T>` .</span><span class="sxs-lookup"><span data-stu-id="58bcd-128">Element extensions are accessed using the `ReadElementExtensions<T>` method.</span></span>  
  
```csharp  
foreach( string s in feed2.ElementExtensions.ReadElementExtensions<string>("simpleString", ""))  
{  
    Console.WriteLine(s);  
}  
  
foreach (DataContractExtension dce in feed2.ElementExtensions.ReadElementExtensions<DataContractExtension>("DataContractExtension",  
"http://schemas.datacontract.org/2004/07/SyndicationExtensions"))  
{  
    Console.WriteLine(dce.ToString());  
}  
  
foreach (XmlSerializerExtension xse in feed2.ElementExtensions.ReadElementExtensions<XmlSerializerExtension>("XmlSerializerExtension", "", new XmlSerializer(typeof(XmlSerializerExtension))))  
{  
    Console.WriteLine(xse.ToString());  
}  
```  
  
 <span data-ttu-id="58bcd-129">`XmlReader`Yöntemi kullanılarak tek tek öğe uzantıları elde etmek de mümkündür <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader> .</span><span class="sxs-lookup"><span data-stu-id="58bcd-129">It is also possible to obtain an `XmlReader` at individual element extensions by using the <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader> method.</span></span>  
  
```csharp  
foreach (SyndicationElementExtension extension in feed2.ElementExtensions.Where<SyndicationElementExtension>(x => x.OuterName == "xElementExtension"))  
{  
    XNode xelement = XElement.ReadFrom(extension.GetReader());  
    Console.WriteLine(xelement.ToString());  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="58bcd-130">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="58bcd-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="58bcd-131">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="58bcd-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="58bcd-132">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="58bcd-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="58bcd-133">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="58bcd-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="58bcd-134">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="58bcd-134">The samples may already be installed on your machine.</span></span> <span data-ttu-id="58bcd-135">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="58bcd-135">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="58bcd-136">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="58bcd-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="58bcd-137">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="58bcd-137">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\LooselyTypedExtensions`  
  
## <a name="see-also"></a><span data-ttu-id="58bcd-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58bcd-138">See also</span></span>

- [<span data-ttu-id="58bcd-139">Türü kesin belirlenmiş uzantılar</span><span class="sxs-lookup"><span data-stu-id="58bcd-139">Strongly typed Extensions</span></span>](strongly-typed-extensions-sample.md)
- [<span data-ttu-id="58bcd-140">WCF Dağıtımı</span><span class="sxs-lookup"><span data-stu-id="58bcd-140">WCF Syndication</span></span>](../feature-details/wcf-syndication.md)
