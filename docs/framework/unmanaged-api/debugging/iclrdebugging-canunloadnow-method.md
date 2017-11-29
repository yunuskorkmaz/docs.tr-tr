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
ms.openlocfilehash: b013231666ca6dfde5ab16e58023da1ae2a72941
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdebuggingcanunloadnow-method"></a><span data-ttu-id="de9d2-102">ICLRDebugging::CanUnloadNow Yöntemi</span><span class="sxs-lookup"><span data-stu-id="de9d2-102">ICLRDebugging::CanUnloadNow Method</span></span>
<span data-ttu-id="de9d2-103">Tarafından sağlanan bir kitaplık olup olmadığını belirleyen bir [Iclrdebugginglibraryprovider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) arabirimi hala kullanımda veya kaldırılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="de9d2-103">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de9d2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="de9d2-104">Syntax</span></span>  
  
```  
HRESULT CanUnloadNow(HMODULE hModule);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="de9d2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="de9d2-105">Parameters</span></span>  
 `hmodule`  
 <span data-ttu-id="de9d2-106">[in] Hedef işlemin modülünde temel adres.</span><span class="sxs-lookup"><span data-stu-id="de9d2-106">[in] The base address of a module in the target process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="de9d2-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="de9d2-107">Return Value</span></span>  
 <span data-ttu-id="de9d2-108">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="de9d2-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="de9d2-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="de9d2-109">HRESULT</span></span>|<span data-ttu-id="de9d2-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de9d2-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="de9d2-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="de9d2-111">S_OK</span></span>|<span data-ttu-id="de9d2-112">Tarafından başvurulan modül `hmodule` kaldırılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="de9d2-112">The module that is referenced by `hmodule` can be unloaded.</span></span>|  
|<span data-ttu-id="de9d2-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="de9d2-113">S_FALSE</span></span>|<span data-ttu-id="de9d2-114">Tarafından başvurulan modül `hmodule` hala kullanımda.</span><span class="sxs-lookup"><span data-stu-id="de9d2-114">The module that is referenced by `hmodule` is still in use.</span></span>|  
|<span data-ttu-id="de9d2-115">COR_E_NOT_CLR</span><span class="sxs-lookup"><span data-stu-id="de9d2-115">COR_E_NOT_CLR</span></span>|<span data-ttu-id="de9d2-116">Belirtilen modül bir CLR modül değil.</span><span class="sxs-lookup"><span data-stu-id="de9d2-116">The indicated module is not a CLR module.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="de9d2-117">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="de9d2-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de9d2-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="de9d2-118">Remarks</span></span>  
 <span data-ttu-id="de9d2-119">Bu yöntem tüm bakar örneklerini `ICorDebug*` arabirimleri serbest bırakılmış ve hiçbir iş parçacığı şu an için bir çağrı içinde [Iclrdebugging::openvirtualprocess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="de9d2-119">This method checks to see if all instances of `ICorDebug*` interfaces have been released and no thread is currently within a call to the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de9d2-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="de9d2-120">Requirements</span></span>  
 <span data-ttu-id="de9d2-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de9d2-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de9d2-122">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="de9d2-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="de9d2-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="de9d2-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="de9d2-124">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de9d2-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de9d2-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="de9d2-125">See Also</span></span>  
 [<span data-ttu-id="de9d2-126">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="de9d2-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="de9d2-127">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="de9d2-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
