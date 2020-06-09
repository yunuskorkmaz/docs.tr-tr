---
title: 'Nasıl yapılır: çift yönlü sözleşme ile hizmetlere erişme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 746a9d64-f21c-426c-b85d-972e916ec6c5
ms.openlocfilehash: bc42792b827b49265a0b1addf959de2fa1a041e3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597221"
---
# <a name="how-to-access-services-with-a-duplex-contract"></a>Nasıl yapılır: çift yönlü sözleşme ile hizmetlere erişme

Windows Communication Foundation (WCF) özelliğinin bir özelliği, çift yönlü mesajlaşma modelini kullanan bir hizmet oluşturma olanağıdır. Bu model, bir hizmetin geri çağırma yoluyla istemciyle iletişim kurmasına olanak tanır. Bu konuda, geri çağırma arabirimini uygulayan bir istemci sınıfında bir WCF istemcisi oluşturma adımları gösterilmektedir.

İkili bağlama, istemcinin IP adresini hizmete gösterir. İstemci, yalnızca güvendiği hizmetlere bağlanmasını sağlamak için güvenliği kullanmalıdır.

Temel bir WCF hizmeti ve istemcisi oluşturmaya yönelik bir öğretici için bkz. [Başlangıç Öğreticisi](../getting-started-tutorial.md).

## <a name="to-access-a-duplex-service"></a>Çift yönlü hizmete erişmek için

1. İki arabirim içeren bir hizmet oluşturun. İlk arabirim hizmet içindir, ikincisi geri arama içindir. Çift yönlü hizmet oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: çift yönlü sözleşme oluşturma](how-to-create-a-duplex-contract.md).

2. Hizmeti çalıştırın.

3. İstemci için sözleşmeler (arabirimler) oluşturmak üzere [ServiceModel meta veri yardımcı programı aracını (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) kullanın. Bunun nasıl yapılacağı hakkında bilgi için bkz. [nasıl yapılır: Istemci oluşturma](../how-to-create-a-wcf-client.md).

4. Aşağıdaki örnekte gösterildiği gibi, istemci sınıfında geri çağırma arabirimini uygulayın.

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
            Console.WriteLine("Equation({0})", equation)
        End Sub
    End Class
    ```

5. Öğesinin bir örneğini oluşturur <xref:System.ServiceModel.InstanceContext> sınıfı. Oluşturucu, istemci sınıfının bir örneğini gerektirir.

    ```csharp
    InstanceContext site = new InstanceContext(new CallbackHandler());
    ```

    ```vb
    Dim site As InstanceContext = New InstanceContext(new CallbackHandler())
    ```

6. Bir nesne gerektiren oluşturucuyu kullanarak WCF istemcisinin bir örneğini oluşturun <xref:System.ServiceModel.InstanceContext> . Oluşturucunun ikinci parametresi, yapılandırma dosyasında bulunan bir uç noktanın adıdır.

    ```csharp
    CalculatorDuplexClient wcfClient = new CalculatorDuplexClient(site, "default");
    ```

    ```vb
    Dim wcfClient As New CalculatorDuplexClient(site, "default")
    ```

7. WCF istemcisinin yöntemlerini gereken şekilde çağırın.

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, çift yönlü bir sözleşmeye erişen bir istemci sınıfının nasıl oluşturulacağını göstermektedir.

[!code-csharp[S_DuplexClients#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_duplexclients/cs/client.cs#1)]
[!code-vb[S_DuplexClients#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_duplexclients/vb/client.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

- [Başlangıç Öğreticisi](../getting-started-tutorial.md)
- [Nasıl yapılır: Çift Yönlü Sözleşme Oluşturma](how-to-create-a-duplex-contract.md)
- [ServiceModel Meta Veri Yardımcı Programracı (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Nasıl yapılır: İstemci Oluşturma](../how-to-create-a-wcf-client.md)
- [Nasıl yapılır: ChannelFactory Kullanma](how-to-use-the-channelfactory.md)
