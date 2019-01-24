---
title: ICLRDebugging::CanUnloadNow Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRDebugging.CanUnloadNow Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging::CanUnloadNow
helpviewer_keywords:
- CanUnloadNow method [.NET Framework debugging]
- ICLRDebugging::CanUnloadNow method [.NET Framework debugging]
ms.assetid: 62e0630c-8cb7-45d2-b622-5a472abfd8cf
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8fd0a7322437cb89fe62729f86f5ce8005ed3b5e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646756"
---
# <a name="iclrdebuggingcanunloadnow-method"></a><span data-ttu-id="6de98-102">ICLRDebugging::CanUnloadNow Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6de98-102">ICLRDebugging::CanUnloadNow Method</span></span>
<span data-ttu-id="6de98-103">Tarafından sağlanan bir kitaplığı olup olmadığını belirleyen bir [Iclrdebugginglibraryprovider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) arabirimi hala kullanımda olduğu veya kaldırılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="6de98-103">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6de98-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6de98-104">Syntax</span></span>  
  
```  
HRESULT CanUnloadNow(HMODULE hModule);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6de98-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6de98-105">Parameters</span></span>  
 `hmodule`  
 <span data-ttu-id="6de98-106">[in] Hedef işlemde bir modülün temel adres.</span><span class="sxs-lookup"><span data-stu-id="6de98-106">[in] The base address of a module in the target process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6de98-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6de98-107">Return Value</span></span>  
 <span data-ttu-id="6de98-108">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="6de98-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="6de98-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6de98-109">HRESULT</span></span>|<span data-ttu-id="6de98-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6de98-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6de98-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="6de98-111">S_OK</span></span>|<span data-ttu-id="6de98-112">Tarafından başvurulan modül `hmodule` kaldırılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="6de98-112">The module that is referenced by `hmodule` can be unloaded.</span></span>|  
|<span data-ttu-id="6de98-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="6de98-113">S_FALSE</span></span>|<span data-ttu-id="6de98-114">Tarafından başvurulan modül `hmodule` hala kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="6de98-114">The module that is referenced by `hmodule` is still in use.</span></span>|  
|<span data-ttu-id="6de98-115">COR_E_NOT_CLR</span><span class="sxs-lookup"><span data-stu-id="6de98-115">COR_E_NOT_CLR</span></span>|<span data-ttu-id="6de98-116">Belirtilen modül bir CLR modülünü değil.</span><span class="sxs-lookup"><span data-stu-id="6de98-116">The indicated module is not a CLR module.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="6de98-117">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="6de98-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6de98-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6de98-118">Remarks</span></span>  
 <span data-ttu-id="6de98-119">Bu yöntem tüm olup olmadığını denetler örneklerini `ICorDebug*` arabirimi yayımladı ve iş parçacığı şu anda bir çağrı içinde [Iclrdebugging::openvirtualprocess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6de98-119">This method checks to see if all instances of `ICorDebug*` interfaces have been released and no thread is currently within a call to the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6de98-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6de98-120">Requirements</span></span>  
 <span data-ttu-id="6de98-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6de98-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6de98-122">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6de98-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6de98-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6de98-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6de98-124">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6de98-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6de98-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6de98-125">See also</span></span>
- [<span data-ttu-id="6de98-126">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6de98-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="6de98-127">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="6de98-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
