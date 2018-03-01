---
title: "CorExitProcess İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorExitProcess
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CorExitProcess
helpviewer_keywords:
- CorExitProcess function [.NET Framework hosting]
ms.assetid: a5cab4c6-990e-47f3-8798-cf422b791015
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 560f63c131ad336a3ff4b4edec0aed2b58d33ba5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="corexitprocess-function"></a><span data-ttu-id="68250-102">CorExitProcess İşlevi</span><span class="sxs-lookup"><span data-stu-id="68250-102">CorExitProcess Function</span></span>
<span data-ttu-id="68250-103">Geçerli yönetilmeyen işlemi kapatır.</span><span class="sxs-lookup"><span data-stu-id="68250-103">Shuts down the current unmanaged process.</span></span>  
  
 <span data-ttu-id="68250-104">Bu işlev kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="68250-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="68250-105">Kullanım [Iclrmetahost::exitprocess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="68250-105">Use the [ICLRMetaHost::ExitProcess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68250-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="68250-106">Syntax</span></span>  
  
```  
void STDMETHODCALLTYPE CorExitProcess (   
  int  exitCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="68250-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="68250-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="68250-108">İşlem çıkış kodu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="68250-108">An integer that specifies the process exit code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68250-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="68250-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="68250-110">İle başlayarak [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], `CorExitProcess` işleminde, yalnızca, eski API bağlı çalışma zamanı başlatılan her çalışma zamanı çıkar.</span><span class="sxs-lookup"><span data-stu-id="68250-110">Beginning with the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], `CorExitProcess` exits every started runtime in the process, not just the runtime to which the legacy APIs have been bound.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68250-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="68250-111">Requirements</span></span>  
 <span data-ttu-id="68250-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68250-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68250-113">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="68250-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="68250-114">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="68250-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="68250-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68250-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68250-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="68250-116">See Also</span></span>  
 [<span data-ttu-id="68250-117">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="68250-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
