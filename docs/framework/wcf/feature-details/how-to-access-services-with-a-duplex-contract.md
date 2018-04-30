---
title: 'Nasıl yapılır: Çift Yönlü Sözleşme ile Hizmetlere Erişme'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 746a9d64-f21c-426c-b85d-972e916ec6c5
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c80980ff5a5b1011c021bcaf0688747178ec5b9b
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-access-services-with-a-duplex-contract"></a><span data-ttu-id="5f6a5-102">Nasıl yapılır: Çift Yönlü Sözleşme ile Hizmetlere Erişme</span><span class="sxs-lookup"><span data-stu-id="5f6a5-102">How to: Access Services with a Duplex Contract</span></span>
<span data-ttu-id="5f6a5-103">Bir özelliği [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] çift yönlü bir Mesajlaşma düzeni kullanan bir hizmet oluşturma yeteneği.</span><span class="sxs-lookup"><span data-stu-id="5f6a5-103">One feature of [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is the ability to create a service that uses a duplex messaging pattern.</span></span> <span data-ttu-id="5f6a5-104">Bu desen bir geri çağırma istemcinize ile iletişim kurmak bir hizmet sağlar.</span><span class="sxs-lookup"><span data-stu-id="5f6a5-104">This pattern allows a service to communicate with the client through a callback.</span></span> <span data-ttu-id="5f6a5-105">Bu konuda oluşturmaya yönelik adımlar gösterilmektedir bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] geri çağırma arabirimini uygulayan bir istemci sınıfı istemcisinde.</span><span class="sxs-lookup"><span data-stu-id="5f6a5-105">This topic shows the steps to create a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client in a client class that implements the callback interface.</span></span>  
  
 <span data-ttu-id="5f6a5-106">Bir çift bağlama hizmeti istemcinin IP adresini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5f6a5-106">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="5f6a5-107">İstemci, yalnızca Hizmetleri için güvenleri bağladığı emin olmak için güvenlik kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5f6a5-107">The client should use security to ensure that it connects only to services it trusts.</span></span>  
  
 <span data-ttu-id="5f6a5-108">Temel bir oluşturma bir öğretici için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet ve istemci, bkz: [başlangıç Öğreticisi](../../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="5f6a5-108">For a tutorial on creating a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service and client, see [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span>  
  
### <a name="to-access-a-duplex-service"></a><span data-ttu-id="5f6a5-109">Çift yönlü bir hizmete erişmek için</span><span class="sxs-lookup"><span data-stu-id="5f6a5-109">To access a duplex service</span></span>  
  
1.  <span data-ttu-id="5f6a5-110">İki arabirim içeren bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5f6a5-110">Create a service that contains two interfaces.</span></span> <span data-ttu-id="5f6a5-111">İlk arabirimi hizmet için ikinci için geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="5f6a5-111">The first interface is for the service, the second is for the callback.</span></span> <span data-ttu-id="5f6a5-112">Çift yönlü bir hizmet oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: çift yönlü sözleşme oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="5f6a5-112">For more information about creating a duplex service, see [How to: Create a Duplex Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
2.  <span data-ttu-id="5f6a5-113">Hizmet çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5f6a5-113">Run the service.</span></span>  
  
3.  <span data-ttu-id="5f6a5-114">Kullanım [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) sözleşmeleri (arabirimler) için istemci oluşturulamadı.</span><span class="sxs-lookup"><span data-stu-id="5f6a5-114">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate contracts (interfaces) for the client.</span></span> <span data-ttu-id="5f6a5-115">Bunun nasıl yapılacağı hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir istemci oluşturmak](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="5f6a5-115">For information about how to do this, see  [How to: Create a Client](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>  
  
4.  <span data-ttu-id="5f6a5-116">Geri çağırma arabirimi, aşağıdaki örnekte gösterildiği gibi istemci sınıfında uygulayın.</span><span class="sxs-lookup"><span data-stu-id="5f6a5-116">Implement the callback interface in the client class, as shown in the following example.</span></span>  
  
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
  
5.  <span data-ttu-id="5f6a5-117">Öğesinin bir örneğini oluşturur <xref:System.ServiceModel.InstanceContext> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5f6a5-117">Create an instance of the <xref:System.ServiceModel.InstanceContext> class.</span></span> <span data-ttu-id="5f6a5-118">Oluşturucu istemci sınıfının bir örneğini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5f6a5-118">The constructor requires an instance of the client class.</span></span>  
  
    ```csharp  
    InstanceContext site = new InstanceContext(new CallbackHandler());  
    ```  
  
    ```vb  
    Dim site As InstanceContext = New InstanceContext(new CallbackHandler())  
    ```  
  
6.  <span data-ttu-id="5f6a5-119">Bir örneğini oluşturmak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gerektirir Oluşturucusu kullanılarak istemci bir <xref:System.ServiceModel.InstanceContext> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="5f6a5-119">Create an instance of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client using the constructor that requires an <xref:System.ServiceModel.InstanceContext> object.</span></span> <span data-ttu-id="5f6a5-120">Öğesinin ikinci parametresi oluşturucusu, yapılandırma dosyasında bulunan bir uç nokta adıdır.</span><span class="sxs-lookup"><span data-stu-id="5f6a5-120">The second parameter of the constructor is the name of an endpoint found in the configuration file.</span></span>  
  
    ```csharp  
    CalculatorDuplexClient wcfClient =   
    new CalculatorDuplexClient(site, "default")  
    ```  
  
    ```vb  
    Dim wcfClient As New CalculatorDuplexClient(site, "default")  
    ```  
  
7.  <span data-ttu-id="5f6a5-121">Yöntemleri çağırma [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gerektiği gibi istemci.</span><span class="sxs-lookup"><span data-stu-id="5f6a5-121">Call the methods of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client as required.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f6a5-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="5f6a5-122">Example</span></span>  
 <span data-ttu-id="5f6a5-123">Aşağıdaki kod örneğinde, çift yönlü sözleşme erişen istemci sınıfın nasıl oluşturulacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5f6a5-123">The following code example demonstrates how to create a client class that accesses a duplex contract.</span></span>  
  
 [!code-csharp[S_DuplexClients#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_duplexclients/cs/client.cs#1)]
 [!code-vb[S_DuplexClients#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_duplexclients/vb/client.vb#1)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="5f6a5-124">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="5f6a5-124">.NET Framework Security</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f6a5-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5f6a5-125">See Also</span></span>  
 [<span data-ttu-id="5f6a5-126">Başlangıç Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="5f6a5-126">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)  
 [<span data-ttu-id="5f6a5-127">Nasıl yapılır: Çift Yönlü Anlaşma Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5f6a5-127">How to: Create a Duplex Contract</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
 [<span data-ttu-id="5f6a5-128">ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="5f6a5-128">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [<span data-ttu-id="5f6a5-129">Nasıl yapılır: İstemci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5f6a5-129">How to: Create a Client</span></span>](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [<span data-ttu-id="5f6a5-130">Nasıl yapılır: ChannelFactory Kullanma</span><span class="sxs-lookup"><span data-stu-id="5f6a5-130">How to: Use the ChannelFactory</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)
