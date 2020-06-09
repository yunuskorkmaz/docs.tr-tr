---
title: Geniş Yazılmış Uzantılar Örneği
ms.date: 03/30/2017
ms.assetid: 56ce265b-8163-4b85-98e7-7692a12c4357
ms.openlocfilehash: 0a08ca19e5e6bff7223d45726617d2c2163ca3df
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591871"
---
# <a name="loosely-typed-extensions-sample"></a>Geniş Yazılmış Uzantılar Örneği
Dağıtım nesnesi modeli, uzantı verileriyle çalışma için zengin destek sağlar — bir dağıtım akışının XML gösteriminde bulunan ancak ve gibi sınıflar tarafından açıkça gösterilmeyen bilgiler <xref:System.ServiceModel.Syndication.SyndicationFeed> <xref:System.ServiceModel.Syndication.SyndicationItem> . Bu örnek, uzantı verileriyle çalışmaya yönelik temel teknikleri gösterir.  
  
 Örnek, <xref:System.ServiceModel.Syndication.SyndicationFeed> örnek amacıyla sınıfını kullanır. Ancak, bu örnekte gösterilen desenler uzantı verilerini destekleyen tüm dağıtım sınıflarıyla birlikte kullanılabilir:  
  
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
  
- `myAttribute` `<feed>` Öğesinin özniteliği.  
  
- `<simpleString>`dosyalarında.  
  
- `<DataContractExtension>`dosyalarında.  
  
- `<XmlSerializerExtension>`dosyalarında.  
  
- `<xElementExtension>`dosyalarında.  
  
## <a name="writing-extension-data"></a>Uzantı verileri yazma  
 Öznitelik uzantıları, <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> Aşağıdaki örnek kodda gösterildiği gibi koleksiyona giriş eklenerek oluşturulur.  
  
```csharp  
//Attribute extensions are stored in a dictionary indexed by
// XmlQualifiedName  
feed.AttributeExtensions.Add(new XmlQualifiedName("myAttribute", ""), "someValue");  
```  
  
 Öğe uzantıları, koleksiyona girdi eklenerek oluşturulur <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> . Bu uzantılar, dizeler gibi temel değerler, .NET Framework nesnelerin XML serileştirmeleri veya el ile kodlanmış XML düğümleri olabilir.  
  
 Aşağıdaki örnek kod adlı bir uzantı öğesi oluşturur `simpleString` .  
  
```csharp  
feed.ElementExtensions.Add("simpleString", "", "hello, world!");  
```  
  
 Bu öğenin XML ad alanı boş ("") ad alanıdır ve değeri "Hello, World!" dizesini içeren bir metin düğümüdür.  
  
 Birçok iç içe öğeden oluşan karmaşık öğe uzantıları oluşturmanın bir yolu, aşağıdaki örneklerde gösterildiği gibi serileştirme için .NET Framework API 'Leri kullanmaktır (hem hem de <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Xml.Serialization.XmlSerializer> desteklenir).  
  
```csharp  
feed.ElementExtensions.Add( new DataContractExtension() { Key = "X", Value = 4 } );  
feed.ElementExtensions.Add( new XmlSerializerExtension { Key = "Y", Value = 8 }, new XmlSerializer( typeof( XmlSerializerExtension ) ) );  
```  
  
 Bu örnekte, ve, `DataContractExtension` `XmlSerializerExtension` serileştirici ile kullanılmak üzere yazılmış özel türlerdir.  
  
 <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection>Sınıfı bir örnekten öğe uzantıları oluşturmak için de kullanılabilir <xref:System.Xml.XmlReader> . Bu <xref:System.Xml.Linq.XElement> , aşağıdaki örnek kodda gösterildiği gıbı XML Işleme API 'leriyle kolay tümleştirme sağlar.  
  
```csharp  
feed.ElementExtensions.Add(new XElement("xElementExtension",  
        new XElement("Key", new XAttribute("attr1", "someValue"), "Z"),  
        new XElement("Value", new XAttribute("attr1", "someValue"),
        "15")).CreateReader());  
```  
  
## <a name="reading-extension-data"></a>Uzantı verilerini okuma  
 Öznitelik uzantılarının değerleri, <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> <xref:System.Xml.XmlQualifiedName> Aşağıdaki örnek kodda gösterildiği gibi, koleksiyonundaki özniteliğe bakılarak elde edilebilir.  
  
```csharp  
Console.WriteLine( feed.AttributeExtensions[ new XmlQualifiedName( "myAttribute", "" )]);  
```  
  
 Öğe uzantılarına yöntemi kullanılarak erişilir `ReadElementExtensions<T>` .  
  
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
  
 `XmlReader`Yöntemi kullanılarak tek tek öğe uzantıları elde etmek de mümkündür <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader> .  
  
```csharp  
foreach (SyndicationElementExtension extension in feed2.ElementExtensions.Where<SyndicationElementExtension>(x => x.OuterName == "xElementExtension"))  
{  
    XNode xelement = XElement.ReadFrom(extension.GetReader());  
    Console.WriteLine(xelement.ToString());  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\LooselyTypedExtensions`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Türü kesin belirlenmiş uzantılar](strongly-typed-extensions-sample.md)
- [WCF Dağıtımı](../feature-details/wcf-syndication.md)
