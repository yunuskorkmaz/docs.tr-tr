---
title: "Nasıl yapılır: Bir Windows Communication Foundation İstemcisi Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF clients [WCF], using
ms.assetid: 190349fc-0573-49c7-bb85-8e316df7f31f
caps.latest.revision: "38"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0330c386730c6b0436196bb5b85162bc4621c214
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-windows-communication-foundation-client"></a><span data-ttu-id="67687-102">Nasıl yapılır: Bir Windows Communication Foundation İstemcisi Kullanma</span><span class="sxs-lookup"><span data-stu-id="67687-102">How to: Use a Windows Communication Foundation Client</span></span>
<span data-ttu-id="67687-103">Son altı görevlerin bir temel oluşturmak için gereken budur [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="67687-103">This is the last of six tasks required to create a basic [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] application.</span></span> <span data-ttu-id="67687-104">Tüm altı görevlerinin genel bakış için bkz: [başlangıç Öğreticisi](../../../docs/framework/wcf/getting-started-tutorial.md) konu.</span><span class="sxs-lookup"><span data-stu-id="67687-104">For an overview of all six of the tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>  
  
 <span data-ttu-id="67687-105">Bir kez bir [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] proxy oluşturulur ve yapılandırılmış bir istemci örneği oluşturulabilir ve istemci uygulaması derlenmiş ve iletişim için kullanılan [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet.</span><span class="sxs-lookup"><span data-stu-id="67687-105">Once a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] proxy has been created and configured, a client instance can be created and the client application can be compiled and used to communicate with the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="67687-106">Bu konuda, örnek oluşturma ve kullanma ile ilgili yordamlar açıklanmaktadır bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemci.</span><span class="sxs-lookup"><span data-stu-id="67687-106">This topic describes procedures for instantiating and using a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client.</span></span> <span data-ttu-id="67687-107">Bu yordam üç şey yapar:</span><span class="sxs-lookup"><span data-stu-id="67687-107">This procedure does three things:</span></span>  
  
1.  <span data-ttu-id="67687-108">Başlatır bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemci.</span><span class="sxs-lookup"><span data-stu-id="67687-108">Instantiates a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client.</span></span>  
  
2.  <span data-ttu-id="67687-109">Hizmet işlemleri oluşturulan proxy sunucudan çağırır.</span><span class="sxs-lookup"><span data-stu-id="67687-109">Calls the service operations from the generated proxy.</span></span>  
  
3.  <span data-ttu-id="67687-110">İşlem çağrısı tamamlandığında istemci kapatır.</span><span class="sxs-lookup"><span data-stu-id="67687-110">Closes the client once the operation call is completed.</span></span>  
  
### <a name="to-use-a-windows-communication-foundation-client"></a><span data-ttu-id="67687-111">Windows Communication Foundation istemcisi kullanmak için</span><span class="sxs-lookup"><span data-stu-id="67687-111">To use a Windows Communication Foundation client</span></span>  
  
1.  <span data-ttu-id="67687-112">GettingStartedClient projesinden Program.cs veya Program.vb dosyasını açın ve var olan kodu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="67687-112">Open the Program.cs or Program.vb file from the GettingStartedClient project and replace the existing code with the following code:</span></span>  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using GettingStartedClient.ServiceReference1;  
  
    namespace GettingStartedClient  
    {  
        class Program  
        {  
            static void Main(string[] args)  
            {  
                //Step 1: Create an instance of the WCF proxy.  
                CalculatorClient client = new CalculatorClient();  
  
                // Step 2: Call the service operations.  
                // Call the Add service operation.  
                double value1 = 100.00D;  
                double value2 = 15.99D;  
                double result = client.Add(value1, value2);  
                Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
                // Call the Subtract service operation.  
                value1 = 145.00D;  
                value2 = 76.54D;  
                result = client.Subtract(value1, value2);  
                Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
                // Call the Multiply service operation.  
                value1 = 9.00D;  
                value2 = 81.25D;  
                result = client.Multiply(value1, value2);  
                Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
                // Call the Divide service operation.  
                value1 = 22.00D;  
                value2 = 7.00D;  
                result = client.Divide(value1, value2);  
                Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
  
                //Step 3: Closing the client gracefully closes the connection and cleans up resources.  
                client.Close();  
            }  
        }  
    }  
    ```  
  
    ```  
    Imports System  
    Imports System.Collections.Generic  
    Imports System.Text  
    Imports System.ServiceModel  
    Imports GettingStartedClientVB2.ServiceReference1  
  
    Module Module1  
  
        Sub Main()  
            ' Step 1: Create an instance of the WCF proxy  
            Dim Client As New CalculatorClient()  
  
            'Step 2: Call the service operations.  
            'Call the Add service operation.  
            Dim value1 As Double = 100D  
            Dim value2 As Double = 15.99D  
            Dim result As Double = Client.Add(value1, value2)  
            Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)  
  
            'Call the Subtract service operation.  
            value1 = 145D  
            value2 = 76.54D  
            result = Client.Subtract(value1, value2)  
            Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result)  
  
            'Call the Multiply service operation.  
            value1 = 9D  
            value2 = 81.25D  
            result = Client.Multiply(value1, value2)  
            Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result)  
  
            'Call the Divide service operation.  
            value1 = 22D  
            value2 = 7D  
            result = Client.Divide(value1, value2)  
            Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result)  
  
            ' Step 3: Closing the client gracefully closes the connection and cleans up resources.  
            Client.Close()  
  
            Console.WriteLine()  
            Console.WriteLine("Press <ENTER> to terminate client.")  
            Console.ReadLine()  
  
        End Sub  
  
    End Module  
    ```  
  
     <span data-ttu-id="67687-113">GettingStartedClient.ServiceReference1 alır kullanarak veya Imports deyimi dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="67687-113">Notice the using or imports statement that imports the GettingStartedClient.ServiceReference1.</span></span> <span data-ttu-id="67687-114">Visual Studio'da hizmet Başvurusu Ekle tarafından oluşturulan kodu alır.</span><span class="sxs-lookup"><span data-stu-id="67687-114">This imports the code generated by Add Service Reference in Visual Studio.</span></span> <span data-ttu-id="67687-115">Kod WCF proxy başlatır ve ardından her hesaplayıcı hizmeti tarafından sunulan hizmet işlemlerinin çağırır, proxy kapatır ve sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="67687-115">The code instantiates the WCF proxy and then calls each of the service operations exposed by the calculator service, closes the proxy and terminates.</span></span>  
  
 <span data-ttu-id="67687-116">Şimdi öğreticisini tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="67687-116">You have now completed the tutorial.</span></span> <span data-ttu-id="67687-117">Bir hizmet sözleşmesini tanımlı, hizmet sözleşmesi uygulanan, WCF proxy oluşturulan, WCF istemci uygulaması yapılandırılmış ve proxy hizmet işlemlerini çağırma kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="67687-117">You defined a service contract, implemented the service contract, generated a WCF proxy, configured a WCF client application, and then used the proxy to call service operations.</span></span> <span data-ttu-id="67687-118">Uygulamayı test etmek için önce hizmeti başlatmayı GettingStartedHost çalıştırın ve ardından GettingStartedClient çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="67687-118">To test out the application first run GettingStartedHost to start the service and then run GettingStartedClient.</span></span> <span data-ttu-id="67687-119">GettingStartedHost çıkışı aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="67687-119">The output from GettingStartedHost should look like this:</span></span>  
  
```Output  
The service is ready.Press <ENTER> to terminate service.Received Add(100,15.99)Return: 115.99Received Subtract(145,76.54)Return: 68.46Received Multiply(9,81.25)Return: 731.25Received Divide(22,7)Return: 3.14285714285714  
```  
  
 <span data-ttu-id="67687-120">GettingStartedClient çıkışı aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="67687-120">The output from GettingStartedClient should look like this:</span></span>  
  
```Output  
Add(100,15.99) = 115.99Subtract(145,76.54) = 68.46Multiply(9,81.25) = 731.25Divide(22,7) = 3.14285714285714Press <ENTER> to terminate client.  
```  
  
## <a name="see-also"></a><span data-ttu-id="67687-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="67687-121">See Also</span></span>  
 [<span data-ttu-id="67687-122">İstemci Derleme</span><span class="sxs-lookup"><span data-stu-id="67687-122">Building Clients</span></span>](../../../docs/framework/wcf/building-clients.md)  
 [<span data-ttu-id="67687-123">Nasıl yapılır: İstemci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="67687-123">How to: Create a Client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [<span data-ttu-id="67687-124">Başlangıç Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="67687-124">Getting Started Tutorial</span></span>](../../../docs/framework/wcf/getting-started-tutorial.md)  
 [<span data-ttu-id="67687-125">Temel WCF Programlama</span><span class="sxs-lookup"><span data-stu-id="67687-125">Basic WCF Programming</span></span>](../../../docs/framework/wcf/basic-wcf-programming.md)  
 [<span data-ttu-id="67687-126">Nasıl yapılır: Çift Yönlü Anlaşma Oluşturma</span><span class="sxs-lookup"><span data-stu-id="67687-126">How to: Create a Duplex Contract</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
 [<span data-ttu-id="67687-127">Nasıl yapılır: Çift Yönlü Sözleşme ile Hizmetlere Erişme</span><span class="sxs-lookup"><span data-stu-id="67687-127">How to: Access Services with a Duplex Contract</span></span>](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)  
 [<span data-ttu-id="67687-128">Başlarken</span><span class="sxs-lookup"><span data-stu-id="67687-128">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [<span data-ttu-id="67687-129">Kendini Barındırma</span><span class="sxs-lookup"><span data-stu-id="67687-129">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)
