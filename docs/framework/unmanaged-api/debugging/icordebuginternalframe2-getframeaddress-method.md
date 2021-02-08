---
description: 'Daha fazla bilgi edinin: ICorDebugInternalFrame2:: GetFrameAddress yöntemi'
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
ms.openlocfilehash: bb745424680c5b9a5277badfbe2d96db46e2e3d8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791120"
---
# <a name="icordebuginternalframe2getframeaddress-method"></a><span data-ttu-id="b8594-103">ICorDebugInternalFrame2::GetFrameAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b8594-103">ICorDebugInternalFrame2::GetFrameAddress Method</span></span>

<span data-ttu-id="b8594-104">İç çerçevenin yığın adresini döndürür.</span><span class="sxs-lookup"><span data-stu-id="b8594-104">Returns the stack address of the internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8594-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b8594-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameAddress([out] CORDB_ADDRESS *pAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8594-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b8594-106">Parameters</span></span>  

 `pAddress`  
 <span data-ttu-id="b8594-107">dışı `CORDB_ADDRESS` İç çerçeve için işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="b8594-107">[out] Pointer to the `CORDB_ADDRESS` for the internal frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b8594-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b8594-108">Return Value</span></span>  

 <span data-ttu-id="b8594-109">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="b8594-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="b8594-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b8594-110">HRESULT</span></span>|<span data-ttu-id="b8594-111">Description</span><span class="sxs-lookup"><span data-stu-id="b8594-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b8594-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="b8594-112">S_OK</span></span>|<span data-ttu-id="b8594-113">İç çerçevenin adresi başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="b8594-113">The address of the internal frame was successfully returned.</span></span>|  
|<span data-ttu-id="b8594-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b8594-114">E_FAIL</span></span>|<span data-ttu-id="b8594-115">İç çerçevenin adresi döndürülemedi.</span><span class="sxs-lookup"><span data-stu-id="b8594-115">The address of the internal frame could not be returned.</span></span>|  
|<span data-ttu-id="b8594-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="b8594-116">E_INVALIDARG</span></span>|<span data-ttu-id="b8594-117">`pAddress`, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="b8594-117">`pAddress` is `null`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8594-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b8594-118">Remarks</span></span>  

 <span data-ttu-id="b8594-119">İçinde döndürülen değer, `pAddress` yığındaki diğer çerçevelere göre iç çerçevenin konumunu belirlemede kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b8594-119">The value returned in `pAddress` can be used to determine the location of the internal frame relative to other frames on the stack.</span></span> <span data-ttu-id="b8594-120">IA-64 tabanlı bilgisayarlarda bile iç çerçeve yalnızca yığında bulunur ve bir yedekleme deposuna karşılık gelen bir işaretçi yoktur.</span><span class="sxs-lookup"><span data-stu-id="b8594-120">Even on IA-64-based computers, the internal frame lives on the stack only, and there is no corresponding pointer to a backing store.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8594-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b8594-121">Requirements</span></span>  

 <span data-ttu-id="b8594-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8594-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8594-123">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b8594-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8594-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b8594-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8594-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8594-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8594-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8594-126">See also</span></span>

- [<span data-ttu-id="b8594-127">ICorDebugInternalFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b8594-127">ICorDebugInternalFrame2 Interface</span></span>](icordebuginternalframe2-interface.md)
- [<span data-ttu-id="b8594-128">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b8594-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="b8594-129">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="b8594-129">Debugging</span></span>](index.md)
