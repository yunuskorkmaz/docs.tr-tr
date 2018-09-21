---
title: 'Nasıl yapılır: Temel Bir WCF Web HTTP Hizmeti Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 877662d3-d372-4e08-b417-51f66a0095cd
ms.openlocfilehash: 1b76d21cb4f416aae76e7597ad16cfd45e5b7cad
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46532434"
---
# <a name="how-to-create-a-basic-wcf-web-http-service"></a>Nasıl yapılır: Temel Bir WCF Web HTTP Hizmeti Oluşturma

Windows Communication Foundation (WCF), bir Web uç noktası hizmetidir oluşturmanıza olanak sağlar. Hiç SOAP Zarfı olduğunda, XML veya JSON veri Web uç gönderin. Bu konuda, bu tür bir uç noktanın kullanıma gösterilmiştir.

> [!NOTE]
> Yalnızca bir Web uç noktası güvenli şekilde bunu aktarım güvenliği kullanarak HTTPS kullanıma sağlamaktır. İleti tabanlı güvenlik kullanırken, güvenlik bilgileri genellikle SOAP üst bilgilerinde yerleştirilir ve gönderilen iletiler için hiç SOAP Zarfı olmayan SOAP uç noktaları içeren saklanıyorsa güvenlik bilgilerini yerleştirmek için yoktur ve aktarım güvenliği kullanmanız gerekir.

## <a name="to-create-a-web-endpoint"></a>Bir Web uç noktası oluşturma

1. İle işaretlenmiş bir arabirim kullanarak bir hizmet sözleşmesini tanımlama <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> ve <xref:System.ServiceModel.Web.WebGetAttribute> öznitelikleri.

     [!code-csharp[htBasicService#0](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#0)]
     [!code-vb[htBasicService#0](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#0)]

    > [!NOTE]
    > Varsayılan olarak, <xref:System.ServiceModel.Web.WebInvokeAttribute> işlemi POST çağrısına eşler. Ancak, işlemi belirterek eşleştirmek için HTTP yöntemini (örneğin, HEAD, PUT veya Sil) belirtebilirsiniz bir "yöntemi =" parametresi. <xref:System.ServiceModel.Web.WebGetAttribute> olmayan bir "yöntemi =" parametresi ve yalnızca eşlemeler GET hizmet işlemine çağırır.

2. Hizmet sözleşmesini uygulama.

     [!code-csharp[htBasicService#1](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#1)]
     [!code-vb[htBasicService#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#1)]

## <a name="to-host-the-service"></a>Ana bilgisayar hizmeti

1. Oluşturma bir <xref:System.ServiceModel.Web.WebServiceHost> nesne.

     [!code-csharp[htBasicService#2](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#2)]
     [!code-vb[htBasicService#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#2)]

2. Ekleme bir <xref:System.ServiceModel.Description.ServiceEndpoint> ile <xref:System.ServiceModel.Description.WebHttpBehavior>.

     [!code-csharp[htBasicService#3](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#3)]
     [!code-vb[htBasicService#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#3)]

    > [!NOTE]
    > Bir uç nokta eklemezseniz <xref:System.ServiceModel.Web.WebServiceHost> otomatik olarak bir varsayılan uç noktası oluşturur. <xref:System.ServiceModel.Web.WebServiceHost> Ayrıca ekler <xref:System.ServiceModel.Description.WebHttpBehavior> ve meta veri uç noktasının varsayılan HTTP uç noktası ile aksatmaz için HTTP yardım sayfasına ve Web Hizmetleri Açıklama Dili (WSDL) alma işlevselliğini devre dışı bırakır.
    >
    >  Bir URL ile bir olmayan SOAP uç noktası ekleme "" uç noktasında bir işlemi çağırma girişimi yapıldığında beklenmeyen davranışlara neden olur. Bunun nedeni, uç nokta URI'si (temel bir WCF Hizmeti adresine göz atarken görüntülenen sayfa) yardım sayfasına URI'sini aynıdır dinleme ' dir.

     Bunun gerçekleşmesini önlemek için aşağıdaki işlemlerden birini yapabilirsiniz:

    - Her zaman bir olmayan SOAP uç noktası için boş olmayan URI belirtin.

    - Yardım sayfasını kapat. Bu, aşağıdaki kod ile yapılabilir:

     [!code-csharp[htBasicService#4](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#4)]
     [!code-vb[htBasicService#4](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#4)]

3. Hizmet ana bilgisayarı'nı açın ve kullanıcı ENTER tuşuna bastığında kadar bekleyin.

     [!code-csharp[htBasicService#5](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#5)]
     [!code-vb[htBasicService#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#5)]

     Bu örnek bir konsol uygulaması ile Web stili hizmet barındırmak nasıl gösterir. Ayrıca, böyle bir hizmet IIS içinde barındırabilirsiniz. Bunu yapmak için belirtin <xref:System.ServiceModel.Activation.WebServiceHostFactory> .svc dosyasında aşağıdaki kodun gösterdiği gibi sınıf.

    ```
    <%ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Samples.Service"
        Factory=System.ServiceModel.Activation.WebServiceHostFactory%>
    ```

## <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a>Internet Explorer'da GET eşlenen hizmet işlemlerini aramak üzere

1. Internet Explorer ve tür açın "`http://localhost:8000/EchoWithGet?s=Hello, world!`" ve ENTER tuşuna basın. Hizmetin taban adresi URL içerir (`http://localhost:8000/`), ilgili uç nokta adresi (""), hizmet işlemine çağrı ("EchoWithGet") yanı sıra, bir soru işareti ve işareti tarafından ayrılmış, adlandırılan parametrelerin bir listesi ve ardından (&).

## <a name="to-call-service-operations-in-code"></a>Kod içinde hizmet işlemlerini aramak üzere

1. Bir örneğini oluşturmak <xref:System.ServiceModel.ChannelFactory%601> içinde bir `using` blok.

     [!code-csharp[htBasicService#6](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#6)]
     [!code-vb[htBasicService#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#6)]

2. Ekleme <xref:System.ServiceModel.Description.WebHttpBehavior> uç noktasına <xref:System.ServiceModel.ChannelFactory%601> çağırır.

     [!code-csharp[htBasicService#7](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#7)]
     [!code-vb[htBasicService#7](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#7)]

3. Bir kanal oluşturmak ve hizmet çağırın.

     [!code-csharp[htBasicService#8](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#8)]
     [!code-vb[htBasicService#8](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#8)]

4. Kapat <xref:System.ServiceModel.Web.WebServiceHost>.

     [!code-csharp[htBasicService#9](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#9)]
     [!code-vb[htBasicService#9](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#9)]

## <a name="example"></a>Örnek

Bu örnek için listeleme tam kod aşağıda verilmiştir.

[!code-csharp[htBasicService#10](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#10)]
[!code-vb[htBasicService#10](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#10)]

## <a name="compiling-the-code"></a>Kod derleme

Adını da başvuru System.ServiceModel.dll ve System.ServiceModel.Web.dll derlenirken.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
- <xref:System.ServiceModel.Web.WebInvokeAttribute>
- <xref:System.ServiceModel.Web.WebServiceHost>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [WCF Web HTTP Programlama Modeli](wcf-web-http-programming-model.md)