---
description: 'Daha fazla bilgi edinin: nasıl yapılır: çift yönlü sözleşme ile hizmetlere erişme'
title: 'Nasıl yapılır: çift yönlü sözleşme ile hizmetlere erişme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 746a9d64-f21c-426c-b85d-972e916ec6c5
ms.openlocfilehash: e58225e6b77115004c3c201d606e328aab184b75
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742894"
---
# <a name="how-to-access-services-with-a-duplex-contract"></a><span data-ttu-id="67809-103">Nasıl yapılır: çift yönlü sözleşme ile hizmetlere erişme</span><span class="sxs-lookup"><span data-stu-id="67809-103">How to: Access services with a duplex contract</span></span>

<span data-ttu-id="67809-104">Windows Communication Foundation (WCF) özelliğinin bir özelliği, çift yönlü mesajlaşma modelini kullanan bir hizmet oluşturma olanağıdır.</span><span class="sxs-lookup"><span data-stu-id="67809-104">One feature of Windows Communication Foundation (WCF) is the ability to create a service that uses a duplex messaging pattern.</span></span> <span data-ttu-id="67809-105">Bu model, bir hizmetin geri çağırma yoluyla istemciyle iletişim kurmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="67809-105">This pattern allows a service to communicate with the client through a callback.</span></span> <span data-ttu-id="67809-106">Bu konuda, geri çağırma arabirimini uygulayan bir istemci sınıfında bir WCF istemcisi oluşturma adımları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="67809-106">This topic shows the steps to create a WCF client in a client class that implements the callback interface.</span></span>

<span data-ttu-id="67809-107">İkili bağlama, istemcinin IP adresini hizmete gösterir.</span><span class="sxs-lookup"><span data-stu-id="67809-107">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="67809-108">İstemci, yalnızca güvendiği hizmetlere bağlanmasını sağlamak için güvenliği kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="67809-108">The client should use security to ensure that it connects only to services it trusts.</span></span>

<span data-ttu-id="67809-109">Temel bir WCF hizmeti ve istemcisi oluşturmaya yönelik bir öğretici için bkz. [Başlangıç Öğreticisi](../getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="67809-109">For a tutorial on creating a basic WCF service and client, see [Getting Started Tutorial](../getting-started-tutorial.md).</span></span>

## <a name="to-access-a-duplex-service"></a><span data-ttu-id="67809-110">Çift yönlü hizmete erişmek için</span><span class="sxs-lookup"><span data-stu-id="67809-110">To access a duplex service</span></span>

1. <span data-ttu-id="67809-111">İki arabirim içeren bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="67809-111">Create a service that contains two interfaces.</span></span> <span data-ttu-id="67809-112">İlk arabirim hizmet içindir, ikincisi geri arama içindir.</span><span class="sxs-lookup"><span data-stu-id="67809-112">The first interface is for the service, the second is for the callback.</span></span> <span data-ttu-id="67809-113">Çift yönlü hizmet oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: çift yönlü sözleşme oluşturma](how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="67809-113">For more information about creating a duplex service, see [How to: Create a Duplex Contract](how-to-create-a-duplex-contract.md).</span></span>

2. <span data-ttu-id="67809-114">Hizmeti çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="67809-114">Run the service.</span></span>

3. <span data-ttu-id="67809-115">İstemci için sözleşmeler (arabirimler) oluşturmak üzere [ServiceModel meta veri yardımcı programı aracını (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="67809-115">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate contracts (interfaces) for the client.</span></span> <span data-ttu-id="67809-116">Bunun nasıl yapılacağı hakkında bilgi için bkz.  [nasıl yapılır: Istemci oluşturma](../how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="67809-116">For information about how to do this, see  [How to: Create a Client](../how-to-create-a-wcf-client.md).</span></span>

4. <span data-ttu-id="67809-117">Aşağıdaki örnekte gösterildiği gibi, istemci sınıfında geri çağırma arabirimini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="67809-117">Implement the callback interface in the client class, as shown in the following example.</span></span>

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

5. <span data-ttu-id="67809-118">Öğesinin bir örneğini oluşturur <xref:System.ServiceModel.InstanceContext> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="67809-118">Create an instance of the <xref:System.ServiceModel.InstanceContext> class.</span></span> <span data-ttu-id="67809-119">Oluşturucu, istemci sınıfının bir örneğini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="67809-119">The constructor requires an instance of the client class.</span></span>

    ```csharp
    InstanceContext site = new InstanceContext(new CallbackHandler());
    ```

    ```vb
    Dim site As InstanceContext = New InstanceContext(new CallbackHandler())
    ```

6. <span data-ttu-id="67809-120">Bir nesne gerektiren oluşturucuyu kullanarak WCF istemcisinin bir örneğini oluşturun <xref:System.ServiceModel.InstanceContext> .</span><span class="sxs-lookup"><span data-stu-id="67809-120">Create an instance of the WCF client using the constructor that requires an <xref:System.ServiceModel.InstanceContext> object.</span></span> <span data-ttu-id="67809-121">Oluşturucunun ikinci parametresi, yapılandırma dosyasında bulunan bir uç noktanın adıdır.</span><span class="sxs-lookup"><span data-stu-id="67809-121">The second parameter of the constructor is the name of an endpoint found in the configuration file.</span></span>

    ```csharp
    CalculatorDuplexClient wcfClient = new CalculatorDuplexClient(site, "default");
    ```

    ```vb
    Dim wcfClient As New CalculatorDuplexClient(site, "default")
    ```

7. <span data-ttu-id="67809-122">WCF istemcisinin yöntemlerini gereken şekilde çağırın.</span><span class="sxs-lookup"><span data-stu-id="67809-122">Call the methods of the WCF client as required.</span></span>

## <a name="example"></a><span data-ttu-id="67809-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="67809-123">Example</span></span>

<span data-ttu-id="67809-124">Aşağıdaki kod örneği, çift yönlü bir sözleşmeye erişen bir istemci sınıfının nasıl oluşturulacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="67809-124">The following code example demonstrates how to create a client class that accesses a duplex contract.</span></span>

[!code-csharp[S_DuplexClients#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_duplexclients/cs/client.cs#1)]
[!code-vb[S_DuplexClients#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_duplexclients/vb/client.vb#1)]

## <a name="see-also"></a><span data-ttu-id="67809-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67809-125">See also</span></span>

- [<span data-ttu-id="67809-126">Başlangıç Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="67809-126">Getting Started Tutorial</span></span>](../getting-started-tutorial.md)
- [<span data-ttu-id="67809-127">Nasıl yapılır: Çift Yönlü Sözleşme Oluşturma</span><span class="sxs-lookup"><span data-stu-id="67809-127">How to: Create a Duplex Contract</span></span>](how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="67809-128">ServiceModel Meta Veri Yardımcı Programracı (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="67809-128">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="67809-129">Nasıl yapılır: İstemci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="67809-129">How to: Create a Client</span></span>](../how-to-create-a-wcf-client.md)
- [<span data-ttu-id="67809-130">Nasıl yapılır: ChannelFactory Kullanma</span><span class="sxs-lookup"><span data-stu-id="67809-130">How to: Use the ChannelFactory</span></span>](how-to-use-the-channelfactory.md)
