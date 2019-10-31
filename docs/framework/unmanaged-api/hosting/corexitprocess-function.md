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
ms.openlocfilehash: fe61503cdf46b6b2cf568deb78b96f8fa885c203
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136928"
---
# <a name="corexitprocess-function"></a><span data-ttu-id="88230-102">CorExitProcess İşlevi</span><span class="sxs-lookup"><span data-stu-id="88230-102">CorExitProcess Function</span></span>
<span data-ttu-id="88230-103">Geçerli yönetilmeyen işlemi kapatır.</span><span class="sxs-lookup"><span data-stu-id="88230-103">Shuts down the current unmanaged process.</span></span>  
  
 <span data-ttu-id="88230-104">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="88230-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="88230-105">Bunun yerine [ICLRMetaHost:: ExitProcess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="88230-105">Use the [ICLRMetaHost::ExitProcess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88230-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="88230-106">Syntax</span></span>  
  
```cpp  
void STDMETHODCALLTYPE CorExitProcess (   
  int  exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="88230-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="88230-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="88230-108">İşlem çıkış kodunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="88230-108">An integer that specifies the process exit code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88230-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="88230-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="88230-110">.NET Framework 4 ' ten başlayarak, yalnızca eski API 'Lerin bağlandığı çalışma zamanına değil, işlemdeki tüm başlatılan çalışma zamanına çıkış `CorExitProcess`.</span><span class="sxs-lookup"><span data-stu-id="88230-110">Beginning with the .NET Framework 4, `CorExitProcess` exits every started runtime in the process, not just the runtime to which the legacy APIs have been bound.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88230-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="88230-111">Requirements</span></span>  
 <span data-ttu-id="88230-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88230-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88230-113">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="88230-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="88230-114">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="88230-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="88230-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88230-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88230-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88230-116">See also</span></span>

- [<span data-ttu-id="88230-117">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="88230-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
