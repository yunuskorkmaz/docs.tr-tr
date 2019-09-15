---
title: Geniş Yazılmış Uzantılar Örneği
ms.date: 03/30/2017
ms.assetid: 56ce265b-8163-4b85-98e7-7692a12c4357
ms.openlocfilehash: 6cfdef1d083a25999f62c23667c9c6ea00326dca
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989787"
---
# <a name="loosely-typed-extensions-sample"></a><span data-ttu-id="568f2-102">Geniş Yazılmış Uzantılar Örneği</span><span class="sxs-lookup"><span data-stu-id="568f2-102">Loosely-Typed Extensions Sample</span></span>
<span data-ttu-id="568f2-103">Dağıtım nesnesi modeli, uzantı verileriyle çalışma için zengin destek sağlar — bir dağıtım akışının xml gösteriminde bulunan ancak <xref:System.ServiceModel.Syndication.SyndicationFeed> ve <xref:System.ServiceModel.Syndication.SyndicationItem>gibi sınıflar tarafından açıkça gösterilmeyen bilgiler.</span><span class="sxs-lookup"><span data-stu-id="568f2-103">The Syndication object model provides rich support for working with extension data—information that is present in a syndication feed's XML representation but not explicitly exposed by classes such as <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem>.</span></span> <span data-ttu-id="568f2-104">Bu örnek, uzantı verileriyle çalışmaya yönelik temel teknikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="568f2-104">This sample illustrates the basic techniques for working with extension data.</span></span>  
  
 <span data-ttu-id="568f2-105">Örnek, örnek amacıyla <xref:System.ServiceModel.Syndication.SyndicationFeed> sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="568f2-105">The sample uses the <xref:System.ServiceModel.Syndication.SyndicationFeed> class for the purposes of the example.</span></span> <span data-ttu-id="568f2-106">Ancak, bu örnekte gösterilen desenler uzantı verilerini destekleyen tüm dağıtım sınıflarıyla birlikte kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="568f2-106">However, the patterns demonstrated in this sample can be used with all of the Syndication classes that support extension data:</span></span>  
  
 <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
 <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
 <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
 <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
## <a name="sample-xml"></a><span data-ttu-id="568f2-107">Örnek XML</span><span class="sxs-lookup"><span data-stu-id="568f2-107">Sample XML</span></span>  
 <span data-ttu-id="568f2-108">Başvuru için, bu örnekte aşağıdaki XML belgesi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="568f2-108">For reference, the following XML document is used in this sample.</span></span>  
  
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
  
 <span data-ttu-id="568f2-109">Bu belge aşağıdaki uzantı verisi parçalarını içerir:</span><span class="sxs-lookup"><span data-stu-id="568f2-109">This document contains the following pieces of extension data:</span></span>  
  
- <span data-ttu-id="568f2-110">`<feed>` Öğesinin `myAttribute` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="568f2-110">The `myAttribute` attribute of the `<feed>` element.</span></span>  
  
- <span data-ttu-id="568f2-111">`<simpleString>`dosyalarında.</span><span class="sxs-lookup"><span data-stu-id="568f2-111">`<simpleString>` element.</span></span>  
  
- <span data-ttu-id="568f2-112">`<DataContractExtension>`dosyalarında.</span><span class="sxs-lookup"><span data-stu-id="568f2-112">`<DataContractExtension>` element.</span></span>  
  
- <span data-ttu-id="568f2-113">`<XmlSerializerExtension>`dosyalarında.</span><span class="sxs-lookup"><span data-stu-id="568f2-113">`<XmlSerializerExtension>` element.</span></span>  
  
- <span data-ttu-id="568f2-114">`<xElementExtension>`dosyalarında.</span><span class="sxs-lookup"><span data-stu-id="568f2-114">`<xElementExtension>` element.</span></span>  
  
## <a name="writing-extension-data"></a><span data-ttu-id="568f2-115">Uzantı verileri yazma</span><span class="sxs-lookup"><span data-stu-id="568f2-115">Writing Extension Data</span></span>  
 <span data-ttu-id="568f2-116">Öznitelik uzantıları, aşağıdaki örnek kodda gösterildiği gibi <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> koleksiyona giriş eklenerek oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="568f2-116">Attribute extensions are created by adding entries to the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection as shown in the following sample code.</span></span>  
  
```csharp  
//Attribute extensions are stored in a dictionary indexed by   
// XmlQualifiedName  
feed.AttributeExtensions.Add(new XmlQualifiedName("myAttribute", ""), "someValue");  
```  
  
 <span data-ttu-id="568f2-117">Öğe uzantıları, <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> koleksiyona girdi eklenerek oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="568f2-117">Element extensions are created by adding entries to the <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> collection.</span></span> <span data-ttu-id="568f2-118">Bu uzantılar, dizeler gibi temel değerler, .NET Framework nesnelerin XML serileştirmeleri veya el ile kodlanmış XML düğümleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="568f2-118">These extensions can by basic values such as strings, XML serializations of .NET Framework objects, or XML nodes coded by hand.</span></span>  
  
 <span data-ttu-id="568f2-119">Aşağıdaki örnek kod adlı `simpleString`bir uzantı öğesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="568f2-119">The following sample code creates an extension element named `simpleString`.</span></span>  
  
```csharp  
feed.ElementExtensions.Add("simpleString", "", "hello, world!");  
```  
  
 <span data-ttu-id="568f2-120">Bu öğenin XML ad alanı boş ("") ad alanıdır ve değeri "Hello, World!" dizesini içeren bir metin düğümüdür.</span><span class="sxs-lookup"><span data-stu-id="568f2-120">The XML namespace for this element is the empty namespace ("") and its value is a text node that contains the string "hello, world!".</span></span>  
  
 <span data-ttu-id="568f2-121">Birçok iç içe öğeden oluşan karmaşık öğe uzantıları oluşturmanın bir yolu, aşağıdaki örneklerde gösterildiği gibi serileştirme için .NET Framework API 'leri kullanmaktır (hem <xref:System.Runtime.Serialization.DataContractSerializer> hem de <xref:System.Xml.Serialization.XmlSerializer> desteklenir).</span><span class="sxs-lookup"><span data-stu-id="568f2-121">One way to create complex element extensions that consist of many nested elements is to use the .NET Framework APIs for serialization (both the <xref:System.Runtime.Serialization.DataContractSerializer> and the <xref:System.Xml.Serialization.XmlSerializer> are supported) as shown in the following examples.</span></span>  
  
```csharp  
feed.ElementExtensions.Add( new DataContractExtension() { Key = "X", Value = 4 } );  
feed.ElementExtensions.Add( new XmlSerializerExtension { Key = "Y", Value = 8 }, new XmlSerializer( typeof( XmlSerializerExtension ) ) );  
```  
  
 <span data-ttu-id="568f2-122">Bu örnekte, ve `DataContractExtension` `XmlSerializerExtension` , serileştirici ile kullanılmak üzere yazılmış özel türlerdir.</span><span class="sxs-lookup"><span data-stu-id="568f2-122">In this example, the `DataContractExtension` and `XmlSerializerExtension` are custom types written for use with a serializer.</span></span>  
  
 <span data-ttu-id="568f2-123"><xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> Sınıfı bir<xref:System.Xml.XmlReader> örnekten öğe uzantıları oluşturmak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="568f2-123">The <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> class can also be used to create element extensions from an <xref:System.Xml.XmlReader> instance.</span></span> <span data-ttu-id="568f2-124">Bu, aşağıdaki örnek kodda gösterildiği gibi XML işleme API 'leriyle <xref:System.Xml.Linq.XElement> kolay tümleştirme sağlar.</span><span class="sxs-lookup"><span data-stu-id="568f2-124">This allows for easy integration with XML processing APIs such as <xref:System.Xml.Linq.XElement> as shown in the following sample code.</span></span>  
  
```csharp  
feed.ElementExtensions.Add(new XElement("xElementExtension",  
        new XElement("Key", new XAttribute("attr1", "someValue"), "Z"),  
        new XElement("Value", new XAttribute("attr1", "someValue"),   
        "15")).CreateReader());  
```  
  
## <a name="reading-extension-data"></a><span data-ttu-id="568f2-125">Uzantı verilerini okuma</span><span class="sxs-lookup"><span data-stu-id="568f2-125">Reading Extension Data</span></span>  
 <span data-ttu-id="568f2-126">Öznitelik uzantılarının değerleri, aşağıdaki örnek kodda gösterildiği <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> <xref:System.Xml.XmlQualifiedName> gibi, koleksiyonundaki özniteliğe bakılarak elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="568f2-126">The values for attribute extensions can be obtained by looking up the attribute in the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection by its <xref:System.Xml.XmlQualifiedName> as shown in the following sample code.</span></span>  
  
```csharp  
Console.WriteLine( feed.AttributeExtensions[ new XmlQualifiedName( "myAttribute", "" )]);  
```  
  
 <span data-ttu-id="568f2-127">Öğe uzantılarına `ReadElementExtensions<T>` yöntemi kullanılarak erişilir.</span><span class="sxs-lookup"><span data-stu-id="568f2-127">Element extensions are accessed using the `ReadElementExtensions<T>` method.</span></span>  
  
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
  
 <span data-ttu-id="568f2-128">Yöntemi kullanılarak tek tek öğe uzantıları elde `XmlReader` etmek de mümkündür. <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader></span><span class="sxs-lookup"><span data-stu-id="568f2-128">It is also possible to obtain an `XmlReader` at individual element extensions by using the <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader> method.</span></span>  
  
```csharp  
foreach (SyndicationElementExtension extension in feed2.ElementExtensions.Where<SyndicationElementExtension>(x => x.OuterName == "xElementExtension"))  
{  
    XNode xelement = XElement.ReadFrom(extension.GetReader());  
    Console.WriteLine(xelement.ToString());  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="568f2-129">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="568f2-129">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="568f2-130">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="568f2-130">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="568f2-131">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="568f2-131">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="568f2-132">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="568f2-132">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="568f2-133">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="568f2-133">The samples may already be installed on your machine.</span></span> <span data-ttu-id="568f2-134">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="568f2-134">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="568f2-135">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="568f2-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="568f2-136">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="568f2-136">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\LooselyTypedExtensions`  
  
## <a name="see-also"></a><span data-ttu-id="568f2-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="568f2-137">See also</span></span>

- [<span data-ttu-id="568f2-138">Kesin Tür Belirtilmiş Uzantılar</span><span class="sxs-lookup"><span data-stu-id="568f2-138">Strongly-Typed Extensions</span></span>](../../../../docs/framework/wcf/samples/strongly-typed-extensions-sample.md)
- [<span data-ttu-id="568f2-139">WCF Dağıtımı</span><span class="sxs-lookup"><span data-stu-id="568f2-139">WCF Syndication</span></span>](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
