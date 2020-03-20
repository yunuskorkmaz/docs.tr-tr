---
title: Güçlü Yazılmış Uzantılar Örneği
ms.date: 03/30/2017
ms.assetid: 02220f11-1a83-441c-9e5a-85f9a9367572
ms.openlocfilehash: 3cfbcddfdc7700618d499dd41d3a8c3b629bf550
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183310"
---
# <a name="strongly-typed-extensions-sample"></a>Güçlü Yazılmış Uzantılar Örneği
Örnek, <xref:System.ServiceModel.Syndication.SyndicationFeed> sınıfı örnek amaçları için kullanır. Ancak, bu örnekte gösterilen desenler, uzantı verilerini destekleyen tüm Sendikasyon sınıfları ile kullanılabilir.  
  
 Sendikasyon nesnesi<xref:System.ServiceModel.Syndication.SyndicationFeed>modeli <xref:System.ServiceModel.Syndication.SyndicationItem>( , , ve ilgili sınıflar) <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> ve <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> özelliklerini kullanarak uzantı verilerine gevşek dakti-yazılı erişimi destekler. Bu örnek, özel türemiş sınıfları uygulayarak <xref:System.ServiceModel.Syndication.SyndicationFeed> uzantı verilerine <xref:System.ServiceModel.Syndication.SyndicationItem> güçlü bir şekilde daktiledilen erişimin nasıl sağlayabileceğini ve belirli uygulamaya özgü uzantıları güçlü bir şekilde yazılmış özellikler olarak kullanılabilir hale getirerek gösterir.  
  
 Örnek olarak, bu örnek, önerilen Atom İş parçacığı uzantıları RFC tanımlanan bir uzantı öğesi nasıl uygulanacağını gösterir. Bu yalnızca gösteri amaçlıdır ve bu örnek önerilen belirtimin tam olarak uygulanması için tasarlanmamıştır.  
  
## <a name="sample-xml"></a>Örnek XML  
 Aşağıdaki XML örneği, ek `<in-reply-to>` bir uzantı öğesi içeren bir Atom 1.0 girişini gösterir.  
  
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
  
 Öğe, `<in-reply-to>` ek uzantı`ref` `type` özniteliklerinin `href`ve uzantı öğelerinin varlığına izin verirken, gerekli üç özniteliği (ve ) belirtir.  
  
## <a name="modeling-the-in-reply-to-element"></a>Yanıt-Yanıt-Yanıt öğesini modelleme  
 Bu örnekte, `<in-reply-to>` eleman CLR <xref:System.Xml.Serialization.IXmlSerializable>olarak modellenir, hangi ile kullanılmasını <xref:System.Runtime.Serialization.DataContractSerializer>sağlar . Ayrıca, aşağıdaki örnek kodda gösterildiği gibi öğenin verilerine erişmek için bazı yöntemler ve özellikler uygular.  
  
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
  
 `InReplyToElement` Sınıf, gerekli öznitelik (`HRef`, `MediaType`, `Source`ve ) özelliklerinin yanı <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>sıra tutmak için koleksiyonlar ve .  
  
 Sınıf, `InReplyToElement` nesne <xref:System.Xml.Serialization.IXmlSerializable> örneklerinin XML'den nasıl okunduğu ve yazıldığı üzerinde doğrudan denetim sağlayan arabirimi uygular. Yöntem `ReadXml` ilk `Ref` `HRef` <xref:System.Xml.XmlReader> olarak, geçirilen , `Source`, `MediaType` ve özellikleriiçin değerleri okur. Bilinmeyen öznitelikler <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> koleksiyonda depolanır. Tüm öznitelikleri okunduğunda, <xref:System.Xml.XmlReader.ReadStartElement> bir sonraki öğeye okuyucu ilerlemek için çağrılır. Bu sınıf tarafından modellenen öğenin gerekli alt öğeleri olmadığından, `XElement` alt öğeler aşağıdaki kodda gösterildiği gibi arabelleğe alınarak <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> koleksiyonda depolanır.  
  
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
  
 İçinde `WriteXml`, `InReplyToElement` yöntem ilk xml `Ref`öznitelikleri `Source`olarak `MediaType` , , `HRef`ve`WriteXml` özellikleri değerlerini yazar ( gerçek dış öğenin kendisi `WriteXml`yazmaktan sorumlu değildir, arayan tarafından yapılan gibi ). Ayrıca aşağıdaki kodda <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> gösterildiği <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> gibi, ve yazar içeriğini yazar.  
  
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
 Örnekte, `SyndicationItems` uzantıları `InReplyTo` ile `ThreadedItem` sınıf tarafından modellenir. Benzer şekilde, `ThreadedFeed` sınıf `SyndicationFeed` öğeleri tüm örnekleri olan `ThreadedItem`bir .  
  
 Sınıf `ThreadedFeed` devralır `SyndicationFeed` ve bir `OnCreateItem` `ThreadedItem`döndürmek için geçersiz kılar. Ayrıca, aşağıdaki kodda gösterildiği `Items` gibi `ThreadedItems`koleksiyona erişmek için bir yöntem uygular.  
  
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
  
 Sınıf `ThreadedItem` devralır `SyndicationItem` ve `InReplyToElement` güçlü bir şekilde yazılan bir özellik olarak yapar. `InReplyTo` Bu, uzantı verilerine uygun programlı erişim sağlar. Ayrıca, aşağıdaki `TryParseElement` `WriteElementExtensions` kodda gösterildiği gibi uzantı verilerini okumak ve yazmak için de uygular.  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler bilgisayarınıza zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StronglyTypedExtensions`  
