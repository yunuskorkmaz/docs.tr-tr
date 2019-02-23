---
title: FilterInputMessage
ms.date: 03/30/2017
helpviewer_keywords:
- raw input [WPF]
- FilterInputMessage method [WPF]
ms.assetid: 4d74c6cf-7d1d-49ff-96c1-231340ce54f5
ms.openlocfilehash: c3620e13951afddc8de25c314de17704548d2366
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56746172"
---
# <a name="filterinputmessage"></a><span data-ttu-id="7a960-102">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="7a960-102">FilterInputMessage</span></span>
<span data-ttu-id="7a960-103">E_NOTIMPL sürece bir ileti alındığında PresentationHost.exe tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="7a960-103">Called by PresentationHost.exe whenever a message is received unless E_NOTIMPL is returned.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a960-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7a960-104">Syntax</span></span>  
  
```  
HRESULT FilterInputMessage( [in] MSG* pMsg ) ;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7a960-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7a960-105">Parameters</span></span>  
 `pMsg`  
  
 <span data-ttu-id="7a960-106">[in] WM_INPUT iletisi, işlenmemiş giriş alma pencereye Gönder.</span><span class="sxs-lookup"><span data-stu-id="7a960-106">[in] The WM_INPUT message sent to the window that is getting raw input.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="7a960-107">Özellik Değeri/Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7a960-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="7a960-108">HRESULT:</span><span class="sxs-lookup"><span data-stu-id="7a960-108">HRESULT:</span></span>  
  
 <span data-ttu-id="7a960-109">S_OK - İleti Filtresi işlemedi ve daha fazla işleme ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="7a960-109">S_OK - The filter did not process the message and further processing may occur.</span></span>  
  
 <span data-ttu-id="7a960-110">Bu ileti filtresi S_FALSE - işleme ve başka işlem gerçekleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="7a960-110">S_FALSE - The filter processed this message and no further processing should occur.</span></span>  
  
 <span data-ttu-id="7a960-111">Bu değer döndürmüyorsa E_NOTIMPL – [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md) yeniden çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="7a960-111">E_NOTIMPL – If this value is returned, [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md) is not called again.</span></span> <span data-ttu-id="7a960-112">Bu yalnızca özel ilerleme sağlanmasıyla ilgilenen bir ana bilgisayar uygulaması öğesinden döndürülen ve PresentationHost.exe hata kullanıcı arabirimleri İlgilenmiyor ham giriş iletileri PresentationHost.exe iletilen.</span><span class="sxs-lookup"><span data-stu-id="7a960-112">This might be returned from a host application that is only interested in providing custom progress and error user interfaces to PresentationHost.exe is not interested in being forwarded raw input messages from PresentationHost.exe.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a960-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7a960-113">Remarks</span></span>  
 <span data-ttu-id="7a960-114">PresentationHost.exe klavye, fare ve uzak denetimler gibi çeşitli ham giriş cihazlar hedefidir.</span><span class="sxs-lookup"><span data-stu-id="7a960-114">PresentationHost.exe is the target of various raw input devices, including keyboard, mice, and remote controls.</span></span> <span data-ttu-id="7a960-115">Bazı durumlarda, ana uygulama davranışını PresentationHost.exe tarafından tüketilen giriş bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="7a960-115">Sometimes, behavior in the host application is dependent on input that would otherwise be consumed by PresentationHost.exe.</span></span> <span data-ttu-id="7a960-116">Örneğin, bir ana bilgisayar uygulaması belirli kullanıcı arabirimi öğeleri görüntülemek gerekip gerekmediğini belirlemek için belirli giriş iletileri almaya üzerinde bağlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="7a960-116">For example, a host application may depend on receiving certain input messages to determine whether or not to display specific user interface elements.</span></span>  
  
 <span data-ttu-id="7a960-117">Bu davranışların sağlamak için gerekli giriş iletileri almak ana bilgisayar uygulaması izin vermek için PresentationHost.exe barındırılan uygulama için uygun ham giriş iletileri çağırarak iletir [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md).</span><span class="sxs-lookup"><span data-stu-id="7a960-117">To allow the host application to receive the necessary input messages to provide these behaviors, PresentationHost.exe forwards appropriate raw input messages to the hosted application by calling [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md).</span></span>  
  
 <span data-ttu-id="7a960-118">Grup tarafından döndürülen ham giriş cihazı (İnsan Arabirimi cihazları) ile kaydederek barındırılan uygulama ham giriş iletileri alan [GetRawInputDevices](../../../../docs/framework/wpf/app-development/getrawinputdevices.md).</span><span class="sxs-lookup"><span data-stu-id="7a960-118">The hosted application receives raw input messages by registering with the set of raw input devices (Human Interface Devices) returned by [GetRawInputDevices](../../../../docs/framework/wpf/app-development/getrawinputdevices.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a960-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a960-119">See also</span></span>
- [<span data-ttu-id="7a960-120">WM_INPUT iletisi</span><span class="sxs-lookup"><span data-stu-id="7a960-120">WM_INPUT message</span></span>](/windows/desktop/inputdev/wm-input)
