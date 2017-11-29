---
title: "ICLRMetaHost::ExitProcess Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHost.ExitProcess
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHost::ExitProcess
helpviewer_keywords:
- ICLRMetaHost::ExitProcess method [.NET Framework hosting]
- ExitProcess method, ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: b4df98cc-4e4e-407b-b8f4-e0076afef3a4
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 10fb9bef99a90a76ea5bb1f4abe73cd756717285
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrmetahostexitprocess-method"></a><span data-ttu-id="56777-102">ICLRMetaHost::ExitProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="56777-102">ICLRMetaHost::ExitProcess Method</span></span>
<span data-ttu-id="56777-103">Tüm yüklenen çalışma zamanları dikkatlice kapatmak çalışır ve işlemi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="56777-103">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="56777-104">Yerine geçen [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="56777-104">Supersedes the [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56777-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="56777-105">Syntax</span></span>  
  
```  
HRESULT ExitProcess (  
    [in] INT32 iExitCode);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="56777-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="56777-106">Parameters</span></span>  
 `iExitCode`  
 <span data-ttu-id="56777-107">[in] İşlem çıkış kodu.</span><span class="sxs-lookup"><span data-stu-id="56777-107">[in] The exit code for the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="56777-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="56777-108">Return Value</span></span>  
 <span data-ttu-id="56777-109">Dönüş değeri tanımsız olduğu için bu yöntem hiçbir zaman, döndürür.</span><span class="sxs-lookup"><span data-stu-id="56777-109">This method never returns, so its return value is undefined.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56777-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="56777-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56777-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="56777-111">Requirements</span></span>  
 <span data-ttu-id="56777-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56777-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56777-113">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="56777-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="56777-114">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="56777-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="56777-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56777-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56777-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="56777-116">See Also</span></span>  
 [<span data-ttu-id="56777-117">Iclrmetahost arabirimi</span><span class="sxs-lookup"><span data-stu-id="56777-117">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [<span data-ttu-id="56777-118">Barındırma</span><span class="sxs-lookup"><span data-stu-id="56777-118">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
