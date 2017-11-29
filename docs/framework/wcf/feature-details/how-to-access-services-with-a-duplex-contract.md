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
# <a name="how-to-access-services-with-a-duplex-contract"></a><span data-ttu-id="61486-102">Nasıl yapılır: Çift Yönlü Sözleşme ile Hizmetlere Erişme</span><span class="sxs-lookup"><span data-stu-id="61486-102">How to: Access Services with a Duplex Contract</span></span>
<span data-ttu-id="61486-103">Bir özelliği [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] çift yönlü bir Mesajlaşma düzeni kullanan bir hizmet oluşturma yeteneği.</span><span class="sxs-lookup"><span data-stu-id="61486-103">One feature of [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is the ability to create a service that uses a duplex messaging pattern.</span></span> <span data-ttu-id="61486-104">Bu desen bir geri çağırma istemcinize ile iletişim kurmak bir hizmet sağlar.</span><span class="sxs-lookup"><span data-stu-id="61486-104">This pattern allows a service to communicate with the client through a callback.</span></span> <span data-ttu-id="61486-105">Bu konuda oluşturmaya yönelik adımlar gösterilmektedir bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] geri çağırma arabirimini uygulayan bir istemci sınıfı istemcisinde.</span><span class="sxs-lookup"><span data-stu-id="61486-105">This topic shows the steps to create a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client in a client class that implements the callback interface.</span></span>  
  
 <span data-ttu-id="61486-106">Bir çift bağlama hizmeti istemcinin IP adresini gösterir.</span><span class="sxs-lookup"><span data-stu-id="61486-106">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="61486-107">İstemci, yalnızca Hizmetleri için güvenleri bağladığı emin olmak için güvenlik kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="61486-107">The client should use security to ensure that it connects only to services it trusts.</span></span>  
  
 <span data-ttu-id="61486-108">Temel bir oluşturma bir öğretici için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet ve istemci, bkz: [başlangıç Öğreticisi](../../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="61486-108">For a tutorial on creating a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service and client, see [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span>  
  
### <a name="to-access-a-duplex-service"></a><span data-ttu-id="61486-109">Çift yönlü bir hizmete erişmek için</span><span class="sxs-lookup"><span data-stu-id="61486-109">To access a duplex service</span></span>  
  
1.  <span data-ttu-id="61486-110">İki arabirim içeren bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="61486-110">Create a service that contains two interfaces.</span></span> <span data-ttu-id="61486-111">İlk arabirimi hizmet için ikinci için geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="61486-111">The first interface is for the service, the second is for the callback.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="61486-112">bkz. çift yönlü bir hizmet oluşturma [nasıl yapılır: çift yönlü sözleşme oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="61486-112"> creating a duplex service, see [How to: Create a Duplex Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
2.  <span data-ttu-id="61486-113">Hizmet çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="61486-113">Run the service.</span></span>  
  
3.  <span data-ttu-id="61486-114">Kullanım [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) sözleşmeleri (arabirimler) için istemci oluşturulamadı.</span><span class="sxs-lookup"><span data-stu-id="61486-114">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate contracts (interfaces) for the client.</span></span> <span data-ttu-id="61486-115">Bunun nasıl yapılacağı hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir istemci oluşturmak](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="61486-115">For information about how to do this, see  [How to: Create a Client](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>  
  
4.  <span data-ttu-id="61486-116">Geri çağırma arabirimi, aşağıdaki örnekte gösterildiği gibi istemci sınıfında uygulayın.</span><span class="sxs-lookup"><span data-stu-id="61486-116">Implement the callback interface in the client class, as shown in the following example.</span></span>  
  
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
  
5.  <span data-ttu-id="61486-117">Öğesinin bir örneğini oluşturur <xref:System.ServiceModel.InstanceContext> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="61486-117">Create an instance of the <xref:System.ServiceModel.InstanceContext> class.</span></span> <span data-ttu-id="61486-118">Oluşturucu istemci sınıfının bir örneğini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="61486-118">The constructor requires an instance of the client class.</span></span>  
  
    ```csharp  
    InstanceContext site = new InstanceContext(new CallbackHandler());  
    ```  
  
    ```vb  
    Dim site As InstanceContext = New InstanceContext(new CallbackHandler())  
    ```  
  
6.  <span data-ttu-id="61486-119">Bir örneğini oluşturmak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gerektirir Oluşturucusu kullanılarak istemci bir <xref:System.ServiceModel.InstanceContext> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="61486-119">Create an instance of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client using the constructor that requires an <xref:System.ServiceModel.InstanceContext> object.</span></span> <span data-ttu-id="61486-120">Öğesinin ikinci parametresi oluşturucusu, yapılandırma dosyasında bulunan bir uç nokta adıdır.</span><span class="sxs-lookup"><span data-stu-id="61486-120">The second parameter of the constructor is the name of an endpoint found in the configuration file.</span></span>  
  
    ```csharp  
    CalculatorDuplexClient wcfClient =   
    new CalculatorDuplexClient(site, "default")  
    ```  
  
    ```vb  
    Dim wcfClient As New CalculatorDuplexClient(site, "default")  
    ```  
  
7.  <span data-ttu-id="61486-121">Yöntemleri çağırma [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gerektiği gibi istemci.</span><span class="sxs-lookup"><span data-stu-id="61486-121">Call the methods of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client as required.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61486-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="61486-122">Example</span></span>  
 <span data-ttu-id="61486-123">Aşağıdaki kod örneğinde, çift yönlü sözleşme erişen istemci sınıfın nasıl oluşturulacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="61486-123">The following code example demonstrates how to create a client class that accesses a duplex contract.</span></span>  
  
 [!code-csharp[S_DuplexClients#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_duplexclients/cs/client.cs#1)]
 [!code-vb[S_DuplexClients#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_duplexclients/vb/client.vb#1)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="61486-124">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="61486-124">.NET Framework Security</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61486-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="61486-125">See Also</span></span>  
 [<span data-ttu-id="61486-126">Başlangıç Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="61486-126">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)  
 [<span data-ttu-id="61486-127">Nasıl yapılır: çift yönlü sözleşme oluşturma</span><span class="sxs-lookup"><span data-stu-id="61486-127">How to: Create a Duplex Contract</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
 [<span data-ttu-id="61486-128">ServiceModel meta veri yardımcı Programracı (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="61486-128">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [<span data-ttu-id="61486-129">Nasıl yapılır: bir istemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="61486-129">How to: Create a Client</span></span>](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [<span data-ttu-id="61486-130">Nasıl yapılır: ChannelFactory kullanma</span><span class="sxs-lookup"><span data-stu-id="61486-130">How to: Use the ChannelFactory</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)
