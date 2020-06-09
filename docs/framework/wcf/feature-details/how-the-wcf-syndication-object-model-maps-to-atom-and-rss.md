---
title: WCF Dağıtım Nesnesi Modeli Atom ve RSS Eşlemelerini Nasıl Yapar?
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0365eb37-98cc-4b13-80fb-f1e78847a748
ms.openlocfilehash: 67fbbb035a3a6683cefbf24e299f32579b674bbd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597260"
---
# <a name="how-the-wcf-syndication-object-model-maps-to-atom-and-rss"></a>WCF Dağıtım Nesnesi Modeli Atom ve RSS Eşlemelerini Nasıl Yapar?
Windows Communication Foundation (WCF) bir dağıtım hizmeti geliştirirken, aşağıdaki sınıfları kullanarak akışlar ve öğeler oluşturursunuz:  
  
- <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
- <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
- <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
- <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
- <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
- <xref:System.ServiceModel.Syndication.TextSyndicationContent>  
  
- <xref:System.ServiceModel.Syndication.UrlSyndicationContent>  
  
- <xref:System.ServiceModel.Syndication.XmlSyndicationContent>  
  
 Bir <xref:System.ServiceModel.Syndication.SyndicationFeed> biçimlendirici tarafından tanımlanan herhangi bir dağıtım formatında seri hale getirilebilir. WCF iki biçim ile birlikte gelir: <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> ve <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> .  
  
 Ve etrafında nesne modeli <xref:System.ServiceModel.Syndication.SyndicationFeed> , <xref:System.ServiceModel.Syndication.SyndicationItem> Atom 1,0 belirtimine 2,0 göre daha yakından hizalanır. Bunun nedeni, Atom 1,0 'nin RSS 2,0 belirtiminde belirsiz veya atlanmış öğeleri tanımlayan daha önemli bir belirtimdir. Bu nedenle, WCF dağıtım nesne modelindeki birçok öğenin RSS 2,0 belirtiminde doğrudan temsili yoktur. <xref:System.ServiceModel.Syndication.SyndicationFeed> <xref:System.ServiceModel.Syndication.SyndicationItem> , RSS 2,0 ' de nesneler serileştirilirken ve Atom belirtimine uygun olan ad alanı nitelikli uzantı öğeleri olarak atom 'a özgü veri öğelerini Serileştirmeye olanak tanır. Bunu, oluşturucuya geçirilen bir parametre ile kontrol edebilirsiniz <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> .  
  
 Bu konudaki kod örnekleri, gerçek serileştirme yapmak için burada tanımlanan iki yöntemden birini kullanır.  
  
 `SerializeFeed`bir dağıtım akışını seri hale getirir.  
  
 [!code-csharp[SyndicationMapping#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#10)]
 [!code-vb[SyndicationMapping#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#10)]  
  
 `SerializeItem`bir dağıtım öğesini seri hale getirir.  
  
 [!code-csharp[SyndicationMapping#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#11)]
 [!code-vb[SyndicationMapping#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#11)]  
  
## <a name="syndicationfeed"></a>SyndicationFeed  
 Aşağıdaki kod örneği, <xref:System.ServiceModel.Syndication.SyndicationFeed> sınıfının Atom 1,0 ve RSS 2,0 olarak serileştirilme şeklini gösterir.  
  
 [!code-csharp[SyndicationMapping#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#0)]
 [!code-vb[SyndicationMapping#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#0)]  
  
 Aşağıdaki XML, ' <xref:System.ServiceModel.Syndication.SyndicationFeed> nin Atom 1,0 ' de nasıl serileştirildiği gösterilmektedir.  
  
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
  
 Aşağıdaki XML, ' <xref:System.ServiceModel.Syndication.SyndicationFeed> nın RSS 2,0 ' e nasıl serileştirildiği gösterir.  
  
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
 Aşağıdaki kod örneği, <xref:System.ServiceModel.Syndication.SyndicationItem> sınıfının Atom 1,0 ve RSS 2,0 olarak serileştirilme şeklini gösterir.  
  
 [!code-csharp[SyndicationMapping#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#1)]
 [!code-vb[SyndicationMapping#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#1)]  
  
 Aşağıdaki XML, ' <xref:System.ServiceModel.Syndication.SyndicationItem> nin Atom 1,0 ' de nasıl serileştirildiği gösterilmektedir.  
  
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
  
 Aşağıdaki XML, ' <xref:System.ServiceModel.Syndication.SyndicationItem> nın RSS 2,0 ' e nasıl serileştirildiği gösterir.  
  
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
 Aşağıdaki kod örneği, <xref:System.ServiceModel.Syndication.SyndicationPerson> sınıfının Atom 1,0 ve RSS 2,0 olarak serileştirilme şeklini gösterir.  
  
 [!code-csharp[SyndicationMapping#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#2)]
 [!code-vb[SyndicationMapping#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#2)]  
  
 Aşağıdaki XML, ' <xref:System.ServiceModel.Syndication.SyndicationPerson> nin Atom 1,0 ' de nasıl serileştirildiği gösterilmektedir.  
  
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
  
 Aşağıdaki XML, <xref:System.ServiceModel.Syndication.SyndicationPerson> veya koleksiyonlarında yalnızca bir tane varsa, SıNıFıNıN RSS 2,0 'e nasıl serileştirildiği gösterilmektedir <xref:System.ServiceModel.Syndication.SyndicationPerson> `Authors` `Contributors` .  
  
```xml  
<author>Jesper.Aaberg@contoso.com</author>  
<a10:contributor>  
    <a10:name>Lene Aaling</a10:name>  
    <a10:uri>http://Contoso/Aaling</a10:uri>  
    <a10:email>Lene.Aaling@contoso.com</a10:email>  
</a10:contributor>  
```  
  
 Aşağıdaki XML, <xref:System.ServiceModel.Syndication.SyndicationPerson> ya da koleksiyonlarında birden fazla varsa, SıNıFıNıN RSS 2,0 'e nasıl serileştirildiği gösterilmektedir <xref:System.ServiceModel.Syndication.SyndicationPerson> `Authors` `Contributors` .  
  
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
 Aşağıdaki kod örneği, <xref:System.ServiceModel.Syndication.SyndicationLink> sınıfının Atom 1,0 ve RSS 2,0 olarak serileştirilme şeklini gösterir.  
  
 [!code-csharp[SyndicationMapping#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#3)]
 [!code-vb[SyndicationMapping#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#3)]  
  
 Aşağıdaki XML, ' <xref:System.ServiceModel.Syndication.SyndicationLink> nin Atom 1,0 ' de nasıl serileştirildiği gösterilmektedir.  
  
 `<link rel="alternate" type="text/html" title="My Link Title" length="2048" href="http://contoso/MyLink" />`  
  
 Aşağıdaki XML, ' <xref:System.ServiceModel.Syndication.SyndicationLink> nın RSS 2,0 ' e nasıl serileştirildiği gösterir.  
  
 `<a10:link rel="alternate" type="text/html" title="My Link Title" length="2048" href="http://contoso/MyLink" />`  
  
## <a name="syndicationcategory"></a>SyndicationCategory  
 Aşağıdaki kod örneği, <xref:System.ServiceModel.Syndication.SyndicationCategory> sınıfının Atom 1,0 ve RSS 2,0 olarak serileştirilme şeklini gösterir.  
  
 [!code-csharp[SyndicationMapping#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#4)]
 [!code-vb[SyndicationMapping#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#4)]  
  
 Aşağıdaki XML, ' <xref:System.ServiceModel.Syndication.SyndicationCategory> nin Atom 1,0 ' de nasıl serileştirildiği gösterilmektedir.  
  
 `<category term="categoryName" label="categoryLabel" scheme="categoryScheme" />`  
  
 Aşağıdaki XML, ' <xref:System.ServiceModel.Syndication.SyndicationCategory> nın RSS 2,0 ' e nasıl serileştirildiği gösterir.  
  
 `<category domain="categoryScheme">categoryName</category>`  
  
## <a name="textsyndicationcontent"></a>TextSyndicationContent  
 Aşağıdaki kod örneği, <xref:System.ServiceModel.Syndication.TextSyndicationContent> HTML içeriğiyle oluşturulduğunda sınıfının Atom 1,0 ve RSS 2,0 olarak serileştirilme şeklini gösterir <xref:System.ServiceModel.Syndication.TextSyndicationContent> .  
  
 [!code-csharp[SyndicationMapping#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#5)]
 [!code-vb[SyndicationMapping#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#5)]  
  
 Aşağıdaki XML, <xref:System.ServiceModel.Syndication.TextSyndicationContent> HTML içeriğine sahip sınıfın Atom 1,0 ' de nasıl serileştirildiği gösterilmektedir.  
  
 `<content type="html"><html> some html </html></content>`  
  
 Aşağıdaki XML, <xref:System.ServiceModel.Syndication.TextSyndicationContent> sınıfının nasıl RSS 2,0 ' e serileştirildiği gösterilmektedir.  
  
 `<description><html> some html </html></description>`  
  
 Aşağıdaki kod örneği, <xref:System.ServiceModel.Syndication.TextSyndicationContent> düz metin içeriğiyle oluşturulduğunda sınıfının Atom 1,0 ve RSS 2,0 ' ye nasıl serileştirilmek <xref:System.ServiceModel.Syndication.TextSyndicationContent> olduğunu gösterir.  
  
 [!code-csharp[SyndicationMapping#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#6)]
 [!code-vb[SyndicationMapping#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#6)]  
  
 Aşağıdaki XML, <xref:System.ServiceModel.Syndication.TextSyndicationContent> düz metin içeriğine sahip sınıfın Atom 1,0 ' de nasıl serileştirildiği gösterilmektedir.  
  
 `<content type="text">Some Plain Text</content>`  
  
 Aşağıdaki XML, <xref:System.ServiceModel.Syndication.TextSyndicationContent> düz metin içeriğine sahip sınıfın nasıl bır RSS 2,0 serileştirildiği gösterir.  
  
 `<description>Some Plain Text</description>`  
  
 Aşağıdaki kod örneği, <xref:System.ServiceModel.Syndication.TextSyndicationContent> <xref:System.ServiceModel.Syndication.TextSyndicationContent> XHTML içerik ile oluşturulduğunda sınıfının Atom 1,0 ve RSS 2,0 olarak serileştirilme şeklini gösterir.  
  
 [!code-csharp[SyndicationMapping#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#7)]
 [!code-vb[SyndicationMapping#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#7)]  
  
 Aşağıdaki XML, <xref:System.ServiceModel.Syndication.TextSyndicationContent> XHTML içeriğine sahip sınıfın Atom 1,0 ' de nasıl serileştirildiği gösterir.  
  
 `<content type="xhtml">`  
  
 `<html> some xhtml </html>`  
  
 `</content>`  
  
 Aşağıdaki XML, <xref:System.ServiceModel.Syndication.TextSyndicationContent> XHTML içeriğine sahip sınıfın nasıl 2,0 RSS 'e serileştirildiği gösterilmektedir.  
  
 `<description><html> some xhtml </html></description>`  
  
## <a name="urlsyndicationcontent"></a>UrlSyndicationContent  
 Aşağıdaki kod örneği, <xref:System.ServiceModel.Syndication.UrlSyndicationContent> sınıfının Atom 1,0 ve RSS 2,0 olarak serileştirilme şeklini gösterir.  
  
 [!code-csharp[SyndicationMapping#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#8)]
 [!code-vb[SyndicationMapping#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#8)]  
  
 Aşağıdaki XML, <xref:System.ServiceModel.Syndication.UrlSyndicationContent> sınıfının Atom 1,0 ' de nasıl serileştirildiği gösterilmektedir.  
  
 `<content type="audio" src="http://someurl/" />`  
  
 Aşağıdaki XML, <xref:System.ServiceModel.Syndication.UrlSyndicationContent> XHTML içeriğine sahip sınıfın nasıl 2,0 RSS 'e serileştirildiği gösterilmektedir.  
  
 `<description />`  
  
 `<content type="audio" src="http://Contoso/someurl/" xmlns="http://www.w3.org/2005/Atom" />`  
  
## <a name="xmlsyndicationcontent"></a>XmlSyndicationContent  
 Aşağıdaki kod örneği, <xref:System.ServiceModel.Syndication.XmlSyndicationContent> sınıfının Atom 1,0 ve RSS 2,0 olarak serileştirilme şeklini gösterir.  
  
 [!code-csharp[SyndicationMapping#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#9)]
 [!code-vb[SyndicationMapping#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#9)]  
  
 Aşağıdaki XML, <xref:System.ServiceModel.Syndication.XmlSyndicationContent> sınıfının Atom 1,0 ' de nasıl serileştirildiği gösterilmektedir.  
  
 `<content type="mytype">`  
  
 `<SomeData xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/FeedMapping" />`  
  
 `</content>`  
  
 Aşağıdaki XML, <xref:System.ServiceModel.Syndication.XmlSyndicationContent> XHTML içeriğine sahip sınıfın nasıl 2,0 RSS 'e serileştirildiği gösterilmektedir.  
  
 `<content type="mytype" xmlns="http://www.w3.org/2005/Atom">`  
  
 `<SomeData xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/FeedMapping" />`  
  
 `</content>`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Dağıtımı Genel Bakış](wcf-syndication-overview.md)
- [Dağıtım Mimarisi](architecture-of-syndication.md)
- [Nasıl Yapılır: Temel Bir RSS Akışı Oluşturma](how-to-create-a-basic-rss-feed.md)
- [Nasıl Yapılır: Temel Bir Atom Akışı Oluşturma](how-to-create-a-basic-atom-feed.md)
- [Nasıl yapılır: Bir Akışı Hem Atom Hem de RSS Olarak Kullanıma Sunma](how-to-expose-a-feed-as-both-atom-and-rss.md)
