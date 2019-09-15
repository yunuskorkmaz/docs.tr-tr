---
title: GetRawInputDevices
ms.date: 03/30/2017
helpviewer_keywords:
- raw input [WPF]
ms.assetid: c4d37ecd-065a-4d1c-9e6c-26804ae968ca
ms.openlocfilehash: 4fc7a5021f9f8d9e6badcd3e13266fb8f4bfe7a4
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991753"
---
# <a name="getrawinputdevices"></a><span data-ttu-id="36a2e-102">GetRawInputDevices</span><span class="sxs-lookup"><span data-stu-id="36a2e-102">GetRawInputDevices</span></span>
<span data-ttu-id="36a2e-103">PresentationHost. exe ' nin, ana bilgisayar uygulamasının ilgilendiği ham giriş cihazlarını (Insan arabirimi cihazları) bulmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="36a2e-103">Allows PresentationHost.exe to discover the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36a2e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="36a2e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRawInputDevices( [out] IEnumRAWINPUTDEVICE **ppEnum );  
```  
  
## <a name="parameters"></a><span data-ttu-id="36a2e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="36a2e-105">Parameters</span></span>  
 `ppEnum`  
  
 <span data-ttu-id="36a2e-106">dışı Ham giriş cihazlarını numaralandırmak için bir [ıenumoywınputdevice](ienumrawinputdevice.md) işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="36a2e-106">[out] A pointer to an [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) for enumerating the raw input devices.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="36a2e-107">Özellik Değeri/Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="36a2e-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="36a2e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="36a2e-108">HRESULT:</span></span>  
  
 <span data-ttu-id="36a2e-109">S_OK- [ıenumkıwınputdevice](ienumrawinputdevice.md) yalnızca S_OK döndürülürse, PresentationHost. exe tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="36a2e-109">S_OK - [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) will only be used by PresentationHost.exe if S_OK is returned.</span></span>  
  
 <span data-ttu-id="36a2e-110">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="36a2e-110">E_NOTIMPL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36a2e-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="36a2e-111">Remarks</span></span>  
 <span data-ttu-id="36a2e-112">Ham giriş aygıtları, uzaktan kumandalar gibi klavye, fare ve daha az geleneksel cihazları içeren giriş cihazlarıdır.</span><span class="sxs-lookup"><span data-stu-id="36a2e-112">Raw input devices are the set of input devices that includes keyboards, mice, and less traditional devices like remote controls.</span></span>  
  
 <span data-ttu-id="36a2e-113">Ham giriş cihazlarının listesi alındıktan sonra PresentationHost. exe, WM_INPUT bildirim iletilerini almak için cihazlara kaydolur.</span><span class="sxs-lookup"><span data-stu-id="36a2e-113">Once the list of raw input devices has been retrieved, PresentationHost.exe registers with the devices to receive WM_INPUT notification messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36a2e-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36a2e-114">See also</span></span>

- [<span data-ttu-id="36a2e-115">Getpwınputdevicelist</span><span class="sxs-lookup"><span data-stu-id="36a2e-115">GetRawInputDeviceList</span></span>](/windows/desktop/api/winuser/nf-winuser-getrawinputdevicelist)
- [<span data-ttu-id="36a2e-116">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="36a2e-116">FilterInputMessage</span></span>](filterinputmessage.md)
