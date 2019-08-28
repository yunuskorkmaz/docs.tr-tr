---
title: Geniş Yazılmış Uzantılar Örneği
ms.date: 03/30/2017
ms.assetid: 56ce265b-8163-4b85-98e7-7692a12c4357
ms.openlocfilehash: 21690aebca250880a8eb51aee0821220a00bc0c0
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039475"
---
# <a name="loosely-typed-extensions-sample"></a>Geniş Yazılmış Uzantılar Örneği
Dağıtım nesnesi modeli, uzantı verileriyle çalışma için zengin destek sağlar — bir dağıtım akışının xml gösteriminde bulunan ancak <xref:System.ServiceModel.Syndication.SyndicationFeed> ve <xref:System.ServiceModel.Syndication.SyndicationItem>gibi sınıflar tarafından açıkça gösterilmeyen bilgiler. Bu örnek, uzantı verileriyle çalışmaya yönelik temel teknikleri gösterir.  
  
 Örnek, örnek amacıyla <xref:System.ServiceModel.Syndication.SyndicationFeed> sınıfını kullanır. Ancak, bu örnekte gösterilen desenler uzantı verilerini destekleyen tüm dağıtım sınıflarıyla birlikte kullanılabilir:  
  
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
  
- `<feed>` Öğesinin `myAttribute` özniteliği.  
  
- `<simpleString>`dosyalarında.  
  
- `<DataContractExtension>`dosyalarında.  
  
- `<XmlSerializerExtension>`dosyalarında.  
  
- `<xElementExtension>`dosyalarında.  
  
## <a name="writing-extension-data"></a>Uzantı verileri yazma  
 Öznitelik uzantıları, aşağıdaki örnek kodda gösterildiği gibi <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> koleksiyona giriş eklenerek oluşturulur.  
  
```  
//Attribute extensions are stored in a dictionary indexed by   
// XmlQualifiedName  
feed.AttributeExtensions.Add(new XmlQualifiedName("myAttribute", ""), "someValue");  
```  
  
 Öğe uzantıları, <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> koleksiyona girdi eklenerek oluşturulur. Bu uzantılar, dizeler gibi temel değerler, .NET Framework nesnelerin XML serileştirmeleri veya el ile kodlanmış XML düğümleri olabilir.  
  
 Aşağıdaki örnek kod adlı `simpleString`bir uzantı öğesi oluşturur.  
  
```  
feed.ElementExtensions.Add("simpleString", "", "hello, world!");  
```  
  
 Bu öğenin XML ad alanı boş ("") ad alanıdır ve değeri "Hello, World!" dizesini içeren bir metin düğümüdür.  
  
 Birçok iç içe öğeden oluşan karmaşık öğe uzantıları oluşturmanın bir yolu, aşağıdaki örneklerde gösterildiği gibi serileştirme için .NET Framework API 'leri kullanmaktır (hem <xref:System.Runtime.Serialization.DataContractSerializer> hem de <xref:System.Xml.Serialization.XmlSerializer> desteklenir).  
  
```  
feed.ElementExtensions.Add( new DataContractExtension() { Key = "X", Value = 4 } );  
feed.ElementExtensions.Add( new XmlSerializerExtension { Key = "Y", Value = 8 }, new XmlSerializer( typeof( XmlSerializerExtension ) ) );  
```  
  
 Bu örnekte, ve `DataContractExtension` `XmlSerializerExtension` , serileştirici ile kullanılmak üzere yazılmış özel türlerdir.  
  
 <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> Sınıfı bir<xref:System.Xml.XmlReader> örnekten öğe uzantıları oluşturmak için de kullanılabilir. Bu, aşağıdaki örnek kodda gösterildiği gibi XML işleme API 'leriyle <xref:System.Xml.Linq.XElement> kolay tümleştirme sağlar.  
  
```  
feed.ElementExtensions.Add(new XElement("xElementExtension",  
        new XElement("Key", new XAttribute("attr1", "someValue"), "Z"),  
        new XElement("Value", new XAttribute("attr1", "someValue"),   
        "15")).CreateReader());  
```  
  
## <a name="reading-extension-data"></a>Uzantı verilerini okuma  
 Öznitelik uzantılarının değerleri, aşağıdaki örnek kodda gösterildiği <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> <xref:System.Xml.XmlQualifiedName> gibi, koleksiyonundaki özniteliğe bakılarak elde edilebilir.  
  
```  
Console.WriteLine( feed.AttributeExtensions[ new XmlQualifiedName( "myAttribute", "" )]);  
```  
  
 Öğe uzantılarına `ReadElementExtensions<T>` yöntemi kullanılarak erişilir.  
  
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
  
 Yöntemi kullanılarak tek tek öğe uzantıları elde `XmlReader` etmek de mümkündür. <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader>  
  
```  
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
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\LooselyTypedExtensions`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kesin Tür Belirtilmiş Uzantılar](../../../../docs/framework/wcf/samples/strongly-typed-extensions-sample.md)
- [WCF Dağıtımı](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
