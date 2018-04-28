---
title: PrintForm bileşeni (Visual Basic) başvuruda bulunan uygulamaları dağıtma
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- PrintForm component [Visual Basic], deploying
ms.assetid: b595ea44-a712-4625-a761-190c64f59bbe
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f49a5ef8dd4e36c9ab055ca01dc25ed05b083349
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="deploying-applications-that-reference-the-printform-component-visual-basic"></a><span data-ttu-id="9385a-102">PrintForm bileşeni (Visual Basic) başvuruda bulunan uygulamaları dağıtma</span><span class="sxs-lookup"><span data-stu-id="9385a-102">Deploying applications that reference the PrintForm component (Visual Basic)</span></span>
<span data-ttu-id="9385a-103">Başvuruda bulunan bir uygulamayı dağıtmak istiyorsanız, <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> bileşen, bileşen hedef bilgisayarda yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9385a-103">If you want to deploy an application that references the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component, the component must be installed on the destination computer.</span></span>  
  
 <span data-ttu-id="9385a-104">PowerPack denetimleri artık Visual Studio'ya dahil olan, ancak bunları indirebilirsiniz [Yükleme Merkezi'nden](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span><span class="sxs-lookup"><span data-stu-id="9385a-104">The PowerPack controls are no longer included in Visual Studio, but you can download them from the [Download Center](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span></span>  
  
## <a name="installing-the-printform-as-a-prerequisite"></a><span data-ttu-id="9385a-105">PrintForm bir önkoşul olarak yükleme</span><span class="sxs-lookup"><span data-stu-id="9385a-105">Installing the PrintForm as a prerequisite</span></span>  
 <span data-ttu-id="9385a-106">Bir uygulamayı başarıyla dağıtmak için uygulama tarafından başvurulan tüm bileşenleri dağıtmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9385a-106">To successfully deploy an application, you must also deploy all components that are referenced by the application.</span></span> <span data-ttu-id="9385a-107">Önkoşul bileşenlerini yükleme işlemi olarak bilinen *önyükleme*.</span><span class="sxs-lookup"><span data-stu-id="9385a-107">The process of installing prerequisite components is known as *bootstrapping*.</span></span>  
  
 <span data-ttu-id="9385a-108">Zaman <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> bileşeni geliştirme bilgisayarınızda yüklü, Microsoft Visual Basic Power Packs önyükleyici paketi Visual Studio önyükleyici dizinine eklenir.</span><span class="sxs-lookup"><span data-stu-id="9385a-108">When the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is installed on your development computer, a Microsoft Visual Basic Power Packs bootstrapper package is added to the Visual Studio bootstrapper directory.</span></span> <span data-ttu-id="9385a-109">Bu paket sonra da önkoşulları ekleme yordamlarına izlediğinizde kullanılabilir [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] veya Windows Installer dağıtımı.</span><span class="sxs-lookup"><span data-stu-id="9385a-109">This package is then available when you follow the procedures for adding prerequisites for either [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] or Windows Installer deployment.</span></span>  
  
 <span data-ttu-id="9385a-110">Varsayılan olarak, yükleme paketi aynı konumda önyükleme bileşenleri dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="9385a-110">By default, bootstrapped components are deployed from the same location as the installation package.</span></span> <span data-ttu-id="9385a-111">Alternatif olarak, kullanıcılar bunları gerektiği şekilde yükleyebileceğiniz bir URL veya dosya paylaşımı konumu bileşenlerini dağıtmayı seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9385a-111">Alternatively, you can choose to deploy the components from a URL or file share location from which users can download them as necessary.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9385a-112">Önyükleme bileşenlerini yüklemek için kullanıcının bilgisayarda yönetici veya benzer kullanıcı izinlerine gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="9385a-112">To install bootstrapped components, the user might need administrative or similar user permissions on the computer.</span></span> <span data-ttu-id="9385a-113">İçin [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] uygulamalar, yani kullanıcı uygulama tarafından belirtilen güvenlik düzeyi bağımsız olarak uygulamayı yüklemek için yönetici izinleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="9385a-113">For [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] applications, this means that the user will need administrative permissions to install the application, regardless of the security level specified by the application.</span></span> <span data-ttu-id="9385a-114">Uygulama yüklendikten sonra kullanıcı uygulamayı yönetim izinleri olmadan çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9385a-114">After the application is installed, the user can run the application without administrative permissions.</span></span>  
  
 <span data-ttu-id="9385a-115">Yükleme sırasında kullanıcıların yüklemeniz istenir <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> hedef bilgisayarda mevcut değilse bileşeni.</span><span class="sxs-lookup"><span data-stu-id="9385a-115">During installation, users will be prompted to install the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component if it is not present on the destination computer.</span></span>  
  
 <span data-ttu-id="9385a-116">Önyükleme alternatif olarak, önceden dağıtabileceğiniz <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Microsoft Systems Management Server gibi bir elektronik yazılım dağıtım sistemi kullanarak bileşen.</span><span class="sxs-lookup"><span data-stu-id="9385a-116">As an alternative to bootstrapping, you can pre-deploy the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component by using an electronic software distribution system like Microsoft Systems Management Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9385a-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9385a-117">See also</span></span>  
 [<span data-ttu-id="9385a-118">Nasıl yapılır: ClickOnce Uygulamasıyla Önkoşulları Yükleme</span><span class="sxs-lookup"><span data-stu-id="9385a-118">How to: Install Prerequisites with a ClickOnce Application</span></span>](/visualstudio/deployment/how-to-install-prerequisites-with-a-clickonce-application)  
 [<span data-ttu-id="9385a-119">PrintForm Bileşeni</span><span class="sxs-lookup"><span data-stu-id="9385a-119">PrintForm Component</span></span>](../../../visual-basic/developing-apps/printing/printform-component.md)
