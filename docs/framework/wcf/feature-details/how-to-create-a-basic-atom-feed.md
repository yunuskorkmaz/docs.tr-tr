---
title: 'Nasıl yapılır: Temel Bir Atom Akışı Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6e0cacc1-9b11-4665-adb7-577a62626fd6
ms.openlocfilehash: 82095f397195fbf333bab8d043da18114e2a5dba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968467"
---
# <a name="how-to-create-a-basic-atom-feed"></a>Nasıl yapılır: Temel Bir Atom Akışı Oluşturma
Windows Communication Foundation (WCF), bir dağıtım akışı sunan bir hizmet oluşturmanıza olanak sağlar. Bu konuda, bir Atom dağıtım akışını kullanıma sunan bir dağıtım hizmeti oluşturma konusu ele alınmaktadır.  
  
### <a name="to-create-a-basic-syndication-service"></a>Temel bir dağıtım hizmeti oluşturmak için  
  
1. <xref:System.ServiceModel.Web.WebGetAttribute> Özniteliği ile işaretlenmiş bir arabirim kullanarak bir hizmet sözleşmesi tanımlayın. Bir dağıtım akışı olarak sunulan her işlem bir <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> nesne döndürmelidir.  
  
     [!code-csharp[htAtomBasic#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#0)]
     [!code-vb[htAtomBasic#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#0)]  
  
    > [!NOTE]
    > ' İ uygulayan tüm hizmet işlemleri <xref:System.ServiceModel.Web.WebGetAttribute> http get isteklerine eşlenir. İşleminizi farklı bir http yöntemiyle eşlemek için, <xref:System.ServiceModel.Web.WebInvokeAttribute> bunun yerine kullanın. Daha fazla bilgi için [nasıl yapılır: Temel bir WCF Web HTTP hizmeti](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)oluşturun.  
  
2. Hizmet sözleşmesini uygulayın.  
  
     [!code-csharp[htAtomBasic#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#1)]
     [!code-vb[htAtomBasic#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#1)]  
  
3. Bir <xref:System.ServiceModel.Syndication.SyndicationFeed> nesne oluşturun ve yazar, kategori ve açıklama ekleyin.  
  
     [!code-csharp[htAtomBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#2)]
     [!code-vb[htAtomBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#2)]  
  
4. Birkaç <xref:System.ServiceModel.Syndication.SyndicationItem> nesne oluşturun.  
  
     [!code-csharp[htAtomBasic#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#3)]
     [!code-vb[htAtomBasic#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#3)]  
  
5. <xref:System.ServiceModel.Syndication.SyndicationItem> Nesneleri akışa ekleyin.  
  
     [!code-csharp[htAtomBasic#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#4)]
     [!code-vb[htAtomBasic#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#4)]  
  
6. Akışı döndürün.  
  
     [!code-csharp[htAtomBasic#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#5)]
     [!code-vb[htAtomBasic#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#5)]  
  
### <a name="to-host-the-service"></a>Hizmeti barındırmak için  
  
1. Bir <xref:System.ServiceModel.Web.WebServiceHost> nesne oluşturun.  
  
     [!code-csharp[htAtomBasic#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#6)]
     [!code-vb[htAtomBasic#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#6)]  
  
2. Hizmet konağını açın, hizmetten akışı yükleyin, akışı görüntüleyin ve kullanıcının ENTER tuşuna basması için bekleyin.  
  
     [!code-csharp[htAtomBasic#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#8)]
     [!code-vb[htAtomBasic#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a>HTTP GET ile GetBlog () çağırmak için  
  
1. Internet Explorer 'ı açın, aşağıdaki URL 'yi yazın ve ENTER tuşuna basın:`http://localhost:8000/BlogService/GetBlog`  
  
     URL, hizmetin temel adresini (`http://localhost:8000/BlogService`), bitiş noktasının göreli adresini ve çağrılacak hizmet işlemini içerir.  
  
### <a name="to-call-getblog-from-code"></a>Koddan GetBlog () çağırmak için  
  
1. Temel adresi <xref:System.Xml.XmlReader> ve aradığınız yöntemi içeren bir oluşturun.  
  
     [!code-csharp[htAtomBasic#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#9)]
     [!code-vb[htAtomBasic#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#9)]  
  
2. Yeni oluşturduğunuz ' <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> ı geçirerek <xref:System.Xml.XmlReader> statik yöntemi çağırın.  
  
     [!code-csharp[htAtomBasic#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#10)]
     [!code-vb[htAtomBasic#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#10)]  
  
     Bu, hizmet işlemini çağırır ve hizmet işleminden döndürülen <xref:System.ServiceModel.Syndication.SyndicationFeed> biçimlendirici ile yeni bir doldurur.  
  
3. Akış nesnesine erişin.  
  
     [!code-csharp[htAtomBasic#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#11)]
     [!code-vb[htAtomBasic#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#11)]  
  
## <a name="example"></a>Örnek  
 Bu örnek için tam kod listesi aşağıda verilmiştir.  
  
 [!code-csharp[htAtomBasic#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#12)]
 [!code-vb[htAtomBasic#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#12)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki kod derlenirken, System. ServiceModel. dll ve System. ServiceModel. Web. dll ' ye başvurun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
