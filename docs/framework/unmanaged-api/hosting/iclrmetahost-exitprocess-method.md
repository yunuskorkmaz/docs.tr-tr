---
title: ICLRMetaHost::ExitProcess Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.ExitProcess
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::ExitProcess
helpviewer_keywords:
- ICLRMetaHost::ExitProcess method [.NET Framework hosting]
- ExitProcess method, ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: b4df98cc-4e4e-407b-b8f4-e0076afef3a4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fc71762fb4a660cf84814cdd46d09696a161f3c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431603"
---
# <a name="iclrmetahostexitprocess-method"></a><span data-ttu-id="be59b-102">ICLRMetaHost::ExitProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="be59b-102">ICLRMetaHost::ExitProcess Method</span></span>
<span data-ttu-id="be59b-103">Tüm yüklenen çalışma zamanları dikkatlice kapatmak çalışır ve işlemi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="be59b-103">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="be59b-104">Yerine geçen [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="be59b-104">Supersedes the [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be59b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="be59b-105">Syntax</span></span>  
  
```  
HRESULT ExitProcess (  
    [in] INT32 iExitCode);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="be59b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="be59b-106">Parameters</span></span>  
 `iExitCode`  
 <span data-ttu-id="be59b-107">[in] İşlem çıkış kodu.</span><span class="sxs-lookup"><span data-stu-id="be59b-107">[in] The exit code for the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="be59b-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="be59b-108">Return Value</span></span>  
 <span data-ttu-id="be59b-109">Dönüş değeri tanımsız olduğu için bu yöntem hiçbir zaman, döndürür.</span><span class="sxs-lookup"><span data-stu-id="be59b-109">This method never returns, so its return value is undefined.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be59b-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="be59b-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be59b-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="be59b-111">Requirements</span></span>  
 <span data-ttu-id="be59b-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be59b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be59b-113">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="be59b-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="be59b-114">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="be59b-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="be59b-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be59b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be59b-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="be59b-116">See Also</span></span>  
 [<span data-ttu-id="be59b-117">ICLRMetaHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="be59b-117">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [<span data-ttu-id="be59b-118">Barındırma</span><span class="sxs-lookup"><span data-stu-id="be59b-118">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
