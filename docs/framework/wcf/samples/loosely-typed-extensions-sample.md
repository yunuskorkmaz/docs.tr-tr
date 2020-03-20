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
# <a name="loosely-typed-extensions-sample"></a>Geniş Yazılmış Uzantılar Örneği
Sendikasyon nesnesi modeli, uzantı lı verilerle çalışmak için zengin destek sağlar— bir sendikasyon akışının XML <xref:System.ServiceModel.Syndication.SyndicationFeed> <xref:System.ServiceModel.Syndication.SyndicationItem>gösteriminde bulunan ancak bu tür sınıflar tarafından açıkça açığa alınmayan bilgiler. Bu örnek, uzantı verileriyle çalışmak için temel teknikleri göstermektedir.  
  
 Örnek, <xref:System.ServiceModel.Syndication.SyndicationFeed> sınıfı örnek amaçları için kullanır. Ancak, bu örnekte gösterilen desenler, uzantı verilerini destekleyen tüm Sendikasyon sınıfları ile kullanılabilir:  
  
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
  
 Bu belge, aşağıdaki uzantı verileri parçalarını içerir:  
  
- Öğenin `myAttribute` `<feed>` özniteliği.  
  
- `<simpleString>`Öğe.  
  
- `<DataContractExtension>`Öğe.  
  
- `<XmlSerializerExtension>`Öğe.  
  
- `<xElementExtension>`Öğe.  
  
## <a name="writing-extension-data"></a>Uzantı Verilerini Yazma  
 Öznitelik uzantıları, aşağıdaki örnek kodda gösterildiği gibi <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> koleksiyona girişler eklenerek oluşturulur.  
  
```csharp  
//Attribute extensions are stored in a dictionary indexed by
// XmlQualifiedName  
feed.AttributeExtensions.Add(new XmlQualifiedName("myAttribute", ""), "someValue");  
```  
  
 Öğe uzantıları <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> koleksiyona girişler eklenerek oluşturulur. Bu uzantılar dizeleri, .NET Framework nesnelerinin XML serileştirmeleri veya elle kodlanmış XML düğümleri gibi temel değerlerle olabilir.  
  
 Aşağıdaki örnek kod adlı `simpleString`bir uzantı öğesi oluşturur.  
  
```csharp  
feed.ElementExtensions.Add("simpleString", "", "hello, world!");  
```  
  
 Bu öğenin XML ad alanı boş ad alanıdır ("") ve değeri "merhaba, dünya!" dizesini içeren bir metin düğümüdür.  
  
 Birçok iç içe öğeden oluşan karmaşık öğe uzantıları oluşturmanın bir yolu, aşağıdaki örneklerde <xref:System.Runtime.Serialization.DataContractSerializer> gösterildiği <xref:System.Xml.Serialization.XmlSerializer> gibi .NET Framework API'lerini serileştirme (hem de desteklenir) için kullanmaktır.  
  
```csharp  
feed.ElementExtensions.Add( new DataContractExtension() { Key = "X", Value = 4 } );  
feed.ElementExtensions.Add( new XmlSerializerExtension { Key = "Y", Value = 8 }, new XmlSerializer( typeof( XmlSerializerExtension ) ) );  
```  
  
 Bu örnekte, `DataContractExtension` `XmlSerializerExtension` ve özel türleri bir serializer ile kullanılmak üzere yazılmıştır.  
  
 Sınıf, <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> bir <xref:System.Xml.XmlReader> örnekten öğe uzantıları oluşturmak için de kullanılabilir. Bu, aşağıdaki örnek kodda gösterildiği gibi <xref:System.Xml.Linq.XElement> XML işleme API'leri ile kolay entegrasyon sağlar.  
  
```csharp  
feed.ElementExtensions.Add(new XElement("xElementExtension",  
        new XElement("Key", new XAttribute("attr1", "someValue"), "Z"),  
        new XElement("Value", new XAttribute("attr1", "someValue"),
        "15")).CreateReader());  
```  
  
## <a name="reading-extension-data"></a>Okuma Uzantısı Verileri  
 Öznitelik uzantıları için değerler, <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> aşağıdaki örnek kodda gösterildiği <xref:System.Xml.XmlQualifiedName> gibi koleksiyondaki özniteliğe bakarak elde edilebilir.  
  
```csharp  
Console.WriteLine( feed.AttributeExtensions[ new XmlQualifiedName( "myAttribute", "" )]);  
```  
  
 Öğe uzantıları `ReadElementExtensions<T>` yöntemi kullanılarak erişilir.  
  
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
  
 Yöntemi kullanarak <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader> tek tek `XmlReader` eleman uzantıları elde etmek de mümkündür.  
  
```csharp  
foreach (SyndicationElementExtension extension in feed2.ElementExtensions.Where<SyndicationElementExtension>(x => x.OuterName == "xElementExtension"))  
{  
    XNode xelement = XElement.ReadFrom(extension.GetReader());  
    Console.WriteLine(xelement.ToString());  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\LooselyTypedExtensions`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güçlü Yazılmış Uzantılar](../../../../docs/framework/wcf/samples/strongly-typed-extensions-sample.md)
- [WCF Dağıtımı](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
