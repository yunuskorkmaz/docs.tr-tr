---
title: "WCF Dağıtım Nesnesi Modeli Atom ve RSS Eşlemelerini Nasıl Yapar?"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 0365eb37-98cc-4b13-80fb-f1e78847a748
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 01030ed226a5cdc384db56933325d7c4eeade989
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-the-wcf-syndication-object-model-maps-to-atom-and-rss"></a><span data-ttu-id="12b0b-102">WCF Dağıtım Nesnesi Modeli Atom ve RSS Eşlemelerini Nasıl Yapar?</span><span class="sxs-lookup"><span data-stu-id="12b0b-102">How the WCF Syndication Object Model Maps to Atom and RSS</span></span>
<span data-ttu-id="12b0b-103">Geliştirirken bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] dağıtım hizmeti, oluşturduğunuz akışları ve aşağıdaki sınıflar kullanarak öğeleri:</span><span class="sxs-lookup"><span data-stu-id="12b0b-103">When developing a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] syndication service, you create feeds and items using the following classes:</span></span>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
-   <xref:System.ServiceModel.Syndication.TextSyndicationContent>  
  
-   <xref:System.ServiceModel.Syndication.UrlSyndicationContent>  
  
-   <xref:System.ServiceModel.Syndication.XmlSyndicationContent>  
  
 <span data-ttu-id="12b0b-104">A <xref:System.ServiceModel.Syndication.SyndicationFeed> bir biçimlendirici tanımlanır tüm dağıtım biçiminde seri hale getirilebilir.</span><span class="sxs-lookup"><span data-stu-id="12b0b-104">A <xref:System.ServiceModel.Syndication.SyndicationFeed> can be serialized into any syndication format for which a formatter is defined.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="12b0b-105">iki biçimlendiricileri ile birlikte gelir: <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> ve <xref:System.ServiceModel.Syndication.Rss20FeedFormatter>.</span><span class="sxs-lookup"><span data-stu-id="12b0b-105"> ships with two formatters: <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> and <xref:System.ServiceModel.Syndication.Rss20FeedFormatter>.</span></span>  
  
 <span data-ttu-id="12b0b-106">Nesne modeli çevresinde <xref:System.ServiceModel.Syndication.SyndicationFeed> ve <xref:System.ServiceModel.Syndication.SyndicationItem> RSS 2.0 belirtimi daha Atom 1.0 belirtimiyle daha yakından hizalanır.</span><span class="sxs-lookup"><span data-stu-id="12b0b-106">The object model around <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem> is aligned more closely with the Atom 1.0 specification than the RSS 2.0 specification.</span></span> <span data-ttu-id="12b0b-107">Atom 1.0 belirsiz ya da RSS 2.0 belirtiminden belirtilmemişse öğeleri tanımlayan daha önemli bir belirtimi olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="12b0b-107">This is because Atom 1.0 is a more substantial specification that defines elements that are ambiguous or omitted from the RSS 2.0 specification.</span></span> <span data-ttu-id="12b0b-108">Bu nedenle, birçok öğeleri [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dağıtım nesnesi modeli sahip hiçbir doğrudan gösterimi RSS 2.0 belirtimi.</span><span class="sxs-lookup"><span data-stu-id="12b0b-108">Because of this, many items in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] syndication object model have no direct representation in the RSS 2.0 specification.</span></span> <span data-ttu-id="12b0b-109">Serileştirilirken <xref:System.ServiceModel.Syndication.SyndicationFeed> ve <xref:System.ServiceModel.Syndication.SyndicationItem> RSS 2.0 nesnelerine [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Atom belirtimine uygun ad alanı tam genişletme öğeleri olarak Atom'a özgü veri öğeleri seri olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="12b0b-109">When serializing <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem> objects into RSS 2.0, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] allows you to serialize Atom-specific data elements as namespace-qualified extension elements that conform to the Atom specification.</span></span> <span data-ttu-id="12b0b-110">Bunun için geçirilen parametre ile denetleyebilirsiniz <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="12b0b-110">You can control this with a parameter passed to the <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> constructor.</span></span>  
  
 <span data-ttu-id="12b0b-111">Bu konuda kullanılan iki yöntemden birini kod örnekleri, burada fiili serileştirme yapmak için tanımlanan.</span><span class="sxs-lookup"><span data-stu-id="12b0b-111">The code samples in this topic use one of two methods defined here to do the actual serialization.</span></span>  
  
 <span data-ttu-id="12b0b-112">`SerializeFeed`Akış bir dağıtım serileştirir.</span><span class="sxs-lookup"><span data-stu-id="12b0b-112">`SerializeFeed` serializes a syndication feed.</span></span>  
  
 [!code-csharp[SyndicationMapping#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#10)]
 [!code-vb[SyndicationMapping#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#10)]  
  
 <span data-ttu-id="12b0b-113">`SerializeItem`bir dağıtım öğesi serileştirir.</span><span class="sxs-lookup"><span data-stu-id="12b0b-113">`SerializeItem` serializes a syndication item.</span></span>  
  
 [!code-csharp[SyndicationMapping#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#11)]
 [!code-vb[SyndicationMapping#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#11)]  
  
## <a name="syndicationfeed"></a><span data-ttu-id="12b0b-114">SyndicationFeed</span><span class="sxs-lookup"><span data-stu-id="12b0b-114">SyndicationFeed</span></span>  
 <span data-ttu-id="12b0b-115">Aşağıdaki kod örneğinde, seri hale getirmek gösterilmiştir <xref:System.ServiceModel.Syndication.SyndicationFeed> Atom 1.0 ve RSS 2.0 sınıfı.</span><span class="sxs-lookup"><span data-stu-id="12b0b-115">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.SyndicationFeed> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#0)]
 [!code-vb[SyndicationMapping#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#0)]  
  
 <span data-ttu-id="12b0b-116">Aşağıdaki XML gösterilmektedir nasıl <xref:System.ServiceModel.Syndication.SyndicationFeed> Atom 1.0 için serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="12b0b-116">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationFeed> is serialized to Atom 1.0.</span></span>  
  
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
  
 <span data-ttu-id="12b0b-117">Aşağıdaki XML gösterilmektedir nasıl <xref:System.ServiceModel.Syndication.SyndicationFeed> RSS 2.0 için serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="12b0b-117">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationFeed> is serialized to RSS 2.0.</span></span>  
  
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
  
## <a name="syndicationitem"></a><span data-ttu-id="12b0b-118">SyndicationItem</span><span class="sxs-lookup"><span data-stu-id="12b0b-118">SyndicationItem</span></span>  
 <span data-ttu-id="12b0b-119">Aşağıdaki kod örneğinde, seri hale getirmek gösterilmiştir <xref:System.ServiceModel.Syndication.SyndicationItem> Atom 1.0 ve RSS 2.0 sınıfı.</span><span class="sxs-lookup"><span data-stu-id="12b0b-119">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.SyndicationItem> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#1)]
 [!code-vb[SyndicationMapping#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#1)]  
  
 <span data-ttu-id="12b0b-120">Aşağıdaki XML gösterilmektedir nasıl <xref:System.ServiceModel.Syndication.SyndicationItem> Atom 1.0 için serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="12b0b-120">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationItem> is serialized to Atom 1.0.</span></span>  
  
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
  
 <span data-ttu-id="12b0b-121">Aşağıdaki XML gösterilmektedir nasıl <xref:System.ServiceModel.Syndication.SyndicationItem> RSS 2.0 için serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="12b0b-121">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationItem> is serialized to RSS 2.0.</span></span>  
  
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
  
## <a name="syndicationperson"></a><span data-ttu-id="12b0b-122">SyndicationPerson</span><span class="sxs-lookup"><span data-stu-id="12b0b-122">SyndicationPerson</span></span>  
 <span data-ttu-id="12b0b-123">Aşağıdaki kod örneğinde, seri hale getirmek gösterilmiştir <xref:System.ServiceModel.Syndication.SyndicationPerson> Atom 1.0 ve RSS 2.0 sınıfı.</span><span class="sxs-lookup"><span data-stu-id="12b0b-123">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.SyndicationPerson> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#2)]
 [!code-vb[SyndicationMapping#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#2)]  
  
 <span data-ttu-id="12b0b-124">Aşağıdaki XML gösterilmektedir nasıl <xref:System.ServiceModel.Syndication.SyndicationPerson> Atom 1.0 için serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="12b0b-124">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationPerson> is serialized to Atom 1.0.</span></span>  
  
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
  
 <span data-ttu-id="12b0b-125">Aşağıdaki XML gösterilmektedir nasıl <xref:System.ServiceModel.Syndication.SyndicationPerson> sınıfı yalnızca bir RSS 2.0 serileştirilmiş <xref:System.ServiceModel.Syndication.SyndicationPerson> bulunmaktadır `Authors` veya `Contributors` koleksiyonlar, sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="12b0b-125">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationPerson> class is serialized to RSS 2.0 if only one <xref:System.ServiceModel.Syndication.SyndicationPerson> exists in the `Authors` or `Contributors` collections, respectively.</span></span>  
  
```xml  
<author>Jesper.Aaberg@contoso.com</author>  
<a10:contributor>  
    <a10:name>Lene Aaling</a10:name>  
    <a10:uri>http://Contoso/Aaling</a10:uri>  
    <a10:email>Lene.Aaling@contoso.com</a10:email>  
</a10:contributor>  
```  
  
 <span data-ttu-id="12b0b-126">Aşağıdaki XML gösterilmektedir nasıl <xref:System.ServiceModel.Syndication.SyndicationPerson> sınıfı birden fazla RSS 2.0 serileştirilmiş <xref:System.ServiceModel.Syndication.SyndicationPerson> bulunmaktadır `Authors` veya `Contributors` koleksiyonlar, sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="12b0b-126">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationPerson> class is serialized to RSS 2.0 if more than one <xref:System.ServiceModel.Syndication.SyndicationPerson> exists in the `Authors` or `Contributors` collections, respectively.</span></span>  
  
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
  
## <a name="syndicationlink"></a><span data-ttu-id="12b0b-127">SyndicationLink</span><span class="sxs-lookup"><span data-stu-id="12b0b-127">SyndicationLink</span></span>  
 <span data-ttu-id="12b0b-128">Aşağıdaki kod örneğinde, seri hale getirmek gösterilmiştir <xref:System.ServiceModel.Syndication.SyndicationLink> Atom 1.0 ve RSS 2.0 sınıfı.</span><span class="sxs-lookup"><span data-stu-id="12b0b-128">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.SyndicationLink> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#3)]
 [!code-vb[SyndicationMapping#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#3)]  
  
 <span data-ttu-id="12b0b-129">Aşağıdaki XML gösterilmektedir nasıl <xref:System.ServiceModel.Syndication.SyndicationLink> Atom 1.0 için serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="12b0b-129">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationLink> is serialized to Atom 1.0.</span></span>  
  
 `<link rel="alternate" type="text/html" title="My Link Title" length="2048" href="http://contoso/MyLink" />`  
  
 <span data-ttu-id="12b0b-130">Aşağıdaki XML gösterilmektedir nasıl <xref:System.ServiceModel.Syndication.SyndicationLink> RSS 2.0 için serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="12b0b-130">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationLink> is serialized to RSS 2.0.</span></span>  
  
 `<a10:link rel="alternate" type="text/html" title="My Link Title" length="2048" href="http://contoso/MyLink" />`  
  
## <a name="syndicationcategory"></a><span data-ttu-id="12b0b-131">SyndicationCategory</span><span class="sxs-lookup"><span data-stu-id="12b0b-131">SyndicationCategory</span></span>  
 <span data-ttu-id="12b0b-132">Aşağıdaki kod örneğinde, seri hale getirmek gösterilmiştir <xref:System.ServiceModel.Syndication.SyndicationCategory> Atom 1.0 ve RSS 2.0 sınıfı.</span><span class="sxs-lookup"><span data-stu-id="12b0b-132">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.SyndicationCategory> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#4)]
 [!code-vb[SyndicationMapping#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#4)]  
  
 <span data-ttu-id="12b0b-133">Aşağıdaki XML gösterilmektedir nasıl <xref:System.ServiceModel.Syndication.SyndicationCategory> Atom 1.0 için serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="12b0b-133">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationCategory> is serialized to Atom 1.0.</span></span>  
  
 `<category term="categoryName" label="categoryLabel" scheme="categoryScheme" />`  
  
 <span data-ttu-id="12b0b-134">Aşağıdaki XML gösterilmektedir nasıl <xref:System.ServiceModel.Syndication.SyndicationCategory> RSS 2.0 için serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="12b0b-134">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationCategory> is serialized to RSS 2.0.</span></span>  
  
 `<category domain="categoryScheme">categoryName</category>`  
  
## <a name="textsyndicationcontent"></a><span data-ttu-id="12b0b-135">TextSyndicationContent</span><span class="sxs-lookup"><span data-stu-id="12b0b-135">TextSyndicationContent</span></span>  
 <span data-ttu-id="12b0b-136">Aşağıdaki kod örneğinde, seri hale getirmek gösterilmiştir <xref:System.ServiceModel.Syndication.TextSyndicationContent> Atom 1.0 ve RSS 2.0 sınıfına zaman <xref:System.ServiceModel.Syndication.TextSyndicationContent> HTML içeriği ile oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="12b0b-136">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class to Atom 1.0 and RSS 2.0 when <xref:System.ServiceModel.Syndication.TextSyndicationContent> is created with HTML content.</span></span>  
  
 [!code-csharp[SyndicationMapping#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#5)]
 [!code-vb[SyndicationMapping#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#5)]  
  
 <span data-ttu-id="12b0b-137">Aşağıdaki XML gösterilmektedir nasıl <xref:System.ServiceModel.Syndication.TextSyndicationContent> HTML içeriğini sınıfıyla Atom 1.0 serileştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="12b0b-137">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with HTML content is serialized to Atom 1.0.</span></span>  
  
 `<content type="html"><html> some html </html></content>`  
  
 <span data-ttu-id="12b0b-138">Aşağıdaki XML gösterilmektedir nasıl <xref:System.ServiceModel.Syndication.TextSyndicationContent> HTML içeriğini sınıfıyla RSS 2.0 serileştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="12b0b-138">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with HTML content is serialized to RSS 2.0.</span></span>  
  
 `<description><html> some html </html></description>`  
  
 <span data-ttu-id="12b0b-139">Aşağıdaki kod örneğinde, seri hale getirmek gösterilmiştir <xref:System.ServiceModel.Syndication.TextSyndicationContent> Atom 1.0 ve RSS 2.0 sınıfına zaman <xref:System.ServiceModel.Syndication.TextSyndicationContent> düz metin içeriği ile oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="12b0b-139">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class to Atom 1.0 and RSS 2.0 when <xref:System.ServiceModel.Syndication.TextSyndicationContent> is created with plain text content.</span></span>  
  
 [!code-csharp[SyndicationMapping#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#6)]
 [!code-vb[SyndicationMapping#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#6)]  
  
 <span data-ttu-id="12b0b-140">Aşağıdaki XML gösterilmektedir nasıl <xref:System.ServiceModel.Syndication.TextSyndicationContent> düz metin içeriği sınıfıyla Atom 1.0 için serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="12b0b-140">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with plain text content is serialized to Atom 1.0.</span></span>  
  
 `<content type="text">Some Plain Text</content>`  
  
 <span data-ttu-id="12b0b-141">Aşağıdaki XML gösterilmektedir nasıl <xref:System.ServiceModel.Syndication.TextSyndicationContent> düz metin içeriği sınıfıyla RSS 2.0 için serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="12b0b-141">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with plain text content is serialized to RSS 2.0.</span></span>  
  
 `<description>Some Plain Text</description>`  
  
 <span data-ttu-id="12b0b-142">Aşağıdaki kod örneğinde, seri hale getirmek gösterilmiştir <xref:System.ServiceModel.Syndication.TextSyndicationContent> Atom 1.0 ve RSS 2.0 sınıfına zaman <xref:System.ServiceModel.Syndication.TextSyndicationContent> XHTML içerikle oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="12b0b-142">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class to Atom 1.0 and RSS 2.0 when <xref:System.ServiceModel.Syndication.TextSyndicationContent> is created with XHTML content.</span></span>  
  
 [!code-csharp[SyndicationMapping#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#7)]
 [!code-vb[SyndicationMapping#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#7)]  
  
 <span data-ttu-id="12b0b-143">Aşağıdaki XML gösterilmektedir nasıl <xref:System.ServiceModel.Syndication.TextSyndicationContent> XHTML içerikle sınıfı Atom 1.0 serileştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="12b0b-143">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with XHTML content is serialized to Atom 1.0.</span></span>  
  
 `<content type="xhtml">`  
  
 `<html> some xhtml </html>`  
  
 `</content>`  
  
 <span data-ttu-id="12b0b-144">Aşağıdaki XML gösterilmektedir nasıl <xref:System.ServiceModel.Syndication.TextSyndicationContent> XHTML içerikle sınıfı RSS 2.0 serileştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="12b0b-144">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with XHTML content is serialized to RSS 2.0.</span></span>  
  
 `<description><html> some xhtml </html></description>`  
  
## <a name="urlsyndicationcontent"></a><span data-ttu-id="12b0b-145">UrlSyndicationContent</span><span class="sxs-lookup"><span data-stu-id="12b0b-145">UrlSyndicationContent</span></span>  
 <span data-ttu-id="12b0b-146">Aşağıdaki kod örneğinde, seri hale getirmek gösterilmiştir <xref:System.ServiceModel.Syndication.UrlSyndicationContent> Atom 1.0 ve RSS 2.0 sınıfı.</span><span class="sxs-lookup"><span data-stu-id="12b0b-146">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.UrlSyndicationContent> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#8)]
 [!code-vb[SyndicationMapping#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#8)]  
  
 <span data-ttu-id="12b0b-147">Aşağıdaki XML gösterilmektedir nasıl <xref:System.ServiceModel.Syndication.UrlSyndicationContent> sınıfı Atom 1.0 için serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="12b0b-147">The following XML shows how the <xref:System.ServiceModel.Syndication.UrlSyndicationContent> class is serialized to Atom 1.0.</span></span>  
  
 `<content type="audio" src="http://someurl/" />`  
  
 <span data-ttu-id="12b0b-148">Aşağıdaki XML gösterilmektedir nasıl <xref:System.ServiceModel.Syndication.UrlSyndicationContent> XHTML içerikle sınıfı RSS 2.0 serileştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="12b0b-148">The following XML shows how the <xref:System.ServiceModel.Syndication.UrlSyndicationContent> class with XHTML content is serialized to RSS 2.0.</span></span>  
  
 `<description />`  
  
 `<content type="audio" src="http://Contoso/someurl/" xmlns="http://www.w3.org/2005/Atom" />`  
  
## <a name="xmlsyndicationcontent"></a><span data-ttu-id="12b0b-149">XmlSyndicationContent</span><span class="sxs-lookup"><span data-stu-id="12b0b-149">XmlSyndicationContent</span></span>  
 <span data-ttu-id="12b0b-150">Aşağıdaki kod örneğinde, seri hale getirmek gösterilmiştir <xref:System.ServiceModel.Syndication.XmlSyndicationContent> Atom 1.0 ve RSS 2.0 sınıfı.</span><span class="sxs-lookup"><span data-stu-id="12b0b-150">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.XmlSyndicationContent> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#9)]
 [!code-vb[SyndicationMapping#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#9)]  
  
 <span data-ttu-id="12b0b-151">Aşağıdaki XML gösterilmektedir nasıl <xref:System.ServiceModel.Syndication.XmlSyndicationContent> sınıfı Atom 1.0 için serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="12b0b-151">The following XML shows how the <xref:System.ServiceModel.Syndication.XmlSyndicationContent> class is serialized to Atom 1.0.</span></span>  
  
 `<content type="mytype">`  
  
 `<SomeData xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/FeedMapping" />`  
  
 `</content>`  
  
 <span data-ttu-id="12b0b-152">Aşağıdaki XML gösterilmektedir nasıl <xref:System.ServiceModel.Syndication.XmlSyndicationContent> XHTML içerikle sınıfı RSS 2.0 serileştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="12b0b-152">The following XML shows how the <xref:System.ServiceModel.Syndication.XmlSyndicationContent> class with XHTML content is serialized to RSS 2.0.</span></span>  
  
 `<content type="mytype" xmlns="http://www.w3.org/2005/Atom">`  
  
 `<SomeData xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/FeedMapping" />`  
  
 `</content>`  
  
## <a name="see-also"></a><span data-ttu-id="12b0b-153">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="12b0b-153">See Also</span></span>  
 [<span data-ttu-id="12b0b-154">WCF Dağıtımı Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="12b0b-154">WCF Syndication Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md)  
 [<span data-ttu-id="12b0b-155">Dağıtım Mimarisi</span><span class="sxs-lookup"><span data-stu-id="12b0b-155">Architecture of Syndication</span></span>](../../../../docs/framework/wcf/feature-details/architecture-of-syndication.md)  
 [<span data-ttu-id="12b0b-156">Nasıl Yapılır: Temel Bir RSS Akışı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="12b0b-156">How to: Create a Basic RSS Feed</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-rss-feed.md)  
 [<span data-ttu-id="12b0b-157">Nasıl Yapılır: Temel Bir Atom Akışı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="12b0b-157">How to: Create a Basic Atom Feed</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-atom-feed.md)  
 [<span data-ttu-id="12b0b-158">Nasıl yapılır: Bir Akışı Hem Atom Hem de RSS Olarak Kullanıma Sunma</span><span class="sxs-lookup"><span data-stu-id="12b0b-158">How to: Expose a Feed as Both Atom and RSS</span></span>](../../../../docs/framework/wcf/feature-details/how-to-expose-a-feed-as-both-atom-and-rss.md)
