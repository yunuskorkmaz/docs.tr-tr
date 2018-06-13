---
title: "Nasıl yapılır: IIS'de WCF Hizmeti Barındırma"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b044b1c9-c1e5-4c9f-84d8-0f02f4537f8b
ms.openlocfilehash: a1759434d259cdffe1dac6b19a6582bfb83784bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492491"
---
# <a name="how-to-host-a-wcf-service-in-iis"></a><span data-ttu-id="47984-102">Nasıl yapılır: IIS'de WCF Hizmeti Barındırma</span><span class="sxs-lookup"><span data-stu-id="47984-102">How to: Host a WCF Service in IIS</span></span>
<span data-ttu-id="47984-103">Bu konu, Internet Information Services (IIS) barındırılan bir Windows Communication Foundation (WCF) hizmetini oluşturmak için gereken temel adımlarda özetler.</span><span class="sxs-lookup"><span data-stu-id="47984-103">This topic outlines the basic steps required to create a Windows Communication Foundation (WCF) service that is hosted in Internet Information Services (IIS).</span></span> <span data-ttu-id="47984-104">Bu konu, IIS ile bilgi sahibiyseniz ve IIS uygulamaları oluşturmak ve yönetmek için IIS Yönetim Aracı'nı kullanmayı öğrenme varsayar.</span><span class="sxs-lookup"><span data-stu-id="47984-104">This topic assumes you are familiar with IIS and understand how to use the IIS management tool to create and manage IIS applications.</span></span> <span data-ttu-id="47984-105">IIS hakkında daha fazla bilgi için bkz: [Internet Information Services](http://go.microsoft.com/fwlink/?LinkId=132449).</span><span class="sxs-lookup"><span data-stu-id="47984-105">For more information about IIS see [Internet Information Services](http://go.microsoft.com/fwlink/?LinkId=132449).</span></span> <span data-ttu-id="47984-106">IIS ortamı çalıştırmalarında IIS özellikleri, işlem geri dönüştürme gibi tüm avantajlarından yararlanır bir WCF Hizmeti kapatma, sistem durumu izleme işlemi ve ileti tabanlı etkinleştirme boş.</span><span class="sxs-lookup"><span data-stu-id="47984-106">A WCF service that runs in the IIS environment takes full advantage of IIS features, such as process recycling, idle shutdown, process health monitoring, and message-based activation.</span></span> <span data-ttu-id="47984-107">Bu barındırma seçeneği IIS düzgün şekilde yapılandırılmasını gerektirir, ancak herhangi bir barındırma kod uygulamanın bir parçası yazılması gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="47984-107">This hosting option requires that IIS be properly configured, but it does not require that any hosting code be written as part of the application.</span></span> <span data-ttu-id="47984-108">IIS ile yalnızca bir HTTP aktarma barındırma kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47984-108">You can use IIS hosting only with an HTTP transport.</span></span>  
  
 <span data-ttu-id="47984-109">Hakkında daha fazla bilgi için WCF ve [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] etkileşim kurmak için bkz: [WCF hizmetleri ve ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="47984-109">For more information about how WCF and [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] interact, see [WCF Services and ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).</span></span> <span data-ttu-id="47984-110">Güvenlik yapılandırma hakkında daha fazla bilgi için bkz: [güvenlik](../../../../docs/framework/wcf/feature-details/security.md).</span><span class="sxs-lookup"><span data-stu-id="47984-110">For more information about configuring security, see [Security](../../../../docs/framework/wcf/feature-details/security.md).</span></span>  
  
 <span data-ttu-id="47984-111">Bu örnekte kaynak kopyası için bkz: [IIS barındırma kullanarak satır içi kod](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md).</span><span class="sxs-lookup"><span data-stu-id="47984-111">For the source copy of this example, see [IIS Hosting Using Inline Code](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md).</span></span>  
  
### <a name="to-create-a-service-hosted-by-iis"></a><span data-ttu-id="47984-112">IIS tarafından barındırılan bir hizmet oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="47984-112">To create a service hosted by IIS</span></span>  
  
1.  <span data-ttu-id="47984-113">IIS yüklü ve bilgisayarınızda çalışır durumda olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="47984-113">Confirm that IIS is installed and running on your computer.</span></span> <span data-ttu-id="47984-114">Yükleme ve IIS yapılandırma hakkında daha fazla bilgi için bkz: [yükleme ve IIS 7.0 yapılandırma](http://go.microsoft.com/fwlink/?LinkID=132128)</span><span class="sxs-lookup"><span data-stu-id="47984-114">For more information about installing and configuring IIS see [Installing and Configuring IIS 7.0](http://go.microsoft.com/fwlink/?LinkID=132128)</span></span>  
  
2.  <span data-ttu-id="47984-115">Uygulama dosyalarınızın "IISHostedCalcService" adlı yeni bir klasör oluşturun, emin [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] klasörünün içeriğini erişimi vardır ve bu uygulamada fiziksel olarak bulunan yeni bir IIS uygulama oluşturmak için IIS Yönetim Aracı'nı kullanın Dizin.</span><span class="sxs-lookup"><span data-stu-id="47984-115">Create a new folder for your application files called "IISHostedCalcService", ensure that [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] has access to the contents of the folder, and use the IIS management tool to create a new IIS application that is physically located in this application directory.</span></span> <span data-ttu-id="47984-116">Uygulama dizini kullanımı "IISHostedCalc" için bir diğer ad oluştururken.</span><span class="sxs-lookup"><span data-stu-id="47984-116">When creating an alias for the application directory use "IISHostedCalc".</span></span>  
  
3.  <span data-ttu-id="47984-117">Uygulama dizinindeki "service.svc" adlı yeni bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="47984-117">Create a new file named "service.svc" in the application directory.</span></span> <span data-ttu-id="47984-118">Aşağıdakileri ekleyerek bu dosyayı düzenlemek @ServiceHost öğesi.</span><span class="sxs-lookup"><span data-stu-id="47984-118">Edit this file by adding the following @ServiceHost element.</span></span>  
  
    ```  
    <%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService"%>  
    ```  
  
4.  <span data-ttu-id="47984-119">Uygulama dizininin içinde bir App_Code dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="47984-119">Create an App_Code subdirectory within the application directory.</span></span>  
  
5.  <span data-ttu-id="47984-120">App_Code alt dizinindeki adını da adlı bir kod dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="47984-120">Create a code file named Service.cs in the App_Code subdirectory.</span></span>  
  
6.  <span data-ttu-id="47984-121">Aşağıdaki using deyimlerini adını da dosyanın en üstüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="47984-121">Add the following using statements to the top of the Service.cs file.</span></span>  
  
    ```csharp  
    using System;  
    using System.ServiceModel;  
    ```  
  
7.  <span data-ttu-id="47984-122">Kullandıktan sonra aşağıdaki ad alanı bildirimi ekleyin deyimleri.</span><span class="sxs-lookup"><span data-stu-id="47984-122">Add the following namespace declaration after the using statements.</span></span>  
  
    ```csharp  
    namespace Microsoft.ServiceModel.Samples  
    {  
    }  
    ```  
  
8.  <span data-ttu-id="47984-123">Aşağıdaki kodda gösterildiği gibi ad alanı bildiriminin içinde hizmet sözleşmesini tanımlama.</span><span class="sxs-lookup"><span data-stu-id="47984-123">Define the service contract inside the namespace declaration as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInIIS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#11)]
     [!code-vb[c_HowTo_HostInIIS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#11)]  
  
9. <span data-ttu-id="47984-124">Hizmet sözleşme sonra tanımı aşağıdaki kodda gösterildiği gibi hizmet sözleşmesini uygulama.</span><span class="sxs-lookup"><span data-stu-id="47984-124">Implement the service contract after the service contract definition as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInIIS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#12)]
     [!code-vb[c_HowTo_HostInIIS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#12)]  
  
10. <span data-ttu-id="47984-125">Uygulama dizininde "Web.config" adlı bir dosya oluşturun ve aşağıdaki yapılandırma kodunu dosyasına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="47984-125">Create a file named "Web.config" in the application directory and add the following configuration code into the file.</span></span> <span data-ttu-id="47984-126">Çalışma zamanında WCF altyapı bilgileri istemci uygulamaları ile iletişim kurabilen bir uç nokta oluşturmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="47984-126">At runtime, the WCF infrastructure uses the information to construct an endpoint that client applications can communicate with.</span></span>  
  
     [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]      
  
     <span data-ttu-id="47984-127">Bu örnek, yapılandırma dosyasında uç noktalar açıkça belirtir.</span><span class="sxs-lookup"><span data-stu-id="47984-127">This example explicitly specifies endpoints in the configuration file.</span></span> <span data-ttu-id="47984-128">Hizmeti için uç nokta eklemezseniz çalışma zamanı varsayılan uç noktaları ekler.</span><span class="sxs-lookup"><span data-stu-id="47984-128">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="47984-129">Varsayılan uç noktalar, bağlamaları ve davranışları bakın hakkında daha fazla bilgi için [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="47984-129">For more information about default endpoints, bindings, and behaviors see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
11. <span data-ttu-id="47984-130">Hizmet doğru şekilde barındırılan emin olmak için Internet Explorer ve hizmetin URL'ye örneği açın: `http://localhost/IISHostedCalc/Service.svc`</span><span class="sxs-lookup"><span data-stu-id="47984-130">To make sure the service is hosted correctly, open an instance of Internet Explorer and browse to the service's URL: `http://localhost/IISHostedCalc/Service.svc`</span></span>  
  
## <a name="example"></a><span data-ttu-id="47984-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="47984-131">Example</span></span>  
 <span data-ttu-id="47984-132">Barındırılan hesaplayıcı hizmetin IIS kodunu tam listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="47984-132">The following is a complete listing of the code for the IIS hosted calculator service.</span></span>  
  
 [!code-csharp[C_HowTo_HostInIIS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#1)] 
 [!code-vb[C_HowTo_HostInIIS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#1)] 
 [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]  
  
## <a name="see-also"></a><span data-ttu-id="47984-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="47984-133">See Also</span></span>  
 [<span data-ttu-id="47984-134">Internet Information Services'te Barındırma</span><span class="sxs-lookup"><span data-stu-id="47984-134">Hosting in Internet Information Services</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 [<span data-ttu-id="47984-135">Barındırma Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="47984-135">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)  
 [<span data-ttu-id="47984-136">WCF Hizmetleri ve ASP.NET</span><span class="sxs-lookup"><span data-stu-id="47984-136">WCF Services and ASP.NET</span></span>](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)  
 [<span data-ttu-id="47984-137">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="47984-137">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)  
 [<span data-ttu-id="47984-138">Windows Server App Fabric barındırma özellikleri</span><span class="sxs-lookup"><span data-stu-id="47984-138">Windows Server App Fabric Hosting Features</span></span>](http://go.microsoft.com/fwlink/?LinkId=201276)
