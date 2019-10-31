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
ms.openlocfilehash: 0369cc6d98736542b764e5914d733a9341753b24
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088874"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a><span data-ttu-id="ec92b-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ec92b-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Method</span></span>
<span data-ttu-id="ec92b-103">Bir uygulama etki alanındaki önbelleğe alınmış Windows Çalışma Zamanı türleri için kendi arabirim tanımlayıcılarına göre bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="ec92b-103">Gets an enumerator for cached Windows Runtime types in an application domain based on their interface identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec92b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ec92b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedWinRTTypesForIIDs (   
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec92b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ec92b-105">Parameters</span></span>  
 `cReqTypes`  
 <span data-ttu-id="ec92b-106">'ndaki Gerekli türlerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="ec92b-106">[in] The number of required types.</span></span>  
  
 `iidsToResolve`  
 <span data-ttu-id="ec92b-107">'ndaki Alınacak Windows Çalışma Zamanı türlerinin yönetilen temsillerine karşılık gelen arabirim tanımlayıcılarını içeren bir dizi işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="ec92b-107">[in] A pointer to an array that contains the interface identifiers corresponding to the managed representations of the Windows Runtime types to be retrieved.</span></span>  
  
 `ppTypesEnum`  
 <span data-ttu-id="ec92b-108">dışı Bir "ICorDebugTypeEnum" arabirim nesnesinin, `iidsToResolve`içindeki arabirim tanımlayıcılarına göre alınan Windows Çalışma Zamanı türlerinin önbelleğe alınmış yönetilen temsillerine yönelik numaralandırılmasına izin veren bir.</span><span class="sxs-lookup"><span data-stu-id="ec92b-108">[out] A pointer to the address of an "ICorDebugTypeEnum" interface object that allows enumeration of the cached managed representations of the Windows Runtime types retrieved, based on the interface identifiers in `iidsToResolve`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec92b-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ec92b-109">Remarks</span></span>  
 <span data-ttu-id="ec92b-110">Yöntem belirli bir arabirim tanımlayıcısı için bilgileri alamadığında, "ICorDebugTypeEnum" koleksiyonundaki karşılık gelen giriş, veri alımı sorunları veya bilinmeyen arabirim tanımlayıcıları için `ELEMENT_TYPE_VOID` bir tür `ELEMENT_TYPE_END` olacaktır.</span><span class="sxs-lookup"><span data-stu-id="ec92b-110">If the method fails to retrieve information for a specific interface identifier, the corresponding entry in the "ICorDebugTypeEnum" collection will have a type of `ELEMENT_TYPE_END` for errors due to data retrieval issues, or `ELEMENT_TYPE_VOID` for unknown interface identifiers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec92b-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ec92b-111">Requirements</span></span>  
 <span data-ttu-id="ec92b-112">**Platformlar:** Windows Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="ec92b-112">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="ec92b-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ec92b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ec92b-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ec92b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec92b-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec92b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec92b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec92b-116">See also</span></span>

- [<span data-ttu-id="ec92b-117">ICorDebugAppDomain3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ec92b-117">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
