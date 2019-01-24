---
title: 'Nasıl yapılır: Çift yönlü sözleşme ile hizmetlere erişim'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 746a9d64-f21c-426c-b85d-972e916ec6c5
ms.openlocfilehash: 2f83b8ac71bfc53791f7de42d127badbda0d3881
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54610322"
---
# <a name="how-to-access-services-with-a-duplex-contract"></a>Nasıl yapılır: Çift yönlü sözleşme ile hizmetlere erişim

Bir Windows Communication Foundation (WCF) çift yönlü bir Mesajlaşma deseni kullanan bir hizmet oluşturma yeteneği özelliğidir. Bu düzen, bir geri çağırma aracılığıyla istemcisi ile iletişim kurmak bir hizmet sağlar. Bu konuda, geri arama arabirimini uygulayan bir istemci sınıfta bir WCF istemcisi oluşturma adımları gösterilmektedir.

İkili bir bağlama hizmeti için istemci IP adresi sunar. İstemci, yalnızca Hizmetleri için güvenleri bağladığı emin olmak için güvenlik kullanmanız gerekir.

Temel WCF hizmeti ve istemci oluşturmaya ilişkin öğretici için bkz: [başlangıç Öğreticisi](../../../../docs/framework/wcf/getting-started-tutorial.md).

## <a name="to-access-a-duplex-service"></a>Çift yönlü bir hizmete erişmek için

1. İki arabirim içeren bir hizmet oluşturursunuz. İlk arabirim hizmet için ikinci için geri çağırma. Çift yönlü bir hizmet oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Çift yönlü sözleşme oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).

2. Hizmet çalıştırın.

3. Kullanım [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) sözleşmelerinin (arabirimleri) istemcisi oluşturmak için. Bunun nasıl yapılacağı hakkında daha fazla bilgi için bkz. [nasıl yapılır: Bir istemci oluşturmanız](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).

4. Geri arama arabirimini istemci sınıfında, aşağıdaki örnekte gösterildiği gibi uygulayın.

    ```csharp
    public class CallbackHandler : ICalculatorDuplexCallback
    {
        public void Result(double result)
        {
            Console.WriteLine("Result ({0})", result);
        }
        public void Equation(string equation)
        {
            Console.WriteLine("Equation({0})", equation);
        }
    }
    ```

    ```vb
    Public Class CallbackHandler
    Implements ICalculatorDuplexCallback
       Public Sub Result (ByVal result As Double)
          Console.WriteLine("Result ({0})", result)
       End Sub
        Public Sub Equation(ByVal equation As String)
            Console.Writeline("Equation({0})", equation)
        End Sub
    End Class
    ```

5. Öğesinin bir örneğini oluşturur <xref:System.ServiceModel.InstanceContext> sınıfı. Oluşturucu istemci sınıfının bir örneğini gerektirir.

    ```csharp
    InstanceContext site = new InstanceContext(new CallbackHandler());
    ```

    ```vb
    Dim site As InstanceContext = New InstanceContext(new CallbackHandler())
    ```

6. Gerektiren oluşturucuyu kullanarak WCF istemci örneği oluşturun bir <xref:System.ServiceModel.InstanceContext> nesne. İkinci oluşturucu parametresi yapılandırma dosyasında bulunan bir uç nokta adıdır.

    ```csharp
    CalculatorDuplexClient wcfClient = new CalculatorDuplexClient(site, "default");
    ```

    ```vb
    Dim wcfClient As New CalculatorDuplexClient(site, "default")
    ```

7. WCF istemcisi gerektiği gibi'nin yöntemlerini çağırabilirsiniz.

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, çift yönlü sözleşme erişen istemci sınıf oluşturma işlemini gösterir.

[!code-csharp[S_DuplexClients#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_duplexclients/cs/client.cs#1)]
[!code-vb[S_DuplexClients#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_duplexclients/vb/client.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

- [Başlangıç Öğreticisi](../../../../docs/framework/wcf/getting-started-tutorial.md)
- [Nasıl yapılır: Çift yönlü sözleşme oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
- [ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Nasıl yapılır: Bir istemci oluşturma](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [Nasıl yapılır: ChannelFactory kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)
