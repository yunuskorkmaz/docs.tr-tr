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
ms.openlocfilehash: 79de8adbc0f994653f308882b335da2ffa5f7455
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48035928"
---
# <a name="develop-windows-service-apps"></a><span data-ttu-id="9bb87-102">Windows hizmet uygulamaları geliştirme</span><span class="sxs-lookup"><span data-stu-id="9bb87-102">Develop Windows service apps</span></span>

<span data-ttu-id="9bb87-103">Visual Studio veya .NET Framework SDK'sını kullanarak bir hizmet olarak yüklenen bir uygulama oluşturarak, hizmetleri kolayca oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9bb87-103">Using Visual Studio or the .NET Framework SDK, you can easily create services by creating an application that is installed as a service.</span></span> <span data-ttu-id="9bb87-104">Bu tür bir uygulama, bir Windows hizmeti olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="9bb87-104">This type of application is called a Windows service.</span></span> <span data-ttu-id="9bb87-105">Framework özellikleri ile Hizmetleri oluşturun, bunları yükleyin ve başlatın, durdurabilir ve davranışlarını denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9bb87-105">With framework features, you can create services, install them, and start, stop, and otherwise control their behavior.</span></span>

> [!NOTE]
> <span data-ttu-id="9bb87-106">Visual Studio'da Visual C# veya Visual Basic, ile mevcut C++ kodunu gerekirse çalışabilirler yönetilen kodda bir hizmet oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9bb87-106">In Visual Studio you can create a service in managed code in Visual C# or Visual Basic, which can interoperate with existing C++ code if required.</span></span> <span data-ttu-id="9bb87-107">Ya da kullanarak yerel C++'da bir Windows hizmeti oluşturabilirsiniz [ATL projesi Sihirbazı](/cpp/atl/reference/atl-project-wizard).</span><span class="sxs-lookup"><span data-stu-id="9bb87-107">Or, you can create a Windows service in native C++ by using the [ATL Project Wizard](/cpp/atl/reference/atl-project-wizard).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="9bb87-108">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="9bb87-108">In this section</span></span>

[<span data-ttu-id="9bb87-109">Windows Hizmeti Uygulamalarına Giriş</span><span class="sxs-lookup"><span data-stu-id="9bb87-109">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)

<span data-ttu-id="9bb87-110">Bir hizmet ve hizmet uygulamaları diğer ortak proje türlerinden farklılıklar ömrünü Windows hizmet uygulamaları, genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="9bb87-110">Provides an overview of Windows service applications, the lifetime of a service, and how service applications differ from other common project types.</span></span>

[<span data-ttu-id="9bb87-111">İzlenecek Yol: Bileşen Tasarımcısında Windows Hizmeti Uygulaması Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9bb87-111">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)

<span data-ttu-id="9bb87-112">Visual Basic ve Visual C# içinde bir hizmet oluşturma örneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="9bb87-112">Provides an example of creating a service in Visual Basic and Visual C#.</span></span>

[<span data-ttu-id="9bb87-113">Hizmet Uygulaması Programlama Mimarisi</span><span class="sxs-lookup"><span data-stu-id="9bb87-113">Service Application Programming Architecture</span></span>](../../../docs/framework/windows-services/service-application-programming-architecture.md)

<span data-ttu-id="9bb87-114">Hizmet programlamada kullanılan dil öğelerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="9bb87-114">Explains the language elements used in service programming.</span></span>

[<span data-ttu-id="9bb87-115">Nasıl Yapılır: Windows Hizmetleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9bb87-115">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)

<span data-ttu-id="9bb87-116">Oluşturma ve Windows services Windows hizmeti proje şablonunu kullanarak yapılandırma işlemi açıklanır.</span><span class="sxs-lookup"><span data-stu-id="9bb87-116">Describes the process of creating and configuring Windows services using the Windows service project template.</span></span>

## <a name="related-sections"></a><span data-ttu-id="9bb87-117">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="9bb87-117">Related sections</span></span>

<span data-ttu-id="9bb87-118"><xref:System.ServiceProcess.ServiceBase> -Ana özelliklerini açıklar <xref:System.ServiceProcess.ServiceBase> hizmetleri oluşturmak için kullanılan sınıf.</span><span class="sxs-lookup"><span data-stu-id="9bb87-118"><xref:System.ServiceProcess.ServiceBase> - Describes the major features of the <xref:System.ServiceProcess.ServiceBase> class, which is used to create services.</span></span>

<span data-ttu-id="9bb87-119"><xref:System.ServiceProcess.ServiceProcessInstaller> -Özelliklerini açıklar <xref:System.ServiceProcess.ServiceProcessInstaller> ile birlikte kullanılan sınıfı <xref:System.ServiceProcess.ServiceInstaller> yüklemek ve hizmetlerinizi kaldırmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="9bb87-119"><xref:System.ServiceProcess.ServiceProcessInstaller> - Describes the features of the <xref:System.ServiceProcess.ServiceProcessInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceInstaller> class to install and uninstall your services.</span></span>

<span data-ttu-id="9bb87-120"><xref:System.ServiceProcess.ServiceInstaller> -Özelliklerini açıklar <xref:System.ServiceProcess.ServiceInstaller> ile birlikte kullanılan sınıfı <xref:System.ServiceProcess.ServiceProcessInstaller> yüklemek ve hizmetinizi kaldırmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="9bb87-120"><xref:System.ServiceProcess.ServiceInstaller> - Describes the features of the <xref:System.ServiceProcess.ServiceInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceProcessInstaller> class to install and uninstall your service.</span></span>

<span data-ttu-id="9bb87-121">[Şablonlardan proje oluşturma](https://msdn.microsoft.com/library/7c36d86a-6b79-4480-8228-0f925f1204b2) -projeleri açıklar ve bunlar arasında seçim yapma Bu bölümde kullanılan türleri.</span><span class="sxs-lookup"><span data-stu-id="9bb87-121">[Create Projects from Templates](https://msdn.microsoft.com/library/7c36d86a-6b79-4480-8228-0f925f1204b2) -  Describes the projects types used in this chapter and how to choose between them.</span></span>
