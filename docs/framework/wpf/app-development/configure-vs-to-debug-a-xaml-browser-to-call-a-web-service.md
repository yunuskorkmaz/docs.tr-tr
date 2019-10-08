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
ms.openlocfilehash: 8ec278f2bc66d9b40786123af684f6468b6a9d83
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005677"
---
# <a name="how-to-configure-visual-studio-to-debug-a-xaml-browser-application-to-call-a-web-service"></a><span data-ttu-id="ada59-102">Nasıl yapılır: Web Hizmeti Çağırmak Amacıyla XAML Tarayıcı Uygulamasında Hata Ayıklamak için Visual Studio'yu Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ada59-102">How to: Configure Visual Studio to Debug a XAML Browser Application to Call a Web Service</span></span>
[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]<span data-ttu-id="ada59-103">, Internet bölgesi izin kümesiyle kısıtlanmış bir kısmi güven güvenlik alanı içinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="ada59-103">run within a partial-trust security sandbox that is restricted to the Internet zone set of permissions.</span></span> <span data-ttu-id="ada59-104">Bu izin kümesi, Web hizmeti çağrılarını yalnızca [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] uygulamasının kaynak sitesinde bulunan Web hizmetlerine kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="ada59-104">This permission set restricts Web service calls to only Web services that are located at the [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] application's site of origin.</span></span> <span data-ttu-id="ada59-105">@No__t-0 ' dan Visual Studio 2005 hatası ayıklandığında, başvurduğu Web hizmetiyle aynı kaynak sitesine sahip olarak değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="ada59-105">When an [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] is debugged from Visual Studio 2005, though, it is not considered to have the same site of origin as the Web service it references.</span></span> <span data-ttu-id="ada59-106">Bu, [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Web hizmetini çağırmaya çalıştığında güvenlik özel durumlarının oluşturulmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="ada59-106">This causes security exceptions to be raised when the [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] attempts to call the Web service.</span></span> <span data-ttu-id="ada59-107">Ancak, bir Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] projesi, hata ayıklama sırasında çağırdığı Web hizmeti ile aynı kaynak sitesine sahip olmayı taklit etmek için yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="ada59-107">However, a Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] project can be configured to simulate having the same site of origin as the Web service it calls while debugging.</span></span> <span data-ttu-id="ada59-108">Bu, [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] ' ın güvenlik özel durumlarına neden olmadan Web hizmetini güvenle çağırmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="ada59-108">This allows the [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] to safely call the Web service without causing security exceptions.</span></span>

## <a name="configuring-visual-studio"></a><span data-ttu-id="ada59-109">Visual Studio’yu yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ada59-109">Configuring Visual Studio</span></span>
 <span data-ttu-id="ada59-110">Visual Studio 2005 ' i bir Web hizmeti çağıran @no__t hata ayıklaması yapmak üzere yapılandırmak için:</span><span class="sxs-lookup"><span data-stu-id="ada59-110">To configure Visual Studio 2005 to debug an [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] that calls a Web service:</span></span>

1. <span data-ttu-id="ada59-111">**Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="ada59-111">With a project selected in **Solution Explorer**, on the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="ada59-112">**Proje tasarımcısında** **Hata Ayıkla** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="ada59-112">In the **Project Designer**, click the **Debug** tab.</span></span>

3. <span data-ttu-id="ada59-113">**Başlat eylemi** bölümünde **dış program Başlat** ' ı seçin ve aşağıdakileri girin:</span><span class="sxs-lookup"><span data-stu-id="ada59-113">In the **Start Action** section, select **Start external program** and enter the following:</span></span>

     `C:\WINDOWS\System32\PresentationHost.exe`

4. <span data-ttu-id="ada59-114">**Başlangıç seçenekleri** bölümünde **komut satırı bağımsız değişkenleri** metin kutusuna aşağıdakini girin:</span><span class="sxs-lookup"><span data-stu-id="ada59-114">In the **Start Options** section, enter the following into the **Command line arguments** text box:</span></span>

     <span data-ttu-id="ada59-115">`-debug`  *dosya adı*</span><span class="sxs-lookup"><span data-stu-id="ada59-115">`-debug`  *filename*</span></span>

     <span data-ttu-id="ada59-116">**-Debug** parametresinin *filename* değeri. XBAP dosya adıdır; Örneğin:</span><span class="sxs-lookup"><span data-stu-id="ada59-116">The *filename* value for the **-debug** parameter is the .xbap filename; for example:</span></span>

     `-debug c:\example.xbap`

> [!NOTE]
> <span data-ttu-id="ada59-117">Bu, Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] proje şablonuyla oluşturulan çözümlerin varsayılan yapılandırmadır.</span><span class="sxs-lookup"><span data-stu-id="ada59-117">This is the default configuration for solutions that are created with the Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] project template.</span></span>

1. <span data-ttu-id="ada59-118">**Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="ada59-118">With a project selected in **Solution Explorer**, on the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="ada59-119">**Proje tasarımcısında** **Hata Ayıkla** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="ada59-119">In the **Project Designer**, click the **Debug** tab.</span></span>

3. <span data-ttu-id="ada59-120">**Başlangıç seçenekleri** bölümünde **komut satırı bağımsız değişkenleri** metin kutusuna aşağıdaki komut satırı parametresini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="ada59-120">In the **Start Options** section, add the following command-line parameter to the **Command line arguments** text box:</span></span>

     <span data-ttu-id="ada59-121">`-debugSecurityZoneURL`  *URL 'si*</span><span class="sxs-lookup"><span data-stu-id="ada59-121">`-debugSecurityZoneURL`  *URL*</span></span>

     <span data-ttu-id="ada59-122">**-DebugSecurityZoneURL** parametresi için *URL* değeri, uygulamanızın kaynak sitesi olarak benzetimini yapmak istediğiniz konum için [!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)] ' dir.</span><span class="sxs-lookup"><span data-stu-id="ada59-122">The *URL* value for the **-debugSecurityZoneURL** parameter is the [!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)] for the location that you want to simulate as being the site of origin of your application.</span></span>

 <span data-ttu-id="ada59-123">Örnek olarak, aşağıdaki URL ile bir Web hizmeti kullanan [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] ' ı düşünün:</span><span class="sxs-lookup"><span data-stu-id="ada59-123">As an example, consider a [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] that uses a Web service with the following URL:</span></span>

 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`

 <span data-ttu-id="ada59-124">Bu Web hizmetinin kaynak URL 'SI sitesi:</span><span class="sxs-lookup"><span data-stu-id="ada59-124">The site of origin URL for this Web service is:</span></span>

 `http://services.msdn.microsoft.com`

 <span data-ttu-id="ada59-125">Sonuç olarak, tam **-DebugSecurityZoneURL** komut satırı parametresi ve değeri:</span><span class="sxs-lookup"><span data-stu-id="ada59-125">Consequently, the complete **-debugSecurityZoneURL** command-line parameter and value is:</span></span>

 `-debugSecurityZoneURL http://services.msdn.microsoft.com`

## <a name="see-also"></a><span data-ttu-id="ada59-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ada59-126">See also</span></span>

- [<span data-ttu-id="ada59-127">WPF Konağı (PresentationHost.exe)</span><span class="sxs-lookup"><span data-stu-id="ada59-127">WPF Host (PresentationHost.exe)</span></span>](wpf-host-presentationhost-exe.md)
