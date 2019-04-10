---
title: 'Nasıl yapılır: Bir Akışı Hem Atom Hem de RSS Olarak Kullanıma Sunma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fe374932-67f5-487d-9325-f868812b92e4
ms.openlocfilehash: 17494b00259839be3beb580a516ff017ec3de50e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228412"
---
# <a name="how-to-expose-a-feed-as-both-atom-and-rss"></a>Nasıl yapılır: Bir Akışı Hem Atom Hem de RSS Olarak Kullanıma Sunma
Windows Communication Foundation (WCF), bir dağıtım akışı hizmetidir oluşturmanıza olanak sağlar. Bu konu, bir dağıtım akışı hem Atom 1.0 hem de RSS 2.0 kullanarak kullanıma sunan bir dağıtım hizmetinin nasıl oluşturulduğunu açıklar. Bu hizmet ya da dağıtım biçimi döndüren bir uç noktasını kullanıma sunar. Kolaylık olması için bu örnekte kullanılan kendi kendine barındırılan hizmetidir. Bir üretim ortamında bu türde bir hizmet IIS ya da WAS altında barındırılması. Barındırma seçenekleri farklı WCF hakkında daha fazla bilgi için bkz. [barındırma](../../../../docs/framework/wcf/feature-details/hosting.md).  
  
### <a name="to-create-a-basic-syndication-service"></a>Temel Sendikasyon hizmeti oluşturmak için  
  
1.  İle işaretlenmiş bir arabirim kullanarak bir hizmet sözleşmesini tanımlama <xref:System.ServiceModel.Web.WebGetAttribute> özniteliği. Döndürür bir dağıtım akışı olarak sunulan her işlem bir <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> nesne. Parametreler için Not <xref:System.ServiceModel.Web.WebGetAttribute>. `UriTemplate` Bu hizmet işlemini çağırmak için kullanılan URL'sini belirtir. Bu parametre için dize değişmez değerleri ve küme ayraçları içinde bir değişken içeriyor ({*biçimi*}). Hizmet işlem için bu değişkeni karşılık gelen `format` parametresi. Daha fazla bilgi için bkz. <xref:System.UriTemplate>. `BodyStyle` Bu hizmet işlemi gönderip aldığı iletileri nasıl yazılır etkiler. <xref:System.ServiceModel.Web.WebMessageBodyStyle.Bare> Altyapı tarafından tanımlanan XML öğeleri tarafından gönderilen ve alınan bu hizmet işlemi verileri kaydırılan değil belirtir. Daha fazla bilgi için bkz. <xref:System.ServiceModel.Web.WebMessageBodyStyle>.  
  
     [!code-csharp[htAtomRss#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#0)]
     [!code-vb[htAtomRss#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#0)]  
  
    > [!NOTE]
    >  Kullanım <xref:System.ServiceModel.ServiceKnownTypeAttribute> bu arabirim, hizmet işlemleri tarafından döndürülen türlerini belirtmek için.  
  
2.  Hizmet sözleşmesini uygulama.  
  
     [!code-csharp[htAtomRss#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#1)]
     [!code-vb[htAtomRss#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#1)]  
  
3.  Oluşturma bir <xref:System.ServiceModel.Syndication.SyndicationFeed> nesnesi ve bir yazar, kategori ve açıklama ekleyin.  
  
     [!code-csharp[htAtomRss#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#2)]
     [!code-vb[htAtomRss#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#2)]  
  
4.  Birkaç oluşturma <xref:System.ServiceModel.Syndication.SyndicationItem> nesneleri.  
  
     [!code-csharp[htAtomRss#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#3)]
     [!code-vb[htAtomRss#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#3)]  
  
5.  Ekleme <xref:System.ServiceModel.Syndication.SyndicationItem> akışı nesneleri.  
  
     [!code-csharp[htAtomRss#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#4)]
     [!code-vb[htAtomRss#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#4)]  
  
6.  İstenen biçimi döndürmek için biçim parametresi'ı kullanın.  
  
     [!code-csharp[htAtomRss#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#5)]
     [!code-vb[htAtomRss#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#5)]  
  
### <a name="to-host-the-service"></a>Ana bilgisayar hizmeti  
  
1.  Oluşturma bir <xref:System.ServiceModel.Web.WebServiceHost> nesne. <xref:System.ServiceModel.Web.WebServiceHost> Sınıfı otomatik olarak ekler bir uç nokta hizmetin temel adresinde bir kod veya yapılandırma belirtilmediği sürece. Bu örnekte, varsayılan uç nokta açıklanması uç nokta belirtilir.  
  
     [!code-csharp[htAtomRss#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#6)]
     [!code-vb[htAtomRss#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#6)]  
  
2.  Hizmet ana bilgisayarı'nı açın, akışın hizmetten yük, akışı görüntülemek ve kullanıcıyı ENTER tuşuna basın.  
  
     [!code-csharp[htAtomRss#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#8)]
     [!code-vb[htAtomRss#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a>Bir HTTP GET ile GetBlog çağırmak için  
  
1.  Internet Explorer'ı açın, aşağıdaki URL'yi yazın ve ENTER tuşuna basın: `http://localhost:8000/BlogService/GetBlog`.
  
     Hizmetin taban adresi URL içerir (`http://localhost:8000/BlogService`), hizmetin göreli adresini uç nokta ve çağırmak için hizmet işlemi.  
  
### <a name="to-call-getblog-from-code"></a>GetBlog() koddan çağırmak için  
  
1.  Oluşturma bir <xref:System.Xml.XmlReader> taban adresini ve çağırdığınız yöntemi.  
  
     [!code-csharp[htAtomRss#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#9)]
     [!code-vb[htAtomRss#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#9)]  
  
2.  Statik çağrı <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> tümleştirilmesidir yöntemi <xref:System.Xml.XmlReader> oluşturdunuz.  
  
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
 Yukarıdaki kod derlenirken System.ServiceModel.dll ve System.ServiceModel.Web.dll başvuru.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
