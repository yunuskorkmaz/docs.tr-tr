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
ms.openlocfilehash: 6ef8d1c47275d3cbd69c1516b788b950f8535513
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737723"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a><span data-ttu-id="a0b68-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a0b68-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Method</span></span>
<span data-ttu-id="a0b68-103">Bir numaralandırıcı, kendi arabirimi tanımlayıcılarına göre bir uygulama etki alanındaki önbelleğe alınmış Windows çalışma zamanı türleri için alır.</span><span class="sxs-lookup"><span data-stu-id="a0b68-103">Gets an enumerator for cached Windows Runtime types in an application domain based on their interface identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0b68-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a0b68-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedWinRTTypesForIIDs (   
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0b68-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a0b68-105">Parameters</span></span>  
 `cReqTypes`  
 <span data-ttu-id="a0b68-106">[in] Gerekli türleri sayısı.</span><span class="sxs-lookup"><span data-stu-id="a0b68-106">[in] The number of required types.</span></span>  
  
 `iidsToResolve`  
 <span data-ttu-id="a0b68-107">[in] Alınacak Windows çalışma zamanı türlerini yönetilen gösterimi için karşılık gelen arabirimi tanımlayıcıları içeren bir dizi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a0b68-107">[in] A pointer to an array that contains the interface identifiers corresponding to the managed representations of the Windows Runtime types to be retrieved.</span></span>  
  
 `ppTypesEnum`  
 <span data-ttu-id="a0b68-108">[out] Windows çalışma zamanı türleri önbelleğe alınan yönetilen temsillerini numaralandırmasına izin veren "ICorDebugTypeEnum" arabirimi nesnenin adresini bir işaretçiye alınan, arabirimi tanımlayıcılara göre `iidsToResolve`.</span><span class="sxs-lookup"><span data-stu-id="a0b68-108">[out] A pointer to the address of an "ICorDebugTypeEnum" interface object that allows enumeration of the cached managed representations of the Windows Runtime types retrieved, based on the interface identifiers in `iidsToResolve`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a0b68-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a0b68-109">Remarks</span></span>  
 <span data-ttu-id="a0b68-110">Özel arabirim tanımlayıcısı için daha fazla bilgi almak yöntem başarısız olursa, ilgili girişi "ICorDebugTypeEnum" koleksiyonundaki bir türüne sahip `ELEMENT_TYPE_END` hataları veri alma sorunları nedeniyle veya `ELEMENT_TYPE_VOID` bilinmeyen arabirimi tanımlayıcıları.</span><span class="sxs-lookup"><span data-stu-id="a0b68-110">If the method fails to retrieve information for a specific interface identifier, the corresponding entry in the "ICorDebugTypeEnum" collection will have a type of `ELEMENT_TYPE_END` for errors due to data retrieval issues, or `ELEMENT_TYPE_VOID` for unknown interface identifiers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0b68-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a0b68-111">Requirements</span></span>  
 <span data-ttu-id="a0b68-112">**Platformlar:** Windows Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="a0b68-112">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="a0b68-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a0b68-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a0b68-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a0b68-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0b68-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0b68-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0b68-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0b68-116">See also</span></span>

- [<span data-ttu-id="a0b68-117">ICorDebugAppDomain3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a0b68-117">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
