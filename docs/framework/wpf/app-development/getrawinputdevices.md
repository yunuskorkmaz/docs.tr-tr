---
title: GetRawInputDevices
ms.date: 03/30/2017
helpviewer_keywords:
- raw input [WPF]
ms.assetid: c4d37ecd-065a-4d1c-9e6c-26804ae968ca
ms.openlocfilehash: 0cb1184ddc3e8051a68dfed12367dea65a06b623
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50034506"
---
# <a name="getrawinputdevices"></a><span data-ttu-id="7d027-102">GetRawInputDevices</span><span class="sxs-lookup"><span data-stu-id="7d027-102">GetRawInputDevices</span></span>
<span data-ttu-id="7d027-103">Ana bilgisayar uygulaması, ilgileniyor ham giriş cihazlarını (İnsan Arabirimi aygıtları) bulma PresentationHost.exe sağlar.</span><span class="sxs-lookup"><span data-stu-id="7d027-103">Allows PresentationHost.exe to discover the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d027-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7d027-104">Syntax</span></span>  
  
```  
HRESULT GetRawInputDevices( [out] IEnumRAWINPUTDEVICE **ppEnum );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7d027-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7d027-105">Parameters</span></span>  
 `ppEnum`  
  
 <span data-ttu-id="7d027-106">[out] Bir işaretçi bir [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) için ham giriş cihazları listeleniyor.</span><span class="sxs-lookup"><span data-stu-id="7d027-106">[out] A pointer to an [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) for enumerating the raw input devices.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="7d027-107">Özellik Değeri/Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7d027-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="7d027-108">HRESULT:</span><span class="sxs-lookup"><span data-stu-id="7d027-108">HRESULT:</span></span>  
  
 <span data-ttu-id="7d027-109">S_OK - [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) S_OK döndürülürse yalnızca PresentationHost.exe tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7d027-109">S_OK - [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) will only be used by PresentationHost.exe if S_OK is returned.</span></span>  
  
 <span data-ttu-id="7d027-110">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="7d027-110">E_NOTIMPL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d027-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7d027-111">Remarks</span></span>  
 <span data-ttu-id="7d027-112">Ham giriş cihazları klavye, fare ve daha az geleneksel cihazları uzaktan kumandalar gibi içeren giriş cihazları kümesidir.</span><span class="sxs-lookup"><span data-stu-id="7d027-112">Raw input devices are the set of input devices that includes keyboards, mice, and less traditional devices like remote controls.</span></span>  
  
 <span data-ttu-id="7d027-113">Ham giriş cihazların listesini alındıktan sonra PresentationHost.exe WM_INPUT bildirim iletilerinin alınacağı ile cihazları kaydeder.</span><span class="sxs-lookup"><span data-stu-id="7d027-113">Once the list of raw input devices has been retrieved, PresentationHost.exe registers with the devices to receive WM_INPUT notification messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d027-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7d027-114">See Also</span></span>  
 [<span data-ttu-id="7d027-115">GetRawInputDeviceList</span><span class="sxs-lookup"><span data-stu-id="7d027-115">GetRawInputDeviceList</span></span>](/windows/desktop/api/winuser/nf-winuser-getrawinputdevicelist)  
 [<span data-ttu-id="7d027-116">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="7d027-116">FilterInputMessage</span></span>](../../../../docs/framework/wpf/app-development/filterinputmessage.md)
