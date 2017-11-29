---
title: "Nasıl yapılır: Web Hizmeti Çağırmak Amacıyla XAML Tarayıcı Uygulamasında Hata Ayıklamak için Visual Studio'yu Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging XBAPs that call a Web service [WPF]
- debugging security exceptions for XBAPs [WPF]
- security exception for XBAPs [WPF], debugging
- configuring Visual Studio to debug XAML browser applications [WPF]
- configuring Visual Studio to debug XBAPs [WPF]
ms.assetid: fd1db082-a7bb-4c4b-9331-6ad74a0682d0
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5db89cf6220f086d2d71b99f3e6440e584d6a5d7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-configure-visual-studio-to-debug-a-xaml-browser-application-to-call-a-web-service"></a><span data-ttu-id="ff354-102">Nasıl yapılır: Web Hizmeti Çağırmak Amacıyla XAML Tarayıcı Uygulamasında Hata Ayıklamak için Visual Studio'yu Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ff354-102">How to: Configure Visual Studio to Debug a XAML Browser Application to Call a Web Service</span></span>
[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]<span data-ttu-id="ff354-103">Internet bölgesi izinleri kümesi için kısıtlı bir kısmi güven güvenlik sandbox içinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="ff354-103"> run within a partial-trust security sandbox that is restricted to the Internet zone set of permissions.</span></span> <span data-ttu-id="ff354-104">Bu izin kümesi yalnızca Web konumunda yer Hizmetleri için Web hizmeti çağrıları kısıtlayan [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] kaynak uygulamanın site.</span><span class="sxs-lookup"><span data-stu-id="ff354-104">This permission set restricts Web service calls to only Web services that are located at the [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] application's site of origin.</span></span> <span data-ttu-id="ff354-105">Zaman bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] gelen hata ayıklaması [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)]Web hizmeti olarak başvuruları aynı kaynak sitesi için dikkate alınmaz ancak.</span><span class="sxs-lookup"><span data-stu-id="ff354-105">When an [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] is debugged from [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)], though, it is not considered to have the same site of origin as the Web service it references.</span></span> <span data-ttu-id="ff354-106">Ne zaman oluşturulması için bu nedenler güvenlik özel durumları [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Web hizmetini çağırmak çalışır.</span><span class="sxs-lookup"><span data-stu-id="ff354-106">This causes security exceptions to be raised when the [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] attempts to call the Web service.</span></span> <span data-ttu-id="ff354-107">Ancak, bir [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] proje, kaynak çağırdığı hata ayıklama sırasında Web hizmeti ile aynı sitede olması benzetimini yapmak için yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="ff354-107">However, a [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] project can be configured to simulate having the same site of origin as the Web service it calls while debugging.</span></span> <span data-ttu-id="ff354-108">Böylece [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] güvenlik özel durumları neden olmadan güvenli bir şekilde Web hizmetini çağırmak için.</span><span class="sxs-lookup"><span data-stu-id="ff354-108">This allows the [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] to safely call the Web service without causing security exceptions.</span></span>  
  
## <a name="configuring-visual-studio"></a><span data-ttu-id="ff354-109">Visual Studio'yu yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ff354-109">Configuring Visual Studio</span></span>  
 <span data-ttu-id="ff354-110">Yapılandırmak için [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] hata ayıklamak için bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] bir Web hizmeti çağrıları:</span><span class="sxs-lookup"><span data-stu-id="ff354-110">To configure [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] to debug an [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] that calls a Web service:</span></span>  
  
1.  <span data-ttu-id="ff354-111">Seçili bir proje ile **Çözüm Gezgini**, **proje** menüsünde tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="ff354-111">With a project selected in **Solution Explorer**, on the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="ff354-112">İçinde **Proje Tasarımcısı**, tıklatın **hata ayıklama** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="ff354-112">In the **Project Designer**, click the **Debug** tab.</span></span>  
  
3.  <span data-ttu-id="ff354-113">İçinde **eylemi Başlat** bölümünde, select **başlangıç dış program** ve aşağıdakileri girin:</span><span class="sxs-lookup"><span data-stu-id="ff354-113">In the **Start Action** section, select **Start external program** and enter the following:</span></span>  
  
     `C:\WINDOWS\System32\PresentationHost.exe`  
  
4.  <span data-ttu-id="ff354-114">İçinde **başlangıç seçenekleri** bölümünde, aşağıdaki girin **komut satırı bağımsız değişkenleri** metin kutusu:</span><span class="sxs-lookup"><span data-stu-id="ff354-114">In the **Start Options** section, enter the following into the **Command line arguments** text box:</span></span>  
  
     <span data-ttu-id="ff354-115">`-debug`  *Dosya adı*</span><span class="sxs-lookup"><span data-stu-id="ff354-115">`-debug`  *filename*</span></span>  
  
     <span data-ttu-id="ff354-116">*Filename* değerini **-debug** parametredir .xbap filename; örneğin:</span><span class="sxs-lookup"><span data-stu-id="ff354-116">The *filename* value for the **-debug** parameter is the .xbap filename; for example:</span></span>  
  
     `-debug c:\example.xbap`  
  
> [!NOTE]
>  <span data-ttu-id="ff354-117">İle oluşturulan çözümleri için varsayılan yapılandırma budur [!INCLUDE[TLA2#tla_visualstu2005](../../../../includes/tla2sharptla-visualstu2005-md.md)] [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] proje şablonu.</span><span class="sxs-lookup"><span data-stu-id="ff354-117">This is the default configuration for solutions that are created with the [!INCLUDE[TLA2#tla_visualstu2005](../../../../includes/tla2sharptla-visualstu2005-md.md)] [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] project template.</span></span>  
  
1.  <span data-ttu-id="ff354-118">Seçili bir proje ile **Çözüm Gezgini**, **proje** menüsünde tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="ff354-118">With a project selected in **Solution Explorer**, on the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="ff354-119">İçinde **Proje Tasarımcısı**, tıklatın **hata ayıklama** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="ff354-119">In the **Project Designer**, click the **Debug** tab.</span></span>  
  
3.  <span data-ttu-id="ff354-120">İçinde **başlangıç seçenekleri** bölümünde, aşağıdaki komut satırı parametresini ekleyin **komut satırı bağımsız değişkenleri** metin kutusu:</span><span class="sxs-lookup"><span data-stu-id="ff354-120">In the **Start Options** section, add the following command-line parameter to the **Command line arguments** text box:</span></span>  
  
     <span data-ttu-id="ff354-121">`-debugSecurityZoneURL`  *URL*</span><span class="sxs-lookup"><span data-stu-id="ff354-121">`-debugSecurityZoneURL`  *URL*</span></span>  
  
     <span data-ttu-id="ff354-122">*URL* değerini **- debugSecurityZoneURL** parametresi [!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)] , uygulamanızın kaynak site olarak benzetimini yapmak istediğiniz konum.</span><span class="sxs-lookup"><span data-stu-id="ff354-122">The *URL* value for the **-debugSecurityZoneURL** parameter is the [!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)] for the location that you want to simulate as being the site of origin of your application.</span></span>  
  
 <span data-ttu-id="ff354-123">Örnek olarak, göz önünde bulundurun bir [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] ile aşağıdakileri bir Web hizmeti kullanan [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="ff354-123">As an example, consider a [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] that uses a Web service with the following [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]:</span></span>  
  
 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`  
  
 <span data-ttu-id="ff354-124">Kaynak sitesi [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] için bu Web hizmetidir:</span><span class="sxs-lookup"><span data-stu-id="ff354-124">The site of origin [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] for this Web service is:</span></span>  
  
 `http://services.msdn.microsoft.com`  
  
 <span data-ttu-id="ff354-125">Sonuç olarak, tam **- debugSecurityZoneURL** komut satırı parametresi ve değeri:</span><span class="sxs-lookup"><span data-stu-id="ff354-125">Consequently, the complete **-debugSecurityZoneURL** command-line parameter and value is:</span></span>  
  
 `-debugSecurityZoneURL http://services.msdn.microsoft.com`  
  
## <a name="see-also"></a><span data-ttu-id="ff354-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ff354-126">See Also</span></span>  
 [<span data-ttu-id="ff354-127">WPF Konağı (PresentationHost.exe)</span><span class="sxs-lookup"><span data-stu-id="ff354-127">WPF Host (PresentationHost.exe)</span></span>](../../../../docs/framework/wpf/app-development/wpf-host-presentationhost-exe.md)
