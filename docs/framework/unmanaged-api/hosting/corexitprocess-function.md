---
description: 'Daha fazla bilgi edinin: CorExitProcess Işlevi'
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
ms.openlocfilehash: 68d33dec76387e103a34e99c529a4e7aff7535b4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649591"
---
# <a name="corexitprocess-function"></a><span data-ttu-id="b2a0b-103">CorExitProcess İşlevi</span><span class="sxs-lookup"><span data-stu-id="b2a0b-103">CorExitProcess Function</span></span>

<span data-ttu-id="b2a0b-104">Geçerli yönetilmeyen işlemi kapatır.</span><span class="sxs-lookup"><span data-stu-id="b2a0b-104">Shuts down the current unmanaged process.</span></span>  
  
 <span data-ttu-id="b2a0b-105">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="b2a0b-105">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="b2a0b-106">Bunun yerine [ICLRMetaHost:: ExitProcess](iclrmetahost-exitprocess-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="b2a0b-106">Use the [ICLRMetaHost::ExitProcess](iclrmetahost-exitprocess-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2a0b-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b2a0b-107">Syntax</span></span>  
  
```cpp  
void STDMETHODCALLTYPE CorExitProcess (
  int  exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2a0b-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b2a0b-108">Parameters</span></span>  

 `exitCode`  
 <span data-ttu-id="b2a0b-109">İşlem çıkış kodunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="b2a0b-109">An integer that specifies the process exit code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b2a0b-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b2a0b-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b2a0b-111">.NET Framework 4 ' ten başlayarak, `CorExitProcess` yalnızca eski API 'lerin bağlandığı çalışma zamanına değil, işlemdeki tüm başlatılan çalışma zamanından çıkılıyor.</span><span class="sxs-lookup"><span data-stu-id="b2a0b-111">Beginning with the .NET Framework 4, `CorExitProcess` exits every started runtime in the process, not just the runtime to which the legacy APIs have been bound.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2a0b-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b2a0b-112">Requirements</span></span>  

 <span data-ttu-id="b2a0b-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2a0b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2a0b-114">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b2a0b-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b2a0b-115">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b2a0b-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b2a0b-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2a0b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2a0b-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2a0b-117">See also</span></span>

- [<span data-ttu-id="b2a0b-118">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="b2a0b-118">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
