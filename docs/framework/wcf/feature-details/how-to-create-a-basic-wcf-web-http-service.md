---
title: 'Nasıl yapılır: Temel Bir WCF Web HTTP Hizmeti Oluşturma'
description: WCF 'de Web uç noktası sunan bir hizmetin nasıl oluşturulacağını öğrenin. Web uç noktaları, XML veya JSON kullanarak veri gönderir. SOAP Zarfı yok.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 877662d3-d372-4e08-b417-51f66a0095cd
ms.openlocfilehash: 7481367f27d973ba809dff5ca1c4a4f168fbbb98
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247110"
---
# <a name="how-to-create-a-basic-wcf-web-http-service"></a>Nasıl yapılır: Temel Bir WCF Web HTTP Hizmeti Oluşturma

Windows Communication Foundation (WCF), bir Web uç noktası sunan bir hizmet oluşturmanıza olanak sağlar. Web uç noktaları, verileri XML veya JSON ile gönderir, hiç SOAP Zarfı yoktur. Bu konuda, bu tür bir uç noktanın nasıl kullanılacağı gösterilmektedir.

> [!NOTE]
> Web uç noktasını güvenli hale getirmenin tek yolu, aktarım güvenliği kullanılarak HTTPS üzerinden kullanıma sunulmasıdır. İleti tabanlı güvenlik kullanırken, güvenlik bilgileri genellikle SOAP üst bilgilerine yerleştirilir ve SOAP olmayan uç noktalara gönderilen iletiler SOAP Zarfı içermediği için, güvenlik bilgilerinin yerleştirilmesi ve aktarım güvenliğine güvenmesi gerekir.

## <a name="to-create-a-web-endpoint"></a>Web uç noktası oluşturmak için

1. Ve öznitelikleri ile işaretlenmiş bir arabirim kullanarak bir hizmet sözleşmesi <xref:System.ServiceModel.ServiceContractAttribute> tanımlayın <xref:System.ServiceModel.Web.WebInvokeAttribute> <xref:System.ServiceModel.Web.WebGetAttribute> .

     [!code-csharp[htBasicService#0](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#0)]
     [!code-vb[htBasicService#0](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#0)]

    > [!NOTE]
    > Varsayılan olarak, <xref:System.ServiceModel.Web.WebInvokeAttribute> eşleme çağrıları işleme gönderisini. Ancak, bir "method =" parametresi belirterek, işleme eşlenecek HTTP yöntemini (örneğin, HEAD, PUT veya DELETE) belirtebilirsiniz. <xref:System.ServiceModel.Web.WebGetAttribute>"method =" parametresine sahip değildir ve yalnızca hizmet işlemine yapılan çağrıları eşler.

2. Hizmet sözleşmesini uygulayın.

     [!code-csharp[htBasicService#1](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#1)]
     [!code-vb[htBasicService#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#1)]

## <a name="to-host-the-service"></a>Hizmeti barındırmak için

1. Bir <xref:System.ServiceModel.Web.WebServiceHost> nesne oluşturun.

     [!code-csharp[htBasicService#2](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#2)]
     [!code-vb[htBasicService#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#2)]

2. İle bir ekleyin <xref:System.ServiceModel.Description.ServiceEndpoint> <xref:System.ServiceModel.Description.WebHttpBehavior> .

     [!code-csharp[htBasicService#3](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#3)]
     [!code-vb[htBasicService#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#3)]

    > [!NOTE]
    > Uç nokta eklemedıysanız, <xref:System.ServiceModel.Web.WebServiceHost> otomatik olarak varsayılan bir uç nokta oluşturur. <xref:System.ServiceModel.Web.WebServiceHost>Ayrıca, <xref:System.ServiceModel.Description.WebHttpBehavior> http yardım sayfasını ve Web Hizmetleri Açıklama Dili (wsdl) Al işlevini ekler ve devre dışı bırakır, böylece meta veri uç noktası varsayılan HTTP uç noktasına müdahale etmez.
    >
    >  "" URL 'SI ile SOAP olmayan bir uç nokta eklemek, uç noktada bir işlemi çağırmak için bir girişim yapıldığında beklenmeyen davranışlara neden olur. Bunun nedeni, uç noktanın dinleme URI 'si, yardım sayfasının URI 'siyle aynıdır (bir WCF hizmetinin temel adresine gözattığınızda görüntülenen sayfa).

     Bunun oluşmasını engellemek için aşağıdaki eylemlerden birini yapabilirsiniz:

    - SOAP olmayan bir uç nokta için her zaman boş olmayan bir URI belirtin.

    - Yardım sayfasını kapatın. Bu, aşağıdaki kodla yapılabilir:

     [!code-csharp[htBasicService#4](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#4)]
     [!code-vb[htBasicService#4](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#4)]

3. Hizmet konağını açın ve Kullanıcı ENTER tuşuna basana kadar bekleyin.

     [!code-csharp[htBasicService#5](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#5)]
     [!code-vb[htBasicService#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#5)]

     Bu örnek, bir konsol uygulamasıyla bir Web stili hizmetin nasıl barındırılacağını gösterir. Bu hizmeti IIS içinde de barındırabilirsiniz. Bunu yapmak için, <xref:System.ServiceModel.Activation.WebServiceHostFactory> aşağıdaki kodda gösterildiği gibi bir. svc dosyasında sınıfını belirtin.

    ```text
    <%ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Samples.Service"
        Factory=System.ServiceModel.Activation.WebServiceHostFactory%>
    ```

## <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a>Internet Explorer 'da almak üzere eşlenmiş hizmet işlemlerini çağırmak için

1. Internet Explorer 'ı açın ve " `http://localhost:8000/EchoWithGet?s=Hello, world!` " yazın ve ENTER tuşuna basın. URL, hizmetin temel adresini ( `http://localhost:8000/` ), uç noktanın göreli adresini (""), çağrı yapılacak hizmet işlemini ("yankı \ al") ve ardından bir ve işareti (&) ile ayrılmış adlandırılmış parametrelerin bir listesini içerir.

## <a name="to-call-service-operations-in-code"></a>Koddaki hizmet işlemlerini çağırmak için

1. <xref:System.ServiceModel.ChannelFactory%601>Bir blok içinde bir örnek oluşturun `using` .

     [!code-csharp[htBasicService#6](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#6)]
     [!code-vb[htBasicService#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#6)]

2. <xref:System.ServiceModel.Description.WebHttpBehavior>Çağrıları uç noktaya ekleyin <xref:System.ServiceModel.ChannelFactory%601> .

     [!code-csharp[htBasicService#7](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#7)]
     [!code-vb[htBasicService#7](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#7)]

3. Kanalı oluşturun ve hizmeti çağırın.

     [!code-csharp[htBasicService#8](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#8)]
     [!code-vb[htBasicService#8](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#8)]

4. Öğesini kapatın <xref:System.ServiceModel.Web.WebServiceHost> .

     [!code-csharp[htBasicService#9](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#9)]
     [!code-vb[htBasicService#9](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#9)]

## <a name="example"></a>Örnek

Bu örnek için tam kod listesi aşağıda verilmiştir.

[!code-csharp[htBasicService#10](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#10)]
[!code-vb[htBasicService#10](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#10)]

## <a name="compiling-the-code"></a>Kod derleme

Service.cs başvurusunu derlerken System.ServiceModel.dll ve System.ServiceModel.Web.dll.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
- <xref:System.ServiceModel.Web.WebInvokeAttribute>
- <xref:System.ServiceModel.Web.WebServiceHost>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [WCF Web HTTP Programlama Modeli](wcf-web-http-programming-model.md)
