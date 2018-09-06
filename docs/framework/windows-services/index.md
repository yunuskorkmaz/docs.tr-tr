---
title: Windows Hizmet Uygulamaları Geliştirme
ms.date: 03/30/2017
helpviewer_keywords:
- ServiceInstaller class, Windows Service applications
- Service class, Windows Service applications
- Windows Service applications
- Windows NT services
- ServiceProcessInstaller class, Windows Service applications
- services
- .NET applications, Windows applications
ms.assetid: ba72d648-9553-4849-b829-069ad5ea014b
author: ghogen
manager: douge
ms.openlocfilehash: 2c7fb148b96d5ff9804bcb0bb7c842c475c0f117
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43740836"
---
# <a name="developing-windows-service-applications"></a><span data-ttu-id="943cb-102">Windows Hizmet Uygulamaları Geliştirme</span><span class="sxs-lookup"><span data-stu-id="943cb-102">Developing Windows Service Applications</span></span>
<span data-ttu-id="943cb-103">Microsoft Visual Studio veya Microsoft kullanarak [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK'sı, kolayca oluşturmak için kullanabileceğiniz Hizmetleri hizmeti olarak yüklenen bir uygulama oluşturarak.</span><span class="sxs-lookup"><span data-stu-id="943cb-103">Using Microsoft Visual Studio or the Microsoft [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK, you can easily create services by creating an application that is installed as a service.</span></span> <span data-ttu-id="943cb-104">Bu tür bir uygulama, bir Windows hizmeti olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="943cb-104">This type of application is called a Windows service.</span></span> <span data-ttu-id="943cb-105">Framework özellikleri ile Hizmetleri oluşturun, bunları yükleyin ve başlatın, durdurabilir ve davranışlarını denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="943cb-105">With framework features, you can create services, install them, and start, stop, and otherwise control their behavior.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="943cb-106">Visual Studio 2010'da Windows hizmet şablonunu c++ eklenmez.</span><span class="sxs-lookup"><span data-stu-id="943cb-106">The Windows service template for C++ was not included in Visual Studio 2010.</span></span> <span data-ttu-id="943cb-107">Bir Windows hizmeti oluşturmak için Visual C# veya gerekirse mevcut C++ kodu ile birlikte çalışmak, Visual Basic, yönetilen kodda bir hizmeti oluşturabilir veya kullanarak, yerleşik C++'da bir Windows hizmeti oluşturabilirsiniz [ATL projesi Sihirbazı](/cpp/atl/reference/atl-project-wizard).</span><span class="sxs-lookup"><span data-stu-id="943cb-107">To create a Windows service, you can either create a service in managed code in Visual C# or Visual Basic, which could interoperate with existing C++ code if required, or you can create a Windows service in native C++ by using the [ATL Project Wizard](/cpp/atl/reference/atl-project-wizard).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="943cb-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="943cb-108">In This Section</span></span>  
 [<span data-ttu-id="943cb-109">Windows Hizmeti Uygulamalarına Giriş</span><span class="sxs-lookup"><span data-stu-id="943cb-109">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 <span data-ttu-id="943cb-110">Bir hizmet ve hizmet uygulamaları diğer ortak proje türlerinden farklılıklar ömrünü Windows hizmet uygulamaları, genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="943cb-110">Provides an overview of Windows service applications, the lifetime of a service, and how service applications differ from other common project types.</span></span>  
  
 [<span data-ttu-id="943cb-111">İzlenecek Yol: Bileşen Tasarımcısında Windows Hizmeti Uygulaması Oluşturma</span><span class="sxs-lookup"><span data-stu-id="943cb-111">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)  
 <span data-ttu-id="943cb-112">Visual Basic ve Visual C# içinde bir hizmet oluşturma örneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="943cb-112">Provides an example of creating a service in Visual Basic and Visual C#.</span></span>  
  
 [<span data-ttu-id="943cb-113">Hizmet Uygulaması Programlama Mimarisi</span><span class="sxs-lookup"><span data-stu-id="943cb-113">Service Application Programming Architecture</span></span>](../../../docs/framework/windows-services/service-application-programming-architecture.md)  
 <span data-ttu-id="943cb-114">Hizmet programlamada kullanılan dil öğelerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="943cb-114">Explains the language elements used in service programming.</span></span>  
  
 [<span data-ttu-id="943cb-115">Nasıl Yapılır: Windows Hizmetleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="943cb-115">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 <span data-ttu-id="943cb-116">Oluşturma ve Windows services Windows hizmeti proje şablonunu kullanarak yapılandırma işlemi açıklanır.</span><span class="sxs-lookup"><span data-stu-id="943cb-116">Describes the process of creating and configuring Windows services using the Windows service project template.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="943cb-117">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="943cb-117">Related Sections</span></span>  
 <xref:System.ServiceProcess.ServiceBase>  
 <span data-ttu-id="943cb-118">Önemli özelliklerini açıklar <xref:System.ServiceProcess.ServiceBase> hizmetleri oluşturmak için kullanılan sınıf.</span><span class="sxs-lookup"><span data-stu-id="943cb-118">Describes the major features of the <xref:System.ServiceProcess.ServiceBase> class, which is used to create services.</span></span>  
  
 <xref:System.ServiceProcess.ServiceProcessInstaller>  
 <span data-ttu-id="943cb-119">Özelliklerini açıklayan <xref:System.ServiceProcess.ServiceProcessInstaller> ile birlikte kullanılan sınıfı <xref:System.ServiceProcess.ServiceInstaller> yüklemek ve hizmetlerinizi kaldırmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="943cb-119">Describes the features of the <xref:System.ServiceProcess.ServiceProcessInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceInstaller> class to install and uninstall your services.</span></span>  
  
 <xref:System.ServiceProcess.ServiceInstaller>  
 <span data-ttu-id="943cb-120">Özelliklerini açıklayan <xref:System.ServiceProcess.ServiceInstaller> ile birlikte kullanılan sınıfı <xref:System.ServiceProcess.ServiceProcessInstaller> yüklemek ve hizmetinizi kaldırmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="943cb-120">Describes the features of the <xref:System.ServiceProcess.ServiceInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceProcessInstaller> class to install and uninstall your service.</span></span>  
  
 [<span data-ttu-id="943cb-121">NIB oluşturma proje şablonları</span><span class="sxs-lookup"><span data-stu-id="943cb-121">NIB Creating Projects from Templates</span></span>](https://msdn.microsoft.com/library/7c36d86a-6b79-4480-8228-0f925f1204b2)  
 <span data-ttu-id="943cb-122">Projeleri açıklar ve bunlar arasında seçim yapma Bu bölümde kullanılan türleri.</span><span class="sxs-lookup"><span data-stu-id="943cb-122">Describes the projects types used in this chapter and how to choose between them.</span></span>
