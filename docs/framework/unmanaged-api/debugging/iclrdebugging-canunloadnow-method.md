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
ms.openlocfilehash: e89d936c528ea7482487a8629dbd882f6f67483e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723577"
---
# <a name="iclrdebuggingcanunloadnow-method"></a><span data-ttu-id="a19f6-102">ICLRDebugging::CanUnloadNow Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a19f6-102">ICLRDebugging::CanUnloadNow Method</span></span>

<span data-ttu-id="a19f6-103">Bir [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) arabirimi tarafından sağlanmış bir kitaplığın hala kullanımda olup olmadığını veya kaldırılabileceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="a19f6-103">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a19f6-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a19f6-104">Syntax</span></span>  
  
```cpp  
HRESULT CanUnloadNow(HMODULE hModule);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a19f6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a19f6-105">Parameters</span></span>  

 `hmodule`  
 <span data-ttu-id="a19f6-106">'ndaki Hedef işlemdeki bir modülün temel adresi.</span><span class="sxs-lookup"><span data-stu-id="a19f6-106">[in] The base address of a module in the target process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a19f6-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a19f6-107">Return Value</span></span>  

 <span data-ttu-id="a19f6-108">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="a19f6-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a19f6-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a19f6-109">HRESULT</span></span>|<span data-ttu-id="a19f6-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a19f6-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a19f6-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a19f6-111">S_OK</span></span>|<span data-ttu-id="a19f6-112">Tarafından başvurulan modül `hmodule` bellekten kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="a19f6-112">The module that is referenced by `hmodule` can be unloaded.</span></span>|  
|<span data-ttu-id="a19f6-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="a19f6-113">S_FALSE</span></span>|<span data-ttu-id="a19f6-114">Tarafından başvurulan modül `hmodule` hala kullanımda.</span><span class="sxs-lookup"><span data-stu-id="a19f6-114">The module that is referenced by `hmodule` is still in use.</span></span>|  
|<span data-ttu-id="a19f6-115">COR_E_NOT_CLR</span><span class="sxs-lookup"><span data-stu-id="a19f6-115">COR_E_NOT_CLR</span></span>|<span data-ttu-id="a19f6-116">Belirtilen modül bir CLR modülü değil.</span><span class="sxs-lookup"><span data-stu-id="a19f6-116">The indicated module is not a CLR module.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="a19f6-117">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="a19f6-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a19f6-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a19f6-118">Remarks</span></span>  

 <span data-ttu-id="a19f6-119">Bu yöntem, tüm `ICorDebug*` arabirimlerin örneklerinin serbest bırakıldığını ve şu anda [ICLRDebugging:: OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) metoduna yapılan bir çağrı içinde iş parçacığı olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="a19f6-119">This method checks to see if all instances of `ICorDebug*` interfaces have been released and no thread is currently within a call to the [ICLRDebugging::OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a19f6-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a19f6-120">Requirements</span></span>  

 <span data-ttu-id="a19f6-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a19f6-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a19f6-122">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a19f6-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a19f6-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a19f6-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a19f6-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a19f6-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a19f6-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a19f6-125">See also</span></span>

- [<span data-ttu-id="a19f6-126">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a19f6-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="a19f6-127">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="a19f6-127">Debugging</span></span>](index.md)
