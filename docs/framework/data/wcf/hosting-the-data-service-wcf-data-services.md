---
description: 'Hakkında daha fazla bilgi edinin: veri hizmetini barındırma (WCF Veri Hizmetleri)'
title: Veri hizmetini barındırma (WCF Veri Hizmetleri)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, Windows Communication Foundation
ms.assetid: b48f42ce-22ce-4f8d-8f0d-f7ddac9125ee
ms.openlocfilehash: 519adde3a3e054d68ff9a1b7acf7ff06c0ca7532
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765795"
---
# <a name="hosting-the-data-service-wcf-data-services"></a><span data-ttu-id="85fc0-103">Veri hizmetini barındırma (WCF Veri Hizmetleri)</span><span class="sxs-lookup"><span data-stu-id="85fc0-103">Hosting the Data Service (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="85fc0-104">WCF Veri Hizmetleri kullanarak, verileri açık veri Protokolü (OData) akışı olarak sunan bir hizmet oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="85fc0-104">By using WCF Data Services, you can create a service that exposes data as an Open Data Protocol (OData) feed.</span></span> <span data-ttu-id="85fc0-105">Bu veri hizmeti, öğesinden devralan bir sınıf olarak tanımlanır <xref:System.Data.Services.DataService%601> .</span><span class="sxs-lookup"><span data-stu-id="85fc0-105">This data service is defined as a class that inherits from <xref:System.Data.Services.DataService%601>.</span></span> <span data-ttu-id="85fc0-106">Bu sınıf, istek iletilerini işlemek, veri kaynağına karşı güncelleştirmeler gerçekleştirmek ve OData için gereken yanıt iletilerini oluşturmak için gereken işlevselliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="85fc0-106">This class provides the functionality required to process request messages, perform updates against the data source, and generate responses messages, as required by OData.</span></span> <span data-ttu-id="85fc0-107">Ancak, bir veri hizmeti gelen HTTP istekleri için bir ağ yuvasına bağlanamaz ve bu yuvayı dinlemez.</span><span class="sxs-lookup"><span data-stu-id="85fc0-107">However, a data service cannot bind to and listen on a network socket for incoming HTTP requests.</span></span> <span data-ttu-id="85fc0-108">Bu gerekli işlevsellik için veri hizmeti bir barındırma bileşeni kullanır.</span><span class="sxs-lookup"><span data-stu-id="85fc0-108">For this required functionality, the data service relies on a hosting component.</span></span>

 <span data-ttu-id="85fc0-109">Veri hizmeti ana bilgisayarı, veri hizmeti adına aşağıdaki görevleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="85fc0-109">The data service host performs the following tasks on behalf of the data service:</span></span>

- <span data-ttu-id="85fc0-110">İstekleri dinler ve bu istekleri veri hizmetine yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="85fc0-110">Listens for requests and routes these requests to the data service.</span></span>

- <span data-ttu-id="85fc0-111">Her istek için veri hizmetinin bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="85fc0-111">Creates an instance of the data service for each request.</span></span>

- <span data-ttu-id="85fc0-112">Veri hizmetinin gelen isteği işlemesini ister.</span><span class="sxs-lookup"><span data-stu-id="85fc0-112">Requests that the data service process the incoming request.</span></span>

- <span data-ttu-id="85fc0-113">Yanıtı veri hizmeti adına gönderir.</span><span class="sxs-lookup"><span data-stu-id="85fc0-113">Sends the response on behalf of the data service.</span></span>

 <span data-ttu-id="85fc0-114">Bir veri hizmetini barındırmayı basitleştirmek için WCF Veri Hizmetleri, Windows Communication Foundation (WCF) ile tümleştirilecek şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="85fc0-114">To simplify hosting a data service, WCF Data Services is designed to integrate with Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="85fc0-115">Veri hizmeti bir ASP.NET uygulamasında veri hizmeti Konağı görevi gören varsayılan bir WCF uygulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="85fc0-115">The data service provides a default WCF implementation that serves as the data service host in an ASP.NET application.</span></span> <span data-ttu-id="85fc0-116">Bu nedenle, aşağıdaki yollarla bir veri hizmetini barındırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="85fc0-116">Therefore, you can host a data service in one of the following ways:</span></span>

- <span data-ttu-id="85fc0-117">Bir ASP.NET uygulamasında.</span><span class="sxs-lookup"><span data-stu-id="85fc0-117">In an ASP.NET application.</span></span>

- <span data-ttu-id="85fc0-118">Şirket içinde barındırılan WCF hizmetlerini destekleyen bir yönetilen uygulama.</span><span class="sxs-lookup"><span data-stu-id="85fc0-118">In a managed application that supports self-hosted WCF services.</span></span>

- <span data-ttu-id="85fc0-119">Diğer bazı özel veri hizmeti ana bilgisayarında.</span><span class="sxs-lookup"><span data-stu-id="85fc0-119">In some other custom data service host.</span></span>

## <a name="hosting-a-data-service-in-an-aspnet-application"></a><span data-ttu-id="85fc0-120">Bir ASP.NET uygulamasında veri hizmeti barındırma</span><span class="sxs-lookup"><span data-stu-id="85fc0-120">Hosting a Data Service in an ASP.NET Application</span></span>

<span data-ttu-id="85fc0-121">Bir ASP.NET uygulamasında veri hizmeti tanımlamak için Visual Studio 2015 ' de **Yeni öğe Ekle** iletişim kutusunu kullandığınızda, araç projede iki yeni dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="85fc0-121">When you use the **Add New Item** dialog in Visual Studio 2015 to define a data service in an ASP.NET application, the tool generates two new files in the project.</span></span> <span data-ttu-id="85fc0-122">İlk dosya bir uzantıya sahiptir `.svc` ve WCF çalışma zamanına veri hizmetini nasıl örneklendirilecek.</span><span class="sxs-lookup"><span data-stu-id="85fc0-122">The first file has a `.svc` extension and instructs the WCF runtime how to instantiate the data service.</span></span> <span data-ttu-id="85fc0-123">Aşağıda, [hızlı](quickstart-wcf-data-services.md)başlangıcı tamamladığınızda oluşturulan Northwind örnek veri hizmeti için bu dosyaya bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="85fc0-123">The following is an example of this file for the Northwind sample data service created when you complete the [quickstart](quickstart-wcf-data-services.md):</span></span>

```aspx-csharp
<%@ ServiceHost Language="C#"
    Factory="System.Data.Services.DataServiceHostFactory,
            System.Data.Services, Version=4.0.0.0,
            Culture=neutral, PublicKeyToken=b77a5c561934e089"
    Service="NorthwindService.Northwind" %>
```

 <span data-ttu-id="85fc0-124">Bu yönerge, uygulamanın sınıfını kullanarak adlandırılmış veri hizmeti sınıfı için hizmet ana bilgisayarı oluşturmasını söyler <xref:System.Data.Services.DataServiceHostFactory> .</span><span class="sxs-lookup"><span data-stu-id="85fc0-124">This directive tells the application to create the service host for the named data service class by using the <xref:System.Data.Services.DataServiceHostFactory> class.</span></span>

 <span data-ttu-id="85fc0-125">Dosya için arka plan kod sayfası, `.svc` Northwind örnek veri hizmeti için aşağıdaki şekilde tanımlanan veri hizmeti 'nin uygulanması olan sınıfı içerir:</span><span class="sxs-lookup"><span data-stu-id="85fc0-125">The code-behind page for the `.svc` file contains the class that is the implementation of the data service itself, which is defined as follows for the Northwind sample data service:</span></span>

 [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
 [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

 <span data-ttu-id="85fc0-126">Bir veri hizmeti bir WCF hizmeti gibi davrandığı için, veri hizmeti ASP.NET ile tümleşir ve WCF Web programlama modelini izler.</span><span class="sxs-lookup"><span data-stu-id="85fc0-126">Because a data service behaves like a WCF service, the data service integrates with ASP.NET and follows the WCF Web programming model.</span></span> <span data-ttu-id="85fc0-127">Daha fazla bilgi için bkz. [WCF Hizmetleri ve ASP.net](../../wcf/feature-details/wcf-services-and-aspnet.md) ve [WCF Web http programlama modeli](../../wcf/feature-details/wcf-web-http-programming-model.md).</span><span class="sxs-lookup"><span data-stu-id="85fc0-127">For more information, see [WCF Services and ASP.NET](../../wcf/feature-details/wcf-services-and-aspnet.md) and [WCF Web HTTP Programming Model](../../wcf/feature-details/wcf-web-http-programming-model.md).</span></span>

## <a name="self-hosted-wcf-services"></a><span data-ttu-id="85fc0-128">WCF hizmetlerini Self-Hosted</span><span class="sxs-lookup"><span data-stu-id="85fc0-128">Self-Hosted WCF Services</span></span>

 <span data-ttu-id="85fc0-129">Bir WCF uygulamasını içerdiğinden WCF Veri Hizmetleri, bir WCF hizmeti olarak veri hizmetini kendi kendine barındırmayı destekler.</span><span class="sxs-lookup"><span data-stu-id="85fc0-129">Because it incorporates a WCF implementation, WCF Data Services support self-hosting a data service as a WCF service.</span></span> <span data-ttu-id="85fc0-130">Bir hizmet, konsol uygulaması gibi herhangi bir .NET Framework uygulamasında şirket içinde barınabilir.</span><span class="sxs-lookup"><span data-stu-id="85fc0-130">A service can be self-hosted in any .NET Framework application, such as a console application.</span></span> <span data-ttu-id="85fc0-131"><xref:System.Data.Services.DataServiceHost>Öğesinden devralan sınıf, <xref:System.ServiceModel.Web.WebServiceHost> belirli bir adreste veri hizmetinin örneğini oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="85fc0-131">The <xref:System.Data.Services.DataServiceHost> class, which inherits from <xref:System.ServiceModel.Web.WebServiceHost>, is used to instantiate the data service at a specific address.</span></span>

 <span data-ttu-id="85fc0-132">Self barındırma, hizmeti dağıtmayı ve sorunlarını gidermeyi kolaylaştıran geliştirme ve test için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="85fc0-132">Self-hosting can be used for development and testing because it can make it easier to deploy and troubleshoot the service.</span></span> <span data-ttu-id="85fc0-133">Ancak, bu tür bir barındırma, ASP.NET tarafından veya Internet Information Services (IIS) tarafından sunulan gelişmiş barındırma ve yönetim özelliklerini sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="85fc0-133">However, this kind of hosting does not provide the advanced hosting and management features provided by ASP.NET or by Internet Information Services (IIS).</span></span> <span data-ttu-id="85fc0-134">Daha fazla bilgi için bkz. [yönetilen bir uygulamada barındırma](../../wcf/feature-details/hosting-in-a-managed-application.md).</span><span class="sxs-lookup"><span data-stu-id="85fc0-134">For more information, see [Hosting in a Managed Application](../../wcf/feature-details/hosting-in-a-managed-application.md).</span></span>

## <a name="defining-a-custom-data-service-host"></a><span data-ttu-id="85fc0-135">Özel veri hizmeti Konağı tanımlama</span><span class="sxs-lookup"><span data-stu-id="85fc0-135">Defining a Custom Data Service Host</span></span>

 <span data-ttu-id="85fc0-136">WCF ana bilgisayar uygulamasının çok kısıtlayıcı olduğu durumlarda, bir veri hizmeti için özel bir ana bilgisayar da tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="85fc0-136">For cases where the WCF host implementation is too restrictive, you can also define a custom host for a data service.</span></span> <span data-ttu-id="85fc0-137">Arabirim uygulayan herhangi <xref:System.Data.Services.IDataServiceHost> bir sınıf, bir veri hizmeti için ağ ana bilgisayarı olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="85fc0-137">Any class that implements <xref:System.Data.Services.IDataServiceHost> interface can be used as the network host for a data service.</span></span> <span data-ttu-id="85fc0-138">Özel bir ana bilgisayar arabirimi uygulamalıdır <xref:System.Data.Services.IDataServiceHost> ve veri hizmeti konağının aşağıdaki temel sorumluluklarını işleyebilmelidir:</span><span class="sxs-lookup"><span data-stu-id="85fc0-138">A custom host must implement the <xref:System.Data.Services.IDataServiceHost> interface and be able to handle the following basic responsibilities of the data service host:</span></span>

- <span data-ttu-id="85fc0-139">Hizmet kök yolu ile veri hizmeti sağlayın.</span><span class="sxs-lookup"><span data-stu-id="85fc0-139">Provide the data service with the service root path.</span></span>

- <span data-ttu-id="85fc0-140">İstek ve yanıt üst bilgileri bilgilerini uygun <xref:System.Data.Services.IDataServiceHost> üye uygulamasına işleyin.</span><span class="sxs-lookup"><span data-stu-id="85fc0-140">Process request and response headers information to the appropriate <xref:System.Data.Services.IDataServiceHost> member implementation.</span></span>

- <span data-ttu-id="85fc0-141">Veri hizmeti tarafından oluşturulan özel durumları işleyin.</span><span class="sxs-lookup"><span data-stu-id="85fc0-141">Handle exceptions raised by the data service.</span></span>

- <span data-ttu-id="85fc0-142">Sorgu dizesindeki parametreleri doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="85fc0-142">Validate parameters in the query string.</span></span>

## <a name="see-also"></a><span data-ttu-id="85fc0-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85fc0-143">See also</span></span>

- [<span data-ttu-id="85fc0-144">WCF Veri Hizmetlerini Tanımlama</span><span class="sxs-lookup"><span data-stu-id="85fc0-144">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)
- [<span data-ttu-id="85fc0-145">Verilerinizi Hizmet Olarak Kullanıma Sunma</span><span class="sxs-lookup"><span data-stu-id="85fc0-145">Exposing Your Data as a Service</span></span>](exposing-your-data-as-a-service-wcf-data-services.md)
- [<span data-ttu-id="85fc0-146">Veri Hizmeti Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="85fc0-146">Configuring the Data Service</span></span>](configuring-the-data-service-wcf-data-services.md)
