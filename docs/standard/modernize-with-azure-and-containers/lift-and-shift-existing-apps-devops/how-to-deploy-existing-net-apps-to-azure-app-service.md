---
title: "Azure App Service'e varolan .NET uygulamalarını dağıtma"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Azure App Service'e varolan .NET uygulamalarını dağıtma"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: c83703c6f3dede0f92263e0d46bf48525c3eefaf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-deploy-existing-net-apps-to-azure-app-service"></a><span data-ttu-id="b21a8-103">Azure App Service'e varolan .NET uygulamalarını dağıtma</span><span class="sxs-lookup"><span data-stu-id="b21a8-103">How to deploy existing .NET apps to Azure App Service</span></span> 

<span data-ttu-id="b21a8-104">Azure App Service Web Apps özelliğini Web sitelerini ve web uygulamalarını barındırmak için iyileştirilmiş bir tam olarak yönetilen bir işlem platformudur.</span><span class="sxs-lookup"><span data-stu-id="b21a8-104">The Web Apps feature of Azure App Service is a fully managed compute platform that is optimized for hosting websites and web apps.</span></span> <span data-ttu-id="b21a8-105">Microsoft Azure sağlar, bu PaaS teklifi Azure alır çalıştırmak ve uygulamalarınızı ölçeklendirmek için altyapınızla ilgilenirken, iş mantığına odaklanın.</span><span class="sxs-lookup"><span data-stu-id="b21a8-105">This PaaS offering in Microsoft Azure lets you focus on your business logic, while Azure takes care of the infrastructure to run and scale your apps.</span></span>

## <a name="validate-sites-and-migrate-to-app-service-with-azure-app-service-migration-assistant"></a><span data-ttu-id="b21a8-106">Siteleri doğrulamak ve Azure App Service geçiş Yardımcısı ile App Service'e geçirme</span><span class="sxs-lookup"><span data-stu-id="b21a8-106">Validate sites and migrate to App Service with Azure App Service Migration Assistant</span></span>

<span data-ttu-id="b21a8-107">Visual Studio, uygulama için uygulama hizmeti genellikle taşıma yeni bir uygulama oluşturduğunuzda basittir.</span><span class="sxs-lookup"><span data-stu-id="b21a8-107">When you create a new application in Visual Studio, moving the app to App Service usually is straightforward.</span></span> <span data-ttu-id="b21a8-108">Uygulama hizmeti varolan bir uygulamaya geçirmeyi planlıyorsanız, ancak öncelikle tüm uygulama bağımlılıklarını App Service ile uyumlu olup olmadığını değerlendirmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="b21a8-108">However, if you are planning to migrate an existing application to App Service, first you need to evaluate whether all your application's dependencies are compatible with App Service.</span></span> <span data-ttu-id="b21a8-109">Bu, sunucu işletim sistemi ve sunucuda yüklü herhangi bir üçüncü taraf yazılım gibi bağımlılıkları içerir.</span><span class="sxs-lookup"><span data-stu-id="b21a8-109">This includes dependencies like server OS and any third-party software that's installed on the server.</span></span>

<span data-ttu-id="b21a8-110">Kullanabileceğiniz [Azure App Service geçiş Yardımcısı](https://www.migratetoazure.net/) siteleri çözümlemek ve bunları Windows ve Linux web sunucularından App Service'e geçirme.</span><span class="sxs-lookup"><span data-stu-id="b21a8-110">You can use [Azure App Service Migration Assistant](https://www.migratetoazure.net/) to analyze sites and then migrate them from Windows and Linux web servers to App Service.</span></span> <span data-ttu-id="b21a8-111">Geçiş işleminin bir parçası olarak aracı, web uygulamaları oluşturur ve Azure veritabanlarında gerektiği gibi içeriği yayımlar ve veritabanınızı yayımlar.</span><span class="sxs-lookup"><span data-stu-id="b21a8-111">As part of the migration, the tool creates web apps and databases on Azure as needed, publishes content, and publishes your database.</span></span>

<span data-ttu-id="b21a8-112">Azure uygulama hizmeti geçiş Yardımcısı buluta Windows Server'da çalışan IIS geçiş destekler.</span><span class="sxs-lookup"><span data-stu-id="b21a8-112">Azure App Service Migration Assistant supports migrating from IIS running on Windows Server to the cloud.</span></span> <span data-ttu-id="b21a8-113">Uygulama hizmeti, Windows Server 2003 ve sonraki sürümleri destekler.</span><span class="sxs-lookup"><span data-stu-id="b21a8-113">App Service supports Windows Server 2003 and later versions.</span></span>

> ![https://www.migratetoazure.NET/Images/ImageCanvas.PNG](./media/image5.png)
>
> <span data-ttu-id="b21a8-115">**Şekil 4-5.**</span><span class="sxs-lookup"><span data-stu-id="b21a8-115">**Figure 4-5.**</span></span> <span data-ttu-id="b21a8-116">Azure uygulama hizmeti geçiş Yardımcısını kullanma</span><span class="sxs-lookup"><span data-stu-id="b21a8-116">Using Azure App Service Migration Assistant</span></span>

<span data-ttu-id="b21a8-117">Uygulama hizmeti geçiş Yardımcısı, Web siteleri, web sunucularından Azure bulut taşınan bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="b21a8-117">App Service Migration Assistant is a tool that moves your websites from your web servers to the Azure cloud.</span></span>

<span data-ttu-id="b21a8-118">Bir Web sitesi için uygulama hizmeti geçirildikten sonra site güvenli ve verimli bir şekilde çalışması için gereken her şeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="b21a8-118">After a website is migrated to App Service, the site has everything it needs to run safely and efficiently.</span></span> <span data-ttu-id="b21a8-119">Siteleri ayarlamak ve otomatik olarak Azure bulut PaaS hizmeti (uygulama hizmeti) çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b21a8-119">Sites are set up and run automatically in the Azure cloud PaaS service (App Service).</span></span>

<span data-ttu-id="b21a8-120">Uygulama hizmeti geçiş aracı, Web sitelerinizi çözümleyebilir ve App Service'e taşıma için kendi uyumluluğu hakkında rapor oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b21a8-120">The App Service migration tool can analyze your websites and report on their compatibility for moving to App Service.</span></span> <span data-ttu-id="b21a8-121">Analizi ile memnun kaldıysanız, App Service geçiş içerik, veriler ve ayarlar, geçiş Yardımcısı izin verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b21a8-121">If you're happy with the analysis, you can let App Service Migration Assistant migrate content, data, and settings for you.</span></span> <span data-ttu-id="b21a8-122">Bir site oldukça uyumlu değilse, geçiş aracının çalışması için ayarlamak gerekenleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="b21a8-122">If a site is not quite compatible, the migration tool tells you what you need to adjust to make it work.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="b21a8-123">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="b21a8-123">Additional resources</span></span>

-   <span data-ttu-id="b21a8-124">**Azure uygulama hizmeti geçiş Yardımcısı**</span><span class="sxs-lookup"><span data-stu-id="b21a8-124">**Azure App Service Migration Assistant**</span></span>

    [<span data-ttu-id="b21a8-125">https://www.migratetoazure.NET/</span><span class="sxs-lookup"><span data-stu-id="b21a8-125">https://www.migratetoazure.net/</span></span>](https://www.migratetoazure.net/)

>[!div class="step-by-step"]
<span data-ttu-id="b21a8-126">[Önceki](what-about-cloud-optimized-applications.md)
[sonraki](deploy-existing-net-apps-as-windows-containers.md)</span><span class="sxs-lookup"><span data-stu-id="b21a8-126">[Previous](what-about-cloud-optimized-applications.md)
[Next](deploy-existing-net-apps-as-windows-containers.md)</span></span>
