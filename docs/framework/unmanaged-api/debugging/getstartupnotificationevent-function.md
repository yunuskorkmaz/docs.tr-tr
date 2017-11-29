---
title: "GetStartupNotificationEvent İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetStartupNotificationEvent
api_location: dbgshim.dll
api_type: COM
f1_keywords: GetStartupNotificationEvent
helpviewer_keywords:
- GetStartupNotificationEvent function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: c94b1b61-045a-4695-bacd-0f18c5acc246
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 305350a9186c90af1e8646bc230536dcd2de47cc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="getstartupnotificationevent-function"></a><span data-ttu-id="cd08b-102">GetStartupNotificationEvent İşlevi</span><span class="sxs-lookup"><span data-stu-id="cd08b-102">GetStartupNotificationEvent Function</span></span>
<span data-ttu-id="cd08b-103">Sonra belirtilen hedef işleminde yüklenen tüm ortak dil çalışma zamanı (CLR) tarafından bildirim yapılan bir olay tanıtıcısı açar veya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cd08b-103">Creates or opens an event handle that will be signaled upon by any common language runtime (CLR) that is loading in the specified target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd08b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cd08b-104">Syntax</span></span>  
  
```  
HRESULT GetStartupNotificationEvent  
    (  
    [in]  DWORD     debuggeePID,  
    [out]  HANDLE*  phStartupEvent  
    );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cd08b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cd08b-105">Parameters</span></span>  
 `debuggeePID`  
 <span data-ttu-id="cd08b-106">[in] CLR başlatma bildirimlerini almak üzere hedef işlemini işlem tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="cd08b-106">[in] Process identifier of the target process from which to receive CLR startup notifications.</span></span>  
  
 `phStartupEvent`  
 <span data-ttu-id="cd08b-107">[out] Bir işaretçi bir CLR başlangıçta tarafından işaret işlenecek.</span><span class="sxs-lookup"><span data-stu-id="cd08b-107">[out] A pointer to a handle that will be signaled by a CLR on startup.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cd08b-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cd08b-108">Return Value</span></span>  
 <span data-ttu-id="cd08b-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="cd08b-109">S_OK</span></span>  
 <span data-ttu-id="cd08b-110">Başlangıç bildirim olayı tanıtıcısını başarıyla aldı.</span><span class="sxs-lookup"><span data-stu-id="cd08b-110">Successfully obtained the handle to the startup notification event.</span></span>  
  
 <span data-ttu-id="cd08b-111">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="cd08b-111">E_INVALIDARG</span></span>  
 <span data-ttu-id="cd08b-112">`phStartupEvent`null veya `debuggeePID` şu anda çalışan bir işlemin başvurmuyor.</span><span class="sxs-lookup"><span data-stu-id="cd08b-112">`phStartupEvent` is null or `debuggeePID` does not refer to a process that is currently running.</span></span>  
  
 <span data-ttu-id="cd08b-113">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="cd08b-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="cd08b-114">Başlangıç bildirim olayı tanıtıcısını elde edilemiyor.</span><span class="sxs-lookup"><span data-stu-id="cd08b-114">Unable to obtain the handle to the startup notification event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd08b-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cd08b-115">Remarks</span></span>  
 <span data-ttu-id="cd08b-116">Windows işletim sisteminde `debuggeePID` eşlemeleri bir işletim sistemi için işlem tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="cd08b-116">On the Windows operating system, `debuggeePID` maps to an OS process identifier.</span></span>  
  
 <span data-ttu-id="cd08b-117">Olay herhangi önce yönetilen kod olay işareti CLR tarafından yürütülen verdi.</span><span class="sxs-lookup"><span data-stu-id="cd08b-117">The event is signaled before any managed code is executed by the CLR that signaled the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd08b-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cd08b-118">Requirements</span></span>  
 <span data-ttu-id="cd08b-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd08b-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd08b-120">**Başlık:** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="cd08b-120">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="cd08b-121">**Kitaplığı:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="cd08b-121">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="cd08b-122">**.NET framework sürümleri:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="cd08b-122">**.NET Framework Versions:** 3.5 SP1</span></span>
