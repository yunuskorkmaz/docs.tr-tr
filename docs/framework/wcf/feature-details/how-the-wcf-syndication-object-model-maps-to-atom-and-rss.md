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
ms.openlocfilehash: 00c5b310fbda189cfffe74767c9d77ac86481afe
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-the-wcf-syndication-object-model-maps-to-atom-and-rss"></a>WCF Dağıtım Nesnesi Modeli Atom ve RSS Eşlemelerini Nasıl Yapar?
Geliştirirken bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] dağıtım hizmeti, oluşturduğunuz akışları ve aşağıdaki sınıflar kullanarak öğeleri:  
  
-   <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
-   <xref:System.ServiceModel.Syndication.TextSyndicationContent>  
  
-   <xref:System.ServiceModel.Syndication.UrlSyndicationContent>  
  
-   <xref:System.ServiceModel.Syndication.XmlSyndicationContent>  
  
 A <xref:System.ServiceModel.Syndication.SyndicationFeed> bir biçimlendirici tanımlanır tüm dağıtım biçiminde seri hale getirilebilir. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]iki biçimlendiricileri ile birlikte gelir: <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> ve <xref:System.ServiceModel.Syndication.Rss20FeedFormatter>.  
  
 Nesne modeli çevresinde <xref:System.ServiceModel.Syndication.SyndicationFeed> ve <xref:System.ServiceModel.Syndication.SyndicationItem> RSS 2.0 belirtimi daha Atom 1.0 belirtimiyle daha yakından hizalanır. Atom 1.0 belirsiz ya da RSS 2.0 belirtiminden belirtilmemişse öğeleri tanımlayan daha önemli bir belirtimi olmasıdır. Bu nedenle, birçok öğeleri [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dağıtım nesnesi modeli sahip hiçbir doğrudan gösterimi RSS 2.0 belirtimi. Serileştirilirken <xref:System.ServiceModel.Syndication.SyndicationFeed> ve <xref:System.ServiceModel.Syndication.SyndicationItem> RSS 2.0 nesnelerine [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Atom belirtimine uygun ad alanı tam genişletme öğeleri olarak Atom'a özgü veri öğeleri seri olanak tanır. Bunun için geçirilen parametre ile denetleyebilirsiniz <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> Oluşturucusu.  
  
 Bu konuda kullanılan iki yöntemden birini kod örnekleri, burada fiili serileştirme yapmak için tanımlanan.  
  
 `SerializeFeed`Akış bir dağıtım serileştirir.  
  
 [!code-csharp[SyndicationMapping#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#10)]
 [!code-vb[SyndicationMapping#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#10)]  
  
 `SerializeItem`bir dağıtım öğesi serileştirir.  
  
 [!code-csharp[SyndicationMapping#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#11)]
 [!code-vb[SyndicationMapping#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#11)]  
  
## <a name="syndicationfeed"></a>SyndicationFeed  
 Aşağıdaki kod örneğinde, seri hale getirmek gösterilmiştir <xref:System.ServiceModel.Syndication.SyndicationFeed> Atom 1.0 ve RSS 2.0 sınıfı.  
  
 [!code-csharp[SyndicationMapping#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#0)]
 [!code-vb[SyndicationMapping#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#0)]  
  
 Aşağıdaki XML gösterilmektedir nasıl <xref:System.ServiceModel.Syndication.SyndicationFeed> Atom 1.0 için serileştirilir.  
  
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
  
 Aşağıdaki XML gösterilmektedir nasıl <xref:System.ServiceModel.Syndication.SyndicationFeed> RSS 2.0 için serileştirilir.  
  
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
 Aşağıdaki kod örneğinde, seri hale getirmek gösterilmiştir <xref:System.ServiceModel.Syndication.SyndicationItem> Atom 1.0 ve RSS 2.0 sınıfı.  
  
 [!code-csharp[SyndicationMapping#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#1)]
 [!code-vb[SyndicationMapping#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#1)]  
  
 Aşağıdaki XML gösterilmektedir nasıl <xref:System.ServiceModel.Syndication.SyndicationItem> Atom 1.0 için serileştirilir.  
  
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
  
 Aşağıdaki XML gösterilmektedir nasıl <xref:System.ServiceModel.Syndication.SyndicationItem> RSS 2.0 için serileştirilir.  
  
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
 Aşağıdaki kod örneğinde, seri hale getirmek gösterilmiştir <xref:System.ServiceModel.Syndication.SyndicationPerson> Atom 1.0 ve RSS 2.0 sınıfı.  
  
 [!code-csharp[SyndicationMapping#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#2)]
 [!code-vb[SyndicationMapping#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#2)]  
  
 Aşağıdaki XML gösterilmektedir nasıl <xref:System.ServiceModel.Syndication.SyndicationPerson> Atom 1.0 için serileştirilir.  
  
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
  
 Aşağıdaki XML gösterilmektedir nasıl <xref:System.ServiceModel.Syndication.SyndicationPerson> sınıfı yalnızca bir RSS 2.0 serileştirilmiş <xref:System.ServiceModel.Syndication.SyndicationPerson> bulunmaktadır `Authors` veya `Contributors` koleksiyonlar, sırasıyla.  
  
```xml  
<author>Jesper.Aaberg@contoso.com</author>  
<a10:contributor>  
    <a10:name>Lene Aaling</a10:name>  
    <a10:uri>http://Contoso/Aaling</a10:uri>  
    <a10:email>Lene.Aaling@contoso.com</a10:email>  
</a10:contributor>  
```  
  
 Aşağıdaki XML gösterilmektedir nasıl <xref:System.ServiceModel.Syndication.SyndicationPerson> sınıfı birden fazla RSS 2.0 serileştirilmiş <xref:System.ServiceModel.Syndication.SyndicationPerson> bulunmaktadır `Authors` veya `Contributors` koleksiyonlar, sırasıyla.  
  
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
 Aşağıdaki kod örneğinde, seri hale getirmek gösterilmiştir <xref:System.ServiceModel.Syndication.SyndicationLink> Atom 1.0 ve RSS 2.0 sınıfı.  
  
 [!code-csharp[SyndicationMapping#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#3)]
 [!code-vb[SyndicationMapping#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#3)]  
  
 Aşağıdaki XML gösterilmektedir nasıl <xref:System.ServiceModel.Syndication.SyndicationLink> Atom 1.0 için serileştirilir.  
  
 `<link rel="alternate" type="text/html" title="My Link Title" length="2048" href="http://contoso/MyLink" />`  
  
 Aşağıdaki XML gösterilmektedir nasıl <xref:System.ServiceModel.Syndication.SyndicationLink> RSS 2.0 için serileştirilir.  
  
 `<a10:link rel="alternate" type="text/html" title="My Link Title" length="2048" href="http://contoso/MyLink" />`  
  
## <a name="syndicationcategory"></a>SyndicationCategory  
 Aşağıdaki kod örneğinde, seri hale getirmek gösterilmiştir <xref:System.ServiceModel.Syndication.SyndicationCategory> Atom 1.0 ve RSS 2.0 sınıfı.  
  
 [!code-csharp[SyndicationMapping#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#4)]
 [!code-vb[SyndicationMapping#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#4)]  
  
 Aşağıdaki XML gösterilmektedir nasıl <xref:System.ServiceModel.Syndication.SyndicationCategory> Atom 1.0 için serileştirilir.  
  
 `<category term="categoryName" label="categoryLabel" scheme="categoryScheme" />`  
  
 Aşağıdaki XML gösterilmektedir nasıl <xref:System.ServiceModel.Syndication.SyndicationCategory> RSS 2.0 için serileştirilir.  
  
 `<category domain="categoryScheme">categoryName</category>`  
  
## <a name="textsyndicationcontent"></a>TextSyndicationContent  
 Aşağıdaki kod örneğinde, seri hale getirmek gösterilmiştir <xref:System.ServiceModel.Syndication.TextSyndicationContent> Atom 1.0 ve RSS 2.0 sınıfına zaman <xref:System.ServiceModel.Syndication.TextSyndicationContent> HTML içeriği ile oluşturulur.  
  
 [!code-csharp[SyndicationMapping#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#5)]
 [!code-vb[SyndicationMapping#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#5)]  
  
 Aşağıdaki XML gösterilmektedir nasıl <xref:System.ServiceModel.Syndication.TextSyndicationContent> HTML içeriğini sınıfıyla Atom 1.0 serileştirilmiş.  
  
 `<content type="html"><html> some html </html></content>`  
  
 Aşağıdaki XML gösterilmektedir nasıl <xref:System.ServiceModel.Syndication.TextSyndicationContent> HTML içeriğini sınıfıyla RSS 2.0 serileştirilmiş.  
  
 `<description><html> some html </html></description>`  
  
 Aşağıdaki kod örneğinde, seri hale getirmek gösterilmiştir <xref:System.ServiceModel.Syndication.TextSyndicationContent> Atom 1.0 ve RSS 2.0 sınıfına zaman <xref:System.ServiceModel.Syndication.TextSyndicationContent> düz metin içeriği ile oluşturulur.  
  
 [!code-csharp[SyndicationMapping#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#6)]
 [!code-vb[SyndicationMapping#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#6)]  
  
 Aşağıdaki XML gösterilmektedir nasıl <xref:System.ServiceModel.Syndication.TextSyndicationContent> düz metin içeriği sınıfıyla Atom 1.0 için serileştirilir.  
  
 `<content type="text">Some Plain Text</content>`  
  
 Aşağıdaki XML gösterilmektedir nasıl <xref:System.ServiceModel.Syndication.TextSyndicationContent> düz metin içeriği sınıfıyla RSS 2.0 için serileştirilir.  
  
 `<description>Some Plain Text</description>`  
  
 Aşağıdaki kod örneğinde, seri hale getirmek gösterilmiştir <xref:System.ServiceModel.Syndication.TextSyndicationContent> Atom 1.0 ve RSS 2.0 sınıfına zaman <xref:System.ServiceModel.Syndication.TextSyndicationContent> XHTML içerikle oluşturulur.  
  
 [!code-csharp[SyndicationMapping#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#7)]
 [!code-vb[SyndicationMapping#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#7)]  
  
 Aşağıdaki XML gösterilmektedir nasıl <xref:System.ServiceModel.Syndication.TextSyndicationContent> XHTML içerikle sınıfı Atom 1.0 serileştirilmiş.  
  
 `<content type="xhtml">`  
  
 `<html> some xhtml </html>`  
  
 `</content>`  
  
 Aşağıdaki XML gösterilmektedir nasıl <xref:System.ServiceModel.Syndication.TextSyndicationContent> XHTML içerikle sınıfı RSS 2.0 serileştirilmiş.  
  
 `<description><html> some xhtml </html></description>`  
  
## <a name="urlsyndicationcontent"></a>UrlSyndicationContent  
 Aşağıdaki kod örneğinde, seri hale getirmek gösterilmiştir <xref:System.ServiceModel.Syndication.UrlSyndicationContent> Atom 1.0 ve RSS 2.0 sınıfı.  
  
 [!code-csharp[SyndicationMapping#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#8)]
 [!code-vb[SyndicationMapping#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#8)]  
  
 Aşağıdaki XML gösterilmektedir nasıl <xref:System.ServiceModel.Syndication.UrlSyndicationContent> sınıfı Atom 1.0 için serileştirilir.  
  
 `<content type="audio" src="http://someurl/" />`  
  
 Aşağıdaki XML gösterilmektedir nasıl <xref:System.ServiceModel.Syndication.UrlSyndicationContent> XHTML içerikle sınıfı RSS 2.0 serileştirilmiş.  
  
 `<description />`  
  
 `<content type="audio" src="http://Contoso/someurl/" xmlns="http://www.w3.org/2005/Atom" />`  
  
## <a name="xmlsyndicationcontent"></a>XmlSyndicationContent  
 Aşağıdaki kod örneğinde, seri hale getirmek gösterilmiştir <xref:System.ServiceModel.Syndication.XmlSyndicationContent> Atom 1.0 ve RSS 2.0 sınıfı.  
  
 [!code-csharp[SyndicationMapping#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#9)]
 [!code-vb[SyndicationMapping#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#9)]  
  
 Aşağıdaki XML gösterilmektedir nasıl <xref:System.ServiceModel.Syndication.XmlSyndicationContent> sınıfı Atom 1.0 için serileştirilir.  
  
 `<content type="mytype">`  
  
 `<SomeData xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/FeedMapping" />`  
  
 `</content>`  
  
 Aşağıdaki XML gösterilmektedir nasıl <xref:System.ServiceModel.Syndication.XmlSyndicationContent> XHTML içerikle sınıfı RSS 2.0 serileştirilmiş.  
  
 `<content type="mytype" xmlns="http://www.w3.org/2005/Atom">`  
  
 `<SomeData xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/FeedMapping" />`  
  
 `</content>`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF dağıtımı genel bakış](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md)  
 [Dağıtım mimarisi](../../../../docs/framework/wcf/feature-details/architecture-of-syndication.md)  
 [Nasıl yapılır: temel bir RSS akışı oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-rss-feed.md)  
 [Nasıl yapılır: temel bir Atom akışı oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-atom-feed.md)  
 [Nasıl yapılır: bir akışı hem Atom olarak kullanıma sunmak ve RSS](../../../../docs/framework/wcf/feature-details/how-to-expose-a-feed-as-both-atom-and-rss.md)
