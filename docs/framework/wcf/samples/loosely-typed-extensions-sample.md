---
title: Geniş Yazılmış Uzantılar Örneği
ms.date: 03/30/2017
ms.assetid: 56ce265b-8163-4b85-98e7-7692a12c4357
ms.openlocfilehash: 19d39e4a70022304262c5872636d3ea03a3b861b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54668489"
---
# <a name="loosely-typed-extensions-sample"></a>Geniş Yazılmış Uzantılar Örneği
Zengin destek uzantısı verilerle çalışmak için dağıtım nesne modeli sağlar — akışı bir dağıtımda mevcut olan bilgiler XML gösterimi kullanıcının, ancak açıkça gibi sınıfları tarafından sunulan <xref:System.ServiceModel.Syndication.SyndicationFeed> ve <xref:System.ServiceModel.Syndication.SyndicationItem>. Bu örnek, uzantı verilerle çalışmak için temel teknikleri gösterir.  
  
 Örnek kullanır <xref:System.ServiceModel.Syndication.SyndicationFeed> amacıyla sınıfının örneği. Ancak, bu örnekte gösterilen desenleri tüm uzantı verileri destekleyen bir dağıtım sınıfları kullanılabilir:  
  
 <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
 <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
 <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
 <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
## <a name="sample-xml"></a>Örnek XML  
 Başvuru için bu örnekte aşağıdaki XML belgesi kullanılır.  
  
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
  
 Bu belge aşağıdaki uzantı veri parçasını içerir:  
  
-   `myAttribute` Özniteliği `<feed>` öğesi.  
  
-   `<simpleString>` öğe.  
  
-   `<DataContractExtension>` öğe.  
  
-   `<XmlSerializerExtension>` öğe.  
  
-   `<xElementExtension>` öğe.  
  
## <a name="writing-extension-data"></a>Uzantı verileri yazma  
 Öznitelik uzantıları girişlere ekleyerek oluşturulur <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> aşağıdaki örnek kodda gösterildiği gibi bir koleksiyon.  
  
```  
//Attribute extensions are stored in a dictionary indexed by   
// XmlQualifiedName  
feed.AttributeExtensions.Add(new XmlQualifiedName("myAttribute", ""), "someValue");  
```  
  
 Öğesi uzantıları oluşturulduğu girişlerine ekleyerek <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> koleksiyonu. Bu uzantılar, dizeler, .NET Framework nesneleri veya el ile kodlanmış bir XML düğümüyle XML serializations gibi temel değerlere göre yapabilirsiniz.  
  
 Aşağıdaki örnek kod adlı bir uzantı öğesi oluşturur `simpleString`.  
  
```  
feed.ElementExtensions.Add("simpleString", "", "hello, world!");  
```  
  
 Bu öğe için XML ad alanı boş ad alanıdır ("") ve değeri "hello, world!" dizesini içeren bir metin düğümü.  
  
 İç içe öğelerin birçoğunu oluşan karmaşık öğesi uzantıları oluşturmak için tek yönlü olan seri hale getirme için .NET Framework API'ları kullanmak için (hem <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Xml.Serialization.XmlSerializer> desteklenir) aşağıdaki örneklerde gösterildiği gibi.  
  
```  
feed.ElementExtensions.Add( new DataContractExtension() { Key = "X", Value = 4 } );  
feed.ElementExtensions.Add( new XmlSerializerExtension { Key = "Y", Value = 8 }, new XmlSerializer( typeof( XmlSerializerExtension ) ) );  
```  
  
 Bu örnekte, `DataContractExtension` ve `XmlSerializerExtension` seri hale getirici ile kullanım için yazılan özel tür.  
  
 <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> Sınıfı da öğesi uzantıları oluşturmak için kullanılabilir bir <xref:System.Xml.XmlReader> örneği. Bu kolay tümleştirme için API'leri gibi işleme XML ile sağlar <xref:System.Xml.Linq.XElement> aşağıdaki örnek kodda gösterildiği gibi.  
  
```  
feed.ElementExtensions.Add(new XElement("xElementExtension",  
        new XElement("Key", new XAttribute("attr1", "someValue"), "Z"),  
        new XElement("Value", new XAttribute("attr1", "someValue"),   
        "15")).CreateReader());  
```  
  
## <a name="reading-extension-data"></a>Uzantı verileri okuma  
 Öznitelik, bakarak özniteliği uzantıları için değerlerinin elde edilebilmesini <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> koleksiyona göre kendi <xref:System.Xml.XmlQualifiedName> aşağıdaki örnek kodda gösterildiği gibi.  
  
```  
Console.WriteLine( feed.AttributeExtensions[ new XmlQualifiedName( "myAttribute", "" )]);  
```  
  
 Öğesi uzantıları kullanılarak erişilir `ReadElementExtensions<T>` yöntemi.  
  
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
  
 Elde etmek mümkündür bir `XmlReader` tek öğe uzantıları kullanarak, <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader> yöntemi.  
  
```  
foreach (SyndicationElementExtension extension in feed2.ElementExtensions.Where<SyndicationElementExtension>(x => x.OuterName == "xElementExtension"))  
{  
    XNode xelement = XElement.ReadFrom(extension.GetReader());  
    Console.WriteLine(xelement.ToString());  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\LooselyTypedExtensions`  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Kesin Tür Belirtilmiş Uzantılar](../../../../docs/framework/wcf/samples/strongly-typed-extensions-sample.md)
- [WCF Dağıtımı](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
