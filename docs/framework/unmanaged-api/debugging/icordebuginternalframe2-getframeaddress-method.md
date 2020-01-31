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
ms.openlocfilehash: 967c0e18b354e6e1cd0d87900e3cde85991c0862
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794323"
---
# <a name="icordebuginternalframe2getframeaddress-method"></a><span data-ttu-id="a3d18-102">ICorDebugInternalFrame2::GetFrameAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a3d18-102">ICorDebugInternalFrame2::GetFrameAddress Method</span></span>
<span data-ttu-id="a3d18-103">İç çerçevenin yığın adresini döndürür.</span><span class="sxs-lookup"><span data-stu-id="a3d18-103">Returns the stack address of the internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3d18-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a3d18-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameAddress([out] CORDB_ADDRESS *pAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3d18-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a3d18-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="a3d18-106">dışı İç çerçeve için `CORDB_ADDRESS` işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="a3d18-106">[out] Pointer to the `CORDB_ADDRESS` for the internal frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a3d18-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a3d18-107">Return Value</span></span>  
 <span data-ttu-id="a3d18-108">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="a3d18-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a3d18-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a3d18-109">HRESULT</span></span>|<span data-ttu-id="a3d18-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a3d18-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a3d18-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a3d18-111">S_OK</span></span>|<span data-ttu-id="a3d18-112">İç çerçevenin adresi başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="a3d18-112">The address of the internal frame was successfully returned.</span></span>|  
|<span data-ttu-id="a3d18-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a3d18-113">E_FAIL</span></span>|<span data-ttu-id="a3d18-114">İç çerçevenin adresi döndürülemedi.</span><span class="sxs-lookup"><span data-stu-id="a3d18-114">The address of the internal frame could not be returned.</span></span>|  
|<span data-ttu-id="a3d18-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a3d18-115">E_INVALIDARG</span></span>|<span data-ttu-id="a3d18-116">`pAddress` `null`.</span><span class="sxs-lookup"><span data-stu-id="a3d18-116">`pAddress` is `null`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3d18-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a3d18-117">Remarks</span></span>  
 <span data-ttu-id="a3d18-118">`pAddress` döndürülen değer, iç çerçevenin yığındaki diğer çerçevelere göre konumunu belirlemede kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a3d18-118">The value returned in `pAddress` can be used to determine the location of the internal frame relative to other frames on the stack.</span></span> <span data-ttu-id="a3d18-119">IA-64 tabanlı bilgisayarlarda bile iç çerçeve yalnızca yığında bulunur ve bir yedekleme deposuna karşılık gelen bir işaretçi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a3d18-119">Even on IA-64-based computers, the internal frame lives on the stack only, and there is no corresponding pointer to a backing store.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3d18-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a3d18-120">Requirements</span></span>  
 <span data-ttu-id="a3d18-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3d18-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3d18-122">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a3d18-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a3d18-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a3d18-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3d18-124">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3d18-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3d18-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a3d18-125">See also</span></span>

- [<span data-ttu-id="a3d18-126">ICorDebugInternalFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a3d18-126">ICorDebugInternalFrame2 Interface</span></span>](icordebuginternalframe2-interface.md)
- [<span data-ttu-id="a3d18-127">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a3d18-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="a3d18-128">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="a3d18-128">Debugging</span></span>](index.md)
