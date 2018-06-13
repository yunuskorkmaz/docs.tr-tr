---
title: 'Nasıl yapılır: Bir Sözleşmeyi SOAP ve Web İstemcilerine Sunma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: bb765a48-12f2-430d-a54d-6f0c20f2a23a
ms.openlocfilehash: a9a730fe94d1df8c887a2eaf20c1e338bd056ed5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33494156"
---
# <a name="how-to-expose-a-contract-to-soap-and-web-clients"></a>Nasıl yapılır: Bir Sözleşmeyi SOAP ve Web İstemcilerine Sunma
Varsayılan olarak, Windows Communication Foundation (WCF) uç noktalar yalnızca SOAP istemcilerin kullanımına sunuyor. İçinde [nasıl yapılır: temel bir WCF Web HTTP hizmeti oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md), bir uç nokta SOAP olmayan istemciler için kullanılabilir hale getirilir. Aynı sözleşme çift yönlü bir Web uç noktası ve bir SOAP uç noktası olarak kullanılabilir hale getirmek istediğinizde zamanlar olabilir. Bu konu bunun nasıl yapılacağı örneği gösterir.  
  
### <a name="to-define-the-service-contract"></a>Hizmet sözleşmesi tanımlamak için  
  
1.  İle işaretlenen arabirimini kullanarak bir hizmet sözleşmesini tanımlayan <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> ve <xref:System.ServiceModel.Web.WebGetAttribute> aşağıdaki kodda gösterildiği gibi öznitelikleri.  
  
     [!code-csharp[htSoapWeb#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#0)]
     [!code-vb[htSoapWeb#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#0)]  
  
    > [!NOTE]
    >  Varsayılan olarak <xref:System.ServiceModel.Web.WebInvokeAttribute> işlemi POST çağrıları eşler. Bununla birlikte, belirterek işlemi eşleştirmek için yöntemini belirleyebilirsiniz bir "yöntemi =" parametresi. <xref:System.ServiceModel.Web.WebGetAttribute> sahip olmayan bir "yöntemi =" GET parametre ve yalnızca eşlemeleri hizmet işlemini çağırır.  
  
2.  Aşağıdaki kodda gösterildiği gibi hizmet sözleşmesini uygulayın.  
  
     [!code-csharp[htSoapWeb#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#1)]
     [!code-vb[htSoapWeb#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#1)]  
  
### <a name="to-host-the-service"></a>Ana bilgisayar hizmeti  
  
1.  Oluşturma bir <xref:System.ServiceModel.ServiceHost> aşağıdaki kodda gösterildiği gibi nesne.  
  
     [!code-csharp[htSoapWeb#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#2)]
     [!code-vb[htSoapWeb#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#2)]  
  
2.  Ekleme bir <xref:System.ServiceModel.Description.ServiceEndpoint> ile <xref:System.ServiceModel.BasicHttpBinding> aşağıdaki kodda gösterildiği gibi SOAP uç için.  
  
     [!code-csharp[htSoapWeb#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#3)]
     [!code-vb[htSoapWeb#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#3)]  
  
3.  Ekleme bir <xref:System.ServiceModel.Description.ServiceEndpoint> ile <xref:System.ServiceModel.WebHttpBinding> olmayan SOAP uç noktası için ve ekleme <xref:System.ServiceModel.Description.WebHttpBehavior> aşağıdaki kodda gösterildiği gibi uç.  
  
     [!code-csharp[htSoapWeb#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#4)]
     [!code-vb[htSoapWeb#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#4)]  
  
4.  Çağrı `Open()` üzerinde bir <xref:System.ServiceModel.ServiceHost> aşağıdaki kodda gösterildiği gibi hizmet ana bilgisayarını açma örneği.  
  
     [!code-csharp[htSoapWeb#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#5)]
     [!code-vb[htSoapWeb#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#5)]  
  
### <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a>Internet Explorer'da GET eşlenen hizmet işlemleri çağırmak için  
  
1.  Açık Internet Explorer ve türü "`http://localhost:8000/Web/EchoWithGet?s=Hello, world!`" ve ENTER tuşuna basın. Hizmetin taban adresi URL içerir ("http://localhost:8000/"), bitiş noktasının göreli adresi (""), hizmet işlemi çağrı ("EchoWithGet") ve bir soru işareti adlandırılmış parametreleri ampersan tarafından ayrılmış bir listesi ve ardından (&).  
  
### <a name="to-call-service-operations-on-the-web-endpoint-in-code"></a>Kod içinde hizmet işlemleri üzerinde Web uç noktası çağırmak için  
  
1.  Bir örneğini oluşturmak <xref:System.ServiceModel.Web.WebChannelFactory%601> içinde bir `using` aşağıdaki kodda gösterildiği gibi engelleyin.  
  
     [!code-csharp[htSoapWeb#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#6)]
     [!code-vb[htSoapWeb#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#6)]  
  
> [!NOTE]
>  `Close()` kanalda sonunda otomatik olarak çağrılır `using` bloğu.  
  
1.  Kanal oluşturun ve aşağıdaki kodda gösterildiği gibi hizmet çağırın.  
  
     [!code-csharp[htSoapWeb#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#8)]
     [!code-vb[htSoapWeb#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#8)]  
  
### <a name="to-call-service-operations-on-the-soap-endpoint"></a>SOAP uç noktasındaki hizmet işlemleri çağırmak için  
  
1.  Bir örneğini oluşturmak <xref:System.ServiceModel.ChannelFactory> içinde bir `using` aşağıdaki kodda gösterildiği gibi engelleyin.  
  
     [!code-csharp[htSoapWeb#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#10)]
     [!code-vb[htSoapWeb#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#10)]  
  
2.  Kanal oluşturun ve aşağıdaki kodda gösterildiği gibi hizmet çağırın.  
  
     [!code-csharp[htSoapWeb#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#11)]
     [!code-vb[htSoapWeb#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#11)]  
  
### <a name="to-close-the-service-host"></a>Hizmet ana bilgisayarı kapatmak için  
  
1.  Aşağıdaki kodda gösterildiği gibi hizmet ana bilgisayarını kapatın.  
  
     [!code-csharp[htSoapWeb#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#9)]
     [!code-vb[htSoapWeb#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#9)]  
  
## <a name="example"></a>Örnek  
 Bu konu için tam kod verilmiştir.  
  
 [!code-csharp[htSoapWeb#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#13)]
 [!code-vb[htSoapWeb#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#13)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Adını da derlerken System.ServiceModel.dll ve System.ServiceModel.Web.dll başvuru.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>  
 <xref:System.ServiceModel.Web.WebInvokeAttribute>  
 <xref:System.ServiceModel.Web.WebServiceHost>  
 <xref:System.ServiceModel.ChannelFactory>  
 <xref:System.ServiceModel.Description.WebHttpBehavior>  
 [WCF Web HTTP Programlama Modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
