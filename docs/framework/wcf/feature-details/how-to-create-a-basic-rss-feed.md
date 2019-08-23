---
title: 'Nasıl yapılır: Temel Bir RSS Akışı Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 431879b8-a5f8-4947-ad1e-4768c726aca8
ms.openlocfilehash: 9a07754e8fdad700bd5488f392f80b5c5f907f6e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968440"
---
# <a name="how-to-create-a-basic-rss-feed"></a>Nasıl yapılır: Temel Bir RSS Akışı Oluşturma
Windows Communication Foundation (WCF), bir dağıtım akışı sunan bir hizmet oluşturmanıza olanak sağlar. Bu konuda, RSS dağıtım akışını kullanıma sunan bir dağıtım hizmeti oluşturma konusu ele alınmaktadır.  
  
### <a name="to-create-a-basic-syndication-service"></a>Temel bir dağıtım hizmeti oluşturmak için  
  
1. <xref:System.ServiceModel.Web.WebGetAttribute> Özniteliği ile işaretlenmiş bir arabirim kullanarak bir hizmet sözleşmesi tanımlayın. Bir dağıtım akışı olarak sunulan her işlem bir <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> nesne döndürmelidir.  
  
     [!code-csharp[htRssBasic#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#0)]
     [!code-vb[htRssBasic#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#0)]  
  
    > [!NOTE]
    > <xref:System.ServiceModel.Web.WebGetAttribute> Özniteliğini uygulayan tüm hizmet işlemleri http get istekleri ile eşleştirilir. İşleminizi farklı bir http yöntemiyle eşlemek için, <xref:System.ServiceModel.Web.WebInvokeAttribute> bunun yerine kullanın. Daha fazla bilgi için [nasıl yapılır: Temel bir WCF Web HTTP hizmeti](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)oluşturun.  
  
2. Hizmet sözleşmesini uygulayın.  
  
     [!code-csharp[htRssBasic#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#1)]
     [!code-vb[htRssBasic#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#1)]  
  
3. Bir <xref:System.ServiceModel.Syndication.SyndicationFeed> nesne oluşturun ve yazar, kategori ve açıklama ekleyin.  
  
     [!code-csharp[htRssBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#2)]
     [!code-vb[htRssBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#2)]  
  
4. Birkaç <xref:System.ServiceModel.Syndication.SyndicationItem> nesne oluşturun.  
  
     [!code-csharp[htRssBasic#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#3)]
     [!code-vb[htRssBasic#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#3)]  
  
5. <xref:System.ServiceModel.Syndication.SyndicationItem> ' İ akışa ekleyin.  
  
     [!code-csharp[htRssBasic#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#4)]
     [!code-vb[htRssBasic#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#4)]  
  
6. Akışı döndürün.  
  
     [!code-csharp[htRssBasic#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#5)]
     [!code-vb[htRssBasic#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#5)]  
  
### <a name="to-host-a-service"></a>Bir hizmeti barındırmak için  
  
1. Bir <xref:System.ServiceModel.Web.WebServiceHost> nesne oluşturun.  
  
     [!code-csharp[htRssBasic#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#6)]
     [!code-vb[htRssBasic#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#6)]  
  
2. Hizmet konağını açın ve Kullanıcı ENTER tuşuna basana kadar bekleyin.  
  
     [!code-csharp[htRssBasic#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#8)]
     [!code-vb[htRssBasic#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a>HTTP GET ile GetBlog () çağırmak için  
  
1. Internet Explorer 'ı açın, aşağıdaki URL 'yi yazın ve ENTER tuşuna basın `http://localhost:8000/BlogService/GetBlog`:. URL, hizmetin temel adresini (`http://localhost:8000/BlogService`), bitiş noktasının göreli adresini ve çağrılacak hizmet işlemini içerir.  
  
### <a name="to-call-getblog-from-code"></a>Koddan GetBlog () çağırmak için  
  
1. Temel adresi <xref:System.Xml.XmlReader> ve aradığınız yöntemi içeren bir oluşturun.  
  
     [!code-csharp[htRssBasic#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#9)]
     [!code-vb[htRssBasic#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#9)]  
  
2. Yeni oluşturduğunuz ' <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> ı geçirerek <xref:System.Xml.XmlReader> statik yöntemi çağırın.  
  
     [!code-csharp[htRssBasic#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#10)]
     [!code-vb[htRssBasic#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#10)]  
  
     Bu, hizmet işlemini çağırır ve hizmet işleminden döndürülen <xref:System.ServiceModel.Syndication.SyndicationFeed> biçimlendirici ile yeni bir doldurur.  
  
3. Akış nesnesine erişin.  
  
     [!code-csharp[htRssBasic#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#11)]
     [!code-vb[htRssBasic#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#11)]  
  
## <a name="example"></a>Örnek  
 Bu örnek için tam kod listesi aşağıda verilmiştir.  
  
 [!code-csharp[htRssBasic#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#12)]
 [!code-vb[htRssBasic#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#12)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki kod derlenirken, System. ServiceModel. dll ve System. ServiceModel. Web. dll ' ye başvurun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
