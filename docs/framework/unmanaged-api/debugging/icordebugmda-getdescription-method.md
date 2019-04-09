---
title: ICorDebugMDA::GetDescription Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetDescription
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetDescription
helpviewer_keywords:
- GetDescription method [.NET Framework debugging]
- ICorDebugMDA::GetDescription method [.NET Framework debugging]
ms.assetid: 01d1b481-ca67-4712-8744-d342ec0df639
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 998d4baf03123f1ffc174b2a7aeed0ff4a25b001
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59133498"
---
# <a name="icordebugmdagetdescription-method"></a><span data-ttu-id="c8a0c-102">ICorDebugMDA::GetDescription Metodu</span><span class="sxs-lookup"><span data-stu-id="c8a0c-102">ICorDebugMDA::GetDescription Method</span></span>
<span data-ttu-id="c8a0c-103">Tarafından temsil edilen yönetilen hata ayıklama Yardımcısı (MDA) açıklamasını içeren bir dize alır [Icordebugmda](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="c8a0c-103">Gets a string containing the description of the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8a0c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c8a0c-104">Syntax</span></span>  
  
```  
HRESULT GetDescription (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8a0c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c8a0c-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="c8a0c-106">[in] Açıklama depolayacak dize arabelleğinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="c8a0c-106">[in] The size of the string buffer that will store the description.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="c8a0c-107">[out] Döndürülen dize arabellekteki bayt sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c8a0c-107">[out] A pointer to the number of bytes returned in the string buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="c8a0c-108">[out] MDA açıklamasını içeren bir dize arabelleği.</span><span class="sxs-lookup"><span data-stu-id="c8a0c-108">[out] A string buffer containing the description of the MDA.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8a0c-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c8a0c-109">Remarks</span></span>  
 <span data-ttu-id="c8a0c-110">Dize uzunluğu sıfır olabilir.</span><span class="sxs-lookup"><span data-stu-id="c8a0c-110">The string can be zero in length.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8a0c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c8a0c-111">Requirements</span></span>  
 <span data-ttu-id="c8a0c-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8a0c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8a0c-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c8a0c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c8a0c-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c8a0c-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="c8a0c-115">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="c8a0c-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c8a0c-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8a0c-116">See also</span></span>

- [<span data-ttu-id="c8a0c-117">ICorDebugMDA Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c8a0c-117">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [<span data-ttu-id="c8a0c-118">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="c8a0c-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
