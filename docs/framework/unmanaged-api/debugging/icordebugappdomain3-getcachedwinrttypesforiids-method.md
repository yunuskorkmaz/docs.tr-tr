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
ms.openlocfilehash: 2aff86fb63b87869ed13028bd7344afe11363f51
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723187"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a><span data-ttu-id="599d0-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="599d0-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Method</span></span>

<span data-ttu-id="599d0-103">Bir uygulama etki alanındaki önbelleğe alınmış Windows Çalışma Zamanı türleri için kendi arabirim tanımlayıcılarına göre bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="599d0-103">Gets an enumerator for cached Windows Runtime types in an application domain based on their interface identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="599d0-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="599d0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedWinRTTypesForIIDs (
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="599d0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="599d0-105">Parameters</span></span>  

 `cReqTypes`  
 <span data-ttu-id="599d0-106">'ndaki Gerekli türlerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="599d0-106">[in] The number of required types.</span></span>  
  
 `iidsToResolve`  
 <span data-ttu-id="599d0-107">'ndaki Alınacak Windows Çalışma Zamanı türlerinin yönetilen temsillerine karşılık gelen arabirim tanımlayıcılarını içeren bir dizi işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="599d0-107">[in] A pointer to an array that contains the interface identifiers corresponding to the managed representations of the Windows Runtime types to be retrieved.</span></span>  
  
 `ppTypesEnum`  
 <span data-ttu-id="599d0-108">dışı İçindeki arabirim tanımlayıcılarına göre alınan Windows Çalışma Zamanı türlerinin önbelleğe alınmış yönetilen temsillerine yönelik numaralandırılmasına izin veren bir "ICorDebugTypeEnum" arabirim nesnesinin adresine yönelik bir işaretçi `iidsToResolve` .</span><span class="sxs-lookup"><span data-stu-id="599d0-108">[out] A pointer to the address of an "ICorDebugTypeEnum" interface object that allows enumeration of the cached managed representations of the Windows Runtime types retrieved, based on the interface identifiers in `iidsToResolve`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="599d0-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="599d0-109">Remarks</span></span>  

 <span data-ttu-id="599d0-110">Yöntem belirli bir arabirim tanımlayıcısı için bilgileri alamadığında, "ICorDebugTypeEnum" koleksiyonundaki karşılık gelen giriş, `ELEMENT_TYPE_END` veri alımı sorunları veya bilinmeyen arabirim tanımlayıcıları nedeniyle hata için bir tür olur `ELEMENT_TYPE_VOID` .</span><span class="sxs-lookup"><span data-stu-id="599d0-110">If the method fails to retrieve information for a specific interface identifier, the corresponding entry in the "ICorDebugTypeEnum" collection will have a type of `ELEMENT_TYPE_END` for errors due to data retrieval issues, or `ELEMENT_TYPE_VOID` for unknown interface identifiers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="599d0-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="599d0-111">Requirements</span></span>  

 <span data-ttu-id="599d0-112">**Platformlar:** Windows Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="599d0-112">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="599d0-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="599d0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="599d0-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="599d0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="599d0-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="599d0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="599d0-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="599d0-116">See also</span></span>

- [<span data-ttu-id="599d0-117">ICorDebugAppDomain3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="599d0-117">ICorDebugAppDomain3 Interface</span></span>](icordebugappdomain3-interface.md)
