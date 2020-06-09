---
title: WCF Dağıtımı Genel Bakış
ms.date: 03/30/2017
ms.assetid: af6d4c39-e5e8-4099-aee6-5261feff9107
ms.openlocfilehash: 4f72a6d797f195108401a361cc73d74d309d5602
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600964"
---
# <a name="wcf-syndication-overview"></a>WCF Dağıtımı Genel Bakış
Windows Communication Foundation (WCF), bir WCF hizmetinden dağıtım akışlarını açığa çıkarmak için destek sağlar. Dağıtım, bir sunucunun bazı uygulama verilerini akış olarak bilinen bir birlikte çalışabilen biçimde kullanıma sunduğu bir uygulama tümleştirme mekanizmasıdır. Akış, bazı akış düzeyi meta verilerden (başlık, yazar, URL ve diğer meta veriler) oluşan bir uygulama verileri koleksiyonudur ve bir dizi akış öğesi. Akış içinde, akış öğeleri genellikle doğru kronolojik düzende zaman içinde sıralanır. Bir akış öğesi, standart bir öğe düzeyi meta veri kümesinden (başlık, URL, oluşturma tarihi, kategori ve diğer öğe düzeyi meta veriler) ve rastgele uygulamaya özgü verilerin oluşur. En yaygın iki dağıtım akışı türü, her ikisi de WCF tarafından desteklenen basit dağıtım (RSS) 2,0 ve Atom 1,0 ' dir.  
  
## <a name="object-model"></a>Nesne modeli  
 WCF, akışlar, akış öğeleri ve ilgili meta veriler ile bağımsız bir biçimde,,,, <xref:System.ServiceModel.Syndication.SyndicationFeed> <xref:System.ServiceModel.Syndication.SyndicationItem> <xref:System.ServiceModel.Syndication.SyndicationPerson> <xref:System.ServiceModel.Syndication.SyndicationLink> ve diğer dağıtım özgü sınıflar ile çalışmanıza olanak sağlayan bir dağıtım özgü sınıflar kümesi tanımlar. WCF Ayrıca, ve dahil olmak üzere dağıtım desteği sağlamak üzere WCF REST programlama modeli üzerinde derleme yapan altyapı sınıflarını tanımlar <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> . Akış biçimlendirici sınıfları, RSS 2,0 ve Atom 1,0 nesne modelini ve bu bilgisayardan serileştirmek destekler.  
  
## <a name="scenarios"></a>Senaryolar  
 Bugün bir genel dağıtımın kullanımı, blog yazarının düzenli olarak bazı bilgileri bir şekilde yayımladığı bir blog kullanmaktır. Bu metin, görüntü, ses veya diğer bilgi türleri olabilir. Birçok Gazeteler ve dergi Ayrıca, dağıtım kullanarak haber hikayeleri veya makaleler yayımlar. Bu tür bir akışa abone olurken, bir Kullanıcı bu türden sitelerden gelen tüm yeni bilgileri kullanarak güncel olabilir. Dağıtım, blogların ve yayımcıların en yaygın olarak ilişkili olmasına karşın, bir bilgi koleksiyonu sunan herhangi bir uygulamayla birlikte kullanılabilir; Örneğin, bir dağıtım akışı kullanarak sunmak istediğiniz bir hata veritabanı. Adlı bir işlemi kullanıma sunan bir WCF hizmeti oluşturabilirsiniz `CodeDefects` . Bu işlem, hatalarını almak istediğiniz kişinin e-posta adresini belirten bir parametre alabilir. İstemci, işlemi çağırmak için aşağıdaki URL 'YI kullanabilir: `http://someserver/bugDatabase/CodeDefects?user=johndoe` .  
  
## <a name="syndication-formats"></a>Dağıtım biçimleri  
 WCF dağıtım platformu RSS 2,0 ve Atom 1,0 ' ü destekler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Web HTTP Programlama Modeli](wcf-web-http-programming-model.md)
