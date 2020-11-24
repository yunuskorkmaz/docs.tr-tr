---
title: GetStartupNotificationEvent İşlevi
ms.date: 03/30/2017
api_name:
- GetStartupNotificationEvent
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- GetStartupNotificationEvent
helpviewer_keywords:
- GetStartupNotificationEvent function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: c94b1b61-045a-4695-bacd-0f18c5acc246
topic_type:
- apiref
ms.openlocfilehash: 1c6ad35cd42760a4d88cf78bb084a25cf58a1064
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676094"
---
# <a name="getstartupnotificationevent-function"></a><span data-ttu-id="c802f-102">GetStartupNotificationEvent İşlevi</span><span class="sxs-lookup"><span data-stu-id="c802f-102">GetStartupNotificationEvent Function</span></span>

<span data-ttu-id="c802f-103">Belirtilen hedef işlemde yüklenen herhangi bir ortak dil çalışma zamanı (CLR) tarafından işaret edilecek bir olay tanıtıcısı oluşturur veya açar.</span><span class="sxs-lookup"><span data-stu-id="c802f-103">Creates or opens an event handle that will be signaled upon by any common language runtime (CLR) that is loading in the specified target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c802f-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c802f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStartupNotificationEvent  
    (  
    [in]  DWORD     debuggeePID,  
    [out]  HANDLE*  phStartupEvent  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="c802f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c802f-105">Parameters</span></span>  

 `debuggeePID`  
 <span data-ttu-id="c802f-106">'ndaki CLR başlangıç bildirimlerinin alınacağı hedef işlemin işlem tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="c802f-106">[in] Process identifier of the target process from which to receive CLR startup notifications.</span></span>  
  
 `phStartupEvent`  
 <span data-ttu-id="c802f-107">dışı Başlangıçta CLR tarafından bildirilecektir bir tanıtıcı işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="c802f-107">[out] A pointer to a handle that will be signaled by a CLR on startup.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c802f-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c802f-108">Return Value</span></span>  

 <span data-ttu-id="c802f-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="c802f-109">S_OK</span></span>  
 <span data-ttu-id="c802f-110">Tanıtıcı, başlangıç bildirimi olayına başarıyla alındı.</span><span class="sxs-lookup"><span data-stu-id="c802f-110">Successfully obtained the handle to the startup notification event.</span></span>  
  
 <span data-ttu-id="c802f-111">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c802f-111">E_INVALIDARG</span></span>  
 <span data-ttu-id="c802f-112">`phStartupEvent` null veya `debuggeePID` Şu anda çalışan bir işleme başvurmuyor.</span><span class="sxs-lookup"><span data-stu-id="c802f-112">`phStartupEvent` is null or `debuggeePID` does not refer to a process that is currently running.</span></span>  
  
 <span data-ttu-id="c802f-113">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="c802f-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="c802f-114">Başlangıç bildirimi olayının tanıtıcısı alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="c802f-114">Unable to obtain the handle to the startup notification event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c802f-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c802f-115">Remarks</span></span>  

 <span data-ttu-id="c802f-116">Windows işletim sisteminde `debuggeePID` BIR işletim sistemi işlem tanımlayıcısına eşlenir.</span><span class="sxs-lookup"><span data-stu-id="c802f-116">On the Windows operating system, `debuggeePID` maps to an OS process identifier.</span></span>  
  
 <span data-ttu-id="c802f-117">Olaya, olayı gösteren CLR tarafından yönetilen herhangi bir kod yürütülmeden önce sinyal gönderilir.</span><span class="sxs-lookup"><span data-stu-id="c802f-117">The event is signaled before any managed code is executed by the CLR that signaled the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c802f-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c802f-118">Requirements</span></span>  

 <span data-ttu-id="c802f-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c802f-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c802f-120">**Üstbilgi:** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="c802f-120">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="c802f-121">**Kitaplık:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="c802f-121">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="c802f-122">**.NET Framework sürümleri:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="c802f-122">**.NET Framework Versions:** 3.5 SP1</span></span>
