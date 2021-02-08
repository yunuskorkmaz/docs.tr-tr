---
description: 'Daha fazla bilgi edinin: GetStartupNotificationEvent Işlevi'
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
ms.openlocfilehash: 49b0e3f9b2acec87e419bae03086a7e437f45f98
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801390"
---
# <a name="getstartupnotificationevent-function"></a><span data-ttu-id="07cc6-103">GetStartupNotificationEvent İşlevi</span><span class="sxs-lookup"><span data-stu-id="07cc6-103">GetStartupNotificationEvent Function</span></span>

<span data-ttu-id="07cc6-104">Belirtilen hedef işlemde yüklenen herhangi bir ortak dil çalışma zamanı (CLR) tarafından işaret edilecek bir olay tanıtıcısı oluşturur veya açar.</span><span class="sxs-lookup"><span data-stu-id="07cc6-104">Creates or opens an event handle that will be signaled upon by any common language runtime (CLR) that is loading in the specified target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07cc6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="07cc6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStartupNotificationEvent  
    (  
    [in]  DWORD     debuggeePID,  
    [out]  HANDLE*  phStartupEvent  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="07cc6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="07cc6-106">Parameters</span></span>  

 `debuggeePID`  
 <span data-ttu-id="07cc6-107">'ndaki CLR başlangıç bildirimlerinin alınacağı hedef işlemin işlem tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="07cc6-107">[in] Process identifier of the target process from which to receive CLR startup notifications.</span></span>  
  
 `phStartupEvent`  
 <span data-ttu-id="07cc6-108">dışı Başlangıçta CLR tarafından bildirilecektir bir tanıtıcı işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="07cc6-108">[out] A pointer to a handle that will be signaled by a CLR on startup.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="07cc6-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="07cc6-109">Return Value</span></span>  

 <span data-ttu-id="07cc6-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="07cc6-110">S_OK</span></span>  
 <span data-ttu-id="07cc6-111">Tanıtıcı, başlangıç bildirimi olayına başarıyla alındı.</span><span class="sxs-lookup"><span data-stu-id="07cc6-111">Successfully obtained the handle to the startup notification event.</span></span>  
  
 <span data-ttu-id="07cc6-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="07cc6-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="07cc6-113">`phStartupEvent` null veya `debuggeePID` Şu anda çalışan bir işleme başvurmuyor.</span><span class="sxs-lookup"><span data-stu-id="07cc6-113">`phStartupEvent` is null or `debuggeePID` does not refer to a process that is currently running.</span></span>  
  
 <span data-ttu-id="07cc6-114">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="07cc6-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="07cc6-115">Başlangıç bildirimi olayının tanıtıcısı alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="07cc6-115">Unable to obtain the handle to the startup notification event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07cc6-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="07cc6-116">Remarks</span></span>  

 <span data-ttu-id="07cc6-117">Windows işletim sisteminde `debuggeePID` BIR işletim sistemi işlem tanımlayıcısına eşlenir.</span><span class="sxs-lookup"><span data-stu-id="07cc6-117">On the Windows operating system, `debuggeePID` maps to an OS process identifier.</span></span>  
  
 <span data-ttu-id="07cc6-118">Olaya, olayı gösteren CLR tarafından yönetilen herhangi bir kod yürütülmeden önce sinyal gönderilir.</span><span class="sxs-lookup"><span data-stu-id="07cc6-118">The event is signaled before any managed code is executed by the CLR that signaled the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07cc6-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="07cc6-119">Requirements</span></span>  

 <span data-ttu-id="07cc6-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07cc6-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07cc6-121">**Üstbilgi:** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="07cc6-121">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="07cc6-122">**Kitaplık:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="07cc6-122">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="07cc6-123">**.NET Framework sürümleri:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="07cc6-123">**.NET Framework Versions:** 3.5 SP1</span></span>
