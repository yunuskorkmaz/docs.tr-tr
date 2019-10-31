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
ms.openlocfilehash: b27e7a2cdcbfc3a88a734230118d99c2dd5c700e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129533"
---
# <a name="icordebugmodulegetname-method"></a><span data-ttu-id="60890-102">ICorDebugModule::GetName Metodu</span><span class="sxs-lookup"><span data-stu-id="60890-102">ICorDebugModule::GetName Method</span></span>
<span data-ttu-id="60890-103">Modülün dosya adını alır.</span><span class="sxs-lookup"><span data-stu-id="60890-103">Gets the file name of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60890-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="60890-104">Syntax</span></span>  
  
```cpp
HRESULT GetName(  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60890-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="60890-105">Parameters</span></span>  
 `cchname`  
 <span data-ttu-id="60890-106">'ndaki `szName` dizisinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="60890-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="60890-107">'ndaki Döndürülen adın uzunluğuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="60890-107">[in] A pointer to the length of the returned name.</span></span>  
  
 `szName`  
 <span data-ttu-id="60890-108">dışı Döndürülen adı depolayan bir dizi.</span><span class="sxs-lookup"><span data-stu-id="60890-108">[out] An array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60890-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="60890-109">Remarks</span></span>  
 <span data-ttu-id="60890-110">Modülün dosya adı diskteki adla eşleşiyorsa `GetName` yöntemi bir S_OK HRESULT döndürür.</span><span class="sxs-lookup"><span data-stu-id="60890-110">The `GetName` method returns an S_OK HRESULT if the module's file name matches the name on disk.</span></span> <span data-ttu-id="60890-111">`GetName`, bir dinamik veya bellek içi modül gibi bir ad olursa, bir S_FALSE HRESULT döndürür.</span><span class="sxs-lookup"><span data-stu-id="60890-111">`GetName` returns an S_FALSE HRESULT if the name is fabricated, such as for a dynamic or in-memory module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60890-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="60890-112">Requirements</span></span>  
 <span data-ttu-id="60890-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60890-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60890-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="60890-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="60890-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="60890-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60890-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60890-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60890-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="60890-117">See also</span></span>
