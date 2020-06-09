---
title: 'Nasıl yapılır: Bir Akışı Hem Atom Hem de RSS Olarak Kullanıma Sunma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fe374932-67f5-487d-9325-f868812b92e4
ms.openlocfilehash: e4ce1fa7b494c2317a1bddc57ee6b150c84b9a96
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593152"
---
# <a name="how-to-expose-a-feed-as-both-atom-and-rss"></a>Nasıl yapılır: Bir Akışı Hem Atom Hem de RSS Olarak Kullanıma Sunma
Windows Communication Foundation (WCF), bir dağıtım akışı sunan bir hizmet oluşturmanıza olanak sağlar. Bu konu, hem Atom 1,0 hem de RSS 2,0 kullanarak bir dağıtım akışı sunan bir dağıtım hizmeti oluşturmayı açıklamaktadır. Bu hizmet, bir dağıtım biçimi döndüren bir uç noktayı kullanıma sunar. Basitlik için, bu örnekte kullanılan hizmetin kendine barındırıldığı yer vardır. Üretim ortamında, bu türde bir hizmet IIS veya WAS altında barındırılır. Farklı WCF barındırma seçenekleri hakkında daha fazla bilgi için bkz. [barındırma](hosting.md).  
  
### <a name="to-create-a-basic-syndication-service"></a>Temel bir dağıtım hizmeti oluşturmak için  
  
1. Özniteliği ile işaretlenmiş bir arabirim kullanarak bir hizmet sözleşmesi tanımlayın <xref:System.ServiceModel.Web.WebGetAttribute> . Bir dağıtım akışı olarak sunulan her işlem, bir nesnesi döndürür <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> . İçin parametreleri aklınızda edin <xref:System.ServiceModel.Web.WebGetAttribute> . `UriTemplate`Bu hizmet işlemini çağırmak için kullanılan URL 'YI belirtir. Bu parametre için dize, sabit değer ve küme ayracı ({*Format*}) içinde bir değişken içerir. Bu değişken, hizmet işleminin parametresine karşılık gelir `format` . Daha fazla bilgi için bkz. <xref:System.UriTemplate>. `BodyStyle`Bu hizmet işleminin gönderdiği ve aldığı iletilerin nasıl yazıldığını etkiler. <xref:System.ServiceModel.Web.WebMessageBodyStyle.Bare>Bu hizmet işlemine gönderilen ve bu hizmetten gönderilen verilerin altyapı tanımlı XML öğeleri tarafından kaydırılmayacağı belirtir. Daha fazla bilgi için bkz. <xref:System.ServiceModel.Web.WebMessageBodyStyle>.  
  
     [!code-csharp[htAtomRss#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#0)]
     [!code-vb[htAtomRss#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#0)]  
  
    > [!NOTE]
    > <xref:System.ServiceModel.ServiceKnownTypeAttribute>Bu arabirimdeki hizmet işlemleri tarafından döndürülen türleri belirtmek için öğesini kullanın.  
  
2. Hizmet sözleşmesini uygulayın.  
  
     [!code-csharp[htAtomRss#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#1)]
     [!code-vb[htAtomRss#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#1)]  
  
3. Bir <xref:System.ServiceModel.Syndication.SyndicationFeed> nesne oluşturun ve yazar, kategori ve açıklama ekleyin.  
  
     [!code-csharp[htAtomRss#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#2)]
     [!code-vb[htAtomRss#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#2)]  
  
4. Birkaç <xref:System.ServiceModel.Syndication.SyndicationItem> nesne oluşturun.  
  
     [!code-csharp[htAtomRss#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#3)]
     [!code-vb[htAtomRss#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#3)]  
  
5. <xref:System.ServiceModel.Syndication.SyndicationItem>Nesneleri akışa ekleyin.  
  
     [!code-csharp[htAtomRss#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#4)]
     [!code-vb[htAtomRss#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#4)]  
  
6. İstenen biçimi döndürmek için biçim parametresini kullanın.  
  
     [!code-csharp[htAtomRss#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#5)]
     [!code-vb[htAtomRss#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#5)]  
  
### <a name="to-host-the-service"></a>Hizmeti barındırmak için  
  
1. Bir <xref:System.ServiceModel.Web.WebServiceHost> nesne oluşturun. <xref:System.ServiceModel.Web.WebServiceHost>Kod veya yapılandırmada belirtilmemişse, sınıf otomatik olarak hizmetin temel adresinde bir uç nokta ekler. Bu örnekte, varsayılan uç noktanın açığa çıkarılması için uç nokta belirtilmedi.  
  
     [!code-csharp[htAtomRss#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#6)]
     [!code-vb[htAtomRss#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#6)]  
  
2. Hizmet konağını açın, hizmetten akışı yükleyin, akışı görüntüleyin ve kullanıcının ENTER tuşuna basması için bekleyin.  
  
     [!code-csharp[htAtomRss#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#8)]
     [!code-vb[htAtomRss#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a>Getblogi HTTP GET ile çağırmak için  
  
1. Internet Explorer 'ı açın, aşağıdaki URL 'yi yazın ve ENTER tuşuna basın: `http://localhost:8000/BlogService/GetBlog` .
  
     URL, hizmetin temel adresini ( `http://localhost:8000/BlogService` ), bitiş noktasının göreli adresini ve çağrılacak hizmet işlemini içerir.  
  
### <a name="to-call-getblog-from-code"></a>Koddan GetBlog () çağırmak için  
  
1. <xref:System.Xml.XmlReader>Temel adresi ve aradığınız yöntemi içeren bir oluşturun.  
  
     [!code-csharp[htAtomRss#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#9)]
     [!code-vb[htAtomRss#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#9)]  
  
2. <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29>Yeni oluşturduğunuz ' ı geçirerek statik yöntemi çağırın <xref:System.Xml.XmlReader> .  
  
     [!code-csharp[htAtomRss#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#10)]
     [!code-vb[htAtomRss#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#10)]  
  
     Bu, hizmet işlemini çağırır ve <xref:System.ServiceModel.Syndication.SyndicationFeed> hizmet işleminden döndürülen biçimlendirici ile yeni bir doldurur.  
  
3. Akış nesnesine erişin.  
  
     [!code-csharp[htAtomRss#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#11)]
     [!code-vb[htAtomRss#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#11)]  
  
## <a name="example"></a>Örnek  
 Bu örnek için tam kod listesi aşağıda verilmiştir.  
  
 [!code-csharp[htAtomRss#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#12)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki kod derlenirken, System. ServiceModel. dll ve System. ServiceModel. Web. dll ' ye başvurun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
