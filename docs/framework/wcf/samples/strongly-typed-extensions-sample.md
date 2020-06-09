---
title: Kesin tür belirtilmiş Uzantılar örneği
ms.date: 03/30/2017
ms.assetid: 02220f11-1a83-441c-9e5a-85f9a9367572
ms.openlocfilehash: e8c3bf202a1fb76d383f0a3fe15084d19a1d51fb
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600886"
---
# <a name="strongly-typed-extensions-sample"></a>Kesin tür belirtilmiş Uzantılar örneği

Örnek, <xref:System.ServiceModel.Syndication.SyndicationFeed> örnek amacıyla sınıfını kullanır. Ancak, bu örnekte gösterilen desenler uzantı verilerini destekleyen tüm dağıtım sınıflarıyla birlikte kullanılabilir.  
  
 Dağıtım nesne modeli ( <xref:System.ServiceModel.Syndication.SyndicationFeed> , <xref:System.ServiceModel.Syndication.SyndicationItem> ve ilgili sınıflar), ve özellikleri kullanılarak uzantı verilerine gevşek olarak yazılmış erişimi destekler <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> . Bu örnek, özel türetilmiş sınıfları uygulayarak <xref:System.ServiceModel.Syndication.SyndicationFeed> ve <xref:System.ServiceModel.Syndication.SyndicationItem> kesin tür belirtilmiş özellikler olarak uygulamaya özgü belirli uzantıları kullanıma sunarak uzantı verilerine kesin olarak belirlenmiş erişimin nasıl sağlanması gerektiğini gösterir.  
  
 Örnek olarak, bu örnek, önerilen atom Iş parçacığı uzantıları RFC 'de tanımlanan bir uzantı öğesinin nasıl uygulanacağını gösterir. Bu yalnızca tanıtım amaçlıdır ve bu örnek önerilen belirtim için tam bir uygulama olmak üzere tasarlanmamıştır.  
  
## <a name="sample-xml"></a>Örnek XML  
 Aşağıdaki XML örneği, ek bir genişletme öğesiyle bir Atom 1,0 girişi göstermektedir `<in-reply-to>` .  
  
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
  
 `<in-reply-to>`Öğesi, `ref` `type` `href` ek uzantı özniteliklerinin ve uzantı öğelerinin varlığına izin verirken, üç gerekli özniteliği (, ve) belirler.  
  
## <a name="modeling-the-in-reply-to-element"></a>-Reply-To öğesini modelleme  
 Bu örnekte, `<in-reply-to>` öğesi <xref:System.Xml.Serialization.IXmlSerializable> , ile kullanımını sağlayan CLR olarak modellenir <xref:System.Runtime.Serialization.DataContractSerializer> . Ayrıca, aşağıdaki örnek kodda gösterildiği gibi, öğe verilerine erişmek için bazı yöntemler ve özellikler uygular.  
  
```csharp  
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
  
 `InReplyToElement`Sınıfı, gerekli öznitelik ( `HRef` , `MediaType` , ve `Source` ) ve tutulacak koleksiyonlar için <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> özellikleri uygular <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> .  
  
 `InReplyToElement`Sınıfı, <xref:System.Xml.Serialization.IXmlSerializable> nesne örneklerinin XML 'den okuma ve yazma konusunda doğrudan denetime izin veren arabirimini uygular. `ReadXml`Yöntemi `Ref` , geçirilen öğesinden,,, `HRef` `Source` ve `MediaType` özelliklerine ilişkin değerleri ilk olarak okur <xref:System.Xml.XmlReader> . Bilinmeyen tüm öznitelikler <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> koleksiyonda depolanır. Tüm öznitelikler okundum, <xref:System.Xml.XmlReader.ReadStartElement> okuyucuyu bir sonraki öğeye ilerletmek için çağırılır. Bu sınıf tarafından modellenen öğede gerekli alt öğe bulunmadığından, alt öğeler `XElement` aşağıdaki kodda gösterildiği gibi örneklerle arabelleğe alınır ve koleksiyonda depolanır <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> .  
  
```csharp
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
  
 İçinde, `WriteXml` `InReplyToElement` yöntemi ilk olarak,,, `Ref` `HRef` `Source` ve özelliklerinin değerlerini `MediaType` XML öznitelikleri olarak yazar (, `WriteXml` çağıran tarafından yapıldığı gibi gerçek dış öğenin kendisini yazmadan sorumludur `WriteXml` ). Ayrıca, <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> aşağıdaki kodda gösterildiği gibi, ve ' nin içeriğini yaza yazar.  
  
```csharp
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
 Örnekte, `SyndicationItems` `InReplyTo` uzantıları sınıfına göre modellenir `ThreadedItem` . Benzer şekilde, `ThreadedFeed` sınıfı `SyndicationFeed` öğelerinin tüm örnekleri olan bir olur `ThreadedItem` .  
  
 `ThreadedFeed`Sınıfı öğesinden devralır `SyndicationFeed` ve `OnCreateItem` döndürür `ThreadedItem` . Ayrıca `Items` `ThreadedItems` , aşağıdaki kodda gösterildiği gibi, koleksiyona erişim için bir yöntem uygular.  
  
```csharp
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
  
 Sınıfı `ThreadedItem` öğesinden devralır `SyndicationItem` ve `InReplyToElement` türü kesin belirlenmiş bir özellik olarak yapılır. Bu, uzantı verilerine kolay programlı erişim sağlar `InReplyTo` . Ayrıca `TryParseElement` `WriteElementExtensions` , aşağıdaki kodda gösterildiği gibi, uzantı verilerini okumak ve yazmak için de uygular.  
  
```csharp
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
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StronglyTypedExtensions`  
