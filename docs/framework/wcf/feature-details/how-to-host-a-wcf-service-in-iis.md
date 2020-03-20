---
title: "Nasıl yapılır: IIS'de WCF Hizmeti Barındırma"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b044b1c9-c1e5-4c9f-84d8-0f02f4537f8b
ms.openlocfilehash: 580b380a6c6349c6a4efa26e3eefe38bd660fa1b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184919"
---
# <a name="how-to-host-a-wcf-service-in-iis"></a><span data-ttu-id="d66e6-102">Nasıl yapılır: IIS'de WCF Hizmeti Barındırma</span><span class="sxs-lookup"><span data-stu-id="d66e6-102">How to: Host a WCF Service in IIS</span></span>
<span data-ttu-id="d66e6-103">Bu konu, Internet Bilgi Hizmetleri'nde (IIS) barındırılan bir Windows Communication Foundation (WCF) hizmeti oluşturmak için gereken temel adımları özetlemektedir.</span><span class="sxs-lookup"><span data-stu-id="d66e6-103">This topic outlines the basic steps required to create a Windows Communication Foundation (WCF) service that is hosted in Internet Information Services (IIS).</span></span> <span data-ttu-id="d66e6-104">Bu konu, IIS'ye aşina olduğunuzu ve IIS uygulamalarını oluşturmak ve yönetmek için IIS yönetim aracını nasıl kullanacağınızı bildiğinizi varsayar.</span><span class="sxs-lookup"><span data-stu-id="d66e6-104">This topic assumes you are familiar with IIS and understand how to use the IIS management tool to create and manage IIS applications.</span></span> <span data-ttu-id="d66e6-105">IIS hakkında daha fazla bilgi için [Internet Bilgi Hizmetleri'ne](https://www.iis.net/)bakın.</span><span class="sxs-lookup"><span data-stu-id="d66e6-105">For more information about IIS see [Internet Information Services](https://www.iis.net/).</span></span> <span data-ttu-id="d66e6-106">IIS ortamında çalışan bir WCF hizmeti, işlem geri dönüşümü, boşta kapatma, işlem durumu izleme ve ileti tabanlı etkinleştirme gibi IIS özelliklerinden tam olarak yararlanır.</span><span class="sxs-lookup"><span data-stu-id="d66e6-106">A WCF service that runs in the IIS environment takes full advantage of IIS features, such as process recycling, idle shutdown, process health monitoring, and message-based activation.</span></span> <span data-ttu-id="d66e6-107">Bu barındırma seçeneği, IIS'nin düzgün şekilde yapılandırılmasını gerektirir, ancak herhangi bir barındırma kodunun uygulamanın bir parçası olarak yazılmasını gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="d66e6-107">This hosting option requires that IIS be properly configured, but it does not require that any hosting code be written as part of the application.</span></span> <span data-ttu-id="d66e6-108">IIS barındırma yı yalnızca bir HTTP taşıma ile kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d66e6-108">You can use IIS hosting only with an HTTP transport.</span></span>  
  
 <span data-ttu-id="d66e6-109">WCF ve ASP.NET etkileşimi hakkında daha fazla bilgi için [WCF Hizmetleri ve ASP.NET'](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)a bakın.</span><span class="sxs-lookup"><span data-stu-id="d66e6-109">For more information about how WCF and ASP.NET interact, see [WCF Services and ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).</span></span> <span data-ttu-id="d66e6-110">Güvenliği yapılandırma hakkında daha fazla bilgi için [Güvenlik'e](../../../../docs/framework/wcf/feature-details/security.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="d66e6-110">For more information about configuring security, see [Security](../../../../docs/framework/wcf/feature-details/security.md).</span></span>  
  
 <span data-ttu-id="d66e6-111">Bu örneğin kaynak kopyası için, [Satır Satır Kodu Kullanarak IIS Hosting'e](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="d66e6-111">For the source copy of this example, see [IIS Hosting Using Inline Code](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md).</span></span>  
  
### <a name="to-create-a-service-hosted-by-iis"></a><span data-ttu-id="d66e6-112">IIS tarafından barındırılan bir hizmet oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d66e6-112">To create a service hosted by IIS</span></span>  
  
1. <span data-ttu-id="d66e6-113">IIS'nin bilgisayarınızda yüklü ve çalıştığını doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="d66e6-113">Confirm that IIS is installed and running on your computer.</span></span> <span data-ttu-id="d66e6-114">IIS'nin yüklenmesi ve yapılandırılması hakkında daha fazla bilgi için [bkz.](https://docs.microsoft.com/iis/install/installing-iis-7/installing-necessary-iis-components-on-windows-vista)</span><span class="sxs-lookup"><span data-stu-id="d66e6-114">For more information about installing and configuring IIS see [Installing and Configuring IIS 7.0](https://docs.microsoft.com/iis/install/installing-iis-7/installing-necessary-iis-components-on-windows-vista)</span></span>  
  
2. <span data-ttu-id="d66e6-115">"IISHostedCalcService" adlı uygulama dosyalarınız için yeni bir klasör oluşturun, ASP.NET klasörün içeriğine erişebilmesini sağlayın ve bu uygulama dizininde fiziksel olarak bulunan yeni bir IIS uygulaması oluşturmak için IIS yönetim aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="d66e6-115">Create a new folder for your application files called "IISHostedCalcService", ensure that ASP.NET has access to the contents of the folder, and use the IIS management tool to create a new IIS application that is physically located in this application directory.</span></span> <span data-ttu-id="d66e6-116">Uygulama dizini için bir takma ad oluştururken "IISHostedCalc" kullanın.</span><span class="sxs-lookup"><span data-stu-id="d66e6-116">When creating an alias for the application directory use "IISHostedCalc".</span></span>  
  
3. <span data-ttu-id="d66e6-117">Uygulama dizininde "service.svc" adlı yeni bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d66e6-117">Create a new file named "service.svc" in the application directory.</span></span> <span data-ttu-id="d66e6-118">Aşağıdaki @ServiceHost öğeyi ekleyerek bu dosyayı düzenleme.</span><span class="sxs-lookup"><span data-stu-id="d66e6-118">Edit this file by adding the following @ServiceHost element.</span></span>  
  
   ```
   <%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService"%>
   ```  
  
4. <span data-ttu-id="d66e6-119">Uygulama dizininde App_Code bir alt dizini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d66e6-119">Create an App_Code subdirectory within the application directory.</span></span>  
  
5. <span data-ttu-id="d66e6-120">App_Code alt dizininde Service.cs adlı bir kod dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d66e6-120">Create a code file named Service.cs in the App_Code subdirectory.</span></span>  
  
6. <span data-ttu-id="d66e6-121">Service.cs dosyasının üst bölümüne aşağıdaki ifadeleri kullanarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d66e6-121">Add the following using statements to the top of the Service.cs file.</span></span>  
  
    ```csharp  
    using System;  
    using System.ServiceModel;  
    ```  
  
7. <span data-ttu-id="d66e6-122">Aşağıdaki ad alanı bildirimini kullanarak ifadelerden sonra ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d66e6-122">Add the following namespace declaration after the using statements.</span></span>  
  
    ```csharp  
    namespace Microsoft.ServiceModel.Samples  
    {  
    }  
    ```  
  
8. <span data-ttu-id="d66e6-123">Ad alanı bildirimi içindeki hizmet sözleşmesini aşağıdaki kodda gösterildiği şekilde tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="d66e6-123">Define the service contract inside the namespace declaration as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInIIS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#11)]
     [!code-vb[c_HowTo_HostInIIS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#11)]  
  
9. <span data-ttu-id="d66e6-124">Aşağıdaki kodda gösterildiği gibi hizmet sözleşmesi tanımından sonra hizmet sözleşmesini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="d66e6-124">Implement the service contract after the service contract definition as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInIIS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#12)]
     [!code-vb[c_HowTo_HostInIIS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#12)]  
  
10. <span data-ttu-id="d66e6-125">Uygulama dizininde "Web.config" adlı bir dosya oluşturun ve dosyaya aşağıdaki yapılandırma kodunu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d66e6-125">Create a file named "Web.config" in the application directory and add the following configuration code into the file.</span></span> <span data-ttu-id="d66e6-126">Çalışma zamanında, WCF altyapısı istemci uygulamalarının iletişim kurabileceği bir bitiş noktası oluşturmak için bilgileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="d66e6-126">At runtime, the WCF infrastructure uses the information to construct an endpoint that client applications can communicate with.</span></span>  
  
     [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]
  
     <span data-ttu-id="d66e6-127">Bu örnek, yapılandırma dosyasındaki uç noktaları açıkça belirtir.</span><span class="sxs-lookup"><span data-stu-id="d66e6-127">This example explicitly specifies endpoints in the configuration file.</span></span> <span data-ttu-id="d66e6-128">Hizmete herhangi bir uç nokta eklemezseniz, çalışma süresi sizin için varsayılan uç noktaları ekler.</span><span class="sxs-lookup"><span data-stu-id="d66e6-128">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="d66e6-129">Varsayılan uç noktalar, bağlamalar ve davranışlar hakkında daha fazla bilgi için WCF Hizmetleri için [Basitleştirilmiş Yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md) ve [Basitleştirilmiş Yapılandırma'ya](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="d66e6-129">For more information about default endpoints, bindings, and behaviors see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
11. <span data-ttu-id="d66e6-130">Hizmetin doğru şekilde barındırıldığından emin olmak için Internet Explorer'ın bir örneğini açın ve hizmetin URL'sine göz atın:`http://localhost/IISHostedCalc/Service.svc`</span><span class="sxs-lookup"><span data-stu-id="d66e6-130">To make sure the service is hosted correctly, open an instance of Internet Explorer and browse to the service's URL: `http://localhost/IISHostedCalc/Service.svc`</span></span>  
  
## <a name="example"></a><span data-ttu-id="d66e6-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="d66e6-131">Example</span></span>  
 <span data-ttu-id="d66e6-132">Aşağıda, IIS barındırılan hesap makinesi hizmeti için kodun tam listesi veremivettir.</span><span class="sxs-lookup"><span data-stu-id="d66e6-132">The following is a complete listing of the code for the IIS hosted calculator service.</span></span>  
  
 [!code-csharp[C_HowTo_HostInIIS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#1)]
 [!code-vb[C_HowTo_HostInIIS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#1)]
 [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]  
  
## <a name="see-also"></a><span data-ttu-id="d66e6-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d66e6-133">See also</span></span>

- [<span data-ttu-id="d66e6-134">Internet Information Services'te Barındırma</span><span class="sxs-lookup"><span data-stu-id="d66e6-134">Hosting in Internet Information Services</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)
- [<span data-ttu-id="d66e6-135">Barındırma Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="d66e6-135">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)
- [<span data-ttu-id="d66e6-136">WCF Hizmetleri ve ASP.NET</span><span class="sxs-lookup"><span data-stu-id="d66e6-136">WCF Services and ASP.NET</span></span>](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)
- [<span data-ttu-id="d66e6-137">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="d66e6-137">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
- <span data-ttu-id="d66e6-138">[Windows Server App Kumaş Barındırma Özellikleri](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="d66e6-138">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
