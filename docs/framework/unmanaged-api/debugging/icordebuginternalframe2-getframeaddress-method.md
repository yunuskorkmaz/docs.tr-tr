---
title: ICorDebugInternalFrame2::GetFrameAddress Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame2.GetFrameAddress Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame2::GetFrameAddress
helpviewer_keywords:
- GetFrameAddress method [.NET Framework debugging]
- ICorDebugInternalFrame2::GetFrameAddress method [.NET Framework debugging]
ms.assetid: 4ee8d058-ffc8-4967-9133-a5adfef4e518
topic_type:
- apiref
ms.openlocfilehash: 05a9ab58acb3bf5829fd231ae6d8bcc96ae06da6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724877"
---
# <a name="icordebuginternalframe2getframeaddress-method"></a><span data-ttu-id="ea3cb-102">ICorDebugInternalFrame2::GetFrameAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ea3cb-102">ICorDebugInternalFrame2::GetFrameAddress Method</span></span>

<span data-ttu-id="ea3cb-103">İç çerçevenin yığın adresini döndürür.</span><span class="sxs-lookup"><span data-stu-id="ea3cb-103">Returns the stack address of the internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea3cb-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ea3cb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameAddress([out] CORDB_ADDRESS *pAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea3cb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ea3cb-105">Parameters</span></span>  

 `pAddress`  
 <span data-ttu-id="ea3cb-106">dışı `CORDB_ADDRESS` İç çerçeve için işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="ea3cb-106">[out] Pointer to the `CORDB_ADDRESS` for the internal frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ea3cb-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ea3cb-107">Return Value</span></span>  

 <span data-ttu-id="ea3cb-108">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="ea3cb-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ea3cb-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ea3cb-109">HRESULT</span></span>|<span data-ttu-id="ea3cb-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea3cb-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ea3cb-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ea3cb-111">S_OK</span></span>|<span data-ttu-id="ea3cb-112">İç çerçevenin adresi başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="ea3cb-112">The address of the internal frame was successfully returned.</span></span>|  
|<span data-ttu-id="ea3cb-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ea3cb-113">E_FAIL</span></span>|<span data-ttu-id="ea3cb-114">İç çerçevenin adresi döndürülemedi.</span><span class="sxs-lookup"><span data-stu-id="ea3cb-114">The address of the internal frame could not be returned.</span></span>|  
|<span data-ttu-id="ea3cb-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="ea3cb-115">E_INVALIDARG</span></span>|<span data-ttu-id="ea3cb-116">`pAddress`, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="ea3cb-116">`pAddress` is `null`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea3cb-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ea3cb-117">Remarks</span></span>  

 <span data-ttu-id="ea3cb-118">İçinde döndürülen değer, `pAddress` yığındaki diğer çerçevelere göre iç çerçevenin konumunu belirlemede kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ea3cb-118">The value returned in `pAddress` can be used to determine the location of the internal frame relative to other frames on the stack.</span></span> <span data-ttu-id="ea3cb-119">IA-64 tabanlı bilgisayarlarda bile iç çerçeve yalnızca yığında bulunur ve bir yedekleme deposuna karşılık gelen bir işaretçi yoktur.</span><span class="sxs-lookup"><span data-stu-id="ea3cb-119">Even on IA-64-based computers, the internal frame lives on the stack only, and there is no corresponding pointer to a backing store.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea3cb-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ea3cb-120">Requirements</span></span>  

 <span data-ttu-id="ea3cb-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea3cb-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea3cb-122">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ea3cb-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ea3cb-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ea3cb-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea3cb-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea3cb-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea3cb-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea3cb-125">See also</span></span>

- [<span data-ttu-id="ea3cb-126">ICorDebugInternalFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ea3cb-126">ICorDebugInternalFrame2 Interface</span></span>](icordebuginternalframe2-interface.md)
- [<span data-ttu-id="ea3cb-127">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ea3cb-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="ea3cb-128">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="ea3cb-128">Debugging</span></span>](index.md)
