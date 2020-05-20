---
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
ms.openlocfilehash: f037e902a9f573023022c81503ea3b987cf6d424
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615767"
---
# <a name="iclrdebugmanagersetsymbolreadingpolicy-method"></a><span data-ttu-id="07a69-102">ICLRDebugManager::SetSymbolReadingPolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="07a69-102">ICLRDebugManager::SetSymbolReadingPolicy Method</span></span>
<span data-ttu-id="07a69-103">Program veritabanı (PDB) dosyalarını okuma ilkesini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="07a69-103">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="07a69-104">İlke, satır numaraları ve dosya hakkındaki bilgilerin çağrı yığınlarına dahil edilip edilmeyeceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="07a69-104">The policy determines whether information about line numbers and files is included in call stacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07a69-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="07a69-105">Syntax</span></span>  
  
```cpp  
HRESULT SetSymbolReadingPolicy (  
    [in] ESymbolReadingPolicy policy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07a69-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="07a69-106">Parameters</span></span>  
 `policy`  
 <span data-ttu-id="07a69-107">'ndaki [Esi Mbolreadingpolicy](esymbolreadingpolicy-enumeration.md) numaralandırması üyesi.</span><span class="sxs-lookup"><span data-stu-id="07a69-107">[in] A member of the [ESymbolReadingPolicy](esymbolreadingpolicy-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="07a69-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="07a69-108">Return Value</span></span>  
  
|<span data-ttu-id="07a69-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="07a69-109">HRESULT</span></span>|<span data-ttu-id="07a69-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="07a69-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="07a69-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="07a69-111">S_OK</span></span>|<span data-ttu-id="07a69-112">`SetSymbolReadingPolicy`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="07a69-112">`SetSymbolReadingPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="07a69-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="07a69-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="07a69-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="07a69-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="07a69-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="07a69-115">E_FAIL</span></span>|<span data-ttu-id="07a69-116">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="07a69-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="07a69-117">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="07a69-117">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="07a69-118">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="07a69-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="07a69-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="07a69-119">Requirements</span></span>  
 <span data-ttu-id="07a69-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07a69-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07a69-121">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="07a69-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="07a69-122">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="07a69-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="07a69-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07a69-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07a69-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07a69-124">See also</span></span>

- [<span data-ttu-id="07a69-125">ICLRDebugManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="07a69-125">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
