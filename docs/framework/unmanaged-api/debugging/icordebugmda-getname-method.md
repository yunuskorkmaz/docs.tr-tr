---
description: ': ICorDebugMDA:: GetName metodu hakkında daha fazla bilgi edinin'
title: ICorDebugMDA::GetName Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetName
helpviewer_keywords:
- ICorDebugMDA::GetName method [.NET Framework debugging]
- GetName method, ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 885bf5e8-00b7-4cd7-9d8d-e720d47918c4
topic_type:
- apiref
ms.openlocfilehash: 4ea39f062071073684a20d8f60875fbaaab43a2f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801175"
---
# <a name="icordebugmdagetname-method"></a><span data-ttu-id="4c47f-103">ICorDebugMDA::GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4c47f-103">ICorDebugMDA::GetName Method</span></span>

<span data-ttu-id="4c47f-104">[ICorDebugMDA](icordebugmda-interface.md)tarafından temsil edilen yönetilen hata ayıklama Yardımcısı 'NıN (MDA) adını içeren bir dize alır.</span><span class="sxs-lookup"><span data-stu-id="4c47f-104">Gets a string containing the name of the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c47f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4c47f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c47f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4c47f-106">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="4c47f-107">'ndaki `szName` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="4c47f-107">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="4c47f-108">dışı Adın uzunluğuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4c47f-108">[out] A pointer to the length of the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="4c47f-109">dışı Adın kaydedileceği bir dizi.</span><span class="sxs-lookup"><span data-stu-id="4c47f-109">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c47f-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4c47f-110">Remarks</span></span>  

 <span data-ttu-id="4c47f-111">MDA adları benzersiz değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="4c47f-111">MDA names are unique values.</span></span> <span data-ttu-id="4c47f-112">`GetName`Yöntemi, XML akışının alınması ve şemayı temel alarak akıştan ad ayıklamanın uygun bir performans alternatifidir.</span><span class="sxs-lookup"><span data-stu-id="4c47f-112">The `GetName` method is a convenient performance alternative to getting the XML stream and extracting the name from the stream based on the schema.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c47f-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4c47f-113">Requirements</span></span>  

 <span data-ttu-id="4c47f-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c47f-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c47f-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4c47f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4c47f-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4c47f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4c47f-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c47f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c47f-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4c47f-118">See also</span></span>

- [<span data-ttu-id="4c47f-119">ICorDebugMDA Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4c47f-119">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="4c47f-120">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="4c47f-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
