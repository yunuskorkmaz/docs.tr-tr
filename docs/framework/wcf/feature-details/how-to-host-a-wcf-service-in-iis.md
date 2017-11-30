---
title: "Nasıl yapılır: IIS'de WCF Hizmeti Barındırma"
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
ms.assetid: b044b1c9-c1e5-4c9f-84d8-0f02f4537f8b
caps.latest.revision: "28"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4fb3957543d6a0fcf3b375f9cb43ae089ac9d600
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-host-a-wcf-service-in-iis"></a><span data-ttu-id="00a9d-102">Nasıl yapılır: IIS'de WCF Hizmeti Barındırma</span><span class="sxs-lookup"><span data-stu-id="00a9d-102">How to: Host a WCF Service in IIS</span></span>
<span data-ttu-id="00a9d-103">Bu konu oluşturmak için gereken temel adımlarda özetler bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Internet Information Services (IIS) barındırılan hizmet.</span><span class="sxs-lookup"><span data-stu-id="00a9d-103">This topic outlines the basic steps required to create a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service that is hosted in Internet Information Services (IIS).</span></span> <span data-ttu-id="00a9d-104">Bu konu, IIS ile bilgi sahibiyseniz ve IIS uygulamaları oluşturmak ve yönetmek için IIS Yönetim Aracı'nı kullanmayı öğrenme varsayar.</span><span class="sxs-lookup"><span data-stu-id="00a9d-104">This topic assumes you are familiar with IIS and understand how to use the IIS management tool to create and manage IIS applications.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="00a9d-105">IIS bkz [Internet Information Services](http://go.microsoft.com/fwlink/?LinkId=132449).</span><span class="sxs-lookup"><span data-stu-id="00a9d-105"> IIS see [Internet Information Services](http://go.microsoft.com/fwlink/?LinkId=132449).</span></span> <span data-ttu-id="00a9d-106">A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] IIS ortamında çalışan bir hizmete işlem geri dönüştürme, boşta kapatma, sistem durumu izleme işlemi ve ileti tabanlı etkinleştirme gibi IIS özellikleri tüm avantajlarından yararlanır.</span><span class="sxs-lookup"><span data-stu-id="00a9d-106">A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that runs in the IIS environment takes full advantage of IIS features, such as process recycling, idle shutdown, process health monitoring, and message-based activation.</span></span> <span data-ttu-id="00a9d-107">Bu barındırma seçeneği IIS düzgün şekilde yapılandırılmasını gerektirir, ancak herhangi bir barındırma kod uygulamanın bir parçası yazılması gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="00a9d-107">This hosting option requires that IIS be properly configured, but it does not require that any hosting code be written as part of the application.</span></span> <span data-ttu-id="00a9d-108">IIS ile yalnızca bir HTTP aktarma barındırma kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00a9d-108">You can use IIS hosting only with an HTTP transport.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="00a9d-109">nasıl [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ve [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] etkileşim kurmak için bkz: [WCF hizmetleri ve ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="00a9d-109"> how [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] and [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] interact, see [WCF Services and ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="00a9d-110">bkz: güvenlik, yapılandırma [güvenlik](../../../../docs/framework/wcf/feature-details/security.md).</span><span class="sxs-lookup"><span data-stu-id="00a9d-110"> configuring security, see [Security](../../../../docs/framework/wcf/feature-details/security.md).</span></span>  
  
 <span data-ttu-id="00a9d-111">Bu örnekte kaynak kopyası için bkz: [IIS barındırma kullanarak satır içi kod](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md).</span><span class="sxs-lookup"><span data-stu-id="00a9d-111">For the source copy of this example, see [IIS Hosting Using Inline Code](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md).</span></span>  
  
### <a name="to-create-a-service-hosted-by-iis"></a><span data-ttu-id="00a9d-112">IIS tarafından barındırılan bir hizmet oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="00a9d-112">To create a service hosted by IIS</span></span>  
  
1.  <span data-ttu-id="00a9d-113">IIS yüklü ve bilgisayarınızda çalışır durumda olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="00a9d-113">Confirm that IIS is installed and running on your computer.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="00a9d-114">IIS yükleniyor ve yapılandırılıyor bkz [yükleme ve IIS 7.0 yapılandırma](http://go.microsoft.com/fwlink/?LinkID=132128)</span><span class="sxs-lookup"><span data-stu-id="00a9d-114"> installing and configuring IIS see [Installing and Configuring IIS 7.0](http://go.microsoft.com/fwlink/?LinkID=132128)</span></span>  
  
2.  <span data-ttu-id="00a9d-115">Uygulama dosyalarınızın "IISHostedCalcService" adlı yeni bir klasör oluşturun, emin [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] klasörünün içeriğini erişimi vardır ve bu uygulamada fiziksel olarak bulunan yeni bir IIS uygulama oluşturmak için IIS Yönetim Aracı'nı kullanın Dizin.</span><span class="sxs-lookup"><span data-stu-id="00a9d-115">Create a new folder for your application files called "IISHostedCalcService", ensure that [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] has access to the contents of the folder, and use the IIS management tool to create a new IIS application that is physically located in this application directory.</span></span> <span data-ttu-id="00a9d-116">Uygulama dizini kullanımı "IISHostedCalc" için bir diğer ad oluştururken.</span><span class="sxs-lookup"><span data-stu-id="00a9d-116">When creating an alias for the application directory use "IISHostedCalc".</span></span>  
  
3.  <span data-ttu-id="00a9d-117">Uygulama dizinindeki "service.svc" adlı yeni bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="00a9d-117">Create a new file named "service.svc" in the application directory.</span></span> <span data-ttu-id="00a9d-118">Aşağıdakileri ekleyerek bu dosyayı düzenlemek @ServiceHost öğesi.</span><span class="sxs-lookup"><span data-stu-id="00a9d-118">Edit this file by adding the following @ServiceHost element.</span></span>  
  
    ```  
    <%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService"%>  
    ```  
  
4.  <span data-ttu-id="00a9d-119">Uygulama dizininin içinde bir App_Code dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="00a9d-119">Create an App_Code subdirectory within the application directory.</span></span>  
  
5.  <span data-ttu-id="00a9d-120">App_Code alt dizinindeki adını da adlı bir kod dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="00a9d-120">Create a code file named Service.cs in the App_Code subdirectory.</span></span>  
  
6.  <span data-ttu-id="00a9d-121">Aşağıdaki using deyimlerini adını da dosyanın en üstüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="00a9d-121">Add the following using statements to the top of the Service.cs file.</span></span>  
  
    ```csharp  
    using System;  
    using System.ServiceModel;  
    ```  
  
7.  <span data-ttu-id="00a9d-122">Kullandıktan sonra aşağıdaki ad alanı bildirimi ekleyin deyimleri.</span><span class="sxs-lookup"><span data-stu-id="00a9d-122">Add the following namespace declaration after the using statements.</span></span>  
  
    ```csharp  
    namespace Microsoft.ServiceModel.Samples  
    {  
    }  
    ```  
  
8.  <span data-ttu-id="00a9d-123">Aşağıdaki kodda gösterildiği gibi ad alanı bildiriminin içinde hizmet sözleşmesini tanımlama.</span><span class="sxs-lookup"><span data-stu-id="00a9d-123">Define the service contract inside the namespace declaration as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInIIS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#11)]
     [!code-vb[c_HowTo_HostInIIS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#11)]  
  
9. <span data-ttu-id="00a9d-124">Hizmet sözleşme sonra tanımı aşağıdaki kodda gösterildiği gibi hizmet sözleşmesini uygulama.</span><span class="sxs-lookup"><span data-stu-id="00a9d-124">Implement the service contract after the service contract definition as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInIIS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#12)]
     [!code-vb[c_HowTo_HostInIIS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#12)]  
  
10. <span data-ttu-id="00a9d-125">Uygulama dizininde "Web.config" adlı bir dosya oluşturun ve aşağıdaki yapılandırma kodunu dosyasına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="00a9d-125">Create a file named "Web.config" in the application directory and add the following configuration code into the file.</span></span> <span data-ttu-id="00a9d-126">Çalışma zamanında [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] altyapı istemci uygulamaları ile iletişim kurabilen bir uç nokta oluşturmak için bilgileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="00a9d-126">At runtime, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastructure uses the information to construct an endpoint that client applications can communicate with.</span></span>  
  
     [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]      
  
     <span data-ttu-id="00a9d-127">Bu örnek, yapılandırma dosyasında uç noktalar açıkça belirtir.</span><span class="sxs-lookup"><span data-stu-id="00a9d-127">This example explicitly specifies endpoints in the configuration file.</span></span> <span data-ttu-id="00a9d-128">Hizmeti için uç nokta eklemezseniz çalışma zamanı varsayılan uç noktaları ekler.</span><span class="sxs-lookup"><span data-stu-id="00a9d-128">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="00a9d-129">Varsayılan uç noktaları, bağlamaları ve davranışları bakın [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="00a9d-129"> default endpoints, bindings, and behaviors see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
11. <span data-ttu-id="00a9d-130">Hizmet doğru şekilde barındırılan emin olmak için Internet Explorer ve hizmetin URL'ye örneği açın:`http://localhost/IISHostedCalc/Service.svc`</span><span class="sxs-lookup"><span data-stu-id="00a9d-130">To make sure the service is hosted correctly, open an instance of Internet Explorer and browse to the service's URL: `http://localhost/IISHostedCalc/Service.svc`</span></span>  
  
## <a name="example"></a><span data-ttu-id="00a9d-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="00a9d-131">Example</span></span>  
 <span data-ttu-id="00a9d-132">Barındırılan hesaplayıcı hizmetin IIS kodunu tam listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="00a9d-132">The following is a complete listing of the code for the IIS hosted calculator service.</span></span>  
  
 [!code-csharp[C_HowTo_HostInIIS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#1)] 
 [!code-vb[C_HowTo_HostInIIS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#1)] 
 [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]  
  
## <a name="see-also"></a><span data-ttu-id="00a9d-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="00a9d-133">See Also</span></span>  
 [<span data-ttu-id="00a9d-134">Internet Information Services'te barındırma</span><span class="sxs-lookup"><span data-stu-id="00a9d-134">Hosting in Internet Information Services</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 [<span data-ttu-id="00a9d-135">Barındırma hizmetleri</span><span class="sxs-lookup"><span data-stu-id="00a9d-135">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)  
 [<span data-ttu-id="00a9d-136">WCF hizmetleri ve ASP.NET</span><span class="sxs-lookup"><span data-stu-id="00a9d-136">WCF Services and ASP.NET</span></span>](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)  
 [<span data-ttu-id="00a9d-137">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="00a9d-137">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)  
 [<span data-ttu-id="00a9d-138">Windows Server App Fabric barındırma özellikleri</span><span class="sxs-lookup"><span data-stu-id="00a9d-138">Windows Server App Fabric Hosting Features</span></span>](http://go.microsoft.com/fwlink/?LinkId=201276)
