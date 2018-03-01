---
title: ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5a7ce44dcfc709b4fea1952471cf31f5f07d4d0e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a><span data-ttu-id="dc445-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Metodu</span><span class="sxs-lookup"><span data-stu-id="dc445-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Method</span></span>
<span data-ttu-id="dc445-103">Önbelleğe alınan için bir numaralandırıcı alır [!INCLUDE[wrt](../../../../includes/wrt-md.md)] kendi arabirim tanımlayıcıları temel alarak bir uygulama etki alanındaki tür.</span><span class="sxs-lookup"><span data-stu-id="dc445-103">Gets an enumerator for cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types in an application domain based on their interface identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc445-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dc445-104">Syntax</span></span>  
  
```  
HRESULT GetCachedWinRTTypesForIIDs (   
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dc445-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dc445-105">Parameters</span></span>  
 `cReqTypes`  
 <span data-ttu-id="dc445-106">[in] Gerekli türlerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="dc445-106">[in] The number of required types.</span></span>  
  
 `iidsToResolve`  
 <span data-ttu-id="dc445-107">[in] Yönetilen gösterimlerini karşılık gelen arabirim tanımlayıcıları içeren bir dizi için bir işaretçi [!INCLUDE[wrt](../../../../includes/wrt-md.md)] alınacak türleri.</span><span class="sxs-lookup"><span data-stu-id="dc445-107">[in] A pointer to an array that contains the interface identifiers corresponding to the managed representations of the [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types to be retrieved.</span></span>  
  
 `ppTypesEnum`  
 <span data-ttu-id="dc445-108">[out] Önbelleğe alınan listesi izin veren bir "ICorDebugTypeEnum" arabirimi nesnesi adresini gösteren bir işaretçi yönetilen gösterimlerini [!INCLUDE[wrt](../../../../includes/wrt-md.md)] türleri alınan, arabirim tanımlayıcıları temel `iidsToResolve`.</span><span class="sxs-lookup"><span data-stu-id="dc445-108">[out] A pointer to the address of an "ICorDebugTypeEnum" interface object that allows enumeration of the cached managed representations of the [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types retrieved, based on the interface identifiers in `iidsToResolve`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc445-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dc445-109">Remarks</span></span>  
 <span data-ttu-id="dc445-110">Belirli bir arabirim tanımlayıcısı bilgilerini almak yöntem başarısız olursa, karşılık gelen bir giriş "ICorDebugTypeEnum" koleksiyonundaki bir türüne sahip `ELEMENT_TYPE_END` veri alma sorunları nedeniyle hatalara veya `ELEMENT_TYPE_VOID` bilinmeyen arabirimi tanımlayıcıları.</span><span class="sxs-lookup"><span data-stu-id="dc445-110">If the method fails to retrieve information for a specific interface identifier, the corresponding entry in the "ICorDebugTypeEnum" collection will have a type of `ELEMENT_TYPE_END` for errors due to data retrieval issues, or `ELEMENT_TYPE_VOID` for unknown interface identifiers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc445-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dc445-111">Requirements</span></span>  
 <span data-ttu-id="dc445-112">**Platformlar:**[!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc445-112">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span></span>  
  
 <span data-ttu-id="dc445-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dc445-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dc445-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dc445-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc445-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc445-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc445-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dc445-116">See Also</span></span>  
 [<span data-ttu-id="dc445-117">ICorDebugAppDomain3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dc445-117">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
