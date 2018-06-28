---
title: 'Nasıl yapılır: çift yönlü sözleşme ile hizmetlere erişme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 746a9d64-f21c-426c-b85d-972e916ec6c5
ms.openlocfilehash: 6675da079b343b1b80477c65260ee8a1f44df72a
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37027908"
---
# <a name="how-to-access-services-with-a-duplex-contract"></a>Nasıl yapılır: çift yönlü sözleşme ile hizmetlere erişme

Bir Windows Communication Foundation (WCF) çift yönlü bir Mesajlaşma düzeni kullanan bir hizmet oluşturma yeteneği özelliğidir. Bu desen bir geri çağırma istemcinize ile iletişim kurmak bir hizmet sağlar. Bu konu geri çağırma arabirimini uygulayan bir istemci sınıfta bir WCF istemcisi oluşturma adımlarını gösterir.

Bir çift bağlama hizmeti istemcinin IP adresini gösterir. İstemci, yalnızca Hizmetleri için güvenleri bağladığı emin olmak için güvenlik kullanmanız gerekir.

Temel WCF hizmeti ve istemci oluşturma bir öğretici için bkz: [başlangıç Öğreticisi](../../../../docs/framework/wcf/getting-started-tutorial.md).

## <a name="to-access-a-duplex-service"></a>Çift yönlü bir hizmete erişmek için

1. İki arabirim içeren bir hizmet oluşturun. İlk arabirimi hizmet için ikinci için geri çağırma. Çift yönlü bir hizmet oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: çift yönlü sözleşme oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).

2. Hizmet çalıştırın.

3. Kullanım [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) sözleşmeleri (arabirimler) için istemci oluşturulamadı. Bunun nasıl yapılacağı hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir istemci oluşturmak](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).

4. Geri çağırma arabirimi, aşağıdaki örnekte gösterildiği gibi istemci sınıfında uygulayın.

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

6. Gerektirir Oluşturucusu kullanarak WCF istemci örneğini oluşturmak bir <xref:System.ServiceModel.InstanceContext> nesnesi. Öğesinin ikinci parametresi oluşturucusu, yapılandırma dosyasında bulunan bir uç nokta adıdır.

    ```csharp
    CalculatorDuplexClient wcfClient = new CalculatorDuplexClient(site, "default");
    ```

    ```vb
    Dim wcfClient As New CalculatorDuplexClient(site, "default")
    ```

7. WCF istemcisi gerekli olarak yöntemlerini çağırın.

## <a name="example"></a>Örnek

Aşağıdaki kod örneğinde, çift yönlü sözleşme erişen istemci sınıfın nasıl oluşturulacağı gösterilmektedir.

[!code-csharp[S_DuplexClients#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_duplexclients/cs/client.cs#1)]
[!code-vb[S_DuplexClients#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_duplexclients/vb/client.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

[Başlangıç Öğreticisi](../../../../docs/framework/wcf/getting-started-tutorial.md)  
[Nasıl yapılır: Çift Yönlü Anlaşma Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
[ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
[Nasıl yapılır: İstemci Oluşturma](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
[Nasıl yapılır: ChannelFactory Kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)
