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
ms.openlocfilehash: 61f969c22ac06bd6ed20ccfa9124db3bb35d0692
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053551"
---
# <a name="develop-windows-service-apps"></a><span data-ttu-id="a762b-102">Windows hizmeti uygulamaları geliştirme</span><span class="sxs-lookup"><span data-stu-id="a762b-102">Develop Windows service apps</span></span>

<span data-ttu-id="a762b-103">Visual Studio veya .NET Framework SDK kullanarak, hizmet olarak yüklenen bir uygulama oluşturarak kolayca hizmet oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a762b-103">Using Visual Studio or the .NET Framework SDK, you can easily create services by creating an application that is installed as a service.</span></span> <span data-ttu-id="a762b-104">Bu tür bir uygulama Windows hizmeti olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="a762b-104">This type of application is called a Windows service.</span></span> <span data-ttu-id="a762b-105">Çerçeve özellikleri sayesinde, hizmetler oluşturabilir, bunları yükleyebilir ve davranışlarını başlatabilir, durdurabilir ve başka bir şekilde denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a762b-105">With framework features, you can create services, install them, and start, stop, and otherwise control their behavior.</span></span>

> [!NOTE]
> <span data-ttu-id="a762b-106">Visual Studio 'da, Visual C# veya Visual Basic yönetilen kodda bir hizmet oluşturabilirsiniz. Bu, gerekirse mevcut C++ kodla birlikte çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="a762b-106">In Visual Studio you can create a service in managed code in Visual C# or Visual Basic, which can interoperate with existing C++ code if required.</span></span> <span data-ttu-id="a762b-107">Veya, C++ [atl Proje Sihirbazı 'nı](/cpp/atl/reference/atl-project-wizard)kullanarak yerel olarak bir Windows hizmeti oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a762b-107">Or, you can create a Windows service in native C++ by using the [ATL Project Wizard](/cpp/atl/reference/atl-project-wizard).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="a762b-108">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="a762b-108">In this section</span></span>

[<span data-ttu-id="a762b-109">Windows Hizmeti Uygulamalarına Giriş</span><span class="sxs-lookup"><span data-stu-id="a762b-109">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)

<span data-ttu-id="a762b-110">Windows hizmet uygulamalarına genel bakış, bir hizmetin kullanım süresi ve hizmet uygulamalarının diğer ortak proje türlerinden farkı nasıl farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="a762b-110">Provides an overview of Windows service applications, the lifetime of a service, and how service applications differ from other common project types.</span></span>

[<span data-ttu-id="a762b-111">İzlenecek yol: Bileşen tasarımcısında bir Windows hizmeti uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="a762b-111">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)

<span data-ttu-id="a762b-112">Visual Basic ve görselde C#bir hizmet oluşturma örneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="a762b-112">Provides an example of creating a service in Visual Basic and Visual C#.</span></span>

[<span data-ttu-id="a762b-113">Hizmet Uygulaması Programlama Mimarisi</span><span class="sxs-lookup"><span data-stu-id="a762b-113">Service Application Programming Architecture</span></span>](service-application-programming-architecture.md)

<span data-ttu-id="a762b-114">Hizmet programlamasında kullanılan dil öğelerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="a762b-114">Explains the language elements used in service programming.</span></span>

[<span data-ttu-id="a762b-115">Nasıl yapılır: Windows Hizmetleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="a762b-115">How to: Create Windows Services</span></span>](how-to-create-windows-services.md)

<span data-ttu-id="a762b-116">Windows hizmeti proje şablonunu kullanarak Windows hizmetlerini oluşturma ve yapılandırma sürecini açıklar.</span><span class="sxs-lookup"><span data-stu-id="a762b-116">Describes the process of creating and configuring Windows services using the Windows service project template.</span></span>

## <a name="related-sections"></a><span data-ttu-id="a762b-117">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="a762b-117">Related sections</span></span>

<span data-ttu-id="a762b-118"><xref:System.ServiceProcess.ServiceBase>- <xref:System.ServiceProcess.ServiceBase> Sınıfının hizmetleri oluşturmak için kullanılan ana özelliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="a762b-118"><xref:System.ServiceProcess.ServiceBase> - Describes the major features of the <xref:System.ServiceProcess.ServiceBase> class, which is used to create services.</span></span>

<span data-ttu-id="a762b-119"><xref:System.ServiceProcess.ServiceProcessInstaller>-Hizmetlerinizi yüklemek ve kaldırmak için <xref:System.ServiceProcess.ServiceProcessInstaller> <xref:System.ServiceProcess.ServiceInstaller> sınıfıyla birlikte kullanılan sınıfının özelliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="a762b-119"><xref:System.ServiceProcess.ServiceProcessInstaller> - Describes the features of the <xref:System.ServiceProcess.ServiceProcessInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceInstaller> class to install and uninstall your services.</span></span>

<span data-ttu-id="a762b-120"><xref:System.ServiceProcess.ServiceInstaller>-Hizmetinizi yüklemek ve kaldırmak için <xref:System.ServiceProcess.ServiceInstaller> <xref:System.ServiceProcess.ServiceProcessInstaller> sınıfıyla birlikte kullanılan sınıfının özelliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="a762b-120"><xref:System.ServiceProcess.ServiceInstaller> - Describes the features of the <xref:System.ServiceProcess.ServiceInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceProcessInstaller> class to install and uninstall your service.</span></span>

<span data-ttu-id="a762b-121">[Şablonlardan proje oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0fyc0azh(v=vs.120)) -bu bölümde kullanılan proje türlerini ve bunların arasından nasıl seçim yapılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="a762b-121">[Create Projects from Templates](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0fyc0azh(v=vs.120)) -  Describes the projects types used in this chapter and how to choose between them.</span></span>
