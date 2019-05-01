---
title: "Nasıl yapılır: IIS'de WCF Hizmeti Barındırma"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b044b1c9-c1e5-4c9f-84d8-0f02f4537f8b
ms.openlocfilehash: f106ce1bca67f8b88df0835496eea0b3297ac946
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000837"
---
# <a name="how-to-host-a-wcf-service-in-iis"></a><span data-ttu-id="47932-102">Nasıl yapılır: IIS'de WCF Hizmeti Barındırma</span><span class="sxs-lookup"><span data-stu-id="47932-102">How to: Host a WCF Service in IIS</span></span>
<span data-ttu-id="47932-103">Bu konuda, Internet Information Services (IIS) barındırılan Windows Communication Foundation (WCF) hizmet oluşturmak için gerekli temel adımlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="47932-103">This topic outlines the basic steps required to create a Windows Communication Foundation (WCF) service that is hosted in Internet Information Services (IIS).</span></span> <span data-ttu-id="47932-104">Bu konuda, IIS ile ilgili bilgi sahibi olduğunuz ve IIS uygulamaları oluşturmak ve yönetmek için IIS Yönetim Aracı'nı kullanmayı öğrenmenize varsayılır.</span><span class="sxs-lookup"><span data-stu-id="47932-104">This topic assumes you are familiar with IIS and understand how to use the IIS management tool to create and manage IIS applications.</span></span> <span data-ttu-id="47932-105">IIS hakkında daha fazla bilgi için bkz. [Internet Information Services](https://go.microsoft.com/fwlink/?LinkId=132449).</span><span class="sxs-lookup"><span data-stu-id="47932-105">For more information about IIS see [Internet Information Services](https://go.microsoft.com/fwlink/?LinkId=132449).</span></span> <span data-ttu-id="47932-106">Bir WCF Hizmeti IIS ortamında çalışır gibi işlem geri dönüştürme, IIS özellikleri tüm avantajlarından yararlanır, kapatma, sistem durumu izleme işlemi ve ileti tabanlı etkinleştirme boş.</span><span class="sxs-lookup"><span data-stu-id="47932-106">A WCF service that runs in the IIS environment takes full advantage of IIS features, such as process recycling, idle shutdown, process health monitoring, and message-based activation.</span></span> <span data-ttu-id="47932-107">Bu barındırma seçeneği IIS düzgün şekilde yapılandırılmasını gerektirir, ancak uygulamanın bir parçası herhangi bir barındırma kod yazılmasını gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="47932-107">This hosting option requires that IIS be properly configured, but it does not require that any hosting code be written as part of the application.</span></span> <span data-ttu-id="47932-108">Yalnızca bir HTTP aktarımı ile IIS barındırma kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47932-108">You can use IIS hosting only with an HTTP transport.</span></span>  
  
 <span data-ttu-id="47932-109">Hakkında daha fazla bilgi için WCF ve [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] etkileşim kurmak için bkz: [WCF hizmetleri ve ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="47932-109">For more information about how WCF and [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] interact, see [WCF Services and ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).</span></span> <span data-ttu-id="47932-110">Güvenlik yapılandırma hakkında daha fazla bilgi için bkz. [güvenlik](../../../../docs/framework/wcf/feature-details/security.md).</span><span class="sxs-lookup"><span data-stu-id="47932-110">For more information about configuring security, see [Security](../../../../docs/framework/wcf/feature-details/security.md).</span></span>  
  
 <span data-ttu-id="47932-111">Bu örnekte kaynak kopyası için bkz: [IIS kullanarak satır içi kod barındırma](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md).</span><span class="sxs-lookup"><span data-stu-id="47932-111">For the source copy of this example, see [IIS Hosting Using Inline Code](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md).</span></span>  
  
### <a name="to-create-a-service-hosted-by-iis"></a><span data-ttu-id="47932-112">IIS tarafından barındırılan bir hizmet oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="47932-112">To create a service hosted by IIS</span></span>  
  
1. <span data-ttu-id="47932-113">IIS yüklü ve bilgisayarınızda çalışmakta olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="47932-113">Confirm that IIS is installed and running on your computer.</span></span> <span data-ttu-id="47932-114">Yükleme ve IIS yapılandırma hakkında daha fazla bilgi için bkz: [yükleme ve IIS 7.0 yapılandırma](https://go.microsoft.com/fwlink/?LinkID=132128)</span><span class="sxs-lookup"><span data-stu-id="47932-114">For more information about installing and configuring IIS see [Installing and Configuring IIS 7.0](https://go.microsoft.com/fwlink/?LinkID=132128)</span></span>  
  
2. <span data-ttu-id="47932-115">"IISHostedCalcService" adlı uygulama dosyalarınızı için yeni bir klasör oluşturun, emin [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] klasörünün içeriğini erişimi vardır ve bu uygulamada bulunan fiziksel olarak yeni bir IIS uygulama oluşturmak için IIS Yönetim Aracı'nı kullanın Dizin.</span><span class="sxs-lookup"><span data-stu-id="47932-115">Create a new folder for your application files called "IISHostedCalcService", ensure that [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] has access to the contents of the folder, and use the IIS management tool to create a new IIS application that is physically located in this application directory.</span></span> <span data-ttu-id="47932-116">Uygulamanın directory kullan "IISHostedCalc" için bir diğer ad oluştururken.</span><span class="sxs-lookup"><span data-stu-id="47932-116">When creating an alias for the application directory use "IISHostedCalc".</span></span>  
  
3. <span data-ttu-id="47932-117">Uygulama dizininde, "service.svc" adlı yeni bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="47932-117">Create a new file named "service.svc" in the application directory.</span></span> <span data-ttu-id="47932-118">Aşağıdakileri ekleyerek bu dosyayı Düzenle @ServiceHost öğesi.</span><span class="sxs-lookup"><span data-stu-id="47932-118">Edit this file by adding the following @ServiceHost element.</span></span>  
  
    ```  
    <%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService"%>  
    ```  
  
4. <span data-ttu-id="47932-119">Uygulama dizininin içinde bir App_Code dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="47932-119">Create an App_Code subdirectory within the application directory.</span></span>  
  
5. <span data-ttu-id="47932-120">App_Code alt dizinde adını da adlı bir kod dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="47932-120">Create a code file named Service.cs in the App_Code subdirectory.</span></span>  
  
6. <span data-ttu-id="47932-121">Aşağıdaki using deyimlerini adını da dosyasının en üstüne.</span><span class="sxs-lookup"><span data-stu-id="47932-121">Add the following using statements to the top of the Service.cs file.</span></span>  
  
    ```csharp  
    using System;  
    using System.ServiceModel;  
    ```  
  
7. <span data-ttu-id="47932-122">Kullandıktan sonra aşağıdaki ad alanı bildirimi ekleyin deyimleri.</span><span class="sxs-lookup"><span data-stu-id="47932-122">Add the following namespace declaration after the using statements.</span></span>  
  
    ```csharp  
    namespace Microsoft.ServiceModel.Samples  
    {  
    }  
    ```  
  
8. <span data-ttu-id="47932-123">Aşağıdaki kodda gösterildiği gibi ad alanı bildirimi içinde hizmet sözleşmesini tanımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="47932-123">Define the service contract inside the namespace declaration as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInIIS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#11)]
     [!code-vb[c_HowTo_HostInIIS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#11)]  
  
9. <span data-ttu-id="47932-124">Hizmet sözleşme sonra tanımı aşağıdaki kodda gösterildiği gibi hizmet sözleşmesini uygulama.</span><span class="sxs-lookup"><span data-stu-id="47932-124">Implement the service contract after the service contract definition as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInIIS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#12)]
     [!code-vb[c_HowTo_HostInIIS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#12)]  
  
10. <span data-ttu-id="47932-125">Uygulama dizininde "Web.config" adlı bir dosya oluşturun ve aşağıdaki kodu yapılandırma dosyasına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="47932-125">Create a file named "Web.config" in the application directory and add the following configuration code into the file.</span></span> <span data-ttu-id="47932-126">Çalışma zamanında, WCF altyapısı, istemci uygulamaları ile iletişim kurabilen bir uç nokta oluşturmak için bilgileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="47932-126">At runtime, the WCF infrastructure uses the information to construct an endpoint that client applications can communicate with.</span></span>  
  
     [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]      
  
     <span data-ttu-id="47932-127">Bu örnek, uç noktaları yapılandırma dosyasında açıkça belirtir.</span><span class="sxs-lookup"><span data-stu-id="47932-127">This example explicitly specifies endpoints in the configuration file.</span></span> <span data-ttu-id="47932-128">Hizmet için uç nokta eklemezseniz, çalışma zamanı varsayılan uç noktalar ekler.</span><span class="sxs-lookup"><span data-stu-id="47932-128">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="47932-129">Varsayılan uç noktaları, bağlamalar ve davranışları bakın hakkında daha fazla bilgi için [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="47932-129">For more information about default endpoints, bindings, and behaviors see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
11. <span data-ttu-id="47932-130">Hizmet doğru şekilde barındırılan emin olmak için Internet Explorer ve hizmetin URL'ye Gözat örneğini açın: `http://localhost/IISHostedCalc/Service.svc`</span><span class="sxs-lookup"><span data-stu-id="47932-130">To make sure the service is hosted correctly, open an instance of Internet Explorer and browse to the service's URL: `http://localhost/IISHostedCalc/Service.svc`</span></span>  
  
## <a name="example"></a><span data-ttu-id="47932-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="47932-131">Example</span></span>  
 <span data-ttu-id="47932-132">Barındırılan hesaplayıcı hizmeti IIS için kod tam listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="47932-132">The following is a complete listing of the code for the IIS hosted calculator service.</span></span>  
  
 [!code-csharp[C_HowTo_HostInIIS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#1)] 
 [!code-vb[C_HowTo_HostInIIS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#1)] 
 [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]  
  
## <a name="see-also"></a><span data-ttu-id="47932-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47932-133">See also</span></span>

- [<span data-ttu-id="47932-134">Internet Information Services'te Barındırma</span><span class="sxs-lookup"><span data-stu-id="47932-134">Hosting in Internet Information Services</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)
- [<span data-ttu-id="47932-135">Barındırma Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="47932-135">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)
- [<span data-ttu-id="47932-136">WCF Hizmetleri ve ASP.NET</span><span class="sxs-lookup"><span data-stu-id="47932-136">WCF Services and ASP.NET</span></span>](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)
- [<span data-ttu-id="47932-137">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="47932-137">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
- [<span data-ttu-id="47932-138">Windows Server App Fabric barındırma özellikleri</span><span class="sxs-lookup"><span data-stu-id="47932-138">Windows Server App Fabric Hosting Features</span></span>](https://go.microsoft.com/fwlink/?LinkId=201276)
