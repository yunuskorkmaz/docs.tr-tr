---
title: "Nasıl yapılır: Çift Yönlü Sözleşme ile Hizmetlere Erişme"
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
helpviewer_keywords: duplex contracts [WCF]
ms.assetid: 746a9d64-f21c-426c-b85d-972e916ec6c5
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e4c273e674fb7cb0f2801d9858d598baab5973a6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-services-with-a-duplex-contract"></a>Nasıl yapılır: Çift Yönlü Sözleşme ile Hizmetlere Erişme
Bir özelliği [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] çift yönlü bir Mesajlaşma düzeni kullanan bir hizmet oluşturma yeteneği. Bu desen bir geri çağırma istemcinize ile iletişim kurmak bir hizmet sağlar. Bu konuda oluşturmaya yönelik adımlar gösterilmektedir bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] geri çağırma arabirimini uygulayan bir istemci sınıfı istemcisinde.  
  
 Bir çift bağlama hizmeti istemcinin IP adresini gösterir. İstemci, yalnızca Hizmetleri için güvenleri bağladığı emin olmak için güvenlik kullanmanız gerekir.  
  
 Temel bir oluşturma bir öğretici için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet ve istemci, bkz: [başlangıç Öğreticisi](../../../../docs/framework/wcf/getting-started-tutorial.md).  
  
### <a name="to-access-a-duplex-service"></a>Çift yönlü bir hizmete erişmek için  
  
1.  İki arabirim içeren bir hizmet oluşturun. İlk arabirimi hizmet için ikinci için geri çağırma. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]bkz. çift yönlü bir hizmet oluşturma [nasıl yapılır: çift yönlü sözleşme oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
2.  Hizmet çalıştırın.  
  
3.  Kullanım [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) sözleşmeleri (arabirimler) için istemci oluşturulamadı. Bunun nasıl yapılacağı hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir istemci oluşturmak](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).  
  
4.  Geri çağırma arabirimi, aşağıdaki örnekte gösterildiği gibi istemci sınıfında uygulayın.  
  
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
  
5.  Öğesinin bir örneğini oluşturur <xref:System.ServiceModel.InstanceContext> sınıfı. Oluşturucu istemci sınıfının bir örneğini gerektirir.  
  
    ```csharp  
    InstanceContext site = new InstanceContext(new CallbackHandler());  
    ```  
  
    ```vb  
    Dim site As InstanceContext = New InstanceContext(new CallbackHandler())  
    ```  
  
6.  Bir örneğini oluşturmak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gerektirir Oluşturucusu kullanılarak istemci bir <xref:System.ServiceModel.InstanceContext> nesnesi. Öğesinin ikinci parametresi oluşturucusu, yapılandırma dosyasında bulunan bir uç nokta adıdır.  
  
    ```csharp  
    CalculatorDuplexClient wcfClient =   
    new CalculatorDuplexClient(site, "default")  
    ```  
  
    ```vb  
    Dim wcfClient As New CalculatorDuplexClient(site, "default")  
    ```  
  
7.  Yöntemleri çağırma [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gerektiği gibi istemci.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde, çift yönlü sözleşme erişen istemci sınıfın nasıl oluşturulacağı gösterilmektedir.  
  
 [!code-csharp[S_DuplexClients#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_duplexclients/cs/client.cs#1)]
 [!code-vb[S_DuplexClients#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_duplexclients/vb/client.vb#1)]  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başlangıç Öğreticisi](../../../../docs/framework/wcf/getting-started-tutorial.md)  
 [Nasıl yapılır: çift yönlü sözleşme oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
 [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [Nasıl yapılır: bir istemci oluşturma](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [Nasıl yapılır: ChannelFactory kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)
