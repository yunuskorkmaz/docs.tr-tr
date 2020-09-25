---
title: Veri hizmetini barındırma (WCF Veri Hizmetleri)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, Windows Communication Foundation
ms.assetid: b48f42ce-22ce-4f8d-8f0d-f7ddac9125ee
ms.openlocfilehash: 5dfa1d9f02f660b55ecf6598ef5012174a1ba853
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172599"
---
# <a name="hosting-the-data-service-wcf-data-services"></a><span data-ttu-id="6f689-102">Veri hizmetini barındırma (WCF Veri Hizmetleri)</span><span class="sxs-lookup"><span data-stu-id="6f689-102">Hosting the Data Service (WCF Data Services)</span></span>

<span data-ttu-id="6f689-103">WCF Veri Hizmetleri kullanarak, verileri açık veri Protokolü (OData) akışı olarak sunan bir hizmet oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f689-103">By using WCF Data Services, you can create a service that exposes data as an Open Data Protocol (OData) feed.</span></span> <span data-ttu-id="6f689-104">Bu veri hizmeti, öğesinden devralan bir sınıf olarak tanımlanır <xref:System.Data.Services.DataService%601> .</span><span class="sxs-lookup"><span data-stu-id="6f689-104">This data service is defined as a class that inherits from <xref:System.Data.Services.DataService%601>.</span></span> <span data-ttu-id="6f689-105">Bu sınıf, istek iletilerini işlemek, veri kaynağına karşı güncelleştirmeler gerçekleştirmek ve OData için gereken yanıt iletilerini oluşturmak için gereken işlevselliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f689-105">This class provides the functionality required to process request messages, perform updates against the data source, and generate responses messages, as required by OData.</span></span> <span data-ttu-id="6f689-106">Ancak, bir veri hizmeti gelen HTTP istekleri için bir ağ yuvasına bağlanamaz ve bu yuvayı dinlemez.</span><span class="sxs-lookup"><span data-stu-id="6f689-106">However, a data service cannot bind to and listen on a network socket for incoming HTTP requests.</span></span> <span data-ttu-id="6f689-107">Bu gerekli işlevsellik için veri hizmeti bir barındırma bileşeni kullanır.</span><span class="sxs-lookup"><span data-stu-id="6f689-107">For this required functionality, the data service relies on a hosting component.</span></span>

 <span data-ttu-id="6f689-108">Veri hizmeti ana bilgisayarı, veri hizmeti adına aşağıdaki görevleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="6f689-108">The data service host performs the following tasks on behalf of the data service:</span></span>

- <span data-ttu-id="6f689-109">İstekleri dinler ve bu istekleri veri hizmetine yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="6f689-109">Listens for requests and routes these requests to the data service.</span></span>

- <span data-ttu-id="6f689-110">Her istek için veri hizmetinin bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6f689-110">Creates an instance of the data service for each request.</span></span>

- <span data-ttu-id="6f689-111">Veri hizmetinin gelen isteği işlemesini ister.</span><span class="sxs-lookup"><span data-stu-id="6f689-111">Requests that the data service process the incoming request.</span></span>

- <span data-ttu-id="6f689-112">Yanıtı veri hizmeti adına gönderir.</span><span class="sxs-lookup"><span data-stu-id="6f689-112">Sends the response on behalf of the data service.</span></span>

 <span data-ttu-id="6f689-113">Bir veri hizmetini barındırmayı basitleştirmek için WCF Veri Hizmetleri, Windows Communication Foundation (WCF) ile tümleştirilecek şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="6f689-113">To simplify hosting a data service, WCF Data Services is designed to integrate with Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="6f689-114">Veri hizmeti bir ASP.NET uygulamasında veri hizmeti Konağı görevi gören varsayılan bir WCF uygulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f689-114">The data service provides a default WCF implementation that serves as the data service host in an ASP.NET application.</span></span> <span data-ttu-id="6f689-115">Bu nedenle, aşağıdaki yollarla bir veri hizmetini barındırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6f689-115">Therefore, you can host a data service in one of the following ways:</span></span>

- <span data-ttu-id="6f689-116">Bir ASP.NET uygulamasında.</span><span class="sxs-lookup"><span data-stu-id="6f689-116">In an ASP.NET application.</span></span>

- <span data-ttu-id="6f689-117">Şirket içinde barındırılan WCF hizmetlerini destekleyen bir yönetilen uygulama.</span><span class="sxs-lookup"><span data-stu-id="6f689-117">In a managed application that supports self-hosted WCF services.</span></span>

- <span data-ttu-id="6f689-118">Diğer bazı özel veri hizmeti ana bilgisayarında.</span><span class="sxs-lookup"><span data-stu-id="6f689-118">In some other custom data service host.</span></span>

## <a name="hosting-a-data-service-in-an-aspnet-application"></a><span data-ttu-id="6f689-119">Bir ASP.NET uygulamasında veri hizmeti barındırma</span><span class="sxs-lookup"><span data-stu-id="6f689-119">Hosting a Data Service in an ASP.NET Application</span></span>

<span data-ttu-id="6f689-120">Bir ASP.NET uygulamasında veri hizmeti tanımlamak için Visual Studio 2015 ' de **Yeni öğe Ekle** iletişim kutusunu kullandığınızda, araç projede iki yeni dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6f689-120">When you use the **Add New Item** dialog in Visual Studio 2015 to define a data service in an ASP.NET application, the tool generates two new files in the project.</span></span> <span data-ttu-id="6f689-121">İlk dosya bir uzantıya sahiptir `.svc` ve WCF çalışma zamanına veri hizmetini nasıl örneklendirilecek.</span><span class="sxs-lookup"><span data-stu-id="6f689-121">The first file has a `.svc` extension and instructs the WCF runtime how to instantiate the data service.</span></span> <span data-ttu-id="6f689-122">Aşağıda, [hızlı](quickstart-wcf-data-services.md)başlangıcı tamamladığınızda oluşturulan Northwind örnek veri hizmeti için bu dosyaya bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="6f689-122">The following is an example of this file for the Northwind sample data service created when you complete the [quickstart](quickstart-wcf-data-services.md):</span></span>

```aspx-csharp
<%@ ServiceHost Language="C#"
    Factory="System.Data.Services.DataServiceHostFactory,
            System.Data.Services, Version=4.0.0.0,
            Culture=neutral, PublicKeyToken=b77a5c561934e089"
    Service="NorthwindService.Northwind" %>
```

 <span data-ttu-id="6f689-123">Bu yönerge, uygulamanın sınıfını kullanarak adlandırılmış veri hizmeti sınıfı için hizmet ana bilgisayarı oluşturmasını söyler <xref:System.Data.Services.DataServiceHostFactory> .</span><span class="sxs-lookup"><span data-stu-id="6f689-123">This directive tells the application to create the service host for the named data service class by using the <xref:System.Data.Services.DataServiceHostFactory> class.</span></span>

 <span data-ttu-id="6f689-124">Dosya için arka plan kod sayfası, `.svc` Northwind örnek veri hizmeti için aşağıdaki şekilde tanımlanan veri hizmeti 'nin uygulanması olan sınıfı içerir:</span><span class="sxs-lookup"><span data-stu-id="6f689-124">The code-behind page for the `.svc` file contains the class that is the implementation of the data service itself, which is defined as follows for the Northwind sample data service:</span></span>

 [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
 [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

 <span data-ttu-id="6f689-125">Bir veri hizmeti bir WCF hizmeti gibi davrandığı için, veri hizmeti ASP.NET ile tümleşir ve WCF Web programlama modelini izler.</span><span class="sxs-lookup"><span data-stu-id="6f689-125">Because a data service behaves like a WCF service, the data service integrates with ASP.NET and follows the WCF Web programming model.</span></span> <span data-ttu-id="6f689-126">Daha fazla bilgi için bkz. [WCF Hizmetleri ve ASP.net](../../wcf/feature-details/wcf-services-and-aspnet.md) ve [WCF Web http programlama modeli](../../wcf/feature-details/wcf-web-http-programming-model.md).</span><span class="sxs-lookup"><span data-stu-id="6f689-126">For more information, see [WCF Services and ASP.NET](../../wcf/feature-details/wcf-services-and-aspnet.md) and [WCF Web HTTP Programming Model](../../wcf/feature-details/wcf-web-http-programming-model.md).</span></span>

## <a name="self-hosted-wcf-services"></a><span data-ttu-id="6f689-127">Şirket içinde barındırılan WCF Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="6f689-127">Self-Hosted WCF Services</span></span>

 <span data-ttu-id="6f689-128">Bir WCF uygulamasını içerdiğinden WCF Veri Hizmetleri, bir WCF hizmeti olarak veri hizmetini kendi kendine barındırmayı destekler.</span><span class="sxs-lookup"><span data-stu-id="6f689-128">Because it incorporates a WCF implementation, WCF Data Services support self-hosting a data service as a WCF service.</span></span> <span data-ttu-id="6f689-129">Bir hizmet, konsol uygulaması gibi herhangi bir .NET Framework uygulamasında şirket içinde barınabilir.</span><span class="sxs-lookup"><span data-stu-id="6f689-129">A service can be self-hosted in any .NET Framework application, such as a console application.</span></span> <span data-ttu-id="6f689-130"><xref:System.Data.Services.DataServiceHost>Öğesinden devralan sınıf, <xref:System.ServiceModel.Web.WebServiceHost> belirli bir adreste veri hizmetinin örneğini oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6f689-130">The <xref:System.Data.Services.DataServiceHost> class, which inherits from <xref:System.ServiceModel.Web.WebServiceHost>, is used to instantiate the data service at a specific address.</span></span>

 <span data-ttu-id="6f689-131">Self barındırma, hizmeti dağıtmayı ve sorunlarını gidermeyi kolaylaştıran geliştirme ve test için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6f689-131">Self-hosting can be used for development and testing because it can make it easier to deploy and troubleshoot the service.</span></span> <span data-ttu-id="6f689-132">Ancak, bu tür bir barındırma, ASP.NET tarafından veya Internet Information Services (IIS) tarafından sunulan gelişmiş barındırma ve yönetim özelliklerini sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="6f689-132">However, this kind of hosting does not provide the advanced hosting and management features provided by ASP.NET or by Internet Information Services (IIS).</span></span> <span data-ttu-id="6f689-133">Daha fazla bilgi için bkz. [yönetilen bir uygulamada barındırma](../../wcf/feature-details/hosting-in-a-managed-application.md).</span><span class="sxs-lookup"><span data-stu-id="6f689-133">For more information, see [Hosting in a Managed Application](../../wcf/feature-details/hosting-in-a-managed-application.md).</span></span>

## <a name="defining-a-custom-data-service-host"></a><span data-ttu-id="6f689-134">Özel veri hizmeti Konağı tanımlama</span><span class="sxs-lookup"><span data-stu-id="6f689-134">Defining a Custom Data Service Host</span></span>

 <span data-ttu-id="6f689-135">WCF ana bilgisayar uygulamasının çok kısıtlayıcı olduğu durumlarda, bir veri hizmeti için özel bir ana bilgisayar da tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f689-135">For cases where the WCF host implementation is too restrictive, you can also define a custom host for a data service.</span></span> <span data-ttu-id="6f689-136">Arabirim uygulayan herhangi <xref:System.Data.Services.IDataServiceHost> bir sınıf, bir veri hizmeti için ağ ana bilgisayarı olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6f689-136">Any class that implements <xref:System.Data.Services.IDataServiceHost> interface can be used as the network host for a data service.</span></span> <span data-ttu-id="6f689-137">Özel bir ana bilgisayar arabirimi uygulamalıdır <xref:System.Data.Services.IDataServiceHost> ve veri hizmeti konağının aşağıdaki temel sorumluluklarını işleyebilmelidir:</span><span class="sxs-lookup"><span data-stu-id="6f689-137">A custom host must implement the <xref:System.Data.Services.IDataServiceHost> interface and be able to handle the following basic responsibilities of the data service host:</span></span>

- <span data-ttu-id="6f689-138">Hizmet kök yolu ile veri hizmeti sağlayın.</span><span class="sxs-lookup"><span data-stu-id="6f689-138">Provide the data service with the service root path.</span></span>

- <span data-ttu-id="6f689-139">İstek ve yanıt üst bilgileri bilgilerini uygun <xref:System.Data.Services.IDataServiceHost> üye uygulamasına işleyin.</span><span class="sxs-lookup"><span data-stu-id="6f689-139">Process request and response headers information to the appropriate <xref:System.Data.Services.IDataServiceHost> member implementation.</span></span>

- <span data-ttu-id="6f689-140">Veri hizmeti tarafından oluşturulan özel durumları işleyin.</span><span class="sxs-lookup"><span data-stu-id="6f689-140">Handle exceptions raised by the data service.</span></span>

- <span data-ttu-id="6f689-141">Sorgu dizesindeki parametreleri doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="6f689-141">Validate parameters in the query string.</span></span>

## <a name="see-also"></a><span data-ttu-id="6f689-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f689-142">See also</span></span>

- [<span data-ttu-id="6f689-143">WCF Veri Hizmetlerini Tanımlama</span><span class="sxs-lookup"><span data-stu-id="6f689-143">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)
- [<span data-ttu-id="6f689-144">Verilerinizi Hizmet Olarak Kullanıma Sunma</span><span class="sxs-lookup"><span data-stu-id="6f689-144">Exposing Your Data as a Service</span></span>](exposing-your-data-as-a-service-wcf-data-services.md)
- [<span data-ttu-id="6f689-145">Veri Hizmeti Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6f689-145">Configuring the Data Service</span></span>](configuring-the-data-service-wcf-data-services.md)
