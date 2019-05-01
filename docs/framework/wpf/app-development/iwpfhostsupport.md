---
title: IWpfHostSupport
ms.date: 03/30/2017
helpviewer_keywords:
- IWpfHostSupport interface [WPF]
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
ms.openlocfilehash: 074167111b78edc517dda019465260d0acd54737
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62006700"
---
# <a name="iwpfhostsupport"></a><span data-ttu-id="e20ec-102">IWpfHostSupport</span><span class="sxs-lookup"><span data-stu-id="e20ec-102">IWpfHostSupport</span></span>
<span data-ttu-id="e20ec-103">Barındıran uygulamalar [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] PresentationHost.exe üzerinden içerik PresentationHost.exe ve konak arasında tümleştirme noktası sağlamak için bu arabirimi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="e20ec-103">Applications that host [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] content via PresentationHost.exe implement this interface to provide a point of integration between the host and PresentationHost.exe.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e20ec-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e20ec-104">Remarks</span></span>  
 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] <span data-ttu-id="e20ec-105">Web tarayıcıları gibi uygulamaları barındırabilir [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] dahil olmak üzere içerik [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] ve XAML kaybedilir.</span><span class="sxs-lookup"><span data-stu-id="e20ec-105">applications such as Web browsers can host [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] content, including [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] and loose XAML.</span></span> <span data-ttu-id="e20ec-106">Ana bilgisayara [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] içerik [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] uygulamaları oluşturma örneği [WebBrowser denetimi](https://go.microsoft.com/fwlink/?LinkId=97911).</span><span class="sxs-lookup"><span data-stu-id="e20ec-106">To host [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] content, [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] applications create an instance of the [WebBrowser control](https://go.microsoft.com/fwlink/?LinkId=97911).</span></span> <span data-ttu-id="e20ec-107">Barındırılması için [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] barındırılan sağlayan PresentationHost.exe örneği oluşturur [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] görüntülemek için ana içerik [WebBrowser denetimi](https://go.microsoft.com/fwlink/?LinkId=97911).</span><span class="sxs-lookup"><span data-stu-id="e20ec-107">To be hosted, [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] creates an instance of PresentationHost.exe, which provides the hosted [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] content to the host for display in the [WebBrowser control](https://go.microsoft.com/fwlink/?LinkId=97911).</span></span>  
  
 <span data-ttu-id="e20ec-108">Tarafından etkinleştirilen tümleştirme `IWpfHostSupport` için PresentationHost.exe sağlar:</span><span class="sxs-lookup"><span data-stu-id="e20ec-108">The integration enabled by `IWpfHostSupport` allows PresentationHost.exe to:</span></span>  
  
- <span data-ttu-id="e20ec-109">Bul ve ana bilgisayar uygulaması, ilgileniyor ham giriş cihazları (İnsan Arabirimi cihazlar) ile kaydedin.</span><span class="sxs-lookup"><span data-stu-id="e20ec-109">Discover and register with the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>  
  
- <span data-ttu-id="e20ec-110">Giriş iletileri ham giriş cihazlar kayıtlı ve uygun iletileri yönlendirmek için ana bilgisayar uygulaması alabilir.</span><span class="sxs-lookup"><span data-stu-id="e20ec-110">Receive input messages from the registered raw input devices and forward appropriate messages to the host application.</span></span>  
  
- <span data-ttu-id="e20ec-111">Konak uygulama özel ilerleme durumu ve hata kullanıcı arabirimleri için sorgu.</span><span class="sxs-lookup"><span data-stu-id="e20ec-111">Query the host application for custom progress and error user interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e20ec-112">Bu API yalnızca hedeflenen ve yerel istemci makinesinde kullanımı desteklenen</span><span class="sxs-lookup"><span data-stu-id="e20ec-112">This API is only intended and supported for use on the local client machine</span></span>  
  
## <a name="members"></a><span data-ttu-id="e20ec-113">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e20ec-113">Members</span></span>  
  
|<span data-ttu-id="e20ec-114">Üye</span><span class="sxs-lookup"><span data-stu-id="e20ec-114">Member</span></span>|<span data-ttu-id="e20ec-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e20ec-115">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e20ec-116">GetRawInputDevices</span><span class="sxs-lookup"><span data-stu-id="e20ec-116">GetRawInputDevices</span></span>](getrawinputdevices.md)|<span data-ttu-id="e20ec-117">Ana bilgisayar uygulaması, ilgileniyor ham giriş cihazlarını (İnsan Arabirimi aygıtları) bulma PresentationHost.exe sağlar.</span><span class="sxs-lookup"><span data-stu-id="e20ec-117">Allows PresentationHost.exe to discover the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>|  
|[<span data-ttu-id="e20ec-118">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="e20ec-118">FilterInputMessage</span></span>](filterinputmessage.md)|<span data-ttu-id="e20ec-119">E_NOTIMPL sürece bir ileti alındığında PresentationHost.exe tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="e20ec-119">Called by PresentationHost.exe whenever a message is received unless E_NOTIMPL is returned.</span></span>|  
|[<span data-ttu-id="e20ec-120">GetCustomUI</span><span class="sxs-lookup"><span data-stu-id="e20ec-120">GetCustomUI</span></span>](getcustomui.md)|<span data-ttu-id="e20ec-121">Varsayılan olarak, kendi dağıtımının ilerleme durumunu ve dağıtım hata PresentationHost.exe WPF içeriği dağıtıldığında görüntülenen kullanıcı arabirimleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="e20ec-121">By default, PresentationHost.exe provides its own deployment progress and deployment error user interfaces that are displayed when WPF content is deployed.</span></span>|
