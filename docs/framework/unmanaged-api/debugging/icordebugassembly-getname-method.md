---
title: ICorDebugAssembly::GetName Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetName
helpviewer_keywords:
- ICorDebugAssembly::GetName method [.NET Framework debugging]
- GetName method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: cdeda721-b214-4503-a291-c70b68b5f36b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 38542ec28cce9687dc3ed824f9d449f3070976da
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737306"
---
# <a name="icordebugassemblygetname-method"></a><span data-ttu-id="9c76c-102">ICorDebugAssembly::GetName Metodu</span><span class="sxs-lookup"><span data-stu-id="9c76c-102">ICorDebugAssembly::GetName Method</span></span>
<span data-ttu-id="9c76c-103">Derlemenin adını alır bu `ICorDebugAssembly` örneğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9c76c-103">Gets the name of the assembly that this `ICorDebugAssembly` instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c76c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9c76c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in] ULONG32  cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c76c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9c76c-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="9c76c-106">[in] Boyutu `szName` dizisi.</span><span class="sxs-lookup"><span data-stu-id="9c76c-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="9c76c-107">[out] Gerçek uzunluk adını belirten bir tamsayı işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="9c76c-107">[out] A pointer to an integer that specifies the actual length of the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="9c76c-108">[out] Dizisi adını depolar.</span><span class="sxs-lookup"><span data-stu-id="9c76c-108">[out] An array that stores the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c76c-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9c76c-109">Remarks</span></span>  
 <span data-ttu-id="9c76c-110">`GetName` Yöntemi derlemenin tam yolu ve dosya adını döndürür.</span><span class="sxs-lookup"><span data-stu-id="9c76c-110">The `GetName` method returns the full path and file name of the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c76c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9c76c-111">Requirements</span></span>  
 <span data-ttu-id="9c76c-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c76c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c76c-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9c76c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9c76c-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9c76c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9c76c-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c76c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
