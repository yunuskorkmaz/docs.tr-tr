---
title: IWpfHostSupport
ms.date: 03/30/2017
helpviewer_keywords:
- IWpfHostSupport interface [WPF]
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
ms.openlocfilehash: 57d9ef87a078655a89a5869a48a1bd16f21b000f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43500932"
---
# <a name="iwpfhostsupport"></a><span data-ttu-id="f32ab-102">IWpfHostSupport</span><span class="sxs-lookup"><span data-stu-id="f32ab-102">IWpfHostSupport</span></span>
<span data-ttu-id="f32ab-103">Barındıran uygulamalar [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] PresentationHost.exe üzerinden içerik PresentationHost.exe ve konak arasında tümleştirme noktası sağlamak için bu arabirimi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="f32ab-103">Applications that host [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] content via PresentationHost.exe implement this interface to provide a point of integration between the host and PresentationHost.exe.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f32ab-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f32ab-104">Remarks</span></span>  
 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]<span data-ttu-id="f32ab-105"> Web tarayıcıları gibi uygulamaları barındırabilir [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] dahil olmak üzere içerik [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] ve XAML kaybedilir.</span><span class="sxs-lookup"><span data-stu-id="f32ab-105"> applications such as Web browsers can host [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] content, including [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] and loose XAML.</span></span> <span data-ttu-id="f32ab-106">Ana bilgisayara [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] içerik [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] uygulamaları oluşturma örneği [WebBrowser denetimi](https://go.microsoft.com/fwlink/?LinkId=97911).</span><span class="sxs-lookup"><span data-stu-id="f32ab-106">To host [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] content, [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] applications create an instance of the [WebBrowser control](https://go.microsoft.com/fwlink/?LinkId=97911).</span></span> <span data-ttu-id="f32ab-107">Barındırılması için [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] barındırılan sağlayan PresentationHost.exe örneği oluşturur [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] görüntülemek için ana içerik [WebBrowser denetimi](https://go.microsoft.com/fwlink/?LinkId=97911).</span><span class="sxs-lookup"><span data-stu-id="f32ab-107">To be hosted, [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] creates an instance of PresentationHost.exe, which provides the hosted [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] content to the host for display in the [WebBrowser control](https://go.microsoft.com/fwlink/?LinkId=97911).</span></span>  
  
 <span data-ttu-id="f32ab-108">Tarafından etkinleştirilen tümleştirme `IWpfHostSupport` için PresentationHost.exe sağlar:</span><span class="sxs-lookup"><span data-stu-id="f32ab-108">The integration enabled by `IWpfHostSupport` allows PresentationHost.exe to:</span></span>  
  
-   <span data-ttu-id="f32ab-109">Bul ve ana bilgisayar uygulaması, ilgileniyor ham giriş cihazları (İnsan Arabirimi cihazlar) ile kaydedin.</span><span class="sxs-lookup"><span data-stu-id="f32ab-109">Discover and register with the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>  
  
-   <span data-ttu-id="f32ab-110">Giriş iletileri ham giriş cihazlar kayıtlı ve uygun iletileri yönlendirmek için ana bilgisayar uygulaması alabilir.</span><span class="sxs-lookup"><span data-stu-id="f32ab-110">Receive input messages from the registered raw input devices and forward appropriate messages to the host application.</span></span>  
  
-   <span data-ttu-id="f32ab-111">Konak uygulama özel ilerleme durumu ve hata kullanıcı arabirimleri için sorgu.</span><span class="sxs-lookup"><span data-stu-id="f32ab-111">Query the host application for custom progress and error user interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f32ab-112">Bu API yalnızca hedeflenen ve yerel istemci makinesinde kullanımı desteklenen</span><span class="sxs-lookup"><span data-stu-id="f32ab-112">This API is only intended and supported for use on the local client machine</span></span>  
  
## <a name="members"></a><span data-ttu-id="f32ab-113">Üyeler</span><span class="sxs-lookup"><span data-stu-id="f32ab-113">Members</span></span>  
  
|<span data-ttu-id="f32ab-114">Üye</span><span class="sxs-lookup"><span data-stu-id="f32ab-114">Member</span></span>|<span data-ttu-id="f32ab-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f32ab-115">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f32ab-116">GetRawInputDevices</span><span class="sxs-lookup"><span data-stu-id="f32ab-116">GetRawInputDevices</span></span>](../../../../docs/framework/wpf/app-development/getrawinputdevices.md)|<span data-ttu-id="f32ab-117">Ana bilgisayar uygulaması, ilgileniyor ham giriş cihazlarını (İnsan Arabirimi aygıtları) bulma PresentationHost.exe sağlar.</span><span class="sxs-lookup"><span data-stu-id="f32ab-117">Allows PresentationHost.exe to discover the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>|  
|[<span data-ttu-id="f32ab-118">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="f32ab-118">FilterInputMessage</span></span>](../../../../docs/framework/wpf/app-development/filterinputmessage.md)|<span data-ttu-id="f32ab-119">E_NOTIMPL sürece bir ileti alındığında PresentationHost.exe tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f32ab-119">Called by PresentationHost.exe whenever a message is received unless E_NOTIMPL is returned.</span></span>|  
|[<span data-ttu-id="f32ab-120">GetCustomUI</span><span class="sxs-lookup"><span data-stu-id="f32ab-120">GetCustomUI</span></span>](../../../../docs/framework/wpf/app-development/getcustomui.md)|<span data-ttu-id="f32ab-121">Varsayılan olarak, kendi dağıtımının ilerleme durumunu ve dağıtım hata PresentationHost.exe WPF içeriği dağıtıldığında görüntülenen kullanıcı arabirimleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="f32ab-121">By default, PresentationHost.exe provides its own deployment progress and deployment error user interfaces that are displayed when WPF content is deployed.</span></span>|
