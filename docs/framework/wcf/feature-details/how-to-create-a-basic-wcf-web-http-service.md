---
title: "Nasıl yapılır: Temel Bir WCF Web HTTP Hizmeti Oluşturma"
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
ms.assetid: 877662d3-d372-4e08-b417-51f66a0095cd
caps.latest.revision: "26"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8352c7761447322d1ddf8381be145e38d6b7df8d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-basic-wcf-web-http-service"></a>Nasıl yapılır: Temel Bir WCF Web HTTP Hizmeti Oluşturma
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]bir Web uç noktası kullanıma sunan bir hizmet oluşturmanıza olanak sağlar. Web uç noktaları XML veya JSON veri gönderme, SOAP Zarfı. Bu konu, bu tür bir uç nokta kullanıma gösterilmiştir.  
  
> [!NOTE]
>  Taşıma güvenliği kullanarak, HTTPS kullanıma sunmak için yalnızca bir Web uç noktası güvenli şekilde denetleyebilirsiniz. İleti tabanlı güvenlik kullanırken, güvenlik bilgileri genellikle SOAP üstbilgileri yerleştirilir ve gönderilen iletiler için hiç SOAP Zarfı olmayan SOAP uç noktaları içeren, saklanıyorsa güvenlik bilgilerini yerleştirmek için yoktur ve aktarım güvenliğe güvenmesi gerekir.  
  
### <a name="to-create-a-web-endpoint"></a>Bir Web uç noktası oluşturmak için  
  
1.  İle işaretlenen arabirimini kullanarak bir hizmet sözleşmesini tanımlayan <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> ve <xref:System.ServiceModel.Web.WebGetAttribute> öznitelikleri.  
  
     [!code-csharp[htBasicService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#0)]
     [!code-vb[htBasicService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#0)]  
  
    > [!NOTE]
    >  Varsayılan olarak, <xref:System.ServiceModel.Web.WebInvokeAttribute> işlemi POST çağrıları eşler. Bununla birlikte, çalışması için belirterek eşleştirmek için HTTP yöntemini (örneğin, HEAD, PUT veya Sil) belirleyebilirsiniz bir "yöntemi =" parametresi. <xref:System.ServiceModel.Web.WebGetAttribute>sahip olmayan bir "yöntemi =" GET parametre ve yalnızca eşlemeleri hizmet işlemini çağırır.  
  
2.  Hizmet sözleşmesini uygulama.  
  
     [!code-csharp[htBasicService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#1)]
     [!code-vb[htBasicService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#1)]  
  
### <a name="to-host-the-service"></a>Ana bilgisayar hizmeti  
  
1.  Oluşturma bir <xref:System.ServiceModel.Web.WebServiceHost> nesnesi.  
  
     [!code-csharp[htBasicService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#2)]
     [!code-vb[htBasicService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#2)]  
  
2.  Ekleme bir <xref:System.ServiceModel.Description.ServiceEndpoint> ile <xref:System.ServiceModel.Description.WebHttpBehavior>.  
  
     [!code-csharp[htBasicService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#3)]
     [!code-vb[htBasicService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#3)]  
  
    > [!NOTE]
    >  Bir uç nokta eklemezseniz <xref:System.ServiceModel.Web.WebServiceHost> otomatik olarak varsayılan uç noktası oluşturur. <xref:System.ServiceModel.Web.WebServiceHost>Ayrıca ekler <xref:System.ServiceModel.Description.WebHttpBehavior> ve meta veri uç noktasının varsayılan HTTP uç noktası ile etkilemediğinden için HTTP yardım sayfasına ve Web Hizmetleri Açıklama Dili (WSDL) alma işlevini devre dışı bırakır.  
    >   
    >  SOAP olmayan uç nokta URL'si ile ekleme "" uç nokta üzerinde bir işlemi çağırmak için bir girişimde beklenmeyen davranışlara neden olur. Bu uç nokta URI'sini dinleme aynıdır yardım sayfasına URI'sini nedeni (temel adresine göz atarken görüntülenen sayfa bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmeti).  
  
     Bunun olmaması için aşağıdaki işlemlerden birini yapabilirsiniz:  
  
    -   Her zaman bir SOAP olmayan uç noktası için boş olmayan URI belirtin.  
  
    -   Yardım sayfasını kapat. Bu, aşağıdaki kod ile yapılabilir.  
  
     [!code-csharp[htBasicService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#4)]
     [!code-vb[htBasicService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#4)]  
  
3.  Hizmet ana bilgisayarı'nı açın ve kullanıcı ENTER tuşuna bastığında kadar bekleyin.  
  
     [!code-csharp[htBasicService#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#5)]
     [!code-vb[htBasicService#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#5)]  
  
     Bu örnek, bir konsol uygulaması ile Web stili hizmeti barındırma gösterilmiştir. Ayrıca, bu tür bir hizmet IIS içinde barındırabilir. Bunu yapmak için belirtmek <xref:System.ServiceModel.Activation.WebServiceHostFactory> aşağıdaki kodda gibi .svc dosyasında sınıfı.  
  
    ```  
          <%ServiceHost   
    language=c#  
    Debug="true"  
    Service="Microsoft.Samples.Service"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory%>  
    ```  
  
### <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a>Internet Explorer'da GET eşlenen hizmet işlemleri çağırmak için  
  
1.  Açık Internet Explorer ve türü "`http://localhost:8000/EchoWithGet?s=Hello, world!`" ve ENTER tuşuna basın. Hizmetin taban adresi URL içerir ("8000 /"), bitiş noktasının göreli adresi (""), hizmet işlemi çağrı ("EchoWithGet") ve bir soru işareti adlandırılmış parametreleri ampersan tarafından ayrılmış bir listesi ve ardından (&).  
  
### <a name="to-call-service-operations-in-code"></a>Kod içinde hizmet işlemleri çağırmak için  
  
1.  Bir örneğini oluşturmak <!--zz <xref:System.ServiceModel.Web.WebChannelFactory>--> `System.ServiceModel.Web.WebChannelFactory` içinde bir `using` bloğu.  
  
     [!code-csharp[htBasicService#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#6)]
     [!code-vb[htBasicService#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#6)]  
  
2.  Ekleme <xref:System.ServiceModel.Description.WebHttpBehavior> uç <xref:System.ServiceModel.ChannelFactory> çağrıları.  
  
     [!code-csharp[htBasicService#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#7)]
     [!code-vb[htBasicService#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#7)]  
  
3.  Kanal oluşturmak ve hizmet çağırın.  
  
     [!code-csharp[htBasicService#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#8)]
     [!code-vb[htBasicService#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#8)]  
  
4.  Kapat <xref:System.ServiceModel.Web.WebServiceHost>.  
  
     [!code-csharp[htBasicService#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#9)]
     [!code-vb[htBasicService#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#9)]  
  
## <a name="example"></a>Örnek  
 Bu örnek için listeleme tam kod aşağıda verilmiştir.  
  
 [!code-csharp[htBasicService#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#10)]
 [!code-vb[htBasicService#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#10)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Adını da başvuru System.ServiceModel.dll ve System.ServiceModel.Web.dll derlerken.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>  
 <xref:System.ServiceModel.Web.WebInvokeAttribute>  
 <xref:System.ServiceModel.Web.WebServiceHost>  
 <xref:System.ServiceModel.Description.WebHttpBehavior>  
 [WCF Web HTTP programlama modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
