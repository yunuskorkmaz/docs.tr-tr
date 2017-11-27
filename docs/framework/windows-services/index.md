---
title: "Windows Hizmet Uygulamaları Geliştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ServiceInstaller class, Windows Service applications
- Service class, Windows Service applications
- Windows Service applications
- Windows NT services
- ServiceProcessInstaller class, Windows Service applications
- services
- .NET applications, Windows applications
ms.assetid: ba72d648-9553-4849-b829-069ad5ea014b
caps.latest.revision: "18"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: 2912568e967c8c6096842b1b4f24eac88318dffb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="developing-windows-service-applications"></a><span data-ttu-id="2216e-102">Windows Hizmet Uygulamaları Geliştirme</span><span class="sxs-lookup"><span data-stu-id="2216e-102">Developing Windows Service Applications</span></span>
<span data-ttu-id="2216e-103">Microsoft kullanılarak [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] veya Microsoft [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK, kolayca oluşturabileceğiniz Hizmetleri hizmeti olarak yüklenen bir uygulama oluşturarak.</span><span class="sxs-lookup"><span data-stu-id="2216e-103">Using Microsoft [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] or the Microsoft [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK, you can easily create services by creating an application that is installed as a service.</span></span> <span data-ttu-id="2216e-104">Bu tür bir uygulama bir Windows hizmeti adı verilir.</span><span class="sxs-lookup"><span data-stu-id="2216e-104">This type of application is called a Windows service.</span></span> <span data-ttu-id="2216e-105">Framework özelliklerle hizmetleri oluşturmak, bunları yüklemeniz ve Başlat, durdurabilir ve davranışlarını denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2216e-105">With framework features, you can create services, install them, and start, stop, and otherwise control their behavior.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="2216e-106">Windows hizmet şablonu C++ için Visual Studio 2010'da dahil edilmedi.</span><span class="sxs-lookup"><span data-stu-id="2216e-106">The Windows service template for C++ was not included in Visual Studio 2010.</span></span> <span data-ttu-id="2216e-107">Bir Windows hizmeti oluşturmak için Visual C# veya Visual Basic, gerekirse mevcut C++ kodu ile birlikte çalışmak, yönetilen kodda bir hizmeti oluşturabilir veya kullanarak bir Windows hizmeti yerel C++'da oluşturabilirsiniz [ATL Proje Sihirbazı](/cpp/atl/reference/atl-project-wizard).</span><span class="sxs-lookup"><span data-stu-id="2216e-107">To create a Windows service, you can either create a service in managed code in Visual C# or Visual Basic, which could interoperate with existing C++ code if required, or you can create a Windows service in native C++ by using the [ATL Project Wizard](/cpp/atl/reference/atl-project-wizard).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2216e-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="2216e-108">In This Section</span></span>  
 [<span data-ttu-id="2216e-109">Windows hizmet uygulamalarına giriş</span><span class="sxs-lookup"><span data-stu-id="2216e-109">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 <span data-ttu-id="2216e-110">Bir hizmet ve hizmet uygulamalarının diğer ortak proje türlerinden farklılıklar ömrü Windows hizmet uygulamaları, genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="2216e-110">Provides an overview of Windows service applications, the lifetime of a service, and how service applications differ from other common project types.</span></span>  
  
 [<span data-ttu-id="2216e-111">İzlenecek yol: Bileşen tasarımcısında Windows hizmet uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="2216e-111">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)  
 <span data-ttu-id="2216e-112">Hizmet oluşturma örneğidir [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] ve Visual C#.</span><span class="sxs-lookup"><span data-stu-id="2216e-112">Provides an example of creating a service in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] and Visual C#.</span></span>  
  
 [<span data-ttu-id="2216e-113">Hizmet uygulaması programlama mimarisi</span><span class="sxs-lookup"><span data-stu-id="2216e-113">Service Application Programming Architecture</span></span>](../../../docs/framework/windows-services/service-application-programming-architecture.md)  
 <span data-ttu-id="2216e-114">Hizmet programlamada kullanılan dil öğeleri açıklanır.</span><span class="sxs-lookup"><span data-stu-id="2216e-114">Explains the language elements used in service programming.</span></span>  
  
 [<span data-ttu-id="2216e-115">Nasıl yapılır: Windows Hizmetleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="2216e-115">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 <span data-ttu-id="2216e-116">Oluşturma ve Windows hizmeti proje şablonunu kullanarak Windows Hizmetleri yapılandırma sürecini açıklar.</span><span class="sxs-lookup"><span data-stu-id="2216e-116">Describes the process of creating and configuring Windows services using the Windows service project template.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2216e-117">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="2216e-117">Related Sections</span></span>  
 <xref:System.ServiceProcess.ServiceBase>  
 <span data-ttu-id="2216e-118">En önemli özelliklerini açıklayan <xref:System.ServiceProcess.ServiceBase> hizmetleri oluşturmak için kullanılan sınıf.</span><span class="sxs-lookup"><span data-stu-id="2216e-118">Describes the major features of the <xref:System.ServiceProcess.ServiceBase> class, which is used to create services.</span></span>  
  
 <xref:System.ServiceProcess.ServiceProcessInstaller>  
 <span data-ttu-id="2216e-119">Özelliklerini açıklayan <xref:System.ServiceProcess.ServiceProcessInstaller> ile birlikte kullanılan sınıf <xref:System.ServiceProcess.ServiceInstaller> yüklemek ve hizmetlerinizi kaldırmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="2216e-119">Describes the features of the <xref:System.ServiceProcess.ServiceProcessInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceInstaller> class to install and uninstall your services.</span></span>  
  
 <xref:System.ServiceProcess.ServiceInstaller>  
 <span data-ttu-id="2216e-120">Özelliklerini açıklayan <xref:System.ServiceProcess.ServiceInstaller> ile birlikte kullanılan sınıf <xref:System.ServiceProcess.ServiceProcessInstaller> yükleyip hizmetinizi kaldırmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="2216e-120">Describes the features of the <xref:System.ServiceProcess.ServiceInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceProcessInstaller> class to install and uninstall your service.</span></span>  
  
 [<span data-ttu-id="2216e-121">Şablonlardan NIB oluşturma projeleri</span><span class="sxs-lookup"><span data-stu-id="2216e-121">NIB Creating Projects from Templates</span></span>](http://msdn.microsoft.com/en-us/7c36d86a-6b79-4480-8228-0f925f1204b2)  
 <span data-ttu-id="2216e-122">Projeleri açıklar ve bunlar arasında seçim yapma Bu bölümde kullanılan türleri.</span><span class="sxs-lookup"><span data-stu-id="2216e-122">Describes the projects types used in this chapter and how to choose between them.</span></span>
