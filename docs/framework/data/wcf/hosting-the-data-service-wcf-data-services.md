---
title: "Veri Hizmeti (WCF Veri Hizmetleri) barındırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, Windows Communication Foundation
ms.assetid: b48f42ce-22ce-4f8d-8f0d-f7ddac9125ee
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e8819e8127d16b83d531dc6bdcd3af88245c695e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="hosting-the-data-service-wcf-data-services"></a><span data-ttu-id="b0df7-102">Veri Hizmeti (WCF Veri Hizmetleri) barındırma</span><span class="sxs-lookup"><span data-stu-id="b0df7-102">Hosting the Data Service (WCF Data Services)</span></span>
<span data-ttu-id="b0df7-103">Kullanarak [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], olarak kullanıma sunan bir hizmet oluşturabilmeniz için bir [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] akış.</span><span class="sxs-lookup"><span data-stu-id="b0df7-103">By using [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], you can create a service that exposes data as an [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed.</span></span> <span data-ttu-id="b0df7-104">Bu veri hizmeti öğesinden devralınan bir sınıf olarak tanımlanır <xref:System.Data.Services.DataService%601>.</span><span class="sxs-lookup"><span data-stu-id="b0df7-104">This data service is defined as a class that inherits from <xref:System.Data.Services.DataService%601>.</span></span> <span data-ttu-id="b0df7-105">Bu sınıf, istek iletilerini işlemek, veri kaynağına karşı güncelleştirmeleri gerçekleştirmek ve gerektirdiği şekilde yanıt iletileri oluşturmak için gereken işlevleri sağlar [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b0df7-105">This class provides the functionality required to process request messages, perform updates against the data source, and generate responses messages, as required by [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].</span></span> <span data-ttu-id="b0df7-106">Ancak, bir veri hizmeti bağlamak ve ağ yuvada gelen HTTP isteklerini dinlemeye.</span><span class="sxs-lookup"><span data-stu-id="b0df7-106">However, a data service cannot bind to and listen on a network socket for incoming HTTP requests.</span></span> <span data-ttu-id="b0df7-107">Bu gerekli işlevselliği için bir barındırma bileşenin veri hizmeti kullanır.</span><span class="sxs-lookup"><span data-stu-id="b0df7-107">For this required functionality, the data service relies on a hosting component.</span></span>  
  
 <span data-ttu-id="b0df7-108">Veri Hizmeti ana veri hizmeti adına aşağıdaki görevleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="b0df7-108">The data service host performs the following tasks on behalf of the data service:</span></span>  
  
-   <span data-ttu-id="b0df7-109">İsteklerini dinler ve bu istekleri için veri hizmeti yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="b0df7-109">Listens for requests and routes these requests to the data service.</span></span>  
  
-   <span data-ttu-id="b0df7-110">Her istek için veri hizmeti örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b0df7-110">Creates an instance of the data service for each request.</span></span>  
  
-   <span data-ttu-id="b0df7-111">Veri Hizmeti gelen istek işlemi istek sayısı.</span><span class="sxs-lookup"><span data-stu-id="b0df7-111">Requests that the data service process the incoming request.</span></span>  
  
-   <span data-ttu-id="b0df7-112">Veri hizmeti adına yanıt gönderir.</span><span class="sxs-lookup"><span data-stu-id="b0df7-112">Sends the response on behalf of the data service.</span></span>  
  
 <span data-ttu-id="b0df7-113">Veri hizmetini barındıran basitleştirmek için [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Windows Communication Foundation (WCF) ile tümleştirmek için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="b0df7-113">To simplify hosting a data service, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] is designed to integrate with Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="b0df7-114">Veri Hizmeti veri hizmeti konak görevi gören bir varsayılan WCF uygulaması sağlayan bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="b0df7-114">The data service provides a default WCF implementation that serves as the data service host in an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application.</span></span> <span data-ttu-id="b0df7-115">Bu nedenle, bir veri hizmeti aşağıdaki yollardan biriyle barındırabilir:</span><span class="sxs-lookup"><span data-stu-id="b0df7-115">Therefore, you can host a data service in one of the following ways:</span></span>  
  
-   <span data-ttu-id="b0df7-116">İçinde bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="b0df7-116">In an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application.</span></span>  
  
-   <span data-ttu-id="b0df7-117">Kendini barındıran WCF hizmetlerini destekleyen yönetilen bir uygulamada.</span><span class="sxs-lookup"><span data-stu-id="b0df7-117">In a managed application that supports self-hosted WCF services.</span></span>  
  
-   <span data-ttu-id="b0df7-118">Bazı diğer özel veri hizmeti ana bilgisayarı.</span><span class="sxs-lookup"><span data-stu-id="b0df7-118">In some other custom data service host.</span></span>  
  
## <a name="hosting-a-data-service-in-an-aspnet-application"></a><span data-ttu-id="b0df7-119">Bir ASP.NET uygulamasında veri hizmeti barındırma</span><span class="sxs-lookup"><span data-stu-id="b0df7-119">Hosting a Data Service in an ASP.NET Application</span></span>  
 <span data-ttu-id="b0df7-120">Kullandığınızda **Yeni Öğe Ekle** iletişim aracı bir ASP.NET uygulamasındaki bir veri hizmeti tanımlamak için Visual Studio'da projeye iki yeni dosyaları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b0df7-120">When you use the **Add New Item** dialog in Visual Studio to define a data service in an ASP.NET application, the tool generates two new files in the project.</span></span> <span data-ttu-id="b0df7-121">İlk dosya sahip bir `.svc` uzantısı ve veri hizmeti örneği oluşturmak nasıl WCF çalışma zamanı bildirir.</span><span class="sxs-lookup"><span data-stu-id="b0df7-121">The first file has a `.svc` extension and instructs the WCF runtime how to instantiate the data service.</span></span> <span data-ttu-id="b0df7-122">Aşağıdaki tamamladığınızda oluşturduğunuz Northwind örnek veri hizmeti bu dosyayı örneğidir [Hızlı Başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md):</span><span class="sxs-lookup"><span data-stu-id="b0df7-122">The following is an example of this file for the Northwind sample data service created when you complete the [quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md):</span></span>  
  
```  
<%@ ServiceHost Language="C#"   
    Factory="System.Data.Services.DataServiceHostFactory,   
            System.Data.Services, Version=4.0.0.0,   
            Culture=neutral, PublicKeyToken=b77a5c561934e089"   
    Service="NorthwindService.Northwind" %>   
```  
  
 <span data-ttu-id="b0df7-123">Bu yönerge kullanarak hizmet ana bilgisayarı adlandırılmış veri hizmet sınıfı oluşturmak için uygulama söyler <xref:System.Data.Services.DataServiceHostFactory> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b0df7-123">This directive tells the application to create the service host for the named data service class by using the <xref:System.Data.Services.DataServiceHostFactory> class.</span></span>  
  
 <span data-ttu-id="b0df7-124">Arka plan kodu sayfada `.svc` dosya şu şekilde Northwind örnek veri hizmeti için tanımlanan veri hizmetin kendisini uygulamasıdır sınıfı içerir:</span><span class="sxs-lookup"><span data-stu-id="b0df7-124">The code-behind page for the `.svc` file contains the class that is the implementation of the data service itself, which is defined as follows for the Northwind sample data service:</span></span>  
  
 [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
 [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]  
  
 <span data-ttu-id="b0df7-125">Veri hizmeti bir WCF hizmeti gibi davrandığı için veri hizmeti ile tümleştirilir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ve WCF Web programlama modelini izler.</span><span class="sxs-lookup"><span data-stu-id="b0df7-125">Because a data service behaves like a WCF service, the data service integrates with [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] and follows the WCF Web programming model.</span></span> <span data-ttu-id="b0df7-126">Daha fazla bilgi için bkz: [WCF hizmetleri ve ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) ve [WCF Web HTTP programlama modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md).</span><span class="sxs-lookup"><span data-stu-id="b0df7-126">For more information, see [WCF Services and ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) and [WCF Web HTTP Programming Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md).</span></span>  
  
## <a name="self-hosted-wcf-services"></a><span data-ttu-id="b0df7-127">Kendini barındıran WCF hizmetleri</span><span class="sxs-lookup"><span data-stu-id="b0df7-127">Self-Hosted WCF Services</span></span>  
 <span data-ttu-id="b0df7-128">WCF uygulaması sahiptir çünkü [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] veri hizmeti bir WCF hizmeti olarak kendi kendine barındırma destekler.</span><span class="sxs-lookup"><span data-stu-id="b0df7-128">Because it incorporates a WCF implementation, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] support self-hosting a data service as a WCF service.</span></span> <span data-ttu-id="b0df7-129">Bir hizmet birinde kendini barındıran [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] bir konsol uygulaması gibi uygulama.</span><span class="sxs-lookup"><span data-stu-id="b0df7-129">A service can be self-hosted in any [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] application, such as a console application.</span></span> <span data-ttu-id="b0df7-130"><xref:System.Data.Services.DataServiceHost> Devraldığı sınıfı <xref:System.ServiceModel.Web.WebServiceHost>, belirli bir adresinden veri hizmeti örneğini oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b0df7-130">The <xref:System.Data.Services.DataServiceHost> class, which inherits from <xref:System.ServiceModel.Web.WebServiceHost>, is used to instantiate the data service at a specific address.</span></span>  
  
 <span data-ttu-id="b0df7-131">Bu, dağıtmayı ve hizmet sorunlarını kolaylaştırabilir çünkü kendi kendine barındırma geliştirme ve test amacıyla kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b0df7-131">Self-hosting can be used for development and testing because it can make it easier to deploy and troubleshoot the service.</span></span> <span data-ttu-id="b0df7-132">Ancak, bu tür barındırma tarafından sağlanan Gelişmiş barındırma ve yönetim özellikleri sağlamaz [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] veya Internet Information Services (IIS) tarafından.</span><span class="sxs-lookup"><span data-stu-id="b0df7-132">However, this kind of hosting does not provide the advanced hosting and management features provided by [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] or by Internet Information Services (IIS).</span></span> <span data-ttu-id="b0df7-133">Daha fazla bilgi için bkz: [yönetilen bir uygulamada barındırma](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).</span><span class="sxs-lookup"><span data-stu-id="b0df7-133">For more information, see [Hosting in a Managed Application](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).</span></span>  
  
## <a name="defining-a-custom-data-service-host"></a><span data-ttu-id="b0df7-134">Bir özel veri hizmeti ana bilgisayarı tanımlama</span><span class="sxs-lookup"><span data-stu-id="b0df7-134">Defining a Custom Data Service Host</span></span>  
 <span data-ttu-id="b0df7-135">WCF konak uygulaması çok kısıtlayıcı olduğu durumlarda, özel bir ana bilgisayar veri hizmeti için de tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0df7-135">For cases where the WCF host implementation is too restrictive, you can also define a custom host for a data service.</span></span> <span data-ttu-id="b0df7-136">Uygulayan herhangi bir sınıf <xref:System.Data.Services.IDataServiceHost> arabirimi kullanılabilir ağ ana bilgisayar için bir veri hizmeti.</span><span class="sxs-lookup"><span data-stu-id="b0df7-136">Any class that implements <xref:System.Data.Services.IDataServiceHost> interface can be used as the network host for a data service.</span></span> <span data-ttu-id="b0df7-137">Özel bir ana bilgisayar uygulamalıdır <xref:System.Data.Services.IDataServiceHost> arabirim ve veri hizmeti ana bilgisayarı aşağıdaki temel sorumluluklarını işleyebilen:</span><span class="sxs-lookup"><span data-stu-id="b0df7-137">A custom host must implement the <xref:System.Data.Services.IDataServiceHost> interface and be able to handle the following basic responsibilities of the data service host:</span></span>  
  
-   <span data-ttu-id="b0df7-138">Veri Hizmeti ile hizmet kök yolu sağlar.</span><span class="sxs-lookup"><span data-stu-id="b0df7-138">Provide the data service with the service root path.</span></span>  
  
-   <span data-ttu-id="b0df7-139">İşlem istek ve yanıt üstbilgileri bilgi uygun <xref:System.Data.Services.IDataServiceHost> üye uygulama.</span><span class="sxs-lookup"><span data-stu-id="b0df7-139">Process request and response headers information to the appropriate <xref:System.Data.Services.IDataServiceHost> member implementation.</span></span>  
  
-   <span data-ttu-id="b0df7-140">Veri Hizmeti tarafından oluşturulan özel durumları işleme.</span><span class="sxs-lookup"><span data-stu-id="b0df7-140">Handle exceptions raised by the data service.</span></span>  
  
-   <span data-ttu-id="b0df7-141">Sorgu dizesi parametreleri doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="b0df7-141">Validate parameters in the query string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0df7-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b0df7-142">See Also</span></span>  
 [<span data-ttu-id="b0df7-143">WCF Veri Hizmetlerini Tanımlama</span><span class="sxs-lookup"><span data-stu-id="b0df7-143">Defining WCF Data Services</span></span>](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [<span data-ttu-id="b0df7-144">Verilerinizi Hizmet Olarak Kullanıma Sunma</span><span class="sxs-lookup"><span data-stu-id="b0df7-144">Exposing Your Data as a Service</span></span>](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md)  
 [<span data-ttu-id="b0df7-145">Veri Hizmeti Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b0df7-145">Configuring the Data Service</span></span>](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
