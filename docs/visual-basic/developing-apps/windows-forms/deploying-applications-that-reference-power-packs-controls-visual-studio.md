---
title: "(Visual Studio) Power Packs denetimlerine başvuruda bulunan uygulamaları dağıtma"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Power Packs, deploying
ms.assetid: f2230f53-a745-4731-89e6-033943faa209
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2a9562acf05cd27eed7bc1ad963845af9a7ca5f9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="deploying-applications-that-reference-power-packs-controls-visual-studio"></a><span data-ttu-id="0fc2b-102">(Visual Studio) Power Packs denetimlerine başvuruda bulunan uygulamaları dağıtma</span><span class="sxs-lookup"><span data-stu-id="0fc2b-102">Deploying applications that reference Power Packs controls (Visual Studio)</span></span>
<span data-ttu-id="0fc2b-103">Power Packs denetimlerine başvuruda bulunan bir uygulamayı dağıtmak istiyorsanız (<xref:Microsoft.VisualBasic.PowerPacks.LineShape>, <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>, <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>, veya <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>), denetimler hedef bilgisayarda yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0fc2b-103">If you want to deploy an application that references the Power Packs controls (<xref:Microsoft.VisualBasic.PowerPacks.LineShape>, <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>, <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>, or <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>), the controls must be installed on the destination computer.</span></span>  
  
## <a name="installing-the-power-packs-controls-as-a-prerequisite"></a><span data-ttu-id="0fc2b-104">Power Packs denetimlerine bir önkoşul olarak yükleme</span><span class="sxs-lookup"><span data-stu-id="0fc2b-104">Installing the Power Packs controls as a prerequisite</span></span>  
 <span data-ttu-id="0fc2b-105">Bir uygulamayı başarıyla dağıtmak için uygulama tarafından başvurulan tüm bileşenleri dağıtmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0fc2b-105">To successfully deploy an application, you must also deploy all components that are referenced by the application.</span></span> <span data-ttu-id="0fc2b-106">Önkoşul bileşenlerini yükleme işlemi olarak bilinen *önyükleme*.</span><span class="sxs-lookup"><span data-stu-id="0fc2b-106">The process of installing prerequisite components is known as *bootstrapping*.</span></span>  
  
 <span data-ttu-id="0fc2b-107">Zaman [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] önyükleyici paketi eklenir Power Packs, geliştirme bilgisayarınızda yüklü [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] önyükleyici dizini.</span><span class="sxs-lookup"><span data-stu-id="0fc2b-107">When [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] is installed on your development computer, a Power Packs bootstrapper package is added to the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] bootstrapper directory.</span></span> <span data-ttu-id="0fc2b-108">Bu paket sonra da önkoşulları ekleme yordamlarına izlediğinizde kullanılabilir [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] veya Windows Installer dağıtımı.</span><span class="sxs-lookup"><span data-stu-id="0fc2b-108">This package is then available when you follow the procedures for adding prerequisites for either [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] or Windows Installer deployment.</span></span>  
  
 <span data-ttu-id="0fc2b-109">Varsayılan olarak, yükleme paketi aynı konumda önyükleme bileşenleri dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="0fc2b-109">By default, bootstrapped components are deployed from the same location as the installation package.</span></span> <span data-ttu-id="0fc2b-110">Alternatif olarak, kullanıcılar bunları gerektiği şekilde yükleyebileceğiniz bir URL veya dosya paylaşımı konumu bileşenlerini dağıtmayı seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0fc2b-110">Alternatively, you can choose to deploy the components from a URL or file share location from which users can download them as necessary.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0fc2b-111">Önyükleme bileşenlerini yüklemek için kullanıcının bilgisayarda yönetici veya benzer kullanıcı izinlerine gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="0fc2b-111">To install bootstrapped components, the user might need administrative or similar user permissions on the computer.</span></span> <span data-ttu-id="0fc2b-112">İçin [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] uygulamalar, yani kullanıcı uygulama tarafından belirtilen güvenlik düzeyi bağımsız olarak uygulamayı yüklemek için yönetici izinleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="0fc2b-112">For [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] applications, this means that the user will need administrative permissions to install the application, regardless of the security level specified by the application.</span></span> <span data-ttu-id="0fc2b-113">Uygulama yüklendikten sonra kullanıcı uygulamayı yönetim izinleri olmadan çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0fc2b-113">After the application is installed, the user can run the application without administrative permissions.</span></span>  
  
 <span data-ttu-id="0fc2b-114">Yükleme sırasında bunlar hedef bilgisayarda mevcut değilse Power Packs denetimlerine yüklemek için kullanıcılara sorulur.</span><span class="sxs-lookup"><span data-stu-id="0fc2b-114">During installation, users will be prompted to install the Power Packs controls if they are not present on the destination computer.</span></span>  
  
 <span data-ttu-id="0fc2b-115">Önyükleme alternatif olarak, Power Packs denetimlerine Microsoft Systems Management Server gibi bir elektronik yazılım dağıtım sistemi kullanarak önceden dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0fc2b-115">As an alternative to bootstrapping, you can pre-deploy the Power Packs controls by using an electronic software distribution system such as Microsoft Systems Management Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fc2b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0fc2b-116">See also</span></span>  
 [<span data-ttu-id="0fc2b-117">Nasıl yapılır: ClickOnce uygulamasıyla Önkoşulları Yükleme</span><span class="sxs-lookup"><span data-stu-id="0fc2b-117">How to: Install Prerequisites with a ClickOnce Application</span></span>](/visualstudio/deployment/how-to-install-prerequisites-with-a-clickonce-application)  
 [<span data-ttu-id="0fc2b-118">Visual Basic Power Packs denetimleri</span><span class="sxs-lookup"><span data-stu-id="0fc2b-118">Visual Basic Power Packs Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)
