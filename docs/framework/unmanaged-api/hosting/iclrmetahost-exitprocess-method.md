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
ms.openlocfilehash: bbf3c00eafe47556c6b46e1acb687a19df5a2b28
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54601768"
---
# <a name="iclrmetahostexitprocess-method"></a><span data-ttu-id="67d53-102">ICLRMetaHost::ExitProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="67d53-102">ICLRMetaHost::ExitProcess Method</span></span>
<span data-ttu-id="67d53-103">Yüklenen tüm çalışma zamanları düzgün biçimde kapatılamadı dener ve sonra da işlemi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="67d53-103">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="67d53-104">Yerine geçen [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="67d53-104">Supersedes the [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67d53-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="67d53-105">Syntax</span></span>  
  
```  
HRESULT ExitProcess (  
    [in] INT32 iExitCode);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="67d53-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="67d53-106">Parameters</span></span>  
 `iExitCode`  
 <span data-ttu-id="67d53-107">[in] İşlem çıkış kodu.</span><span class="sxs-lookup"><span data-stu-id="67d53-107">[in] The exit code for the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="67d53-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="67d53-108">Return Value</span></span>  
 <span data-ttu-id="67d53-109">Dönüş değeri tanımlanmamış, bu nedenle bu yöntem hiçbir zaman, döndürür.</span><span class="sxs-lookup"><span data-stu-id="67d53-109">This method never returns, so its return value is undefined.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67d53-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="67d53-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67d53-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="67d53-111">Requirements</span></span>  
 <span data-ttu-id="67d53-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67d53-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67d53-113">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="67d53-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="67d53-114">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="67d53-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="67d53-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67d53-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67d53-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67d53-116">See also</span></span>
- [<span data-ttu-id="67d53-117">ICLRMetaHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="67d53-117">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="67d53-118">Barındırma</span><span class="sxs-lookup"><span data-stu-id="67d53-118">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
