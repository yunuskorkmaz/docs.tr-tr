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
ms.openlocfilehash: 64c212d064ad658678926690d1e680afe27c7c99
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993258"
---
# <a name="iclrmetahostexitprocess-method"></a><span data-ttu-id="52c85-102">ICLRMetaHost::ExitProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="52c85-102">ICLRMetaHost::ExitProcess Method</span></span>
<span data-ttu-id="52c85-103">Yüklenen tüm çalışma zamanları düzgün biçimde kapatılamadı dener ve sonra da işlemi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="52c85-103">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="52c85-104">Yerine geçen [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="52c85-104">Supersedes the [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52c85-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="52c85-105">Syntax</span></span>  
  
```  
HRESULT ExitProcess (  
    [in] INT32 iExitCode);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52c85-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="52c85-106">Parameters</span></span>  
 `iExitCode`  
 <span data-ttu-id="52c85-107">[in] İşlem çıkış kodu.</span><span class="sxs-lookup"><span data-stu-id="52c85-107">[in] The exit code for the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="52c85-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="52c85-108">Return Value</span></span>  
 <span data-ttu-id="52c85-109">Dönüş değeri tanımlanmamış, bu nedenle bu yöntem hiçbir zaman, döndürür.</span><span class="sxs-lookup"><span data-stu-id="52c85-109">This method never returns, so its return value is undefined.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52c85-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="52c85-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52c85-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="52c85-111">Requirements</span></span>  
 <span data-ttu-id="52c85-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52c85-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52c85-113">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="52c85-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="52c85-114">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="52c85-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="52c85-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52c85-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52c85-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52c85-116">See also</span></span>

- [<span data-ttu-id="52c85-117">ICLRMetaHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="52c85-117">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="52c85-118">Barındırma</span><span class="sxs-lookup"><span data-stu-id="52c85-118">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
