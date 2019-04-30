---
title: Veri hizmetini (WCF Veri Hizmetleri) barındırma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, Windows Communication Foundation
ms.assetid: b48f42ce-22ce-4f8d-8f0d-f7ddac9125ee
ms.openlocfilehash: e738fa1feebdd91bdb84484340b31e599d7f5f76
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765586"
---
# <a name="hosting-the-data-service-wcf-data-services"></a><span data-ttu-id="b8a2d-102">Veri hizmetini (WCF Veri Hizmetleri) barındırma</span><span class="sxs-lookup"><span data-stu-id="b8a2d-102">Hosting the Data Service (WCF Data Services)</span></span>
<span data-ttu-id="b8a2d-103">WCF veri hizmetlerini kullanarak, verileri olarak kullanıma sunan bir hizmet oluşturabilmeniz için bir [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] akış.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-103">By using WCF Data Services, you can create a service that exposes data as an [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed.</span></span> <span data-ttu-id="b8a2d-104">Bu veri hizmeti öğesinden devralınan bir sınıf olarak tanımlanan <xref:System.Data.Services.DataService%601>.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-104">This data service is defined as a class that inherits from <xref:System.Data.Services.DataService%601>.</span></span> <span data-ttu-id="b8a2d-105">Bu sınıf, OData gerektirdiği yanıt iletilerini istek iletilerini işlemek ve güncelleştirmeleri veri kaynağına karşı gerçekleştirmek için gereken işlevleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-105">This class provides the functionality required to process request messages, perform updates against the data source, and generate responses messages, as required by OData.</span></span> <span data-ttu-id="b8a2d-106">Ancak, bir veri hizmeti bağlamak ve bir ağ yuvayı için gelen HTTP istek dinleyemedi.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-106">However, a data service cannot bind to and listen on a network socket for incoming HTTP requests.</span></span> <span data-ttu-id="b8a2d-107">Bu gerekli işlevselliği için veri hizmetini barındıran bir bileşende kullanır.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-107">For this required functionality, the data service relies on a hosting component.</span></span>

 <span data-ttu-id="b8a2d-108">Veri Hizmeti ana veri hizmeti adına aşağıdaki görevleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="b8a2d-108">The data service host performs the following tasks on behalf of the data service:</span></span>

- <span data-ttu-id="b8a2d-109">İsteklerini dinler ve bu istekleri veri hizmetine yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-109">Listens for requests and routes these requests to the data service.</span></span>

- <span data-ttu-id="b8a2d-110">Her istek için veri Hizmeti'nin bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-110">Creates an instance of the data service for each request.</span></span>

- <span data-ttu-id="b8a2d-111">İstekleri veri hizmeti gelen isteği işleyemedi.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-111">Requests that the data service process the incoming request.</span></span>

- <span data-ttu-id="b8a2d-112">Veri hizmeti adına yanıtı gönderir.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-112">Sends the response on behalf of the data service.</span></span>

 <span data-ttu-id="b8a2d-113">Veri hizmetini barındıran basitleştirmek için WCF Veri Hizmetleri Windows Communication Foundation (WCF) ile tümleştirmek için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-113">To simplify hosting a data service, WCF Data Services is designed to integrate with Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="b8a2d-114">Veri Hizmeti ana bilgisayar olarak hizmet veren bir varsayılan WCF uygulaması veri hizmetinin sağladığı bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-114">The data service provides a default WCF implementation that serves as the data service host in an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application.</span></span> <span data-ttu-id="b8a2d-115">Bu nedenle, aşağıdaki yollardan birinde bir veri hizmeti barındırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b8a2d-115">Therefore, you can host a data service in one of the following ways:</span></span>

- <span data-ttu-id="b8a2d-116">İçinde bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-116">In an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application.</span></span>

- <span data-ttu-id="b8a2d-117">Yönetilen bir uygulamada, şirket içinde barındırılan WCF hizmetleri destekler.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-117">In a managed application that supports self-hosted WCF services.</span></span>

- <span data-ttu-id="b8a2d-118">Bazı diğer özel veri hizmeti ana bilgisayar.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-118">In some other custom data service host.</span></span>

## <a name="hosting-a-data-service-in-an-aspnet-application"></a><span data-ttu-id="b8a2d-119">Bir ASP.NET uygulamasında veri hizmeti barındırma</span><span class="sxs-lookup"><span data-stu-id="b8a2d-119">Hosting a Data Service in an ASP.NET Application</span></span>

<span data-ttu-id="b8a2d-120">Kullanırken **Yeni Öğe Ekle** iletişim Aracı'nı bir ASP.NET uygulamasında veri hizmeti tanımlamak için Visual Studio 2015'te, projede iki yeni dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-120">When you use the **Add New Item** dialog in Visual Studio 2015 to define a data service in an ASP.NET application, the tool generates two new files in the project.</span></span> <span data-ttu-id="b8a2d-121">İlk dosya bir `.svc` uzantısı ve veri hizmeti örneği oluşturmak nasıl WCF çalıştırma zamanı bildirir.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-121">The first file has a `.svc` extension and instructs the WCF runtime how to instantiate the data service.</span></span> <span data-ttu-id="b8a2d-122">Tamamlandığında, oluşturulan Northwind örnek veri hizmeti için bu dosyanın bir örneği verilmiştir [hızlı](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md):</span><span class="sxs-lookup"><span data-stu-id="b8a2d-122">The following is an example of this file for the Northwind sample data service created when you complete the [quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md):</span></span>

```
<%@ ServiceHost Language="C#"
    Factory="System.Data.Services.DataServiceHostFactory,
            System.Data.Services, Version=4.0.0.0,
            Culture=neutral, PublicKeyToken=b77a5c561934e089"
    Service="NorthwindService.Northwind" %>
```

 <span data-ttu-id="b8a2d-123">Bu yönerge kullanarak hizmet ana bilgisayarı için adlandırılmış veri hizmeti sınıfındaki oluşturmak için uygulama bildirir <xref:System.Data.Services.DataServiceHostFactory> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-123">This directive tells the application to create the service host for the named data service class by using the <xref:System.Data.Services.DataServiceHostFactory> class.</span></span>

 <span data-ttu-id="b8a2d-124">Arka plan kod sayfası `.svc` dosyası gibi Northwind örnek veri hizmeti için tanımlanan veri hizmetinin kendisi, uygulama sınıfı içerir:</span><span class="sxs-lookup"><span data-stu-id="b8a2d-124">The code-behind page for the `.svc` file contains the class that is the implementation of the data service itself, which is defined as follows for the Northwind sample data service:</span></span>

 [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
 [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

 <span data-ttu-id="b8a2d-125">Bir veri hizmeti bir WCF hizmeti gibi davranan olduğundan, veri hizmeti ile tümleşir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ve WCF Web programlama modelini kullanır.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-125">Because a data service behaves like a WCF service, the data service integrates with [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] and follows the WCF Web programming model.</span></span> <span data-ttu-id="b8a2d-126">Daha fazla bilgi için [WCF hizmetleri ve ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) ve [WCF Web HTTP programlama modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md).</span><span class="sxs-lookup"><span data-stu-id="b8a2d-126">For more information, see [WCF Services and ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) and [WCF Web HTTP Programming Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md).</span></span>

## <a name="self-hosted-wcf-services"></a><span data-ttu-id="b8a2d-127">Şirket içinde barındırılan WCF hizmetleri</span><span class="sxs-lookup"><span data-stu-id="b8a2d-127">Self-Hosted WCF Services</span></span>
 <span data-ttu-id="b8a2d-128">WCF uygulaması içerir olduğundan, bir veri hizmetine bir WCF hizmeti olarak kendi kendine barındırma WCF veri hizmetleri destekler.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-128">Because it incorporates a WCF implementation, WCF Data Services support self-hosting a data service as a WCF service.</span></span> <span data-ttu-id="b8a2d-129">Bir hizmet, tüm şirket içinde barındırılan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] bir konsol uygulaması gibi uygulama.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-129">A service can be self-hosted in any [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] application, such as a console application.</span></span> <span data-ttu-id="b8a2d-130"><xref:System.Data.Services.DataServiceHost> Öğesinden devralan sınıf <xref:System.ServiceModel.Web.WebServiceHost>, belirli bir adresten veri hizmeti örneklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-130">The <xref:System.Data.Services.DataServiceHost> class, which inherits from <xref:System.ServiceModel.Web.WebServiceHost>, is used to instantiate the data service at a specific address.</span></span>

 <span data-ttu-id="b8a2d-131">Bu, dağıtmak ve hizmette sorun gidermek kolaylaştırabilir çünkü kendi kendine barındırma geliştirme ve test için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-131">Self-hosting can be used for development and testing because it can make it easier to deploy and troubleshoot the service.</span></span> <span data-ttu-id="b8a2d-132">Ancak, bu tür barındırma tarafından sağlanan Gelişmiş barındırma ve yönetim özellikleri sağlamaz [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] veya Internet Information Services (IIS) tarafından.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-132">However, this kind of hosting does not provide the advanced hosting and management features provided by [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] or by Internet Information Services (IIS).</span></span> <span data-ttu-id="b8a2d-133">Daha fazla bilgi için [yönetilen bir uygulamada barındırma](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).</span><span class="sxs-lookup"><span data-stu-id="b8a2d-133">For more information, see [Hosting in a Managed Application](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).</span></span>

## <a name="defining-a-custom-data-service-host"></a><span data-ttu-id="b8a2d-134">Bir özel veri hizmeti ana bilgisayarı tanımlama</span><span class="sxs-lookup"><span data-stu-id="b8a2d-134">Defining a Custom Data Service Host</span></span>
 <span data-ttu-id="b8a2d-135">WCF konak uygulama çok kısıtlayıcı olduğu durumlarda, veri hizmeti için özel bir ana bilgisayar da tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-135">For cases where the WCF host implementation is too restrictive, you can also define a custom host for a data service.</span></span> <span data-ttu-id="b8a2d-136">Uygulayan sınıfa <xref:System.Data.Services.IDataServiceHost> arabirimi kullanılabilir ağ ana bilgisayarı için bir veri hizmeti.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-136">Any class that implements <xref:System.Data.Services.IDataServiceHost> interface can be used as the network host for a data service.</span></span> <span data-ttu-id="b8a2d-137">Özel bir ana bilgisayar uygulamalıdır <xref:System.Data.Services.IDataServiceHost> arabirim ve veri hizmeti ana bilgisayarının aşağıdaki temel sorumluluklarını işleyebilir:</span><span class="sxs-lookup"><span data-stu-id="b8a2d-137">A custom host must implement the <xref:System.Data.Services.IDataServiceHost> interface and be able to handle the following basic responsibilities of the data service host:</span></span>

- <span data-ttu-id="b8a2d-138">Veri hizmetinin Hizmet kök yoluyla sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-138">Provide the data service with the service root path.</span></span>

- <span data-ttu-id="b8a2d-139">İşlem istek ve yanıt üst bilgileri uygun <xref:System.Data.Services.IDataServiceHost> üye uygulaması.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-139">Process request and response headers information to the appropriate <xref:System.Data.Services.IDataServiceHost> member implementation.</span></span>

- <span data-ttu-id="b8a2d-140">Veri Hizmeti tarafından oluşturulan özel durumları işler.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-140">Handle exceptions raised by the data service.</span></span>

- <span data-ttu-id="b8a2d-141">Sorgu dizesi parametreleri doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-141">Validate parameters in the query string.</span></span>

## <a name="see-also"></a><span data-ttu-id="b8a2d-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-142">See also</span></span>

- [<span data-ttu-id="b8a2d-143">WCF Veri Hizmetlerini Tanımlama</span><span class="sxs-lookup"><span data-stu-id="b8a2d-143">Defining WCF Data Services</span></span>](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
- [<span data-ttu-id="b8a2d-144">Verilerinizi Hizmet Olarak Kullanıma Sunma</span><span class="sxs-lookup"><span data-stu-id="b8a2d-144">Exposing Your Data as a Service</span></span>](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md)
- [<span data-ttu-id="b8a2d-145">Veri Hizmeti Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b8a2d-145">Configuring the Data Service</span></span>](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
