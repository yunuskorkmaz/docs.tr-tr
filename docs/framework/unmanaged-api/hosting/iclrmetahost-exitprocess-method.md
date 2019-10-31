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
ms.openlocfilehash: d8643c54950486b6374045ff83928c8c7fb568a9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140945"
---
# <a name="iclrmetahostexitprocess-method"></a><span data-ttu-id="68478-102">ICLRMetaHost::ExitProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="68478-102">ICLRMetaHost::ExitProcess Method</span></span>
<span data-ttu-id="68478-103">Tüm yüklenen çalışma zamanlarını sorunsuz bir şekilde kapatmaya çalışır ve sonra işlemi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="68478-103">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="68478-104">[CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) işlevinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="68478-104">Supersedes the [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68478-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="68478-105">Syntax</span></span>  
  
```cpp  
HRESULT ExitProcess (  
    [in] INT32 iExitCode);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68478-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="68478-106">Parameters</span></span>  
 `iExitCode`  
 <span data-ttu-id="68478-107">'ndaki İşlemin çıkış kodu.</span><span class="sxs-lookup"><span data-stu-id="68478-107">[in] The exit code for the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="68478-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="68478-108">Return Value</span></span>  
 <span data-ttu-id="68478-109">Bu yöntem hiçbir şekilde döndürmez, bu nedenle dönüş değeri tanımsız olur.</span><span class="sxs-lookup"><span data-stu-id="68478-109">This method never returns, so its return value is undefined.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68478-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="68478-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68478-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="68478-111">Requirements</span></span>  
 <span data-ttu-id="68478-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68478-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68478-113">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="68478-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="68478-114">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="68478-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="68478-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68478-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68478-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68478-116">See also</span></span>

- [<span data-ttu-id="68478-117">ICLRMetaHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="68478-117">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="68478-118">Barındırma</span><span class="sxs-lookup"><span data-stu-id="68478-118">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
