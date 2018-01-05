---
title: "WCF Dağıtımı Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af6d4c39-e5e8-4099-aee6-5261feff9107
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: acc7131d02f1f4e3cde0df152bdfbc591724b600
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-syndication-overview"></a>WCF Dağıtımı Genel Bakış
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]Dağıtım Akışları'gösterme için destek sağlayan bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet. Dağıtım, bir sunucu bazı uygulama veri akışı olarak bilinen bir birlikte çalışabilen biçiminde kullanıma sunar uygulama tümleştirme bir mekanizmadır. Bir akış bazı akış düzeyi meta verileri (başlık, yazar, URL ve diğer meta verileri) oluşur uygulama verilerinin bir koleksiyonunu ve akış öğelerini bir dizi ' dir. Akış içinde genellikle zaman ters tarih sırasına göre sıralı akış öğelerdir. Bir akış öğesi (başlık, URL, oluşturulduğu tarih, kategori ve diğer öğe düzeyinde meta verileri) öğe düzeyinde meta verileri ve rasgele bir uygulama belirli veri miktarı standart kümesinden oluşur. İki en yaygın dağıtım akışlarını gerçekten basit dağıtım (RSS) 2.0 ve Atom 1.0, her ikisi de tarafından desteklendiği türleridir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="object-model"></a>Nesne modeli  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Akışlar, akış öğelerini ve ilgili meta veri biçimi bağımsız bir şekilde çalışmanıza olanak sağlayan dağıtım özgü sınıflar kümesini tanımlar: <xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem>, <xref:System.ServiceModel.Syndication.SyndicationPerson>, <xref:System.ServiceModel.Syndication.SyndicationLink>ve diğer dağıtım özgü sınıflar. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]aynı zamanda WCF REST programlama dağıtım desteği dahil olmak üzere sağlamak için Model üzerinde yapı altyapı sınıfları tanımlar: <xref:System.ServiceModel.Syndication.Atom10FeedFormatter>, ve <!--zz <xref:System.ServiceModel.Syndication.RSS20FeedFormatter>--> `RSS20FeedFormatter`. Akış biçimlendirici sınıfları için ve RSS 2.0 ve Atom 1.0 nesne modeli seri hale getirme destekler.  
  
## <a name="scenarios"></a>Senaryolar  
 Bir ortak dağıtım bugün blog, blog Yazar düzenli olarak bilgi çeşit yayımladığı kullanılır. Bu metin, görüntüler, ses veya başka tür bilgileri olabilir. Birçok gazete ve dergi haberleri veya dağıtım kullanan makaleler de yayımlar. Bu tür bir Özet akışına abone olarak bir kullanıcı gibi sitelerinden gelen tüm yeni bilgilerle güncel tutabilirsiniz. Dağıtım Web Günlükleri ve yayımcılar en yaygın olarak ilişkili olsa da, bu bilgilerin toplanması kullanıma sunan herhangi bir uygulama ile kullanılabilir; Örneğin, bir dağıtım kullanarak kullanıma sunmak istediğiniz bir hata veritabanı akış. Oluşturabileceğiniz bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] çağrılan bir işlem sunan hizmeti `CodeDefects`. Bu işlem, hatalar, almak istediğiniz kişinin e-posta adresini belirten bir parametre ele geçirebilir. Bir istemci işlemi çağırmak için aşağıdaki URL'yi kullanın: http://someserver/bugDatabase/CodeDefects?user=johndoe.  
  
## <a name="syndication-formats"></a>Dağıtım biçimlerini  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Dağıtım platformu RSS 2.0 ve Atom 1.0 destekler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Web HTTP Programlama Modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
