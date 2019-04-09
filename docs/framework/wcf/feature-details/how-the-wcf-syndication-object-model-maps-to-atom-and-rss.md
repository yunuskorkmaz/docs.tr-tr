---
title: WCF Dağıtım Nesnesi Modeli Atom ve RSS Eşlemelerini Nasıl Yapar?
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0365eb37-98cc-4b13-80fb-f1e78847a748
ms.openlocfilehash: b5a7f68edc49a02bb99ca05765d4582b798e72ef
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127393"
---
# <a name="how-the-wcf-syndication-object-model-maps-to-atom-and-rss"></a>WCF Dağıtım Nesnesi Modeli Atom ve RSS Eşlemelerini Nasıl Yapar?
Bir Windows Communication Foundation (WCF) dağıtım hizmeti geliştirirken, akışları ve aşağıdaki sınıfları kullanarak öğeleri oluşturun:  
  
-   <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
-   <xref:System.ServiceModel.Syndication.TextSyndicationContent>  
  
-   <xref:System.ServiceModel.Syndication.UrlSyndicationContent>  
  
-   <xref:System.ServiceModel.Syndication.XmlSyndicationContent>  
  
 A <xref:System.ServiceModel.Syndication.SyndicationFeed> bir biçimlendirici tanımlanır dağıtım biçime seri hale getirilebilir. WCF iki biçimlendiricileri ile birlikte gelir: <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> ve <xref:System.ServiceModel.Syndication.Rss20FeedFormatter>.  
  
 Geçici nesne modeli <xref:System.ServiceModel.Syndication.SyndicationFeed> ve <xref:System.ServiceModel.Syndication.SyndicationItem> daha yakından RSS 2.0 belirtimini Atom 1.0 belirtimi ile hizalanır. Atom 1.0 belirsiz veya atlanamaz RSS 2.0 belirtiminden öğeleri tanımlayan daha önemli bir özelliğidir olmasıdır. Bu nedenle, WCF dağıtım nesnesi modeli birçok öğeler RSS 2.0 belirtimini hiçbir doğrudan gösterimini içerir. Serileştirilirken <xref:System.ServiceModel.Syndication.SyndicationFeed> ve <xref:System.ServiceModel.Syndication.SyndicationItem> nesneleri RSS 2.0 WCF Atom belirtime uygun ad alanıyla nitelenen uzantı öğesi olarak Atom'a özgü veri öğelerini serileştirmek izin verir. Geçirilen bir parametre ile bu denetleyebilirsiniz <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> Oluşturucusu.  
  
 Bu konuda kullanılan iki yöntemden biri kod örnekleri, burada gerçek serileştirme yapmak için tanımlanan.  
  
 `SerializeFeed` bir dağıtım akışı serileştirir.  
  
 [!code-csharp[SyndicationMapping#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#10)]
 [!code-vb[SyndicationMapping#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#10)]  
  
 `SerializeItem` bir dağıtım öğesi serileştirir.  
  
 [!code-csharp[SyndicationMapping#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#11)]
 [!code-vb[SyndicationMapping#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#11)]  
  
## <a name="syndicationfeed"></a>SyndicationFeed  
 Aşağıdaki kod örneği, seri hale getirmek gösterilmektedir <xref:System.ServiceModel.Syndication.SyndicationFeed> Atom 1.0 ve RSS 2.0 sınıfı.  
  
 [!code-csharp[SyndicationMapping#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#0)]
 [!code-vb[SyndicationMapping#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#0)]  
  
 Aşağıdaki XML gösterildiği nasıl <xref:System.ServiceModel.Syndication.SyndicationFeed> Atom 1.0 için serileştirilir.  
  
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
  
 Aşağıdaki XML gösterildiği nasıl <xref:System.ServiceModel.Syndication.SyndicationFeed> RSS 2.0 için serileştirilir.  
  
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
  
## <a name="syndicationitem"></a>SyndicationItem  
 Aşağıdaki kod örneği, seri hale getirmek gösterilmektedir <xref:System.ServiceModel.Syndication.SyndicationItem> Atom 1.0 ve RSS 2.0 sınıfı.  
  
 [!code-csharp[SyndicationMapping#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#1)]
 [!code-vb[SyndicationMapping#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#1)]  
  
 Aşağıdaki XML gösterildiği nasıl <xref:System.ServiceModel.Syndication.SyndicationItem> Atom 1.0 için serileştirilir.  
  
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
  
 Aşağıdaki XML gösterildiği nasıl <xref:System.ServiceModel.Syndication.SyndicationItem> RSS 2.0 için serileştirilir.  
  
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
  
## <a name="syndicationperson"></a>SyndicationPerson  
 Aşağıdaki kod örneği, seri hale getirmek gösterilmektedir <xref:System.ServiceModel.Syndication.SyndicationPerson> Atom 1.0 ve RSS 2.0 sınıfı.  
  
 [!code-csharp[SyndicationMapping#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#2)]
 [!code-vb[SyndicationMapping#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#2)]  
  
 Aşağıdaki XML gösterildiği nasıl <xref:System.ServiceModel.Syndication.SyndicationPerson> Atom 1.0 için serileştirilir.  
  
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
  
 Aşağıdaki XML gösterildiği nasıl <xref:System.ServiceModel.Syndication.SyndicationPerson> yalnızca bir sınıf için RSS 2.0 serileştirildiği <xref:System.ServiceModel.Syndication.SyndicationPerson> var. `Authors` veya `Contributors` koleksiyonları, sırasıyla.  
  
```xml  
<author>Jesper.Aaberg@contoso.com</author>  
<a10:contributor>  
    <a10:name>Lene Aaling</a10:name>  
    <a10:uri>http://Contoso/Aaling</a10:uri>  
    <a10:email>Lene.Aaling@contoso.com</a10:email>  
</a10:contributor>  
```  
  
 Aşağıdaki XML gösterildiği nasıl <xref:System.ServiceModel.Syndication.SyndicationPerson> sınıf, RSS 2.0 serileştirildiği, birden fazla ise <xref:System.ServiceModel.Syndication.SyndicationPerson> var. `Authors` veya `Contributors` koleksiyonları, sırasıyla.  
  
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
  
## <a name="syndicationlink"></a>SyndicationLink  
 Aşağıdaki kod örneği, seri hale getirmek gösterilmektedir <xref:System.ServiceModel.Syndication.SyndicationLink> Atom 1.0 ve RSS 2.0 sınıfı.  
  
 [!code-csharp[SyndicationMapping#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#3)]
 [!code-vb[SyndicationMapping#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#3)]  
  
 Aşağıdaki XML gösterildiği nasıl <xref:System.ServiceModel.Syndication.SyndicationLink> Atom 1.0 için serileştirilir.  
  
 `<link rel="alternate" type="text/html" title="My Link Title" length="2048" href="http://contoso/MyLink" />`  
  
 Aşağıdaki XML gösterildiği nasıl <xref:System.ServiceModel.Syndication.SyndicationLink> RSS 2.0 için serileştirilir.  
  
 `<a10:link rel="alternate" type="text/html" title="My Link Title" length="2048" href="http://contoso/MyLink" />`  
  
## <a name="syndicationcategory"></a>SyndicationCategory  
 Aşağıdaki kod örneği, seri hale getirmek gösterilmektedir <xref:System.ServiceModel.Syndication.SyndicationCategory> Atom 1.0 ve RSS 2.0 sınıfı.  
  
 [!code-csharp[SyndicationMapping#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#4)]
 [!code-vb[SyndicationMapping#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#4)]  
  
 Aşağıdaki XML gösterildiği nasıl <xref:System.ServiceModel.Syndication.SyndicationCategory> Atom 1.0 için serileştirilir.  
  
 `<category term="categoryName" label="categoryLabel" scheme="categoryScheme" />`  
  
 Aşağıdaki XML gösterildiği nasıl <xref:System.ServiceModel.Syndication.SyndicationCategory> RSS 2.0 için serileştirilir.  
  
 `<category domain="categoryScheme">categoryName</category>`  
  
## <a name="textsyndicationcontent"></a>TextSyndicationContent  
 Aşağıdaki kod örneği, seri hale getirmek gösterilmektedir <xref:System.ServiceModel.Syndication.TextSyndicationContent> Atom 1.0 ve RSS 2.0 sınıfı zaman <xref:System.ServiceModel.Syndication.TextSyndicationContent> HTML içerikle oluşturulur.  
  
 [!code-csharp[SyndicationMapping#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#5)]
 [!code-vb[SyndicationMapping#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#5)]  
  
 Aşağıdaki XML gösterildiği nasıl <xref:System.ServiceModel.Syndication.TextSyndicationContent> Atom 1.0 için HTML içeriğe sahip bir sınıf seri hale.  
  
 `<content type="html"><html> some html </html></content>`  
  
 Aşağıdaki XML gösterildiği nasıl <xref:System.ServiceModel.Syndication.TextSyndicationContent> RSS 2.0 için HTML içeriğe sahip bir sınıf seri hale.  
  
 `<description><html> some html </html></description>`  
  
 Aşağıdaki kod örneği, seri hale getirmek gösterilmektedir <xref:System.ServiceModel.Syndication.TextSyndicationContent> Atom 1.0 ve RSS 2.0 sınıfı zaman <xref:System.ServiceModel.Syndication.TextSyndicationContent> düz metin içerikle oluşturulur.  
  
 [!code-csharp[SyndicationMapping#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#6)]
 [!code-vb[SyndicationMapping#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#6)]  
  
 Aşağıdaki XML gösterildiği nasıl <xref:System.ServiceModel.Syndication.TextSyndicationContent> Atom 1.0 için düz metin içerikli sınıfın serileştirilmiş.  
  
 `<content type="text">Some Plain Text</content>`  
  
 Aşağıdaki XML gösterildiği nasıl <xref:System.ServiceModel.Syndication.TextSyndicationContent> RSS 2.0 için düz metin içerikli sınıfın serileştirilmiş.  
  
 `<description>Some Plain Text</description>`  
  
 Aşağıdaki kod örneği, seri hale getirmek gösterilmektedir <xref:System.ServiceModel.Syndication.TextSyndicationContent> Atom 1.0 ve RSS 2.0 sınıfı zaman <xref:System.ServiceModel.Syndication.TextSyndicationContent> XHTML içerikle oluşturulur.  
  
 [!code-csharp[SyndicationMapping#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#7)]
 [!code-vb[SyndicationMapping#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#7)]  
  
 Aşağıdaki XML gösterildiği nasıl <xref:System.ServiceModel.Syndication.TextSyndicationContent> Atom 1.0 XHTML içerikle sınıfın serileştirilmiş.  
  
 `<content type="xhtml">`  
  
 `<html> some xhtml </html>`  
  
 `</content>`  
  
 Aşağıdaki XML gösterildiği nasıl <xref:System.ServiceModel.Syndication.TextSyndicationContent> RSS 2.0 XHTML içerikle sınıfın serileştirilmiş.  
  
 `<description><html> some xhtml </html></description>`  
  
## <a name="urlsyndicationcontent"></a>UrlSyndicationContent  
 Aşağıdaki kod örneği, seri hale getirmek gösterilmektedir <xref:System.ServiceModel.Syndication.UrlSyndicationContent> Atom 1.0 ve RSS 2.0 sınıfı.  
  
 [!code-csharp[SyndicationMapping#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#8)]
 [!code-vb[SyndicationMapping#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#8)]  
  
 Aşağıdaki XML gösterildiği nasıl <xref:System.ServiceModel.Syndication.UrlSyndicationContent> Atom 1.0 sınıfın serileştirilmiş.  
  
 `<content type="audio" src="http://someurl/" />`  
  
 Aşağıdaki XML gösterildiği nasıl <xref:System.ServiceModel.Syndication.UrlSyndicationContent> RSS 2.0 XHTML içerikle sınıfın serileştirilmiş.  
  
 `<description />`  
  
 `<content type="audio" src="http://Contoso/someurl/" xmlns="http://www.w3.org/2005/Atom" />`  
  
## <a name="xmlsyndicationcontent"></a>XmlSyndicationContent  
 Aşağıdaki kod örneği, seri hale getirmek gösterilmektedir <xref:System.ServiceModel.Syndication.XmlSyndicationContent> Atom 1.0 ve RSS 2.0 sınıfı.  
  
 [!code-csharp[SyndicationMapping#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#9)]
 [!code-vb[SyndicationMapping#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#9)]  
  
 Aşağıdaki XML gösterildiği nasıl <xref:System.ServiceModel.Syndication.XmlSyndicationContent> Atom 1.0 sınıfın serileştirilmiş.  
  
 `<content type="mytype">`  
  
 `<SomeData xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/FeedMapping" />`  
  
 `</content>`  
  
 Aşağıdaki XML gösterildiği nasıl <xref:System.ServiceModel.Syndication.XmlSyndicationContent> RSS 2.0 XHTML içerikle sınıfın serileştirilmiş.  
  
 `<content type="mytype" xmlns="http://www.w3.org/2005/Atom">`  
  
 `<SomeData xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/FeedMapping" />`  
  
 `</content>`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Dağıtımı Genel Bakış](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md)
- [Dağıtım Mimarisi](../../../../docs/framework/wcf/feature-details/architecture-of-syndication.md)
- [Nasıl yapılır: Temel Bir RSS Akışı Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-rss-feed.md)
- [Nasıl yapılır: Temel Bir Atom Akışı Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-atom-feed.md)
- [Nasıl yapılır: Bir Akışı Hem Atom Hem de RSS Olarak Kullanıma Sunma](../../../../docs/framework/wcf/feature-details/how-to-expose-a-feed-as-both-atom-and-rss.md)
