---
description: ': ICLRDebugging:: CanUnloadNow Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 537494fe862c58aa8a8768dd5ce2abc8ca94f87d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723380"
---
# <a name="iclrdebuggingcanunloadnow-method"></a><span data-ttu-id="8c3c9-103">ICLRDebugging::CanUnloadNow Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8c3c9-103">ICLRDebugging::CanUnloadNow Method</span></span>

<span data-ttu-id="8c3c9-104">Bir [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) arabirimi tarafından sağlanmış bir kitaplığın hala kullanımda olup olmadığını veya kaldırılabileceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="8c3c9-104">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c3c9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8c3c9-105">Syntax</span></span>  
  
```cpp  
HRESULT CanUnloadNow(HMODULE hModule);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c3c9-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8c3c9-106">Parameters</span></span>  

 `hmodule`  
 <span data-ttu-id="8c3c9-107">'ndaki Hedef işlemdeki bir modülün temel adresi.</span><span class="sxs-lookup"><span data-stu-id="8c3c9-107">[in] The base address of a module in the target process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8c3c9-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8c3c9-108">Return Value</span></span>  

 <span data-ttu-id="8c3c9-109">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="8c3c9-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="8c3c9-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8c3c9-110">HRESULT</span></span>|<span data-ttu-id="8c3c9-111">Description</span><span class="sxs-lookup"><span data-stu-id="8c3c9-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8c3c9-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="8c3c9-112">S_OK</span></span>|<span data-ttu-id="8c3c9-113">Tarafından başvurulan modül `hmodule` bellekten kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="8c3c9-113">The module that is referenced by `hmodule` can be unloaded.</span></span>|  
|<span data-ttu-id="8c3c9-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="8c3c9-114">S_FALSE</span></span>|<span data-ttu-id="8c3c9-115">Tarafından başvurulan modül `hmodule` hala kullanımda.</span><span class="sxs-lookup"><span data-stu-id="8c3c9-115">The module that is referenced by `hmodule` is still in use.</span></span>|  
|<span data-ttu-id="8c3c9-116">COR_E_NOT_CLR</span><span class="sxs-lookup"><span data-stu-id="8c3c9-116">COR_E_NOT_CLR</span></span>|<span data-ttu-id="8c3c9-117">Belirtilen modül bir CLR modülü değil.</span><span class="sxs-lookup"><span data-stu-id="8c3c9-117">The indicated module is not a CLR module.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="8c3c9-118">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="8c3c9-118">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c3c9-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8c3c9-119">Remarks</span></span>  

 <span data-ttu-id="8c3c9-120">Bu yöntem, tüm `ICorDebug*` arabirimlerin örneklerinin serbest bırakıldığını ve şu anda [ICLRDebugging:: OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) metoduna yapılan bir çağrı içinde iş parçacığı olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="8c3c9-120">This method checks to see if all instances of `ICorDebug*` interfaces have been released and no thread is currently within a call to the [ICLRDebugging::OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c3c9-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8c3c9-121">Requirements</span></span>  

 <span data-ttu-id="8c3c9-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c3c9-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c3c9-123">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8c3c9-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8c3c9-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8c3c9-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c3c9-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c3c9-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c3c9-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8c3c9-126">See also</span></span>

- [<span data-ttu-id="8c3c9-127">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8c3c9-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="8c3c9-128">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="8c3c9-128">Debugging</span></span>](index.md)
