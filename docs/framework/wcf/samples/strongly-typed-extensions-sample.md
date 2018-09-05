---
title: Güçlü Yazılmış Uzantılar Örneği
ms.date: 03/30/2017
ms.assetid: 02220f11-1a83-441c-9e5a-85f9a9367572
ms.openlocfilehash: eccb0ce240d01ab8592a44daddcfa7aa3d2023fb
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43659374"
---
# <a name="strongly-typed-extensions-sample"></a>Güçlü Yazılmış Uzantılar Örneği
Örnek kullanır <xref:System.ServiceModel.Syndication.SyndicationFeed> amacıyla sınıfının örneği. Ancak, bu örnekte gösterilen desenleri tüm uzantı verileri destekleyen bir dağıtım sınıfları ile kullanılabilir.  
  
 Dağıtım nesnesi modeli (<xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem>, ve ilgili sınıflar) kullanarak uzantı verilerine erişim geniş yazılmış desteklediği <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> ve <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> özellikleri. Bu örnek özel türetilmiş sınıfları uygulayarak uzantı verileri kesin türü belirtilmiş erişim sağlamak nasıl gösterir <xref:System.ServiceModel.Syndication.SyndicationFeed> ve <xref:System.ServiceModel.Syndication.SyndicationItem> , kullanılabilir duruma özellikleri kesin olarak belirli bir uygulamaya özgü uzantılar.  
  
 Bu örnek, örnek olarak, önerilen Atom iş parçacığı uzantıları RFC tanımlanmış bir uzantı öğesi uygulamak nasıl gösterir. Bu yalnızca tanıtım amacıyla, ve bu örnek önerilen belirtiminin tam bir uygulaması olacak şekilde tasarlanmamıştır.  
  
## <a name="sample-xml"></a>Örnek XML  
 Aşağıdaki XML örneği gösterir bir Atom 1.0 giriş ek ile `<in-reply-to>` uzantı öğesi.  
  
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
  
 `<in-reply-to>` Öğesi üç gerekli öznitelikleri belirtir (`ref`, `type` ve `href`) sağlarken ayrıca ek uzantı öznitelikleri ve uzantı öğesi varlığı için.  
  
## <a name="modeling-the-in-reply-to-element"></a>In yanıt için öğe modelleme  
 Bu örnekte `<in-reply-to>` öğesini uygulayan CLR modellenir <xref:System.Xml.Serialization.IXmlSerializable>, kullanımını sağlayan <xref:System.Runtime.Serialization.DataContractSerializer>. Ayrıca bazı yöntemler ve özellikler bu öğenin verilerine erişmek için aşağıdaki örnek kodda gösterildiği gibi uygular.  
  
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
  
 `InReplyToElement` Sınıfı gerekli öznitelik özelliklerini uygular (`HRef`, `MediaType`, ve `Source`) tutmak için koleksiyonları yanı sıra <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> ve <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>.  
  
 `InReplyToElement` Sınıfının Implements <xref:System.Xml.Serialization.IXmlSerializable> nesne örneklerini nasıl okuma ve XML olarak yazılmış üzerinde doğrudan denetim sağlayan arabirim. `ReadXml` Yöntemi ilk değerlerini okur `Ref`, `HRef`, `Source`, ve `MediaType` özelliklerinden <xref:System.Xml.XmlReader> geçirilen. Bilinmeyen tüm öznitelikler depolanır <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> koleksiyonu. Tüm öznitelikleri okuduktan sonra <xref:System.Xml.XmlReader.ReadStartElement> okuyucu sonraki öğeye ilerlemek için çağrılır. Bu sınıf tarafından modellenir öğesi gerekli alt öğesi olduğundan, alt öğeleri olarak arabelleğe `XElement` örnekler ve depolanan <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> koleksiyonu, aşağıdaki kodda gösterildiği gibi.  
  
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
  
 İçinde `WriteXml`, `InReplyToElement` yöntemi ilk değerleri Yazar `Ref`, `HRef`, `Source`, ve `MediaType` özellikler XML özniteliği olarak (`WriteXml` gerçek dış öğe yazmak için sorumlu değildir çağıran tarafından yapılan olarak kendisini `WriteXml`). Ayrıca içeriğini Yazar <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> ve <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> için aşağıdaki kodda gösterildiği gibi yazıcı.  
  
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
 Örnekte, `SyndicationItems` ile `InReplyTo` uzantıları tarafından modellenir `ThreadedItem` sınıfı. Benzer şekilde, `ThreadedFeed` sınıfı bir `SyndicationFeed` öğeleri olan tüm örneklerini `ThreadedItem`.  
  
 `ThreadedFeed` Sınıfının devraldığı `SyndicationFeed` ve geçersiz kılmaları `OnCreateItem` döndürülecek bir `ThreadedItem`. Ayrıca erişmek için bir yöntem uygular `Items` koleksiyonu olarak `ThreadedItems`aşağıdaki kodda gösterildiği gibi.  
  
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
  
 Sınıf `ThreadedItem` devraldığı `SyndicationItem` ve `InReplyToElement` kesin türü belirtilmiş bir özellik olarak. Bu kullanışlı programlı erişim sağlayan `InReplyTo` uzantı verileri. Ayrıca uygulayan `TryParseElement` ve `WriteElementExtensions` uzantı verilerini, aşağıdaki kodda gösterildiği gibi yazma ve okuma için.  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StronglyTypedExtensions`  
  
## <a name="see-also"></a>Ayrıca Bkz.
