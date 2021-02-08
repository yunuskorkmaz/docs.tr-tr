---
description: ': ICLRDebugManager:: SetSymbolReadingPolicy yöntemi hakkında daha fazla bilgi edinin'
title: ICLRDebugManager::SetSymbolReadingPolicy Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.SetSymbolReadingPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::SetSymbolReadingPolicy
helpviewer_keywords:
- ICLRDebugManager, SetSymbolREadingPolicy method
- SetSymbolReadingPolicy method [.NET Framework hosting]
- ICLRDebugManager::SetSymbolReadingPolicy method [.NET Framework hosting]
ms.assetid: bd921fa2-d377-4d79-acfc-64c38d4dcae9
topic_type:
- apiref
ms.openlocfilehash: 2c0862f3c572808ffbf418b275e1ad1c62c2ac89
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781954"
---
# <a name="iclrdebugmanagersetsymbolreadingpolicy-method"></a><span data-ttu-id="e0301-103">ICLRDebugManager::SetSymbolReadingPolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e0301-103">ICLRDebugManager::SetSymbolReadingPolicy Method</span></span>

<span data-ttu-id="e0301-104">Program veritabanı (PDB) dosyalarını okuma ilkesini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e0301-104">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="e0301-105">İlke, satır numaraları ve dosya hakkındaki bilgilerin çağrı yığınlarına dahil edilip edilmeyeceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="e0301-105">The policy determines whether information about line numbers and files is included in call stacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0301-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e0301-106">Syntax</span></span>  
  
```cpp  
HRESULT SetSymbolReadingPolicy (  
    [in] ESymbolReadingPolicy policy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0301-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e0301-107">Parameters</span></span>  

 `policy`  
 <span data-ttu-id="e0301-108">'ndaki [Esi Mbolreadingpolicy](esymbolreadingpolicy-enumeration.md) numaralandırması üyesi.</span><span class="sxs-lookup"><span data-stu-id="e0301-108">[in] A member of the [ESymbolReadingPolicy](esymbolreadingpolicy-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e0301-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e0301-109">Return Value</span></span>  
  
|<span data-ttu-id="e0301-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e0301-110">HRESULT</span></span>|<span data-ttu-id="e0301-111">Description</span><span class="sxs-lookup"><span data-stu-id="e0301-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e0301-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="e0301-112">S_OK</span></span>|<span data-ttu-id="e0301-113">`SetSymbolReadingPolicy` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e0301-113">`SetSymbolReadingPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="e0301-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e0301-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e0301-115">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="e0301-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e0301-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e0301-116">E_FAIL</span></span>|<span data-ttu-id="e0301-117">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e0301-117">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e0301-118">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e0301-118">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e0301-119">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="e0301-119">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e0301-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e0301-120">Requirements</span></span>  

 <span data-ttu-id="e0301-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0301-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0301-122">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e0301-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e0301-123">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="e0301-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e0301-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0301-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0301-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0301-125">See also</span></span>

- [<span data-ttu-id="e0301-126">ICLRDebugManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e0301-126">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
