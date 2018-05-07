---
title: Dağıtım Mimarisi
ms.date: 03/30/2017
ms.assetid: ed4ca86e-e3d8-4acb-87aa-1921fbc353be
ms.openlocfilehash: f0a6b288860c343157f31f74d5a461fad1784e0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="architecture-of-syndication"></a>Dağıtım Mimarisi
Dağıtım API, çeşitli biçimlerde hat açın yazılacak dağıtılmış içerik sağlayan bir biçimi Tarafsız programlama modeli sağlamak için tasarlanmıştır. Soyut veri modeli şu sınıflardan oluşur:  
  
-   <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 Adlarından bazıları farklı olmasına rağmen bu sınıfların Atom 1.0 belirtiminde tanımlanan yapıları yakından eşlenir.  
  
 Başka türde bir hizmet işlemi, bir dönüş türü olduğu türetilmiş sınıfları biri Modellenen Windows Communication Foundation (WCF), dağıtım akışlarını <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>. Bir akış alınmasını istek-yanıt iletisi exchange modellenir. Bir istemci, hizmet ve hizmet isteğine yanıt gönderir. İstek iletisi bir altyapı Protokolü (örneğin, ham HTTP) üzerinden ayarlanır ve anlaşılır dağıtım biçimlerinin (RSS 2.0 veya Atom 1.0) oluşan bir yükü yanıt iletisi içerir. Bu ileti alışverişlerinde uygulama Hizmetleri Dağıtım Hizmetleri olarak adlandırılır.  
  
 Bir dağıtım hizmet sözleşmesi örneğini döndürür işlemlerinin bir dizi oluşur <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> sınıfı. Aşağıdaki örnek, bir dağıtım hizmeti için bir arabirim bildiriminde gösterir.  
  
 [!code-csharp[S_UE_SyndicationBoth#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_syndicationboth/cs/service.cs#0)]  
  
 Dağıtım desteği WCF REST programlama tanımlayan bir Model temelinde oluşturulmuştur <xref:System.ServiceModel.WebHttpBinding> ile birlikte kullanılan bağlama <xref:System.ServiceModel.Description.WebHttpBehavior> akışları Hizmetleri olarak kullanılabilir duruma getirilecek. WCF REST programlama modeli hakkında daha fazla bilgi için bkz: [WCF Web HTTP programlama modeline genel bakış](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md).  
  
> [!NOTE]
>  Atom 1.0 belirtimi tarih yapıları hiçbirinde belirtilmesini Kesirli saniye sağlar. Ne zaman seri hale getirme ve seri durumdan WCF uygulaması Kesirli saniye yoksayar.  
  
## <a name="object-model"></a>Nesne modeli  
 Aşağıdaki tablolarda sınıfların gruplarının dağıtım için nesne modeli oluşur.  
  
 Biçimlendirme sınıflar:  
  
|örneği|Açıklama|  
|-----------|-----------------|  
|<xref:System.ServiceModel.Syndication.Atom10FeedFormatter>|Serileştiren bir sınıf bir <xref:System.ServiceModel.Syndication.SyndicationFeed> Atom 1.0 biçim örneği.|  
|<xref:System.ServiceModel.Syndication.Atom10FeedFormatter%601>|Serileştiren bir sınıf <xref:System.ServiceModel.Syndication.SyndicationFeed> Atom 1.0 biçimine türetilmiş sınıfları.|  
|<xref:System.ServiceModel.Syndication.Atom10ItemFormatter>|Serileştiren bir sınıf bir <xref:System.ServiceModel.Syndication.SyndicationItem> Atom 1.0 biçim örneği.|  
|<xref:System.ServiceModel.Syndication.Atom10ItemFormatter%601>|Serileştiren bir sınıf <xref:System.ServiceModel.Syndication.SyndicationItem> Atom 1.0 biçimine türetilmiş sınıfları.|  
|<xref:System.ServiceModel.Syndication.Rss20FeedFormatter>|Serileştiren bir sınıf bir <xref:System.ServiceModel.Syndication.SyndicationFeed> RSS 2.0 biçiminde örneğine.|  
|<xref:System.ServiceModel.Syndication.Rss20FeedFormatter%601>|Serileştiren bir sınıf <xref:System.ServiceModel.Syndication.SyndicationFeed> RSS 2.0 biçimine türetilmiş sınıfları.|  
|<xref:System.ServiceModel.Syndication.Rss20ItemFormatter>|Serileştiren bir sınıf bir <xref:System.ServiceModel.Syndication.SyndicationItem> RSS 2.0 biçiminde örneğine.|  
|<xref:System.ServiceModel.Syndication.Rss20ItemFormatter%601>|Serileştiren bir sınıf <xref:System.ServiceModel.Syndication.SyndicationItem> RSS 2.0 biçimine türetilmiş sınıfları.|  
  
 Nesne modeli sınıfları:  
  
|örneği|Açıklama|  
|-----------|-----------------|  
|<xref:System.ServiceModel.Syndication.SyndicationCategory>|Bir dağıtım akışı kategorisini temsil eden sınıf.|  
|<xref:System.ServiceModel.Syndication.SyndicationContent>|Dağıtım içeriğini temsil eden bir temel sınıf.|  
|<xref:System.ServiceModel.Syndication.SyndicationElementExtension>|Bir dağıtım öğesi uzantısı temsil eden sınıf.|  
|<xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection>|Bir koleksiyonu <xref:System.ServiceModel.Syndication.SyndicationElementExtension> nesneleri.|  
|<xref:System.ServiceModel.Syndication.SyndicationFeed>|Üst düzey akış nesnesini temsil eden sınıf.|  
|<xref:System.ServiceModel.Syndication.SyndicationItem>|Akış bir öğeyi temsil eden sınıf.|  
|<xref:System.ServiceModel.Syndication.SyndicationLink>|Bir akış yayınlama veya öğesi bir bağlantıyı temsil eden sınıf.|  
|<xref:System.ServiceModel.Syndication.SyndicationPerson>|Atom kişi temsil eden bir sınıf oluşturun.|  
|<xref:System.ServiceModel.Syndication.SyndicationVersions>|Desteklenen dağıtım protokol sürümleri temsil eden sınıf.|  
|<xref:System.ServiceModel.Syndication.TextSyndicationContent>|Herhangi bir temsil eden bir sınıf <xref:System.ServiceModel.Syndication.SyndicationItem> son kullanıcıya görüntülenecek içerik.|  
|<xref:System.ServiceModel.Syndication.TextSyndicationContentKind>|Metin dağıtım içerik desteklenen farklı uygulama türleri temsil eden bir numaralandırması.|  
|<xref:System.ServiceModel.Syndication.UrlSyndicationContent>|Başka bir kaynak için bir URL oluşan dağıtım içeriği temsil eden sınıf.|  
|<xref:System.ServiceModel.Syndication.XmlSyndicationContent>|Bir tarayıcıda gösterilmeyecek olan dağıtım içerik temsil eden sınıf.|  
  
 Nesne modelinde çekirdek veri soyutlamalar akış ve karşılık gelen öğe olan <xref:System.ServiceModel.Syndication.SyndicationFeed> ve <xref:System.ServiceModel.Syndication.SyndicationItem> sınıfları. Bir akış bazı akış düzeyi meta veriler (örneğin, başlık, açıklama ve yazar), bir bilinmeyen uzantıları depolamak için konum ve akışın bilgi içerik rest yapmak öğeleri kümesi bir kullanıma sunar. Bir öğenin bazı öğe düzeyinde meta veriler (örneğin, başlık, özetini ve PublicationDate), bir bilinmeyen uzantıları depolamak için konum ve içeriği bir kullanılabilmesini öğenin bilgi içeriği kalan içeren öğe. Akış öğesi ve çekirdek soyutlamalar Atom 1.0 ve RSS belirtimleri başvurulan ortak veri yapıları temsil eden ek sınıflar tarafından desteklenir.  
  
 Bir akış örneği taşınan bilgiler çeşitli XML biçimlerinde dönüştürülebilir. XML gelen ve giden dönüştürme işlemi tarafından yönetilen <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> sınıfı. Bu sınıf soyuttur; somut uygulamaları Atom 1.0 ve RSS 2.0 için sağlanan <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> ve <xref:System.ServiceModel.Syndication.Rss20FeedFormatter>. Türetilen akış sınıflarını kullanmak için kullanın ya da <xref:System.ServiceModel.Syndication.Atom10FeedFormatter%601> veya <xref:System.ServiceModel.Syndication.Rss20FeedFormatter%601> gibi türetilmiş bir akış sınıf belirtmenizi sağlar. Türetilen öğesi sınıflar ya da kullanmayı <xref:System.ServiceModel.Syndication.Atom10ItemFormatter%601> veya <xref:System.ServiceModel.Syndication.Rss20ItemFormatter%601> belirlemenizi sağlayan gibi türetilen öğesi sınıfı üçüncü tarafların kendi uyarlamasını türetilemeyeceğini <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> farklı dağıtım biçimlerini desteklemek için.  
  
## <a name="extensibility"></a>Genişletilebilirlik  
  
-   Bir anahtar dağıtım protokolleri genişletilebilirlik özelliğidir. Atom 1.0 ve RSS 2.0 teknik özelliklerine tanımlanmamış dağıtım akışlarını için öznitelikler ve öğeler eklemenize izin verir. Özel öznitelikler ve uzantıları ile çalışmaya ilişkin iki yolla WCF dağıtım programlama modeli sağlar: yeni bir sınıf ve geniş yazılmış erişim türetme. Daha fazla bilgi için bkz: [dağıtım genişletilebilirliği](../../../../docs/framework/wcf/feature-details/syndication-extensibility.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Dağıtımı Genel Bakış](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md)  
 [WCF Dağıtım Nesnesi Modeli Atom ve RSS Eşlemelerini Nasıl Yapar?](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md)  
 [WCF Web HTTP Programlama Modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
