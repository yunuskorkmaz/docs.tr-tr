---
title: Dağıtım Mimarisi
ms.date: 03/30/2017
ms.assetid: ed4ca86e-e3d8-4acb-87aa-1921fbc353be
ms.openlocfilehash: 4083f7f7ef3fc986e9a7c430b8ed8cfe451c9d86
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61596368"
---
# <a name="architecture-of-syndication"></a>Dağıtım Mimarisi
Dağıtım API dağıtılmış içeriği, çeşitli biçimlerde hat açın yazılmasına izin veren bir biçim nötr programlama modeli sağlamak için tasarlanmıştır. Aşağıdaki sınıflar soyut bir veri modeli oluşur:  
  
- <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
- <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
- <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
- <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
- <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 Bazı adları farklı olmasına rağmen bu sınıfların Atom 1.0 belirtiminde tanımlanan yapıları yakından eşlenir.  
  
 Windows Communication Foundation (WCF), dağıtım akışlarını başka türde bir hizmet işlemi, bir dönüş türü olduğu türetilmiş sınıfları biri modellenir <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>. Bir akış alma, bir istek-yanıt iletisi exchange modellenir. Bir istemci bir hizmet ve hizmet isteğine yanıt gönderir. İstek iletisi altyapı Protokolü (örneğin, ham HTTP) üzerinden ayarlanır ve anlaşılır dağıtım biçiminin (RSS 2.0 veya Atom 1.0) oluşan bir yükü yanıt iletisini içerir. Bu ileti alışverişlerinde uygulama Hizmetleri Dağıtım Hizmetleri olarak adlandırılır.  
  
 Bir dağıtım hizmeti sözleşmesi örneğini döndüren işlemlerinin kümesinden oluşur <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> sınıfı. Aşağıdaki örnek bir dağıtım hizmeti için bir arabirim bildirimi gösterir.  
  
 [!code-csharp[S_UE_SyndicationBoth#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_syndicationboth/cs/service.cs#0)]  
  
 Dağıtım desteği, WCF REST programlama tanımlayan bir Model temelinde oluşturulmuştur <xref:System.ServiceModel.WebHttpBinding> ile birlikte kullanılan bağlama <xref:System.ServiceModel.Description.WebHttpBehavior> akışları Hizmetleri olarak kullanılabilir hale getirmek için. WCF REST programlama modeli hakkında daha fazla bilgi için bkz: [WCF Web HTTP programlama modeli genel bakış](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md).  
  
> [!NOTE]
>  Atom 1.0 belirtimi Kesirli saniye, tarih yapıları hiçbirinde belirtilmesine izin verir. WCF uygulaması, serileştirmek ve seri durumdan çıkarılırken zaman Kesirli saniye yok sayar.  
  
## <a name="object-model"></a>Nesne modeli  
 Dağıtım için nesne modeli sınıfları aşağıdaki tablolarda gruplarını oluşur.  
  
 Biçimlendirme sınıflar:  
  
|örneği|Açıklama|  
|-----------|-----------------|  
|<xref:System.ServiceModel.Syndication.Atom10FeedFormatter>|Serileştiren bir sınıf bir <xref:System.ServiceModel.Syndication.SyndicationFeed> Atom 1.0 biçim örneği.|  
|<xref:System.ServiceModel.Syndication.Atom10FeedFormatter%601>|Serileştiren bir sınıf <xref:System.ServiceModel.Syndication.SyndicationFeed> Atom 1.0 biçimine türetilmiş sınıflar.|  
|<xref:System.ServiceModel.Syndication.Atom10ItemFormatter>|Serileştiren bir sınıf bir <xref:System.ServiceModel.Syndication.SyndicationItem> Atom 1.0 biçim örneği.|  
|<xref:System.ServiceModel.Syndication.Atom10ItemFormatter%601>|Serileştiren bir sınıf <xref:System.ServiceModel.Syndication.SyndicationItem> Atom 1.0 biçimine türetilmiş sınıflar.|  
|<xref:System.ServiceModel.Syndication.Rss20FeedFormatter>|Serileştiren bir sınıf bir <xref:System.ServiceModel.Syndication.SyndicationFeed> RSS 2.0 biçim örneği.|  
|<xref:System.ServiceModel.Syndication.Rss20FeedFormatter%601>|Serileştiren bir sınıf <xref:System.ServiceModel.Syndication.SyndicationFeed> RSS 2.0 biçimine türetilmiş sınıflar.|  
|<xref:System.ServiceModel.Syndication.Rss20ItemFormatter>|Serileştiren bir sınıf bir <xref:System.ServiceModel.Syndication.SyndicationItem> RSS 2.0 biçim örneği.|  
|<xref:System.ServiceModel.Syndication.Rss20ItemFormatter%601>|Serileştiren bir sınıf <xref:System.ServiceModel.Syndication.SyndicationItem> RSS 2.0 biçimine türetilmiş sınıflar.|  
  
 Nesne modeli sınıfları:  
  
|örneği|Açıklama|  
|-----------|-----------------|  
|<xref:System.ServiceModel.Syndication.SyndicationCategory>|Bir dağıtım akışı kategorisini temsil eden sınıf.|  
|<xref:System.ServiceModel.Syndication.SyndicationContent>|Dağıtım içeriğini temsil eder bir temel sınıf.|  
|<xref:System.ServiceModel.Syndication.SyndicationElementExtension>|Bir dağıtım öğesi uzantısı temsil eden sınıf.|  
|<xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection>|Bir koleksiyonu <xref:System.ServiceModel.Syndication.SyndicationElementExtension> nesneleri.|  
|<xref:System.ServiceModel.Syndication.SyndicationFeed>|Bir üst düzey akış nesnesini temsil eden sınıf.|  
|<xref:System.ServiceModel.Syndication.SyndicationItem>|Akış öğesi temsil eden sınıf.|  
|<xref:System.ServiceModel.Syndication.SyndicationLink>|Bir dağıtım akışı veya öğesi bir bağlantıyı temsil eden sınıf.|  
|<xref:System.ServiceModel.Syndication.SyndicationPerson>|Bir kişinin Atom yapısını temsil eden sınıf.|  
|<xref:System.ServiceModel.Syndication.SyndicationVersions>|Desteklenen dağıtım protokol sürümleri temsil eden sınıf.|  
|<xref:System.ServiceModel.Syndication.TextSyndicationContent>|Tüm temsil eden bir sınıf <xref:System.ServiceModel.Syndication.SyndicationItem> içeriği son kullanıcıya görüntülenecek.|  
|<xref:System.ServiceModel.Syndication.TextSyndicationContentKind>|Farklı içerik desteklenen metin dağıtım türleri temsil eden bir sabit listesi.|  
|<xref:System.ServiceModel.Syndication.UrlSyndicationContent>|Başka bir kaynak URL'sini içeren dağıtım içeriğini temsil eden sınıf.|  
|<xref:System.ServiceModel.Syndication.XmlSyndicationContent>|Bir tarayıcıda gösterilmeyecek için dağıtım içeriğini temsil eden sınıf.|  
  
 Çekirdek veri nesne modelinde akışı ve karşılık gelen öğe özetlerdir <xref:System.ServiceModel.Syndication.SyndicationFeed> ve <xref:System.ServiceModel.Syndication.SyndicationItem> sınıfları. Bir akış, bir bilinmeyen uzantılarını depolamak için konum ve akışın bilgi içeriği kalan öğelerin kümesi (örneğin, başlık, açıklama ve yazar), bazı akış düzeyinde meta verileri kullanıma sunar. Bir öğenin bazı öğe düzeyinde meta veri (örneğin, başlık, Özet ve PublicationDate), bir bilinmeyen uzantılarını depolamak için konum ve içerik kullanılabilmesini öğenin bilgi içeriği geri kalanı içeren öğe. Akış öğesi ve çekirdek soyutlama Atom 1.0 ve RSS belirtimlerinde başvurulan ortak veri yapılarını temsil eden ek sınıfları tarafından desteklenir.  
  
 Bir akışı örneğinde taşınan bilgiler çeşitli biçimlerde XML için dönüştürülebilir. XML'den ve dönüştürme işlemi tarafından yönetilen <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> sınıfı. Bu sınıf soyuttur; somut uygulamaları, Atom 1.0 ve RSS 2.0 için sağlanan <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> ve <xref:System.ServiceModel.Syndication.Rss20FeedFormatter>. Türetilmiş akışı sınıflarını kullanmak için kullanın <xref:System.ServiceModel.Syndication.Atom10FeedFormatter%601> veya <xref:System.ServiceModel.Syndication.Rss20FeedFormatter%601> akışı türetilen belirtmek izin. Türetilen öğesi sınıfları ya da kullanmayı <xref:System.ServiceModel.Syndication.Atom10ItemFormatter%601> veya <xref:System.ServiceModel.Syndication.Rss20ItemFormatter%601> belirlemenize olanak tanır şekilde türetilen öğesi sınıfı üçüncü tarafların kendi türetebilirsiniz <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> farklı dağıtım biçimlerini desteklemek için.  
  
## <a name="extensibility"></a>Genişletilebilirlik  
  
- Bir anahtar dağıtım protokolleri genişletilebilirlik özelliğidir. Hem Atom 1.0 hem de RSS 2.0 öznitelikler ve öğeler'de tanımlanmayan, dağıtım akışlarını eklemenize olanak tanır. Özel öznitelikler ve Uzantılar ile çalışmaya ilişkin iki yöntem WCF dağıtım programlama modeli sağlar: yeni bir sınıf ve geniş yazılmış erişim türetme. Daha fazla bilgi için [dağıtım genişletilebilirliği](../../../../docs/framework/wcf/feature-details/syndication-extensibility.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Dağıtımı Genel Bakış](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md)
- [WCF Dağıtım Nesnesi Modeli Atom ve RSS Eşlemelerini Nasıl Yapar?](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md)
- [WCF Web HTTP Programlama Modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
