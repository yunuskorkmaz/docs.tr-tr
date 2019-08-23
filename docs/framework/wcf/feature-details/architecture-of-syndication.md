---
title: Dağıtım Mimarisi
ms.date: 03/30/2017
ms.assetid: ed4ca86e-e3d8-4acb-87aa-1921fbc353be
ms.openlocfilehash: 5f93c7a11ed37e411fc584c8de16f141336c7f43
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952637"
---
# <a name="architecture-of-syndication"></a>Dağıtım Mimarisi
Dağıtım API 'SI, dağıtılmış içeriğin çok sayıda biçimde kabloda yazılmasına izin veren biçim nötr bir programlama modeli sağlamak üzere tasarlanmıştır. Soyut veri modeli aşağıdaki sınıflardan oluşur:  
  
- <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
- <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
- <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
- <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
- <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 Bu sınıflar, bazı adların farklı olmasına rağmen Atom 1,0 belirtiminde tanımlanan yapılara yakın şekilde eşlenir.  
  
 Windows Communication Foundation (WCF) ' de, dağıtım akışları başka bir hizmet işlemi türü olarak modellenir, biri dönüş türünün türetilmiş sınıflarından <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>biridir. Bir akışın alınması, istek-yanıt iletisi değişimi olarak modellenir. İstemci hizmete bir istek gönderir ve hizmet yanıt verir. İstek iletisi bir altyapı Protokolü (örneğin, ham HTTP) üzerinde ayarlanır ve yanıt iletisi, yaygın olarak anlaşılan bir dağıtım biçiminden (RSS 2,0 veya Atom 1,0) oluşan bir yük içerir. Bu ileti alışverişlerini uygulayan hizmetlere, Dağıtım Hizmetleri adı verilir.  
  
 Bir dağıtım hizmeti sözleşmesi, <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> sınıfının bir örneğini döndüren bir dizi işlemden oluşur. Aşağıdaki örnek, bir dağıtım hizmeti için bir arabirim bildirimi gösterir.  
  
 [!code-csharp[S_UE_SyndicationBoth#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_syndicationboth/cs/service.cs#0)]  
  
 Dağıtım desteği, akışı hizmet olarak kullanılabilir hale getirmek için ile <xref:System.ServiceModel.WebHttpBinding> <xref:System.ServiceModel.Description.WebHttpBehavior> birlikte kullanılan bağlamayı tanımlayan WCF REST programlama modelinin üzerine kurulmuştur. WCF REST programlama modeli hakkında daha fazla bilgi için bkz. [WCF Web http programlama modeline genel bakış](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md).  
  
> [!NOTE]
> Atom 1,0 belirtimi, bir tarih yapılarından birinde kesirli saniye belirtilmesine izin verir. WCF uygulamasının serileştirilmesi ve serisi kaldırılırken Kesirli saniyeler yok sayılır.  
  
## <a name="object-model"></a>Nesne modeli  
 Dağıtım için nesne modeli, aşağıdaki tablolardaki sınıf gruplarından oluşur.  
  
 Sınıfları biçimlendirme:  
  
|örneği|Açıklama|  
|-----------|-----------------|  
|<xref:System.ServiceModel.Syndication.Atom10FeedFormatter>|Bir <xref:System.ServiceModel.Syndication.SyndicationFeed> örneği Atom 1,0 biçimine serileştiren bir sınıf.|  
|<xref:System.ServiceModel.Syndication.Atom10FeedFormatter%601>|Türetilmiş sınıfları Atom 1,0 biçimine <xref:System.ServiceModel.Syndication.SyndicationFeed> serileştiren bir sınıf.|  
|<xref:System.ServiceModel.Syndication.Atom10ItemFormatter>|Bir <xref:System.ServiceModel.Syndication.SyndicationItem> örneği Atom 1,0 biçimine serileştiren bir sınıf.|  
|<xref:System.ServiceModel.Syndication.Atom10ItemFormatter%601>|Türetilmiş sınıfları Atom 1,0 biçimine <xref:System.ServiceModel.Syndication.SyndicationItem> serileştiren bir sınıf.|  
|<xref:System.ServiceModel.Syndication.Rss20FeedFormatter>|Bir <xref:System.ServiceModel.Syndication.SyndicationFeed> örneği RSS 2,0 biçimine serileştiren bir sınıf.|  
|<xref:System.ServiceModel.Syndication.Rss20FeedFormatter%601>|Türetilmiş sınıfları bir RSS 2,0 <xref:System.ServiceModel.Syndication.SyndicationFeed> biçimine serileştiren bir sınıf.|  
|<xref:System.ServiceModel.Syndication.Rss20ItemFormatter>|Bir <xref:System.ServiceModel.Syndication.SyndicationItem> örneği RSS 2,0 biçimine serileştiren bir sınıf.|  
|<xref:System.ServiceModel.Syndication.Rss20ItemFormatter%601>|Türetilmiş sınıfları bir RSS 2,0 <xref:System.ServiceModel.Syndication.SyndicationItem> biçimine serileştiren bir sınıf.|  
  
 Nesne modeli sınıfları:  
  
|örneği|Açıklama|  
|-----------|-----------------|  
|<xref:System.ServiceModel.Syndication.SyndicationCategory>|Bir dağıtım akışının kategorisini temsil eden bir sınıf.|  
|<xref:System.ServiceModel.Syndication.SyndicationContent>|Dağıtım içeriğini temsil eden bir temel sınıf.|  
|<xref:System.ServiceModel.Syndication.SyndicationElementExtension>|Bir dağıtım öğesi uzantısını temsil eden sınıf.|  
|<xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection>|<xref:System.ServiceModel.Syndication.SyndicationElementExtension> Nesneler koleksiyonu.|  
|<xref:System.ServiceModel.Syndication.SyndicationFeed>|Üst düzey bir akış nesnesini temsil eden bir sınıf.|  
|<xref:System.ServiceModel.Syndication.SyndicationItem>|Bir akış öğesini temsil eden sınıf.|  
|<xref:System.ServiceModel.Syndication.SyndicationLink>|Bir dağıtım akışı veya öğe içindeki bir bağlantıyı temsil eden sınıf.|  
|<xref:System.ServiceModel.Syndication.SyndicationPerson>|Atom kişi yapısını temsil eden bir sınıf.|  
|<xref:System.ServiceModel.Syndication.SyndicationVersions>|Desteklenen dağıtım protokolü sürümlerini temsil eden bir sınıf.|  
|<xref:System.ServiceModel.Syndication.TextSyndicationContent>|Son kullanıcıya görüntülenecek <xref:System.ServiceModel.Syndication.SyndicationItem> içeriği temsil eden bir sınıf.|  
|<xref:System.ServiceModel.Syndication.TextSyndicationContentKind>|Desteklenen farklı metin dağıtım içeriği türlerini temsil eden bir sabit listesi.|  
|<xref:System.ServiceModel.Syndication.UrlSyndicationContent>|Başka bir kaynağa ait bir URL 'den oluşan bir dağıtım içeriğini temsil eden bir sınıf.|  
|<xref:System.ServiceModel.Syndication.XmlSyndicationContent>|Bir tarayıcıda görüntülenmeyen dağıtım içeriğini temsil eden bir sınıf.|  
  
 Nesne modelindeki temel veri soyutlamaları, <xref:System.ServiceModel.Syndication.SyndicationFeed> ve <xref:System.ServiceModel.Syndication.SyndicationItem> sınıflarına karşılık gelen akış ve öğedir. Akış, bazı akış düzeyi meta verileri (örneğin, başlık, açıklama ve yazar), bilinmeyen uzantıları depolamak için bir konum ve akışın bilgi içeriğini oluşturan bir öğe kümesi sunar. Öğe, bazı öğe düzeyi meta verileri (örneğin, başlık, Özet ve PublicationDate), bilinmeyen uzantıları depolamak için bir konum ve öğenin bilgi içeriğinin geri kalanını içeren bir içerik öğesi sağlar. Akışın ve öğenin temel soyutlamaları, Atom 1,0 ve RSS belirtimlerinde başvurulan ortak veri yapılarını temsil eden ek sınıflar tarafından desteklenir.  
  
 Bir akış örneğinde taşınan bilgiler çeşitli XML biçimlerine dönüştürülebilir. XML 'e ve öğesinden dönüştürme işlemi <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> sınıfı tarafından yönetilir. Bu sınıf soyuttur; somut uygulamalar, <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> Atom 1,0 ve RSS 2,0 için sağlanır ve <xref:System.ServiceModel.Syndication.Rss20FeedFormatter>. Türetilmiş akış sınıflarını kullanmak için ya <xref:System.ServiceModel.Syndication.Atom10FeedFormatter%601> <xref:System.ServiceModel.Syndication.Rss20FeedFormatter%601> da türetilmiş bir akış sınıfı belirtmenize izin veren olarak kullanın. Türetilmiş öğe sınıflarını kullanmak için ya <xref:System.ServiceModel.Syndication.Atom10ItemFormatter%601> <xref:System.ServiceModel.Syndication.Rss20ItemFormatter%601> da türetilmiş bir öğe sınıfını belirtmenizi sağlayan üçüncü taraflar, <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> farklı dağıtım biçimlerini desteklemek için kendi uygulamasını türetebilirler.  
  
## <a name="extensibility"></a>Genişletilebilirlik  
  
- Dağıtım protokollerinin temel bir özelliği genişletilebilirlik ' dir. Hem Atom 1,0 hem de RSS 2,0, belirtimlerde tanımlanmayan dağıtım akışlarına öznitelikler ve öğeler eklemenize olanak tanır. WCF dağıtım programlama modeli, özel öznitelikler ve uzantılar ile çalışmanın iki yolunu sağlar: yeni bir sınıf türetiliyor ve gevşek olarak yazılmış erişim. Daha fazla bilgi için bkz. [Dağıtım Genişletilebilirliği](../../../../docs/framework/wcf/feature-details/syndication-extensibility.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Dağıtımı Genel Bakış](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md)
- [WCF Dağıtım Nesnesi Modeli Atom ve RSS Eşlemelerini Nasıl Yapar?](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md)
- [WCF Web HTTP Programlama Modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
