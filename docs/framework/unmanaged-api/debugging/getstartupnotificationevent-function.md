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
ms.openlocfilehash: 3377dcd5d45ca8e31a57a75bd81366d41837c12c
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860708"
---
# <a name="getstartupnotificationevent-function"></a><span data-ttu-id="926d4-102">GetStartupNotificationEvent İşlevi</span><span class="sxs-lookup"><span data-stu-id="926d4-102">GetStartupNotificationEvent Function</span></span>
<span data-ttu-id="926d4-103">Belirtilen hedef işlemde yüklenen herhangi bir ortak dil çalışma zamanı (CLR) tarafından işaret edilecek bir olay tanıtıcısı oluşturur veya açar.</span><span class="sxs-lookup"><span data-stu-id="926d4-103">Creates or opens an event handle that will be signaled upon by any common language runtime (CLR) that is loading in the specified target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="926d4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="926d4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStartupNotificationEvent  
    (  
    [in]  DWORD     debuggeePID,  
    [out]  HANDLE*  phStartupEvent  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="926d4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="926d4-105">Parameters</span></span>  
 `debuggeePID`  
 <span data-ttu-id="926d4-106">'ndaki CLR başlangıç bildirimlerinin alınacağı hedef işlemin işlem tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="926d4-106">[in] Process identifier of the target process from which to receive CLR startup notifications.</span></span>  
  
 `phStartupEvent`  
 <span data-ttu-id="926d4-107">dışı Başlangıçta CLR tarafından bildirilecektir bir tanıtıcı işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="926d4-107">[out] A pointer to a handle that will be signaled by a CLR on startup.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="926d4-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="926d4-108">Return Value</span></span>  
 <span data-ttu-id="926d4-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="926d4-109">S_OK</span></span>  
 <span data-ttu-id="926d4-110">Tanıtıcı, başlangıç bildirimi olayına başarıyla alındı.</span><span class="sxs-lookup"><span data-stu-id="926d4-110">Successfully obtained the handle to the startup notification event.</span></span>  
  
 <span data-ttu-id="926d4-111">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="926d4-111">E_INVALIDARG</span></span>  
 <span data-ttu-id="926d4-112">`phStartupEvent`null veya `debuggeePID` Şu anda çalışan bir işleme başvurmuyor.</span><span class="sxs-lookup"><span data-stu-id="926d4-112">`phStartupEvent` is null or `debuggeePID` does not refer to a process that is currently running.</span></span>  
  
 <span data-ttu-id="926d4-113">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="926d4-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="926d4-114">Başlangıç bildirimi olayının tanıtıcısı alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="926d4-114">Unable to obtain the handle to the startup notification event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="926d4-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="926d4-115">Remarks</span></span>  
 <span data-ttu-id="926d4-116">Windows işletim sisteminde bir IŞLETIM sistemi `debuggeePID` işlem tanımlayıcısına eşlenir.</span><span class="sxs-lookup"><span data-stu-id="926d4-116">On the Windows operating system, `debuggeePID` maps to an OS process identifier.</span></span>  
  
 <span data-ttu-id="926d4-117">Olaya, olayı gösteren CLR tarafından yönetilen herhangi bir kod yürütülmeden önce sinyal gönderilir.</span><span class="sxs-lookup"><span data-stu-id="926d4-117">The event is signaled before any managed code is executed by the CLR that signaled the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="926d4-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="926d4-118">Requirements</span></span>  
 <span data-ttu-id="926d4-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="926d4-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="926d4-120">**Üstbilgi:** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="926d4-120">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="926d4-121">**Kitaplık:** dbgshim. dll</span><span class="sxs-lookup"><span data-stu-id="926d4-121">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="926d4-122">**.NET Framework sürümleri:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="926d4-122">**.NET Framework Versions:** 3.5 SP1</span></span>
