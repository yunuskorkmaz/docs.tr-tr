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
ms.openlocfilehash: 6737b953f39c1087d01f3fb864d84340a6968aba
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129350"
---
# <a name="iclrdebugmanagersetsymbolreadingpolicy-method"></a><span data-ttu-id="512f6-102">ICLRDebugManager::SetSymbolReadingPolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="512f6-102">ICLRDebugManager::SetSymbolReadingPolicy Method</span></span>
<span data-ttu-id="512f6-103">Program veritabanı (PDB) dosyalarını okuma ilkesini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="512f6-103">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="512f6-104">İlke, satır numaraları ve dosya hakkındaki bilgilerin çağrı yığınlarına dahil edilip edilmeyeceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="512f6-104">The policy determines whether information about line numbers and files is included in call stacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="512f6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="512f6-105">Syntax</span></span>  
  
```cpp  
HRESULT SetSymbolReadingPolicy (  
    [in] ESymbolReadingPolicy policy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="512f6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="512f6-106">Parameters</span></span>  
 `policy`  
 <span data-ttu-id="512f6-107">'ndaki [Esi Mbolreadingpolicy](../../../../docs/framework/unmanaged-api/hosting/esymbolreadingpolicy-enumeration.md) numaralandırması üyesi.</span><span class="sxs-lookup"><span data-stu-id="512f6-107">[in] A member of the [ESymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/esymbolreadingpolicy-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="512f6-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="512f6-108">Return Value</span></span>  
  
|<span data-ttu-id="512f6-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="512f6-109">HRESULT</span></span>|<span data-ttu-id="512f6-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="512f6-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="512f6-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="512f6-111">S_OK</span></span>|<span data-ttu-id="512f6-112">`SetSymbolReadingPolicy` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="512f6-112">`SetSymbolReadingPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="512f6-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="512f6-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="512f6-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="512f6-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="512f6-115">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="512f6-115">E_FAIL</span></span>|<span data-ttu-id="512f6-116">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="512f6-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="512f6-117">Bir yöntem E_FAıL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="512f6-117">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="512f6-118">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="512f6-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="512f6-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="512f6-119">Requirements</span></span>  
 <span data-ttu-id="512f6-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="512f6-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="512f6-121">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="512f6-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="512f6-122">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="512f6-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="512f6-123">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="512f6-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="512f6-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="512f6-124">See also</span></span>

- [<span data-ttu-id="512f6-125">ICLRDebugManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="512f6-125">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
