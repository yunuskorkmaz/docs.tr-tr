---
description: ': ICorDebugMDA:: GetDescription yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 75ee7d0b912c9f0039acc872173f2cbad25fff38
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801208"
---
# <a name="icordebugmdagetdescription-method"></a><span data-ttu-id="45e27-103">ICorDebugMDA::GetDescription Metodu</span><span class="sxs-lookup"><span data-stu-id="45e27-103">ICorDebugMDA::GetDescription Method</span></span>

<span data-ttu-id="45e27-104">[ICorDebugMDA](icordebugmda-interface.md)tarafından temsil edilen yönetilen hata ayıklama Yardımcısı 'NıN (MDA) açıklamasını içeren bir dize alır.</span><span class="sxs-lookup"><span data-stu-id="45e27-104">Gets a string containing the description of the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45e27-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="45e27-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDescription (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="45e27-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="45e27-106">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="45e27-107">'ndaki Açıklamayı depolayacak dize arabelleğinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="45e27-107">[in] The size of the string buffer that will store the description.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="45e27-108">dışı Dize arabelleğinde döndürülen bayt sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="45e27-108">[out] A pointer to the number of bytes returned in the string buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="45e27-109">dışı MDA öğesinin açıklamasını içeren bir dize arabelleği.</span><span class="sxs-lookup"><span data-stu-id="45e27-109">[out] A string buffer containing the description of the MDA.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45e27-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="45e27-110">Remarks</span></span>  

 <span data-ttu-id="45e27-111">Dize uzunluğu sıfır olabilir.</span><span class="sxs-lookup"><span data-stu-id="45e27-111">The string can be zero in length.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45e27-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="45e27-112">Requirements</span></span>  

 <span data-ttu-id="45e27-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45e27-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45e27-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="45e27-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="45e27-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="45e27-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45e27-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45e27-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45e27-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="45e27-117">See also</span></span>

- [<span data-ttu-id="45e27-118">ICorDebugMDA Arabirimi</span><span class="sxs-lookup"><span data-stu-id="45e27-118">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="45e27-119">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="45e27-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
