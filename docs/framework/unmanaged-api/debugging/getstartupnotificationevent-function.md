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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8ed1db49be78d7d16648a9ef9735e79ef1b3ab98
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487336"
---
# <a name="getstartupnotificationevent-function"></a><span data-ttu-id="6de7b-102">GetStartupNotificationEvent İşlevi</span><span class="sxs-lookup"><span data-stu-id="6de7b-102">GetStartupNotificationEvent Function</span></span>
<span data-ttu-id="6de7b-103">Oluşturur veya üzerine belirtilen hedef işlemde yüklenmekte olan tüm ortak dil çalışma zamanı (CLR) tarafından sinyal bir olay işleyici açılır.</span><span class="sxs-lookup"><span data-stu-id="6de7b-103">Creates or opens an event handle that will be signaled upon by any common language runtime (CLR) that is loading in the specified target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6de7b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6de7b-104">Syntax</span></span>  
  
```  
HRESULT GetStartupNotificationEvent  
    (  
    [in]  DWORD     debuggeePID,  
    [out]  HANDLE*  phStartupEvent  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="6de7b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6de7b-105">Parameters</span></span>  
 `debuggeePID`  
 <span data-ttu-id="6de7b-106">[in] CLR başlatma bildirimlerini almak üzere hedef işlemin işlem tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="6de7b-106">[in] Process identifier of the target process from which to receive CLR startup notifications.</span></span>  
  
 `phStartupEvent`  
 <span data-ttu-id="6de7b-107">[out] Başlangıçta bir CLR tarafından sinyal bir tanıtıcı bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6de7b-107">[out] A pointer to a handle that will be signaled by a CLR on startup.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6de7b-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6de7b-108">Return Value</span></span>  
 <span data-ttu-id="6de7b-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="6de7b-109">S_OK</span></span>  
 <span data-ttu-id="6de7b-110">Başlangıç bildirim olayı tanıtıcısını başarıyla aldı.</span><span class="sxs-lookup"><span data-stu-id="6de7b-110">Successfully obtained the handle to the startup notification event.</span></span>  
  
 <span data-ttu-id="6de7b-111">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="6de7b-111">E_INVALIDARG</span></span>  
 <span data-ttu-id="6de7b-112">`phStartupEvent` null veya `debuggeePID` şu anda çalışan bir işleme başvurmuyor.</span><span class="sxs-lookup"><span data-stu-id="6de7b-112">`phStartupEvent` is null or `debuggeePID` does not refer to a process that is currently running.</span></span>  
  
 <span data-ttu-id="6de7b-113">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="6de7b-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="6de7b-114">Başlangıç bildirim olay tanıtıcısı alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="6de7b-114">Unable to obtain the handle to the startup notification event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6de7b-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6de7b-115">Remarks</span></span>  
 <span data-ttu-id="6de7b-116">Windows işletim sisteminde `debuggeePID` eşlemeleri bir işletim sistemi için işlem tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="6de7b-116">On the Windows operating system, `debuggeePID` maps to an OS process identifier.</span></span>  
  
 <span data-ttu-id="6de7b-117">Olay herhangi önce yönetilen kod olayın sinyal CLR tarafından yürütülen işaret bildirilir.</span><span class="sxs-lookup"><span data-stu-id="6de7b-117">The event is signaled before any managed code is executed by the CLR that signaled the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6de7b-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6de7b-118">Requirements</span></span>  
 <span data-ttu-id="6de7b-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6de7b-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6de7b-120">**Başlık:** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="6de7b-120">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="6de7b-121">**Kitaplığı:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="6de7b-121">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="6de7b-122">**.NET framework sürümleri:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="6de7b-122">**.NET Framework Versions:** 3.5 SP1</span></span>
