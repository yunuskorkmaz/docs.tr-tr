---
title: ICorDebugModule::GetName Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetName
helpviewer_keywords:
- ICorDebugModule::GetName method [.NET Framework debugging]
- GetName method, ICorDebugModule interface [.NET Framework debugging]
ms.assetid: db499637-7ba9-421e-b8b1-35856995e80b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: efbcd6f9eca426cd230653e38d527e184b378fa0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57503157"
---
# <a name="icordebugmodulegetname-method"></a><span data-ttu-id="871b9-102">ICorDebugModule::GetName Metodu</span><span class="sxs-lookup"><span data-stu-id="871b9-102">ICorDebugModule::GetName Method</span></span>
<span data-ttu-id="871b9-103">Modül dosya adını alır.</span><span class="sxs-lookup"><span data-stu-id="871b9-103">Gets the file name of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="871b9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="871b9-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="871b9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="871b9-105">Parameters</span></span>  
 `cchname`  
 <span data-ttu-id="871b9-106">[in] Boyutu `szName` dizisi.</span><span class="sxs-lookup"><span data-stu-id="871b9-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="871b9-107">[in] Döndürülen adının uzunluğu bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="871b9-107">[in] A pointer to the length of the returned name.</span></span>  
  
 `szName`  
 <span data-ttu-id="871b9-108">[out] Döndürülen adını depolar dizisi.</span><span class="sxs-lookup"><span data-stu-id="871b9-108">[out] An array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="871b9-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="871b9-109">Remarks</span></span>  
 <span data-ttu-id="871b9-110">`GetName` Yöntemi modülün dosya adı disk adına eşleşmesi durumunda bir S_OK HRESULT döndürür.</span><span class="sxs-lookup"><span data-stu-id="871b9-110">The `GetName` method returns an S_OK HRESULT if the module's file name matches the name on disk.</span></span> <span data-ttu-id="871b9-111">`GetName` adı üretilmiş, dinamik ya da belleğe modülü gibi ise S_FALSE HRESULT döndürür.</span><span class="sxs-lookup"><span data-stu-id="871b9-111">`GetName` returns an S_FALSE HRESULT if the name is fabricated, such as for a dynamic or in-memory module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="871b9-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="871b9-112">Requirements</span></span>  
 <span data-ttu-id="871b9-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="871b9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="871b9-114">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="871b9-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="871b9-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="871b9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="871b9-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="871b9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="871b9-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="871b9-117">See also</span></span>


