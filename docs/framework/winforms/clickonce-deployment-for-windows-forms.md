---
title: "Windows Forms için ClickOnce Dağıtımı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ClickOnce deployment [Windows Forms]
- Windows Forms, ClickOnce deployment
- walkthroughs [Windows Forms], ClickOnce deployment
ms.assetid: 1451fce9-1965-4a03-b4d3-831b5fe4ad66
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1f157ea4afcaccfffde548c26a440fa6686c87aa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="clickonce-deployment-for-windows-forms"></a><span data-ttu-id="86d48-102">Windows Forms için ClickOnce Dağıtımı</span><span class="sxs-lookup"><span data-stu-id="86d48-102">ClickOnce Deployment for Windows Forms</span></span>
<span data-ttu-id="86d48-103">Aşağıdaki konularda açıklanmıştır [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)], kolayca Windows Forms uygulamaları istemci bilgisayarlara dağıtmak için kullanılan bir teknoloji.</span><span class="sxs-lookup"><span data-stu-id="86d48-103">The following topics describe [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)], a technology used for easily deploying Windows Forms applications to client computers.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="86d48-104">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="86d48-104">Related Sections</span></span>  
 [<span data-ttu-id="86d48-105">ClickOnce Dağıtım Stratejisini Seçme</span><span class="sxs-lookup"><span data-stu-id="86d48-105">Choosing a ClickOnce Deployment Strategy</span></span>](/visualstudio/deployment/choosing-a-clickonce-deployment-strategy)  
 <span data-ttu-id="86d48-106">Dağıtmak için çeşitli seçenekler sunar [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="86d48-106">Presents several options for deploying [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] applications.</span></span>  
  
 [<span data-ttu-id="86d48-107">ClickOnce Güncelleştirme Stratejisini Seçme</span><span class="sxs-lookup"><span data-stu-id="86d48-107">Choosing a ClickOnce Update Strategy</span></span>](/visualstudio/deployment/choosing-a-clickonce-update-strategy)  
 <span data-ttu-id="86d48-108">Güncelleştirme için çeşitli seçenekler sunar [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="86d48-108">Presents several options for updating [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] applications.</span></span>  
  
 [<span data-ttu-id="86d48-109">ClickOnce Uygulamalarının Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="86d48-109">Securing ClickOnce Applications</span></span>](/visualstudio/deployment/securing-clickonce-applications)  
 <span data-ttu-id="86d48-110">Güvenlikle ilgili etkileri açıklanmaktadır [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] dağıtım.</span><span class="sxs-lookup"><span data-stu-id="86d48-110">Explains the security implications of [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] deployment.</span></span>  
  
 [<span data-ttu-id="86d48-111">ClickOnce Dağıtım Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="86d48-111">Troubleshooting ClickOnce Deployments</span></span>](/visualstudio/deployment/troubleshooting-clickonce-deployments)  
 <span data-ttu-id="86d48-112">Dağıtırken oluşabilecek çeşitli sorunları açıklar [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] uygulamaları ve belgeleri en üst düzey hata iletilerini [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="86d48-112">Describes various problems that can occur when deploying [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] applications, and documents the top-level error messages that [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] might generate.</span></span>  
  
 [<span data-ttu-id="86d48-113">ClickOnce ve Uygulama Ayarları</span><span class="sxs-lookup"><span data-stu-id="86d48-113">ClickOnce and Application Settings</span></span>](/visualstudio/deployment/clickonce-and-application-settings)  
 <span data-ttu-id="86d48-114">Açıklar nasıl [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] dağıtım gelecekteki alma için uygulama ve kullanıcı ayarlarını depolayan uygulama ayarları ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="86d48-114">Describes how [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] deployment works with application settings, which stores application and user settings for future retrieval.</span></span>  
  
 [<span data-ttu-id="86d48-115">Güvenilir Uygulama Dağıtımına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="86d48-115">Trusted Application Deployment Overview</span></span>](/visualstudio/deployment/trusted-application-deployment-overview)  
 <span data-ttu-id="86d48-116">Açıklayan bir [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] daha yüksek bir izin düzeyi ile istemci bilgisayarlarda çalıştırmak güvenilir uygulamalar sağlayan özelliği.</span><span class="sxs-lookup"><span data-stu-id="86d48-116">Describes a [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] feature that allows trusted applications to run with a higher level of permission on client computers.</span></span>  
  
 [<span data-ttu-id="86d48-117">ClickOnce ve Authenticode</span><span class="sxs-lookup"><span data-stu-id="86d48-117">ClickOnce and Authenticode</span></span>](/visualstudio/deployment/clickonce-and-authenticode)  
 <span data-ttu-id="86d48-118">Güvenilir Uygulama Dağıtımı'Authenticode teknolojisi nasıl kullanıldığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="86d48-118">Describes how Authenticode technology is used in trusted application deployment.</span></span>  
  
 [<span data-ttu-id="86d48-119">İzlenecek yol: ClickOnce Uygulamasını El ile Dağıtma</span><span class="sxs-lookup"><span data-stu-id="86d48-119">Walkthrough: Manually Deploying a ClickOnce Application</span></span>](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)  
 <span data-ttu-id="86d48-120">Komut satırı kullanarak ve SDK Araçları dağıtmayı gösteren bir [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] Visual Studio kullanmadan uygulama.</span><span class="sxs-lookup"><span data-stu-id="86d48-120">Demonstrates using command-line and SDK tools to deploy a [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] application without using Visual Studio.</span></span>  
  
 [<span data-ttu-id="86d48-121">Nasıl yapılır: ClickOnce Uygulamaları için Sunucu Bilgisayara Güvenilir Yayımcı Ekleme</span><span class="sxs-lookup"><span data-stu-id="86d48-121">How to: Add a Trusted Publisher to a Client Computer for ClickOnce Applications</span></span>](/visualstudio/deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications)  
 <span data-ttu-id="86d48-122">Güvenilir uygulama dağıtımı için gerekli istemci bilgisayarların tek seferlik yapılandırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="86d48-122">Demonstrates the one-time configuration of client computers required for trusted application deployment.</span></span>  
  
 [<span data-ttu-id="86d48-123">Nasıl yapılır: Dağıtım Güncelleştirmeleri için Alternatif Bir Konum Belirtme</span><span class="sxs-lookup"><span data-stu-id="86d48-123">How to: Specify an Alternate Location for Deployment Updates</span></span>](/visualstudio/deployment/how-to-specify-an-alternate-location-for-deployment-updates)  
 <span data-ttu-id="86d48-124">Yapılandırma gösteren bir [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] uygulama, bir uygulamanın yeni sürümlerini için farklı bir konum denetlemek için SDK araçları kullanarak.</span><span class="sxs-lookup"><span data-stu-id="86d48-124">Demonstrates configuring a [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] application, using SDK tools, to check a different location for new versions of an application.</span></span>  
  
 [<span data-ttu-id="86d48-125">İzlenecek yol: ClickOnce Dağıtım API'si ile İsteğe Bağlı Derlemeleri İndirme</span><span class="sxs-lookup"><span data-stu-id="86d48-125">Walkthrough: Downloading Assemblies on Demand with the ClickOnce Deployment API</span></span>](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api)  
 <span data-ttu-id="86d48-126">Uygulamanızı yüklemek için çalışır bir derleme ilk zaman almak için API çağrılarını kullanarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="86d48-126">Demonstrates using API calls to retrieve an assembly the first time your application attempts to load it.</span></span>  
  
 [<span data-ttu-id="86d48-127">Nasıl yapılır: Çevrimiçi bir ClickOnce Uygulamasında Sorgu Dize Bilgilerini Alma</span><span class="sxs-lookup"><span data-stu-id="86d48-127">How to: Retrieve Query String Information in an Online ClickOnce Application</span></span>](/visualstudio/deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application)  
 <span data-ttu-id="86d48-128">Çalıştırmak için kullanılan URL'yi alınırken parametreleri gösteren bir [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="86d48-128">Demonstrates retrieving parameters from the URL used to run a [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] application.</span></span>  
  
 [<span data-ttu-id="86d48-129">ClickOnce Önbelleğine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="86d48-129">ClickOnce Cache Overview</span></span>](/visualstudio/deployment/clickonce-cache-overview)  
 <span data-ttu-id="86d48-130">Depolamak için kullanılan önbellek açıklar [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] yerel bilgisayardaki uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="86d48-130">Describes the cache used to store [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] applications on the local computer.</span></span>  
  
 [<span data-ttu-id="86d48-131">ClickOnce Uygulamalarında Yerel ve Uzak Veri Erişimi</span><span class="sxs-lookup"><span data-stu-id="86d48-131">Accessing Local and Remote Data in ClickOnce Applications</span></span>](/visualstudio/deployment/accessing-local-and-remote-data-in-clickonce-applications)  
 <span data-ttu-id="86d48-132">Yerel veri dosyaları ve uzak veri kaynaklarından nasıl erişileceği açıklayan bir [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="86d48-132">Describes how to access local data files and remote data sources from a [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] application.</span></span>  
  
 [<span data-ttu-id="86d48-133">Nasıl yapılır: ClickOnce Uygulamasına bir Veri Dosyası Dahil Etme</span><span class="sxs-lookup"><span data-stu-id="86d48-133">How to: Include a Data File in a ClickOnce Application</span></span>](/visualstudio/deployment/how-to-include-a-data-file-in-a-clickonce-application)  
 <span data-ttu-id="86d48-134">Böylece, kullanılabilir bir dosyayı işaretler gösterilmiştir [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] veri dizini.</span><span class="sxs-lookup"><span data-stu-id="86d48-134">Demonstrates how to mark a file so that it is available in the [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] data directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86d48-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="86d48-135">See Also</span></span>  
 [<span data-ttu-id="86d48-136">Uygulama Ayarlarına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="86d48-136">Application Settings Overview</span></span>](../../../docs/framework/winforms/advanced/application-settings-overview.md)  
 [<span data-ttu-id="86d48-137">ClickOnce Uygulamalarını Yayımlama</span><span class="sxs-lookup"><span data-stu-id="86d48-137">Publishing ClickOnce Applications</span></span>](/visualstudio/deployment/publishing-clickonce-applications)  
 [<span data-ttu-id="86d48-138">Komut Satırından ClickOnce Uygulamalarını Derleme</span><span class="sxs-lookup"><span data-stu-id="86d48-138">Building ClickOnce Applications from the Command Line</span></span>](/visualstudio/deployment/building-clickonce-applications-from-the-command-line)  
 [<span data-ttu-id="86d48-139">System.Deployment.Application Kullanan ClickOnce Uygulamalarında Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="86d48-139">Debugging ClickOnce Applications That Use System.Deployment.Application</span></span>](http://msdn.microsoft.com/library/86f31948-2ca8-47c0-8e8b-c2b817bbf79f)  
 [<span data-ttu-id="86d48-140">ClickOnce ile COM Bileşenleri Dağıtma</span><span class="sxs-lookup"><span data-stu-id="86d48-140">Deploying COM Components with ClickOnce</span></span>](/visualstudio/deployment/deploying-com-components-with-clickonce)  
 [<span data-ttu-id="86d48-141">Nasıl yapılır: Yayımlama Sihirbazını Kullanarak ClickOnce Uygulaması Yayımlama</span><span class="sxs-lookup"><span data-stu-id="86d48-141">How to: Publish a ClickOnce Application using the Publish Wizard</span></span>](/visualstudio/deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard)
