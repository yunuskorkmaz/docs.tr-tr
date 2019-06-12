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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95c84f7f40db0096b26ec448f8f229cdbfe3afb1
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025900"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a><span data-ttu-id="f6912-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f6912-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Method</span></span>
<span data-ttu-id="f6912-103">Bir numaralandırıcı, kendi arabirimi tanımlayıcılarına göre bir uygulama etki alanındaki önbelleğe alınmış Windows çalışma zamanı türleri için alır.</span><span class="sxs-lookup"><span data-stu-id="f6912-103">Gets an enumerator for cached Windows Runtime types in an application domain based on their interface identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6912-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f6912-104">Syntax</span></span>  
  
```  
HRESULT GetCachedWinRTTypesForIIDs (   
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6912-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f6912-105">Parameters</span></span>  
 `cReqTypes`  
 <span data-ttu-id="f6912-106">[in] Gerekli türleri sayısı.</span><span class="sxs-lookup"><span data-stu-id="f6912-106">[in] The number of required types.</span></span>  
  
 `iidsToResolve`  
 <span data-ttu-id="f6912-107">[in] Alınacak Windows çalışma zamanı türlerini yönetilen gösterimi için karşılık gelen arabirimi tanımlayıcıları içeren bir dizi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f6912-107">[in] A pointer to an array that contains the interface identifiers corresponding to the managed representations of the Windows Runtime types to be retrieved.</span></span>  
  
 `ppTypesEnum`  
 <span data-ttu-id="f6912-108">[out] Windows çalışma zamanı türleri önbelleğe alınan yönetilen temsillerini numaralandırmasına izin veren "ICorDebugTypeEnum" arabirimi nesnenin adresini bir işaretçiye alınan, arabirimi tanımlayıcılara göre `iidsToResolve`.</span><span class="sxs-lookup"><span data-stu-id="f6912-108">[out] A pointer to the address of an "ICorDebugTypeEnum" interface object that allows enumeration of the cached managed representations of the Windows Runtime types retrieved, based on the interface identifiers in `iidsToResolve`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6912-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f6912-109">Remarks</span></span>  
 <span data-ttu-id="f6912-110">Özel arabirim tanımlayıcısı için daha fazla bilgi almak yöntem başarısız olursa, ilgili girişi "ICorDebugTypeEnum" koleksiyonundaki bir türüne sahip `ELEMENT_TYPE_END` hataları veri alma sorunları nedeniyle veya `ELEMENT_TYPE_VOID` bilinmeyen arabirimi tanımlayıcıları.</span><span class="sxs-lookup"><span data-stu-id="f6912-110">If the method fails to retrieve information for a specific interface identifier, the corresponding entry in the "ICorDebugTypeEnum" collection will have a type of `ELEMENT_TYPE_END` for errors due to data retrieval issues, or `ELEMENT_TYPE_VOID` for unknown interface identifiers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6912-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f6912-111">Requirements</span></span>  
 <span data-ttu-id="f6912-112">**Platformlar:** Windows Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="f6912-112">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="f6912-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f6912-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f6912-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f6912-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f6912-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6912-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6912-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f6912-116">See also</span></span>

- [<span data-ttu-id="f6912-117">ICorDebugAppDomain3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f6912-117">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
