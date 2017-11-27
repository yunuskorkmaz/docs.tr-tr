---
title: "Nasıl yapılır: Bir Windows Communication Foundation İstemcisi Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF clients [WCF], configuring
ms.assetid: d067b86d-afb0-47bf-94f6-45180a3d8d78
caps.latest.revision: "47"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1f4d6b5386e82a2052182ba3f4a929de13b27c22
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-configure-a-basic-windows-communication-foundation-client"></a><span data-ttu-id="aaf26-102">Nasıl yapılır: Bir Windows Communication Foundation İstemcisi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="aaf26-102">How to: Configure a Basic Windows Communication Foundation Client</span></span>
<span data-ttu-id="aaf26-103">Temel bir oluşturmak için gereken altı görevleri beşinci budur [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="aaf26-103">This is the fifth of six tasks required to create a basic [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] application.</span></span> <span data-ttu-id="aaf26-104">Tüm altı görevlerinin genel bakış için bkz: [başlangıç Öğreticisi](../../../docs/framework/wcf/getting-started-tutorial.md) konu.</span><span class="sxs-lookup"><span data-stu-id="aaf26-104">For an overview of all six of the tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>  
  
 <span data-ttu-id="aaf26-105">Bu konuda disuccess hizmet Başvurusu Ekle işlevselliği kullanılarak oluşturulan istemci yapılandırma dosyası [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] veya [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="aaf26-105">This topic disuccess the client configuration file that was generated using the Add Service Reference functionality of [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] or the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="aaf26-106">İstemci yapılandırma İstemcinin hizmete erişmek için kullandığı uç noktası belirterek oluşur.</span><span class="sxs-lookup"><span data-stu-id="aaf26-106">Configuring the client consists of specifying the endpoint that the client uses to access the service.</span></span> <span data-ttu-id="aaf26-107">Bir adresi, bağlama ve bir sözleşme bir uç nokta var ve bunların her biri istemci yapılandırma sürecinde belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="aaf26-107">An endpoint has an address, a binding and a contract, and each of these must be specified in the process of configuring the client.</span></span>  
  
### <a name="to-configure-a-windows-communication-foundation-client"></a><span data-ttu-id="aaf26-108">Windows Communication Foundation istemcisi yapılandırma</span><span class="sxs-lookup"><span data-stu-id="aaf26-108">To configure a Windows Communication Foundation client</span></span>  
  
1.  <span data-ttu-id="aaf26-109">Oluşturulan yapılandırma dosyası (App.config) GettingStartedClient projesinden açın.</span><span class="sxs-lookup"><span data-stu-id="aaf26-109">Open the generated configuration file (App.config) from the GettingStartedClient project.</span></span> <span data-ttu-id="aaf26-110">Aşağıdaki örnek, oluşturulan yapılandırma dosyası görülmektedir.</span><span class="sxs-lookup"><span data-stu-id="aaf26-110">The following example is a view of the generated configuration file.</span></span> <span data-ttu-id="aaf26-111">Altında [ \<system.serviceModel >](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) bölümünde, Bul [ \<uç noktası >](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) öğesi.</span><span class="sxs-lookup"><span data-stu-id="aaf26-111">Under the [\<system.serviceModel>](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) section, find the [\<endpoint>](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) element.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
        <startup>   
          <!-- specifies the version of WCF to use-->  
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5,Profile=Client" />  
        </startup>  
        <system.serviceModel>  
            <bindings>  
                <!-- Uses wsHttpBinding-->  
                <wsHttpBinding>  
                    <binding name="WSHttpBinding_ICalculator" />  
                </wsHttpBinding>  
            </bindings>  
            <client>  
                <!-- specifies the endpoint to use when calling the service -->  
                <endpoint address="http://localhost:8000/ServiceModelSamples/Service/CalculatorService"  
                    binding="wsHttpBinding" bindingConfiguration="WSHttpBinding_ICalculator"  
                    contract="ServiceReference1.ICalculator" name="WSHttpBinding_ICalculator">  
                    <identity>  
                        <userPrincipalName value="migree@redmond.corp.microsoft.com" />  
                    </identity>  
                </endpoint>  
            </client>  
        </system.serviceModel>  
    </configuration>   
    ```  
  
     <span data-ttu-id="aaf26-112">Bu örnek istemcinin şu adresten bulunduğu hizmete erişmek için kullandığı uç nokta yapılandırır: 8000/ServiceModelSamples/Service/CalculatorService</span><span class="sxs-lookup"><span data-stu-id="aaf26-112">This example configures the endpoint that the client uses to access the service that is located at the following address: http://localhost:8000/ServiceModelSamples/Service/CalculatorService</span></span>  
  
     <span data-ttu-id="aaf26-113">Uç nokta öğesi belirleyen `ServiceReference1.ICalculator` hizmet sözleşmesini WCF İstemcisi hizmeti arasındaki iletişimi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aaf26-113">The endpoint element specifies that the `ServiceReference1.ICalculator` service contract is used for communication between the WCF client and service.</span></span> <span data-ttu-id="aaf26-114">WCF kanalı sistem tarafından sağlanan ile yapılandırılmış <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>.</span><span class="sxs-lookup"><span data-stu-id="aaf26-114">The WCF channel is configured with the system-provided <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>.</span></span> <span data-ttu-id="aaf26-115">Bu sözleşme, Visual Studio'da hizmet Başvurusu Ekle kullanılarak oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="aaf26-115">This contract was generated by using Add Service Reference in Visual Studio.</span></span> <span data-ttu-id="aaf26-116">Bu temelde GettingStartedLib proje tanımlanan sözleşme bir kopyasıdır.</span><span class="sxs-lookup"><span data-stu-id="aaf26-116">It is essentially a copy of the contract that was defined in the GettingStartedLib project.</span></span> <span data-ttu-id="aaf26-117"><<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> Bağlama HTTP taşıma, birlikte çalışabilen güvenlik ve diğer yapılandırma ayrıntılarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="aaf26-117">The <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> binding specifies HTTP as the transport, interoperable security, and other configuration details.</span></span>  
  
2.  [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="aaf26-118">Bu yapılandırma ile oluşturulan istemciyi kullanma hakkında [nasıl yapılır: bir istemci kullanın](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="aaf26-118"> how to use the generated client with this configuration, see [How to: Use a Client](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aaf26-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aaf26-119">See Also</span></span>  
 [<span data-ttu-id="aaf26-120">Hizmetler ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="aaf26-120">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="aaf26-121">ServiceModel meta veri yardımcı Programracı (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="aaf26-121">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [<span data-ttu-id="aaf26-122">Nasıl yapılır: bir istemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="aaf26-122">How to: Create a Client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [<span data-ttu-id="aaf26-123">Başlarken</span><span class="sxs-lookup"><span data-stu-id="aaf26-123">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [<span data-ttu-id="aaf26-124">Kendini barındırma</span><span class="sxs-lookup"><span data-stu-id="aaf26-124">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)
