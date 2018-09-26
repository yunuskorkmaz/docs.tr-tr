---
title: FilterInputMessage
ms.date: 03/30/2017
helpviewer_keywords:
- raw input [WPF]
- FilterInputMessage method [WPF]
ms.assetid: 4d74c6cf-7d1d-49ff-96c1-231340ce54f5
ms.openlocfilehash: 1a22071696ca012968e042e15cd8a9f4b876fd9f
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47070298"
---
# <a name="filterinputmessage"></a><span data-ttu-id="c7262-102">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="c7262-102">FilterInputMessage</span></span>
<span data-ttu-id="c7262-103">E_NOTIMPL sürece bir ileti alındığında PresentationHost.exe tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="c7262-103">Called by PresentationHost.exe whenever a message is received unless E_NOTIMPL is returned.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7262-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c7262-104">Syntax</span></span>  
  
```  
HRESULT FilterInputMessage( [in] MSG* pMsg ) ;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c7262-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c7262-105">Parameters</span></span>  
 `pMsg`  
  
 <span data-ttu-id="c7262-106">[in] WM_INPUT iletisi, işlenmemiş giriş alma pencereye Gönder.</span><span class="sxs-lookup"><span data-stu-id="c7262-106">[in] The WM_INPUT message sent to the window that is getting raw input.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="c7262-107">Özellik Değeri/Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c7262-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="c7262-108">HRESULT:</span><span class="sxs-lookup"><span data-stu-id="c7262-108">HRESULT:</span></span>  
  
 <span data-ttu-id="c7262-109">S_OK - İleti Filtresi işlemedi ve daha fazla işleme ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="c7262-109">S_OK - The filter did not process the message and further processing may occur.</span></span>  
  
 <span data-ttu-id="c7262-110">Bu ileti filtresi S_FALSE - işleme ve başka işlem gerçekleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="c7262-110">S_FALSE - The filter processed this message and no further processing should occur.</span></span>  
  
 <span data-ttu-id="c7262-111">Bu değer döndürmüyorsa E_NOTIMPL – [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md) yeniden çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="c7262-111">E_NOTIMPL – If this value is returned, [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md) is not called again.</span></span> <span data-ttu-id="c7262-112">Bu yalnızca özel ilerleme sağlanmasıyla ilgilenen bir ana bilgisayar uygulaması öğesinden döndürülen ve PresentationHost.exe hata kullanıcı arabirimleri İlgilenmiyor ham giriş iletileri PresentationHost.exe iletilen.</span><span class="sxs-lookup"><span data-stu-id="c7262-112">This might be returned from a host application that is only interested in providing custom progress and error user interfaces to PresentationHost.exe is not interested in being forwarded raw input messages from PresentationHost.exe.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7262-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c7262-113">Remarks</span></span>  
 <span data-ttu-id="c7262-114">PresentationHost.exe klavye, fare ve uzak denetimler gibi çeşitli ham giriş cihazlar hedefidir.</span><span class="sxs-lookup"><span data-stu-id="c7262-114">PresentationHost.exe is the target of various raw input devices, including keyboard, mice, and remote controls.</span></span> <span data-ttu-id="c7262-115">Bazı durumlarda, ana uygulama davranışını PresentationHost.exe tarafından tüketilen giriş bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="c7262-115">Sometimes, behavior in the host application is dependent on input that would otherwise be consumed by PresentationHost.exe.</span></span> <span data-ttu-id="c7262-116">Örneğin, bir ana bilgisayar uygulaması belirli kullanıcı arabirimi öğeleri görüntülemek gerekip gerekmediğini belirlemek için belirli giriş iletileri almaya üzerinde bağlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="c7262-116">For example, a host application may depend on receiving certain input messages to determine whether or not to display specific user interface elements.</span></span>  
  
 <span data-ttu-id="c7262-117">Bu davranışların sağlamak için gerekli giriş iletileri almak ana bilgisayar uygulaması izin vermek için PresentationHost.exe barındırılan uygulama için uygun ham giriş iletileri çağırarak iletir [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md).</span><span class="sxs-lookup"><span data-stu-id="c7262-117">To allow the host application to receive the necessary input messages to provide these behaviors, PresentationHost.exe forwards appropriate raw input messages to the hosted application by calling [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md).</span></span>  
  
 <span data-ttu-id="c7262-118">Grup tarafından döndürülen ham giriş cihazı (İnsan Arabirimi cihazları) ile kaydederek barındırılan uygulama ham giriş iletileri alan [GetRawInputDevices](../../../../docs/framework/wpf/app-development/getrawinputdevices.md).</span><span class="sxs-lookup"><span data-stu-id="c7262-118">The hosted application receives raw input messages by registering with the set of raw input devices (Human Interface Devices) returned by [GetRawInputDevices](../../../../docs/framework/wpf/app-development/getrawinputdevices.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7262-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c7262-119">See Also</span></span>  
 [<span data-ttu-id="c7262-120">WM_INPUT Bildirimi</span><span class="sxs-lookup"><span data-stu-id="c7262-120">WM_INPUT Notification</span></span>](https://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputmessages/wm_input.asp)
