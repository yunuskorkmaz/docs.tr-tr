---
title: Güçlü Yazılmış Uzantılar Örneği
ms.date: 03/30/2017
ms.assetid: 02220f11-1a83-441c-9e5a-85f9a9367572
ms.openlocfilehash: 1fd873e02dcc1fc824c8b17c52231c80c61e7c60
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045480"
---
# <a name="strongly-typed-extensions-sample"></a>Güçlü Yazılmış Uzantılar Örneği
Örnek, örnek amacıyla <xref:System.ServiceModel.Syndication.SyndicationFeed> sınıfını kullanır. Ancak, bu örnekte gösterilen desenler uzantı verilerini destekleyen tüm dağıtım sınıflarıyla birlikte kullanılabilir.  
  
 Dağıtım nesne modeli<xref:System.ServiceModel.Syndication.SyndicationFeed>(, <xref:System.ServiceModel.Syndication.SyndicationItem>ve ilgili sınıflar), <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> ve <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> özellikleri kullanılarak uzantı verilerine gevşek olarak yazılmış erişimi destekler. Bu örnek, <xref:System.ServiceModel.Syndication.SyndicationFeed> özel türetilmiş sınıfları uygulayarak ve <xref:System.ServiceModel.Syndication.SyndicationItem> kesin tür belirtilmiş özellikler olarak uygulamaya özgü belirli uzantıları kullanıma sunarak uzantı verilerine kesin olarak yazılmış erişimin nasıl sağlanması gerektiğini gösterir.  
  
 Örnek olarak, bu örnek, önerilen atom Iş parçacığı uzantıları RFC 'de tanımlanan bir uzantı öğesinin nasıl uygulanacağını gösterir. Bu yalnızca tanıtım amaçlıdır ve bu örnek önerilen belirtim için tam bir uygulama olmak üzere tasarlanmamıştır.  
  
## <a name="sample-xml"></a>Örnek XML  
 Aşağıdaki xml örneği, ek `<in-reply-to>` bir genişletme öğesiyle bir Atom 1,0 girişi göstermektedir.  
  
```xml  
<entry>  
    <id>tag:example.org,2005:1,2</id>  
    <title type="text">Another response to the original</title>  
    <summary type="text">  
         This is a response to the original entry</summary>  
    <updated>2006-03-01T12:12:13Z</updated>  
    <link href="http://www.example.org/entries/1/2" />  
    <in-reply-to p3:ref="tag:example.org,2005:1"   
                 p3:href="http://www.example.org/entries/1"   
                 p3:type="application/xhtml+xml"   
                 xmlns:p3="http://contoso.org/syndication/thread/1.0"   
                 xmlns="http://contoso.org/syndication/thread/1.0">  
      <anotherElement xmlns="http://www.w3.org/2005/Atom">  
                     Some more data</anotherElement>  
      <aDifferentElement xmlns="http://www.w3.org/2005/Atom">  
                     Even more data</aDifferentElement>  
    </in-reply-to>  
</entry>  
```  
  
 Öğesi, ek uzantı özniteliklerinin ve uzantı`ref`öğelerinin varlığına `href`izin verirken, üç gerekli özniteliği (, `type` ve) belirler. `<in-reply-to>`  
  
## <a name="modeling-the-in-reply-to-element"></a>-Reply-To öğesini modelleme  
 Bu örnekte, `<in-reply-to>` öğesi, <xref:System.Runtime.Serialization.DataContractSerializer>ile kullanımını sağlayan CLR <xref:System.Xml.Serialization.IXmlSerializable>olarak modellenir. Ayrıca, aşağıdaki örnek kodda gösterildiği gibi, öğe verilerine erişmek için bazı yöntemler ve özellikler uygular.  
  
```  
[XmlRoot(ElementName = "in-reply-to", Namespace = "http://contoso.org/syndication/thread/1.0")]  
public class InReplyToElement : IXmlSerializable  
{  
    internal const string ElementName = "in-reply-to";  
    internal const string NsUri =   
                  "http://contoso.org/syndication/thread/1.0";  
    private Dictionary<XmlQualifiedName, string> extensionAttributes;  
    private Collection<XElement> extensionElements;  
  
    public InReplyToElement()  
    {  
        this.extensionElements = new Collection<XElement>();  
        this.extensionAttributes = new Dictionary<XmlQualifiedName,   
                                                          string>();  
    }  
  
    public Dictionary<XmlQualifiedName, string> AttributeExtensions  
    {  
        get { return this.extensionAttributes; }  
    }  
  
    public Collection<XElement> ElementExtensions  
    {  
        get { return this.extensionElements; }  
    }  
  
    public Uri Href  
    { get; set; }  
  
    public string MediaType  
    { get; set; }  
  
    public string Ref  
    { get; set; }  
  
    public Uri Source  
    { get; set; }  
}  
```  
  
 `HRef` `MediaType` `Source` <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> Sınıfı, gerekli öznitelik (,, ve) ve<xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>tutulacak koleksiyonlar için özellikleri uygular. `InReplyToElement`  
  
 Sınıfı, nesne örneklerinin <xref:System.Xml.Serialization.IXmlSerializable> XML 'den okuma ve yazma konusunda doğrudan denetime izin veren arabirimini uygular. `InReplyToElement` `Ref` `HRef`Yöntemi, geçirilen<xref:System.Xml.XmlReader> öğesinden, `MediaType` ,, ve özelliklerine ilişkin değerleri ilk olarak okur. `Source` `ReadXml` Bilinmeyen tüm öznitelikler <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> koleksiyonda depolanır. Tüm öznitelikler okundum, <xref:System.Xml.XmlReader.ReadStartElement> okuyucuyu bir sonraki öğeye ilerletmek için çağırılır. Bu sınıf tarafından modellenen öğede gerekli alt öğe bulunmadığından, alt öğeler aşağıdaki kodda gösterildiği gibi `XElement` örneklerle arabelleğe alınır ve <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> koleksiyonda depolanır.  
  
```  
public void ReadXml(System.Xml.XmlReader reader)  
{  
    bool isEmpty = reader.IsEmptyElement;  
  
    if (reader.HasAttributes)  
    {  
        for (int i = 0; i < reader.AttributeCount; i++)  
        {  
            reader.MoveToNextAttribute();  
  
            if (reader.NamespaceURI == "")  
            {  
                if (reader.LocalName == "ref")  
                {  
                    this.Ref = reader.Value;  
                }  
                else if (reader.LocalName == "href")  
                {  
                    this.Href = new Uri(reader.Value);  
                }  
                else if (reader.LocalName == "source")  
                {  
                    this.Source = new Uri(reader.Value);  
                }  
                else if (reader.LocalName == "type")  
                {  
                    this.MediaType = reader.Value;  
                }  
                else  
                {  
                    this.AttributeExtensions.Add(new   
                                 XmlQualifiedName(reader.LocalName,   
                                 reader.NamespaceURI),   
                                 reader.Value);  
                }  
            }  
        }  
    }  
  
    reader.ReadStartElement();  
  
    if (!isEmpty)  
    {  
        while (reader.IsStartElement())  
        {  
            ElementExtensions.Add(  
                  (XElement) XElement.ReadFrom(reader));  
        }  
        reader.ReadEndElement();  
    }  
}  
```  
  
 `WriteXml` `Ref` `Source`İçinde, yöntemiilk`HRef`olarak,,,`WriteXml` ve özelliklerinindeğerleriniXMLöznitelikleriolarakyazar(gerçekdışöğeninyazılmasındansorumludeğildir`MediaType` `InReplyToElement` kendisini çağıran `WriteXml`tarafından yapıldığı gibi). Ayrıca, <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> aşağıdaki kodda gösterildiği gibi, ve <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> ' nin içeriğini yaza yazar.  
  
```  
public void WriteXml(System.Xml.XmlWriter writer)  
{  
    if (this.Ref != null)  
    {  
        writer.WriteAttributeString("ref", InReplyToElement.NsUri,   
                                            this.Ref);  
    }  
    if (this.Href != null)  
    {  
        writer.WriteAttributeString("href", InReplyToElement.NsUri,   
                                                this.Href.ToString());  
    }  
    if (this.Source != null)  
    {  
        writer.WriteAttributeString("source", InReplyToElement.NsUri,   
                                              this.Source.ToString());  
    }  
    if (this.MediaType != null)  
    {  
        writer.WriteAttributeString("type", InReplyToElement.NsUri,   
                                                    this.MediaType);  
    }  
  
    foreach (KeyValuePair<XmlQualifiedName, string> kvp in   
                                             this.AttributeExtensions)  
    {  
        writer.WriteAttributeString(kvp.Key.Name, kvp.Key.Namespace,   
                                                   kvp.Value);  
    }  
  
    foreach (XElement element in this.ElementExtensions)  
    {  
        element.WriteTo(writer);  
    }  
}  
```  
  
## <a name="threadedfeed-and-threadeditem"></a>ThreadedFeed ve ThreadedItem  
 Örnekte, `SyndicationItems` `InReplyTo` uzantılarısınıfına`ThreadedItem` göre modellenir. Benzer şekilde, `ThreadedFeed` sınıfı öğelerinintüm`SyndicationFeed` örnekleri olan bir olur `ThreadedItem`.  
  
 Sınıfı öğesinden `SyndicationFeed` devralır`OnCreateItem` ve`ThreadedItem`döndürür. `ThreadedFeed` Ayrıca `Items` `ThreadedItems`, aşağıdaki kodda gösterildiği gibi, koleksiyona erişim için bir yöntem uygular.  
  
```  
public class ThreadedFeed : SyndicationFeed  
{  
    public ThreadedFeed()  
    {  
    }  
  
    public IEnumerable<ThreadedItem> ThreadedItems  
    {  
        get  
        {  
            return this.Items.Cast<ThreadedItem>();  
        }  
    }  
  
    protected override SyndicationItem CreateItem()  
    {  
        return new ThreadedItem();  
    }  
}  
```  
  
 Sınıfı `ThreadedItem` `InReplyToElement` öğesinden `SyndicationItem` devralır ve türü kesin belirlenmiş bir özellik olarak yapılır. Bu, `InReplyTo` uzantı verilerine kolay programlı erişim sağlar. Ayrıca, aşağıdaki `TryParseElement` kodda `WriteElementExtensions` gösterildiği gibi, uzantı verilerini okumak ve yazmak için de uygular.  
  
```  
public class ThreadedItem : SyndicationItem  
{  
    private InReplyToElement inReplyTo;  
    // Constructors  
        public ThreadedItem()  
        {  
            inReplyTo = new InReplyToElement();  
        }  
  
        public ThreadedItem(string title, string content, Uri itemAlternateLink, string id, DateTimeOffset lastUpdatedTime) : base(title, content, itemAlternateLink, id, lastUpdatedTime)  
        {  
            inReplyTo = new InReplyToElement();  
        }  
  
    public InReplyToElement InReplyTo  
    {  
        get { return this.inReplyTo; }  
    }  
  
    protected override bool TryParseElement(  
                        System.Xml.XmlReader reader,   
                        string version)  
    {  
        if (version == SyndicationVersions.Atom10 &&  
            reader.NamespaceURI == InReplyToElement.NsUri &&  
            reader.LocalName == InReplyToElement.ElementName)  
        {  
            this.inReplyTo = new InReplyToElement();  
  
            this.InReplyTo.ReadXml(reader);  
  
            return true;  
        }  
        else  
        {  
            return base.TryParseElement(reader, version);  
        }  
    }  
  
    protected override void WriteElementExtensions(XmlWriter writer,   
                                                 string version)  
    {  
        if (this.InReplyTo != null &&   
                     version == SyndicationVersions.Atom10)  
        {  
            writer.WriteStartElement(InReplyToElement.ElementName,   
                                           InReplyToElement.NsUri);  
            this.InReplyTo.WriteXml(writer);  
            writer.WriteEndElement();  
        }  
  
        base.WriteElementExtensions(writer, version);  
    }  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StronglyTypedExtensions`  
