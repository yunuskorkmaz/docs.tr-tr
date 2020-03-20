---
title: ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain3.GetCachedWinRTTypesForIIDs
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs
helpviewer_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs method, [.NET Framework debugging]
- GetCachedWinRTTypesForIIDs method, ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 23682ca0-1bcf-48e6-996e-69f7ba337682
topic_type:
- apiref
ms.openlocfilehash: f8e92ec4f813e8810273a1514298d0739a3d2406
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179058"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a><span data-ttu-id="fee58-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fee58-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Method</span></span>
<span data-ttu-id="fee58-103">Arabirim tanımlayıcılarını temel alan bir uygulama etki alanında önbelleğe alınmış Windows Runtime türleri için bir sayı eritici alır.</span><span class="sxs-lookup"><span data-stu-id="fee58-103">Gets an enumerator for cached Windows Runtime types in an application domain based on their interface identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fee58-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fee58-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedWinRTTypesForIIDs (
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fee58-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fee58-105">Parameters</span></span>  
 `cReqTypes`  
 <span data-ttu-id="fee58-106">[içinde] Gerekli türlerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="fee58-106">[in] The number of required types.</span></span>  
  
 `iidsToResolve`  
 <span data-ttu-id="fee58-107">[içinde] Alınacak Windows Runtime türlerinin yönetilen gösterimlerine karşılık gelen arabirim tanımlayıcılarını içeren bir diziiçin işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fee58-107">[in] A pointer to an array that contains the interface identifiers corresponding to the managed representations of the Windows Runtime types to be retrieved.</span></span>  
  
 `ppTypesEnum`  
 <span data-ttu-id="fee58-108">[çıkış] Alınan Windows Runtime türlerinin önbelleğe alınmış yönetilen gösterimlerinin numaralandırılmasına olanak tanıyan "ICorDebugTypeEnum" arabirimi `iidsToResolve`nesnesinin adresine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fee58-108">[out] A pointer to the address of an "ICorDebugTypeEnum" interface object that allows enumeration of the cached managed representations of the Windows Runtime types retrieved, based on the interface identifiers in `iidsToResolve`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fee58-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fee58-109">Remarks</span></span>  
 <span data-ttu-id="fee58-110">Yöntem belirli bir arabirim tanımlayıcısı için bilgi almak için başarısız olursa, "ICorDebugTypeEnum" koleksiyonunda `ELEMENT_TYPE_END` karşılık gelen giriş veri alma sorunları `ELEMENT_TYPE_VOID` nedeniyle hatalar için bir tür veya bilinmeyen arabirim tanımlayıcıları için olacaktır.</span><span class="sxs-lookup"><span data-stu-id="fee58-110">If the method fails to retrieve information for a specific interface identifier, the corresponding entry in the "ICorDebugTypeEnum" collection will have a type of `ELEMENT_TYPE_END` for errors due to data retrieval issues, or `ELEMENT_TYPE_VOID` for unknown interface identifiers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fee58-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fee58-111">Requirements</span></span>  
 <span data-ttu-id="fee58-112">**Platformlar:** Windows Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="fee58-112">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="fee58-113">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fee58-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fee58-114">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fee58-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fee58-115">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fee58-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fee58-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fee58-116">See also</span></span>

- [<span data-ttu-id="fee58-117">ICorDebugAppDomain3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fee58-117">ICorDebugAppDomain3 Interface</span></span>](icordebugappdomain3-interface.md)
