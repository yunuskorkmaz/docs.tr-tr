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
# <a name="how-to-access-services-with-a-duplex-contract"></a><span data-ttu-id="f9f8c-102">Nasıl yapılır: Çift yönlü sözleşme ile hizmetlere erişim</span><span class="sxs-lookup"><span data-stu-id="f9f8c-102">How to: Access services with a duplex contract</span></span>

<span data-ttu-id="f9f8c-103">Bir Windows Communication Foundation (WCF) çift yönlü bir Mesajlaşma deseni kullanan bir hizmet oluşturma yeteneği özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="f9f8c-103">One feature of Windows Communication Foundation (WCF) is the ability to create a service that uses a duplex messaging pattern.</span></span> <span data-ttu-id="f9f8c-104">Bu düzen, bir geri çağırma aracılığıyla istemcisi ile iletişim kurmak bir hizmet sağlar.</span><span class="sxs-lookup"><span data-stu-id="f9f8c-104">This pattern allows a service to communicate with the client through a callback.</span></span> <span data-ttu-id="f9f8c-105">Bu konuda, geri arama arabirimini uygulayan bir istemci sınıfta bir WCF istemcisi oluşturma adımları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f9f8c-105">This topic shows the steps to create a WCF client in a client class that implements the callback interface.</span></span>

<span data-ttu-id="f9f8c-106">İkili bir bağlama hizmeti için istemci IP adresi sunar.</span><span class="sxs-lookup"><span data-stu-id="f9f8c-106">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="f9f8c-107">İstemci, yalnızca Hizmetleri için güvenleri bağladığı emin olmak için güvenlik kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f9f8c-107">The client should use security to ensure that it connects only to services it trusts.</span></span>

<span data-ttu-id="f9f8c-108">Temel WCF hizmeti ve istemci oluşturmaya ilişkin öğretici için bkz: [başlangıç Öğreticisi](../../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="f9f8c-108">For a tutorial on creating a basic WCF service and client, see [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span>

## <a name="to-access-a-duplex-service"></a><span data-ttu-id="f9f8c-109">Çift yönlü bir hizmete erişmek için</span><span class="sxs-lookup"><span data-stu-id="f9f8c-109">To access a duplex service</span></span>

1. <span data-ttu-id="f9f8c-110">İki arabirim içeren bir hizmet oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="f9f8c-110">Create a service that contains two interfaces.</span></span> <span data-ttu-id="f9f8c-111">İlk arabirim hizmet için ikinci için geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="f9f8c-111">The first interface is for the service, the second is for the callback.</span></span> <span data-ttu-id="f9f8c-112">Çift yönlü bir hizmet oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Çift yönlü sözleşme oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="f9f8c-112">For more information about creating a duplex service, see [How to: Create a Duplex Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>

2. <span data-ttu-id="f9f8c-113">Hizmet çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f9f8c-113">Run the service.</span></span>

3. <span data-ttu-id="f9f8c-114">Kullanım [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) sözleşmelerinin (arabirimleri) istemcisi oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="f9f8c-114">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate contracts (interfaces) for the client.</span></span> <span data-ttu-id="f9f8c-115">Bunun nasıl yapılacağı hakkında daha fazla bilgi için bkz. [nasıl yapılır: Bir istemci oluşturmanız](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="f9f8c-115">For information about how to do this, see  [How to: Create a Client](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>

4. <span data-ttu-id="f9f8c-116">Geri arama arabirimini istemci sınıfında, aşağıdaki örnekte gösterildiği gibi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="f9f8c-116">Implement the callback interface in the client class, as shown in the following example.</span></span>

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

5. <span data-ttu-id="f9f8c-117">Öğesinin bir örneğini oluşturur <xref:System.ServiceModel.InstanceContext> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f9f8c-117">Create an instance of the <xref:System.ServiceModel.InstanceContext> class.</span></span> <span data-ttu-id="f9f8c-118">Oluşturucu istemci sınıfının bir örneğini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f9f8c-118">The constructor requires an instance of the client class.</span></span>

    ```csharp
    InstanceContext site = new InstanceContext(new CallbackHandler());
    ```

    ```vb
    Dim site As InstanceContext = New InstanceContext(new CallbackHandler())
    ```

6. <span data-ttu-id="f9f8c-119">Gerektiren oluşturucuyu kullanarak WCF istemci örneği oluşturun bir <xref:System.ServiceModel.InstanceContext> nesne.</span><span class="sxs-lookup"><span data-stu-id="f9f8c-119">Create an instance of the WCF client using the constructor that requires an <xref:System.ServiceModel.InstanceContext> object.</span></span> <span data-ttu-id="f9f8c-120">İkinci oluşturucu parametresi yapılandırma dosyasında bulunan bir uç nokta adıdır.</span><span class="sxs-lookup"><span data-stu-id="f9f8c-120">The second parameter of the constructor is the name of an endpoint found in the configuration file.</span></span>

    ```csharp
    CalculatorDuplexClient wcfClient = new CalculatorDuplexClient(site, "default");
    ```

    ```vb
    Dim wcfClient As New CalculatorDuplexClient(site, "default")
    ```

7. <span data-ttu-id="f9f8c-121">WCF istemcisi gerektiği gibi'nin yöntemlerini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f9f8c-121">Call the methods of the WCF client as required.</span></span>

## <a name="example"></a><span data-ttu-id="f9f8c-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="f9f8c-122">Example</span></span>

<span data-ttu-id="f9f8c-123">Aşağıdaki kod örneği, çift yönlü sözleşme erişen istemci sınıf oluşturma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f9f8c-123">The following code example demonstrates how to create a client class that accesses a duplex contract.</span></span>

[!code-csharp[S_DuplexClients#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_duplexclients/cs/client.cs#1)]
[!code-vb[S_DuplexClients#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_duplexclients/vb/client.vb#1)]

## <a name="see-also"></a><span data-ttu-id="f9f8c-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9f8c-124">See also</span></span>

- [<span data-ttu-id="f9f8c-125">Başlangıç Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="f9f8c-125">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)
- [<span data-ttu-id="f9f8c-126">Nasıl yapılır: Çift yönlü sözleşme oluşturma</span><span class="sxs-lookup"><span data-stu-id="f9f8c-126">How to: Create a Duplex Contract</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="f9f8c-127">ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="f9f8c-127">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="f9f8c-128">Nasıl yapılır: Bir istemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="f9f8c-128">How to: Create a Client</span></span>](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [<span data-ttu-id="f9f8c-129">Nasıl yapılır: ChannelFactory kullanma</span><span class="sxs-lookup"><span data-stu-id="f9f8c-129">How to: Use the ChannelFactory</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)
