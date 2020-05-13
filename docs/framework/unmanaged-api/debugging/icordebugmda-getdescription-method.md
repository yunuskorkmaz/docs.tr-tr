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
ms.openlocfilehash: 522e992e6d7e9a64f7590bbec0e9106e0e1f8f47
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212145"
---
# <a name="icordebugmdagetdescription-method"></a><span data-ttu-id="344f9-102">ICorDebugMDA::GetDescription Metodu</span><span class="sxs-lookup"><span data-stu-id="344f9-102">ICorDebugMDA::GetDescription Method</span></span>
<span data-ttu-id="344f9-103">[ICorDebugMDA](icordebugmda-interface.md)tarafından temsil edilen yönetilen hata ayıklama Yardımcısı 'NıN (MDA) açıklamasını içeren bir dize alır.</span><span class="sxs-lookup"><span data-stu-id="344f9-103">Gets a string containing the description of the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="344f9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="344f9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDescription (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="344f9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="344f9-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="344f9-106">'ndaki Açıklamayı depolayacak dize arabelleğinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="344f9-106">[in] The size of the string buffer that will store the description.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="344f9-107">dışı Dize arabelleğinde döndürülen bayt sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="344f9-107">[out] A pointer to the number of bytes returned in the string buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="344f9-108">dışı MDA öğesinin açıklamasını içeren bir dize arabelleği.</span><span class="sxs-lookup"><span data-stu-id="344f9-108">[out] A string buffer containing the description of the MDA.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="344f9-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="344f9-109">Remarks</span></span>  
 <span data-ttu-id="344f9-110">Dize uzunluğu sıfır olabilir.</span><span class="sxs-lookup"><span data-stu-id="344f9-110">The string can be zero in length.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="344f9-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="344f9-111">Requirements</span></span>  
 <span data-ttu-id="344f9-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="344f9-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="344f9-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="344f9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="344f9-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="344f9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="344f9-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="344f9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="344f9-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="344f9-116">See also</span></span>

- [<span data-ttu-id="344f9-117">ICorDebugMDA Arabirimi</span><span class="sxs-lookup"><span data-stu-id="344f9-117">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="344f9-118">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="344f9-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
