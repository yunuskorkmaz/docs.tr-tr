---
title: 'Nasıl yapılır: Bir Sözleşmeyi SOAP ve Web İstemcilerine Sunma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: bb765a48-12f2-430d-a54d-6f0c20f2a23a
ms.openlocfilehash: fa02260976c710401a05cce3d723cc0f66804c6e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593139"
---
# <a name="how-to-expose-a-contract-to-soap-and-web-clients"></a>Nasıl yapılır: Bir Sözleşmeyi SOAP ve Web İstemcilerine Sunma

Varsayılan olarak, Windows Communication Foundation (WCF) uç noktaları yalnızca SOAP istemcileri için kullanılabilir hale getirir. [Nasıl yapılır: temel BIR WCF Web http hizmeti oluşturma](how-to-create-a-basic-wcf-web-http-service.md)bölümünde, soap olmayan istemciler için bir uç nokta kullanılabilir hale getirilir. Aynı sözleşmeyi bir Web uç noktası ve bir SOAP uç noktası olarak her iki şekilde de kullanılabilir hale getirmek istediğiniz zamanlar olabilir. Bu konu, bunun nasıl yapılacağını gösteren bir örnek gösterir.

## <a name="to-define-the-service-contract"></a>Hizmet sözleşmesini tanımlamak için

1. <xref:System.ServiceModel.ServiceContractAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> Aşağıdaki kodda gösterildiği gibi, ve öznitelikleri ile işaretlenmiş bir arabirim kullanarak bir hizmet sözleşmesi tanımlayın <xref:System.ServiceModel.Web.WebGetAttribute> :

    [!code-csharp[htSoapWeb#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#0)]
    [!code-vb[htSoapWeb#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#0)]

    > [!NOTE]
    > Varsayılan olarak <xref:System.ServiceModel.Web.WebInvokeAttribute> , işleme yapılan çağrıları eşler. Bununla birlikte, bir "method =" parametresi belirterek, işleme eşlemek için yöntemi belirleyebilirsiniz. <xref:System.ServiceModel.Web.WebGetAttribute>"method =" parametresine sahip değildir ve yalnızca hizmet işlemine yapılan çağrıları eşler.

2. Aşağıdaki kodda gösterildiği gibi hizmet sözleşmesini uygulayın:

     [!code-csharp[htSoapWeb#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#1)]
     [!code-vb[htSoapWeb#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#1)]

## <a name="to-host-the-service"></a>Hizmeti barındırmak için

1. <xref:System.ServiceModel.ServiceHost>Aşağıdaki kodda gösterildiği gibi bir nesne oluşturun:

     [!code-csharp[htSoapWeb#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#2)]
     [!code-vb[htSoapWeb#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#2)]

2. <xref:System.ServiceModel.Description.ServiceEndpoint> <xref:System.ServiceModel.BasicHttpBinding> SOAP uç noktası için aşağıdaki kodda gösterildiği gibi bir ile ekleyin:

     [!code-csharp[htSoapWeb#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#3)]
     [!code-vb[htSoapWeb#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#3)]

3. <xref:System.ServiceModel.Description.ServiceEndpoint> <xref:System.ServiceModel.WebHttpBinding> SOAP olmayan uç nokta için bir ile ekleyin ve <xref:System.ServiceModel.Description.WebHttpBehavior> aşağıdaki kodda gösterildiği gibi uç noktaya ekleyin:

     [!code-csharp[htSoapWeb#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#4)]
     [!code-vb[htSoapWeb#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#4)]

4. `Open()` <xref:System.ServiceModel.ServiceHost> Aşağıdaki kodda gösterildiği gibi, hizmet ana bilgisayarını açmak için bir örneği çağırın:

     [!code-csharp[htSoapWeb#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#5)]
     [!code-vb[htSoapWeb#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#5)]

## <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a>Internet Explorer 'da almak üzere eşlenmiş hizmet işlemlerini çağırmak için

1. Internet Explorer 'ı açın ve " `http://localhost:8000/Web/EchoWithGet?s=Hello, world!` " yazın ve ENTER tuşuna basın. URL, hizmetin temel adresini ( `http://localhost:8000/` ), uç noktanın göreli adresini (""), çağrı yapılacak hizmet işlemini ("yankı \ al") ve ardından bir ve işareti (&) ile ayrılmış adlandırılmış parametrelerin bir listesini içerir.

## <a name="to-call-service-operations-on-the-web-endpoint-in-code"></a>Koddaki Web uç noktasında hizmet işlemlerini çağırmak için

1. <xref:System.ServiceModel.Web.WebChannelFactory%601>Aşağıdaki kodda gösterildiği gibi bir blok içinde öğesinin bir örneğini oluşturun `using` .

     [!code-csharp[htSoapWeb#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#6)]
     [!code-vb[htSoapWeb#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#6)]

> [!NOTE]
> `Close()`, blok sonundaki kanalda otomatik olarak çağrılır `using` .

1. Aşağıdaki kodda gösterildiği gibi kanalı oluşturun ve hizmeti çağırın.

     [!code-csharp[htSoapWeb#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#8)]
     [!code-vb[htSoapWeb#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#8)]

## <a name="to-call-service-operations-on-the-soap-endpoint"></a>SOAP uç noktasındaki hizmet işlemlerini çağırmak için

1. <xref:System.ServiceModel.ChannelFactory>Aşağıdaki kodda gösterildiği gibi bir blok içinde öğesinin bir örneğini oluşturun `using` .

    [!code-csharp[htSoapWeb#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#10)]
    [!code-vb[htSoapWeb#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#10)]

2. Aşağıdaki kodda gösterildiği gibi kanalı oluşturun ve hizmeti çağırın.

    [!code-csharp[htSoapWeb#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#11)]
    [!code-vb[htSoapWeb#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#11)]

## <a name="to-close-the-service-host"></a>Hizmet konağını kapatmak için

1. Aşağıdaki kodda gösterildiği gibi hizmet ana bilgisayarını kapatın.

    [!code-csharp[htSoapWeb#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#9)]
    [!code-vb[htSoapWeb#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#9)]

## <a name="example"></a>Örnek

Aşağıda, bu konunun tam kod listesi verilmiştir:

[!code-csharp[htSoapWeb#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#13)]
[!code-vb[htSoapWeb#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#13)]

## <a name="compiling-the-code"></a>Kod derleme

 Service.cs derlenirken, System. ServiceModel. dll ve System. ServiceModel. Web. dll dosyasına başvurun.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
- <xref:System.ServiceModel.Web.WebInvokeAttribute>
- <xref:System.ServiceModel.Web.WebServiceHost>
- <xref:System.ServiceModel.ChannelFactory>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [WCF Web HTTP Programlama Modeli](wcf-web-http-programming-model.md)
