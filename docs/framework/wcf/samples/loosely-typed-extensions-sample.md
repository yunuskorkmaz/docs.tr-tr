---
title: Geniş Yazılmış Uzantılar Örneği
ms.date: 03/30/2017
ms.assetid: 56ce265b-8163-4b85-98e7-7692a12c4357
ms.openlocfilehash: 9ad00c1e76d14b32cb28216cfdbb1a01f82a70cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33504443"
---
# <a name="loosely-typed-extensions-sample"></a><span data-ttu-id="2bb1b-102">Geniş Yazılmış Uzantılar Örneği</span><span class="sxs-lookup"><span data-stu-id="2bb1b-102">Loosely-Typed Extensions Sample</span></span>
<span data-ttu-id="2bb1b-103">Zengin destek uzantısı verilerle çalışmak için dağıtım nesnesi modeli sunar — akışı bir dağıtım mevcut olan bilgiler XML gösterimi kullanıcının ancak açıkça sınıfları tarafından gibi açığa <xref:System.ServiceModel.Syndication.SyndicationFeed> ve <xref:System.ServiceModel.Syndication.SyndicationItem>.</span><span class="sxs-lookup"><span data-stu-id="2bb1b-103">The Syndication object model provides rich support for working with extension data—information that is present in a syndication feed's XML representation but not explicitly exposed by classes such as <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem>.</span></span> <span data-ttu-id="2bb1b-104">Bu örnek uzantısı verilerle çalışmak için temel teknikleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2bb1b-104">This sample illustrates the basic techniques for working with extension data.</span></span>  
  
 <span data-ttu-id="2bb1b-105">Örnek kullanır <xref:System.ServiceModel.Syndication.SyndicationFeed> amacıyla sınıfının örneği.</span><span class="sxs-lookup"><span data-stu-id="2bb1b-105">The sample uses the <xref:System.ServiceModel.Syndication.SyndicationFeed> class for the purposes of the example.</span></span> <span data-ttu-id="2bb1b-106">Ancak, bu örnekte gösterilen desenler tüm uzantısını verileri destekleyen dağıtım sınıfları kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="2bb1b-106">However, the patterns demonstrated in this sample can be used with all of the Syndication classes that support extension data:</span></span>  
  
 <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
 <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
 <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
 <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
## <a name="sample-xml"></a><span data-ttu-id="2bb1b-107">Örnek XML</span><span class="sxs-lookup"><span data-stu-id="2bb1b-107">Sample XML</span></span>  
 <span data-ttu-id="2bb1b-108">Başvuru için bu örnekte aşağıdaki XML belgesi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2bb1b-108">For reference, the following XML document is used in this sample.</span></span>  
  
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
  
 <span data-ttu-id="2bb1b-109">Bu belge uzantısını verileri aşağıdaki parçalarını içerir:</span><span class="sxs-lookup"><span data-stu-id="2bb1b-109">This document contains the following pieces of extension data:</span></span>  
  
-   <span data-ttu-id="2bb1b-110">`myAttribute` Özniteliği `<feed>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="2bb1b-110">The `myAttribute` attribute of the `<feed>` element.</span></span>  
  
-   <span data-ttu-id="2bb1b-111">`<simpleString>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="2bb1b-111">`<simpleString>` element.</span></span>  
  
-   <span data-ttu-id="2bb1b-112">`<DataContractExtension>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="2bb1b-112">`<DataContractExtension>` element.</span></span>  
  
-   <span data-ttu-id="2bb1b-113">`<XmlSerializerExtension>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="2bb1b-113">`<XmlSerializerExtension>` element.</span></span>  
  
-   <span data-ttu-id="2bb1b-114">`<xElementExtension>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="2bb1b-114">`<xElementExtension>` element.</span></span>  
  
## <a name="writing-extension-data"></a><span data-ttu-id="2bb1b-115">Uzantı veri yazma</span><span class="sxs-lookup"><span data-stu-id="2bb1b-115">Writing Extension Data</span></span>  
 <span data-ttu-id="2bb1b-116">Öznitelik uzantıları girişlere ekleyerek oluşturulur <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> aşağıdaki örnek kodda gösterildiği gibi koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="2bb1b-116">Attribute extensions are created by adding entries to the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection as shown in the following sample code.</span></span>  
  
```  
//Attribute extensions are stored in a dictionary indexed by   
// XmlQualifiedName  
feed.AttributeExtensions.Add(new XmlQualifiedName("myAttribute", ""), "someValue");  
```  
  
 <span data-ttu-id="2bb1b-117">Öğe uzantıları girişlere ekleyerek oluşturulur <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="2bb1b-117">Element extensions are created by adding entries to the <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> collection.</span></span> <span data-ttu-id="2bb1b-118">Dizeleri, .NET Framework nesneleri veya el ile kodlanmış XML düğümlerini XML serializations gibi temel değerlere göre bu uzantıları olabilir.</span><span class="sxs-lookup"><span data-stu-id="2bb1b-118">These extensions can by basic values such as strings, XML serializations of .NET Framework objects, or XML nodes coded by hand.</span></span>  
  
 <span data-ttu-id="2bb1b-119">Aşağıdaki örnek kod adlı bir uzantı öğesi oluşturur `simpleString`.</span><span class="sxs-lookup"><span data-stu-id="2bb1b-119">The following sample code creates an extension element named `simpleString`.</span></span>  
  
```  
feed.ElementExtensions.Add("simpleString", "", "hello, world!");  
```  
  
 <span data-ttu-id="2bb1b-120">Bu öğe için XML ad alanı boş ad alanıdır ("") ve değerini "hello, world!" dizesini içeren bir metin düğümü.</span><span class="sxs-lookup"><span data-stu-id="2bb1b-120">The XML namespace for this element is the empty namespace ("") and its value is a text node that contains the string "hello, world!".</span></span>  
  
 <span data-ttu-id="2bb1b-121">İç içe öğelerin birçok oluşur karmaşık bir öğe uzantıları oluşturmak için tek yönlü olan seri hale getirme için .NET Framework API'ları kullanmak için (hem <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Xml.Serialization.XmlSerializer> desteklenir) aşağıdaki örneklerde gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="2bb1b-121">One way to create complex element extensions that consist of many nested elements is to use the .NET Framework APIs for serialization (both the <xref:System.Runtime.Serialization.DataContractSerializer> and the <xref:System.Xml.Serialization.XmlSerializer> are supported) as shown in the following examples.</span></span>  
  
```  
feed.ElementExtensions.Add( new DataContractExtension() { Key = "X", Value = 4 } );  
feed.ElementExtensions.Add( new XmlSerializerExtension { Key = "Y", Value = 8 }, new XmlSerializer( typeof( XmlSerializerExtension ) ) );  
```  
  
 <span data-ttu-id="2bb1b-122">Bu örnekte, `DataContractExtension` ve `XmlSerializerExtension` ile seri hale getirici kullanım için yazılan özel türü.</span><span class="sxs-lookup"><span data-stu-id="2bb1b-122">In this example, the `DataContractExtension` and `XmlSerializerExtension` are custom types written for use with a serializer.</span></span>  
  
 <span data-ttu-id="2bb1b-123"><xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> Sınıfı ayrıca öğesi Uzantılar'dan oluşturmak için kullanılabilir bir <xref:System.Xml.XmlReader> örneği.</span><span class="sxs-lookup"><span data-stu-id="2bb1b-123">The <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> class can also be used to create element extensions from an <xref:System.Xml.XmlReader> instance.</span></span> <span data-ttu-id="2bb1b-124">API'leri gibi işleme XML ile böylece kolay tümleştirme için <xref:System.Xml.Linq.XElement> aşağıdaki örnek kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="2bb1b-124">This allows for easy integration with XML processing APIs such as <xref:System.Xml.Linq.XElement> as shown in the following sample code.</span></span>  
  
```  
feed.ElementExtensions.Add(new XElement("xElementExtension",  
        new XElement("Key", new XAttribute("attr1", "someValue"), "Z"),  
        new XElement("Value", new XAttribute("attr1", "someValue"),   
        "15")).CreateReader());  
```  
  
## <a name="reading-extension-data"></a><span data-ttu-id="2bb1b-125">Uzantısını verileri okuma</span><span class="sxs-lookup"><span data-stu-id="2bb1b-125">Reading Extension Data</span></span>  
 <span data-ttu-id="2bb1b-126">Öznitelik uzantıları için değerleri özniteliğinde bakarak elde edilebilir <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> koleksiyona göre kendi <xref:System.Xml.XmlQualifiedName> aşağıdaki örnek kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="2bb1b-126">The values for attribute extensions can be obtained by looking up the attribute in the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection by its <xref:System.Xml.XmlQualifiedName> as shown in the following sample code.</span></span>  
  
```  
Console.WriteLine( feed.AttributeExtensions[ new XmlQualifiedName( "myAttribute", "" )]);  
```  
  
 <span data-ttu-id="2bb1b-127">Öğe uzantıları kullanılarak erişilir `ReadElementExtensions<T>` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2bb1b-127">Element extensions are accessed using the `ReadElementExtensions<T>` method.</span></span>  
  
```  
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
  
 <span data-ttu-id="2bb1b-128">Edinme mümkündür bir `XmlReader` kullanarak tek tek öğe uzantıları adresindeki <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2bb1b-128">It is also possible to obtain an `XmlReader` at individual element extensions by using the <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader> method.</span></span>  
  
```  
foreach (SyndicationElementExtension extension in feed2.ElementExtensions.Where<SyndicationElementExtension>(x => x.OuterName == "xElementExtension"))  
{  
    XNode xelement = XElement.ReadFrom(extension.GetReader());  
    Console.WriteLine(xelement.ToString());  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2bb1b-129">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="2bb1b-129">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="2bb1b-130">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2bb1b-130">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="2bb1b-131">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2bb1b-131">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="2bb1b-132">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2bb1b-132">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2bb1b-133">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="2bb1b-133">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2bb1b-134">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="2bb1b-134">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2bb1b-135">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="2bb1b-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2bb1b-136">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="2bb1b-136">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\LooselyTypedExtensions`  
  
## <a name="see-also"></a><span data-ttu-id="2bb1b-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2bb1b-137">See Also</span></span>  
 [<span data-ttu-id="2bb1b-138">Kesin Tür Belirtilmiş Uzantılar</span><span class="sxs-lookup"><span data-stu-id="2bb1b-138">Strongly-Typed Extensions</span></span>](../../../../docs/framework/wcf/samples/strongly-typed-extensions-sample.md)  
 [<span data-ttu-id="2bb1b-139">WCF Dağıtımı</span><span class="sxs-lookup"><span data-stu-id="2bb1b-139">WCF Syndication</span></span>](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
