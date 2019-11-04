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
ms.openlocfilehash: d8cfae2fb47876d578c51e5f4acdfe0c31e752fe
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460906"
---
# <a name="how-to-configure-visual-studio-to-debug-a-xaml-browser-application-to-call-a-web-service"></a><span data-ttu-id="80ba4-102">Nasıl yapılır: Web Hizmeti Çağırmak Amacıyla XAML Tarayıcı Uygulamasında Hata Ayıklamak için Visual Studio'yu Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="80ba4-102">How to: Configure Visual Studio to Debug a XAML Browser Application to Call a Web Service</span></span>
<span data-ttu-id="80ba4-103">XAML tarayıcı uygulamaları (XBAP), Internet bölgesi izinleri kümesiyle kısıtlanmış bir kısmi güven güvenlik korumalı alanı içinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="80ba4-103">XAML browser applications (XBAPs) run within a partial-trust security sandbox that is restricted to the Internet zone set of permissions.</span></span> <span data-ttu-id="80ba4-104">Bu izin kümesi, Web hizmeti çağrılarını yalnızca XBAP uygulamasının kaynak sitesinde bulunan Web hizmetlerine kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="80ba4-104">This permission set restricts Web service calls to only Web services that are located at the XBAP application's site of origin.</span></span> <span data-ttu-id="80ba4-105">Visual Studio 2005 ' den bir XBAP hatası ayıklandığında, başvurduğu Web hizmetiyle aynı kaynak sitesine sahip olarak değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="80ba4-105">When an XBAP is debugged from Visual Studio 2005, though, it is not considered to have the same site of origin as the Web service it references.</span></span> <span data-ttu-id="80ba4-106">Bu, XBAP Web hizmetini çağırmayı denediğinde güvenlik özel durumlarının oluşturulmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="80ba4-106">This causes security exceptions to be raised when the XBAP attempts to call the Web service.</span></span> <span data-ttu-id="80ba4-107">Ancak, bir Visual Studio 2005 XAML tarayıcı uygulaması (WPF) projesi, hata ayıklama sırasında çağırdığı Web hizmeti ile aynı kaynak sitesine sahip olmayı taklit etmek üzere yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="80ba4-107">However, a Visual Studio 2005 XAML Browser Application (WPF) project can be configured to simulate having the same site of origin as the Web service it calls while debugging.</span></span> <span data-ttu-id="80ba4-108">Bu, XBAP 'nin güvenlik özel durumlarına neden olmadan Web hizmetini güvenle çağırmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="80ba4-108">This allows the XBAP to safely call the Web service without causing security exceptions.</span></span>

## <a name="configuring-visual-studio"></a><span data-ttu-id="80ba4-109">Visual Studio’yu yapılandırma</span><span class="sxs-lookup"><span data-stu-id="80ba4-109">Configuring Visual Studio</span></span>
 <span data-ttu-id="80ba4-110">Visual Studio 2005 ' i bir Web hizmeti çağıran bir XBAP hata ayıklaması için yapılandırmak için:</span><span class="sxs-lookup"><span data-stu-id="80ba4-110">To configure Visual Studio 2005 to debug an XBAP that calls a Web service:</span></span>

1. <span data-ttu-id="80ba4-111">**Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="80ba4-111">With a project selected in **Solution Explorer**, on the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="80ba4-112">**Proje tasarımcısında** **Hata Ayıkla** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="80ba4-112">In the **Project Designer**, click the **Debug** tab.</span></span>

3. <span data-ttu-id="80ba4-113">**Başlat eylemi** bölümünde **dış program Başlat** ' ı seçin ve aşağıdakileri girin:</span><span class="sxs-lookup"><span data-stu-id="80ba4-113">In the **Start Action** section, select **Start external program** and enter the following:</span></span>

     `C:\WINDOWS\System32\PresentationHost.exe`

4. <span data-ttu-id="80ba4-114">**Başlangıç seçenekleri** bölümünde **komut satırı bağımsız değişkenleri** metin kutusuna aşağıdakini girin:</span><span class="sxs-lookup"><span data-stu-id="80ba4-114">In the **Start Options** section, enter the following into the **Command line arguments** text box:</span></span>

     <span data-ttu-id="80ba4-115">`-debug`  *dosya adı*</span><span class="sxs-lookup"><span data-stu-id="80ba4-115">`-debug`  *filename*</span></span>

     <span data-ttu-id="80ba4-116">**-Debug** parametresinin *filename* değeri. XBAP dosya adıdır; Örneğin:</span><span class="sxs-lookup"><span data-stu-id="80ba4-116">The *filename* value for the **-debug** parameter is the .xbap filename; for example:</span></span>

     `-debug c:\example.xbap`

> [!NOTE]
> <span data-ttu-id="80ba4-117">Bu, Visual Studio 2005 XAML tarayıcı uygulaması (WPF) proje şablonuyla oluşturulan çözümlerin varsayılan yapılandırmadır.</span><span class="sxs-lookup"><span data-stu-id="80ba4-117">This is the default configuration for solutions that are created with the Visual Studio 2005 XAML Browser Application (WPF) project template.</span></span>

1. <span data-ttu-id="80ba4-118">**Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="80ba4-118">With a project selected in **Solution Explorer**, on the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="80ba4-119">**Proje tasarımcısında** **Hata Ayıkla** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="80ba4-119">In the **Project Designer**, click the **Debug** tab.</span></span>

3. <span data-ttu-id="80ba4-120">**Başlangıç seçenekleri** bölümünde **komut satırı bağımsız değişkenleri** metin kutusuna aşağıdaki komut satırı parametresini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="80ba4-120">In the **Start Options** section, add the following command-line parameter to the **Command line arguments** text box:</span></span>

     <span data-ttu-id="80ba4-121">`-debugSecurityZoneURL`  *URL 'si*</span><span class="sxs-lookup"><span data-stu-id="80ba4-121">`-debugSecurityZoneURL`  *URL*</span></span>

     <span data-ttu-id="80ba4-122">**-DebugSecurityZoneURL** parametresi için *URL* değeri, uygulamanızın kaynak sitesi olarak benzetimini yapmak istediğiniz konumun URL 'sidir.</span><span class="sxs-lookup"><span data-stu-id="80ba4-122">The *URL* value for the **-debugSecurityZoneURL** parameter is the URL for the location that you want to simulate as being the site of origin of your application.</span></span>

 <span data-ttu-id="80ba4-123">Örnek olarak, aşağıdaki URL ile bir Web hizmeti kullanan bir XAML tarayıcı uygulaması (XBAP) göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="80ba4-123">As an example, consider a XAML browser application (XBAP) that uses a Web service with the following URL:</span></span>

 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`

 <span data-ttu-id="80ba4-124">Bu Web hizmetinin kaynak URL 'SI sitesi:</span><span class="sxs-lookup"><span data-stu-id="80ba4-124">The site of origin URL for this Web service is:</span></span>

 `http://services.msdn.microsoft.com`

 <span data-ttu-id="80ba4-125">Sonuç olarak, tam **-DebugSecurityZoneURL** komut satırı parametresi ve değeri:</span><span class="sxs-lookup"><span data-stu-id="80ba4-125">Consequently, the complete **-debugSecurityZoneURL** command-line parameter and value is:</span></span>

 `-debugSecurityZoneURL http://services.msdn.microsoft.com`

## <a name="see-also"></a><span data-ttu-id="80ba4-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80ba4-126">See also</span></span>

- [<span data-ttu-id="80ba4-127">WPF Konağı (PresentationHost.exe)</span><span class="sxs-lookup"><span data-stu-id="80ba4-127">WPF Host (PresentationHost.exe)</span></span>](wpf-host-presentationhost-exe.md)
