---
title: CorExitProcess İşlevi
ms.date: 03/30/2017
api_name:
- CorExitProcess
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CorExitProcess
helpviewer_keywords:
- CorExitProcess function [.NET Framework hosting]
ms.assetid: a5cab4c6-990e-47f3-8798-cf422b791015
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e1104a98afb32dea687949e9c723124014c1e62
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925311"
---
# <a name="corexitprocess-function"></a><span data-ttu-id="3c0b2-102">CorExitProcess İşlevi</span><span class="sxs-lookup"><span data-stu-id="3c0b2-102">CorExitProcess Function</span></span>
<span data-ttu-id="3c0b2-103">Geçerli yönetilmeyen işlemi kapatır.</span><span class="sxs-lookup"><span data-stu-id="3c0b2-103">Shuts down the current unmanaged process.</span></span>  
  
 <span data-ttu-id="3c0b2-104">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="3c0b2-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="3c0b2-105">Bunun yerine [ICLRMetaHost:: ExitProcess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="3c0b2-105">Use the [ICLRMetaHost::ExitProcess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c0b2-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3c0b2-106">Syntax</span></span>  
  
```cpp  
void STDMETHODCALLTYPE CorExitProcess (   
  int  exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c0b2-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3c0b2-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="3c0b2-108">İşlem çıkış kodunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="3c0b2-108">An integer that specifies the process exit code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c0b2-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3c0b2-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3c0b2-110">.NET Framework 4 ' ten başlayarak, `CorExitProcess` yalnızca eski API 'lerin bağlandığı çalışma zamanına değil, işlemdeki tüm başlatılan çalışma zamanından çıkılıyor.</span><span class="sxs-lookup"><span data-stu-id="3c0b2-110">Beginning with the .NET Framework 4, `CorExitProcess` exits every started runtime in the process, not just the runtime to which the legacy APIs have been bound.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c0b2-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3c0b2-111">Requirements</span></span>  
 <span data-ttu-id="3c0b2-112">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c0b2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c0b2-113">**Üst bilgi** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3c0b2-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3c0b2-114">**Kitaplığı** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3c0b2-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3c0b2-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c0b2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c0b2-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c0b2-116">See also</span></span>

- [<span data-ttu-id="3c0b2-117">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="3c0b2-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
