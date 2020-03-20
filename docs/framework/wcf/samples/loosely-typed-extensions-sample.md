---
title: Geniş Yazılmış Uzantılar Örneği
ms.date: 03/30/2017
ms.assetid: 56ce265b-8163-4b85-98e7-7692a12c4357
ms.openlocfilehash: b8d1d42864b8764551cc44a26d820090eb28971e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183544"
---
# <a name="loosely-typed-extensions-sample"></a><span data-ttu-id="7b639-102">Geniş Yazılmış Uzantılar Örneği</span><span class="sxs-lookup"><span data-stu-id="7b639-102">Loosely-Typed Extensions Sample</span></span>
<span data-ttu-id="7b639-103">Sendikasyon nesnesi modeli, uzantı lı verilerle çalışmak için zengin destek sağlar— bir sendikasyon akışının XML <xref:System.ServiceModel.Syndication.SyndicationFeed> <xref:System.ServiceModel.Syndication.SyndicationItem>gösteriminde bulunan ancak bu tür sınıflar tarafından açıkça açığa alınmayan bilgiler.</span><span class="sxs-lookup"><span data-stu-id="7b639-103">The Syndication object model provides rich support for working with extension data—information that is present in a syndication feed's XML representation but not explicitly exposed by classes such as <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem>.</span></span> <span data-ttu-id="7b639-104">Bu örnek, uzantı verileriyle çalışmak için temel teknikleri göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="7b639-104">This sample illustrates the basic techniques for working with extension data.</span></span>  
  
 <span data-ttu-id="7b639-105">Örnek, <xref:System.ServiceModel.Syndication.SyndicationFeed> sınıfı örnek amaçları için kullanır.</span><span class="sxs-lookup"><span data-stu-id="7b639-105">The sample uses the <xref:System.ServiceModel.Syndication.SyndicationFeed> class for the purposes of the example.</span></span> <span data-ttu-id="7b639-106">Ancak, bu örnekte gösterilen desenler, uzantı verilerini destekleyen tüm Sendikasyon sınıfları ile kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="7b639-106">However, the patterns demonstrated in this sample can be used with all of the Syndication classes that support extension data:</span></span>  
  
 <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
 <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
 <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
 <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
## <a name="sample-xml"></a><span data-ttu-id="7b639-107">Örnek XML</span><span class="sxs-lookup"><span data-stu-id="7b639-107">Sample XML</span></span>  
 <span data-ttu-id="7b639-108">Başvuru için, bu örnekte aşağıdaki XML belgesi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7b639-108">For reference, the following XML document is used in this sample.</span></span>  
  
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
  
 <span data-ttu-id="7b639-109">Bu belge, aşağıdaki uzantı verileri parçalarını içerir:</span><span class="sxs-lookup"><span data-stu-id="7b639-109">This document contains the following pieces of extension data:</span></span>  
  
- <span data-ttu-id="7b639-110">Öğenin `myAttribute` `<feed>` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="7b639-110">The `myAttribute` attribute of the `<feed>` element.</span></span>  
  
- <span data-ttu-id="7b639-111">`<simpleString>`Öğe.</span><span class="sxs-lookup"><span data-stu-id="7b639-111">`<simpleString>` element.</span></span>  
  
- <span data-ttu-id="7b639-112">`<DataContractExtension>`Öğe.</span><span class="sxs-lookup"><span data-stu-id="7b639-112">`<DataContractExtension>` element.</span></span>  
  
- <span data-ttu-id="7b639-113">`<XmlSerializerExtension>`Öğe.</span><span class="sxs-lookup"><span data-stu-id="7b639-113">`<XmlSerializerExtension>` element.</span></span>  
  
- <span data-ttu-id="7b639-114">`<xElementExtension>`Öğe.</span><span class="sxs-lookup"><span data-stu-id="7b639-114">`<xElementExtension>` element.</span></span>  
  
## <a name="writing-extension-data"></a><span data-ttu-id="7b639-115">Uzantı Verilerini Yazma</span><span class="sxs-lookup"><span data-stu-id="7b639-115">Writing Extension Data</span></span>  
 <span data-ttu-id="7b639-116">Öznitelik uzantıları, aşağıdaki örnek kodda gösterildiği gibi <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> koleksiyona girişler eklenerek oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7b639-116">Attribute extensions are created by adding entries to the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection as shown in the following sample code.</span></span>  
  
```csharp  
//Attribute extensions are stored in a dictionary indexed by
// XmlQualifiedName  
feed.AttributeExtensions.Add(new XmlQualifiedName("myAttribute", ""), "someValue");  
```  
  
 <span data-ttu-id="7b639-117">Öğe uzantıları <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> koleksiyona girişler eklenerek oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7b639-117">Element extensions are created by adding entries to the <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> collection.</span></span> <span data-ttu-id="7b639-118">Bu uzantılar dizeleri, .NET Framework nesnelerinin XML serileştirmeleri veya elle kodlanmış XML düğümleri gibi temel değerlerle olabilir.</span><span class="sxs-lookup"><span data-stu-id="7b639-118">These extensions can by basic values such as strings, XML serializations of .NET Framework objects, or XML nodes coded by hand.</span></span>  
  
 <span data-ttu-id="7b639-119">Aşağıdaki örnek kod adlı `simpleString`bir uzantı öğesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7b639-119">The following sample code creates an extension element named `simpleString`.</span></span>  
  
```csharp  
feed.ElementExtensions.Add("simpleString", "", "hello, world!");  
```  
  
 <span data-ttu-id="7b639-120">Bu öğenin XML ad alanı boş ad alanıdır ("") ve değeri "merhaba, dünya!" dizesini içeren bir metin düğümüdür.</span><span class="sxs-lookup"><span data-stu-id="7b639-120">The XML namespace for this element is the empty namespace ("") and its value is a text node that contains the string "hello, world!".</span></span>  
  
 <span data-ttu-id="7b639-121">Birçok iç içe öğeden oluşan karmaşık öğe uzantıları oluşturmanın bir yolu, aşağıdaki örneklerde <xref:System.Runtime.Serialization.DataContractSerializer> gösterildiği <xref:System.Xml.Serialization.XmlSerializer> gibi .NET Framework API'lerini serileştirme (hem de desteklenir) için kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="7b639-121">One way to create complex element extensions that consist of many nested elements is to use the .NET Framework APIs for serialization (both the <xref:System.Runtime.Serialization.DataContractSerializer> and the <xref:System.Xml.Serialization.XmlSerializer> are supported) as shown in the following examples.</span></span>  
  
```csharp  
feed.ElementExtensions.Add( new DataContractExtension() { Key = "X", Value = 4 } );  
feed.ElementExtensions.Add( new XmlSerializerExtension { Key = "Y", Value = 8 }, new XmlSerializer( typeof( XmlSerializerExtension ) ) );  
```  
  
 <span data-ttu-id="7b639-122">Bu örnekte, `DataContractExtension` `XmlSerializerExtension` ve özel türleri bir serializer ile kullanılmak üzere yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="7b639-122">In this example, the `DataContractExtension` and `XmlSerializerExtension` are custom types written for use with a serializer.</span></span>  
  
 <span data-ttu-id="7b639-123">Sınıf, <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> bir <xref:System.Xml.XmlReader> örnekten öğe uzantıları oluşturmak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7b639-123">The <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> class can also be used to create element extensions from an <xref:System.Xml.XmlReader> instance.</span></span> <span data-ttu-id="7b639-124">Bu, aşağıdaki örnek kodda gösterildiği gibi <xref:System.Xml.Linq.XElement> XML işleme API'leri ile kolay entegrasyon sağlar.</span><span class="sxs-lookup"><span data-stu-id="7b639-124">This allows for easy integration with XML processing APIs such as <xref:System.Xml.Linq.XElement> as shown in the following sample code.</span></span>  
  
```csharp  
feed.ElementExtensions.Add(new XElement("xElementExtension",  
        new XElement("Key", new XAttribute("attr1", "someValue"), "Z"),  
        new XElement("Value", new XAttribute("attr1", "someValue"),
        "15")).CreateReader());  
```  
  
## <a name="reading-extension-data"></a><span data-ttu-id="7b639-125">Okuma Uzantısı Verileri</span><span class="sxs-lookup"><span data-stu-id="7b639-125">Reading Extension Data</span></span>  
 <span data-ttu-id="7b639-126">Öznitelik uzantıları için değerler, <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> aşağıdaki örnek kodda gösterildiği <xref:System.Xml.XmlQualifiedName> gibi koleksiyondaki özniteliğe bakarak elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="7b639-126">The values for attribute extensions can be obtained by looking up the attribute in the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection by its <xref:System.Xml.XmlQualifiedName> as shown in the following sample code.</span></span>  
  
```csharp  
Console.WriteLine( feed.AttributeExtensions[ new XmlQualifiedName( "myAttribute", "" )]);  
```  
  
 <span data-ttu-id="7b639-127">Öğe uzantıları `ReadElementExtensions<T>` yöntemi kullanılarak erişilir.</span><span class="sxs-lookup"><span data-stu-id="7b639-127">Element extensions are accessed using the `ReadElementExtensions<T>` method.</span></span>  
  
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
  
 <span data-ttu-id="7b639-128">Yöntemi kullanarak <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader> tek tek `XmlReader` eleman uzantıları elde etmek de mümkündür.</span><span class="sxs-lookup"><span data-stu-id="7b639-128">It is also possible to obtain an `XmlReader` at individual element extensions by using the <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader> method.</span></span>  
  
```csharp  
foreach (SyndicationElementExtension extension in feed2.ElementExtensions.Where<SyndicationElementExtension>(x => x.OuterName == "xElementExtension"))  
{  
    XNode xelement = XElement.ReadFrom(extension.GetReader());  
    Console.WriteLine(xelement.ToString());  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7b639-129">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="7b639-129">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="7b639-130">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="7b639-130">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="7b639-131">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="7b639-131">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="7b639-132">Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="7b639-132">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7b639-133">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="7b639-133">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7b639-134">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="7b639-134">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="7b639-135">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="7b639-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7b639-136">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="7b639-136">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\LooselyTypedExtensions`  
  
## <a name="see-also"></a><span data-ttu-id="7b639-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7b639-137">See also</span></span>

- [<span data-ttu-id="7b639-138">Güçlü Yazılmış Uzantılar</span><span class="sxs-lookup"><span data-stu-id="7b639-138">Strongly-Typed Extensions</span></span>](../../../../docs/framework/wcf/samples/strongly-typed-extensions-sample.md)
- [<span data-ttu-id="7b639-139">WCF Dağıtımı</span><span class="sxs-lookup"><span data-stu-id="7b639-139">WCF Syndication</span></span>](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
