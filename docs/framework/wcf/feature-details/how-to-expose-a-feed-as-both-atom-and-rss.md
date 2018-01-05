---
title: "Nasıl yapılır: Bir Akışı Hem Atom Hem de RSS Olarak Kullanıma Sunma"
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
ms.assetid: fe374932-67f5-487d-9325-f868812b92e4
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6584f71450917669024c965c121edebb7dffc677
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-expose-a-feed-as-both-atom-and-rss"></a>Nasıl yapılır: Bir Akışı Hem Atom Hem de RSS Olarak Kullanıma Sunma
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]Akış bir dağıtım kullanıma sunan bir hizmet oluşturmanıza olanak sağlar. Bu konu akışı hem Atom 1.0 hem de RSS 2.0 kullanarak bir dağıtım gösteren bir dağıtım hizmetin nasıl oluşturulacağını açıklar. Bu hizmet ya da yayınlama biçimi döndürebilir bir uç noktasını kullanıma sunar. Kolaylık olması için bu örnekte kullanılan self barındırılan hizmetidir. Bir üretim ortamında bu türde bir hizmet IIS ya da WAS altında barındırılması. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]farklı [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] seçenekleri barındırma, bkz: [barındırma](../../../../docs/framework/wcf/feature-details/hosting.md).  
  
### <a name="to-create-a-basic-syndication-service"></a>Bir temel dağıtım hizmet oluşturmak için  
  
1.  İle işaretlenen arabirimini kullanarak bir hizmet sözleşmesini tanımlama <xref:System.ServiceModel.Web.WebGetAttribute> özniteliği. Bir dağıtım döndürür akış olarak sunulan her işlem bir <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> nesnesi. Parametrelerini Not <xref:System.ServiceModel.Web.WebGetAttribute>. `UriTemplate`Bu hizmet işlemini çağırmak için kullanılan URL'yi belirtir. Bu parametre için dize değişmez değerleri ve küme ayraçları bir değişkende içeriyor ({*biçimi*}). Bu değişken hizmeti işlem için karşılık gelen `format` parametresi. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] <xref:System.UriTemplate>. `BodyStyle`Bu hizmet işlemi alıp gönderen iletileri nasıl yazılır etkiler. <xref:System.ServiceModel.Web.WebMessageBodyStyle.Bare>Altyapı tanımlı XML öğeleri tarafından gönderilen ve bu hizmeti işlem verileri Sarmalanan değil belirtir. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] <xref:System.ServiceModel.Web.WebMessageBodyStyle>.  
  
     [!code-csharp[htAtomRss#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#0)]
     [!code-vb[htAtomRss#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#0)]  
  
    > [!NOTE]
    >  Kullanım <xref:System.ServiceModel.ServiceKnownTypeAttribute> Bu arabirimdeki hizmet işlemleri tarafından döndürülen türlerini belirtmek için.  
  
2.  Hizmet sözleşmesini uygulama.  
  
     [!code-csharp[htAtomRss#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#1)]
     [!code-vb[htAtomRss#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#1)]  
  
3.  Oluşturma bir <xref:System.ServiceModel.Syndication.SyndicationFeed> nesne ve yazar, kategori ve açıklama ekleyin.  
  
     [!code-csharp[htAtomRss#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#2)]
     [!code-vb[htAtomRss#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#2)]  
  
4.  Birkaç oluşturmak <xref:System.ServiceModel.Syndication.SyndicationItem> nesneleri.  
  
     [!code-csharp[htAtomRss#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#3)]
     [!code-vb[htAtomRss#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#3)]  
  
5.  Ekleme <xref:System.ServiceModel.Syndication.SyndicationItem> akışa nesneleri.  
  
     [!code-csharp[htAtomRss#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#4)]
     [!code-vb[htAtomRss#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#4)]  
  
6.  İstenen biçim döndürmek için biçim parametresini kullanın.  
  
     [!code-csharp[htAtomRss#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#5)]
     [!code-vb[htAtomRss#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#5)]  
  
### <a name="to-host-the-service"></a>Ana bilgisayar hizmeti  
  
1.  Oluşturma bir <xref:System.ServiceModel.Web.WebServiceHost> nesnesi. <xref:System.ServiceModel.Web.WebServiceHost> Sınıfı otomatik olarak ekler bir uç nokta hizmetin temel adresinde bir kod veya yapılandırma belirtilmediği sürece. Bu örnekte, varsayılan uç açıklanması için uç nokta yok belirtilir.  
  
     [!code-csharp[htAtomRss#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#6)]
     [!code-vb[htAtomRss#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#6)]  
  
2.  Hizmet ana bilgisayarı açın, akışı hizmetten yüklenemiyor, akışı görüntülemek ve ENTER tuşuna basın kullanıcıya için bekleyin.  
  
     [!code-csharp[htAtomRss#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#8)]
     [!code-vb[htAtomRss#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a>Bir HTTP GET ile GetBlog çağırmak için  
  
1.  Internet Explorer'ı açın, aşağıdaki URL'yi yazın ve ENTER tuşuna basın. 8000/BlogService/GetBlog  
  
     URL (8000/BlogService) hizmeti temel adresi, bitiş noktası ve hizmet işlemini çağırmak için göreli adresini içerir.  
  
### <a name="to-call-getblog-from-code"></a>Koddan GetBlog() çağırmak için  
  
1.  Oluşturma bir <xref:System.Xml.XmlReader> taban adresini ve çağırdığınız yöntemi.  
  
     [!code-csharp[htAtomRss#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#9)]
     [!code-vb[htAtomRss#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#9)]  
  
2.  Statik çağrısı <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> tümleştirilmesidir yöntemi <xref:System.Xml.XmlReader> , yeni oluşturduğunuz.  
  
     [!code-csharp[htAtomRss#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#10)]
     [!code-vb[htAtomRss#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#10)]  
  
     Bu hizmet işlemini çağırır ve yeni bir doldurur <xref:System.ServiceModel.Syndication.SyndicationFeed> hizmet işleminden döndürülen biçimlendirici ile.  
  
3.  Erişim akış nesnesi.  
  
     [!code-csharp[htAtomRss#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#11)]
     [!code-vb[htAtomRss#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#11)]  
  
## <a name="example"></a>Örnek  
 Bu örnek için listeleme tam kod aşağıda verilmiştir.  
  
 [!code-csharp[htAtomRss#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#12)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki kod derlerken System.ServiceModel.dll ve System.ServiceModel.Web.dll başvuru.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>
