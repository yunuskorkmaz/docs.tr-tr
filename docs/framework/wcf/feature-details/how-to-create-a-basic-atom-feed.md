---
title: 'Nasıl yapılır: Temel bir Atom akışı oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6e0cacc1-9b11-4665-adb7-577a62626fd6
ms.openlocfilehash: 1229257cc8c15ea67bd4fdf3ff6ffa959a6bfe02
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582506"
---
# <a name="how-to-create-a-basic-atom-feed"></a>Nasıl yapılır: Temel bir Atom akışı oluşturma
Windows Communication Foundation (WCF), bir dağıtım akışı hizmetidir oluşturmanıza olanak sağlar. Bu konu, bir Atom dağıtım akışı sunan bir dağıtım hizmetinin nasıl oluşturulduğunu açıklar.  
  
### <a name="to-create-a-basic-syndication-service"></a>Temel Sendikasyon hizmeti oluşturmak için  
  
1.  İle işaretlenmiş bir arabirim kullanarak bir hizmet sözleşmesini tanımlama <xref:System.ServiceModel.Web.WebGetAttribute> özniteliği. Bir dağıtım akış döndürmelidir olarak sunulan her işlem bir <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> nesne.  
  
     [!code-csharp[htAtomBasic#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#0)]
     [!code-vb[htAtomBasic#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#0)]  
  
    > [!NOTE]
    >  Geçerli olan tüm hizmet işlemleri <xref:System.ServiceModel.Web.WebGetAttribute> HTTP GET isteklerini eşlenir. İşlemi farklı bir HTTP yöntemine eşleyin <xref:System.ServiceModel.Web.WebInvokeAttribute> yerine. Daha fazla bilgi için [nasıl yapılır: Temel bir WCF Web HTTP hizmeti oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md).  
  
2.  Hizmet sözleşmesini uygulama.  
  
     [!code-csharp[htAtomBasic#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#1)]
     [!code-vb[htAtomBasic#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#1)]  
  
3.  Oluşturma bir <xref:System.ServiceModel.Syndication.SyndicationFeed> nesnesi ve bir yazar, kategori ve açıklama ekleyin.  
  
     [!code-csharp[htAtomBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#2)]
     [!code-vb[htAtomBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#2)]  
  
4.  Birkaç oluşturma <xref:System.ServiceModel.Syndication.SyndicationItem> nesneleri.  
  
     [!code-csharp[htAtomBasic#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#3)]
     [!code-vb[htAtomBasic#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#3)]  
  
5.  Ekleme <xref:System.ServiceModel.Syndication.SyndicationItem> akışı nesneleri.  
  
     [!code-csharp[htAtomBasic#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#4)]
     [!code-vb[htAtomBasic#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#4)]  
  
6.  Akış döndürür.  
  
     [!code-csharp[htAtomBasic#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#5)]
     [!code-vb[htAtomBasic#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#5)]  
  
### <a name="to-host-the-service"></a>Ana bilgisayar hizmeti  
  
1.  Oluşturma bir <xref:System.ServiceModel.Web.WebServiceHost> nesne.  
  
     [!code-csharp[htAtomBasic#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#6)]
     [!code-vb[htAtomBasic#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#6)]  
  
2.  Hizmet ana bilgisayarı'nı açın, akışın hizmetten yük, akışı görüntülemek ve kullanıcıyı ENTER tuşuna basın.  
  
     [!code-csharp[htAtomBasic#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#8)]
     [!code-vb[htAtomBasic#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a>Bir HTTP GET ile GetBlog() çağırmak için  
  
1.  Internet Explorer'ı açın, aşağıdaki URL'yi yazın ve ENTER tuşuna basın: `http://localhost:8000/BlogService/GetBlog`  
  
     Hizmetin taban adresi URL içerir (`http://localhost:8000/BlogService`), hizmetin göreli adresini uç nokta ve çağırmak için hizmet işlemi.  
  
### <a name="to-call-getblog-from-code"></a>GetBlog() koddan çağırmak için  
  
1.  Oluşturma bir <xref:System.Xml.XmlReader> taban adresini ve çağırdığınız yöntemi.  
  
     [!code-csharp[htAtomBasic#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#9)]
     [!code-vb[htAtomBasic#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#9)]  
  
2.  Statik çağrı <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> tümleştirilmesidir yöntemi <xref:System.Xml.XmlReader> oluşturdunuz.  
  
     [!code-csharp[htAtomBasic#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#10)]
     [!code-vb[htAtomBasic#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#10)]  
  
     Bu hizmet işlemini çağırır ve yeni bir doldurur <xref:System.ServiceModel.Syndication.SyndicationFeed> hizmet işleminden döndürülen biçimlendirici ile.  
  
3.  Erişim akış nesnesi.  
  
     [!code-csharp[htAtomBasic#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#11)]
     [!code-vb[htAtomBasic#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#11)]  
  
## <a name="example"></a>Örnek  
 Bu örnek için listeleme tam kod aşağıda verilmiştir.  
  
 [!code-csharp[htAtomBasic#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#12)]
 [!code-vb[htAtomBasic#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#12)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki kod derlenirken System.ServiceModel.dll ve System.ServiceModel.Web.dll başvuru.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
