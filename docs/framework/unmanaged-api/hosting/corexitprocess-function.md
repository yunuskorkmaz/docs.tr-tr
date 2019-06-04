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
ms.openlocfilehash: 2a28b33f80299ae6fce34f9de66b6f7f1bc70ef6
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490560"
---
# <a name="corexitprocess-function"></a><span data-ttu-id="15482-102">CorExitProcess İşlevi</span><span class="sxs-lookup"><span data-stu-id="15482-102">CorExitProcess Function</span></span>
<span data-ttu-id="15482-103">Yönetilmeyen geçerli işlemi kapatır.</span><span class="sxs-lookup"><span data-stu-id="15482-103">Shuts down the current unmanaged process.</span></span>  
  
 <span data-ttu-id="15482-104">Bu işlev .NET Framework 4'te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="15482-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="15482-105">Kullanım [Iclrmetahost::exitprocess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="15482-105">Use the [ICLRMetaHost::ExitProcess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15482-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="15482-106">Syntax</span></span>  
  
```  
void STDMETHODCALLTYPE CorExitProcess (   
  int  exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15482-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="15482-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="15482-108">İşlem çıkış kodunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="15482-108">An integer that specifies the process exit code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15482-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="15482-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="15482-110">.NET Framework 4 ile başlayarak `CorExitProcess` başlatılan her çalışma zamanı işleminde, yalnızca, eski API'ler bağlı çalışma zamanı çıkar.</span><span class="sxs-lookup"><span data-stu-id="15482-110">Beginning with the .NET Framework 4, `CorExitProcess` exits every started runtime in the process, not just the runtime to which the legacy APIs have been bound.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15482-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="15482-111">Requirements</span></span>  
 <span data-ttu-id="15482-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15482-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15482-113">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="15482-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="15482-114">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="15482-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="15482-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15482-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15482-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15482-116">See also</span></span>

- [<span data-ttu-id="15482-117">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="15482-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
