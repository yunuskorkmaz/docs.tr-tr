---
title: Windows Hizmet Uygulamaları Geliştirme
description: Visual Studio veya .NET SDK kullanarak Windows hizmeti uygulamaları geliştirmeyi açıklayan makalelerin bağlantılarını inceleyin.
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
ms.openlocfilehash: 2aea73267f05340930a9591f430de59677c1cb11
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609583"
---
# <a name="develop-windows-service-apps"></a><span data-ttu-id="1d1a4-103">Windows hizmeti uygulamaları geliştirme</span><span class="sxs-lookup"><span data-stu-id="1d1a4-103">Develop Windows service apps</span></span>

<span data-ttu-id="1d1a4-104">Visual Studio veya .NET Framework SDK kullanarak, hizmet olarak yüklenen bir uygulama oluşturarak kolayca hizmet oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d1a4-104">Using Visual Studio or the .NET Framework SDK, you can easily create services by creating an application that is installed as a service.</span></span> <span data-ttu-id="1d1a4-105">Bu tür bir uygulama Windows hizmeti olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="1d1a4-105">This type of application is called a Windows service.</span></span> <span data-ttu-id="1d1a4-106">Çerçeve özellikleri sayesinde, hizmetler oluşturabilir, bunları yükleyebilir ve davranışlarını başlatabilir, durdurabilir ve başka bir şekilde denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d1a4-106">With framework features, you can create services, install them, and start, stop, and otherwise control their behavior.</span></span>

> [!NOTE]
> <span data-ttu-id="1d1a4-107">Visual Studio 'da, Visual C# veya Visual Basic yönetilen kodda bir hizmet oluşturabilirsiniz. Bu, gerekirse mevcut C++ kodu ile birlikte çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="1d1a4-107">In Visual Studio you can create a service in managed code in Visual C# or Visual Basic, which can interoperate with existing C++ code if required.</span></span> <span data-ttu-id="1d1a4-108">Veya, [atl Proje Sihirbazı 'nı](/cpp/atl/reference/atl-project-wizard)kullanarak yerel C++ ' da bir Windows hizmeti oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d1a4-108">Or, you can create a Windows service in native C++ by using the [ATL Project Wizard](/cpp/atl/reference/atl-project-wizard).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="1d1a4-109">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="1d1a4-109">In this section</span></span>

[<span data-ttu-id="1d1a4-110">Windows Hizmet Uygulamalarına Giriş</span><span class="sxs-lookup"><span data-stu-id="1d1a4-110">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)

<span data-ttu-id="1d1a4-111">Windows hizmet uygulamalarına genel bakış, bir hizmetin kullanım süresi ve hizmet uygulamalarının diğer ortak proje türlerinden farkı nasıl farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="1d1a4-111">Provides an overview of Windows service applications, the lifetime of a service, and how service applications differ from other common project types.</span></span>

[<span data-ttu-id="1d1a4-112">İzlenecek Yol: Bileşen Tasarımcısında Windows Hizmeti Uygulaması Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1d1a4-112">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)

<span data-ttu-id="1d1a4-113">Visual Basic ve Visual C# ' de bir hizmet oluşturmak için bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="1d1a4-113">Provides an example of creating a service in Visual Basic and Visual C#.</span></span>

[<span data-ttu-id="1d1a4-114">Hizmet Uygulaması Programlama Mimarisi</span><span class="sxs-lookup"><span data-stu-id="1d1a4-114">Service Application Programming Architecture</span></span>](service-application-programming-architecture.md)

<span data-ttu-id="1d1a4-115">Hizmet programlamasında kullanılan dil öğelerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="1d1a4-115">Explains the language elements used in service programming.</span></span>

[<span data-ttu-id="1d1a4-116">Nasıl yapılır: Windows Hizmetleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1d1a4-116">How to: Create Windows Services</span></span>](how-to-create-windows-services.md)

<span data-ttu-id="1d1a4-117">Windows hizmeti proje şablonunu kullanarak Windows hizmetlerini oluşturma ve yapılandırma sürecini açıklar.</span><span class="sxs-lookup"><span data-stu-id="1d1a4-117">Describes the process of creating and configuring Windows services using the Windows service project template.</span></span>

## <a name="related-sections"></a><span data-ttu-id="1d1a4-118">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="1d1a4-118">Related sections</span></span>

<span data-ttu-id="1d1a4-119"><xref:System.ServiceProcess.ServiceBase> - <xref:System.ServiceProcess.ServiceBase> Sınıfının hizmetleri oluşturmak için kullanılan ana özelliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="1d1a4-119"><xref:System.ServiceProcess.ServiceBase> - Describes the major features of the <xref:System.ServiceProcess.ServiceBase> class, which is used to create services.</span></span>

<span data-ttu-id="1d1a4-120"><xref:System.ServiceProcess.ServiceProcessInstaller> - <xref:System.ServiceProcess.ServiceProcessInstaller> <xref:System.ServiceProcess.ServiceInstaller> Hizmetlerinizi yüklemek ve kaldırmak için sınıfıyla birlikte kullanılan sınıfının özelliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="1d1a4-120"><xref:System.ServiceProcess.ServiceProcessInstaller> - Describes the features of the <xref:System.ServiceProcess.ServiceProcessInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceInstaller> class to install and uninstall your services.</span></span>

<span data-ttu-id="1d1a4-121"><xref:System.ServiceProcess.ServiceInstaller> - <xref:System.ServiceProcess.ServiceInstaller> <xref:System.ServiceProcess.ServiceProcessInstaller> Hizmetinizi yüklemek ve kaldırmak için sınıfıyla birlikte kullanılan sınıfının özelliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="1d1a4-121"><xref:System.ServiceProcess.ServiceInstaller> - Describes the features of the <xref:System.ServiceProcess.ServiceInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceProcessInstaller> class to install and uninstall your service.</span></span>

<span data-ttu-id="1d1a4-122">[Şablonlardan proje oluşturma](/previous-versions/visualstudio/visual-studio-2013/0fyc0azh(v=vs.120)) -bu bölümde kullanılan proje türlerini ve bunların arasından nasıl seçim yapılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="1d1a4-122">[Create Projects from Templates](/previous-versions/visualstudio/visual-studio-2013/0fyc0azh(v=vs.120)) -  Describes the projects types used in this chapter and how to choose between them.</span></span>
