---
title: IWpfHostSupport
ms.date: 03/30/2017
helpviewer_keywords:
- IWpfHostSupport interface [WPF]
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
ms.openlocfilehash: 994e5146e9cf49a9b31396d0b51e7be83bbb3cfb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964779"
---
# <a name="iwpfhostsupport"></a><span data-ttu-id="85e6d-102">IWpfHostSupport</span><span class="sxs-lookup"><span data-stu-id="85e6d-102">IWpfHostSupport</span></span>
<span data-ttu-id="85e6d-103">PresentationHost. exe [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aracılığıyla içerik barındıran uygulamalar, ana bilgisayar ve PresentationHost. exe arasında bir tümleştirme noktası sağlamak için bu arabirimi uygular.</span><span class="sxs-lookup"><span data-stu-id="85e6d-103">Applications that host [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] content via PresentationHost.exe implement this interface to provide a point of integration between the host and PresentationHost.exe.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85e6d-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="85e6d-104">Remarks</span></span>  
 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]<span data-ttu-id="85e6d-105">Web tarayıcıları gibi uygulamalar, XAML dahil [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] ve gevşek XAML [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] dahil, içerik barındırabilirler.</span><span class="sxs-lookup"><span data-stu-id="85e6d-105">applications such as Web browsers can host [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] content, including [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] and loose XAML.</span></span> <span data-ttu-id="85e6d-106">İçerik barındırmak [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] için, [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] uygulamalar [WebBrowser denetiminin](https://go.microsoft.com/fwlink/?LinkId=97911)bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="85e6d-106">To host [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] content, [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] applications create an instance of the [WebBrowser control](https://go.microsoft.com/fwlink/?LinkId=97911).</span></span> <span data-ttu-id="85e6d-107">Barındırılmak üzere, [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] bir PresentationHost. exe ' nin bir örneğini oluşturur ve bu, [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] [WebBrowser denetiminde](https://go.microsoft.com/fwlink/?LinkId=97911)görüntülenmek üzere konak için barındırılan içeriği sağlar.</span><span class="sxs-lookup"><span data-stu-id="85e6d-107">To be hosted, [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] creates an instance of PresentationHost.exe, which provides the hosted [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] content to the host for display in the [WebBrowser control](https://go.microsoft.com/fwlink/?LinkId=97911).</span></span>  
  
 <span data-ttu-id="85e6d-108">Tarafından `IWpfHostSupport` etkinleştirilen tümleştirme PresentationHost. exe ' ye izin verir:</span><span class="sxs-lookup"><span data-stu-id="85e6d-108">The integration enabled by `IWpfHostSupport` allows PresentationHost.exe to:</span></span>  
  
- <span data-ttu-id="85e6d-109">Ana bilgisayar uygulamasının ilgilendiği ham giriş cihazlarını (Insan arabirim aygıtları) bulun ve bunlarla kaydolun.</span><span class="sxs-lookup"><span data-stu-id="85e6d-109">Discover and register with the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>  
  
- <span data-ttu-id="85e6d-110">Kayıtlı ham giriş cihazlarından giriş iletileri alın ve uygun iletileri konak uygulamasına iletin.</span><span class="sxs-lookup"><span data-stu-id="85e6d-110">Receive input messages from the registered raw input devices and forward appropriate messages to the host application.</span></span>  
  
- <span data-ttu-id="85e6d-111">Özel ilerleme ve hata Kullanıcı arabirimleri için konak uygulamasını sorgulayın.</span><span class="sxs-lookup"><span data-stu-id="85e6d-111">Query the host application for custom progress and error user interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="85e6d-112">Bu API yalnızca yerel istemci makinesinde kullanılmak üzere tasarlanmıştır ve desteklenir</span><span class="sxs-lookup"><span data-stu-id="85e6d-112">This API is only intended and supported for use on the local client machine</span></span>  
  
## <a name="members"></a><span data-ttu-id="85e6d-113">Üyeler</span><span class="sxs-lookup"><span data-stu-id="85e6d-113">Members</span></span>  
  
|<span data-ttu-id="85e6d-114">Üye</span><span class="sxs-lookup"><span data-stu-id="85e6d-114">Member</span></span>|<span data-ttu-id="85e6d-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="85e6d-115">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="85e6d-116">GetRawInputDevices</span><span class="sxs-lookup"><span data-stu-id="85e6d-116">GetRawInputDevices</span></span>](getrawinputdevices.md)|<span data-ttu-id="85e6d-117">PresentationHost. exe ' nin, ana bilgisayar uygulamasının ilgilendiği ham giriş cihazlarını (Insan arabirimi cihazları) bulmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="85e6d-117">Allows PresentationHost.exe to discover the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>|  
|[<span data-ttu-id="85e6d-118">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="85e6d-118">FilterInputMessage</span></span>](filterinputmessage.md)|<span data-ttu-id="85e6d-119">E_NOTIMPL döndürülmediği müddetçe PresentationHost. exe tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="85e6d-119">Called by PresentationHost.exe whenever a message is received unless E_NOTIMPL is returned.</span></span>|  
|[<span data-ttu-id="85e6d-120">GetCustomUI</span><span class="sxs-lookup"><span data-stu-id="85e6d-120">GetCustomUI</span></span>](getcustomui.md)|<span data-ttu-id="85e6d-121">Varsayılan olarak, PresentationHost. exe kendi dağıtım ilerlemesini ve WPF içeriği dağıtıldığında görüntülenen dağıtım hatası kullanıcı arabirimlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="85e6d-121">By default, PresentationHost.exe provides its own deployment progress and deployment error user interfaces that are displayed when WPF content is deployed.</span></span>|
