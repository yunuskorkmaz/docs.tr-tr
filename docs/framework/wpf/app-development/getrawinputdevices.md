---
title: GetRawInputDevices
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: raw input [WPF]
ms.assetid: c4d37ecd-065a-4d1c-9e6c-26804ae968ca
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e936b4ef2cab65e72ca9edbc3b95281815938983
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="getrawinputdevices"></a><span data-ttu-id="22ec7-102">GetRawInputDevices</span><span class="sxs-lookup"><span data-stu-id="22ec7-102">GetRawInputDevices</span></span>
<span data-ttu-id="22ec7-103">Ana uygulamanın ilgilendiği ham giriş aygıtlarını (İnsan Arabirimi aygıtları) keşfetmek için PresentationHost.exe'ye izin verir.</span><span class="sxs-lookup"><span data-stu-id="22ec7-103">Allows PresentationHost.exe to discover the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22ec7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="22ec7-104">Syntax</span></span>  
  
```  
HRESULT GetRawInputDevices( [out] IEnumRAWINPUTDEVICE **ppEnum );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="22ec7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="22ec7-105">Parameters</span></span>  
 `ppEnum`  
  
 <span data-ttu-id="22ec7-106">[out] Bir işaretçi bir [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) ham giriş aygıtlarını numaralandırma.</span><span class="sxs-lookup"><span data-stu-id="22ec7-106">[out] A pointer to an [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) for enumerating the raw input devices.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="22ec7-107">Özellik Değeri/Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="22ec7-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="22ec7-108">HRESULT:</span><span class="sxs-lookup"><span data-stu-id="22ec7-108">HRESULT:</span></span>  
  
 <span data-ttu-id="22ec7-109">S_OK - [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) S_OK döndürülürse yalnızca PresentationHost.exe tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="22ec7-109">S_OK - [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) will only be used by PresentationHost.exe if S_OK is returned.</span></span>  
  
 <span data-ttu-id="22ec7-110">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="22ec7-110">E_NOTIMPL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22ec7-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="22ec7-111">Remarks</span></span>  
 <span data-ttu-id="22ec7-112">Ham giriş aygıtları klavye, fare ve Uzaktan denetimleri gibi daha az geleneksel aygıtları içeren giriş aygıtları kümesidir.</span><span class="sxs-lookup"><span data-stu-id="22ec7-112">Raw input devices are the set of input devices that includes keyboards, mice, and less traditional devices like remote controls.</span></span>  
  
 <span data-ttu-id="22ec7-113">Ham giriş aygıtları listesi alındıktan sonra PresentationHost.exe WM_INPUT bildirim iletileri almak için aygıtları kaydeder.</span><span class="sxs-lookup"><span data-stu-id="22ec7-113">Once the list of raw input devices has been retrieved, PresentationHost.exe registers with the devices to receive WM_INPUT notification messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22ec7-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="22ec7-114">See Also</span></span>  
 [<span data-ttu-id="22ec7-115">http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputfunctions/getrawinputdevicelist.asp</span><span class="sxs-lookup"><span data-stu-id="22ec7-115">http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputfunctions/getrawinputdevicelist.asp</span></span>](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputfunctions/getrawinputdevicelist.asp)  
 [<span data-ttu-id="22ec7-116">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="22ec7-116">FilterInputMessage</span></span>](../../../../docs/framework/wpf/app-development/filterinputmessage.md)
