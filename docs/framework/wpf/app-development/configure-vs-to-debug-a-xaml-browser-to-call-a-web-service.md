---
title: "Nasıl yapılır: Web Hizmeti Çağırmak Amacıyla XAML Tarayıcı Uygulamasında Hata Ayıklamak için Visual Studio'yu Yapılandırma"
ms.date: 03/30/2017
helpviewer_keywords:
- debugging XBAPs that call a Web service [WPF]
- debugging security exceptions for XBAPs [WPF]
- security exception for XBAPs [WPF], debugging
- configuring Visual Studio to debug XAML browser applications [WPF]
- configuring Visual Studio to debug XBAPs [WPF]
ms.assetid: fd1db082-a7bb-4c4b-9331-6ad74a0682d0
ms.openlocfilehash: dcaabf9ecd47bc88095e92aa8ed28ad5f13fd1dc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59314379"
---
# <a name="how-to-configure-visual-studio-to-debug-a-xaml-browser-application-to-call-a-web-service"></a><span data-ttu-id="e8fd6-102">Nasıl yapılır: Web Hizmeti Çağırmak Amacıyla XAML Tarayıcı Uygulamasında Hata Ayıklamak için Visual Studio'yu Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e8fd6-102">How to: Configure Visual Studio to Debug a XAML Browser Application to Call a Web Service</span></span>
[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] <span data-ttu-id="e8fd6-103">Internet bölgesi izinleri kümesi için kısıtlı bir kısmi güven güvenliği korumalı alan içinde çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e8fd6-103">run within a partial-trust security sandbox that is restricted to the Internet zone set of permissions.</span></span> <span data-ttu-id="e8fd6-104">Bu izin kümesi, Web hizmeti çağrıları yalnızca şu adreste bulunabilir Hizmetleri Web sınırlar [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] kaynak uygulamanın siteyi.</span><span class="sxs-lookup"><span data-stu-id="e8fd6-104">This permission set restricts Web service calls to only Web services that are located at the [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] application's site of origin.</span></span> <span data-ttu-id="e8fd6-105">Olduğunda bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] hataları ayıklanmakta Visual Studio 2005'ten yine de bu Web hizmeti olarak başvuruları aynı kaynak siteyi sahip olmadığı kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="e8fd6-105">When an [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] is debugged from Visual Studio 2005, though, it is not considered to have the same site of origin as the Web service it references.</span></span> <span data-ttu-id="e8fd6-106">Bu neden güvenlik özel durumlarını ne zaman yükseltilecek [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Web hizmetini çağırmak çalışır.</span><span class="sxs-lookup"><span data-stu-id="e8fd6-106">This causes security exceptions to be raised when the [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] attempts to call the Web service.</span></span> <span data-ttu-id="e8fd6-107">Ancak, bir Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] proje, aynı kaynak siteyi çağırdığı hata ayıklama sırasında Web hizmeti olarak olması benzetimini yapmak için yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="e8fd6-107">However, a Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] project can be configured to simulate having the same site of origin as the Web service it calls while debugging.</span></span> <span data-ttu-id="e8fd6-108">Böylece [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] güvenli bir şekilde güvenlik özel durumları neden olmadan Web hizmetini çağırmak için.</span><span class="sxs-lookup"><span data-stu-id="e8fd6-108">This allows the [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] to safely call the Web service without causing security exceptions.</span></span>

## <a name="configuring-visual-studio"></a><span data-ttu-id="e8fd6-109">Visual Studio’yu yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e8fd6-109">Configuring Visual Studio</span></span>
 <span data-ttu-id="e8fd6-110">Hata ayıklamak için Visual Studio 2005 yapılandırmak için bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] bir Web hizmeti çağırır:</span><span class="sxs-lookup"><span data-stu-id="e8fd6-110">To configure Visual Studio 2005 to debug an [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] that calls a Web service:</span></span>

1. <span data-ttu-id="e8fd6-111">Seçili bir projeyle **Çözüm Gezgini**, **proje** menüsünde tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="e8fd6-111">With a project selected in **Solution Explorer**, on the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="e8fd6-112">İçinde **Proje Tasarımcısı**, tıklayın **hata ayıklama** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="e8fd6-112">In the **Project Designer**, click the **Debug** tab.</span></span>

3. <span data-ttu-id="e8fd6-113">İçinde **başlatma eylemi** bölümünden **harici program Başlat** ve şunu girin:</span><span class="sxs-lookup"><span data-stu-id="e8fd6-113">In the **Start Action** section, select **Start external program** and enter the following:</span></span>

     `C:\WINDOWS\System32\PresentationHost.exe`

4. <span data-ttu-id="e8fd6-114">İçinde **Başlat seçenekleri** bölümünde, aşağıdaki girin **komut satırı bağımsız değişkenleri** metin kutusunda:</span><span class="sxs-lookup"><span data-stu-id="e8fd6-114">In the **Start Options** section, enter the following into the **Command line arguments** text box:</span></span>

     <span data-ttu-id="e8fd6-115">`-debug`  *Dosya adı*</span><span class="sxs-lookup"><span data-stu-id="e8fd6-115">`-debug`  *filename*</span></span>

     <span data-ttu-id="e8fd6-116">*Filename* değerini **-hata ayıklama** parametredir .xbap dosya adı; örneğin:</span><span class="sxs-lookup"><span data-stu-id="e8fd6-116">The *filename* value for the **-debug** parameter is the .xbap filename; for example:</span></span>

     `-debug c:\example.xbap`

> [!NOTE]
>  <span data-ttu-id="e8fd6-117">Bu Visual Studio 2005 ile oluşturulmuş çözümler için varsayılan yapılandırmadır [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] proje şablonu.</span><span class="sxs-lookup"><span data-stu-id="e8fd6-117">This is the default configuration for solutions that are created with the Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] project template.</span></span>

1. <span data-ttu-id="e8fd6-118">Seçili bir projeyle **Çözüm Gezgini**, **proje** menüsünde tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="e8fd6-118">With a project selected in **Solution Explorer**, on the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="e8fd6-119">İçinde **Proje Tasarımcısı**, tıklayın **hata ayıklama** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="e8fd6-119">In the **Project Designer**, click the **Debug** tab.</span></span>

3. <span data-ttu-id="e8fd6-120">İçinde **Başlat seçenekleri** bölümünde, eklemek için aşağıdaki komut satırı parametresini **komut satırı bağımsız değişkenleri** metin kutusunda:</span><span class="sxs-lookup"><span data-stu-id="e8fd6-120">In the **Start Options** section, add the following command-line parameter to the **Command line arguments** text box:</span></span>

     <span data-ttu-id="e8fd6-121">`-debugSecurityZoneURL`  *URL*</span><span class="sxs-lookup"><span data-stu-id="e8fd6-121">`-debugSecurityZoneURL`  *URL*</span></span>

     <span data-ttu-id="e8fd6-122">*URL* değerini **- debugSecurityZoneURL** parametresi [!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)] için uygulamanızın kaynak site olarak benzetimini yapmak istediğiniz konum.</span><span class="sxs-lookup"><span data-stu-id="e8fd6-122">The *URL* value for the **-debugSecurityZoneURL** parameter is the [!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)] for the location that you want to simulate as being the site of origin of your application.</span></span>

 <span data-ttu-id="e8fd6-123">Örneğin, göz önünde bulundurun bir [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] şunlarla birlikte bir Web hizmeti kullanan [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="e8fd6-123">As an example, consider a [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] that uses a Web service with the following [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]:</span></span>

 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`

 <span data-ttu-id="e8fd6-124">Kaynak siteyi [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] için bu Web hizmetidir:</span><span class="sxs-lookup"><span data-stu-id="e8fd6-124">The site of origin [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] for this Web service is:</span></span>

 `http://services.msdn.microsoft.com`

 <span data-ttu-id="e8fd6-125">Sonuç olarak, tam **- debugSecurityZoneURL** komut satırı parametresi ve değeri:</span><span class="sxs-lookup"><span data-stu-id="e8fd6-125">Consequently, the complete **-debugSecurityZoneURL** command-line parameter and value is:</span></span>

 `-debugSecurityZoneURL http://services.msdn.microsoft.com`

## <a name="see-also"></a><span data-ttu-id="e8fd6-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e8fd6-126">See also</span></span>

- [<span data-ttu-id="e8fd6-127">WPF Konağı (PresentationHost.exe)</span><span class="sxs-lookup"><span data-stu-id="e8fd6-127">WPF Host (PresentationHost.exe)</span></span>](wpf-host-presentationhost-exe.md)
