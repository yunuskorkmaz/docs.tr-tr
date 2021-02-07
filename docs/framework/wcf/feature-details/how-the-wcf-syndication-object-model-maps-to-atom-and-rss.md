---
description: 'Hakkında daha fazla bilgi edinin: WCF dağıtım nesnesi modeli atom ve RSS ile nasıl eşlenir?'
title: WCF Dağıtım Nesnesi Modeli Atom ve RSS Eşlemelerini Nasıl Yapar?
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0365eb37-98cc-4b13-80fb-f1e78847a748
ms.openlocfilehash: d66fb30acde18053e866b8986ebf71a6eed562ec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742946"
---
# <a name="how-the-wcf-syndication-object-model-maps-to-atom-and-rss"></a><span data-ttu-id="ece7c-103">WCF Dağıtım Nesnesi Modeli Atom ve RSS Eşlemelerini Nasıl Yapar?</span><span class="sxs-lookup"><span data-stu-id="ece7c-103">How the WCF Syndication Object Model Maps to Atom and RSS</span></span>

<span data-ttu-id="ece7c-104">Windows Communication Foundation (WCF) bir dağıtım hizmeti geliştirirken, aşağıdaki sınıfları kullanarak akışlar ve öğeler oluşturursunuz:</span><span class="sxs-lookup"><span data-stu-id="ece7c-104">When developing a Windows Communication Foundation (WCF) syndication service, you create feeds and items using the following classes:</span></span>  
  
- <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
- <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
- <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
- <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
- <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
- <xref:System.ServiceModel.Syndication.TextSyndicationContent>  
  
- <xref:System.ServiceModel.Syndication.UrlSyndicationContent>  
  
- <xref:System.ServiceModel.Syndication.XmlSyndicationContent>  
  
 <span data-ttu-id="ece7c-105">Bir <xref:System.ServiceModel.Syndication.SyndicationFeed> biçimlendirici tarafından tanımlanan herhangi bir dağıtım formatında seri hale getirilebilir.</span><span class="sxs-lookup"><span data-stu-id="ece7c-105">A <xref:System.ServiceModel.Syndication.SyndicationFeed> can be serialized into any syndication format for which a formatter is defined.</span></span> <span data-ttu-id="ece7c-106">WCF iki biçim ile birlikte gelir: <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> ve <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> .</span><span class="sxs-lookup"><span data-stu-id="ece7c-106">WCF ships with two formatters: <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> and <xref:System.ServiceModel.Syndication.Rss20FeedFormatter>.</span></span>  
  
 <span data-ttu-id="ece7c-107">Ve etrafında nesne modeli <xref:System.ServiceModel.Syndication.SyndicationFeed> , <xref:System.ServiceModel.Syndication.SyndicationItem> Atom 1,0 belirtimine 2,0 göre daha yakından hizalanır.</span><span class="sxs-lookup"><span data-stu-id="ece7c-107">The object model around <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem> is aligned more closely with the Atom 1.0 specification than the RSS 2.0 specification.</span></span> <span data-ttu-id="ece7c-108">Bunun nedeni, Atom 1,0 'nin RSS 2,0 belirtiminde belirsiz veya atlanmış öğeleri tanımlayan daha önemli bir belirtimdir.</span><span class="sxs-lookup"><span data-stu-id="ece7c-108">This is because Atom 1.0 is a more substantial specification that defines elements that are ambiguous or omitted from the RSS 2.0 specification.</span></span> <span data-ttu-id="ece7c-109">Bu nedenle, WCF dağıtım nesne modelindeki birçok öğenin RSS 2,0 belirtiminde doğrudan temsili yoktur.</span><span class="sxs-lookup"><span data-stu-id="ece7c-109">Because of this, many items in the WCF syndication object model have no direct representation in the RSS 2.0 specification.</span></span> <span data-ttu-id="ece7c-110"><xref:System.ServiceModel.Syndication.SyndicationFeed> <xref:System.ServiceModel.Syndication.SyndicationItem> , RSS 2,0 ' de nesneler serileştirilirken ve Atom belirtimine uygun olan ad alanı nitelikli uzantı öğeleri olarak atom 'a özgü veri öğelerini Serileştirmeye olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="ece7c-110">When serializing <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem> objects into RSS 2.0, WCF allows you to serialize Atom-specific data elements as namespace-qualified extension elements that conform to the Atom specification.</span></span> <span data-ttu-id="ece7c-111">Bunu, oluşturucuya geçirilen bir parametre ile kontrol edebilirsiniz <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> .</span><span class="sxs-lookup"><span data-stu-id="ece7c-111">You can control this with a parameter passed to the <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> constructor.</span></span>  
  
 <span data-ttu-id="ece7c-112">Bu konudaki kod örnekleri, gerçek serileştirme yapmak için burada tanımlanan iki yöntemden birini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ece7c-112">The code samples in this topic use one of two methods defined here to do the actual serialization.</span></span>  
  
 <span data-ttu-id="ece7c-113">`SerializeFeed` bir dağıtım akışını seri hale getirir.</span><span class="sxs-lookup"><span data-stu-id="ece7c-113">`SerializeFeed` serializes a syndication feed.</span></span>  
  
 [!code-csharp[SyndicationMapping#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#10)]
 [!code-vb[SyndicationMapping#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#10)]  
  
 <span data-ttu-id="ece7c-114">`SerializeItem` bir dağıtım öğesini seri hale getirir.</span><span class="sxs-lookup"><span data-stu-id="ece7c-114">`SerializeItem` serializes a syndication item.</span></span>  
  
 [!code-csharp[SyndicationMapping#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#11)]
 [!code-vb[SyndicationMapping#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#11)]  
  
## <a name="syndicationfeed"></a><span data-ttu-id="ece7c-115">SyndicationFeed</span><span class="sxs-lookup"><span data-stu-id="ece7c-115">SyndicationFeed</span></span>  

 <span data-ttu-id="ece7c-116">Aşağıdaki kod örneği, <xref:System.ServiceModel.Syndication.SyndicationFeed> sınıfının Atom 1,0 ve RSS 2,0 olarak serileştirilme şeklini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ece7c-116">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.SyndicationFeed> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#0)]
 [!code-vb[SyndicationMapping#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#0)]  
  
 <span data-ttu-id="ece7c-117">Aşağıdaki XML, ' <xref:System.ServiceModel.Syndication.SyndicationFeed> nin Atom 1,0 ' de nasıl serileştirildiği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ece7c-117">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationFeed> is serialized to Atom 1.0.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<feed xml:lang="EN-US" xmlns="http://www.w3.org/2005/Atom">  
  <title type="text">My Feed Title</title>  
  <subtitle type="text">My Feed Description</subtitle>  
  <id>FeedID</id>  
  <rights type="text">Copyright 2007</rights>  
  <updated>2007-08-29T13:57:17-07:00</updated>  
  <category term="categoryName" label="categoryLabel" scheme="categoryScheme" />  
  <logo>http://server/image.jpg</logo>  
  <generator>Sample Code</generator>  
  <link rel="alternate" href="http://myfeeduri/" />  
  <entry>  
    <id>ItemID</id>  
    <title type="text">Item Title</title>  
    <summary type="text">Item Summary</summary>  
    <published>2007-08-29T00:00:00-07:00</published>  
    <updated>2007-08-29T13:57:17-07:00</updated>  
    <author>  
      <name>Jesper Aaberg</name>  
      <uri>http://Jesper/Aaberg</uri>  
      <email>Jesper@Aaberg.com</email>  
    </author>  
    <contributor>  
      <name>Lene Aaling</name>  
      <uri>http://Lene/Aaling</uri>  
      <email>Lene@Aaling.com</email>  
    </contributor>  
    <link rel="alternate" href="http://myitemuri/" />  
    <category term="categoryName" label="categoryLabel" scheme="categoryScheme" />  
    <content type="text">Item Content</content>  
    <rights type="text">Copyright 2007</rights>  
    <source>  
      <title type="text">My Feed Title</title>  
      <subtitle type="text">My Feed Description</subtitle>  
      <id>FeedID</id>  
      <rights type="text">Copyright 2007</rights>  
      <updated>2007-08-29T13:57:17-07:00</updated>  
      <category term="categoryName" label="categoryLabel" scheme="categoryScheme" />  
      <logo>http://server/image.jpg</logo>  
      <generator>Sample Code</generator>  
      <link rel="alternate" href="http://myfeeduri/" />  
    </source>  
  </entry>  
</feed>  
```  
  
 <span data-ttu-id="ece7c-118">Aşağıdaki XML, ' <xref:System.ServiceModel.Syndication.SyndicationFeed> nın RSS 2,0 ' e nasıl serileştirildiği gösterir.</span><span class="sxs-lookup"><span data-stu-id="ece7c-118">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationFeed> is serialized to RSS 2.0.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<rss xmlns:a10="http://www.w3.org/2005/Atom" version="2.0">  
  <channel>  
    <title>My Feed Title</title>  
    <link>http://myfeeduri/</link>  
    <description>My Feed Description</description>  
    <language>EN-US</language>  
    <copyright>Copyright 2007</copyright>  
    <lastBuildDate>Wed, 29 Aug 2007 13:57:17 -0700</lastBuildDate>  
    <category domain="categoryScheme">categoryName</category>  
    <generator>Sample Code</generator>  
    <image>  
      <url>http://server/image.jpg</url>  
      <title>My Feed Title</title>  
      <link>http://myfeeduri/</link>  
    </image>  
    <a10:id>FeedID</a10:id>  
    <item>  
      <guid isPermaLink="false">ItemID</guid>  
      <link>http://myitemuri/</link>  
      <author>Jesper@Aaberg.com</author>  
      <category domain="categoryScheme">categoryName</category>  
      <title>Item Title</title>  
      <description>Item Summary</description>  
      <source>My Feed Title</source>  
      <pubDate>Wed, 29 Aug 2007 00:00:00 -0700</pubDate>  
      <a10:updated>2007-08-29T13:57:17-07:00</a10:updated>  
      <a10:rights type="text">Copyright 2007</a10:rights>  
      <a10:content type="text">Item Content</a10:content>  
      <a10:contributor>  
        <a10:name>Lene Aaling</a10:name>  
        <a10:uri>http://Lene/Aaling</a10:uri>  
        <a10:email>Lene@Aaling.com</a10:email>  
      </a10:contributor>  
    </item>  
  </channel>  
</rss>  
```  
  
## <a name="syndicationitem"></a><span data-ttu-id="ece7c-119">SyndicationItem</span><span class="sxs-lookup"><span data-stu-id="ece7c-119">SyndicationItem</span></span>  

 <span data-ttu-id="ece7c-120">Aşağıdaki kod örneği, <xref:System.ServiceModel.Syndication.SyndicationItem> sınıfının Atom 1,0 ve RSS 2,0 olarak serileştirilme şeklini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ece7c-120">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.SyndicationItem> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#1)]
 [!code-vb[SyndicationMapping#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#1)]  
  
 <span data-ttu-id="ece7c-121">Aşağıdaki XML, ' <xref:System.ServiceModel.Syndication.SyndicationItem> nin Atom 1,0 ' de nasıl serileştirildiği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ece7c-121">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationItem> is serialized to Atom 1.0.</span></span>  
  
```xml  
<entry xmlns="http://www.w3.org/2005/Atom">  
  <id>ItemID</id>  
  <title type="text">Item Title</title>  
  <summary type="text">Item Summary</summary>  
  <published>2007-08-29T00:00:00-07:00</published>  
  <updated>2007-08-29T14:07:09-07:00</updated>  
  <author>  
    <name>Jesper Aaberg</name>  
    <uri>http://Contoso/Aaberg</uri>  
    <email>Jesper.Aaberg@contoso.com</email>  
  </author>  
  <author>  
    <name>Syed Abbas</name>  
    <uri>http://Contoso/Abbas</uri>  
    <email>Syed.Abbas@contoso.com</email>  
  </author>  
  <contributor>  
    <name>Lene Aaling</name>  
    <uri>http://Contoso/Aaling</uri>  
    <email>Lene.Aaling@contoso.com</email>  
  </contributor>  
  <contributor>  
    <name>Kim Abercrombie</name>  
    <uri>http://Contoso/Abercrombie</uri>  
    <email>Kim.Abercrombie@contoso.com</email>  
  </contributor>  
  <link rel="alternate" href="http://myitemuri/" />  
  <category term="categoryName" label="categoryLabel" scheme="categoryScheme" />  
  <category term="categoryName" label="categoryLabel" scheme="categoryScheme" />  
  <content type="text">Item Content</content>  
  <rights type="text">Copyright 2007</rights>  
  <source>  
    <title type="text">My Feed Title</title>  
    <subtitle type="text">My Feed Description</subtitle>  
    <link rel="alternate" href="http://myfeeduri/" />  
  </source>  
</entry>  
```  
  
 <span data-ttu-id="ece7c-122">Aşağıdaki XML, ' <xref:System.ServiceModel.Syndication.SyndicationItem> nın RSS 2,0 ' e nasıl serileştirildiği gösterir.</span><span class="sxs-lookup"><span data-stu-id="ece7c-122">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationItem> is serialized to RSS 2.0.</span></span>  
  
```xml  
<item>  
  <guid isPermaLink="false">ItemID</guid>  
  <link>http://myitemuri/</link>  
  <author xmlns="http://www.w3.org/2005/Atom">  
    <name>Jesper Aaberg</name>  
    <uri>http://Jesper/Aaberg</uri>  
    <email>Jesper@Aaberg.com</email>  
  </author>  
  <author xmlns="http://www.w3.org/2005/Atom">  
    <name>Syed Abbas</name>  
    <uri>http://Contoso/Abbas</uri>  
    <email>Syed.Abbas@contoso.com</email>  
  </author>  
  <category domain="categoryScheme">categoryName</category>  
  <category domain="categoryScheme">categoryName</category>  
  <title>Item Title</title>  
  <description>Item Summary</description>  
  <source>My Feed Title</source>  
  <pubDate>Wed, 29 Aug 2007 00:00:00 -0700</pubDate>  
  <updated xmlns="http://www.w3.org/2005/Atom">2007-08-29T14:07:09-07:00</updated>  
  <rights type="text" xmlns="http://www.w3.org/2005/Atom">Copyright 2007</rights>  
  <content type="text" xmlns="http://www.w3.org/2005/Atom">Item Content</content>  
  <contributor xmlns="http://www.w3.org/2005/Atom">  
    <name>Lene Aaling</name>  
    <uri>http://Contoso/Aaling</uri>  
    <email>Lene.Aaling@contoso.com</email>  
  </contributor>  
  <contributor xmlns="http://www.w3.org/2005/Atom">  
    <name>Kim Abercrombie</name>  
    <uri>http://Contoso/Abercrombie</uri>  
    <email>Kim.Abercrombie@contoso.com</email>  
  </contributor>  
</item>  
```  
  
## <a name="syndicationperson"></a><span data-ttu-id="ece7c-123">SyndicationPerson</span><span class="sxs-lookup"><span data-stu-id="ece7c-123">SyndicationPerson</span></span>  

 <span data-ttu-id="ece7c-124">Aşağıdaki kod örneği, <xref:System.ServiceModel.Syndication.SyndicationPerson> sınıfının Atom 1,0 ve RSS 2,0 olarak serileştirilme şeklini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ece7c-124">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.SyndicationPerson> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#2)]
 [!code-vb[SyndicationMapping#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#2)]  
  
 <span data-ttu-id="ece7c-125">Aşağıdaki XML, ' <xref:System.ServiceModel.Syndication.SyndicationPerson> nin Atom 1,0 ' de nasıl serileştirildiği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ece7c-125">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationPerson> is serialized to Atom 1.0.</span></span>  
  
```xml  
  <author>  
    <name>Jesper Aaberg</name>  
    <uri>http://Contoso/Aaberg</uri>  
    <email>Jesper.Aaberg@contoso.com</email>  
  </author>  
<contributor>  
    <name>Lene Aaling</name>  
    <uri>http://Contoso/Aaling</uri>  
    <email>Lene.Aaling@contoso.com</email>  
  </contributor>  
```  
  
 <span data-ttu-id="ece7c-126">Aşağıdaki XML, <xref:System.ServiceModel.Syndication.SyndicationPerson> veya koleksiyonlarında yalnızca bir tane varsa, SıNıFıNıN RSS 2,0 'e nasıl serileştirildiği gösterilmektedir <xref:System.ServiceModel.Syndication.SyndicationPerson> `Authors` `Contributors` .</span><span class="sxs-lookup"><span data-stu-id="ece7c-126">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationPerson> class is serialized to RSS 2.0 if only one <xref:System.ServiceModel.Syndication.SyndicationPerson> exists in the `Authors` or `Contributors` collections, respectively.</span></span>  
  
```xml  
<author>Jesper.Aaberg@contoso.com</author>  
<a10:contributor>  
    <a10:name>Lene Aaling</a10:name>  
    <a10:uri>http://Contoso/Aaling</a10:uri>  
    <a10:email>Lene.Aaling@contoso.com</a10:email>  
</a10:contributor>  
```  
  
 <span data-ttu-id="ece7c-127">Aşağıdaki XML, <xref:System.ServiceModel.Syndication.SyndicationPerson> ya da koleksiyonlarında birden fazla varsa, SıNıFıNıN RSS 2,0 'e nasıl serileştirildiği gösterilmektedir <xref:System.ServiceModel.Syndication.SyndicationPerson> `Authors` `Contributors` .</span><span class="sxs-lookup"><span data-stu-id="ece7c-127">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationPerson> class is serialized to RSS 2.0 if more than one <xref:System.ServiceModel.Syndication.SyndicationPerson> exists in the `Authors` or `Contributors` collections, respectively.</span></span>  
  
```xml  
<a10:author>  
    <a10:name>Jesper Aaberg</a10:name>  
    <a10:uri>http://Contoso/Aaberg</a10:uri>  
    <a10:email>Jesper.Aaberg@contoso.com</a10:email>  
</a10:author>  
<a10:author>  
    <a10:name>Syed Abbas</a10:name>  
    <a10:uri>http://Contoso/Abbas</a10:uri>  
    <a10:email>Syed.Abbas@contoso.com</a10:email>  
</a10:author>  
<a10:contributor>  
    <a10:name>Lene Aaling</a10:name>  
    <a10:uri>http://Contoso/Aaling</a10:uri>  
    <a10:email>Lene.Aaling@contoso.com</a10:email>  
</a10:contributor>  
<a10:contributor>  
    <a10:name>Kim Abercrombie</a10:name>  
    <a10:uri>http://Contoso/Abercrombie</a10:uri>  
    <a10:email>Kim.Abercrombie@contoso.com</a10:email>  
</a10:contributor>  
```  
  
## <a name="syndicationlink"></a><span data-ttu-id="ece7c-128">SyndicationLink</span><span class="sxs-lookup"><span data-stu-id="ece7c-128">SyndicationLink</span></span>  

 <span data-ttu-id="ece7c-129">Aşağıdaki kod örneği, <xref:System.ServiceModel.Syndication.SyndicationLink> sınıfının Atom 1,0 ve RSS 2,0 olarak serileştirilme şeklini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ece7c-129">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.SyndicationLink> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#3)]
 [!code-vb[SyndicationMapping#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#3)]  
  
 <span data-ttu-id="ece7c-130">Aşağıdaki XML, ' <xref:System.ServiceModel.Syndication.SyndicationLink> nin Atom 1,0 ' de nasıl serileştirildiği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ece7c-130">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationLink> is serialized to Atom 1.0.</span></span>  
  
 `<link rel="alternate" type="text/html" title="My Link Title" length="2048" href="http://contoso/MyLink" />`  
  
 <span data-ttu-id="ece7c-131">Aşağıdaki XML, ' <xref:System.ServiceModel.Syndication.SyndicationLink> nın RSS 2,0 ' e nasıl serileştirildiği gösterir.</span><span class="sxs-lookup"><span data-stu-id="ece7c-131">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationLink> is serialized to RSS 2.0.</span></span>  
  
 `<a10:link rel="alternate" type="text/html" title="My Link Title" length="2048" href="http://contoso/MyLink" />`  
  
## <a name="syndicationcategory"></a><span data-ttu-id="ece7c-132">SyndicationCategory</span><span class="sxs-lookup"><span data-stu-id="ece7c-132">SyndicationCategory</span></span>  

 <span data-ttu-id="ece7c-133">Aşağıdaki kod örneği, <xref:System.ServiceModel.Syndication.SyndicationCategory> sınıfının Atom 1,0 ve RSS 2,0 olarak serileştirilme şeklini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ece7c-133">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.SyndicationCategory> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#4)]
 [!code-vb[SyndicationMapping#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#4)]  
  
 <span data-ttu-id="ece7c-134">Aşağıdaki XML, ' <xref:System.ServiceModel.Syndication.SyndicationCategory> nin Atom 1,0 ' de nasıl serileştirildiği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ece7c-134">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationCategory> is serialized to Atom 1.0.</span></span>  
  
 `<category term="categoryName" label="categoryLabel" scheme="categoryScheme" />`  
  
 <span data-ttu-id="ece7c-135">Aşağıdaki XML, ' <xref:System.ServiceModel.Syndication.SyndicationCategory> nın RSS 2,0 ' e nasıl serileştirildiği gösterir.</span><span class="sxs-lookup"><span data-stu-id="ece7c-135">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationCategory> is serialized to RSS 2.0.</span></span>  
  
 `<category domain="categoryScheme">categoryName</category>`  
  
## <a name="textsyndicationcontent"></a><span data-ttu-id="ece7c-136">TextSyndicationContent</span><span class="sxs-lookup"><span data-stu-id="ece7c-136">TextSyndicationContent</span></span>  

 <span data-ttu-id="ece7c-137">Aşağıdaki kod örneği, <xref:System.ServiceModel.Syndication.TextSyndicationContent> HTML içeriğiyle oluşturulduğunda sınıfının Atom 1,0 ve RSS 2,0 olarak serileştirilme şeklini gösterir <xref:System.ServiceModel.Syndication.TextSyndicationContent> .</span><span class="sxs-lookup"><span data-stu-id="ece7c-137">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class to Atom 1.0 and RSS 2.0 when <xref:System.ServiceModel.Syndication.TextSyndicationContent> is created with HTML content.</span></span>  
  
 [!code-csharp[SyndicationMapping#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#5)]
 [!code-vb[SyndicationMapping#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#5)]  
  
 <span data-ttu-id="ece7c-138">Aşağıdaki XML, <xref:System.ServiceModel.Syndication.TextSyndicationContent> HTML içeriğine sahip sınıfın Atom 1,0 ' de nasıl serileştirildiği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ece7c-138">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with HTML content is serialized to Atom 1.0.</span></span>  
  
 `<content type="html"><html> some html </html></content>`  
  
 <span data-ttu-id="ece7c-139">Aşağıdaki XML, <xref:System.ServiceModel.Syndication.TextSyndicationContent> sınıfının nasıl RSS 2,0 ' e serileştirildiği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ece7c-139">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with HTML content is serialized to RSS 2.0.</span></span>  
  
 `<description><html> some html </html></description>`  
  
 <span data-ttu-id="ece7c-140">Aşağıdaki kod örneği, <xref:System.ServiceModel.Syndication.TextSyndicationContent> düz metin içeriğiyle oluşturulduğunda sınıfının Atom 1,0 ve RSS 2,0 ' ye nasıl serileştirilmek <xref:System.ServiceModel.Syndication.TextSyndicationContent> olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ece7c-140">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class to Atom 1.0 and RSS 2.0 when <xref:System.ServiceModel.Syndication.TextSyndicationContent> is created with plain text content.</span></span>  
  
 [!code-csharp[SyndicationMapping#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#6)]
 [!code-vb[SyndicationMapping#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#6)]  
  
 <span data-ttu-id="ece7c-141">Aşağıdaki XML, <xref:System.ServiceModel.Syndication.TextSyndicationContent> düz metin içeriğine sahip sınıfın Atom 1,0 ' de nasıl serileştirildiği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ece7c-141">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with plain text content is serialized to Atom 1.0.</span></span>  
  
 `<content type="text">Some Plain Text</content>`  
  
 <span data-ttu-id="ece7c-142">Aşağıdaki XML, <xref:System.ServiceModel.Syndication.TextSyndicationContent> düz metin içeriğine sahip sınıfın nasıl bır RSS 2,0 serileştirildiği gösterir.</span><span class="sxs-lookup"><span data-stu-id="ece7c-142">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with plain text content is serialized to RSS 2.0.</span></span>  
  
 `<description>Some Plain Text</description>`  
  
 <span data-ttu-id="ece7c-143">Aşağıdaki kod örneği, <xref:System.ServiceModel.Syndication.TextSyndicationContent> <xref:System.ServiceModel.Syndication.TextSyndicationContent> XHTML içerik ile oluşturulduğunda sınıfının Atom 1,0 ve RSS 2,0 olarak serileştirilme şeklini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ece7c-143">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class to Atom 1.0 and RSS 2.0 when <xref:System.ServiceModel.Syndication.TextSyndicationContent> is created with XHTML content.</span></span>  
  
 [!code-csharp[SyndicationMapping#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#7)]
 [!code-vb[SyndicationMapping#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#7)]  
  
 <span data-ttu-id="ece7c-144">Aşağıdaki XML, <xref:System.ServiceModel.Syndication.TextSyndicationContent> XHTML içeriğine sahip sınıfın Atom 1,0 ' de nasıl serileştirildiği gösterir.</span><span class="sxs-lookup"><span data-stu-id="ece7c-144">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with XHTML content is serialized to Atom 1.0.</span></span>  
  
 `<content type="xhtml">`  
  
 `<html> some xhtml </html>`  
  
 `</content>`  
  
 <span data-ttu-id="ece7c-145">Aşağıdaki XML, <xref:System.ServiceModel.Syndication.TextSyndicationContent> XHTML içeriğine sahip sınıfın nasıl 2,0 RSS 'e serileştirildiği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ece7c-145">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with XHTML content is serialized to RSS 2.0.</span></span>  
  
 `<description><html> some xhtml </html></description>`  
  
## <a name="urlsyndicationcontent"></a><span data-ttu-id="ece7c-146">UrlSyndicationContent</span><span class="sxs-lookup"><span data-stu-id="ece7c-146">UrlSyndicationContent</span></span>  

 <span data-ttu-id="ece7c-147">Aşağıdaki kod örneği, <xref:System.ServiceModel.Syndication.UrlSyndicationContent> sınıfının Atom 1,0 ve RSS 2,0 olarak serileştirilme şeklini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ece7c-147">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.UrlSyndicationContent> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#8)]
 [!code-vb[SyndicationMapping#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#8)]  
  
 <span data-ttu-id="ece7c-148">Aşağıdaki XML, <xref:System.ServiceModel.Syndication.UrlSyndicationContent> sınıfının Atom 1,0 ' de nasıl serileştirildiği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ece7c-148">The following XML shows how the <xref:System.ServiceModel.Syndication.UrlSyndicationContent> class is serialized to Atom 1.0.</span></span>  
  
 `<content type="audio" src="http://someurl/" />`  
  
 <span data-ttu-id="ece7c-149">Aşağıdaki XML, <xref:System.ServiceModel.Syndication.UrlSyndicationContent> XHTML içeriğine sahip sınıfın nasıl 2,0 RSS 'e serileştirildiği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ece7c-149">The following XML shows how the <xref:System.ServiceModel.Syndication.UrlSyndicationContent> class with XHTML content is serialized to RSS 2.0.</span></span>  
  
 `<description />`  
  
 `<content type="audio" src="http://Contoso/someurl/" xmlns="http://www.w3.org/2005/Atom" />`  
  
## <a name="xmlsyndicationcontent"></a><span data-ttu-id="ece7c-150">XmlSyndicationContent</span><span class="sxs-lookup"><span data-stu-id="ece7c-150">XmlSyndicationContent</span></span>  

 <span data-ttu-id="ece7c-151">Aşağıdaki kod örneği, <xref:System.ServiceModel.Syndication.XmlSyndicationContent> sınıfının Atom 1,0 ve RSS 2,0 olarak serileştirilme şeklini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ece7c-151">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.XmlSyndicationContent> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#9)]
 [!code-vb[SyndicationMapping#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#9)]  
  
 <span data-ttu-id="ece7c-152">Aşağıdaki XML, <xref:System.ServiceModel.Syndication.XmlSyndicationContent> sınıfının Atom 1,0 ' de nasıl serileştirildiği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ece7c-152">The following XML shows how the <xref:System.ServiceModel.Syndication.XmlSyndicationContent> class is serialized to Atom 1.0.</span></span>  
  
 `<content type="mytype">`  
  
 `<SomeData xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/FeedMapping" />`  
  
 `</content>`  
  
 <span data-ttu-id="ece7c-153">Aşağıdaki XML, <xref:System.ServiceModel.Syndication.XmlSyndicationContent> XHTML içeriğine sahip sınıfın nasıl 2,0 RSS 'e serileştirildiği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ece7c-153">The following XML shows how the <xref:System.ServiceModel.Syndication.XmlSyndicationContent> class with XHTML content is serialized to RSS 2.0.</span></span>  
  
 `<content type="mytype" xmlns="http://www.w3.org/2005/Atom">`  
  
 `<SomeData xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/FeedMapping" />`  
  
 `</content>`  
  
## <a name="see-also"></a><span data-ttu-id="ece7c-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ece7c-154">See also</span></span>

- [<span data-ttu-id="ece7c-155">WCF Dağıtımı Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ece7c-155">WCF Syndication Overview</span></span>](wcf-syndication-overview.md)
- [<span data-ttu-id="ece7c-156">Dağıtım Mimarisi</span><span class="sxs-lookup"><span data-stu-id="ece7c-156">Architecture of Syndication</span></span>](architecture-of-syndication.md)
- [<span data-ttu-id="ece7c-157">Nasıl yapılır: Temel Bir RSS Akışı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ece7c-157">How to: Create a Basic RSS Feed</span></span>](how-to-create-a-basic-rss-feed.md)
- [<span data-ttu-id="ece7c-158">Nasıl yapılır: Temel Bir Atom Akışı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ece7c-158">How to: Create a Basic Atom Feed</span></span>](how-to-create-a-basic-atom-feed.md)
- [<span data-ttu-id="ece7c-159">Nasıl yapılır: Bir Akışı Hem Atom Hem de RSS Olarak Kullanıma Sunma</span><span class="sxs-lookup"><span data-stu-id="ece7c-159">How to: Expose a Feed as Both Atom and RSS</span></span>](how-to-expose-a-feed-as-both-atom-and-rss.md)
