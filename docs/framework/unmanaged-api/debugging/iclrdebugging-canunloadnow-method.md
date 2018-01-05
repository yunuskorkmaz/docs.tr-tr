---
title: "ICLRDebugging::CanUnloadNow Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebugging.CanUnloadNow Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDebugging::CanUnloadNow
helpviewer_keywords:
- CanUnloadNow method [.NET Framework debugging]
- ICLRDebugging::CanUnloadNow method [.NET Framework debugging]
ms.assetid: 62e0630c-8cb7-45d2-b622-5a472abfd8cf
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b781db409991b07463002008a834dfb7ac32c9e1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdebuggingcanunloadnow-method"></a><span data-ttu-id="f52b4-102">ICLRDebugging::CanUnloadNow Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f52b4-102">ICLRDebugging::CanUnloadNow Method</span></span>
<span data-ttu-id="f52b4-103">Tarafından sağlanan bir kitaplık olup olmadığını belirleyen bir [Iclrdebugginglibraryprovider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) arabirimi hala kullanımda veya kaldırılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="f52b4-103">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f52b4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f52b4-104">Syntax</span></span>  
  
```  
HRESULT CanUnloadNow(HMODULE hModule);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f52b4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f52b4-105">Parameters</span></span>  
 `hmodule`  
 <span data-ttu-id="f52b4-106">[in] Hedef işlemin modülünde temel adres.</span><span class="sxs-lookup"><span data-stu-id="f52b4-106">[in] The base address of a module in the target process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f52b4-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f52b4-107">Return Value</span></span>  
 <span data-ttu-id="f52b4-108">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="f52b4-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="f52b4-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f52b4-109">HRESULT</span></span>|<span data-ttu-id="f52b4-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f52b4-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f52b4-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f52b4-111">S_OK</span></span>|<span data-ttu-id="f52b4-112">Tarafından başvurulan modül `hmodule` kaldırılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="f52b4-112">The module that is referenced by `hmodule` can be unloaded.</span></span>|  
|<span data-ttu-id="f52b4-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="f52b4-113">S_FALSE</span></span>|<span data-ttu-id="f52b4-114">Tarafından başvurulan modül `hmodule` hala kullanımda.</span><span class="sxs-lookup"><span data-stu-id="f52b4-114">The module that is referenced by `hmodule` is still in use.</span></span>|  
|<span data-ttu-id="f52b4-115">COR_E_NOT_CLR</span><span class="sxs-lookup"><span data-stu-id="f52b4-115">COR_E_NOT_CLR</span></span>|<span data-ttu-id="f52b4-116">Belirtilen modül bir CLR modül değil.</span><span class="sxs-lookup"><span data-stu-id="f52b4-116">The indicated module is not a CLR module.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="f52b4-117">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="f52b4-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f52b4-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f52b4-118">Remarks</span></span>  
 <span data-ttu-id="f52b4-119">Bu yöntem tüm bakar örneklerini `ICorDebug*` arabirimleri serbest bırakılmış ve hiçbir iş parçacığı şu an için bir çağrı içinde [Iclrdebugging::openvirtualprocess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f52b4-119">This method checks to see if all instances of `ICorDebug*` interfaces have been released and no thread is currently within a call to the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f52b4-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f52b4-120">Requirements</span></span>  
 <span data-ttu-id="f52b4-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f52b4-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f52b4-122">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f52b4-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f52b4-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f52b4-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f52b4-124">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f52b4-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f52b4-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f52b4-125">See Also</span></span>  
 [<span data-ttu-id="f52b4-126">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f52b4-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="f52b4-127">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="f52b4-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
