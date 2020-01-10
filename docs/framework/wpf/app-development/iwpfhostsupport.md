---
title: IWpfHostSupport
ms.date: 03/30/2017
helpviewer_keywords:
- IWpfHostSupport interface [WPF]
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
ms.openlocfilehash: 4855fae2954e5650d8c9bbb81153ebe64249a867
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740184"
---
# <a name="iwpfhostsupport"></a><span data-ttu-id="a6fc4-102">IWpfHostSupport</span><span class="sxs-lookup"><span data-stu-id="a6fc4-102">IWpfHostSupport</span></span>
<span data-ttu-id="a6fc4-103">PresentationHost. exe aracılığıyla [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] içeriği barındıran uygulamalar, ana bilgisayar ve PresentationHost. exe arasında bir tümleştirme noktası sağlamak için bu arabirimi uygular.</span><span class="sxs-lookup"><span data-stu-id="a6fc4-103">Applications that host [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] content via PresentationHost.exe implement this interface to provide a point of integration between the host and PresentationHost.exe.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6fc4-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a6fc4-104">Remarks</span></span>  
 <span data-ttu-id="a6fc4-105">Web tarayıcıları gibi Win32 uygulamaları, XAML tarayıcı uygulamaları (XBAP 'ler) ve gevşek XAML dahil olmak üzere WPF içeriği barındıralabilir.</span><span class="sxs-lookup"><span data-stu-id="a6fc4-105">Win32 applications such as Web browsers can host WPF content, including XAML browser applications (XBAPs) and loose XAML.</span></span> <span data-ttu-id="a6fc4-106">WPF içeriğini barındırmak için, Win32 uygulamaları [WebBrowser denetiminin](https://go.microsoft.com/fwlink/?LinkId=97911)bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a6fc4-106">To host WPF content, Win32 applications create an instance of the [WebBrowser control](https://go.microsoft.com/fwlink/?LinkId=97911).</span></span> <span data-ttu-id="a6fc4-107">WPF, barındırılan bir PresentationHost. exe ' nin bir örneğini oluşturur ve bu, [WebBrowser denetiminde](https://go.microsoft.com/fwlink/?LinkId=97911)görüntülenmek üzere konak IÇIN barındırılan WPF içeriğini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a6fc4-107">To be hosted, WPF creates an instance of PresentationHost.exe, which provides the hosted WPF content to the host for display in the [WebBrowser control](https://go.microsoft.com/fwlink/?LinkId=97911).</span></span>  
  
 <span data-ttu-id="a6fc4-108">`IWpfHostSupport` tarafından etkinleştirilen tümleştirme PresentationHost. exe ' ye izin veriyor:</span><span class="sxs-lookup"><span data-stu-id="a6fc4-108">The integration enabled by `IWpfHostSupport` allows PresentationHost.exe to:</span></span>  
  
- <span data-ttu-id="a6fc4-109">Ana bilgisayar uygulamasının ilgilendiği ham giriş cihazlarını (Insan arabirim aygıtları) bulun ve bunlarla kaydolun.</span><span class="sxs-lookup"><span data-stu-id="a6fc4-109">Discover and register with the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>  
  
- <span data-ttu-id="a6fc4-110">Kayıtlı ham giriş cihazlarından giriş iletileri alın ve uygun iletileri konak uygulamasına iletin.</span><span class="sxs-lookup"><span data-stu-id="a6fc4-110">Receive input messages from the registered raw input devices and forward appropriate messages to the host application.</span></span>  
  
- <span data-ttu-id="a6fc4-111">Özel ilerleme ve hata Kullanıcı arabirimleri için konak uygulamasını sorgulayın.</span><span class="sxs-lookup"><span data-stu-id="a6fc4-111">Query the host application for custom progress and error user interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a6fc4-112">Bu API yalnızca yerel istemci makinesinde kullanılmak üzere tasarlanmıştır ve desteklenir</span><span class="sxs-lookup"><span data-stu-id="a6fc4-112">This API is only intended and supported for use on the local client machine</span></span>  
  
## <a name="members"></a><span data-ttu-id="a6fc4-113">Üyeler</span><span class="sxs-lookup"><span data-stu-id="a6fc4-113">Members</span></span>  
  
|<span data-ttu-id="a6fc4-114">Üye</span><span class="sxs-lookup"><span data-stu-id="a6fc4-114">Member</span></span>|<span data-ttu-id="a6fc4-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a6fc4-115">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a6fc4-116">GetRawInputDevices</span><span class="sxs-lookup"><span data-stu-id="a6fc4-116">GetRawInputDevices</span></span>](getrawinputdevices.md)|<span data-ttu-id="a6fc4-117">PresentationHost. exe ' nin, ana bilgisayar uygulamasının ilgilendiği ham giriş cihazlarını (Insan arabirimi cihazları) bulmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a6fc4-117">Allows PresentationHost.exe to discover the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>|  
|[<span data-ttu-id="a6fc4-118">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="a6fc4-118">FilterInputMessage</span></span>](filterinputmessage.md)|<span data-ttu-id="a6fc4-119">E_NOTIMPL döndürülmediği takdirde PresentationHost. exe tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="a6fc4-119">Called by PresentationHost.exe whenever a message is received unless E_NOTIMPL is returned.</span></span>|  
|[<span data-ttu-id="a6fc4-120">GetCustomUI</span><span class="sxs-lookup"><span data-stu-id="a6fc4-120">GetCustomUI</span></span>](getcustomui.md)|<span data-ttu-id="a6fc4-121">Varsayılan olarak, PresentationHost. exe kendi dağıtım ilerlemesini ve WPF içeriği dağıtıldığında görüntülenen dağıtım hatası kullanıcı arabirimlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a6fc4-121">By default, PresentationHost.exe provides its own deployment progress and deployment error user interfaces that are displayed when WPF content is deployed.</span></span>|
