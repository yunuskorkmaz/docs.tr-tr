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
ms.openlocfilehash: 44578595b3cb790570c5359e714bd39c109cf1f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176467"
---
# <a name="corexitprocess-function"></a><span data-ttu-id="0e351-102">CorExitProcess İşlevi</span><span class="sxs-lookup"><span data-stu-id="0e351-102">CorExitProcess Function</span></span>
<span data-ttu-id="0e351-103">Geçerli yönetilmeyen işlemi kapatır.</span><span class="sxs-lookup"><span data-stu-id="0e351-103">Shuts down the current unmanaged process.</span></span>  
  
 <span data-ttu-id="0e351-104">Bu işlev .NET Framework 4'te amortismana hazırlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0e351-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="0e351-105">Bunun yerine [ICLRMetaHost::ExitProcess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0e351-105">Use the [ICLRMetaHost::ExitProcess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e351-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0e351-106">Syntax</span></span>  
  
```cpp  
void STDMETHODCALLTYPE CorExitProcess (
  int  exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e351-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0e351-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="0e351-108">İşlem çıkış kodunu belirten bir sonsayı.</span><span class="sxs-lookup"><span data-stu-id="0e351-108">An integer that specifies the process exit code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0e351-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0e351-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0e351-110">.NET Framework 4'ten `CorExitProcess` başlayarak, sadece eski API'lerin bağlı olduğu çalışma zamanı değil, işlemdeki her başlangıç çalışma zamanından çıkar.</span><span class="sxs-lookup"><span data-stu-id="0e351-110">Beginning with the .NET Framework 4, `CorExitProcess` exits every started runtime in the process, not just the runtime to which the legacy APIs have been bound.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e351-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0e351-111">Requirements</span></span>  
 <span data-ttu-id="0e351-112">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e351-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e351-113">**Üstbilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0e351-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0e351-114">**Kütüphane:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="0e351-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0e351-115">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e351-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e351-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e351-116">See also</span></span>

- [<span data-ttu-id="0e351-117">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="0e351-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
