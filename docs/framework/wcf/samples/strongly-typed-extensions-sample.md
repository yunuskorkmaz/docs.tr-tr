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
# <a name="strongly-typed-extensions-sample"></a><span data-ttu-id="c5578-102">Güçlü Yazılmış Uzantılar Örneği</span><span class="sxs-lookup"><span data-stu-id="c5578-102">Strongly-Typed Extensions Sample</span></span>
<span data-ttu-id="c5578-103">Örnek, <xref:System.ServiceModel.Syndication.SyndicationFeed> sınıfı örnek amaçları için kullanır.</span><span class="sxs-lookup"><span data-stu-id="c5578-103">The sample uses the <xref:System.ServiceModel.Syndication.SyndicationFeed> class for the purposes of the example.</span></span> <span data-ttu-id="c5578-104">Ancak, bu örnekte gösterilen desenler, uzantı verilerini destekleyen tüm Sendikasyon sınıfları ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c5578-104">However, the patterns demonstrated in this sample can be used with all of the Syndication classes that support extension data.</span></span>  
  
 <span data-ttu-id="c5578-105">Sendikasyon nesnesi<xref:System.ServiceModel.Syndication.SyndicationFeed>modeli <xref:System.ServiceModel.Syndication.SyndicationItem>( , , ve ilgili sınıflar) <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> ve <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> özelliklerini kullanarak uzantı verilerine gevşek dakti-yazılı erişimi destekler.</span><span class="sxs-lookup"><span data-stu-id="c5578-105">The Syndication object model (<xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem>, and related classes) supports loosely-typed access to extension data by using the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> and <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> properties.</span></span> <span data-ttu-id="c5578-106">Bu örnek, özel türemiş sınıfları uygulayarak <xref:System.ServiceModel.Syndication.SyndicationFeed> uzantı verilerine <xref:System.ServiceModel.Syndication.SyndicationItem> güçlü bir şekilde daktiledilen erişimin nasıl sağlayabileceğini ve belirli uygulamaya özgü uzantıları güçlü bir şekilde yazılmış özellikler olarak kullanılabilir hale getirerek gösterir.</span><span class="sxs-lookup"><span data-stu-id="c5578-106">This sample shows how to provide strongly-typed access to extension data by implementing custom derived classes of <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem> that make available certain application-specific extensions as strongly-typed properties.</span></span>  
  
 <span data-ttu-id="c5578-107">Örnek olarak, bu örnek, önerilen Atom İş parçacığı uzantıları RFC tanımlanan bir uzantı öğesi nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c5578-107">As an example, this sample shows how to implement an extension element defined in the proposed Atom Threading Extensions RFC.</span></span> <span data-ttu-id="c5578-108">Bu yalnızca gösteri amaçlıdır ve bu örnek önerilen belirtimin tam olarak uygulanması için tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="c5578-108">This is for demonstration purposes only and this sample is not intended to be a full implementation of the proposed specification.</span></span>  
  
## <a name="sample-xml"></a><span data-ttu-id="c5578-109">Örnek XML</span><span class="sxs-lookup"><span data-stu-id="c5578-109">Sample XML</span></span>  
 <span data-ttu-id="c5578-110">Aşağıdaki XML örneği, ek `<in-reply-to>` bir uzantı öğesi içeren bir Atom 1.0 girişini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c5578-110">The following XML example shows an Atom 1.0 entry with an additional `<in-reply-to>` extension element.</span></span>  
  
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
  
 <span data-ttu-id="c5578-111">Öğe, `<in-reply-to>` ek uzantı`ref` `type` özniteliklerinin `href`ve uzantı öğelerinin varlığına izin verirken, gerekli üç özniteliği (ve ) belirtir.</span><span class="sxs-lookup"><span data-stu-id="c5578-111">The `<in-reply-to>` element specifies three required attributes (`ref`, `type` and `href`) while also allowing for the presence of additional extension attributes and extension elements.</span></span>  
  
## <a name="modeling-the-in-reply-to-element"></a><span data-ttu-id="c5578-112">Yanıt-Yanıt-Yanıt öğesini modelleme</span><span class="sxs-lookup"><span data-stu-id="c5578-112">Modeling the In-Reply-To element</span></span>  
 <span data-ttu-id="c5578-113">Bu örnekte, `<in-reply-to>` eleman CLR <xref:System.Xml.Serialization.IXmlSerializable>olarak modellenir, hangi ile kullanılmasını <xref:System.Runtime.Serialization.DataContractSerializer>sağlar .</span><span class="sxs-lookup"><span data-stu-id="c5578-113">In this sample, the `<in-reply-to>` element is modeled as CLR that implements <xref:System.Xml.Serialization.IXmlSerializable>, which enables its use with the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="c5578-114">Ayrıca, aşağıdaki örnek kodda gösterildiği gibi öğenin verilerine erişmek için bazı yöntemler ve özellikler uygular.</span><span class="sxs-lookup"><span data-stu-id="c5578-114">It also implements some methods and properties for accessing the element’s data, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="c5578-115">`InReplyToElement` Sınıf, gerekli öznitelik (`HRef`, `MediaType`, `Source`ve ) özelliklerinin yanı <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>sıra tutmak için koleksiyonlar ve .</span><span class="sxs-lookup"><span data-stu-id="c5578-115">The `InReplyToElement` class implements properties for the required attribute (`HRef`, `MediaType`, and `Source`) as well as collections to hold <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> and <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>.</span></span>  
  
 <span data-ttu-id="c5578-116">Sınıf, `InReplyToElement` nesne <xref:System.Xml.Serialization.IXmlSerializable> örneklerinin XML'den nasıl okunduğu ve yazıldığı üzerinde doğrudan denetim sağlayan arabirimi uygular.</span><span class="sxs-lookup"><span data-stu-id="c5578-116">The `InReplyToElement` class implements the <xref:System.Xml.Serialization.IXmlSerializable> interface, which allows direct control over how object instances are read from and written to XML.</span></span> <span data-ttu-id="c5578-117">Yöntem `ReadXml` ilk `Ref` `HRef` <xref:System.Xml.XmlReader> olarak, geçirilen , `Source`, `MediaType` ve özellikleriiçin değerleri okur.</span><span class="sxs-lookup"><span data-stu-id="c5578-117">The `ReadXml` method first reads the values for the `Ref`, `HRef`, `Source`, and `MediaType` properties from the <xref:System.Xml.XmlReader> passed to it.</span></span> <span data-ttu-id="c5578-118">Bilinmeyen öznitelikler <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> koleksiyonda depolanır.</span><span class="sxs-lookup"><span data-stu-id="c5578-118">Any unknown attributes are stored in the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection.</span></span> <span data-ttu-id="c5578-119">Tüm öznitelikleri okunduğunda, <xref:System.Xml.XmlReader.ReadStartElement> bir sonraki öğeye okuyucu ilerlemek için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="c5578-119">When all the attributes have been read, <xref:System.Xml.XmlReader.ReadStartElement> is called to advance the reader to the next element.</span></span> <span data-ttu-id="c5578-120">Bu sınıf tarafından modellenen öğenin gerekli alt öğeleri olmadığından, `XElement` alt öğeler aşağıdaki kodda gösterildiği gibi arabelleğe alınarak <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> koleksiyonda depolanır.</span><span class="sxs-lookup"><span data-stu-id="c5578-120">Because the element modeled by this class has no required children, the child elements get buffered into `XElement` instances and stored in the <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> collection, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="c5578-121">İçinde `WriteXml`, `InReplyToElement` yöntem ilk xml `Ref`öznitelikleri `Source`olarak `MediaType` , , `HRef`ve`WriteXml` özellikleri değerlerini yazar ( gerçek dış öğenin kendisi `WriteXml`yazmaktan sorumlu değildir, arayan tarafından yapılan gibi ).</span><span class="sxs-lookup"><span data-stu-id="c5578-121">In `WriteXml`, the `InReplyToElement` method first writes out the values of the `Ref`, `HRef`, `Source`, and `MediaType` properties as XML attributes (`WriteXml` is not responsible for writing the actual outer element itself, as that done by the caller of `WriteXml`).</span></span> <span data-ttu-id="c5578-122">Ayrıca aşağıdaki kodda <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> gösterildiği <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> gibi, ve yazar içeriğini yazar.</span><span class="sxs-lookup"><span data-stu-id="c5578-122">It also writes the contents of the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> and <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> to the writer, as shown in the following code.</span></span>  
  
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
  
## <a name="threadedfeed-and-threadeditem"></a><span data-ttu-id="c5578-123">ThreadedFeed ve ThreadedItem</span><span class="sxs-lookup"><span data-stu-id="c5578-123">ThreadedFeed and ThreadedItem</span></span>  
 <span data-ttu-id="c5578-124">Örnekte, `SyndicationItems` uzantıları `InReplyTo` ile `ThreadedItem` sınıf tarafından modellenir.</span><span class="sxs-lookup"><span data-stu-id="c5578-124">In the sample, `SyndicationItems` with `InReplyTo` extensions are modeled by the `ThreadedItem` class.</span></span> <span data-ttu-id="c5578-125">Benzer şekilde, `ThreadedFeed` sınıf `SyndicationFeed` öğeleri tüm örnekleri olan `ThreadedItem`bir .</span><span class="sxs-lookup"><span data-stu-id="c5578-125">Similarly, the `ThreadedFeed` class is a `SyndicationFeed` whose items are all instances of `ThreadedItem`.</span></span>  
  
 <span data-ttu-id="c5578-126">Sınıf `ThreadedFeed` devralır `SyndicationFeed` ve bir `OnCreateItem` `ThreadedItem`döndürmek için geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="c5578-126">The `ThreadedFeed` class inherits from `SyndicationFeed` and overrides `OnCreateItem` to return a `ThreadedItem`.</span></span> <span data-ttu-id="c5578-127">Ayrıca, aşağıdaki kodda gösterildiği `Items` gibi `ThreadedItems`koleksiyona erişmek için bir yöntem uygular.</span><span class="sxs-lookup"><span data-stu-id="c5578-127">It also implements a method for accessing the `Items` collection as `ThreadedItems`, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="c5578-128">Sınıf `ThreadedItem` devralır `SyndicationItem` ve `InReplyToElement` güçlü bir şekilde yazılan bir özellik olarak yapar.</span><span class="sxs-lookup"><span data-stu-id="c5578-128">The class `ThreadedItem` inherits from `SyndicationItem` and makes `InReplyToElement` as a strongly-typed property.</span></span> <span data-ttu-id="c5578-129">`InReplyTo` Bu, uzantı verilerine uygun programlı erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5578-129">This provides for convenient programmatic access to the `InReplyTo` extension data.</span></span> <span data-ttu-id="c5578-130">Ayrıca, aşağıdaki `TryParseElement` `WriteElementExtensions` kodda gösterildiği gibi uzantı verilerini okumak ve yazmak için de uygular.</span><span class="sxs-lookup"><span data-stu-id="c5578-130">It also implements `TryParseElement` and `WriteElementExtensions` for reading and writing its extension data, as shown in the following code.</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c5578-131">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="c5578-131">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="c5578-132">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="c5578-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="c5578-133">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="c5578-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="c5578-134">Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="c5578-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c5578-135">Örnekler bilgisayarınıza zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="c5578-135">The samples may already be installed on your computer.</span></span> <span data-ttu-id="c5578-136">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="c5578-136">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="c5578-137">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="c5578-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c5578-138">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="c5578-138">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StronglyTypedExtensions`  
