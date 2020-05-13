---
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
ms.openlocfilehash: 6a6769265a2e140f1fa001bb8240bc5d4bd76018
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213679"
---
# <a name="icordebugmdagetname-method"></a><span data-ttu-id="72d39-102">ICorDebugMDA::GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="72d39-102">ICorDebugMDA::GetName Method</span></span>
<span data-ttu-id="72d39-103">[ICorDebugMDA](icordebugmda-interface.md)tarafından temsil edilen yönetilen hata ayıklama Yardımcısı 'NıN (MDA) adını içeren bir dize alır.</span><span class="sxs-lookup"><span data-stu-id="72d39-103">Gets a string containing the name of the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72d39-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="72d39-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72d39-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="72d39-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="72d39-106">'ndaki `szName`Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="72d39-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="72d39-107">dışı Adın uzunluğuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="72d39-107">[out] A pointer to the length of the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="72d39-108">dışı Adın kaydedileceği bir dizi.</span><span class="sxs-lookup"><span data-stu-id="72d39-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="72d39-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="72d39-109">Remarks</span></span>  
 <span data-ttu-id="72d39-110">MDA adları benzersiz değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="72d39-110">MDA names are unique values.</span></span> <span data-ttu-id="72d39-111">`GetName`Yöntemi, XML akışının alınması ve şemayı temel alarak akıştan ad ayıklamanın uygun bir performans alternatifidir.</span><span class="sxs-lookup"><span data-stu-id="72d39-111">The `GetName` method is a convenient performance alternative to getting the XML stream and extracting the name from the stream based on the schema.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72d39-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="72d39-112">Requirements</span></span>  
 <span data-ttu-id="72d39-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72d39-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72d39-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="72d39-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="72d39-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="72d39-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72d39-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72d39-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72d39-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72d39-117">See also</span></span>

- [<span data-ttu-id="72d39-118">ICorDebugMDA Arabirimi</span><span class="sxs-lookup"><span data-stu-id="72d39-118">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="72d39-119">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="72d39-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
