---
title: ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Metodu
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5aceed6fa662f090dfe360ddca51da1381b12a2b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54631508"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a><span data-ttu-id="30c32-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Metodu</span><span class="sxs-lookup"><span data-stu-id="30c32-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Method</span></span>
<span data-ttu-id="30c32-103">Önbelleğe alınmış için bir numaralandırıcı alır [!INCLUDE[wrt](../../../../includes/wrt-md.md)] temel alarak kendi arabirimi tanımlayıcılarını uygulama etki alanında tür.</span><span class="sxs-lookup"><span data-stu-id="30c32-103">Gets an enumerator for cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types in an application domain based on their interface identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30c32-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="30c32-104">Syntax</span></span>  
  
```  
HRESULT GetCachedWinRTTypesForIIDs (   
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="30c32-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="30c32-105">Parameters</span></span>  
 `cReqTypes`  
 <span data-ttu-id="30c32-106">[in] Gerekli türleri sayısı.</span><span class="sxs-lookup"><span data-stu-id="30c32-106">[in] The number of required types.</span></span>  
  
 `iidsToResolve`  
 <span data-ttu-id="30c32-107">[in] Yönetilen temsillerini karşılık gelen arabirimi tanımlayıcıları içeren bir dizi işaretçi [!INCLUDE[wrt](../../../../includes/wrt-md.md)] alınacak tür.</span><span class="sxs-lookup"><span data-stu-id="30c32-107">[in] A pointer to an array that contains the interface identifiers corresponding to the managed representations of the [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types to be retrieved.</span></span>  
  
 `ppTypesEnum`  
 <span data-ttu-id="30c32-108">[out] Önbelleğe alınan numaralandırmasına izin veren "ICorDebugTypeEnum" arabirimi nesnenin adresini bir işaretçiye yönetilen temsillerini [!INCLUDE[wrt](../../../../includes/wrt-md.md)] türleri alınan, arabirimi tanımlayıcılara göre `iidsToResolve`.</span><span class="sxs-lookup"><span data-stu-id="30c32-108">[out] A pointer to the address of an "ICorDebugTypeEnum" interface object that allows enumeration of the cached managed representations of the [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types retrieved, based on the interface identifiers in `iidsToResolve`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30c32-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="30c32-109">Remarks</span></span>  
 <span data-ttu-id="30c32-110">Özel arabirim tanımlayıcısı için daha fazla bilgi almak yöntem başarısız olursa, ilgili girişi "ICorDebugTypeEnum" koleksiyonundaki bir türüne sahip `ELEMENT_TYPE_END` hataları veri alma sorunları nedeniyle veya `ELEMENT_TYPE_VOID` bilinmeyen arabirimi tanımlayıcıları.</span><span class="sxs-lookup"><span data-stu-id="30c32-110">If the method fails to retrieve information for a specific interface identifier, the corresponding entry in the "ICorDebugTypeEnum" collection will have a type of `ELEMENT_TYPE_END` for errors due to data retrieval issues, or `ELEMENT_TYPE_VOID` for unknown interface identifiers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30c32-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="30c32-111">Requirements</span></span>  
 <span data-ttu-id="30c32-112">**Platformlar:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30c32-112">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span></span>  
  
 <span data-ttu-id="30c32-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="30c32-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="30c32-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30c32-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30c32-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30c32-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30c32-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30c32-116">See also</span></span>
- [<span data-ttu-id="30c32-117">ICorDebugAppDomain3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="30c32-117">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
