---
title: 'Nasıl yapılır: Temel Windows Communication Foundation istemcisi yapılandırma'
ms.date: 09/14/2018
helpviewer_keywords:
- WCF clients [WCF], configuring
ms.assetid: d067b86d-afb0-47bf-94f6-45180a3d8d78
ms.openlocfilehash: 18acec48b2af78877f99335da38ccb0ae8942824
ms.sourcegitcommit: 0069cb3de8eed4e92b2195d29e5769a76111acdd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/16/2019
ms.locfileid: "56332331"
---
# <a name="how-to-configure-a-basic-windows-communication-foundation-client"></a><span data-ttu-id="ae872-102">Nasıl yapılır: Temel Windows Communication Foundation istemcisi yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ae872-102">How to: Configure a Basic Windows Communication Foundation Client</span></span>

<span data-ttu-id="ae872-103">Beşinci altı görev temel Windows Communication Foundation (WCF) uygulaması oluşturmak için gereken budur.</span><span class="sxs-lookup"><span data-stu-id="ae872-103">This is the fifth of six tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="ae872-104">Tüm altı görevleri genel bakış için bkz. [başlangıç Öğreticisi](../../../docs/framework/wcf/getting-started-tutorial.md) konu.</span><span class="sxs-lookup"><span data-stu-id="ae872-104">For an overview of all six of the tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>

<span data-ttu-id="ae872-105">Bu konuda ele alınmıştır kullanılarak oluşturulan istemci yapılandırma dosyası **hizmet Başvurusu Ekle** Visual Studio işlevselliğini veya [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="ae872-105">This topic discusses the client configuration file that was generated using the **Add Service Reference** functionality of Visual Studio or the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="ae872-106">İstemci yapılandırması, istemcinin hizmete erişmek için kullandığı uç noktası belirtme oluşur.</span><span class="sxs-lookup"><span data-stu-id="ae872-106">Configuring the client consists of specifying the endpoint that the client uses to access the service.</span></span> <span data-ttu-id="ae872-107">Bir uç nokta bir adresi, bağlama ve bir sözleşme vardır ve her birinin istemci yapılandırma sürecinde belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="ae872-107">An endpoint has an address, a binding, and a contract, and each of these must be specified in the process of configuring the client.</span></span>

## <a name="configure-a-windows-communication-foundation-client"></a><span data-ttu-id="ae872-108">Bir Windows Communication Foundation istemcisi yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ae872-108">Configure a Windows Communication Foundation client</span></span>

<span data-ttu-id="ae872-109">GettingStartedClient projeden oluşturulan yapılandırma dosyası (App.config) açın.</span><span class="sxs-lookup"><span data-stu-id="ae872-109">Open the generated configuration file (App.config) from the GettingStartedClient project.</span></span> <span data-ttu-id="ae872-110">Aşağıdaki örnek, oluşturulan yapılandırma dosyasının bir görünümüdür.</span><span class="sxs-lookup"><span data-stu-id="ae872-110">The following example is a view of the generated configuration file.</span></span> <span data-ttu-id="ae872-111">Altında [ \<system.serviceModel >](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) bölümünde, bulma [ \<uç noktası >](../configure-apps/file-schema/wcf/endpoint-element.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="ae872-111">Under the [\<system.serviceModel>](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) section, find the [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-element.md) element.</span></span>

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

<span data-ttu-id="ae872-112">Bu örnekte istemci şu adresten bulunduğu hizmete erişmek için kullandığı uç nokta yapılandırır: `http://localhost:8000/ServiceModelSamples/Service/CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="ae872-112">This example configures the endpoint that the client uses to access the service that is located at the following address: `http://localhost:8000/ServiceModelSamples/Service/CalculatorService`.</span></span>

<span data-ttu-id="ae872-113">Uç nokta öğesini belirten `ServiceReference1.ICalculator` hizmet sözleşmesi WCF istemci ve hizmet arasındaki iletişim için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ae872-113">The endpoint element specifies that the `ServiceReference1.ICalculator` service contract is used for communication between the WCF client and service.</span></span> <span data-ttu-id="ae872-114">WCF kanalı sistem tarafından sağlanan ile yapılandırılmış <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="ae872-114">The WCF channel is configured with the system-provided <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="ae872-115">Bu sözleşme kullanılarak oluşturulmuş **hizmet Başvurusu Ekle** Visual Studio'da.</span><span class="sxs-lookup"><span data-stu-id="ae872-115">This contract was generated by using **Add Service Reference** in Visual Studio.</span></span> <span data-ttu-id="ae872-116">Bu temelde GettingStartedLib projede tanımlanan sözleşme bir kopyasıdır.</span><span class="sxs-lookup"><span data-stu-id="ae872-116">It is essentially a copy of the contract that was defined in the GettingStartedLib project.</span></span> <span data-ttu-id="ae872-117"><xref:System.ServiceModel.WSHttpBinding> Bağlama HTTP taşıma, birlikte çalışabilen güvenlik ve diğer yapılandırma ayrıntılarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ae872-117">The <xref:System.ServiceModel.WSHttpBinding> binding specifies HTTP as the transport, interoperable security, and other configuration details.</span></span>

<span data-ttu-id="ae872-118">Bu yapılandırma ile oluşturulan istemciyi kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Bir istemci kullanın](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="ae872-118">For more information about how to use the generated client with this configuration, see [How to: Use a Client](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="ae872-119">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="ae872-119">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ae872-120">Nasıl yapılır: WCF istemci kullanma</span><span class="sxs-lookup"><span data-stu-id="ae872-120">How to: Use a WCF client</span></span>](../../../docs/framework/wcf/how-to-use-a-wcf-client.md)

## <a name="see-also"></a><span data-ttu-id="ae872-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae872-121">See also</span></span>

- [<span data-ttu-id="ae872-122">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="ae872-122">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="ae872-123">ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="ae872-123">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="ae872-124">Nasıl yapılır: Bir istemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="ae872-124">How to: Create a Client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [<span data-ttu-id="ae872-125">Başlarken</span><span class="sxs-lookup"><span data-stu-id="ae872-125">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [<span data-ttu-id="ae872-126">Kendini Barındırma</span><span class="sxs-lookup"><span data-stu-id="ae872-126">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)