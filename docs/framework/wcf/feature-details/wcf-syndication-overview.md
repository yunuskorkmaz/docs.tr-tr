---
title: WCF Dağıtımı Genel Bakış
ms.date: 03/30/2017
ms.assetid: af6d4c39-e5e8-4099-aee6-5261feff9107
ms.openlocfilehash: 82e8e1192b791dde1ca0ea7e030c7cfc82476b76
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718253"
---
# <a name="wcf-syndication-overview"></a>WCF Dağıtımı Genel Bakış
Windows Communication Foundation (WCF), dağıtım akışlarını bir WCF hizmetinden açığa çıkarmak için destek sağlar. Dağıtım, uygulama tümleştirme bir sunucu bazı uygulama veri akışı olarak bilinen birlikte çalışabilen bir biçimde kullanıma sunan bir mekanizmadır. Bir akışı, bazı akış düzeyinde meta verileri (başlık, yazar, URL ve diğer meta verileri) içeren uygulama verilerinin bir koleksiyonunu ve akış öğelerini bir dizi değildir. Akışın içinde genellikle zamana ters sırasına göre sıralı akış öğelerdir. Akış öğesi çoklukta uygulama belirli verileri öğe düzeyinde meta verileri (başlık, URL, oluşturma tarihi, kategori ve diğer öğe düzeyinde meta verileri) ve standart bir kümesinden oluşur. İki en yaygın dağıtım akışlarını gerçekten basit dağıtım (RSS) 2.0 ve Atom 1.0, ikisi için de WCF tarafından desteklenen türleridir.  
  
## <a name="object-model"></a>Nesne modeli  
 WCF akışları, akış öğelerini ve ilgili meta veriler bir biçim bağımsız bir şekilde çalışmanıza olanak tanıyan dağıtım özel sınıf kümesi tanımlar: <xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem>, <xref:System.ServiceModel.Syndication.SyndicationPerson>, <xref:System.ServiceModel.Syndication.SyndicationLink>ve diğer dağıtım özgü sınıflar. WCF aynı zamanda WCF REST programlama dağıtım desteği dahil olmak üzere sağlamak için Model derleme altyapı sınıfları tanımlar: <xref:System.ServiceModel.Syndication.Atom10FeedFormatter>, ve <xref:System.ServiceModel.Syndication.Rss20FeedFormatter>. Akış biçimlendirici sınıfları, RSS 2.0 ve Atom 1.0 gelen ve giden nesne modeli seri hale getirme destekler.  
  
## <a name="scenarios"></a>Senaryolar  
 Bir ortak bugün dağıtım blog, blog yazarı bazı tür bilgileri düzenli aralıklarla yayımladığı kullanılır. Bu metin, görüntü, ses veya başka tür bilgileri olabilir. Ayrıca birçok gazete ve dergilerden haberleri veya dağıtım kullanan makaleler yayımlayın. Böyle bir akışa abone olarak, bir kullanıcı bu sitelerden gelen yeni bilgilerle güncel kalmasını sağlayabilirsiniz. Dağıtım Web Günlükleri ve yayımcılar en yaygın olarak ilişkili olsa da, bilgi koleksiyonunu sunan herhangi bir uygulama ile kullanılabilir; Örneğin, bir dağıtım kullanarak kullanıma sunmak istediğiniz bir hata veritabanı akış. Adlı bir işlem kullanıma sunan bir WCF Hizmeti oluşturabilirsiniz `CodeDefects`. Bu işlem, hataları almak istediğiniz kişinin e-posta adresini belirten bir parametre alabilir. Bir istemci işlemi çağırmak için şu URL'yi kullanın: `http://someserver/bugDatabase/CodeDefects?user=johndoe`.  
  
## <a name="syndication-formats"></a>Dağıtım biçimlerini  
 WCF dağıtım platformu RSS 2.0 ve Atom 1.0 destekler.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [WCF Web HTTP Programlama Modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
