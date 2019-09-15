---
title: "Nasıl yapılır: IIS'de WCF Hizmeti Barındırma"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b044b1c9-c1e5-4c9f-84d8-0f02f4537f8b
ms.openlocfilehash: ad1fb7d289dea3396b4edb4d3b3e9fb7fb1891e3
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972415"
---
# <a name="how-to-host-a-wcf-service-in-iis"></a><span data-ttu-id="bbcdd-102">Nasıl yapılır: IIS'de WCF Hizmeti Barındırma</span><span class="sxs-lookup"><span data-stu-id="bbcdd-102">How to: Host a WCF Service in IIS</span></span>
<span data-ttu-id="bbcdd-103">Bu konuda, Internet Information Services (IIS) içinde barındırılan Windows Communication Foundation (WCF) hizmeti oluşturmak için gereken temel adımlar özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="bbcdd-103">This topic outlines the basic steps required to create a Windows Communication Foundation (WCF) service that is hosted in Internet Information Services (IIS).</span></span> <span data-ttu-id="bbcdd-104">Bu konu, IIS 'yi bildiğiniz ve IIS yönetim aracını kullanarak IIS uygulamaları oluşturma ve yönetme hakkında bilgi sahibi olduğunuz varsayılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bbcdd-104">This topic assumes you are familiar with IIS and understand how to use the IIS management tool to create and manage IIS applications.</span></span> <span data-ttu-id="bbcdd-105">IIS hakkında daha fazla bilgi için bkz. [Internet Information Services](https://go.microsoft.com/fwlink/?LinkId=132449).</span><span class="sxs-lookup"><span data-stu-id="bbcdd-105">For more information about IIS see [Internet Information Services](https://go.microsoft.com/fwlink/?LinkId=132449).</span></span> <span data-ttu-id="bbcdd-106">IIS ortamında çalışan bir WCF hizmeti, işlem geri dönüştürme, boşta kalma, işlem sistem durumu izleme ve ileti tabanlı etkinleştirme gibi IIS özelliklerinden tam olarak yararlanır.</span><span class="sxs-lookup"><span data-stu-id="bbcdd-106">A WCF service that runs in the IIS environment takes full advantage of IIS features, such as process recycling, idle shutdown, process health monitoring, and message-based activation.</span></span> <span data-ttu-id="bbcdd-107">Bu barındırma seçeneği IIS 'nin düzgün şekilde yapılandırılmasını gerektirir, ancak herhangi bir barındırma kodunun uygulamanın bir parçası olarak yazılmasını gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="bbcdd-107">This hosting option requires that IIS be properly configured, but it does not require that any hosting code be written as part of the application.</span></span> <span data-ttu-id="bbcdd-108">Yalnızca bir HTTP taşıması ile IIS barındırma kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bbcdd-108">You can use IIS hosting only with an HTTP transport.</span></span>  
  
 <span data-ttu-id="bbcdd-109">WCF ve ASP.NET ile etkileşim kurma hakkında daha fazla bilgi için bkz. [WCF Hizmetleri ve ASP.net](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="bbcdd-109">For more information about how WCF and ASP.NET interact, see [WCF Services and ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).</span></span> <span data-ttu-id="bbcdd-110">Güvenliği yapılandırma hakkında daha fazla bilgi için bkz. [güvenlik](../../../../docs/framework/wcf/feature-details/security.md).</span><span class="sxs-lookup"><span data-stu-id="bbcdd-110">For more information about configuring security, see [Security](../../../../docs/framework/wcf/feature-details/security.md).</span></span>  
  
 <span data-ttu-id="bbcdd-111">Bu örneğin kaynak kopyası için bkz. [satır Içi kod kullanarak IIS barındırma](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md).</span><span class="sxs-lookup"><span data-stu-id="bbcdd-111">For the source copy of this example, see [IIS Hosting Using Inline Code](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md).</span></span>  
  
### <a name="to-create-a-service-hosted-by-iis"></a><span data-ttu-id="bbcdd-112">IIS tarafından barındırılan bir hizmet oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="bbcdd-112">To create a service hosted by IIS</span></span>  
  
1. <span data-ttu-id="bbcdd-113">IIS 'nin bilgisayarınızda yüklü olduğundan ve çalıştığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="bbcdd-113">Confirm that IIS is installed and running on your computer.</span></span> <span data-ttu-id="bbcdd-114">IIS yükleme ve yapılandırma hakkında daha fazla bilgi için bkz. [ııs 7,0 yükleme ve yapılandırma](https://go.microsoft.com/fwlink/?LinkID=132128)</span><span class="sxs-lookup"><span data-stu-id="bbcdd-114">For more information about installing and configuring IIS see [Installing and Configuring IIS 7.0](https://go.microsoft.com/fwlink/?LinkID=132128)</span></span>  
  
2. <span data-ttu-id="bbcdd-115">"IISHostedCalcService" adlı uygulama dosyalarınız için yeni bir klasör oluşturun, ASP.NET klasörünün içeriğine erişebildiğinden emin olun ve bu uygulama dizininde fiziksel olarak bulunan yeni bir IIS uygulaması oluşturmak için IIS Yönetim Aracı 'nı kullanın.</span><span class="sxs-lookup"><span data-stu-id="bbcdd-115">Create a new folder for your application files called "IISHostedCalcService", ensure that ASP.NET has access to the contents of the folder, and use the IIS management tool to create a new IIS application that is physically located in this application directory.</span></span> <span data-ttu-id="bbcdd-116">Uygulama dizini için bir diğer ad oluştururken "IISHostedCalc" kullanın.</span><span class="sxs-lookup"><span data-stu-id="bbcdd-116">When creating an alias for the application directory use "IISHostedCalc".</span></span>  
  
3. <span data-ttu-id="bbcdd-117">Uygulama dizininde "Service. svc" adlı yeni bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bbcdd-117">Create a new file named "service.svc" in the application directory.</span></span> <span data-ttu-id="bbcdd-118">Aşağıdaki @ServiceHost öğeyi ekleyerek bu dosyayı düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="bbcdd-118">Edit this file by adding the following @ServiceHost element.</span></span>  
  
   ```
   <%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService"%>
   ```  
  
4. <span data-ttu-id="bbcdd-119">Uygulama dizini içinde bir App_Code alt dizini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bbcdd-119">Create an App_Code subdirectory within the application directory.</span></span>  
  
5. <span data-ttu-id="bbcdd-120">Service.cs adlı bir kod dosyasını App_Code alt dizininde oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bbcdd-120">Create a code file named Service.cs in the App_Code subdirectory.</span></span>  
  
6. <span data-ttu-id="bbcdd-121">Aşağıdaki using deyimlerini Service.cs dosyasının en üstüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bbcdd-121">Add the following using statements to the top of the Service.cs file.</span></span>  
  
    ```csharp  
    using System;  
    using System.ServiceModel;  
    ```  
  
7. <span data-ttu-id="bbcdd-122">Using deyimlerinden sonra aşağıdaki ad alanı bildirimini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bbcdd-122">Add the following namespace declaration after the using statements.</span></span>  
  
    ```csharp  
    namespace Microsoft.ServiceModel.Samples  
    {  
    }  
    ```  
  
8. <span data-ttu-id="bbcdd-123">Aşağıdaki kodda gösterildiği gibi, ad alanı bildiriminde hizmet sözleşmesini tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="bbcdd-123">Define the service contract inside the namespace declaration as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInIIS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#11)]
     [!code-vb[c_HowTo_HostInIIS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#11)]  
  
9. <span data-ttu-id="bbcdd-124">Hizmet sözleşmesini, aşağıdaki kodda gösterildiği gibi hizmet sözleşmesi tanımından sonra uygulayın.</span><span class="sxs-lookup"><span data-stu-id="bbcdd-124">Implement the service contract after the service contract definition as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInIIS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#12)]
     [!code-vb[c_HowTo_HostInIIS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#12)]  
  
10. <span data-ttu-id="bbcdd-125">Uygulama dizininde "Web. config" adlı bir dosya oluşturun ve aşağıdaki yapılandırma kodunu dosyaya ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bbcdd-125">Create a file named "Web.config" in the application directory and add the following configuration code into the file.</span></span> <span data-ttu-id="bbcdd-126">Çalışma zamanında, WCF altyapısı, istemci uygulamaların iletişim kurabildiği bir uç nokta oluşturmak için bu bilgileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="bbcdd-126">At runtime, the WCF infrastructure uses the information to construct an endpoint that client applications can communicate with.</span></span>  
  
     [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]      
  
     <span data-ttu-id="bbcdd-127">Bu örnek, yapılandırma dosyasındaki uç noktaları açıkça belirtir.</span><span class="sxs-lookup"><span data-stu-id="bbcdd-127">This example explicitly specifies endpoints in the configuration file.</span></span> <span data-ttu-id="bbcdd-128">Hizmete herhangi bir uç nokta eklemediğiniz takdirde, çalışma zamanı sizin için varsayılan uç noktaları ekler.</span><span class="sxs-lookup"><span data-stu-id="bbcdd-128">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="bbcdd-129">Varsayılan uç noktalar, bağlamalar ve davranışlar hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="bbcdd-129">For more information about default endpoints, bindings, and behaviors see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
11. <span data-ttu-id="bbcdd-130">Hizmetin doğru şekilde barındırıldığından emin olmak için Internet Explorer 'ın bir örneğini açın ve hizmetin URL 'sine gidin:`http://localhost/IISHostedCalc/Service.svc`</span><span class="sxs-lookup"><span data-stu-id="bbcdd-130">To make sure the service is hosted correctly, open an instance of Internet Explorer and browse to the service's URL: `http://localhost/IISHostedCalc/Service.svc`</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbcdd-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="bbcdd-131">Example</span></span>  
 <span data-ttu-id="bbcdd-132">Aşağıda, IIS tarafından barındırılan Hesaplayıcı hizmeti için kodun tamamen bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="bbcdd-132">The following is a complete listing of the code for the IIS hosted calculator service.</span></span>  
  
 [!code-csharp[C_HowTo_HostInIIS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#1)] 
 [!code-vb[C_HowTo_HostInIIS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#1)] 
 [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]  
  
## <a name="see-also"></a><span data-ttu-id="bbcdd-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bbcdd-133">See also</span></span>

- [<span data-ttu-id="bbcdd-134">Internet Information Services'te Barındırma</span><span class="sxs-lookup"><span data-stu-id="bbcdd-134">Hosting in Internet Information Services</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)
- [<span data-ttu-id="bbcdd-135">Barındırma Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="bbcdd-135">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)
- [<span data-ttu-id="bbcdd-136">WCF Hizmetleri ve ASP.NET</span><span class="sxs-lookup"><span data-stu-id="bbcdd-136">WCF Services and ASP.NET</span></span>](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)
- [<span data-ttu-id="bbcdd-137">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="bbcdd-137">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
- [<span data-ttu-id="bbcdd-138">Windows Server App Fabric barındırma özellikleri</span><span class="sxs-lookup"><span data-stu-id="bbcdd-138">Windows Server App Fabric Hosting Features</span></span>](https://go.microsoft.com/fwlink/?LinkId=201276)
