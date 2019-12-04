---
title: Geniş Yazılmış Uzantılar Örneği
ms.date: 03/30/2017
ms.assetid: 56ce265b-8163-4b85-98e7-7692a12c4357
ms.openlocfilehash: f3beed9b9ca1dd6b1d4bb32078e6cd35a636501c
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714876"
---
# <a name="loosely-typed-extensions-sample"></a>Geniş Yazılmış Uzantılar Örneği
Dağıtım nesnesi modeli, uzantı verileriyle çalışma için zengin destek sağlar — bir dağıtım akışının XML gösteriminde bulunan ancak <xref:System.ServiceModel.Syndication.SyndicationFeed> ve <xref:System.ServiceModel.Syndication.SyndicationItem>gibi sınıflar tarafından açıkça gösterilmeyen bilgiler. Bu örnek, uzantı verileriyle çalışmaya yönelik temel teknikleri gösterir.  
  
 Örnek, örnek amaçları için <xref:System.ServiceModel.Syndication.SyndicationFeed> sınıfını kullanır. Ancak, bu örnekte gösterilen desenler uzantı verilerini destekleyen tüm dağıtım sınıflarıyla birlikte kullanılabilir:  
  
 <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
 <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
 <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
 <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
## <a name="sample-xml"></a>Örnek XML  
 Başvuru için, bu örnekte aşağıdaki XML belgesi kullanılır.  
  
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
  
 Bu belge aşağıdaki uzantı verisi parçalarını içerir:  
  
- `<feed>` öğesinin `myAttribute` özniteliği.  
  
- `<simpleString>` öğesi.  
  
- `<DataContractExtension>` öğesi.  
  
- `<XmlSerializerExtension>` öğesi.  
  
- `<xElementExtension>` öğesi.  
  
## <a name="writing-extension-data"></a>Uzantı verileri yazma  
 Öznitelik uzantıları, aşağıdaki örnek kodda gösterildiği gibi <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> koleksiyonuna girdi eklenerek oluşturulur.  
  
```csharp  
//Attribute extensions are stored in a dictionary indexed by   
// XmlQualifiedName  
feed.AttributeExtensions.Add(new XmlQualifiedName("myAttribute", ""), "someValue");  
```  
  
 Öğe uzantıları, <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> koleksiyonuna girdi eklenerek oluşturulur. Bu uzantılar, dizeler gibi temel değerler, .NET Framework nesnelerin XML serileştirmeleri veya el ile kodlanmış XML düğümleri olabilir.  
  
 Aşağıdaki örnek kod, `simpleString`adlı bir uzantı öğesi oluşturur.  
  
```csharp  
feed.ElementExtensions.Add("simpleString", "", "hello, world!");  
```  
  
 Bu öğenin XML ad alanı boş ("") ad alanıdır ve değeri "Hello, World!" dizesini içeren bir metin düğümüdür.  
  
 Birçok iç içe öğeden oluşan karmaşık öğe uzantıları oluşturmanın bir yolu, aşağıdaki örneklerde gösterildiği gibi, serileştirme için .NET Framework API 'Leri (<xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Xml.Serialization.XmlSerializer> desteklenir) kullanmaktır.  
  
```csharp  
feed.ElementExtensions.Add( new DataContractExtension() { Key = "X", Value = 4 } );  
feed.ElementExtensions.Add( new XmlSerializerExtension { Key = "Y", Value = 8 }, new XmlSerializer( typeof( XmlSerializerExtension ) ) );  
```  
  
 Bu örnekte `DataContractExtension` ve `XmlSerializerExtension`, serileştirici ile kullanılmak üzere yazılmış özel türlerdir.  
  
 <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> sınıfı, bir <xref:System.Xml.XmlReader> örneğinden öğe uzantıları oluşturmak için de kullanılabilir. Bu, aşağıdaki örnek kodda gösterildiği gibi, <xref:System.Xml.Linq.XElement> gibi XML işleme API 'Leriyle kolay tümleştirme sağlar.  
  
```csharp  
feed.ElementExtensions.Add(new XElement("xElementExtension",  
        new XElement("Key", new XAttribute("attr1", "someValue"), "Z"),  
        new XElement("Value", new XAttribute("attr1", "someValue"),   
        "15")).CreateReader());  
```  
  
## <a name="reading-extension-data"></a>Uzantı verilerini okuma  
 Öznitelik uzantılarının değerleri, aşağıdaki örnek kodda gösterildiği gibi, <xref:System.Xml.XmlQualifiedName> tarafından <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> koleksiyonundaki özniteliğe bakılarak elde edilebilir.  
  
```csharp  
Console.WriteLine( feed.AttributeExtensions[ new XmlQualifiedName( "myAttribute", "" )]);  
```  
  
 Öğe uzantılarına `ReadElementExtensions<T>` yöntemi kullanılarak erişilir.  
  
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
  
 Ayrıca, <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader> yöntemi kullanılarak tekil öğe uzantılarında `XmlReader` elde etmek de mümkündür.  
  
```csharp  
foreach (SyndicationElementExtension extension in feed2.ElementExtensions.Where<SyndicationElementExtension>(x => x.OuterName == "xElementExtension"))  
{  
    XNode xelement = XElement.ReadFrom(extension.GetReader());  
    Console.WriteLine(xelement.ToString());  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\LooselyTypedExtensions`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kesin Tür Belirtilmiş Uzantılar](../../../../docs/framework/wcf/samples/strongly-typed-extensions-sample.md)
- [WCF Dağıtımı](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
